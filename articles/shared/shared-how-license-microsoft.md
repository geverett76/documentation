---
title: How to license Microsoft software on the UKCloud platform
description: Explains how Microsoft software, such as Windows Server and SQL, is licensed on the UKCloud platform
services: shared-services
author: shall
reviewer: aokanlawon
lastreviewed: 03/05/2022
toc_rootlink: How To
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: License Microsoft software on the UKCloud platform
toc_fullpath: How to/shared-how-license-microsoft.md
toc_mdlink: shared-how-license-microsoft.md
---

# How to license Microsoft applications/software on the UKCloud platform

## Overview

> [!IMPORTANT]
> It is **your** responsibility to ensure that you have a valid licence for any software installed on the UKCloud platform if applicable. Contact your Service Delivery Manager or raise a support ticket if you have any concerns regarding the licensing of your workload and any applications. Microsoft perform regular audits, and in the event that your workloads have been operating without the correct level of licensing in place, UKCloud reserves the right to apply retrospective billing for the missing licensing and to place the relevant licence orders against our SPLA agreement.

This article provides information on how you can apply Microsoft licensing on our platform and the options available to you.

UKCloud offers three ways to license Microsoft software for use on our compute platform, providing you with the flexibility you need to deliver your application workloads in line with Microsoft requirements and obligations:

- UKCloud can purchase licences monthly for you via our Microsoft Services Provider License Agreement (SPLA) or Cloud Solution Provider (CSP) Program.

- You can submit a [Microsoft Licence Mobility Verification form](https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-license-mobility.aspx) to use your own existing licensing. This must be done **before** you use the application on the UKCloud platform.

- You can use your own monthly reported SPLA, for example if you have SPLA application licensing for SQL. In this case, you'll need to provide a confirmation to your UKCloud Service Delivery Manager or raise a support ticket and provide the SPLA details in case of an audit.

## Microsoft SPLA 

Microsoft SPLA is a Service Provider License Agreement. Licences are reported on a monthly basis under SPLA, are non-perpetual and UKCloud uses the per processor/per core model. The core model is ideal for a multi-tenant public cloud as although every physical core on every server will need a licence, an unlimited number of users can access the licensed product. Core licensing is required when the number of users cannot be counted or fluctuates. It's important to note that customers do not need to license SALs when UKCloud are licensing per core. UKCloud uses this method for licensing Microsoft Server, which enables us to charge customers per hour that their VMs use Microsoft Server. 

When using SPLA licensing, customers don't need to purchase Software Assurance as they'll automatically get the latest version rights and can choose any version of the operating system or applcation that suits their requirements. UKCloud has a wide range of versions available in the UKCloud product catalog and can make other versions available on request. It's important to note however, that customers don't get any of the other benefits that Software Assurance offers.

## Microsoft Server licensing

To make the provisioning of Microsoft-based virtual machines (VMs) as simple and quick as possible, while remaining in line with our Microsoft agreement, all Microsoft Server licences must be provided by UKCloud.

The standard licensing approach is for us to provide Microsoft Windows Server licences on a per hour basis. This is retrospectively billed based on your usage of an associated VM.

> [!IMPORTANT]
> You cannot bring your own Microsoft Windows Server licences for use on the UKCloud platform within the multi-tenant (public cloud) environments.

For your Microsoft Windows Server‑based VMs in our multi-tenant environments, to use a UKCloud-purchased licence you must create all your Microsoft VMs using a Microsoft template from the UKCloud product catalog. If you prefer to create your Microsoft VMs using your own template, you must then register these VMs with our Key Management Server (KMS). See the [*How to license Windows VMs using the UKCloud Key Management Server*](shared-how-setup-kms.md) article or [*Licensing Windows VMs using the UKCloud Key Management Server video*](shared-vid-licensing-kms.md) for information about how to do this.

The Microsoft Windows Server licence is invoiced each month, in addition to the cost of the VM, based on the VM's usage.

We automatically bill the usage of Microsoft Windows Server per hour that the VM is powered on, and invoice you for your consumption of Microsoft Windows Server per month using the following pricing table:

VM size | SPLA Per hour per VM | Academic Per hour per VM
--------|----------------------|---------------------------
Micro, Tiny VM | £0.013 | £0.002
Small VM | £0.025 | £0.003
Medium VM, Medium High Memory | £0.051 | £0.007
Large VM, Large High Memory, Tier 1 Apps | £0.149 | £0.020

