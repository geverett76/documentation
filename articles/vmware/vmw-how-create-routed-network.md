---
title: How to create a routed VDC network
description: Shows how to create a routed VDC network using VMware Cloud Director
services: vmware
author: shighmoor
reviewer: shighmoor
lastreviewed: 20/09/2022

toc_rootlink: How To
toc_sub1:
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Create a routed VDC network
toc_fullpath: How To/vmw-how-create-routed-network.md
toc_mdlink: vmw-how-create-routed-network.md
---

# How to create a routed VDC network

## Overview

An organisation virtual data centre (VDC) network enables its virtual machines (VMs) to communicate with each other or to provide access to external networks. A single VDC can have multiple networks.

There are two types of organisation VDC networks:

- An isolated (internally connected) network is one that only VMs within the VDC can connect to. Creation of isolated networks is described in [*How to create an isolated VDC network*](vmw-how-create-isolated-network.md).

- A routed network (externally connected) provides access to machines and networks outside the VDC via the edge gateway. You can have up to nine usable routed networks per VDC. This article describes how to create a routed VDC network.

## Creating a routed VDC network

1. In the VMware Cloud Director *Virtual Data Center* dashboard, select the VDC in which you want to create the network.

2. In the left navigation panel, under *Networking*, select **Networks**.

   ![Networks tab in VMware Cloud Director](images/vmw-vcd10.1-mnu-networks.png)

3. Click **New**.

   ![New network button](images/vmw-vcd10.1-btn-new-network.png)

4. On the *Scope* page of the *New Organization VDC Network* dialog box, **Current Organization Virtual Data Center** should already be selected, so click **Next**.

5. On the *Network Type* page, select **Routed**, then click **Next**.

   ![New Organization VDC Network dialog box - Network Type page - Routed network](images/vmw-vcd10.1-new-network-routed-type.png)

6. On the *Edge Connection* page:

   - Select the edge gateway that you want your network to connect to.

   - From the **Connection Type** list, select **Internal**.

     > [!NOTE]
     > For information about **Distributed** networks, see [*How to configure a Distributed Logical Router*](vmw-how-configure-distributed-logical-router.md). For information about creating a routed network as a **Subinterface** for L2 VPN, see [*How to configure an L2 VPN*](vmw-how-configure-l2-vpn.md).

   - Select the **Guest VLAN Allowed** option to enable tagging of guest VLANs on this network.

   ![New Organization VDC Network dialog box - Edge Connection page](images/vmw-vcd10.1-new-network-routed-edge.png)

7. Click **Next**.

8. On the *General* page:

   - Enter a **Name** and **Description** for the network.

   - In the **Gateway CIDR** field, enter the gateway address for the network.

   - Select the **Shared** option to make the network available to other VDCs within the same organisation.

   ![New Organization VDC Network dialog box - General page](images/vmw-vcd10.1-new-network-general.png)

9. Click **Next**.

10. On the *Static IP Pools* page, in the **Static IP Pools** field, enter a range of addresses to be consumed by the VMs connecting to the network, then click **Add**.

    As an example, if you give the gateway address as `192.168.1.1/24`, you may then want to create a static IP pool of `192.168.1.10-192.168.1.100`. This will give you a pool of 91 IP addresses to assign to machines within your network. You can always increase this later if needed.

    You can add multiple IP pools.

    ![New Organization VDC Network dialog box - Static IP Pools page](images/vmw-vcd10.1-new-network-ip-pool.png)

11. Click **Next**.

12. On the *DNS* page, enter DNS information if applicable, then click **Next**.

    ![New Organization VDC Network dialog box - DNS page](images/vmw-vcd10.1-new-network-dns.png)

13. On the *Ready to Complete* page, review your selections then click **Finish**.

## Next steps

Now you've created your network to connect your VDC with the outside world, you may want to configure your edge gateway to control what traffic is allowed into and out of your VDC. You may also want to start building some VMs. For a walkthrough on how to do this, see [*How to build a virtual machine with UKCloud for VMware*](vmw-gs-build-vm-vcd.md).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
