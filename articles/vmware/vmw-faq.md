---
title: UKCloud for VMware FAQs
description: Frequently asked questions for UKCloud for VMware
services: vmware
author: mwarner
reviewer: gmartin
lastreviewed: 26/05/2022
toc_rootlink: FAQs
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: UKCloud for VMware FAQs
toc_fullpath: FAQs/vmw-faq.md
toc_mdlink: vmw-faq.md
---

# UKCloud for VMware FAQs

## Service

### What is the service?

UKCloud for VMware is an Infrastructure as a Service (IaaS) offering that enables organisations to rapidly provision and scale secure virtual machines (VMs) in minutes, in a flexible and autonomous manner.

UKCloud provides this service across two security domains, Assured OFFICIAL and Elevated OFFICIAL, and with a range of service levels offering up to 99.99% availability. This choice enables customers to precisely match application and user needs to an appropriate security domain, service level and cost, instead of designing to the highest level which may not always be needed.

### Can VMs have different characteristics?

Yes. We offer three VM Types: ESSENTIAL, POWER and PRIORITY.

VM characteristics are inherited from the virtual data centre (VDC) the VM is deployed in. It is not currently possible to have a VDC that has mixed VM types.

However, customers can use multiple VDCs to deliver their solution.

### Are VMs contended?

ESSENTIAL VMs are contended: VMs contend for memory and processor resources.

POWER & PRIORITY VMs: UKCloud has implemented a combination of technical and process controls (for example, an ISO 20000-certified capacity management process) to ensure that these VMs don't contend for memory or processor resources.

POWER VMs operate where automated rebalancing is enabled to pre-emptively optimise performance and availability.

PRIORITY VMs differ from other VM types. Automated rebalancing is configured to reduce workload movement around the platform, reducing workload disruption.

### Can a VM communicate to another VM of a different type?

Yes. VMs can communicate with each other. In some cases, customers may need to use the built-in self-service IPsec VPN functionality to create a virtual private network within our Assured cloud platform.

### Can VMs types be changed?

Yes, but the customer must first export the VMs, then import them back into the VDC that has been created with the target VM type.

### Can I convert from one VM type to another, without having to move VMs between vDCs?

Customers can manage the migration between VM types. Customers can also move vApps and VMs between VDCs as long as they're in the same assurance domain, for example Assured to Assured.

More complex migrations, from the Assured to the Elevated security domain, must be managed by UKCloud.

If you want to migrate a vApp larger than 1.5TiB, you'll need to engage the UKCloud support team to facilitate the process. To do so, raise a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

### What hypervisor do you use?

UKCloud's environment is built using VMware vSphere, the most ubiquitous and mature hypervisor available. Secure multi-tenancy is achieved with VMware Cloud Director.

### Can I have a read-only account in vCloud for monitoring?

This is available on the UKCloud Portal under permissions that can be set by your account administrator.

## Virtual machines (VMs)

### Do I get root access onto the local VM?

Yes, as this is a true IaaS cloud service, you have complete control and autonomy over each VM, and so have full *root* or administrative access.

### What VM sizes are available?

UKCloud offers a variety of *T-shirt sizes* to meet customers' needs. The smallest configuration is 0.5GiB and 1 vCPU. The largest is 128GiB memory with 12 vCPU.

Check the [UKCloud for VMware Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-244-ukcloud-for-vmware-service-definition-13.0.pdf) for more details on the currently available sizes.

> [!NOTE]
> UKCloud for VMware does not currently support custom-sized VMs outside the T-shirt sizes, however if you require more flexibility with regards to VM sizes, we advise the use of our other multi-cloud technologies such as OpenStack, Oracle or Azure. Alternatively, you may consider the use of [Dedicated Compute v2](https://ukcloud.com/app/uploads/2022/08/ukc-svc-227-dedicated-compute-v2-service-definition-13.0.pdf) to build custom-sized VMs.

### Can I resize a VM?

Yes, you can change vCPU, RAM and storage allocations via the self-service vCloud Director/VMware Cloud Tenant Portal and vCloud API.

You can add or remove processors and memory from VMs if the OS supports the 'hot add' capability.

Increasing CPU or memory allocations may result in the VM being billed at a higher rate.

Additional VM storage can be allocated instantly and will be billed on a per GiB basis.

### What is the speed of each vCPU?

This is set at 2GHz for all VMs except Micro sized VMs, which can be restricted to run at 500MHz.

### What is the fastest way of importing large amounts of data onto the UKCloud platform?

The speed of data transfer to the UKCloud platform isn't guaranteed. However, during tests of the upload and download speeds, an average of 8 Mbit/s was achieved for VM import/export and 40 Mbit/s for data transferred over FTPS.

For a transfer time calculator, go to: <https://techinternets.com/copy_calc?do>

If you use FTPS to upload data to or download it from your environment, you can transfer up to 1TiB of data in a day.

Alternatively, we offer the Mass Transfer Facility option enabling customers to import large quantities of data via NAS, HDD or USB devices that are plugged directly into your environment. Please check the [*Mass Transfer Facility Service Scope*](../enablement/enbl-sco-mtf-nas.md) or the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide) for further details.