Due to the elimination of the discount for G-SPLA, there is now price parity with corporate SPLA. As a result, customers who may not have previously been applicable for G-SPLA are not impacted.

## Microsoft desktop licensing

UKCloud offers a variety of ways for you to run and license Windows desktop workloads on the platform:

- UKCloud Desktop as a Service. A purpose-built VDI/remote working solution aimed at enabling customers to virtualise their desktop usage, including all of the licensing required. Details are available within the Knowledge Centre for more information.

- Purchasing Windows 10 Enterprise licences from UKCloud. As a Microsoft CSP, UKCloud is able to purchase and provide Windows 10 Enterprise licences for customers on a monthly basis, charged per month. To utilise this service, create a Service Request stating the number and version of licences required.

  > [!NOTE]
  > For this subscription service to work, the devices or virtual machines that require Windows 10 Enterprise licences must be internet connected to enable the administrator to add users to the Microsoft portal and assign licences to the connected virtual machine or device. If this is not possible, the customer can purchase perpetual licences from their reseller and assign licences by adding licence keys, and then following the QMTH process below.

- Bring your own Windows 10 Enterprise licensing via Qualified MultiTenant Hoster (QMTH). As a Tier 1 direct CSP, UKCloud is an authorised partner on the QMTH program. The QMTH program enables you to purchase Microsoft 10 Enterprise licences and use them on our multi-tenant cloud platform. To bring your own licences, raise a Service Request stating the number of licences and your Microsoft subscription ID.

For more information regarding the QMTH program, we have further details on the [UKCloud web site](https://ukcloud.com/qualified-multitenant-hoster-program/)

If you want to use this option, raise a Generic Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, detailing the VM names.

In addition, you can also bring your own Microsoft desktop licensing for use on a dedicated single tenant cloud server such as Private Cloud. In this instance, contact your Account Director or Service Delivery Manager for further information.

## Options for all other Microsoft applications

As stated, all Microsoft applications on the UKCloud platform must be licensed appropriately by either UKCloud or by using your own existing licensing. There are two options available to you:

- **UKCloud's Microsoft licensing and usage billing.** The standard licensing approach is for us to provide Microsoft licences on a per hour or monthly basis depending on the application. These are retrospectively billed based on your usage of an associated VM for each month. For this option to be valid, you must ensure that you have informed us of all Microsoft installations by raising a Generic Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, detailing the VM names, the application and specific version/level. Not all applications are available using this option, and the Microsoft application list within this document states the eligibility of this option per application.

- **Bring your own Microsoft licensing.** If your organisation has an existing SPLA or Academic licensing contract with Microsoft, or if you want to license your Microsoft software directly, we can offer the option of your organisation using your own Microsoft software licensing.

    > [!NOTE]
    > This is only possible with certain Microsoft applications and is not possible for Microsoft Windows Server as stated above. Before you install any Microsoft software onto a UKCloud VM, you must ensure that you purchase the correct licensing with software assurance and that you have completed the Microsoft Licence Mobility Verification process detailed in this document. The completion of the process is indicated by a signed confirmation sent to you from Microsoft Ireland. If you do not have software assurance, you will not be able to use the Microsoft Mobility option.

    The Microsoft Mobility option involves transferring the use of your licensing to UKCloud VMs, and therefore they cannot be used on other Cloud Service Providers or on your own hardware. However, if you discontinue the use of the application on the UKCloud platform and no longer require the licensing, this can be reverted for your use elsewhere. The [Microsoft Licence Mobility Verification form](https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-license-mobility.aspx) is available on the Microsoft web site. You must complete this form and post it to Microsoft and not to UKCloud. The correct information to use for UKCloud is:

  - Partner entity status: Authorized Mobility Partner
  
  - Authorized Mobility Partner Name: UKCloud
  
  - Authorized Partner Website URL: https://ukcloud.com/
  
  - Authorized Mobility Partner Email Address: licensing@ukcloud.com
  
  - Partner agreement number: 82685361

## Microsoft application list

The following list is aimed at providing you with a summary regarding the licensing options available to you for each specific application. This summary states whether UKCloud licensing and/or Microsoft Mobility is available. This is not intended to be a complete list, but covers the most frequently requested applications. If the application you're looking for is not on this list, engage with your Account Director or Service Delivery Manager who will be able to help and advise you as to whether the software can be licensed and if so how.

- **Microsoft SQL**

  - You don't need to purchase licensing for MySQL, SQL Express or PostgreSQL. However, if you're using SQL Standard or Enterprise for development purposes you're **required** by Microsoft to have valid licensing in place.

  - SQL Developer can only be utilised on a shared platform to test the SQL element of a solution and cannot be used to provide end-user services. If you want to provide SQL services to end-users, SQL Enterprise or SQL Standard must be purchased.

  - We can provide Microsoft SQL Standard Server licences on a per hour basis, Microsoft SQL Enterprise licences billed on a monthly basis or Microsoft SQL Web licenses billed on a monthly basis. These are retrospectively billed based on your usage of an associated VM, and the pricing is available within the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide). Microsoft SQL Web is currently priced at £10.95 per pair of cores per month with a minimum of 4 cores per VM. Note that SQL Web is only for use to support public and internet accessible web pages, sites, applications and services. You cannot use it to support line of business applications (for example, Customer Relationship Management, Enterprise Resource Management and other similar applications).

  - Microsoft Mobility. This is a valid option for both SQL Standard and Enterprise.

  - Under SPLA licensing you only need to purchase the SQL server licence and you do not need to purchase Server Access Licences (SAL).

  - Failover rights. For any operating system environment (OSE) in which you run instances of the server software, you may run up to the same number of passive failover instances in a separate OSE for temporary support. The number of physical and virtual processors used in that separate OSE must not exceed the number of physical and virtual processors used in the corresponding OSE in which the active instances are running. You may run the passive failover instances on a server other than the licensed server. 

