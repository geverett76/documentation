---
title: Secure Remote Access Service Scope
description: Outlines important details regarding UKCloud's Secure Remote Access (SRA) service
services: sra
author: bchallis
reviewer: bchallis
lastreviewed: 30/08/2019

toc_rootlink: Secure Remote Access
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Service Scope
toc_fullpath: Secure Remote Access/sra-sco.md
toc_mdlink: sra-sco.md
---

# Secure Remote Access Service Scope

## About this document

This document describes the boundaries of the Secure Remote Access (SRA) service, along with the division of responsibilities between UKCloud and the customer, to facilitate the provisioning and ongoing use of the service.

## About Secure Remote Access

The Secure Remote Access service enables customers to securely connect to the UKCloud Elevated OFFICIAL security domain using National Cyber Security Centre (NCSC)-approved internet VPN technologies and the walled garden architectural pattern, using bastion VMs.

You can create your own VMs and data flows across the SRA in order to satisfy your access requirements.

## Application process

Customers wanting to use SRA need to go through the CDSZ Application Process.

Customers will have two options when purchasing an SRA service:

- A light-touch design review/self-assessment route for customers with simple implementations, or those who are experienced at designing secure solutions.

- An assurance-wrap style approach with UKCloud's experienced professionals for more complex implementations or those customers who would like support and guidance when developing their solutions.

Both options require the same submission documentation to enable UKCloud to provision the service. This is documented in [*UKCloud Cross Domain Security Zone application process*](../security/cdsz-ref-application-process.md).

## Service architecture

SRA utilizes Cisco AnyConnect as the underlying VPN technology. UKCloud manages the VPN termination and the certificate generation and revocation. The customer will manage the installation of Cisco AnyConnect and installing the certificates onto authorized devices.

The SRA walled garden is a VMware-only environment, utilizing VMware Cloud Director as the management orchestrator for the service. An SRA walled garden is a virtual datacenter (VDC) in which you can build virtual machines and virtual networks in order to inspect and protect data moving between Assured and Elevated cloud environments. You can find more information about architecting an SRA environment in the [*Getting Started Guide for Secure Remote Access*](sra-gs.md).

An SRA walled garden is a VMware only environment, however you can connect it to non-VMware cloud environments within UKCloud, such as Oracle or OpenStack.

UKCloud will provision one free-of-charge Small VM within the SRA walled garden to allow customers access to the Elevated Portal in order to manage the SRA walled garden. Customers may choose to delete this VM once they have configured their own access VM.

## Storage options

All SRA workloads include 60GiB of Tier 2 storage for free. All storage is persistent and resilient to local hardware failures.

You can purchase additional storage to support your application. You can use multiple storage options to support different aspects of the application.

- **Tier 1.** Our most performant storage for workloads requiring consistently higher disk throughput

- **Tier 2.** Persistent block storage with typical performance characteristics for use by production applications or storage

## Storage policies

We provide you with access to two storage policies: Tier 1 and Tier 2. Both policies have a 1TiB soft-quota of storage.

- We do not guarantee storage performance, as it can be affected by many factors

- We do not provide IOPS figures for our storage offerings

- Workloads can use multiple storage profiles

## Protection

Customers have a range of automated, on-platform protection options to choose from for their environments:

- **Catalogue and template-based recovery.** All customers have access to catalogue and template-based recovery as standard. This is a configuration management solution that can re-provision stateless servers to a new VM when required, using standard, and catalogue-based VM templates.

- **Snapshot Protection.** 14-day or 28-day snapshot policies available. Data protected by the snapshot has an RPO of 24 hours, with RTO determined by the time taken to restore the VM after the service request is raised. See the [*Snapshot Protection Service Scope*](../vmware/vmw-sco-snapshot-protection.md) for full details.

## Service availability

The service level agreement (SLA) for SRA workloads guarantees 99.90% availability.

You're entitled to claim Service Credits for outages to services that take you out of SLA. For more about how we calculate SLAs, see the [*SLA Definition*](../other/other-ref-sla-definition.md).

## Service background

- We maintain the standard VM template sizes that control allocation of CPU and resources.

- VMs are fully provisioned.

