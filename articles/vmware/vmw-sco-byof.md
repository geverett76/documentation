---
title: Bring Your Own Firewall Service Scope
description: Outlines important details regarding Bring Your Own Firewall
services: other
author: shall
reviewer: swthomas
lastreviewed: 19/10/2021
toc_rootlink: Service Information
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Bring Your Own Firewall Service Scope
toc_fullpath: Service Information/vmw-sco-byof.md
toc_mdlink: vmw-sco-byof.md
---

# Bring Your Own Firewall Service Scope

## About this document

This document is intended for UKCloud customers who might be considering an alternative virtual firewall or virtual appliance to the presently integrated NSX Edge Services Gateway device within VMware Cloud Director.

The scope of the document is not to provide step by step detail on how to setup or install an alternative virtual firewall but rather the key points that a customer should consider when choosing an alternative product.

The document describes the responsibilities of both UKCloud and the customer in order to facilitate the changes required.

## About Bring Your Own Firewall

Bring your own firewall enables customers to customise their networking infrastructure by installing their own virtual firewall appliance in place of the NSX Edge Services Gateway device UKCloud includes as standard with its compute services.

This can enable customers to leverage their own in-house expertise with a particular technology or can provide access to some higher level networking functionality not natively available in the NSX Edge Services Gateway device.

## Default setup

Presently UKCloud only offers a "bring your own firewall" installation to new VDCs.

In a BYOF implementation, UKCloud present an external network directly to the customer, who can then install the firewall instance of their choice.

## UKCloud responsibilities

Upon a customer's request, UKCloud will:

- Deploy a new VDC without an NSX Edge Services Gateway device

- Present the external network to the customer for them to install their own firewall device

Once the customer has installed their own firewall device, UKCloud will continue to:

- Manage platform availability

- Manage the external network

## Customer responsibilities

By requesting to have the edge gateway device removed and their own firewall technology installed, the customer accepts that:

- Customers are responsible for sourcing their own licensing arrangement with the 3rd party firewall provider.

- Customers are responsible for installing and configuring the firewall device.

- UKCloud do not offer any support of customer installed firewall replacements. This includes but is not limited to install, configuration and troubleshooting issues.

- UKCloud will not be able to perform any network diagnostic tasks on the customer side of the firewall (inside the VDC).

- Outages caused by the customer's new firewall will not be liable to Service Credit claims.

- Customers lose the visibility of the IP address assignments which are currently easily referenced within VMware Cloud Director.

- Customers lose the integrated functionality of configuring the edge gateway device through VMware Cloud Director. Access to the new firewall replacement is only available via the console or from within the customer VDC (based on setup).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
