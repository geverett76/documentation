---
title: Oracle cloud self-service functionality
description: Contains information about changes to the self-service functionality for UKCloud for Oracle Software
services: oracle
author: Sue Highmoor
reviewer: bchallis
lastreviewed: 16/11/2021
toc_rootlink: UKCloud for Oracle Software
toc_sub1: Reference
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Oracle cloud self-service functionality
toc_fullpath: UKCloud for Oracle Software/Reference/orcl-ref-bug-self-service.md
toc_mdlink: orcl-ref-bug-self-service.md
---

# Oracle cloud self-service functionality

> [!IMPORTANT]
> UKCloud for Oracle Software has been retired from sale by UKCloud. We'll continue to support all existing customers who are using this service, however, we are no longer providing this service for new workloads. This article provides existing UKCloud for Oracle Software customers with access to support documentation and we'll continue to update it as required. For new Oracle requests, contact your Client Director or Service Delivery Manager.

## Overview

Due to a bug that has been identified within the Oracle cloud placement engine, until further notice, customers on the Oracle cloud will be unable to perform the following tasks through the Oracle cloud portal:

- Create new VMs

- Modify the compute and storage resources available to existing VMs

Until this issue is resolved, we ask that customers raise a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal so that UKCloud can provision Oracle VMs and VM resources on your behalf.

> [!NOTE]
> All other features within the Oracle portal will continue to function as normal. However, if you do experience any issues, raise a support request so that we can investigate.

We apologise for the inconvenience caused; we are working towards a solution as quickly as we can.

In the meantime, this means information in the following articles relating to VM creation and modification should not be followed, and a Service Request should be raised instead:

- [*How to build an Oracle virtual machine*](orcl-how-build-vm.md)

- [*Getting Started Guide for UKCloud for Oracle Software*](orcl-gs.md)

## Raising a Service Request

### New VMs

When raising a Service Request for new Oracle VMs, we require the following information:

- Customer environment

- UKCloud template (if required)

- CPU

- RAM

- OS (if required)

- Storage disks required (T1/T2 and sizes)

## Additional resources on existing VMs

When raising a Service Request for additional resources on existing Oracle VMs, we require the following information:

- Customer environment

- VM name

- Resource change required (CPU, RAM, disk)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
