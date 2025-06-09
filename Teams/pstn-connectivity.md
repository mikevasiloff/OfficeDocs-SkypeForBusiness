---
title: PSTN connectivity options
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.date: 04/25/2025
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - M365-voice
  - m365initiative-voice
  - m365solution-voice
  - m365solution-scenario
  - highpri
  - Tier1
ms.reviewer: filippse
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.cloudvoice
  - seo-marvel-apr2020
  - seo-marvel-may2020
search.appverid: MET150
description: Learn more about Teams calling (PSTN connectivity) options and the decisions that you'll make for your organization.
appliesto: 
  - Microsoft Teams
---

# PSTN connectivity options

The Public Switched Telephone Network (PSTN) is a network whereby national, regional, and local telephone service providers connect their subscribers with each other. A PSTN service provider might also be referred to as a carrier, an operator, or simply ‘the telephone company’.

In order to use PSTN telephony services with Teams Phone, the user account must be licensed with the Teams Phone application and also be equipped with a PSTN solution from your PSTN service provider of choice.

The PSTN service provider serves as your partner to provide your M365/Teams users with the basic requirements of:

- access to the PSTN (for making/receiving telephone calls)
- allocation of telephone numbers for your enterprise.

A secure PSTN integration with your Teams tenant is required before any licensed Teams Phone accounts can be provisioned to make and receive telephone calls.

In this section, we will discuss options for connecting your tenant with the Public Switched Telephone Network (PSTN).

## PSTN connectivity options

Microsoft’s Teams Phone is a highly flexible platform, supporting several methods to connect with the PSTN, and you can equip your tenant with as many of the available PSTN integrations as you’d like.

A visual reference of PSTN connectivity options follows:

:::image type="content" source="media/PSTN-connectivity-options-small.png" alt-text="Diagram of PSTN connectivity options to M365 Teams tenant." lightbox="media/PSTN-connectivity-options-expandable.png":::

The highlights of the four PSTN connectivity models for Teams are as follows:

- [**Microsoft Teams Calling Plan**](calling-plans-for-office-365.md). A fully integrated, cloud solution with Microsoft as your PSTN operator. Calling Plans are Microsoft licenses that can be tailored to the calling behavior of your user base. PSTN access, phone numbers, emergency screening service in the U.S., and support for your telephone service come from Microsoft, with a 99.999% reliability Service Level Agreement (SLA).
  - This option requires a Microsoft Teams Calling Plan license.

- [**Operator Connect**](operator-connect-plan.md). With the Operator Connect offer, take advantage of certified third-party landline operators who have already completed the PSTN integration with Microsoft. All that is required is a subscription from the certified service provider of your choice. You can easily enable their access to your tenant in the Teams Admin Center and assign their phone numbers to your Teams users. PSTN access, phone numbers, emergency screening service in the U.S., support, SLA and other products for your telephone service come from the certified Operator Connect partner.
  - This option requires a contract with a third-party service provider.
  - For this PSTN connectivity solution in India, see [Operator Connect for India](operator-connect-india-plan.md).

- [**Teams Phone Mobile**](operator-connect-mobile-plan.md). With Microsoft Teams Phone Mobile, take advantage of certified third-party mobile operators, who have already completed the PSTN integration with Microsoft. All that is required is a subscription from the certified mobile operator of your choice. You then administer mobile numbers that are assigned to the user’s mobile SIM to also be assigned as the user’s Teams phone number. PSTN access, phone numbers, emergency screening service in the U.S., support, SLA, and other products for your telephone service come from the certified Teams Phone Mobile partner.
  - This option requires a contract with a third-party service provider.

- [**Direct Routing**](direct-routing-plan.md). With the Direct Routing model, you can use any PSTN operator. Integration of your preferred PSTN operator’s access to your tenant is achieved through a certified Session Border Controller (SBC) that is procured, installed, and managed by you, your integrator, or a Direct-Routing-as-a-Service (DRaaS) provider. PSTN access, phone numbers, emergency screening service in the U.S., support, SLA, and other products for your telephone service come from a combination of your PSTN partner and you.'
  - This option requires a contract with a third-party service provider and a session border controller solution.

