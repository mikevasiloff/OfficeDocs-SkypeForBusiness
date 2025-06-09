---
title:  Manage who can schedule and attend town halls in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: chbalaki
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
description: Learn how to set up and manage town hall policies for IT Admins in Microsoft Teams. Learn how to manage who can schedule and attend town halls in your organization.
---

# Manage who can schedule and attend town halls in Microsoft Teams

**APPLIES TO:** ![Image of a x for no](/office/media/icons/cancel-teams.png)Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png)Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls

## Overview

Town halls in Microsoft Teams are a one-to-many interactive virtual event. This article describes how you, as an admin, can decide which users can create town halls in your organization. To learn more about town hall features and capabilities, see [Plan for town halls](plan-town-halls.md).

For details on how your organizers can create town halls, see [Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c).

## Manage who can schedule town halls

You can use the Teams admin center or PowerShell to manage who can schedule and run town halls in your organization. 

|Teams admin center value| PowerShell value|Behavior|
|---------|---------------|---------------|
|On|Enabled| **This is the default value.** Users with this policy can create town halls. |
|Off|Disabled| Users with this policy can't create town halls.|

### Manage who can schedule town halls using the Teams admin center

To manage who can schedule and run town halls through the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Toggle the **Town halls** setting **On** or **Off**.
6. Select **Save**.

If you change this value to **Off** after a user schedules a town hall, they can't run or start the town hall. 

### Manage who can schedule town halls through PowerShell

You can use PowerShell to manage who can schedule town halls in your organization.

To manage who can schedule town halls, use the **`-AllowTownhalls`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

#### Turn off town halls

To prevent organizers with this policy from creating town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhalls Disabled
```

#### Turn on town halls

To allow organizers with this policy to create town halls, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhalls Enabled
```

## Manage who can attend town halls

> [!NOTE]
> The EveryoneInCompanyExcludingGuests value allows only in org attendees to join town halls created by organizers with this policy. For town halls, in org attendees include guests. However, for webinars, guests aren't considered in org.

You can use the Teams admin center or PowerShell to manage who can attend town halls in your organization.

|Teams admin center value| PowerShell value|Behavior|
|---------|---------------|---------------|
|Everyone|Everyone| **This is the default value.** When organizers with his policy create town halls, any user can attend. |
|Everyone in my organization excluding guests|EveryoneInCompanyExcludingGuests| When organizers with his policy create town halls, only users in your org and guests defined in external access can attend.|

### Manage who can attend town halls using the Teams admin center

To manage who can attend town halls through the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. From the dropdown for the **Who can attend webinars** setting select either **Everyone** or **EveryoneInCompanyExcludingGuests**.
6. Select **Save**

### Manage who can attend town halls through PowerShell

You can use PowerShell to manage who can attend town halls in your organization.

To manage who can attend town halls, use the **`-EventAccessType`** parameter within the PowerShell [**CsTeamsEventsPolicy**](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

#### Turn off public town halls

To only allow users in your organization and guests to attend town halls created by users with this policy, use this script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType EveryoneInCompanyExcludingGuests
```

#### Turn on public town halls

To allow any user to attend town halls created by users with this policy, use this script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -EventAccessType Everyone
```

## Related topics

- [Plan for town halls](plan-town-halls.md)
- [Meetings, webinars, and live events overview](quick-start-meetings-live-events.md)
- [Feature comparison](meeting-webinar-town-hall-feature-comparison.md)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
