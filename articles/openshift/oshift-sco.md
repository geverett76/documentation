---
title: UKCloud for Red Hat OpenShift Service Scope
description: Outlines important details regarding UKCloud for Red Hat OpenShift
services: openshift
author: shighmoor
reviewer: sdixon
lastreviewed: 02/11/2021
toc_rootlink: Service Information
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Service Scope
toc_fullpath: Service Information/oshift-sco.md
toc_mdlink: oshift-sco.md
---

# UKCloud for Red Hat OpenShift Service Scope

## About this Service Scope

If you are considering purchasing our UKCloud for Red Hat OpenShift service, this article describes the boundaries of the service, along with the division of responsibilities between you and UKCloud to facilitate the provisioning and ongoing use of the service.

## About UKCloud for Red Hat OpenShift

UKCloud for Red Hat OpenShift is UKCloud's OpenShift powered Kubernetes Platform as a Service (PaaS). The service provides a secure, private deployment of the [Red Hat&trade; OpenShift&trade; Container Platform](https://www.redhat.com/en/technologies/cloud-computing/openshift/container-platform). The service is delivered as a managed platform, enabling developers to build automation pipelines and leverage the benefits of containerised solutions, helping to deliver modern, cloud-native applications and accelerate digital transformation.

UKCloud deploys, monitors and updates the platform, freeing up your DevOps resources to focus on adding value further up the stack through the rapid delivery of quality controlled code, all without having to worry about the underlying infrastructure.

For more information about what the service offers, see the [UKCloud for Red Hat OpenShift Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-241-ukcloud-for-red-hat-openshift-service-definition-13.0.pdf).

### Key service capabilities

UKCloud for Red Hat OpenShift provides:

- A secure and scalable UK-based platform connected to the internet and government networks including PSN, HSCN, Janet and MCN

- Secure customer separation - UKCloud for Red Hat OpenShift management components and container hosts are dedicated to you, deployed on independently verified, assured multi-tenant infrastructure

- Ability to deploy and manage containers using standardised tools and RESTful APIs

- Ability to connect containers to services hosted within the platform, and externally hosted in UKCloud IaaS, Crown Hosting Data Centres or on your own premises

- Automatic monitoring and redeployment of containers in the event of infrastructure failure

- Autoscale application instances based on resource utilisation metrics

- Streaming of application log and performance metric data to your existing dashboarding tools (for example ELK stack)

- Alignment to the NIST definition of PaaS — extends beyond classic managed service offerings by abstracting users from infrastructure and providing an automated, dynamic and massively scalable application management platform

- Robust isolation providing a high assurance environment — engineered for customers requiring a greater level of control and security beyond typical shared platform offerings

### Typical use cases

Typical use cases include:

- Hosting front-end web application services to ensure that your environment can scale and auto-heal

- Creating an Internet of Things (IoT) endpoint allowing internet devices to talk to your cloud applications

- An elastic analytics platform for capturing and analysing machine data and social media feeds to generate valuable intelligence

- Supporting modern microservice architectures and bringing manageability and scalability to your applications

## Service implementation

UKCloud for Red Hat OpenShift is built using Red Hat's OpenShift Container Platform (OCP) v4, which is the enterprise-hardened version of [OKD](https://www.okd.io/) (previously Origins) v4, which extends the open source Kubernetes project.

UKCloud for Red Hat OpenShift is built as an isolated single-tenant environment on top of UKCloud's secure, assured multi-tenant UKCloud for OpenStack IaaS service, helping to deliver the benefits of single-tenant isolation with the economics and flexibility of multi-tenant infrastructure.

UKCloud for Red Hat OpenShift is available in our Assured OFFICIAL and Elevated OFFICIAL security domains on our Tier 1 platform. UKCloud for Red Hat OpenShift is available on our Tier 2 platform for workloads that require greater levels of security.

### Deployment options

UKCloud for Red Hat OpenShift is packaged to provide you with a high level of flexibility to scale your environments inline with your workloads.

With UKCloud for Red Hat OpenShift, we deploy an OpenShift cluster that contains multiple nodes: nodes for the cluster control plane, infrastructure nodes for additional services, such as ingress controllers, metrics, developer console and aggregated logging, and application nodes for your containerised applications.

