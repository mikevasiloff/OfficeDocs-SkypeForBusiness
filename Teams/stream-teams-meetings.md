---
title: Allow live streaming with RTMP-Out for Teams meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: chbalaki
ms.date: 04/30/2025
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
  - Tier2
  - m365initiative-meetings
description: Learn how to set up and manage streaming also known as RTMP-Out for your Teams meetings, webinars, and town halls.
---

# Allow live streaming with RTMP-Out for Teams meetings and events

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls

Live streaming allows organizers in your organization to expand their reach and provide a unique experience for meeting, webinar, and town hall attendees. As an admin, when you allow live streaming, your organizers can stream meetings and events to external endpoints by providing a Real-Time Messaging Protocol out (RTMP-Out) URL and key to the built-in [Custom Streaming app](https://appsource.microsoft.com/product/office/WA200006865) in Teams.

To learn more about how your organizers can use RTMP to live stream meetings and events, see [Broadcast audio and video from Teams with RTMP](https://support.microsoft.com/office/broadcast-audio-and-video-from-teams-with-rtmp-11d5707b-88bf-411c-aff1-f8d85cab58a0).

> [!NOTE]
> Organizers can't stream live events.

## Manage live streaming for your users

You can use the Teams admin center or PowerShell to manage whether organizers with this assigned policy can live stream their meetings and events through RTMP-Out.

### Manage live streaming in the Teams admin center

Follow these steps to manage live streaming in the Teams admin center:

1. In the Teams admin center, expand **Meetings** and then select **Meeting policies**.
1. Select the policy that you want to edit.
1. Under **Audio & video**, set **Live streaming** to **On** from the dropdown.
1. Select **Save**

### Manage live streaming with PowerShell

To manage whether organizers with this policy can live stream their meetings and events through RTMP, use the **`-LiveStreamingMode`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To allow organizers with this policy to stream their meetings through RTMP, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -LiveStreamingMode Enabled
```

For information on how to assign policies with PowerShell, see [Assign policies in Teams](policy-assignment-overview.md).

## Related topics

- [Assign policies in Teams](policy-assignment-overview.md)
- [Manage RTMP-In for Teams meetings, webinars, and town halls](meetings-rtmp-in.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Quick start - Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Plan meetings](plan-meetings-external-participants.md)
- [Plan webinars](plan-webinars.md)
