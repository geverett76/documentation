---
title: Private Cloud Storage FAQs
description: Frequently asked questions for Private Cloud Storage
services: private-cloud
author: mwarner
reviewer: gmartin
lastreviewed: 26/09/2022
toc_rootlink: FAQs
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Private Cloud Storage FAQs
toc_fullpath: FAQs/prc-faq-storage.md
toc_mdlink: prc-faq-storage.md
---

# Private Cloud Storage FAQs

## Service

### What is the service?

Private Cloud Storage provides single-tenant storage Infrastructure as a Service. Your data is hosted in one of our UK data centres; or in your Crown Hosting Data Centre (CHDC).

### How does Private Cloud Storage differ from UKCloud's Cloud Storage?

The Platform Only package in Private Cloud Storage provides you with the underlying Assured Cloud platform to host and manage dedicated storage hardware. You can arrange your own purchase of it, or UKCloud can broker it for you.

This service differs from Cloud Storage in that it allows you to purchase in bulk up front, to reduce the price per GiB.

### What backup/disaster recovery options do I get?

You can choose between two protection levels:

- STANDARD provides protection in one data centre

- ENHANCED provides remote protection in our second data centre

### Where will my data be physically stored?

Your data will be stored in our highly resilient, UK-sovereign tier 3 data centres, which are separated by over 100km.

### How much data can I store?

A core benefit of Private Cloud Storage is that it can scale to meet the most demanding storage requirements.

### What network protocols are supported on the platform?

There is native support for a wide variety of network protocols including SMB/CIFS, NFS, HTTP and, optionally, HDFS.

## Management

### How do I access the platform?

Documentation on ways to interact with the platform is available from the UKCloud Portal Knowledge Centre.

### What software tools are available?

Advanced software features for Private Cloud Storage include auto-tiering, deduplication, retention, replication, quotas and snapshots.

## Support

### How do I raise a support ticket?

UKCloud's secure online Portal provides the most common service management functionality. Alternatively, you can contact support by phone or email.

### How do I manage my services?

Private Cloud Storage on the Assured OFFICIAL domain can be managed over the internet (or other connectivity) by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

For the Elevated OFFICIAL domain, the security requirements are much stricter and require either a PSN-approved connection, UKCloud Secure Remote Access, or CAPS-approved encryption.

### What are your service maintenance windows?

See [*Understanding UKCloud service maintenance windows*](../other/other-ref-maintenance-windows.md).

## Onboarding

### How can I get started with the service?

On acceptance of your order, we'll work with you to create a detailed design for your Private Cloud Storage service. The design will formalise the dedicated components required for the solution, including storage hardware, storage software, network hardware and cables.

If this is a new service for you, we will create your primary administrator account and send you a welcome pack, which includes the URL for the UKCloud Portal for access to the Knowledge Centre and service management function.

## Billing and legal

### What is the smallest unit of time I will be billed for?

Billing depends on the packaging option chosen. The smallest unit of time you will be billed for this service is monthly.

Private Cloud Storage is offered under a 24-month minimum term commitment.

### How can I pay for the services?

Service charges are billed monthly in arrears. In addition, there will be initial upfront charges, which vary depending on the pricing model selected.

Payment can be made by direct bank transfer (BACS/CHAPS).

### How can I view billing information?

Billing information is available via the UKCloud Portal.

### What are the termination fees?

An early exit charge will be payable if the contract is terminated before the end of its original term. You are responsible for extracting their data from the platform if required.

UKCloud may make an additional charge for transferring data out of the service.

### Is there a free trial?

Owing to the dedicated, single-tenant nature of this service, no trials are available.

## Security

### What data is suitable for your cloud?

This service is hosted in the UK and operated by SC-cleared staff. It has extensive independent validation (including CESG design reviews) that it is fully aligned with the 14 NCSC Cloud Security Principles, and is therefore ideal for all data classified at OFFICIAL (including OFFICIAL SENSITIVE) and legacy IL0--IL4 solutions.

### Can systems on different UKCloud platforms communicate with one another?

UKCloud's Cross Domain Security Zone allows you to use a customer-designed and managed Walled Garden, to enable communication between platforms.

For more information, see the [Cross Domain Security Zone Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-230-cross-domain-security-zone-service-definition-13.0-1.pdf).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
