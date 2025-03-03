---
title: PSN for Policing and enhanced regime FAQs
description: Frequently asked questions for PSN for Policing and enhanced regime
services: connectivity
author: mwarner
reviewer: nstobbart
lastreviewed: 07/12/2021
toc_rootlink: FAQs
toc_title: PSN for Policing and enhanced regime FAQs
toc_fullpath: FAQs/conn-faq-psn-police.md
toc_mdlink: conn-faq-psn-police.md
---

# PSN for Policing and enhanced regime FAQs

## What is PSN for Policing?

The Public Services Network for Policing is a closed user group (CUG) operated by Vodafone over the PSN, using cryptographic overlays, connecting all UK police forces. Supplier CUGs are also available.

## What is the Enhanced Regime?

The Enhanced Regime is sometimes referred to as the PSN in Policing (Protect), which is a set of controls over and above the encryption that is run on parts of the PSN that were PSN Protected (PSN-P) when it was a separate network to PSN Assured (PSN-A). It's generally used to exchange data between police and non-police organisations.

## Why are there two policing networks?

Legacy PSN-P was based on the Inter-Provider Encryption Domain (IPED) to enable multiple DNSPs to provide competition. Since the merge of PSN-A and PSN-P this IPED still exists with those connections that were PSN-P before the flattening, however the downside of IPED is that it introduces latency issues and throughput concerns. There were also a lot of non-police organisations on the PSN-P so police had less trust of this community. Due to this, non-police organisations use the PSN-P with additional controls (Enhanced Regime), as this is easier to consume, but police use the CUG over the PSN (PSN for Policing).

## Can data get between the PSN for Policing CUG and the Enhanced Regime?

Yes. There are gateways, external to UKCloud that allow data to traverse the two networks. This is managed and controlled by Vodafone. For questions relating to this gateway please contact Vodafone or the PSN for Policing Authority.

## How do I get on the PSN for Policing or the Enhanced Regime?

You will need to contact the PSN for Policing Information Assurance team: (<information.assurance@homeoffice.pnn.police.uk>)

- The first stage is for Policing to confirm that there is a business requirement for the organisation (organisation/system/service) to connect to policing - so partners need a sponsoring force or department.

- Secondly it will be confirmed about how they should connect to Police.

- Then it should be confirmed that the supplier meets the necessary IA requirements. Design docs / RMADs / Code of Connection templates should be sent to the IA team - they review and then pass to GDS for approval.

- The supplier will then be granted code of connection by the PSN for Policing IA team.

- The supplier will need to liaise with UKCloud, Vodafone and the Home Office to get connectivity to the relevant network, as directed by the PSN for Policing Authority.

## Can I connect directly to the UKCloud Elevated OFFICIAL platform using a PSN for Policing CUG?

Yes. The PSN for Policing the connection will be installed as a private circuit into UKCloud, provided and managed by Vodafone. This means it can be terminated in the Elevated Cloud platform. Please see our [*HybridConnect FAQs*](conn-faq-hybridconnect.md) for more information around connecting your own line into the UKCloud platform.

## Can I connect directly to the UKCloud Elevated OFFICIAL platform using the Enhanced Regime?

Yes. The Enhanced Regime is a set of additional controls over what was the PSN-P, which terminates in the Elevated platform.

## Can I connect directly to the UKCloud Assured OFFICIAL platform using a PSN for Policing CUG?

Yes. As the connection is installed as a private circuit into UKCloud, provided and managed by Vodafone, you can terminate it into the Assured Official platform. It's worth remembering that the PSN for Policing Authority may influence where this connection is terminated.

## Can I have a combination of government community networks and private accredited networks into the same UKCloud solution, including the PSN for Policing networks?

Yes, subject to compliance with information assurance requirements, as only organisations that demonstrate compliance with the appropriate code of connection (for example PSN compliance certificate or HSCN Connection Agreement) can have access to government community networks.

You should be careful not to misconfigure self-managed components of the solution (OS, application) to 'bridge' between government community networks (PSN) and private networks. This concern must be addressed by accreditation of the customer-managed components - preferably via PSN Accreditation. Local departmental accreditation by a public-sector customer is also allowed. This applies to solutions on both our Assured OFFICIAL and Elevated OFFICIAL cloud platforms.

## What if I have been given some IPs for connection to the Enhanced Regime?

You'll need to liaise with Vodafone to ensure that these IPs are associated with your service within UKCloud. You may be asked by Vodafone for your circuit reference numbers. Raise a service request via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal to obtain these.

You'll then need to have these IPs added to your accounts. You can do this via a service request. UKCloud may need to work with Vodafone to advertise these IPs, which can take up to 10 days to facilitate. Once complete, you'll then be able to provide your service over the new IPs.

## Can I swap out my existing PSN IPs for Enhanced Regime IPs?

Yes. The process is the same as above except there may be an element of disruption to the service as the IP addresses are exchanged.

You should liaise with UKCloud to find a suitable time to do this, to minimise any disruption.

## How do I get PSN for Policing or Enhanced Regime IP addresses?

If you are connected to a PSN for Policing CUG, you'll be provided with an IP range by Vodafone.

If you are connected to the Enhanced Regime, you'll be provided an IP range by Home Office. You'll need to raise a service request with us via the [My Calls](https://portal.skyscapecloud.com/support/ivanti) section of the UKCloud Portal to have these IPs added to the UKCloud firewalls. This may have a lead time of a few days.

## How long is the lead time to get a PSN for Policing network connected to my solution?

This varies depending on the solution and the network you want to connect to. It will take time to gain the accreditation needed through the PSN for Policing Authority. There will then be a lead time to get the connectivity provisioned into your solution.

- When connecting to a PSN for Policing CUG, you'll need to wait for Vodafone to provision the connectivity into the UKCloud data centres. Because of this you'll need to factor in an extended lead time.

- When connecting to the Enhanced Regime you'll need to obtain IPs from the Home Office and have them made available to your solution by UKCloud. This will have a shorter lead time to implement that a CUG network, however it may still take a few weeks to do.

## How much does the PSN for Policing networks cost?

The PSN for Policing CUG will be provided by Vodafone as a single-tenant installation so will be treated as a leased line. There will be Vodafone charges for this service that are outside of UKCloud's control. UKCloud will treat this as a HybridConnect service and will bill accordingly. For more information, see the [*HybridConnect FAQs*](conn-faq-hybridconnect.md).

The Enhanced Regime has additional controls over the PSN and as such customers will be billed in accordance with PSN pricing. For more information, see the [*PSN FAQs*](conn-faq-psn.md).

## General connectivity questions

If you have questions about connectivity in general, see the [*General connectivity FAQs*](conn-faq.md).

## Feedback

If you find a problem with this article, click **Improve this Doc** to make the change yourself or raise an [issue](https://github.com/UKCloud/documentation/issues) in GitHub. If you have an idea for how we could improve any of our services, send an email to <feedback@ukcloud.com>.
