---
title: How to convert a virtual machine to use managed disks using PowerShell
description: Provides help for converting a virtual machine from unmanaged to managed disks on UKCloud for Microsoft Azure
services: azure-stack
author: blawson
reviewer: wturner
lastreviewed: 06/12/2021

toc_rootlink: Users
toc_sub1: How To
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Convert a VM to use managed disks - PowerShell
toc_fullpath: Users/How To/azs-how-convert-to-managed-disks-ps.md
toc_mdlink: azs-how-convert-to-managed-disks-ps.md
---

# How to convert a virtual machine to use managed disks using PowerShell

## Overview

UKCloud for Microsoft Azure supports the use of managed disks on virtual machines (VMs). You can use managed disks as both OS disks and data disks.

For more information, see [Introduction to Azure managed disks](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/managed-disks-overview).

The following article shows you how to convert a virtual machine from unmanaged to managed disks on UKCloud for Microsoft Azure.

> [!WARNING]
> At the time of writing, the [ConvertTo-AzVMManagedDisk](https://docs.microsoft.com/en-us/powershell/module/azurerm.compute/convertto-azurermvmmanageddisk?view=azurermps-6.13.0) cmdlet is not supported on Azure Stack Hub and will result in your VM becoming unmanageable. Follow the process below to convert your unmanaged disks safely.

> [!WARNING]
> Running the script below will result in downtime for your virtual machine as it needs to be removed then recreated.

## Prerequisites

Before you begin, ensure your PowerShell environment is set up as detailed in [Configure the Azure Stack Hub user's PowerShell environment](azs-how-configure-powershell-users.md).

## Converting a virtual machine to use managed disks

### Declare variables

Enter details below to provide values for the variables in the following script in this article:

| Variable name   | Variable description                                               | Input            |
|-----------------|--------------------------------------------------------------------|------------------|
| \$ArmEndpoint   | The Azure Resource Manager endpoint for Azure Stack Hub                | <form oninput="result.value=armendpoint.value" id="armendpoint" style="display: inline;"><input type="text" id="armendpoint" name="armendpoint" style="display: inline;" placeholder="https://management.frn00006.azure.ukcloud.com"/></form> |
| \$RGName        | Name of the resource group that the VM exists in                   | <form oninput="result.value=resourcegroup.value" id="resourcegroup" style="display: inline;"><input type="text" id="resourcegroup" name="resourcegroup" style="display: inline;" placeholder="MyResourceGroup"/></form> |
| \$VMName        | Name of the virtual machine to convert to use managed disks        | <form oninput="result.value=vmname.value" id="vmname" style="display: inline;"><input type="text" id="vmname" name="vmname" style="display: inline;" placeholder="MyVM"/></form> |
| \$SAName        | Name of the storage account that contains the unmanaged disks      | <form oninput="result.value=saname.value" id="saname" style="display: inline;"><input type="text" id="saname" name="saname" style="display: inline;" placeholder="MyStorageAccount"/></form> |

### Convert the virtual machine

From your PowerShell window:

<pre><code class="language-PowerShell"># Initialise environment and variables

# Declare endpoint
$ArmEndpoint = "<output form="armendpoint" name="result" style="display: inline;">https://management.frn00006.azure.ukcloud.com</output>"

## Add environment
Add-AzEnvironment -Name "AzureStackUser" -ArmEndpoint $ArmEndpoint

## Login
Connect-AzAccount -EnvironmentName "AzureStackUser"

# Get location of Azure Stack Hub
$Location = (Get-AzLocation).Location

# Input Variables
$RGName = "<output form="resourcegroup" name="result" style="display: inline;">MyResourceGroup</output>"
$VMName = "<output form="vmname" name="result" style="display: inline;">MyVM</output>"
$SAName = "<output form="saname" name="result" style="display: inline;">MyStorageAccount</output>"

# Retrieve virtual machine details
$OldVM = Get-AzVM -ResourceGroupName $RGName -Name $VMName

# Remove the VM, keeping the disks
Write-Output -InputObject "Removing old virtual machine"
Remove-AzVM -Name $VMName -ResourceGroupName $RGName -Force

# Create OS managed disk
Write-Output -InputObject "Creating OS managed disk"
$SAId = (Get-AzStorageAccount -ResourceGroupName $RGName -Name $SAName).Id
$OSDiskConfig = New-AzDiskConfig -AccountType "Standard_LRS" -Location $Location -DiskSizeGB $OldVM.StorageProfile.OsDisk.DiskSizeGB `
    -SourceUri $OldVM.StorageProfile.OsDisk.Vhd.Uri -StorageAccountId $SAId -CreateOption "Import"
$OSDisk = New-AzDisk -DiskName "$($OldVM.Name)_$($OldVM.StorageProfile.OsDisk.Name)" -Disk $OSDiskConfig -ResourceGroupName $RGName

# Create data managed disks
if ($OldVM.StorageProfile.DataDisks) {
    $DataDiskArray = @()
    foreach ($DataDisk in $OldVM.StorageProfile.DataDisks) {
        Write-Output -InputObject "Creating data managed disk"
        $DataDiskConfig = New-AzDiskConfig -AccountType "Standard_LRS" -Location $Location -DiskSizeGB $DataDisk.DiskSizeGB `
            -SourceUri $DataDisk.Vhd.Uri -StorageAccountId $SAId -CreateOption "Import"
        $DataDiskArray += New-AzDisk -DiskName "$($OldVM.Name)_$($DataDisk.Name)" -Disk $DataDiskConfig -ResourceGroupName $RGName
    }
}

# Create new virtual machine config
$NewVMConfig = New-AzVMConfig -VMName $VMName -VMSize $OldVM.HardwareProfile.VmSize

# Add OS disk to the new virtual machine config
if ($OldVM.OSProfile.LinuxConfiguration) {
    $NewVMConfig = Set-AzVMOSDisk -VM $NewVMConfig -ManagedDiskId $OSDisk.Id -CreateOption "Attach" -Linux
}
else {
    $NewVMConfig = Set-AzVMOSDisk -VM $NewVMConfig -ManagedDiskId $OSDisk.Id -CreateOption "Attach" -Windows
}

# Add data disk(s) to the new virtual machine config
$Lun = 0
foreach ($Disk in $DataDiskArray) {
    $NewVMConfig = Add-AzVMDataDisk -VM $NewVMConfig -ManagedDiskId $Disk.Id -CreateOption Attach -Lun $Lun -DiskSizeInGB $Disk.DiskSizeGB
    $Lun++
}

# Add network interface card(s) to the new virtual machine config
foreach ($Nic in $OldVM.NetworkProfile.NetworkInterfaces) {
    if ($Nic.Primary -eq $true -or $Nic.Primary -eq $null) {
        $NewVMConfig = Add-AzVMNetworkInterface -VM $NewVMConfig -Id $Nic.Id -Primary
    }
    else {
        $NewVMConfig = Add-AzVMNetworkInterface -VM $NewVMConfig -Id $Nic.Id
    }
}

# Create the new virtual machine
Write-Output -InputObject "Creating new virtual machine"
New-AzVM -VM $NewVMConfig -ResourceGroupName $RGName -Location $Location
Get-AzVM -ResourceGroupName $RGName -Name $VMName
Write-Output -InputObject "The virtual machine has been created successfully"
</code></pre>

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