> [!NOTE]
> An operational OpenShift cluster requires a ***Control Plane***, consisting of a minimum of three Control Plane Nodes, and we recommend a minimum of two ***Infrastructure Nodes*** to provide additional services, such as ingress controllers, metrics, developer console and aggregated logging. You'll need at least one ***Application Node*** to run your application, however we recommend a minimum of two nodes for resilience.

#### Control Plane

The Control Plane provides the foundation OpenShift services to support the orchestration and management of the container runtime environments. An operational OpenShift cluster requires a minimum of three Control Plane Nodes for API, scheduling and etcd key-value store.

#### Infrastructure Nodes

Infrastructure Nodes provide supporting services such as OpenShift routers, registry, metric collection and aggregated logging. Infrastructure Nodes are not mandatory, but we recommend a minimum of two Infrastructure Nodes to provide integrated cluster services.

#### Application Nodes

Application Nodes provide the compute resources to host your containerised applications and services. We strongly recommend the initial deployment of two or more Application Nodes for production environments to provide resilience to your workloads in the event of the failure of a single node.

### Storage options

Containers in OpenShift by default don't persist data. Every time an application is started, it creates a new container with an immutable image. Hence, any persisted data in the file systems is lost when the container stops or is destroyed. Use persistent volumes within your OpenShift environment to provide data persistence independent of containers. You can purchase persistent volumes for your cluster as stated below:

&nbsp;                    | Tier 1 Persistent Volume | Tier 2 Persistent Volume
--------------------------|--------------------------|-------------------------
**Overview**              | Provides our most performant block storage for workloads requiring consistently higher disk throughput | Block storage with typical performance characteristics for use by production applications or storage
**Number of file copies** | 3                        | 3
**Use cases**             | Web caching<br>Containerised analytics<br>Highly performant, real-time web/mobile applications | Standard, containerised web/mobile applications<br>Storing OpenShift logs and metrics

> [!NOTE]
> In line with current restrictions on the OpenStack service underpinning OpenShift, you can make/attach 25 additional persistent volume claims (PVCs) to each worker node.

### Optional extras

To complement your UKCloud for Red Hat OpenShift service, UKCloud offers the following value-added options.

> [!NOTE]
> Some of these extras will carry supplementary charges; please see the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide) for full details.

#### Additional networks

By default, your OpenShift cluster will only be connected to the internet. Your OpenShift environment can be provisioned on other networks such as PSN, HSCN, Janet and MCN at a flat fee per month per network plus the additional network charges. For more information, see the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide).

#### Registry storage

A benefit of OpenShift is its ability to build Docker images directly from your source code, deploy them, and manage their lifecycle. To enable this, OpenShift utilises an integrated Docker registry to locally manage images. This registry is stored securely, using our Cloud Storage service, outside of your OpenShift environment to help ensure the resilience and availability of your images. Standard Cloud Storage rates apply, for more information, see the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide).

#### Enhanced aggregated logging

By default, an EFK (Elasticsearch, Fluentd, Kibana) stack is deployed onto infrastructure nodes to aggregate logs for a range of OpenShift Enterprise services. Application developers can view the logs of the projects for which they have view access. The EFK stack aggregates logs from hosts and applications, whether coming from multiple containers or even deleted pods.

To provide this service, UKCloud will need to provision an initial allocation of Tier 2 persistent volume, charged at the prevailing rate, for the storage of logs.

As your workloads increase or become more critical and you want to increase the performance and resilience of your Elasticsearch cluster by scaling it across three nodes, you can deploy an additional infrastructure node.

#### Enhanced metric collection

UKCloud will provision a Prometheus-based metrics platform to collect and publish your cluster's metrics from all containers and components in one user interface. This will run on infrastructure nodes, if you have them, or application nodes otherwise.

To provide this service, UKCloud will need to provision an initial allocation of Tier 2 persistent volume, charged at the prevailing rate, to store this data.

To provide resilience and added performance to your cluster's metrics, you can deploy additional infrastructure nodes.

#### SSL certificates

