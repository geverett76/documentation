---
title: Making the most of your UKCloud for Red Hat OpenShift trial
description: Provides information to get up and running with UKCloud for Red Hat OpenShift trials
services: openshift
author: mhussain
reviewer: gellner
lastreviewed: 04/01/2022

toc_rootlink: Reference
toc_sub1:
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Making the most of your UKCloud for Red Hat OpenShift trial
toc_fullpath: Reference/oshift-ref-trial.md
toc_mdlink: oshift-ref-trial.md
---

# Making the most of your UKCloud for Red Hat OpenShift trial

## Overview

Welcome to your UKCloud for Red Hat OpenShift trial. Your trial OpenShift cluster is a secure, single-tenant private deployment on UKCloud's Assured OpenStack cloud. During an OpenShift trial, the OpenShift cluster is typically only connected to the internet, however connectivity to many other government community networks is available in OpenShift clusters after the trial phase. The purpose of an OpenShift trial is for you to get hands-on experience with Red Hat&trade; OpenShift container orchestration technology to see if it is the correct technology for you.

### Intended audience

This article is intended for developers who have signed up for an OpenShift trial with UKCloud. Developers are expected to have a good understanding of containerisation and container orchestration technologies to maximise their benefit from an OpenShift trial.

## Introduction to UKCloud for Red Hat OpenShift trials

OpenShift provides a platform-as-a-service, which means that you don't need to worry about the underlying hardware or operating system. Instead, you can focus on developing, deploying, scaling and monitoring your applications in OpenShift, maximising your return on investment in terms of money and time.

With UKCloud for Red Hat OpenShift, you have administrator access to your cluster, giving you the control you need to create, deploy and administer your environment as you see fit.

**OpenShift documentation:** [*OpenShift Container Platform architecture*](https://docs.openshift.com/container-platform/4.9/architecture/architecture.html)

## GUI and CLI Access

To access the OpenShift cluster GUI, you need an internet-enabled device running an HTML5-capable browser. You will also be set up for access to the UKCloud Portal and given the relevant access to your OpenShift deployment.

**OpenShift documentation:** [*About the Developer perspective in the web console*](https://docs.openshift.com/container-platform/4.9/web_console/odc-about-developer-perspective.html)

In addition to GUI access, you can also access OpenShift through the CLI. To do this, you need to install the `oc` client on your machines. To avoid any compatibility issues please install the same version of the `oc` client as your OpenShift cluster. 

**OpenShift documentation:** [*Getting started with the OpenShift CLI*](https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/getting-started-cli.html)

## Storage

Each trial deployment has a block storage quota of 2TB across either Tier 1 or Tier 2 storage. This is enforced at the OpenStack project layer. This storage is available to the projects you create within OpenShift and you can consume the storage by creating Persistent Volume Claims (PVCs) for your applications. PVCs are used for pods that run stateful applications; data inside pods that is not stored on PVCs will be lost when the pods are restarted, for example when the application is redeployed, updated or as a result of node evacuations during patching. You can increase your storage quotas by creating a Service Request in the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal. 

Where possible, deploy application pods statelessly. Stateless application pods scale more easily and hence tend to be more resilient and performant.

OpenShift is deployed with an internal image registry making use of UKCloud's object storage service for persistence. This includes 60GB of free storage capacity, which does not consume your 2TB block storage quota; rather this is in addition to the 2TB data limit. UKCloud provisions an Elasticsearch, Fluentd and Kibana stack, which uses 200GB of Tier 2 storage (which does consume some of the 2TB storage limit).

## Image Security

You should take care when creating your container images to ensure the images do not run as root. You should set up containers to run as a user who has just enough rights to run the container workload.

**OpenShift documentation:** [*Creating images*](https://docs.openshift.com/container-platform/4.9/openshift_images/create-images.html)

## RedHat OpenShift Getting Started Documentation

**OpenShift documentation:** [*About the Developer perspective in the web console*](https://docs.openshift.com/container-platform/4.9/web_console/odc-about-developer-perspective.html), [*Getting started with the OpenShift CLI*](https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/getting-started-cli.html), [*OpenShift CLI developer command reference*](https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/developer-cli-commands.html), and [*OpenShift CLI administrator command reference*](https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/administrator-cli-commands.html)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
