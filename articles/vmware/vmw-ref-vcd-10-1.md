---
title: Changes in VMware Cloud Director 10.1
description: Provides information about the changes in VMware Cloud Director 10.1
services: vmware
author: shighmoor
reviewer: swthomas
lastreviewed: 09/11/2021
toc_rootlink: Reference
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Changes in VMware Cloud Director 10.1
toc_fullpath: Reference/vmw-ref-vcd-10-1.md
toc_mdlink: vmw-ref-vcd-10-1.md
---

# Changes in VMware Cloud Director 10.1

## Overview

This article provides information about the changes introduced in VMware Cloud Director 10.1.

## New features

VMware Cloud Director 10.1 provides the following new features.

- UI enhancements in the HTML5 Tenant Portal:

  - Hamburger bar replaced with a menu bar

  - New Applications menu to manage vApps and VMs across data centres

  - New vApp and VM card design

  - New Resources view for VMs and vApps

  - Ability to change the catalog owner

  - Ability to edit the OVF properties of a vApp and VM

  - Option to power on a vApp after vApp deployment

  - vApp templates are differentiated from unexpired templates with a new grid column

  - External IP is showing on the vApp details page

  - Ability to delete Shadow VMs

- Terraform VMware Cloud Director Provider, updated to version 2.8, enables you to access infrastructure-as-code

For more information about new features in VMware Cloud Director 10.1, see <https://docs.vmware.com/en/VMware-Cloud-Director/10.1/rn/VMware-Cloud-Director-101-Release-Notes.html>.

## Legacy UI

The Legacy UI is no longer available in VMware Cloud Director 10.1. All tasks can now be performed using the HTML5-based Tenant Portal, removing the requirement for the Flash browser plugin.

## Browser support

VMware Cloud Director 10.1 is compatible with the current major and previous major releases of the following browsers:

- Google Chrome

- Mozilla Firefox

- Microsoft Edge

- Microsoft Internet Explorer 11

## Changes to APIs

### Supported API versions

VMware Cloud Director 10.1 supports the VMware Cloud Director API version 34.0 (see <https://code.vmware.com/apis/912/vmware-cloud-director>). For information about the changes to the VMware Cloud Director API for this version, see [VMare Cloud Director API Schema Differences](https://code.vmware.com/apis/912/vmware-cloud-director/doc/diff/index.html).

VMware Cloud Director 10.1 is the last release of VMware Cloud Director to support vCloud API 30.0. The 30.0 and 31.0 versions of the API are deprecated in this release and will not be supported in future releases.

The following API versions are still available:

- 30.0 (deprecated)

- 31.0 (deprecated)

- 32.0

- 33.0

- 34.0

### Changes to API URL

The format of the VMware Cloud Director API URL has changed from `api.vcd.xxx` to `vcd.xxx`. You can find the Cloud Director API URL for your service in the UKCloud Portal. For more information, see [*How to access VMware Cloud Director through the Cloud Director API*](vmw-how-access-vcloud-api.md).

### Sandbox for testing Cloud Director API

UKCloud provides sandboxes to enable you to test the next versions of the Cloud Director API so that you can prepare for VMware Cloud Director upgrades. Our latest sandbox (<https://vcd.latest.ukcloud.com/login/>) has been upgraded to VMware Cloud Director 10.1.2.

To gain access to the sandbox, raise a Service Request via My Calls on the UKCloud Portal.

> [!NOTE]
> Some VMware Cloud Director features may be available in the sandbox that will not be enabled in UKCloud for VMware after the 10.1 upgrade. If there's a 10.1 feature that you're particularly interested in, contact your Service Delivery Manager to register interest so that we can consider it for our roadmap.

## Known issues

Known issues you may experience following the upgrade to VMware Cloud Director 10.1 include:

### Known issues in VMware Cloud Director

See [*Known issues in VMware Cloud Director*](vmw-ref-vcd-known-issues.md).

### Known issues in the UKCloud Portal

- Changes to the Cloud Director authentication API mean that the UKCloud Portal function to restrict IP access to the API also restricts access to the VMware Cloud Director Tenant Portal (see [*How to restrict access to VMware Cloud Director*](../portal/ptl-how-restrict-access-vcloud-api.md)). If you have set up these restrictions, you'll need to confirm that the additional restriction of access to the Tenant Portal does not cause issues.

- Changes to the Cloud Director API mean that we are no longer able to display VM storage information in the My VMs area of the UKCloud Portal. Instead, you can access storage usage information within the VMware Cloud Director Tenant Portal (see [*How to view storage profile usage*](vmw-how-view-storage-usage.md)).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
