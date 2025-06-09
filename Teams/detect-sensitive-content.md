---
title: Manage whether meetings in your organization can detect sensitive content during screen sharing
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: freda.li
ms.date: 4/30/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
description: Learn how to manage manage whether meetings in your organization can detect sensitive content during screen share.
---

# Manage whether meetings in your organization can detect sensitive content during screen sharing

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

> [!NOTE]
> This feature is currently in Public Preview.

## Overview

As an admin, you can manage whether meetings in your organization can detect sensitive content during screen sharing. When you turn on the **Detect sensitive content during screen sharing** policy setting for organizers with a Teams Premium license, sensitive information like credit card and account numbers in shared screen content is identified during their meetings. When sensitive content is detected, both the presenter and the meeting organizer receive notifications to stop sharing and the presenter sees a **Stop sharing** button. This added layer of protection helps safeguard sensitive data and minimizes accidental disclosure. Organizers with a Teams Premium license can use their **Meeting options** to choose which meetings have this feature.

We currently support the following sensitive content categories in English:

- Credit Card Numbers
- U.S. Bank Account Numbers
- ABA Routing Numbers
- EU Debit Card Numbers
- EU Password Numbers
- EU Driver’s License Numbers
- EU Social Security Numbers
- EU National Identification Numbers
- U.S. Social Security Numbers
- U.S./U.K. Passport Numbers
- U.S. Individual Taxpayer Identification Numbers
- EU Tax Social Security Numbers

This feature is supported on Teams desktop, web, mobile, and video-based screen sharing (VBSS).  

> [!NOTE]
> End-to-end encryption is turned off in meetings where sensitive content detection is turned on.

To learn more about how your users use this feature, see [Sensitive content detection in Microsoft Teams meetings](https://support.microsoft.com/office/sensitive-content-detection-in-microsoft-teams-meetings-11f235f9-a170-4490-8bcb-703019d20a63).

## Manage whether meetings can detect sensitive content in the Teams admin center

To manage whether meetings in your organization can detect sensitive content in the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Either select an existing policy or create a new one.
4. Within your chosen policy, navigate to the **Content Protection** section.
5. Toggle the **Detect sensitive content during screen sharing** setting **On** (default) or **Off**.
6. Select **Save**.

## Related articles

- [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
- [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md)
- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
