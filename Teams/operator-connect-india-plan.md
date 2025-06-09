---
title: Plan for Operator Connect for India
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.date: 12/13/2024
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
ms.reviewer: roykuntz
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn more about Operator Connect for India, such as requirements and planning for deployment.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Plan Operator Connect for India

Operator Connect for India is a country-specific method for providing Public Switched Telephone Network (PSTN) connectivity to your tenant and PSTN access to Teams Phone users in India. Operator Connect for India is designed to comply with India’s telephony regulatory requirements and provide customers an alternative to Direct Routing. This article is intended to help IT pros and enterprise telecom admins.

## Prerequisite knowledge

- [PSTN connectivity options](pstn-connectivity.md)
- [Operator Connect as a PSTN connectivity option](operator-connect-plan.md)

## Licensing, requirements, and considerations

You can integrate India telephone numbers into your tenant through Microsoft's *Operator Connect for India* solution, which mimics the Operator Connect solution for other countries and regions, but is different in that it also delegates Teams Phone licensing to the India operator.

With Operator Connect for India:

- **You need to acquire the India-specific Microsoft Teams Phone license from a licensed telecom operator in India.** This requirement must be met even if you have an existing Teams Phone entitlement. For example, if you have a Teams Phone entitlement included with an E5 license, you still need to an India-specific Microsoft Teams Phone license. The India Teams Phone license is purchased from the India operator of your choice.

### Wireline and Wireless number types in India

In India regulatory terms, telephone numbers are categorized as either wireline numbers or wireless numbers. The number type categories refer to the ability or inability to roam within the country.

- ***Wireline*** numbers require the user to be collocated in an assigned site when they're using the wireline number to access the PSTN.

  - When India wireline numbers are used, Location Based Routing must be implemented.  

- ***Wireless*** numbers require the user to be located within the country of India but permit the user to roam within the country.

  - When India wireless numbers are used, the user must consent to share their location, at the time of establishing connectivity to the PSTN.
    - Teams client prompts the user for consent and use location services in the operating system of the user's device to share with the operator.
    - Teams client doesn't show the dial button for users whom are assigned an India wireless number but haven’t consented to share their location to Teams.
- The user location data may be shared with the Operator Connect for India partners to fully enable PSTN calling scenarios. Microsoft doesn't store and retain this user location data.
- Location Based Routing and network sites / subnets, which are used to determine the location of a user who is assigned a wireline number, aren't used with wireless numbers.

The controls for PSTN Access and toll bypass are automatically recognized in Teams Phone according to the number type provided by the India operator.

Operator Connect for India supports both number types and Microsoft's method of supporting compliance of both follows:

|**Number type**|**PSTN Access permissions**|**Microsoft's Access control**|
|:--- |:---: |:---: |
|Wireline numbers | Users are permitted to access PSTN only when collocated in the Network Communication Server (NCS) site that is associated with the number. | [Teams Location Based Routing](location-based-routing-india-plan.md) |
|Wireless numbers | Users are permitted to roam and access PSTN from any region within India. | [Location services](https://support.microsoft.com/windows/windows-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088) in the operating system of the user’s device  |

- Operator Connect for India wireless numbers aren't integrating with the user’s mobile phone SIM. Teams Phone Mobile is currently not supported in India.

- The India Teams Phone license available from the Operator Connect for India partners supports both India wireline and wireless numbers.

> [!IMPORTANT]
> Wireline and wireless numbers aren't interchangeable. Prevent unplanned outcomes and extra deployment costs by acquiring the correct number type when purchasing Teams Phone licenses from your India telecom operator. When ordering numbers, specify which type of service you need for each number: wireline or wireless.


- Teams Phone for India supports the entitlement model for [Teams Phone Resource Account licenses](teams-add-on-licensing\virtual-user.md).
  - Resource accounts for Auto attendants and Call Queues can be assigned with Operator Connect for India numbers. The resource accounts are provisioned as described in [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md), and don't require the India Teams Phone license.

- The users in scope must be in **TeamsOnly** mode. It isn't required for the entire organization to be in TeamsOnly mode, but the users getting provisioned with Operator Connect in India must be in TeamsOnly mode. To learn more, see Understand [Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).

- Operator Connect for India wireless numbers aren't supported by Teams Phone devices, SIP Device Hub devices, Microsoft Teams Room systems, Teams web client, or custom clients developed with Azure Communications Services' client SDK.

- It isn't possible to convert wireline numbers to wireless numbers.

- For technical support, contact the customer support of your operator first.  If the partner determines the issue is with Microsoft, they might ask you to raise a case with Microsoft, providing context of the investigation completed by the partner. If needed, the partner can bring the issue to Microsoft through their Microsoft support channel. Microsoft might reject support cases if investigation shows that the issue is one that the partner can address.

- India has a regulated deployment category, known as “other service provider (OSP)”, that allows calls in this type of deployment to egress out of India through your private network, bypassing India PSTN toll. OSP deployments are typically used for call centers and entitlement is arranged by the customer through India’s Department of Telecommunications. For purposes of this article, the deployment is considered non-OSP  and adheres to toll regulations. Microsoft support for Other Service Provider (OSP) calls with international telephone numbers is pending.

## Next steps

For next steps, including selecting your Operator Connect for India partner, see [Configure Operator Connect for India](operator-connect-india-configure.md).

## Related articles

- [Configure Operator Connect for India](operator-connect-india-configure.md)
- [Plan and configure Location-Based Routing for Operator Connect for India](location-based-routing-india-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)