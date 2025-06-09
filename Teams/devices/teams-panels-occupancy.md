---
title: Occupancy state on Teams panels
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 03/11/2025
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides you with the information needed so that Teams panels show the correct status when they are in a call, free, or when the meeting room is occupied.
---

# Occupancy status on Teams panels

Teams panels can now smartly utilize signals from Teams Rooms devices and occupancy sensors paired with Teams panels to indicate when a room is in use, so users aren't surprised to find an available room is occupied. 

Access to this feature is dependent on the version of Teams panels app installed and the license assigned to the resource account that is signed in to that Teams panel. Verify the following:

- The Teams panel is running on version 1449/1.0.97.2025086303 or later.
- The account signed in on your Teams panel device is assigned a Teams Rooms Pro or Teams Shared Devices license.

If the above requirements are met, this feature is on by default. The room is in use when the room isn't currently reserved, and a user is in a call or casting with a Teams Rooms device (Windows or Android), or the room is detected as occupied through a paired occupancy sensor. You can see which occupancy sensors are currently supported at [What's new in Microsoft Teams devices](/microsoftteams/devices/devices-release-notes?branch=main&tabs=panels).

When the room is in use, the panel's LED adjusts to the color selected by the admin for the busy state. In addition, the panel's home screen reflects that the room is occupied.

> [!NOTE]
> The room can still be reserved on the device itself, through Microsoft Outlook, or through Microsoft Teams.

:::image type="content" source="./media/occupy-reserve-low-res.png" alt-text="Screenshot of Inventory rooms tab." lightbox="./media/occupy-reserve-hi-res.png":::

If the device is paired with a Microsoft Teams Rooms on Android, after a user reserves the occupied room from the device, a message will appear on the room display to let the user inside of the room know that the room has been reserved and to exit. This notification will be off by default, and the admin will need to enable it after pairing the device. This feature is coming soon. 

An admin can choose to turn off these features from the device in Teams admin settings > _Device settings > Occupied state._ The two settings are _Allow occupied state_ and _Allow booking notifications_. If _Allow occupied state_ is turned off, the booking notifications will also be turned off.

## Related articles
- [Check-in and auto release on Microsoft Teams panels](/microsoftteams/devices/check-in-and-auto-release)
- [How to use Microsoft Teams panels](/microsoftteams/devices/use-teams-panels)
- [Certified Teams panels](/microsoftteams/devices/teams-panels-certified-hardware?tabs=certified-panels)