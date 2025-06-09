--- 
title: Manage anonymous participant access to Teams meetings, webinars, and town halls (IT admins)
author: wlibebe
ms.author: wlibebe
manager: pamgreen
ms.reviewer: jaydenlee
ms.date: 03/28/2025
ms.topic: how-to
ms.service: msteams
ms.subservice: meetings
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier1
  - m365initiative-meetings
ms.custom: guest-access-external-collab
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: For IT Pros - Learn how anonymous meeting participation works in Microsoft Teams.
---

# Manage anonymous participant access to Teams meetings, webinars, and town halls (IT admins)

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

In meetings, webinars, and town halls hosted by your organization, anonymous users are users whose identities aren't verified. These users could include:

- Users who aren't logged in to Teams with a work or school account.
- Users from non-trusted organizations (as configured in [external access](trusted-organizations-external-meetings-chat.md)) and from organizations that you trust but which don't trust your organization. When defining trusted organizations for external meetings and chat, ensure both organizations allow each other's domains. Meeting organizers and participants should have user policies that allow external access. These settings prevent attendees from being considered anonymous due to external access settings. For details, see [IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md)

As an admin, you have the following options to manage anonymous meeting join for your organization:

- The organization-wide **Anonymous users can join a meeting** setting.
- The per-organizer **Anonymous users can join a meeting unverified** policy setting.
- **Teams Premium**: The per-organizer **Anonymous users can join a meeting after verifying meeting** policy setting that allows anonymous users to join meetings after verifying through a one-time passcode. Only organizers with a Teams Premium license can use this feature.

Your organizers have the following settings in their **Meeting options** to manage anonymous meeting join for their meetings:

- **Require unverified participants to verify their info before joining**

When anonymous users join a meeting unverified, **Unverified** appears next to their name. If anonymous users join a meeting verified through a one-time passcode, **Email Verified** appears next to their name. When a user signs in to their Microsoft account, **External** appears next to their name.

> [!IMPORTANT]
> The **Anonymous users can join a meeting** organization-wide setting is going away. We recommend leaving this setting **On** and using the **Anonymous users can join a meeting unverified** per-organizer meeting policy to manage anonymous meeting join instead.