- **Office 365**

  - UKCloud licensing. We're now able to provide Office 365 and Microsoft 365 subscriptions on a monthly basis under our CSP agreement. Contact your Service Delivery Manager or raise a Generic Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, stating your Microsoft tenant ID (if available) and the number of subscriptions required.

  - Microsoft Mobility. This is a valid option for Office 365 ProPlus licences as long as you have valid Software Assurance in place. To take advantage of this option, you must manage your Office 365 implementation and ensure you have the correct number of licences to reflect your user count. This option is available via the QMTH program, and more information is available on the [UKCloud web site](https://ukcloud.com/qualified-multitenant-hoster-program/).

  - You can use your subscriptions on the UKCloud platform using our QMTH programme as a direct Tier 1 CSP. Raise a Generic Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, stating your Microsoft tenant ID and the number of subscriptions you want to use.

- **Remote Desktop Server Access Licence**

  There's a separate licence for Windows Remote Desktop Services (RDS) that you'll need to use, as the standard Windows license does not cover RDS. Also note that there's no concurrency within SPLA, so the total number of users provisioned to access the RDS environment will need to be licensed. 

  - UKCloud licensing. We're able to provide Microsoft RDS SAL on a monthly basis only. These are retrospectively billed, and the pricing is available within the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide). To use these licences, you must raise a Service Request prior to their use to register them on the UKCloud platform and provision a dedicated RDS licence server. To assign and validate the licences, we will need to arrange a session to connect to your server.

  - Microsoft Mobility. This is a valid option for RDS licences.

- **System Center**

  - We're unable to offer this on our public cloud platform in any form.
  
  - It's available for customers running dedicated or Private Cloud environments, in which case it can be purchased via UKCloud's SPLA agreement. Please contact Support to arrange for System Center licensing to be implemented on 1 or more of your private hosts.

- **SharePoint**

  - UKCloud licensing. We're not currently able to offer licences for this application.

  - Microsoft Mobility. Sharepoint Server or Sharepoint Server for internet sites can be licensed through Licence Mobility, only if Software Assurance is in place. Once verified by Microsoft you'll be able to use the SharePoint software on the UKCloud platform.

- **Office**

  - UKCloud licensing. UKCloud can offer SALs for this software. You need to inform us as to how many users will be accessing the application and we'll bill you on a per user, per month basis. This pricing is available on request as it is not currently stated in the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide).

  - Microsoft Mobility. This is not available via Microsoft Mobility and must be provided by UKCloud.

- **Visual Studio**

  - UKCloud licensing. UKCloud can offer licensing for this software. You need to tell us how many users will be accessing the software and we'll bill you on a per user, per month basis. The only versions of Visual Studio permitted by Microsoft are Enterprise and Professional.

  - Microsoft Mobility. This is not available via Microsoft Mobility and must be provided by UKCloud.

- **Other Microsoft Products**

  - Engage with your Account Director or Service Delivery Manager who'll be able to help and advise you as to whether the software can be licensed, and if so, how.

## Submitting a request to use Microsoft applications on the UKCloud platform

You must advise us of your preferred method for licensing Microsoft applications.

To use your existing Microsoft licensing or use licences billed by us on UKCloud‑provisioned VMs:

1. Log in to the [UKCloud Portal](https://portal.ukcloud.com/login).

    For more detailed instructions, see the [*Getting Started Guide for the UKCloud Portal*](../portal/ptl-gs.md)

2. In the Portal navigation panel, expand the **Support** option and select **My Calls**.

    ![My Calls menu option](images/ptl-mnu-my-calls.png)

3. Click **Go to My Calls Portal**.

4. Click **New Service Request**.

5. Select **Generic Service Request**.

6. Fill in the Service Request form, making sure to provide the following information in the **Additional Details** field:

    - Whether you want UKCloud to provide licensing or bring your own

    - The specific VDC and VMs to which you want the licensing to apply

    - The software licences, version and quantity you require

    - If want UKCloud to provide licensing, the date from which you want the licensing to commence.

    - If want to bring your own licensing and your Microsoft Mobility application has been accepted, the date from which your licensing will take effect. (You must have completed the [Microsoft Mobility](https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-license-mobility.aspx) verification process before choosing this option.)

    > [!NOTE]
    > It is **your** responsibility to inform UKCloud Support if you rename a VM that has licensing applied or if you no longer require the licensing on one or more of the specified VMs.

7. When you're done, click **Review & Submit**.

## Validation

If you request to use your own licensing, let us know when you have submitted the Microsoft Licence Mobility Verification form and the support team will update our records. As soon as Microsoft confirm with us that the licences are available, your own Microsoft licensing will be utilised. If you were previously using UKCloud-provided SQL licensing, this will be stopped and you will no longer be billed by us for SQL.

Microsoft may contact you to confirm that you have the correct number of licences in place to cover the number of Microsoft-based provisioned VMs supplied by UKCloud.

## Microsoft SQL Server images

To install Microsoft SQL Server Standard or Enterprise edition, you can either use your own local images, or we can make an image available to you. To gain access to any images, you must either inform us so that we can bill you for the appropriate usage, or wait until we've received confirmation from Microsoft as per the mobility process. You can request access to images by raising a Service Request in the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

## Responsibilities

As soon as you've completed the form and the actions have been confirmed, your organisation is responsible for ensuring that there are enough eligible licences to cover the specified Microsoft-based VMs on the UKCloud platform.

## Microsoft audits

Infrequently, Microsoft will require an audit of the SPLA software services delivered by UKCloud. This review is currently undertaken by Ernst & Young (EY), the independent audit firm selected by Microsoft to conduct this process. If you're required to participate in such an audit, you'll receive an email from UKCloud to provide the necessary data.

To fulfil the requirements of this compliance audit and remain in compliance with the SPLA program's rules and requirements, Microsoft will request that you enable UKCloud and EY to gather the necessary information from your restricted-access servers. 

To accomplish this, you'll need to run [EY's Inventory tool Script](https://cas.frn00006.ukcloud.com/Docs/UKCloud_Shared_Services/EY-Inventory-Tool.zip?AWSAccessKeyId=438-1048-5-aefff7-1&Expires=1666373254&Signature=2Xxc8koNzSQ1IdEMhreF8R9%2BMsI%3D), using **Option 2**. After running the script, you should upload the results to UKCloud as per the instructions in the initial email. UKCloud will then handle the obfuscation of data before handing it over to EY. The zip file linked above includes documentation with information about the EY scripts, with Section 3.3 providing specific usage details of how to run and use the script to scan all devices in Active Directory.

> [!NOTE]
> The MBSA signed between Microsoft and UKCloud includes a confidentiality clause, and the provisions of this clause are also applicable to these servers; only data associated to the deployment of Microsoft products will therefore be communicated to Microsoft.

## Support

If you have any issues regarding updating, or the support of Microsoft Server, contact the UKCloud support team by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
