---
title: How to reset your Cloud Storage secret key
description: Describes how to reset your Cloud Storage secret key
services: cloud-storage
author: shighmoor
reviewer: sbeck
lastreviewed: 31/03/2022

toc_rootlink: How To
toc_sub1:
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Reset your Cloud Storage secret key
toc_fullpath: How To/cs-how-reset-secret-key.md
toc_mdlink: cs-how-reset-secret-key.md
---

# How to reset your Cloud Storage secret key

## Overview

Cloud Storage is UKCloud's object storage solution based on Dell EMC Elastic Cloud Storage (ECS).

Each user who can access Cloud Storage has an associated secret key to enable secure authentication. When attempting to access Cloud Storage, you must specify the appropriate secret key. If you forget the secret key for your user ID, you can reset it in the UKCloud Portal.

### Intended audience

To complete the steps in this guide you must have been granted access to the relevant namespace.

## Resetting your secret key

For security purposes, the UKCloud Portal does not display secret keys, if you forget your secret key, you must reset it to generate a new one.

1. [*Log in to the UKCloud Portal*](../portal/ptl-gs.md#logging-in-to-the-ukcloud-portal) and select your account.

2. In the Portal navigation panel, expand the **Cloud Storage** option and select **ECS**.

   ![ECS Cloud Storage option in the Portal menu](images/cs-portal-mnu-cloud-storage.png)

3. Click the **Users** button for the namespace for which you want to reset the secret key.

   ![Users button](images/cs-portal-btn-users.png)

4. The **Users** tab lists the different user IDs associated with the namespace.

5. Click the **Reset Secret** button next to the appropriate user ID.

   ![Reset Secret button](images/cs-portal-btn-reset-secret.png)

6. Click **OK** to confirm that you want to reset the secret key.

   ![Reset Secret dialog box](images/cs-portal-reset-secret.png)

7. Stay on the current page until a popup dialog box displays the new secret key.

   ![New secret key](images/cs-portal-new-key.png)

8. Make a note of the key and then click **Close**.

   > [!NOTE]
   > After you close this dialog box, you will not be able to see the secret key again in the UKCloud Portal. If you do not make a note of the secret key or if you forget or lose it, you will need to reset it again.

## Next steps

This guide has shown you how to reset your Cloud Storage secret key. For information about how to use the service, see the following articles:

- [*Getting Started Guide for Cloud Storage*](cs-gs.md)

- [*How to view Cloud Storage information in the UKCloud Portal*](cs-how-view-info-portal.md)

- [*How to create a new Cloud Storage user in the UKCloud Portal*](cs-how-create-user.md)

- [*How to install Dell EMC GeoDrive*](cs-how-install-geodrive2-client.md)

- [*How to use file browsers with Cloud Storage*](cs-how-use-file-browsers.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
