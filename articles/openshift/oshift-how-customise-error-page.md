---
title: How to customise the OpenShift router error page
description: Explains how to change the Application Not Available (503) error page served by the OpenShift routers
services: openshift
author: gellner
reviewer: gellner
lastreviewed: 05/01/2022

toc_rootlink: How To
toc_sub1: OpenShift v3.x
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Customise the router error page
toc_fullpath: How To/oshift-how-customise-error-page.md
toc_mdlink: oshift-how-customise-error-page.md
---

# How to customise the OpenShift router error page

## Overview

UKCloud for Red Hat OpenShift enables you to develop, deploy, and manage digital and container-based applications seamlessly across local physical or virtual environments, with full portability to and from UKCloud.

This article explains how you can edit the *Application Not Available* (503 error) page, which is returned to users by OpenShift routers when an application is unavailable or when an invalid route is accessed.

### Intended audience

This article assumes familiarity with the Linux command line, and with the `oc` command set to manage an OpenShift cluster.

### Prerequisites

To complete the steps in this article, you must have the `oc` command installed and have a suitable account on your OpenShift cluster. Specifically, it is assumed you know the authentication credentials that need to be supplied to `oc login`. Your account must have access to edit objects in the "default" project.

Your OpenShift cluster must be version 3.x.

## Editing the Application Not Available page

1. On your client PC, create a file called `error-page-503.http` containing the HTML required for the custom error page with the following headers at the top of the file:

    ```html
    HTTP/1.0 503 Service Unavailable
    Pragma: no-cache
    Cache-Control: private, max-age=0, no-cache, no-store
    Connection: close
    Content-Type: text/html

    <html>
    <head>
    ...
    ```

2. Create a configmap to pass this file into the router pods:

    ```none
    $ oc project default
    $ oc create configmap haproxy-custom-configs --from-file=error-page-503.http
    ```

3. Attach the configmap as a volume to the router deployment config:

    ```none
    $ oc set volume dc/router --add --name custom-configs -t configmap --configmap-name=haproxy-custom-configs -m /var/lib/haproxy/conf/error-page-503.http --sub-path=error-page-503.http
    ````

5. If your cluster is multi-network (connected to HSCN, VRF, and so on), you may want to repeat this for the router-private configmap so that the private network routers also serve the custom page:

    ```none
    $ oc set volume dc/router-private --add --name custom-configs -t configmap --configmap-name=haproxy-custom-configs -m /var/lib/haproxy/conf/error-page-503.http --sub-path=error-page-503.http
    ```

## Reverting to the default Application Not Available page

To revert the above changes and return to the default error page, run the following:

```none
$ oc set volume dc/router --remove --name custom-configs
$ oc set volume dc/router-private --remove --name custom-configs # (if router-private was edited)
$ oc delete configmap haproxy-custom-configs
```

## Next steps

For more information about the UKCloud for Red Hat OpenShift service, see:

- [*Getting Started Guide for UKCloud for Red Hat OpenShift*](oshift-gs.md)

- [*UKCloud for Red Hat OpenShift FAQs*](oshift-faq.md)

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
