---
title: Manage who can schedule and attend webinars in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: sherimehmood
ms.date: 11/7/2024
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
description: Learn how to set up webinars and manage who can schedule and attend webinars for IT Admins in Teams.
---

# Manage who can schedule and attend webinars in Microsoft Teams

**APPLIES TO:** ![Image of a x for no](/office/media/icons/cancel-teams.png)Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png)Town halls

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

## Overview

Microsoft Teams offers webinars, a two-way interactive virtual event. As an admin, you can set up and manage who can schedule webinars in your organization.

For more information on how to plan for webinars in your organization, see [Plan for Teams webinars](plan-webinars.md).

To learn more about the webinar experience for your users, see [Get Started with Teams webinars](https://support.microsoft.com/office/42f3f874-22dc-4289-b53f-bbc1a69013e3).

## Manage who can schedule webinars

You can use the Teams admin center or PowerShell to manage who can schedule webinars in your organization.

|Teams admin center value| PowerShell value|Behavior|
|---------|---------------|---------------|
|On|Enabled| **This is the default value.** Users with this policy can create webinars. |
|Off|Disabled| Users with this policy can't create webinars.|

### Manage who can schedule webinars using the Teams admin center

To manage who can schedule webinars through the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Webinars** setting **On** or **Off**.
6. Select **Save**.

### Manage who can schedule webinars using PowerShell

You can use PowerShell to manage who can schedule webinars in your organization.

To manage who can schedule webinars, use the **`-AllowWebinars`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

#### Turn off webinars

To prevent organizers with this policy from creating webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Disabled
```

#### Turn on webinars

To allow organizers with this policy to create webinars, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinars Enabled
```

## Manage who can attend webinars

You can use the Teams admin center or PowerShell to manage who can attend webinars in your organization.

|Teams admin center value| PowerShell value|Behavior|
|---------|---------------|---------------|
|Everyone|Everyone| **This is the default value.** When organizers with this policy create webinars, any user can attend. |
|Everyone in my organization excluding guests|EveryoneInCompanyExcludingGuests| When organizers with this policy create webinars, only users in your org can attend.|

### Manage who can attend webinars using the Teams admin center

To manage who can attend webinars through the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. From the dropdown for the **Who can attend webinars** setting, select either **Everyone** or **EveryoneInCompanyExcludingGuests**.
6. Select **Save**

### Manage who can attend webinars using PowerShell

You can use PowerShell to manage who can attend webinars in your organization.

To manage who can attend webinars, use the **`-EventAccessType`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

#### Turn off public webinars

To only allow users in your organization to attend webinars created by users with this policy, use this script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

#### Turn on public webinars

To allow any user to attend webinars created by users with this policy, use this script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
```

## Related articles

- [Issues that affect Teams webinars](/microsoftteams/troubleshoot/meetings/issues-with-webinars)
- [Plan for webinars](plan-webinars.md)
- [Manage the registration form for webinars](manage-registration-form-webinars.md)
- [Manage email communications for webinars](manage-email-communications.md)
- [Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Attendance report for meetings and webinars in Microsoft Teams](teams-analytics-and-reports/meeting-attendance-report.md)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