- The system is configured to automatically balance resources, so your VMs may vMotion between physical hosts.

- To maintain performance across the platform, UKCloud can perform movements/migrations of VMs, vApps or storage within the infrastructure assigned to a service.

- We maintain the VPN termination devices.

- We manage the generation and revocation of digital certificates for the VPN.

- We actively capacity-manage the cloud platform to ensure you have access to the resources you request.

- We control the deployed versions of technology on the platform. This covers internal platform-supporting technologies, and any technology versions available to you.

  - Internally this includes, but isn't limited to, the vSphere and ESX versions, and the hardware version of the platform.

  - Externally this includes the available versions of the edge gateway and VMware Cloud Director.

- Promiscuous mode is disabled.

- You can make additional configurations inside a VM (such as acting as a secondary hypervisor or implementing third-party software technologies). We do not support customer implementations inside a VM.

## Service resilience

- You can specify Farnborough or Corsham as the site where you'd like to have your SRA service provisioned. We'll try to accommodate requests and will advise you if we are unable do so.

- You can set affinity or anti-affinity rules through VMware Cloud Director so that VMs do, or do not, run on the same physical host.

## Operating systems

### Licensing

We can provide:

- OS licensing through the SPLA and academic frameworks for Microsoft

- Red Hat Enterprise Linux licensing

For the latest available licences, see the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide).

You can bring your own licensing for Red Hat and certain Microsoft application licensing under Microsoft Mobility using software assurance. You should inform UKCloud via a Service Request if you're providing your own licensing for a retrospective discount.

For non-UKCloud issued software, you must obey the licensing requirements of the software provider. This includes being aware of any constraints around using the software in a virtualised environment.

### VM server images

We provide base VM images for the operating systems for which we provide licensing. You can access these from VMware Cloud Director.

You can use your own images for non-Windows and RHEL services, where licensing stipulates that to use the VM on our platform it must be licensed (and reported back to the software vendor) by UKCloud.

### Update services

We make update repositories available for all software for which we provide licensing. We don't provide software update facilities for non-UKCloud licensed software.

### Anti-virus

We do not provide anti-virus software as part of the service.

## Networks

From a customer management experience, you manage all your connectivity rules, such as firewall, IPsec VPN and NAT functionality, through your edge gateway, using either the VMware Cloud Director tenant portal or vCloud API.

You can find more information about networking within the SRA walled garden in the [*Getting Started Guide for the Cross Domain Security Zone Walled Garden*](../security/cdsz-gs-walled-garden.md).

## Edge gateway

- By default, we assign two edge gateways per SRA walled garden VDC: one facing the VPN termination devices and one facing Elevated.

- You can have up to nine Org VDC networks per edge gateway.

### vApp edge

vApp networks enable you to create smaller networks within individual vApps that have a vApp edge, similar to the edge gateway on your VDC. Although a vApp edge isn't as feature rich as an edge gateway, it lets you create firewall and NAT rules to separate your VDC networks from your vApp VMs. See [*How to create a vApp network*](../vmware/vmw-how-create-vapp-network.md) for configuration details.

### Site-to-site IPsec VPN

You can create IPsec VPN tunnels to connect from SRA walled garden edges to virtual firewalls in Assured or Elevated. There is a limit of 64 tunnels per edge gateway.

### Load balancing

The edge gateway acts as a basic layer 3 load balancer, including features such as session persistence and health checks. If you need more advanced load balancing, you should consider a third-party product.

## Protective monitoring

We've implemented GPG 13-aligned Protective Monitoring across the Assured and Elevated security domains at the hypervisor level and below. For more information, see [*Protective Monitoring from UKCloud*](../other/other-ref-promon.md).

If you require protective monitoring services above the hypervisor (for example, for your VM), we offer our Security Operations Service to monitor your virtual estate (additional charges apply). For more information, see the [Security Operations Service Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-239-security-operations-service-service-definition-13.0.pdf).

In line with UKCloud's System Interconnect and Security Policy (SISP), we provide notifications of customer-impacting security incidents. It's the customer's responsibility to report similar incidents to us.

## Platform management

