---
title: How to create a key vault using the UKCloud Azure Stack Hub portal
description: Provides help for creating a key vault on UKCloud for Microsoft Azure
services: azure-stack
author: blawson
reviewer: wturner
lastreviewed: 01/04/2022

toc_rootlink: Users
toc_sub1: How To
toc_sub2: Create a Key Vault
toc_sub3:
toc_sub4:
toc_title: Create a key vault - Portal
toc_fullpath: Users/How To/Create a Key Vault/azs-how-create-key-vault-portal.md
toc_mdlink: azs-how-create-key-vault-portal.md
---

# How to create a key vault using the UKCloud Azure Stack Hub portal

## Overview

Key Vault in Azure Stack Hub helps safeguard cryptographic keys and secrets that cloud applications and services use. By using Key Vault, you can encrypt keys and secrets.

The following process shows you how to setup a vault within Azure Stack Hub's Key Vault, store a secret in the vault and how to view the secret using the Azure Stack Hub Portal.

## Prerequisites

To complete the steps in this guide, you must have appropriate access to a subscription in the Azure Stack Hub portal.

## Creating a new key vault

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

      - **Enable Access to:** - Select the check boxes to specify whether certain Azure services are allowed access to the key vault.

      - **Current Access Policies** - Select **+Add access policy** to configure the permissions that a user, group or service principal has to the key vault.

          ![Create new key vault > Access policy](images/azs-browser-create-key-vault-accesspolicy.png)

          ![Create new key vault > Access policy > Add](images/azs-browser-create-key-vault-accesspolicy-add.png)

6. Click **Review + create**.

7. On the **Review + create** tab, review the selections you've made and then click **Create** to start the deployment.

    ![!Create new key vault > Review](images/azs-browser-create-key-vault-review.png)

8. You can monitor the progress of your key vault's deployment by clicking the **Notifications** icon.

    ![!Notification showing vault deployment in progress](images/azsp_createvm_progress.png)

## Adding a secret to the key vault

1. Once the key vault has been deployed, navigate to it by clicking **All services** in the favourites panel, then selecting **Key Vaults** under the *Security* section.

2. Select your key vault from the list.

3. In the *Settings* section of the key vault blade, select **Secrets**.

4. On the *Secrets* page, click the **+ Generate/Import** button.

5. In the *Create a secret* blade, enter the following information:

   - **Upload Options** - Manually enter a secret or upload an x.509 certificate.

   - **Name** - The name of the secret. Secret names can only contain alphanumeric characters and dashes.

   - **Value** - The value you are storing as a secret.

   - **Content Type** - The type of content contained in the secret (for example, Password). There are no pre-defined values for this field.

   - **Activation Date** - Specifies when the secret will become active.

   - **Expiration Date** - Specifies when the secret will become inactive.

   - **Enabled** - Indicates whether or not the secret data can be retrieved.

   ![Create a new secret](images/azs-browser-create-secret.png)

6. Click **Create**.

## Viewing the secret

1. Once you've created the secret, select it on the *Secrets* page.

2. On the secret's blade, select the current version.

    ![Select secret version](images/azs-browser-select-secret-version.png)

3. On the current version's blade, click the **Show secret value** button.

    ![View secret value](images/azs-browser-view-secret-value.png)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