By default, UKCloud will provide 90-day Let's Encrypt SSL certificates for your OpenShift cluster. At the point of deployment, you can provide your own certificates for use with OpenShift.

#### Container native storage

To facilitate the deployment of stateful workloads, UKCloud for Red Hat OpenShift offers dynamically provisioned persistent storage. It is vital that any persistent workloads utilise the appropriate storage policy for the workload to ensure no data loss when a container restarts. The customer is responsible for backup and disaster recovery of any data stored in persistent volumes.

### Backup/recovery and disaster recovery

As standard, localised component failures are tolerated within the infrastructure through elimination of single points of failure (including physical server failure or disk failure).

Although OpenShift is designed to deploy and manage stateless applications (applications that can be destroyed and re-instantiated without risk of data loss), you should maintain an original copy or backup copy of any persistent or dynamic data hosted on this service (such as MySQL DB) by using, for example, UKCloud's [Cloud Storage](https://ukcloud.com/app/uploads/2022/08/ukc-svc-229-cloud-storage-service-definition-13.0-2.pdf) service.

### Service limitations

#### Scalability

As a true cloud platform, UKCloud for Red Hat OpenShift provides full elasticity and scalability. However, to protect the integrity of the platform and manage customer spend, soft limits on the number and size of application instances will be in place. These limits may be extended on request.

#### Persistent volumes

In line with current restrictions on the OpenStack service that underpins OpenShift, you can claim/attach 25 additional persistent volume claims (PVCs) to each worker node.

### Published features not currently available

The following features published in the [UKCloud for Red Hat OpenShift Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-241-ukcloud-for-red-hat-openshift-service-definition-13.0.pdf) are not currently available:

- Janet, PSN and MCN connectivity

Although these features are not currently available, they will be considered on request.

## Service provisioning

### How to buy