Users can access, manage and view the SRA service, accessing only those features allowed by their role, in any of the following ways:

- **vCloud API.** Enables the programmatic creation and management of VMs inside the SRA walled garden.

- **VMware Cloud Director tenant portal.** Provides a graphical interface to access the VMware Cloud Director environment (depending on assigned permissions).

- **UKCloud Portal.** Enables the creation of compute services and subsequently VDCs and edge gateways. The Portal also includes an overview of actual and estimated spend, along with service configuration information. Access to incident and request management is also possible through the Portal.

You cannot access the underlying infrastructure. This includes (but isn't limited to) the hardware and the vSphere environment.

## Service reporting

### Visibility

Maintenance notifications and Service Status reports are delivered through the Portal.

### Billing

We provide you with monthly bills covering your monthly spend.

## Customer service

**Cloud Architect.** UKCloud Cloud Architects support you during the design of solutions for the cloud platform. UKCloud Cloud Architects are ideally placed to help reconcile your requirements with the UKCloud platform. We recommend engagement with a Cloud Architect when implementing an SRA walled garden.

**Service Delivery Manager (SDM).** An assigned point of contact who will provide any assistance you require during your use of the service, including onboarding, service reviews and incident reporting and escalation.

**Support Desk.** After the initial onboarding and design phase, customers can utilise the standard UKCloud support entitlement. For more information, see [*Raising and escalating support tickets with customer support*](../portal/ptl-ref-raise-escalate-service-request.md).

## Customer responsibilities

You are responsible for:

- Assessing whether the UKCloud platform can support the various requirements of your application.

- Completing and submitting an SRA application form in order to be granted access to an SRA walled garden.

- The control and management of access and responsibilities for end users including appropriate connectivity, security and accreditation if required.

- Managing the devices used for access to the SRA service, including patching and anti-virus on the device.

- Installation of the Cisco AnyConnect software on your devices. We are responsible for providing software and updates.

- Installation of the certificates on your devices in order to connect to the SRA service.

- If you require onward connectivity to government secure networks within Elevated (MCN or PSN), you are responsible for adhering to the relevant Code of Connection (CoCo) and for providing evidence of your CoCo to UKCloud upon request. UKCloud is unable to provide access to secure networks where such evidence has not been provided by the customer.

- Management and administration of layers above the hypervisor (OS patching, application performance monitoring, user administration).

- Ensuring only lawful data that supports the UK Public Sector is stored and processed by applications on this environment, and that you fully comply with the UKCloud Security Operating Procedures (SyOPs) and other information assurance requirements as specified in the UKCloud System Interconnect and Security Policy (SISP) and associated accreditation documentation sets.

## Service provisioning

Within 4 hours of accepting an order (shorter deployment times are typically achieved and can be prioritised upon request), UKCloud will create the customer's Primary Administrator account and send a Welcome Pack, which includes the URL for the UKCloud Customer Portal, and the Getting Started Guide.

Customers will have two assessment options when purchasing an SRA service.

- A light-touch design review/self-assessment route for customers with simple implementations, or those who are experienced at designing secure solutions.

- An assurance-wrap style approach with UKCloud's experienced professionals for more complex implementations or those customers who would like support and guidance when developing their solutions.

Both options require the same submission documentation to enable UKCloud to provision the service.

Deployment time following validation of the assurance document set is 5 days. This includes the setup and configuration of customer specific firewall requirements.

UKCloud has created several videos, help guides, manuals and FAQs to help train and instruct users so that they are up and running quickly and easily. These are available within the Knowledge Centre.

UKCloud also has a large ecosystem of partners who can deliver additional services, such as support and professional services. UKCloud would be pleased to introduce you to the right partner to suit your needs.

## Service constraints

For information about Planned and Emergency Maintenance, see [*Understanding UKCloud service maintenance windows*](../other/other-ref-maintenance-windows.md).

## Supporting documents and resources

The following documents contain more information about SRA and the service options:

- [*Getting Started Guide for Secure Remote Access*](sra-gs.md)

- [*Secure Remote Access FAQs*](sra-faq.md)

- [*UKCloud Cross Domain Security Zone application process*](../security/cdsz-ref-application-process.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
