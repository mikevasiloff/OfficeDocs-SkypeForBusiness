---
title: Require verification checks to join Teams meetings and webinars in your org
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: ivah
ms.date: 11/30/2024
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: meetings
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
description: Learn how to require verification checks for Microsoft Teams meetings and webinars in your org to prevent bots from joining.
---

# Require verification checks to join Teams meetings and webinars in your org

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png)Town halls

To ensure a seamless meeting experience, it's essential to manage how anonymous and unverified external participants join meetings and webinars within your organization. Anonymous participants include users who join a Teams meeting without signing in, via the Teams web app, or through external meeting platforms.

If anonymous and unverified external are allowed to bypass the lobby, web bots might join and disrupt meetings and webinars. As an admin, you can use this per-organizer policy to enforce human verification checks for these users to join meetings in your organization. Implementing a CAPTCHA challenge helps prevent unwanted web-based bots from joining, recording, and causing disturbances in meetings and webinars. Users can choose between a text CAPTCHA with Latin characters and an audio CAPTCHA in English.

:::image type="content" source="media/captcha-audio-small.png" alt-text="Screenshot of a user named Daniela completing an audio CAPTCHA challenge to join a meeting." lightbox="media/captcha-audio-expand.png":::
:::image type="content" source="media/captcha-text-small.png" alt-text="Screenshot of a user named Daniela completing a text CAPTCHA challenge to join a meeting." lightbox="media/captcha-text-expand.png":::

## Manage verification checks for meetings and webinars in your org

You can use the Teams admin center or PowerShell to manage verification checks for meetings and webinars in your organization.

|Teams admins center policy value |PowerShell setting value | Behavior|
|---------|---------|---------------|
|Not required|NotRequired| **This is the default value**. When organizers with this policy create meetings and webinars, no users in that meeting complete a verification check before joining the meeting.|
|Anonymous users and people from untrusted organizations|AnonymousUsersAndUntrustedOrganizations| When organizers with this policy create meetings and webinars, anonymous users and people from untrusted organizations must complete a verification check before joining the meeting.  |

### Manage verification checks in the Teams admin center

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Meeting join & lobby** section and select one of the following options for **Require a verification check from:**
   - Not required (default)
   - Anonymous users and people from untrusted organizations
6. Select **Save**

### Manage verification checks using PowerShell

To  manage whether a verification check is required for meetings and webinars that organizers with this policy create, use the **`-CaptchaVerificationForMeetingJoin`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

Require anonymous users and users from untrusted organizations to complete a verification check before joining meetings and webinars created by organizers with this policy:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -CaptchaVerificationForMeetingJoin AnonymousUsersAndUntrustedOrganizations
```

Prevent users from completing a verification check before joining meetings and webinars created by organizers with this policy:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -CaptchaVerificationForMeetingJoin NotRequired
```

## Client and platform support

### Supported

Verification checks are supported on the following clients and platforms:

**Clients:** Teams, Outlook

**Platforms:** Desktop, Web, Virtualized Desktop Infrastructure (VDI), and mobile application (iOS and Android)

### Not supported

When participants from the following clients and platforms attend meetings that require a verification check, they join without completing the CAPTCHA challenge:

**Clients:** Cloud Video Interop (CVI), Azure Communication Services (ACS) platform, Meeting Teams Rooms Android devices

**Platforms:** Third party devices

## Related articles

- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