When anonymous meeting join is turned on, lobby policies affect how anonymous participants join meetings. For details, see [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

## Anonymous users can join a meeting

You can control whether anonymous users can join meetings for your entire organization or for specific organizers and groups.

### Organization-wide

To allow everyone in your organization to create meetings that allow anonymous users, you must turn on this organization-wide setting. When this setting is turned off, anonymous users can't attend meetings hosted by anyone in your organization.

To manage anonymous meeting join for your entire organization, follow these steps:

1. Go to the Teams admin center.
2. Expand **Meetings** > **Meeting settings**.
3. Under **Meeting Join and Lobby**, toggle the **Anonymous users can join a meeting** setting **On** or **Off**.
4. Select **Save**.

### Per-organizer

To control which users or groups can host meetings that allow anonymous participants, assign a per-organizer meeting policy to each organizer or group. If the organization-wide **Anonymous users can join a meeting unverified** setting is on, you can turn off this policy to prevent specific organizers from creating meetings that allow anonymous users to join.

To manage anonymous meeting join for specific meeting organizers, follow these steps:

1. Go to the Teams admin center.
2. Expand **Meetings** > **Meeting policies**.
3. Select an existing policy or create a new one.
4. Under **Meeting Join and Lobby**, toggle the **Anonymous users can join a meeting unverified** setting **Off**.
5. Select **Save**.

Changes to meeting policies might take up to 24 hours to take effect.

### Organizer control

When you turn on the organization-wide **Anonymous users can join a meeting** or per-organizer **Anonymous users can join a meeting unverified** setting, your organizers see the **Require unverified participants to verify their info before joining** setting in their **Meeting options**. This setting is off by default, allowing unverified participants to join meetings. However, organizers can choose to turn on this setting for specific meetings to restrict access. If you turn off the organization-wide **Anonymous users can join a meeting** or per-organizer **Anonymous users can join a meeting unverified** policy setting, organizers can't configure this meeting option.

## Anonymous users can join a meeting after verifying with an email code (Teams Premium)

> [!NOTE]
> This feature requires organizers to have a Teams Premium license.
>
> This feature isn't supported for webinars or town halls.

You can require anonymous users to verify their identities to join meetings in your organization.

When you set **Anonymous users can join a meeting after verifying** to **By email code** and the meeting organizer toggles the **Require unverified participants to verify their info before joining** setting to **On** in their **Meeting options**, unverified anonymous users are prompted to enter up a one-time passcode that gets sent to their email to join the meeting.

If you turn off the organization-wide **Anonymous users can join a meeting** setting and **Anonymous users can join a meeting after verifying** is set to **No**, anonymous users can't join meetings in your organization.

:::image type="content" source="media/prejoin-email-small.png" alt-text="Screenshot of an anonymous user entering their email on the prejoin screen to verify their identity to join a meeting" lightbox="media/prejoin-email-large.png":::

:::image type="content" source="media/prejoin-mobile-code-small.png" alt-text="Screenshot of an anonymous user entering a onet-time passcode on the prejoin screen to verify their identity to join a meeting" lightbox="media/prejoin-mobile-code-expand.png":::

To manage whether unverified anonymous attendees can verify themselves with a one-time passcode to join meetings, follow these steps:

1. Go to the Teams admin center.
1. Expand **Meetings** > **Meeting policies**.
1. Under **Meeting Join and Lobby**, in the drop-down for **Anonymous users can join a meeting after verifying**, select **By email code** or **No**.
1. Select **Save**.

## Manage anonymous meeting join using PowerShell

### Manage whether anonymous participants can join meetings

The **`-DisableAnonymousJoin`** parameter controls whether anonymous users can join meetings for your organization, while the **`-AllowAnonymousUsersToJoinMeeting`** parameter controls this setting at the user or group level. You can use these parameters together to manage how anonymous users join meetings in your organization. For example, when you set **`-DisableAnonymousJoin`** to false for the organization, anonymous users can join meetings in your organization. If you also set **`-AllowAnonymousUsersToJoinMeeting`** to false for a specific user, that user can't create meetings that anonymous users can attend, even though the organization-wide setting allows it.

#### For your organization

We recommend leaving **`-DisableAnonymousJoin`** set to False and using the **`-AllowAnonymousUsersToJoinMeeting`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to manage anonymous meeting join at the user or group level.

To allow anonymous participants to join meetings in your organization, use this script:

```powershell
Set-CsTeamsMeetingConfiguration -Identity <policy name> -DisableAnonymousJoin $false
```per-organizer
To prevent anonymous participants from joining meetings in your organization, use this script:

```powershell
Set-CsTeamsMeetingConfiguration -Identity <policy name> -DisableAnonymousJoin $true
```

#### For specific organizers

To allow anonymous participants to join meetings organized by users or groups with this policy, use this script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowAnonymousUsersToJoinMeeting $true
```

To prevent anonymous participants from joining meetings organized by users or groups with this policy, use this script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowAnonymousUsersToJoinMeeting $false
```

### Allow anonymous users to join a meeting after verifying an email code

To allow unverified anonymous attendees to verify themselves with a one-time passcode to join meetings (default value), use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AnonymousUserAuthenticationMethod OneTimePasscode
```

To prevent unverified anonymous attendees from verifying their identity to join meetings, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AnonymousUserAuthenticationMethod None
```

### Block anonymous meeting join for specific client types

When anonymous participants are allowed to join meetings, they can use either the Teams client or a custom client built using [Azure Communication Services](/azure/communication-services/).

Admins can block either of these client types by using the `-BlockedAnonymousJoinClientTypes` parameter. To learn more, see [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy#-blockedanonymousjoinclienttypes).

## Anonymous participants' meeting experience

Anonymous participants don't have all the same capabilities as other meeting participants. For example, anonymous participants:

- Don't have access to meeting chat before and after the meeting
- Don't have access to [profile cards](https://support.microsoft.com/office/e80f931f-5fc4-4a59-ba6e-c1e35a85b501)
- Don't have access to collaborative meeting notes.

### How anonymous participants interact with apps in meetings

By default, the setting to allow anonymous participants to interact with apps in meetings is enabled. Anonymous participants inherit the *Global (Org-wide default)* Teams apps permission policy. Anonymous participants can interact with apps in Teams meetings as long as the app is turned on in that policy and **Anonymous participants can interact with apps in meetings** is **On**.

Anonymous participants can only interact with apps that are already available in a meeting and can't add or manage these apps.

To manage app access for anonymous meeting participants, follow these steps:

1. Go to the Teams admin center.
1. Expand **Meetings** > **Meeting settings**.
1. Under **Meeting Join and Lobby**, set  **Anonymous participants can interact with apps in meetings** to **On** or **Off**.
1. Select **Save**.

#### PowerShell

To allow anonymous participants to interact with apps in meetings, use this script:

```powershell
Set-CsTeamsMeetingConfiguration -Identity <policy name> -DisableAppInteractionForAnonymousUsers $false
```

To prevent anonymous participants from interacting with apps in meetings, use this script:

```powershell
Set-CsTeamsMeetingConfiguration -Identity <policy name> -DisableAppInteractionForAnonymousUsers $true
```

## Related articles

- [Plan for meetings with external participants in Microsoft Teams](plan-meetings-external-participants.md)
- [Join a meeting without a Teams account](https://support.microsoft.com/office/c6efc38f-4e03-4e79-b28f-e65a4c039508)
- [Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md)
- [Using the Microsoft Teams admin center to configure organization-wide policy](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings)
- [External participants receive "Sign in to Teams to join, or contact the meeting organizer"](/microsoftteams/troubleshoot/meetings/external-participants-join-meeting-blocked)
- [Assign policies in Teams – getting started](policy-assignment-overview.md)