### Does UKCloud offer encryption on the VM?

UKCloud for VMware provides always-on data at rest encryption (D@RE) in Regions 13 and 14.

In other regions UKCloud can supply licensing for HyTrust DataControl. Alternatively, you can implement encryption using the technology of your choice inside the VM's operating system.

### Does your data at rest encryption solution provide FIPS 140-2 or Common Criteria certification?

We use Pure Storage for our data at rest encryption solution in regions 13 and 14, which is FIPS 140-2 and Common Criteria certified.

### Is UKCloud's encryption service available for UKCloud for VMware?

Not currently as a service (see above). We're considering this as an option, so please provide feedback by sending an email to <feedback@ukcloud.com>.

### Is it possible to non-fast-provision vApps, and to convert current vApps into non-fast-provisioned ones?

Fast provisioning is enabled only by customer request - by default, all vApps are non-fast-provisioned. Customers can right-click on a VM and consolidate. This can also be done by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

### What is Dedicated Compute?

Dedicated Compute comprises physical hosts assigned to a customer for their sole use. They're managed using the standard tools and services in the UKCloud platform.

Dedicated Compute enables customers to:

- Comply with legacy licensing requirements from software suppliers whose licensing is based on a physical CPU (such as Oracle or desktop operating systems)

- Build bespoke sized VMs on the UKCloud platform

Dedicated Compute uses the same storage infrastructure as the shared compute platform.

There's a longer deployment lead time for Dedicated Compute, as well as a longer contractual commitment than our shared cloud platform (one month rather than one hour).

For more details, see the [Dedicated Compute v2 Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-227-dedicated-compute-v2-service-definition-13.0.pdf).

> [!NOTE]
> Dedicated Compute is available only in UKCloud regions 5 and 6.

### Can I utilise multiple storage types with my VM?

UKCloud offers two storage types to customers:

- Tier 1 which is a fast storage offering

- Tier 2 which is a standard storage offering

With Tier 1 and Tier 2 storage, customers can utilise both types to deliver their solutions - including running VMs utilising disks on different storage types.

### Can I change between storage types associated with the VMs I've deployed?

If a customer has both Tier 1 and Tier 2 storage profiles available, they can self-migrate between these storage types.

### What happens when I switch off my VMs using the guest operating system?

If you shut down your VM using the guest OS, we will recognise this as a 'Power Off' event and you will not be billed while the VM remains in this state. Billing will resume once the VM is powered on again.

### How do I change the workload type of a VDC?

To change the workload type (for example, ESSENTIAL, POWER or PRIORITY) of a VDC, you must raise a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, and the support team will make the necessary changes.

Please note this change is disruptive and UKCloud will be required to power down all VMs in the VDC during this transition.

## Networking

### How many IP addresses do I get?

You're initially allocated five external IP addresses with a new compute service.

You can ask for more external IP addresses by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal. Please note that there is a £20 charge per additional IP address.

There's no limit to the number of internal IP addresses (RFC1918) you can allocate.

### How many PSN IP addresses do I get?

Customer organisations are initially allocated one external PSN IP address.

You can request additional external PSN IP addresses by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal should a valid business requirement arise. Please note that there is a £20 charge per additional IP address.

There's no limit to the number of internal IP addresses (RFC1918) customers can allocate.

### What firewall services are available?

UKCloud controls and manages a perimeter firewall on the edge of our Assured cloud platform which securely segregates traffic. Within the UKCloud for VMware environment, we provide you with a dedicated self-managed virtual firewall that delivers typical firewall functionality such as access control lists and network address translation, as well as basic load balancing and support for VPNs.

