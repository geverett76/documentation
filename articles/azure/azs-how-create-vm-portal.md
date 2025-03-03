---
title: How to create a VM using the UKCloud Azure Stack Hub portal
description: Create a virtual machine in UKCloud for Microsoft Azure
services: azure-stack
author: shighmoor
reviewer: wturner
lastreviewed: 10/08/2021

toc_rootlink: Users
toc_sub1: How To
toc_sub2: Create a Virtual Machine
toc_sub3:
toc_sub4:
toc_title: Create a virtual machine - Portal
toc_fullpath: Users/How To/Create a Virtual Machine/azs-how-create-vm-portal.md
toc_mdlink: azs-how-create-vm-portal.md
---

# How to create a virtual machine using the UKCloud Azure Stack Hub portal

## Overview

With UKCloud for Microsoft Azure, you can leverage the power of Microsoft Azure to create virtual machines (VMs) for your on-premises applications. As UKCloud for Microsoft Azure is built on UKCloud's assured, UK-sovereign multi-cloud platform, those applications can work alongside other cloud platforms, such as Oracle, VMware and OpenStack, and benefit from native connectivity to non-cloud workloads in Crown Hosting and government community networks, including PSN, HSCN and MCN.

### Intended audience

To complete the steps in this guide, you must have appropriate access to a subscription in the Azure Stack Hub portal.

## Creating a virtual machine

VMs provide the basic compute building blocks in Azure Stack Hub. You can create VMs using the Azure Stack Hub Marketplace, which provides access to pre-created images to quickly deploy the VMs you need to build your applications. Microsoft makes Azure Marketplace images available for Azure Stack Hub once they have passed an accreditation process. If you cannot find the image you require in the Azure Stack Hub Marketplace please raise a support call via the UKCloud portal and if possible we will make your requested image available in Azure Stack Hub Marketplace.

**To create a VM from the Azure Marketplace:**

1. Log in to the Azure Stack Hub portal.

   For more detailed instructions, see the [*Getting Started Guide for UKCloud for Microsoft Azure*](azs-gs.md).

2. In the favourites panel, select **Create a resource**.

    ![New option in favourites panel](images/azsp_newmenu.png)

3. In the *New* blade, select **Compute**.

    ![Compute option in New blade](images/azsp_newblade.png)

4. In the *Compute* blade, select the template that you want to use for your VM.

    ![List of VM images in Compute blade](images/azsp_computeblade.png)

5. In the *Create a virtual machine* blade, in the *Basics* step, enter general information about the VM, including a name, credentials and resource group.

    ![Create virtual machine > Basics](images/azsp_createvm_basics.png)

6. Still in the *Basics* step, click **Change size** under the currently selected VM size to view all the available sizes. Select the appropriate size for your VM, depending on its purpose, then click **Select**.

    For information about the different available VM sizes, see <https://docs.microsoft.com/en-gb/azure/azure-stack/user/azure-stack-vm-sizes>.

    ![Create virtual machine > Size](images/azsp_createvm_size.png)

7. Change any of the optional settings located in the other tabs, then click **Review + create**.

    > [!NOTE]
    > For storage, managed disks are selected by default (*Disks* step).

    ![Create virtual machine > Disks](images/azsp_createvm_disks.png)

    > [!IMPORTANT]
    > There will be no public inbound ports open on the network security group if left unchanged (*Networking* step).

    ![Create virtual machine > Networking](images/azsp_createvm_networking.png)

    > [!NOTE]
    > By default, boot diagnostics will be switched on for the virtual machine (*Management* step).

    ![Create virtual machine > Management](images/azsp_createvm_management.png)

8. In the *Review + create* step, review the selections you've made and then click **Create** to start the deployment.

    ![Create virtual machine > Review](images/azsp_createvm_review.png)

9. You can monitor the progress of your VM's deployment by clicking the **Notifications** icon.

    ![Notification showing VM deployment in progress](images/azsp_createvm_progress.png)

10. Click the deployment notification for the deployment to view details of the deployment of the VM and its resources.

    ![Status of VM deployment](images/azsp_createvm_deployment.png)

11. When the deployment is finished, the notification will change to **Deployment succeeded**.

    ![Notification showing successful VM deployment](images/azsp_createvm_deployment_success.png)

12. After your VM has deployed, you can view it by clicking **Virtual machines** in the favourites panel.

    ![Virtual machines option in favourites panel](images/azsp_vmsmenu.png)

13. Select your VM from the list.

    ![List of deployed VMs](images/azsp_vmslist.png)

14. In the blade for your VM, you can view and monitor the VM, change its settings and perform diagnostics and troubleshooting.

    ![Virtual machine details](images/azsp_vmdetails.png)

## Next steps

For more information about UKCloud for Microsoft Azure, see:

- [*Understanding UKCloud for Microsoft Azure*](azs-ref-overview.md)

- [*Getting Started Guide for UKCloud for Microsoft Azure*](azs-gs.md)

- [*UKCloud for Microsoft Azure FAQs*](azs-faq.md)

## Related videos

- [*UKCloud Azure Stack Hub portal overview video*](azs-vid-overview.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
