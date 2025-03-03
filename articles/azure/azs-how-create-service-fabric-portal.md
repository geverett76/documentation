---
title: How to create a Service Fabric cluster using the UKCloud Azure Stack Hub portal
description: Provides help for creating a Service Fabric cluster on UKCloud for Microsoft Azure
services: azure-stack
author: Bailey Lawson
reviewer: William Turner
lastreviewed: 11/08/2021

toc_rootlink: Users
toc_sub1: How To
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Create a Service Fabric cluster
toc_fullpath: Users/How To/azs-how-create-service-fabric-portal.md
toc_mdlink: azs-how-create-service-fabric-portal.md
---

# How to create a Service Fabric cluster using the UKCloud Azure Stack Hub portal

## Overview

Azure Stack Hub Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers. Service Fabric also addresses the significant challenges in developing and managing cloud native applications. Developers and administrators can avoid complex infrastructure problems and focus on implementing mission-critical, demanding workloads that are scalable, reliable, and manageable. Service Fabric represents the next-generation platform for building and managing these enterprise-class, tier-1, cloud-scale applications running in containers.

The following process shows you how to setup a Service Fabric cluster using the Azure Stack Hub portal.

## Prerequisites

To complete the steps in this guide, you must have appropriate access to a subscription in the Azure Stack Hub portal.

## Creating a new key vault