## PSTN connectivity types comparison

The following table highlights the primary configuration differences. The sections that follow the table provide links to more information and details.

| Consideration | Microsoft Calling Plan | Operator Connect | Teams Phone Mobile | Direct Routing |
| :------------| :-------| :-------| :-------| :-------|
| The PSTN Service Provider | Microsoft| Certified landline operator | Certified mobile operator | Any operator |
| Infrastructure to manage | None | None | Mobile SIM <br> (can be e-SIM) | Physical or virtual certified session border controller (SBC), hosted by you or your service provider, including certificate management, DNS/FQDN settings, and last mile circuit integration to SBC |
| Phone number acquisition | Obtained through Microsoft | Obtained through Operator Connect operator | Obtained through Teams Phone Mobile operator | Obtained through operator |
| Emergency screening service | Included | Optional | Optional | Optional |
| Registered address for Emergency calling | Included. Teams Admin manages | Optional, enabled and managed by operator | Optional, enabled and managed by operator | Not supported |
| Dynamic location information for emergency calling | Supported | Supported | Supported | Supported, but requires additional configuration |
| Call routing | Managed by Microsoft. Teams admin option to configure dialed number translation | Managed by operator. Teams admin option to configure dialed number translation | Managed by operator. Teams admin option to configure dialed number translation | Requires dialed number translation, routing policy, and usage policy configurations in Teams, plus SBC routing configuration |
| Location Based Routing to restrict toll bypass | N/A | N/A | N/A | Supported |
| Local office PSTN survivability in event of interruption to cloud service | N/A | N/A | N/A | Yes, with Survivable Branch Appliance |
| Support | Microsoft | Operator + Microsoft | Operator + Microsoft | Operator + SBC vendor + Microsoft |
| Phone number management | Teams admin center | Teams admin center | Teams admin center | Teams admin center and SBC, optionally with operator |

## PSTN connectivity considerations

Teams Phone with **Microsoft Teams Calling Plan** could be a good solution if:

- Microsoft Teams Calling Plan is available in your region.
- You don't need to retain your current PSTN service provider.
- You want to use Microsoft-managed PSTN services.

Teams Phone with **Operator Connect** could be a good solution if:

- Microsoft Teams Calling Plan isn't available in your geographic location.
- Your preferred carrier is a participant in the Microsoft Operator Connect program.
- You want to find a new service provider to enable calling in Teams.

Teams Phone with **Teams Phone Mobile** could be a good solution if:

- You want to use a SIM-enabled mobile number with Teams Phone as a single number solution.
- Your preferred mobile service provider is a participant in the Microsoft Teams Phone Mobile program.
- You want to find a new service provider to enable calling in Teams.

Teams Phone with **Direct Routing** could be a good solution if:

- You want to use Teams with Teams Phone in any country or region.
- You need to retain your current PSTN service provider.
- You need to interoperate Teams with third-party PBXs and/or equipment such as overhead pagers, analog devices, and so on.

## Use more than one PSTN connectivity type

You can also choose a combination of options, which enables you to design a solution for a complex environment and you can manage the PSTN integrations over time, in any order.
For example, you might use an approach where you:

1. Set up **Microsoft Calling Plans** with *Shared Calling* for everyone
1. Circle back with more prescriptive PSTN connectivity options for different persona types in your enterprise, for example:
    1. **Teams Phone Mobile** for *mobile workers*,
    1. **Operator Connect** for *knowledge workers*, and
    1. **Direct Routing** for *workers in remote regions*.


## Related topics

- [Plan Microsoft Teams Calling Plans](calling-plan-landing-page.md)
- [Plan Operator Connect](operator-connect-plan.md)
- [Plan Teams Phone Mobile](operator-connect-mobile-plan.md)
- [Plan Direct Routing](direct-routing-plan.md)
- [What's included with Teams Phone](here-s-what-you-get-with-phone-system.md)
- [Network settings for cloud voice features in Microsoft Teams](cloud-voice-network-settings.md)
- [Plan emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Plan shared calling](shared-calling-plan.md)
- [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md)
