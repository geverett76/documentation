---
title: Snapshot Protection Service Scope
description: Outlines important details regarding the Snapshot Protection service
services: vmware
author: shall
reviewer: gmartin
lastreviewed: 26/09/2022 
toc_rootlink: Service Information
toc_sub1: 
toc_sub2:
toc_sub3:
toc_sub4:
toc_title: Snapshot Protection Service Scope
toc_fullpath: Service Information/vmw-sco-snapshot-protection.md
toc_mdlink: vmw-sco-snapshot-protection.md
---

# Snapshot Protection

## About this document

This document explains what is and isn't included in the scope of the Snapshot Protection service option.

Snapshot Protection is one of a variety of on‑platform protection options available from UKCloud. Use this service scope to understand Snapshot Protection and whether it will meet your own recovery point (RPO) or recovery time (RTO) objectives.

## About Snapshot Protection

UKCloud offers a choice of snapshot options that operate as a daily backup service for customers using our VMware‑based compute services.

You can choose from the following Snapshot Protection policies:

- 14‑day snapshot

- 28‑day snapshot

When you opt a virtual machine (VM) into a Snapshot Protection policy, the VM is added to a daily automated snapshot. The snapshot is of the entire VM running on your UKCloud for VMware service.

Data protected by the snapshot has an RPO of 24 hours. RTO is determined by the time taken to restore the VM after you've raised a Service Request.

Snapshot Protection is chargeable based on the number of VMs protected and the capacity utilised to store the data.

No protection products are automatically applied to VMs running on the UKCloud platform, therefore you must explicitly select the protection option that best meets your requirements.

## Frequency and timing

Snapshots are scheduled to occur once in a 24-hour period.

Snapshots take place 365 days of the year and are started inside the UKCloud‑defined window: 20:00-08:00. Snapshots are not started before 20:00 or after 08:00.

We cannot guarantee the time at which your VM will have a snapshot taken inside this window; the time may also vary from day to day. The time of a snapshot is reported via the UKCloud Portal the next day.

There's a system hard stop at 09:00, at which time any active snapshots are cancelled.

Due to the higher rate of new data on a VM's initial snapshot backup, each new VM is automatically configured with 'overtime' enabled on it's first backup. This enables it to run to successful completion beyond the standard backup window (20:00-08:00) if required. This helps to ensure the initial backup completes on the first attempt, particularly for large or high change rate VMs. The flag is removed after the first successful backup.

### Success rate

We do not guarantee successful snapshots.

We can provide you with guidance on suitable candidates for Snapshot Protection (data change rate/size).

For regions 1, 2, 7 and 8, large VMs (2 TiB+) with high change rates are not recommended for Snapshot Protection, as the service will spend longer trying to establish what has changed and then attempt to back all of it up. You should take an alternative backup approach with VMs of this size in these regions.

For regions 5, 6, 13 and 14, you can use Snapshot Protection for large VMs. However, you should still consider the impact of recovery time for large VMs.

VM snapshots may be attempted more than once to obtain successful status.

Only the final state will count in our calculations.

Partial snapshots and those with errors count as failed.

Any snapshots still in progress at 09:00 are considered as failed.

Due to the higher rate of new data on a VM's initial snapshot backup, each new VM is automatically configured with 'overtime' enabled on it's first backup. This enables it to run to successful completion beyond the standard backup window (20:00-08:00) if required. This helps to ensure the initial backup completes on the first attempt, particularly for large or high change rate VMs. The flag is removed after the first successful backup.

### Reruns

We may attempt to rerun a failed snapshot inside the window, depending on the failure code.

We will not rerun snapshots outside the window.

### What SLA do you offer on snapshot success?

Automated VM snapshots don't include an SLA. You should be aware that snapshots may occasionally fail for a variety of reasons. The status of automated VM snapshots is monitored continuously, and the UKCloud support team investigates all failures.

It isn't always possible to rerun an automated VM snapshot, if this service doesn't meet your own protection requirements, we can also offer Journaling Protection options.

If none of these services meet your requirements, you can also implement and manage your own protection solution.

The UKCloud Cloud Storage platform may be an appropriate target for self‑managed solutions using software such as CommVault and NetWorker.

The service is not backed by service credits.

### Planned Maintenance

On occasion, Planned Maintenance will take precedence over VM snapshots. If there's a potential disruption, we'll highlight this to you via the [UKCloud Service Status page](https://status.ukcloud.com/).

## Snapshot management

You can make changes to your Snapshot Protection via the UKCloud Portal. You can:

- Opt VMs into Snapshot Protection

- Change the Snapshot Protection policy for a VM

- Opt VMs out of Snapshot Protection

- Set a default Snapshot Protection policy for a VDC

## Alerting and reporting

Information about your backups is reported on the UKCloud Portal. Reports are updated daily and are available by 10:00, but typically within minutes of the close of the backup window.

Reports are available covering every day of the retention period (14 or 28 days as appropriate).

Alerting on individual VMs is not provided.

## Restores

### Timing and process

You can ask to restore a VM by raising a Service Request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal, which is subject to standard support SLA timescales.

Restores are performed outside of the backup window, unless a P1 incident is involved. You can find a definition of our support processes and severity categorisation in [*Raising and escalating support tickets with customer support*](../portal/ptl-ref-raise-escalate-service-request.md).

### What you get

We'll instantiate a new VM. This will incur additional storage charges.

We'll provide an image from a successful snapshot of your choice from within the policy length (that is, the last 14 or 28 days).

You'll need to make any necessary switchover/networking changes.

### Fair use policy

You can request up to four restores per month. If you request more than this, we will suggest a Cloud Architect investigate.

The total number of VMs (or disks) in a restore request should not exceed five.

## KPIs

We'll proactively investigate failures on the platform on the following triggers:

- Individual customer VM:

  - Two successive snapshot window failures

  - A failure of three snapshots in 14 days

- Platform:

  - More than 50 missed VMs (VMs that should be in policy, but have not been backed up)

  - Less than 99% success rate for VM snapshot

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