Before creating a Service Fabric cluster, it is necessary to create a key vault to store the certificates for the cluster. These certificates are used in Service Fabric to provide authentication and encryption to secure various aspects of a cluster and its applications. You can find more information about these certificates [here](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-security#x509-certificates-and-service-fabric).

1. Log in to the Azure Stack Hub portal.

    For more detailed instructions, see the [*Getting Started Guide for UKCloud for Microsoft Azure*](azs-gs.md).

2. In the favourites panel, select **Create a resource**.

    ![New option in favourites panel](images/azsp_newmenu.png)

3. In the *New* blade, select **Security + Identity**.

   ![Security option in New blade](images/azs-browser-new-security.png)

4. In the *Security + Identity* blade, select **Key Vault**.

   ![New Key Vault](images/azs-browser-new-key-vault.png)

5. In the *Create key vault* blade, enter the following information:

    - **Basics** tab

        - **Subscription** - This is your UKCloud for Microsoft Azure subscription.

        - **Resource group** - Select an existing resource group, or create a new one by clicking the **Create new** link and then typing a name for your new resource group in the pop-out window.

        - **Key vault name** - The name of the key vault.

        - **Region** - This will be `frn00006`, which is the Azure Stack Hub region.

        - **Pricing tier** - Azure Stack Hub only offers the Standard pricing tier.

          ![Create new key vault > Basics](images/azs-browser-create-key-vault-basics.png)

    - **Access policy** tab

        - **Enable Access to:** - Select the first two check boxes to allow access to the key vault for virtual machines and the Azure Resource Manager.

        - **Current Access Policies** - Select **+Add access policy** to configure the permissions that a user, group or service principal has to the key vault.

          ![Create new key vault > Access policy](images/azs-browser-create-key-vault-accesspolicy.png)

          ![Create new key vault > Access policy > Add](images/azs-browser-create-key-vault-accesspolicy-add.png)

6. Click **Review + create**.

7. On the **Review + create** tab, review the selections you've made and then click **Create** to start the deployment.

    ![!Create new key vault > Review](images/azs-browser-create-key-vault-review.png)

8. You can monitor the progress of your key vault's deployment by clicking the **Notifications** icon.

    ![!Notification showing vault deployment in progress](images/azsp_createvm_progress.png)

### Adding a certificate to the key vault

1. Once the key vault has been deployed, navigate to it by clicking **All services** in the favourites panel, then selecting **Key Vaults** under the *Security* section.

2. Select your key vault from the list.

3. In the *Settings* section of the key vault blade, select **Secrets**.

4. On the *Secrets* page, click the **+ Generate/Import** button.

5. In the *Create a secret* blade, enter the following information:

   - **Upload options** - Select the **Certificate** option.

   - **Upload certificate** - Select the .pfx certificate to upload.

   - **Name** - The name of the certificate to identify it within the Key Vault.

   - **Activation Date** - Specifies when the certificate will become active.

   - **Expiration Date** - Specifies when the certificate will become inactive.

   - **Enabled** - Indicates whether or not the secret data can be retrieved.

   ![Create a new secret](images/azs-browser-add-certificate.png)

6. Click **Create**.

7. Repeat as necessary, depending on how many certificates you require.

### Gathering key vault and certificate information

During configuration of the Service Fabric cluster, you must provide several details relating to the key vault and certificates.

1. Once you have deployed the key vault, navigate to it by clicking **All services** in the favourites panel, then selecting **Key Vaults** under the *Security* section.

2. Select your key vault from the list.

3. In the *Settings* section of the key vault blade, select **Properties**.

4. Copy the **Resource ID** and store it for later use.

5. In the *Settings* section of the key vault blade, select **Secrets**.

6. On the *Secrets* blade, select the certificate you added in the previous section.

7. On the certificate's blade, select the current version.

8. Copy the **Secret Identifier**.

9. Repeat for each certificate that you are going to use for the Service Fabric cluster.

You also need the thumbprint of the certificate(s). For information about how to find this information, see [here](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate).

## Create a Service Fabric cluster

1. In the favourites panel, select **Create a resource**.

   ![New option in favourites panel](images/azsp_newmenu.png)

2. In the search bar, search for **Service Fabric Cluster**.

   ![Service Fabric Cluster in marketplace](images/azs-browser-new-servicefabriccluster.png)

3. Select **Service Fabric Cluster** and click **Create**.

4. In the **Basics** blade, enter the following information and click **OK**:

   - **Service Fabric Cluster Name** - The name of your cluster.

   - **Node Type Prefix** - Prefix for the name of each node (VM).

   - **Primary Node Type Size** - Size of the VM scale set for the primary node type.

   - **Additional Node Type Sizes** - For every additional node type, add an array with a count of the nodes in each node type. For example, if you want two additional node types with three nodes in each, enter `3,3` (separating the amount of nodes for each node type with a comma).

   - **Admin Username** - The admin username for each node.

   - **Password** - The admin password for each node.

   - **DNS Service** - Select **Yes** to use DNS service, which is an optional system service that enables you to map DNS names to a service name and discover other services using the DNS protocol. If you have applications with existing URLs that you intend to use with Service Fabric, DNS service will help you use the standard DNS protocol (as an alternative to the Service Fabric Naming service) for resolving service names.

   - **Repair Manager** - Select **Yes** to use Repair Manager to enable patch orchestration on node types with a durability of bronze, which helps keep your VMs up to date.

   - **Service Fabric deployment package URL** - Specify the URL to download the Service Fabric deployment package from. For disconnected scenarios, download the service fabric package from the URL specified and upload it to a blob, then enable anonymous access and specify the URL here.

   - **Service Fabric runtime package URL** - Specify the URL to download the Service Fabric runtime package from. For disconnected scenarios, download the service fabric runtime from the URL specified and upload it to a blob, then enable anonymous access and specify the URL here.

   > [!WARNING]
    > There are compatibility issues between the latest release of Service Fabric and its corresponding SDK. Until this issue is addressed, provide the following parameters to the deployment package URL and runtime package URL. Your deployments will fail otherwise.
    >
    > - Service Fabric deployment package URL: https://download.microsoft.com/download/8/3/6/836E3E99-A300-4714-8278-96BC3E8B5528/6.5.641.9590/Microsoft.Azure.ServiceFabric.WindowsServer.6.5.641.9590.zip
    > - Service Fabric runtime package URL: https://download.microsoft.com/download/B/0/B/B0BCCAC5-65AA-4BE3-AB13-D5FF5890F4B5/6.5.641.9590/MicrosoftAzureServiceFabric.6.5.641.9590.cab
    >
    > For disconnected deployments, download these packages from the specified location and host them locally on an Azure Stack Hub Blob.

   - **Subscription** - This is your UKCloud for Microsoft Azure subscription.

   - **Resource Group** - Select an existing resource group, or create a new one by clicking the **Create new** link and then typing a name for your new resource group in the pop-out window. Note that to create a Service Fabric cluster, the resource group must contain no other resources.

   - **Location** - This will be `frn00006`, which is the Azure Stack Hub region.

   ![Create Service Fabric cluster > Basics](images/azs-browser-create-sf-basics.png)

5. In the *Network Settings* blade, enter the following information and click **OK**:

   - **Service Fabric TCP Port** - Service Fabric cluster TCP gateway port to use to connect using the Service Fabric client.

   - **Service Fabric HTTP Port** - Service Fabric cluster HTTP gateway port to use to connect using the Service Fabric Explorer.

   - **Service Fabric Reverse Proxy Port** - Service Fabric cluster reverse proxy port

   - **Custom Application Endpoints** - Custom endpoints to open for connections to applications running on this cluster. Enter endpoints separated by commas, for example, `80,8080,8081`.

   - **Custom ports to open in the Network Security Group** - Custom ports to open in the Network Security Group. Enter ports separated by commas, for example, `3389,80,8080,8081`.

   ![Create Service Fabric cluster > Network Settings](images/azs-browser-create-sf-networking.png)

6. In the *Node Configuration* blade, enter the following information and click **OK**:

   - **Image SKU** - The image template that each node is built from.

   - **VM Size** - The size of each node.

   ![Create Service Fabric cluster > Node Configuration](images/azs-browser-create-sf-node.png)

7. In the *Security* blade, enter the following information and click **OK**:

   - **Source Key Vault** - The resource ID of the key vault that you gathered in the previous section. This should be in the format of **`/subscriptions/<SubscriptionId>/resourceGroups/<ResourceGroupName>/providers/Microsoft.KeyVault/vaults/<VaultName>`**.

   - **Cluster Certificate URL** - The Secret Identifier of the cluster certificate that you gathered in the previous section. It should be in the format of **`https://<VaultEndpoint>/secrets/<SecretName>/<SecretVersion>`**.

   - **Cluster Certificate thumbprint** - Cluster certificate thumbprint that you gathered earlier. For example, **`1742635FBCC5F9A442582516A7292523686DE3D7`**.

   - **Server Certificate URL** - The Secret Identifier of the server certificate that you gathered in the previous section. It should be in the format of
    **`https://<VaultEndpoint>/secrets/<SecretName>/<SecretVersion>`**.

   - **Server Certificate thumbprint** - Server certificate thumbprint that you gathered earlier. For example, **`1742635FBCC5F9A442582516A7292523686DE3D7`**.

   - **Use Reverse Proxy Certificate** - You may specify an SSL certificate to be used by the reverse proxy you have enabled. Doing so will cause the reverse proxy to communicate using HTTPS. If no certificate is specified, then the reverse proxy will communicate using HTTP instead.

   - **Application Certificate URL** - The Secret Identifier of the application certificate that you gathered in the previous section. It should be in the format of **`https://<VaultEndpoint>/secrets/<SecretName>/<SecretVersion>`**.

   - **Admin Client Certificate Thumbprints** - Comma separated list of admin client certificate thumbprints. For example, **`1742635FBCC5F9A442582516A7292523686DE3D7,0272251171BA32CEC7938A65B8A6A553AA2D3283`**.

   - **Non-Admin Client Certificate Thumbprints** - Comma separated list of non-admin client certificate thumbprints. For example, **`1742635FBCC5F9A442582516A7292523686DE3D7,0272251171BA32CEC7938A65B8A6A553AA2D3283`**.

   ![Create Service Fabric cluster > Security](images/azs-browser-create-sf-security.png)

8. In the *Summary* blade, click **OK**. Then in the *Buy* blade, click **Create**.

9. You can monitor the progress of your Service Fabric cluster's deployment by clicking the **Notifications** icon.

   ![!Notification showing Service Fabric cluster deployment in progress](images/azsp_createvm_progress.png)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
