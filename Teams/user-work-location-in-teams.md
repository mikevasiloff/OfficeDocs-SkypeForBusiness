---
title: User work location in Teams
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: seema.bansal
ms.date: 05/22/2025
description: Learn how users can set up and use their daily work location in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
ms.custom: 
  - seo-marvel-apr2020
  - chat-teams-channels-revamp
  - teams-chat-and-channels
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# User work location in Teams

Work location is part of a user's profile in Microsoft Teams and throughout Microsoft 365. Users can set work locations in Microsoft Teams and share visibility for each day they're in the office or working from home, making it easier to coordinate in-person meetings. By default, anyone in the organization using Teams can see, in nearly real time, locations shared by others.

## Work location options in Teams

These work location options are available in Teams:

|Options |Representation |
|---|---|
|Working remotely |![house icon](./media/work-location-remote.png)|
|Working from office |![building icon](./media/work-location-office.png) |
|Working from office, with building details such as floor number, room, or workspace |![add building icon](./media/work-location-add-building-update.png)|

Users can also set up a recurring work plan for each day of the week by [setting work location and work hours in Outlook](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6). When a user sets or changes a recurring work plan, their work location and work hours are also set automatically in Teams; changes are reflected in both apps.

> [!NOTE]
> - The tenant admin must add buildings to Microsoft Places so that users can set their locations with building details. For more information, go to [Configure buildings and floors](/microsoft-365/places/get-started/quick-setup-buildings-floors) in the Microsoft Places documentation.
>
> - In Exchange hybrid environments, Places features are only available for users with a mailbox managed in Exchange Online. Users with an on-premises mailbox can't use work plans or many other Places features.

## Location details in Teams

Users can learn where coworkers are working at any time from their coworkers' profile card details. [Profile cards](https://support.microsoft.com/office/profile-cards-in-microsoft-365-e80f931f-5fc4-4a59-ba6e-c1e35a85b501) make it easy for users to quickly get an overview of coworkers' online status, next available time to meet, work hours, local time, and work location.

Also, users in a group chat can find the location details of other group chat members by opening the chat member list view.

When a user is chatting from the same location as the chat recipient, location details display on the top header area of the chat message window.

> [!TIP]
> By default, all of a user's location details are visible to other users, but admins can use the &#8209;`LocationDetailsInFreeBusy` parameter to the [`set-mailboxconfiguration` Exchange PowerShell cmdlet](/powershell/module/exchange/set-mailboxcalendarconfiguration#-locationdetailsinfreebusy) to control the level of location detail that is visible.

## User settings to edit location sharing

Users must opt in to location sharing by manually setting up their work locations. By opting in, users enable anyone in their organization to view this information.

For more information on disabling location sharing, go to [Access your Account Privacy Settings](https://support.microsoft.com/office/access-your-account-privacy-settings-3e7bc183-bf52-4fd0-8e6b-78978f7f121b) and [Set your work hours and location in Outlook](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6#:~:text=Set%20work%20hours%20and%20location%20from%20Settings).

## Related topics

[Set your work location in Microsoft Teams](https://support.microsoft.com/office/set-your-work-location-in-microsoft-teams-6c14a0f5-3cd6-427d-b1d2-aa0365aebf88)

[Set your work hours and location in Outlook](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6#:~:text=Set%20work%20hours%20and%20location%20from%20Settings)

[Show your hybrid-work location, availability to meet, work hours, and more](https://support.microsoft.com/office/show-your-hybrid-work-location-availability-to-meet-work-hours-and-more-c861198d-f82e-41d7-88ec-c2e716be5ede)

[User presence in Teams](./presence-admins.md)
