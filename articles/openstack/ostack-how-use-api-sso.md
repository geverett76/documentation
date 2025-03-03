---
title: How to use the OpenStack API using an SSO enabled user
description: Explains the changes needed to make use of the OpenStack API with an SSO enabled user.
services: openstack
author: srelf
reviewer: srelf 
lastreviewed: 15/07/2021
toc_rootlink: How To
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Use the OpenStack API with an SSO user
toc_fullpath: How To/ostack-how-use-api-sso.md
toc_mdlink: ostack-how-use-api-sso.md
---

# How to use the OpenStack API using an SSO enabled user

## Overview

If your OpenStack user account is SSO-enabled, and you want to use the OpenStack API you'll need to make a few changes to your downloaded OpenStack RC file. These changes allow any API calls that you make to be correctly passed to the SSO service.

## Downloading your RC file

See the *Bind your OpenStack credentials* section of [*How to use the OpenStack Command Line*](ostack-how-use-cli.md) for details on where to get your RC file. 

> [!NOTE]
> You will require the v3 version of the OpenStack RC file. 

## Modifying your RC file

Once you've downloaded your RC file, open it in your editor of choice and remove the following line: 

```bash
export OS_USER_DOMAIN_NAME="Federated"
```

now add the following lines to the bottom of the file:

```bash 
export OS_IDENTITY_PROVIDER="sso"
export OS_PROTOCOL="oidc"
export OS_AUTH_TYPE="v3oidcpassword"
```

You also need to add the following items to the bottom of the file, substituting the appropriate values from the table below depending on the OpenStack regions you're connecting to:

```bash
export OS_CLIENT_ID=""
export OS_CLIENT_SECRET=""
export OS_ACCESS_TOKEN_ENDPOINT=""
```

If you're using terraform, you'll need to append the following to your file:

```bash
echo "Generating token..."#(optional)
export OS_TOKEN=$(openstack token issue -c id -f value)
```

> [!NOTE]
>
> - Be advised, that the token generated by the above export statement has a lifetime of a couple of hours. You'll need to re-source your RC file if you're working for extended periods.
>
> - To avoid the following error when trying to use the OpenStack CLI, it's advisable to use a separate RC file for use with terraform:
>
>   `__init__() got an unexpected keyword argument 'token'`

| Site         | Variable                 | Value                                                                              |
|--------------|--------------------------|------------------------------------------------------------------------------------|
| Farnborough  | OS_CLIENT_ID             | `cni.1.frn00006`                                                                   |
| &nbsp;       | OS_CLIENT_SECRET         | e7f230b0-e445-444e-9d27-70beb2da3306                                               |
| &nbsp;       | OS_ACCESS_TOKEN_ENDPOINT | `https://idp.ukcloud.com/auth/realms/client-assured/protocol/openid-connect/token` |
| Corsham      | OS_CLIENT_ID             | `cni.2.cor00005`                                                                   |
| &nbsp;       | OS_CLIENT_SECRET         | 56160ec2-17d1-4047-a42a-e6f9f70a3179                                               |
| &nbsp;       | OS_ACCESS_TOKEN_ENDPOINT | `https://idp.ukcloud.com/auth/realms/client-assured/protocol/openid-connect/token` |

**Now save your changes and close the file.**

Your OpenStack RC file is now ready to be used as normal.

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