You can request UKCloud for Red Hat OpenShift by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal or, for new enquires, visit the [Contact Us](https://ukcloud.com/contact/) page of our website.

### Onboarding

Within 5 business days of accepting an order, UKCloud will create your primary account and send a Welcome Pack, which includes the URLs for the UKCloud Portal and the [*Getting Started Guide*](oshift-gs.md).

UKCloud for Red Hat OpenShift is delivered as a private Platform-as-a-Service (PaaS). Each customer will be provided with an isolated OpenShift cluster within which they can build their containerised solutions.

By default, only a single user account will be created per cluster, this user can then create additional users within the cluster by managing account users via the UKCloud Portal.

## Platform management

UKCloud for Red Hat OpenShift is operated directly by the customer, using OpenShift's dashboard, the UKCloud Portal, and APIs associated with both.

UKCloud maintains responsibility for routine patching and upgrades of the OpenShift platform in-line with the published [*OpenShift life cycle and patch management process*](oshift-ref-lifecycle.md).

## Customer responsibilities

You are responsible for:

- The control and management of access and responsibilities for end users, including appropriate connectivity, security and accreditation if required. If access is required over government secure networks, such as HSCN, Janet, MCN or PSN (including legacy networks), you are responsible for adhering to the Code of Connection (CoCo).

- Self-managing the environment including workload deployment, in-cluster workload segregation, network policy management, storage requests and management, and so on.

- Maintaining an original copy or backup copy of the data used in the UKCloud for Red Hat OpenShift service (see [*Backup/recovery and disaster recovery*](#backuprecovery-and-disaster-recovery)).

- Ensuring only appropriate data (for example OFFICIAL) is stored and processed by applications on this environment and that they comply with the UKCloud Security Operating Procedures (SyOps) and other Information Assurance requirements as specified in the UKCloud System Interconnect and Security Policy (SISP) and associated accreditation documentation sets.

  Customers with requirements beyond these limits can raise a service request via [My Calls](https://portal.skyscapecloud.com/support/ivanti) to have these limits per project considered for raising.

## Support

We monitor, maintain and support our controlled UKCloud for Red Hat OpenShift infrastructure and services, including:

- UKCloud-controlled components, such as the virtual infrastructure, storage, power and physical firewalls and routers

- UKCloud-maintained OpenShift services (for example, router service, DEAs, health manager, cloud controller, control plane nodes, worker nodes, routing layer)

UKCloud for Red Hat OpenShift includes full UKCloud support as standard at no additional charge. For more information about how the support process works, see [*Raising and escalating support tickets with customer support*](../portal/ptl-ref-raise-escalate-service-request.md).

In addition, you'll be assigned a Service Delivery Manager (SDM) to provide any assistance you may require during your use of the service, including onboarding, service reviews and incident reporting and escalation.

UKCloud's Professional Services are designed to provide a clear path to true cloud value, no matter where your organisation is on the journey to cloud migration and adoption. We provide expert, agnostic, multi-cloud advice through a structured, modular approach. Each stage is supported by an outcome-focused workflow that delivers tailored, high value output, enabling organisations to adopt and leverage cloud with confidence. For more information, see the [Professional Services Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-232-ukcloud-professional-services-service-definition-13.0-1.pdf).

Cloud Architects are available to support you during the design of solutions to help reconcile your requirements with our cloud platform. We recommend engagement with a Cloud Architect when implementing complex solutions.

### UKCloud Portal

All UKCloud customers have access to the UKCloud Portal, where they can access the [My Calls](https://portal.skyscapecloud.com/support/ivanti) ticketing system to raise Service Requests and Incidents. We also use the Portal to track and log all customer enquiries, requests, support issues, communications and information.

### Knowledge Centre

To assist you in using our services and all associated functionality, the UKCloud Knowledge Centre is continually maintained to provide the latest information. Key articles for UKCloud for Red Hat OpenShift are listed at the end of this Service Scope.

### Protective Monitoring

Protective Monitoring is available for UKCloud for Red Hat OpenShift. For more information, see [*Protective Monitoring from UKCloud*](../other/other-ref-promon.md).

If you require additional protective monitoring services, we offer our Security Operations Service to monitor your virtual estate (additional charges apply). For more information, see the [Security Operations Service Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-239-security-operations-service-service-definition-13.0.pdf).

In line with UKCloud's System Interconnect and Security Policy (SISP), we provide notifications of customer-impacting security incidents. It's the customer's responsibility to report similar incidents to us.

## Service availability

You are entitled to claim Service Credits for outages to services that take you out of SLA. For more information about how we calculate SLAs, see the [*SLA definition*](../other/other-ref-sla-definition.md).

### Service maintenance windows

For UKCloud for Red Hat OpenShift, Planned and Emergency are not included in the SLA.

For information about Planned and Emergency Maintenance, see [*Understanding UKCloud service maintenance windows*](../other/other-ref-maintenance-windows.md).

## Pricing and billing

For UKCloud for Red Hat OpenShift pricing, see the [UKCloud Pricing Guide](https://ukcloud.com/pricing-guide). For additional pricing information related to this service, including pricing examples, billing information, additional fees and free trial information, see [*Pricing information for UKCloud for Red Hat OpenShift*](oshift-ref-pricing.md).

## Termination of service

You can terminate your UKCloud for Red Hat OpenShift service by providing us with no less than 30 days' notice. There are no termination fees for the service.

At the point of termination, you're responsible for extracting your own data from the platform if required. UKCloud may make an additional charge for transferring data out of the service. For more information, see [*Terminating your UKCloud services*](../other/other-ref-offboarding.md).

At the point of termination, all customer data, accounts and access will be permanently deleted and will not be able to be subsequently recovered or restored.

## Supporting information

For more information about UKCloud for Red Hat OpenShift, see the following:

- [UKCloud for Red Hat OpenShift Service Definition](https://ukcloud.com/app/uploads/2022/08/ukc-svc-241-ukcloud-for-red-hat-openshift-service-definition-13.0.pdf)

- [*Pricing information for UKCloud for Red Hat OpenShift*](oshift-ref-pricing.md)

- [*Getting Started Guide for UKCloud for Red Hat OpenShift*](oshift-gs.md)

- [*UKCloud for Red Hat OpenShift FAQs*](oshift-faq.md)

- [*UKCloud Terms and Conditions*](../other/other-ref-terms-and-conditions.md)

- [*SLA definition*](../other/other-ref-sla-definition.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
