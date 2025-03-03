---
title: How to access UKCloud services from Walled Garden and Secure Remote Access
description: Shows how to access UKCloud services (such as WSUS, KMS or Red Hat Update Service) from Secure Remote Access or a Cross Domain Security Zone Walled Garden solution
services: cdsz
author: shighmoor
reviewer: ecorfield
lastreviewed: 18/09/2020

toc_rootlink: Cross Domain Security Zone
toc_sub1:
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Access UKCloud services from Walled Garden and Secure Remote Access
toc_fullpath: Cross Domain Security Zone/cdsz-how-access-services-walled-garden.md
toc_mdlink: cdsz-how-access-services-walled-garden.md
---

# How to access UKCloud services from Walled Garden and Secure Remote Access

## Overview

If you've implemented either Secure Remote Access (SRA) or a Cross Domain Security Zone (CDSZ) Walled Garden solution and want to access UKCloud services (such as WSUS, KMS or Red Hat Update Service), you'll need to edit your edge gateway settings to enable access.

### Intended audience

To complete the steps in this guide you must have VMware Cloud Director administrator access to a virtual data centre (VDC) in the Elevated OFFICIAL security domain.

## Before you begin

Before making network changes to your environment, you'll need the following information:

- The Transit IP for the Elevated edge gateway of your CDSZ or SRA VDC

- The Transit IP for the edge gateway of your Elevated VDC

- The IP of the service you require.

To get the last two octets of the IP addresses for the service you require, raise a Service Request on the UKCloud Elevated Portal.

## Setting up access to UKCloud services

You need to add two static routes and an SNAT rule on two edge gateways.

1. In VMware Cloud Director, locate the edge gateway that is attached to the Elevated side in your CDSZ or SRA VDC.

2. Create a static route that directs traffic for the service you need via the Transit IP of your Elevated edge gateway.

    For more detailed instructions, see [*How to create a static route*](../vmware/vmw-how-create-static-route.md).

3. Create an SNAT rule on your Elevated VDC to allow the private IP range from your CDSZ or SRA to have external access.

    For more detailed instructions, see [*How to create NAT rules*](../vmware/vmw-how-create-nat-rules.md).

4. Amend the firewall to allow the private IP range access to the service you require on your Elevated VDC.

    For more detailed instructions, see [*How to create firewall rules*](../vmware/vmw-how-create-firewall-rules.md)

5. Add a static route for the return traffic on your Elevated VDC to point to the Transit IP of your CDSZ or SRA VDC.

## Next steps

Now that you've set up access to UKCloud services, you can register your VMs with those services. For more information, see:

- [*How to license Windows VMs using the UKCloud Key Management Server*](../shared/shared-how-setup-kms.md)

- [*How to connect to the UKCloud Windows Server Update Services (WSUS)*](../shared/shared-how-connect-windows-update.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