You can also use your preferred firewall and security appliances, as long as they're compatible with the VMware virtual infrastructure used to power the UKCloud Assured cloud platform.

UKCloud also offers the additional benefits of a Distributed Firewall (DFW). An advanced security feature, DFW enables you to create security groups based on VM names, IP address and groups, which in turn enable the creation of firewall rules that are pinned to the VM. This makes firewall rules portable and simplifies the configuration and application. DFW is part of UKCloud for VMware's Advanced Management bundle.

### How do I create and manage firewall rules?

Your UKCloud-provided dedicated virtual firewall is managed exclusively by you. You can set and manage firewall rules via the VMware Cloud Director tenant portal and vCloud API.

On-boarding guides and associated video tutorials are available to help customers configure and manage their firewalls.

### Can I bring my own firewall?

Customers can choose to deploy the firewall technology of their choice.

This service, how to order it, and the constraints it may place on operation, is fully documented within our Knowledge Centre.

### What is the Advanced Management bundle?

The Advanced Management bundle includes Distributed Firewall (DFW), Distributed Logical Router (DLR), Layer 2 VPN and vROPs Tenant Monitoring and Metrics.

> [!NOTE]
>
> - The Advanced Management bundle may not be available in all regions and zones.
>
> - The bundle is enabled at an organisation (vOrg) level, therefore all VMs within the organisation will be uplifted. See the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide) for details.

### How does UKCloud provide urgent maintenance notifications and incident reports?

You can view these, as well as general service status information on the [UKCloud Service Status page](https://status.ukcloud.com/).

### Do you offer dynamic or static IP addresses?

The external IP addresses are static. Internal IPs can be assigned statically from a pool, manually or dynamically via DHCP.

### Are external Domain Name System (DNS) services available?

No, we don't currently offer this service. You can implement your own DNS servers within your solution, or configure your virtual firewall to enable connectivity to an externally hosted DNS server - for example, one hosted on a government secure network such as PSN, Janet or HSCN; or one available on the Internet such as Google `8.8.8.8`.

### Are domain name registration services available?

No, we don't currently offer this service. Some government secure networks (such as PSN and HSCN) offer domain name registration and DNS hosting as part of their service.

For internet-facing services a third-party DNS provider will be required.

### Is Network Time Protocol available for time synchronisation?

Yes, this is available for Assured OFFICIAL and Elevated OFFICIAL. See [*Network Time Protocol server access*](../shared/shared-ref-network-time-server.md) for details.

### Can UKCloud provide SSL certificates or can existing SSL certificates be used?

UKCloud doesn't provide SSL certificates, but you can use your existing ones.

Some government secure networks (such as PSN and HSCN) provide SSL certificates as part of their service.

### Do you offer load balancing?

Yes, you can configure load balancing within the service and it is included within the price.

- Supported protocols: HTTP, HTTPS, TCP.

- Supported algorithms: Round Robin, IP Hash, URI, Least Connected.

### Can I deploy my own load balancer?

Yes, you can deploy your own load-balancing virtual appliance (for example, F5, Stingray, Zeus) if support for other algorithms is required.

In addition, UKCloud offers Neustar UltraDNS from UKCloud - an authoritative DNS and global load balancing service, which you can customise for your own specific requirements. An [*FAQ*](../connectivity/conn-faq-glb.md) and [*Service Scope*](../connectivity/conn-sco-glb.md) are available in the Knowledge Centre.

## Storage

### How much storage do I get with a VM?

A VM comes with a default amount of 60GiB of Tier 2 storage.

The exception is Micro sized VMs. These have a fixed 10GiB allocation that cannot be increased. If this allocation is exceeded, the VM is treated as Tiny.

### Can I reallocate storage across VMs?

No, storage pooling isn't possible. Each VM must have a minimum of 60GiB (except Micro VMs).

You can quickly and easily allocate additional storage via the self-service VMware Cloud Director tenant portal or vCloud API. Additional storage is charged on a per-GiB basis as listed in the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide).

### Is storage persistent?

Yes, unlike some other cloud platforms, storage is persistent.

This means that your data and VM configuration remain available to you even if the VM is switched off or restarted.

### What is the Tier 1 storage solution?

Tier 1 storage is designed for the following scenarios:

- Applications that require improved performance when accessing stored data such as high activity databases

- Applications that have irregular usage patterns that require a consistent performance such as data warehouses or batch process applications

Existing applications can take advantage of Tier 1 storage. A migration process may be involved.

Tier 1 storage is available for use with all VM types and compatible with all protection technologies.

Talk to your UKCloud Account Director or Cloud Architect to understand if Tier 1 storage can benefit your solution.

### What are independent disks?

Independent disks are a technology provided natively by VMware Cloud Director, and are included as options by default in the UKCloud service. They can only be created via the API, and cannot be created though the user interface. UKCloud has provided some advice on how to create and control them [here](https://github.com/UKCloud/vcloud-independent-disks).

Independent disks are stand-alone virtual disks that you create in organization VDCs. Administrators and users who have adequate rights can create, remove, and update independent disks, and connect them to virtual machines.

When you create an independent disk, it is associated with an organisation VDC but not with a VM. After the disk has been created in a VDC, the disk owner or an administrator can attach it to any VM deployed in that VDC. The disk owner can also modify disk properties, detach it from a VM, and remove it from the VDC. The system administrator and organisation administrator of the organisation that contains the VDC have the same rights to use and modify the disk as the disk owner.

Only one VM can be connected to an independent disk at a time.

### Why have independent disks started to appear on my bill?

Previously, independent disks appeared on customer invoices when they were actively attached to a VM. This meant that customers continually mounting and dismounting independent disks may not have seen the true size of their UKCloud for VMware environment.

We have improved our reporting to advise customers of the independent disks they have currently created, and the amount of storage associated with those disks, and the monthly cost associated with those disks.

### What if I use my independent disks with the same VM all the time?

We advise that you move the data in the independent disk into a disk associated with a single VM. This will enable you to take advantage of the free 60GiB of storage included with all UKCloud VMs.

### What rate are independent disks charged at?

Independent disks will be charged at the rate of the storage they are stored on, along with any additional protection applied (Journaling or Snapshot Protection) and charged at a rate per GiB per month.

### Can I use the 60GiB included with my VM on an independent disk?

No, as an independent disk can be mounted to any VM inside a customer's VDC, so is not associated with a single VM.

## Management

### How do I access my systems?

You can access your VMs using:

- The remote console through the UKCloud Portal

- Remote access protocols (RDP/SSH) over a VPN or secure network

### What reports can I get about VM performance?

You can monitor VM performance using standard tools within the operating system.

Additionally, UKCloud provides retrospective performance information via its Portal API.

The Advanced Management bundle for UKCloud for VMware includes advanced monitoring options, powered by the vRealize Operations (vROps) Tenant Appliance, that provide access to more detailed metrics and reports. For more information, see [*How to access advanced monitoring using the vRealize Operations Tenant Appliance*](vmw-how-vrops-use.md).

### Does UKCloud patch the VMs?

No, customers are responsible for the patching of their services. We make a patch repository available to customers for VMs on the Elevated OFFICIAL security domain (which cannot connect to the internet) for common operating systems that we provide.

### How do I access support and patches for operating systems that UKCloud licenses?

UKCloud provides a repository of patches for common operating systems for customers to access and update from. Please refer to the Knowledge Centre for details.

For support, you'll need to log a request with UKCloud, who will log the ticket with the relevant supplier. UKCloud will then inform you about any updates. However, UKCloud isn't responsible for the actual resolution of non-IaaS issues.

### Do you have a Key Management System (KMS) for activating Windows?

Yes, a step-by-step guide on configuring and using this service is included in [*How to license Windows VMs using the UKCloud Key Management Server*](../shared/shared-how-setup-kms.md).

### How do I control a VM?

You control a VM via the VMware Cloud Director tenant portal or vCloud API. Controls include stop, start, restart, load media, clone, snapshot, and so on.

### Do you monitor VMs?

UKCloud monitors the underlying platform but doesn't monitor customers' operating systems or applications. Customers can implement their own application performance monitoring solutions within the VDC.

### Do you offer autoscaling?

There's no standard product offering for autoscale, but the platform API can be used to do this with a little developer effort.

### How quickly can I scale my service up or down?

Horizontal scale can be achieved quickly by adding additional VMs (usually in just a few minutes). Vertical scaling can be achieved by 'hot adding' vCPU or RAM to a VM (where supported by the guest OS). This operation usually takes seconds.

## Licensing, software and anti-virus

### What operating systems are available?

UKCloud UKCloud for VMware is powered by VMware technology, so is compatible with a wide range of x86/x64 operating systems.

VMware provides a compatibility matrix at: <https://partnerweb.vmware.com/comp_guide2/pdf/VMware_GOS_Compatibility_Guide.pdf>.

You can use the UKCloud catalog of operating systems or upload your own.

We offer Windows Server 2012, Windows 2016, Red Hat Enterprise Linux and CentOS.

> [!NOTE]
> On 14 January 2020, Microsoft ended support for Windows Server 2008, therefore we highly recommend that you upgrade to Windows Server 2012 or Windows Server 2016 to remain secure. 

In addition, we provide access to common templates provided by the Bitnami service such as Drupal, Joomla, LAMP and Wordpress.

### How can I license an operating system?

### Microsoft

Microsoft terms and conditions preclude customers from using their own licence agreements for Windows Server in the Cloud. That means all licensing for Windows Server operating systems must be provided by UKCloud.

Microsoft offers License Mobility, a scheme that allows a customer to provide additional software such as Exchange, SQL and so on, as long as the customer has appropriate Microsoft licensing as per the licence terms and conditions and usage rights. In order to use License Mobility, you must complete the form that is available in the from the Microsoft web site and send this by post to Microsoft. For more information, see [*How to licence Microsoft applications/software on the UKCloud platform*](../shared/shared-how-license-microsoft.md).

If you require SQL licensing to be provided by UKCloud, this can be done by completing a Service Request from the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal. SQL standard licensing is charged per hour per VM, whilst SQL Enterprise is charged monthly per VM. It is essential that UKCloud are informed of every instance of SQL on the platform, and that you complete a Licence Mobility form for all licences that you use on the UKCloud platform.

### RHEL

RHEL operating systems can be licensed by UKCloud or the customer.

The customer is responsible for ensuring correct licensing for any other operating system they chose to install. If you want to use your own RHEL licencing, please raise a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal.

### How up to date are the operating system images and mirrors?

All CentOS, Ubuntu, Red Hat and Debian distributions include update mechanisms to install the latest patches and releases. For a list of supported operating systems, and instructions on how to access these update repositories, see the Knowledge Centre.

### What anti-virus do you offer on this service?

For information about UKCloud's Anti-Virus as a Service product, see the [*Anti-Virus as a Service Service Scope*](../managed-operations/man-sco-antivirus.md).

### What applications are available as part of the default service?

UKCloud does not offer any additional software other than what's included in the UKCloud Portal catalog. Any additional software, including its licensing, is the customer's responsibility.

### Are Open Virtualisation Format (OVF) VM images supported?

Yes, you can upload OVF images to the platform, and you can download VMs built in the platform as OVF.

### What is Bring Your Own (BYO) licensing for Red Hat?

BYO licensing for Red Hat enables customers to select VMs running on the UKCloud Assured cloud platform for covering by their own commercial agreement with Red Hat.

UKCloud will remove the cost of the Red Hat licence from the customer's monthly bill for the selected VMs. Customers need to raise a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal to let us know which VMs they will cover with their own Red Hat licence.

## Support

### How do I raise a support ticket?

The secure online UKCloud Portal provides most common service management functionality. Alternatively, you can contact support by phone or email.

### How do I manage my services?

Services on the Assured OFFICIAL security domain can be managed over the internet (or other connectivity) via the UKCloud Portal.

For the Elevated OFFICIAL security domain, security requirements are stricter and require either a PSN-approved connection, UKCloud Secure Remote Access or a self-managed CPA-approved (or equivalent standard) VPN solution (for example, site-to-site VPN).

### What are your service maintenance windows?

See [*Understanding UKCloud service maintenance windows*](../other/other-ref-maintenance-windows.md).

### Can UKCloud provide notifications for service status and maintenance?

Yes, you can subscribe to the [UKCloud Service Status page](https://status.ukcloud.com/) to be alerted to service status and maintenance notifications. Notifications can be via email, text, webhook or Atom/RSS feed. For more information, see [*How to subscribe to service status notifications*](../other/other-how-subscribe-service-status.md).

## Onboarding

### How can I get started with the service?

Within four hours of accepting your order, we'll create your primary administrator account, and send you a Welcome Pack, which includes the URL for the UKCloud Portal and associated authentication details.

Your administrator can then create additional accounts for users within the project. Each user can then log on and begin using the service (depending on the security domain and connectivity).

At the time of order, you can specify which of our two UK data centres you'd like to be deployed into. Meeting your request is at UKCloud's discretion.

### Is there a free trial?

Yes, we offer a 30-day free trial so that you can test and evaluate our service without commitment. Your trial provides you with a live environment on the UKCloud platform to test our services and verify whether they are suited to your needs.

### How do I request a trial?

You can request a trial via the UKCloud [Free Trial page](https://ukcloud.com/free-trials/) and accept the trial terms and conditions. Your environment will then be set up and you will be given trial credits to the equivalent of £500.

### What do I do when my trial comes to an end?

You will be contacted by your Cloud Architect or Service Delivery Manager (SDM) when your trial is due to end, either because you have run out of credits or reached 30 days (whichever is sooner).

At the end of your trial, you have the option to transition to production or cease the trial.

## Protection

### Can I create a clone of my environment?

Yes, you can do this through the VMware Cloud Director tenant portal. This operation can also be performed programmatically via the vCloud API.

It's not possible to restrict the automated VM snapshot backup to specific files or directories. You can install your own backup service and use our Cloud Storage service if you need more flexibility.

## Can I still use Synchronous Protection for my VMs?

Synchronous Protection is no longer available as protection option for UKCloud for VMware. We recommend using one of our other protection options: Journaling Protection or Snapshot Protection. We'll continue to provide support to customers who previously added Synchronous Protection to their environment.

## Snapshot Protection

### What are snapshots?

A snapshot is NOT a copy of the VMDK. Creating a snapshot locks out the base VMDK file and any changes to the data are written to the snapshot delta VMDK. If you want to roll back to the point in time that the snapshot was created and discard any changes since, you can revert the snapshot, which essentially deletes it and discards any changes. If you are happy with the changes made since the snapshot was created, you can delete the snapshot, which essentially consolidated all changes back into the base VMDK. For advice on best practice regarding snapshots, see [*Virtual machine disk limits and considerations*](vmw-ref-vmdk-limits.md).

You can create snapshots using the VMware Cloud Director tenant portal and these are stored in the same zone as the source VM. This is not to be confused with the UKCloud Snapshot Protection service, which uses a temporary snapshot to backup the VM to an external system in another UKCloud site.

For further reference, [*Virtual machine data recovery options*](vmw-ref-vm-data-recovery.md) explains the different recovery options available to you through VMware Cloud Director.

### Can I restrict automated VM snapshot backup to specific files or directories?

It's not possible to restrict the automated VM snapshot backup to specific files or directories. You can install your own backup service and use our Cloud Storage service if you need more flexibility.

### How quickly can a VM be restored?

This depends on the size of the VM, the location from which it's being restored and the priority of the support ticket raised to request the restoration.

You should expect recovery to take two to three days. If you require a faster recovery time, you must implement your own backup/restore solution, which will be entirely under your control. Our Cloud Storage service could be an appropriate target for self-managed backups using software such as CommVault and NetWorker.

### What rate are snapshots charged at?

Snapshots will be charged at the rate of the storage they are stored on (Tier 1 or Tier 2), and charged per GiB per month.

### Can I use the 60GiB included with my VM for snapshots?

Yes, you can use the 60GiB included with the VM for snapshots.

### If I have Snapshot Protection on Dedicated Compute, what will I be charged for?

You will only be charged for the protection of the storage consumed, not the VM.

## Disaster Recovery

### Does UKCloud provide a disaster recovery (DR) service?

With UKCloud for VMware's [*Journaling Protection*](vmw-sco-journaling-protection.md) option, you can protect your UKCloud for VMware applications by replicating them to another UKCloud for VMware-enabled zone. This ensures that you can meet your DR requirements, including any aggressive recovery point (RPO) or recovery time objectives (RTO).

[Disaster Recovery as a Service](https://ukcloud.com/app/uploads/2022/08/ukc-svc-231-disaster-recovery-as-a-service-service-definition-13.0.pdf) enables rapid migration of applications between your local VMware or Hyper-V based VMs and UKCloud for VMware disaster recovery-enabled regions.

### How does UKCloud enable customers to create their own DR solutions?

Although we've engineered our cloud platform to tolerate failures and ensure customers' services remain available, we encourage all our customers to design for failure and build DR capabilities into the system design, or into the application.

To help this process, the UKCloud platform has been designed to give you the options you need to design a disaster-tolerant solution. UKCloud's platform is about providing customers with choice. Clearly, customers need to balance the low probability of these failure scenarios occurring with the cost and complexity involved in mitigating their impact.

Depending on the type of failure you are trying to mitigate, UKCloud services have been developed to enable you to design appropriate resilience into your solution.

At a macro level, UKCloud operate out of two sites. Designing across multiple sites will provide resilience against even the most unlikely of scenarios - including natural disasters and mass WAN failure. UKCloud currently offer two sites:

- The independent cloud platform at our Corsham site

- The independent cloud platform at our Farnborough site

Each site also offers independent regions. These are physically segregated parts of the UKCloud platform that have an independent power and networking components - enabling customers to architect resilient solutions out of a single site.

Services in different regions also have independent control planes. By architecting for separate regions, you improve your resilience to outages that effect the control and management of your VMs.

Finally, each region has a number of distinct hardware zones. For customers looking to architect against mass hardware failures. Zones can be utilised to provide additional confidence in your ability to tolerate outages. For example, you can load-balance across two zones to ensure that your service stays online in the event of an unlikely outage.

In some rare failure scenarios (such as DDoS or Split Brain) the availability of the cloud platform at both our sites may be affected. These scenarios can be mitigated by deploying across multiple cloud providers.

## Billing and legal

### What is the smallest unit of time I will be billed for?

The minimum unit of time for use is one hour. Part hours will be rounded up.

Dedicated Compute v2 has a minimum commit of one month.

### What are the charges to transfer data between VMs within the same data centre?

None. Data transfer between VMs in this scenario is free.

### Will I be charged even if my VM is powered off?

You will not be charged for any VMs while they are turned off, however while the VM is in a powered-off state, any storage associated with the VM will be charged for at the prevailing rate. This includes the 10GiB included with Micro machines and 60GiB in all other VM sizes of Tier 2 storage.

### How will I be billed for additional storage?

You can allocate additional storage to VMs on demand. UKCloud will bill customers for additional allocated storage, regardless of the powered on/off state. Additional storage will also include storage used for templates and media items.  

### What is a template or media item?

Within UKCloud for VMware VDCs, you can deploy your own templates, media items or catalog images. These include templates for applications and operating systems.

### How can I view billing information?

Billing information is available via the UKCloud Portal.

### How can I pay for the services?

Payment for UKCloud services can be made by direct bank transfer (BACS/CHAPS). You can find bank details for payment on your invoice.

### What are the termination fees?

There are no termination costs for this service. Customers are responsible for extracting their own data from the UKCloud for VMware if required.

UKCloud may make an additional charge for transferring data out of the service.

### How is resource usage billed?

Actual real-time resource usage is measured to the nearest second. At the end of each day, periods of time in identical VM state are grouped together and the total for each group in seconds is rounded up to the nearest hour. An identical VM state has the same power status, VM size, service level, storage size, protection and licence. Where rounding up of multiple periods in differing states during the same day would result in more than 24 hours of charges, the period with the lowest price per hour is rounded down.

For example, if a VM was switched off for a total of 890 minutes but was on for 550 minutes, the billable hours would be rounded up to 10 hours for when the VM was on and the off period would be rounded down to 14 hours to cap the day at 24 hours.

### Will I be charged for creating snapshots?

Snapshot Protection can be purchased with any VM and will be charged for in accordance with the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide). Self-service snapshots created within VMware Cloud Director will incur charges as of November 2017. These will be accounted for in the invoices you receive at the beginning of December.

## Security

### What data is suitable for the UKCloud assured cloud platform?

The service is hosted in the UK and operated by UK government security-cleared staff. It has extensive independent validation (including NCSC design reviews) that it is fully aligned with the 14 NCSC Cloud Security Principles, and is therefore ideal for all data classified at OFFICIAL (including OFFICIAL SENSITIVE).

### Can systems on different UKCloud security domains communicate with one and another?

UKCloud's Cross Domain Security Zone enables customers to use a customer-designed and managed Walled Garden to enable communication between platforms.

For more information, see the [Cross Domain Security Zone Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-230-cross-domain-security-zone-service-definition-13.0-1.pdf).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
