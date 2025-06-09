---
title: Plan for Teams town halls
ms.reviewer: bryanyce
ms.date: 3/28/2025
ms.author: wlibebe
author: wlibebe
ms.topic: concept-article
manager: pamgreen
ms.service: msteams
ms.subservice: meetings
ms.custom: intro-overview
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-collaboration
- remotework
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
description: Learn what is a town hall in Microsoft Teams. Understand how to plan for town halls in Microsoft Teams for IT Admins. Guidance and tips for Teams town halls.
---
# Plan for Teams town halls

**APPLIES TO:** ![Image of a x for no](/office/media/icons/cancel-teams.png)Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png)Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls

Town halls are meant for one-to-many communications where the presenters, organizers, and co-organizers lead the presentation. The audience participation is primarily to view and react to the content being shared.
As an admin, this article guides you through how to plan and prepare for town halls in your organization.

> [!IMPORTANT]
> Organizers with a Teams Premium license must work with the Microsoft 365 Live Event Assistance Program (LEAP) to create town halls with more than 20,000 attendees. To learn more about LEAP, see the [Need help with your town hall](#need-help-with-your-town-hall) section in this article.

## Turn town halls on or off

Town halls are enabled by default. If you'd like to disable or manage town halls for users in your organization, see [Manage who can schedule town halls](set-up-town-halls.md).

## Get your network ready for town halls

There are five steps you must follow to ensure your network is set up to support town halls.

1. **Ensure your teams environment is set up to connect to our services**</br>
   Ensure that your network connectivity to Microsoft 365 follows our network connectivity principles outlined in [Microsoft 365 network connectivity principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles). The network connectivity principles are standard principles to follow for all Microsoft 365 services, and not just specific to Teams town hall.
2. **Ensure your devices are optimized to connect to our services**</br>
   As part of the network connectivity principles, ensure that the Microsoft 365 endpoints are reachable as defined in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges).
3. **Understand special considerations for events in VPN environments**</br>
   If your organization is using VPN connectivity for remote participants, review the guidance published in [Special considerations for Stream and Teams events in VPN environments](/microsoft-365/enterprise/microsoft-365-vpn-stream-and-live-events). This article details how to optimize the attendee traffic for direct connectivity (also known as split tunneling) to the service.
4. **Plan for bandwidth considerations for town halls**</br>
   Follow the bandwidth requirements documented in [Prepare your organization's network for Teams](/MicrosoftTeams/prepare-network#bandwidth-requirements) for your organizers, co-organizers, presenters.
   Each attendee stream consumes approximately 1.5 Mbps of bandwidth; attendee connectivity  utilizes HTTPS. Physical locations that have a large/densely populated attendee profile should explore using an eCDN to optimize bandwidth usage.
5. **Optimize your Internal network via eCDN**</br>
   An Enterprise Content Delivery Network (eCDN) takes the video content from the internet and distributes the content throughout your enterprise without impacting network performance.<br><br> Town hall organizers with a Teams Premium license have Microsoft eCDN enabled by default, but you can select a different eCDN solution for these organizers. Keep in mind that some future Teams Premium town hall features might require the Microsoft eCDN. <br>For town hall organizers with all other Teams subscriptions, you can enable them to use the Microsoft eCDN solution or, alternatively, one of the following certified eCDN partner solutions to optimize your network for town halls held within your organization:
   - [Hive](https://www.hivestreaming.com/partners/integration-partners/microsoft/)
   - [Kollective](https://kollective.com/ecdn-solutions/microsoft-live-events/)
   - [Ramp](https://rampecdn.com/)

   To turn off the Microsoft eCDN for town hall organizers with a Premium license and learn more about our partner solutions, see  [Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md). For more information about Microsoft eCDN, see [Introduction to Microsoft eCDN](/ecdn/intro).

## Understand your policies

A combination of admin meeting and event policies with organizer and attendee settings manage town halls.
If you'd like to get familiar with how policies work for Teams meetings and events, see [Manage meeting and event policies in Microsoft Teams](meeting-policies-overview.md).
For a full list of admin policies and organizer settings for town halls, see [Town hall control comparison](#town-hall-policy-and-setting-controls) later in this article.

## Decide the types of town halls that organizers can create

When managing the event access type for town halls to decide whether organizers can schedule public town halls, consider the following points:

- External attendees can only join a town hall if the organizer sets the event to public.
- Guests are considered in-org.
- Attendees who aren't in your organization (including anonymous and external access users) can't join in-org town halls.

## Monitor town halls in your organization

### Real time monitoring

You can use real-time data telemetry to monitor town halls and troubleshoot technical issues.
There are two types of real time monitoring for town halls.

1. **Real time monitoring of the presenter and organizer experience**
   You can view scheduled town halls and see audio, video, content sharing, and network-related issues. As an admin, you can use this telemetry to investigate any issues presenters and organizers experience during the town hall and troubleshoot in real time.
   To learn more about real time monitoring of presenters and organizers, see [Use real-time telemetry to troubleshoot poor meeting quality](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md).
1. **Real time monitoring of the attendee experience (Teams Premium)**
   With a Teams premium license, you can use the Microsoft eCDN analytics dashboard for performance analysis and network troubleshooting of the attendee experience during town halls.

   To learn more about real time monitoring of attendees, see [Microsoft eCDN Real Time analytics](/ecdn/technical-documentation/analytics).

### Call Quality Dashboard

Leverage the Call Quality Dashboard (CQD) to monitor town hall quality at the org-wide level and optimize your network to drive performance quality.
To learn more about using CQD for town halls in your org, see [What is Call Quality Dashboard (CQD)](CQD-what-is-call-quality-dashboard.md). You can use the Microsoft Call Quality connector to view specialized **'Teams Events Overview'** and **'Event Health Details'** reports in Power BI Desktop. To get started, download the latest [CQD Quality of Experience (QER) report template](cqd-power-bi-query-templates.md).

For more information about the dimensions and measurements visible through CQD for town halls, search for the word "events" in [Dimensions and measurements available in Call Quality Dashboard (CQD)](dimensions-and-measures-available-in-call-quality-dashboard.md).

### Town hall insights for organizers

With a Teams Premium license, during a town hall, organizers and co-organizers can see real-time event analytics like viewer count, attendees’ country/region, and more. The analytics consist of several data widgets, including charts and graphs, breakdowns tables, and a viewing experience timeline.
For more information on how organizers in your org can use insights for their town halls, see [Town hall insights in Microsoft Teams.](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741)
For town hall organizers that don't have a Teams Premium license, you can check to see if your eCDN provider offers insights during town halls.

## Live events and Premium town halls

If you've been using live events for your organization, you might want to understand the differences and similarities between live events, town halls, and Premium town halls. With a Teams Premium license, your users have access to extended town hall capabilities. The following table is a comparison of live events, town hall, and Premium town hall features. We'll continue to update this table. Check back often for the latest details:

|Capability|Live Events|Town halls|Premium town halls|
|:------| :---: | :---: | :---: |
|**Scale**||||
|Broadcast capacity|10k|10k|- 50k</br> *- 100k In development*|
|Concurrent events|15|15|50|
|Duration|Four hours|30 hours|30 hours|
|eCDN|Microsoft and partner providers|Microsoft and partner providers|Microsoft and partner providers|
|**Management controls**||||
|Ability to not send emails and calendar invites to attendees|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Email customization|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Control when event invites are sent|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Separate invites for presenters and attendees|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Modern group support|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|External presenters|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Who can present|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Who can produce|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Co-organizer capacity|N/A|10|10|
|Presenter capacity (including external presenters)|100|100|100|
|**Interactivity**||||
|Chat for attendees|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a x for no](/office/media/icons/cancel-teams.png)|Up to 20,000 attendees|
|Default audio and video off|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|DVR|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Live captions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A|Up to to 10,000 attendees|Up to to 10,000 attendees|Up to to 50,000 attendees|
|Q&A: attendees can filter questions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: vote on and sort questions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Reactions|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a x for no](/office/media/icons/cancel-teams.png)|Up to 20,000 attendees|
|**Host and scene controls**||||
|Attendee reporting|![Image of a checkmark for yes](/office/media/icons/success-teams.png)| ![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Download transcripts|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|End event for attendees and return presenters to green room|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|Yes|Yes|
|Green room|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Join as an attendee for presenters and organizers|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Manage what attendees see|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Layouts|Single Video, Video + Content​​|Dynamic focused curated view with up to 7 videos|Dynamic focused curated view with up to 7 videos|
|Live translated captions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|Six languages|10 languages|
|Nudge attendees to join|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Presenters can dial in|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Preview shared content in manage what attendees see|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Queue and preview content and presenters|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Q&A: attendees can filter questions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: delete and archive questions|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: moderators can hide their names|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: organizers can make presenters moderators|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: organizers can privately reply to a question|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Q&A: question export to CSV|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Real time insights|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Video on Demand (VOD)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|**Devices**||||
|Cloud Video Interop (CVI) support|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Microsoft Teams Rooms (Windows) support for presenters and attendees|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Sharepoint embedded support|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Virtualized Desktop Infrastructure (VDI) support|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Viva Engage integration|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|**Admin controls**||||
|Manage the types of events your organizers can create|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Manage whether events in your organization can be recorded|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Manage whether events in your organization can be transcribed|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|*In development*|*In development*|
|Usage reports|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Call quality diagnostics|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|**Advanced broadcast**||||
|RTMP-In|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|RTMP-In Transcription|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|RTMP-Out (Live streaming)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|

For more information on Teams Premium, see [Teams Premium licensing](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams).

## Town hall policy and setting controls

You and your organizers have different policies and settings to control the town hall experience. The following table lists the types of features available for town halls and how the admin and organizer policies and settings interact:

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Announce when callers join or leave](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md)|Control whether an entry and exit announcement is played when attendees who dialed into the town hall join or leave.|No control.|
|[Attendance and engagement reports](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose.|Can turn on or off if allowed by admin.  Organizers with a Teams Premium license can also see engagement information that captures how attendees reacted and interacted during the meeting or event.|
|[Attendee reactions (Teams Premium)](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_townhall_reactions)|No control.| Controls whether attendees can engage during the event with live reactions. Not supported for town halls with more than 20,000 attendees. |
|[Audio and video](meeting-policies-audio-and-video.md)|Can manage the availability and use of audio and video for presenters and organizers.| Only presenters and organizers can use their audio and video. Attendees can't share their audio or video, but interact through Q&A.|
|[Chat for attendees (Teams Premium)](town-hall-chat.md)|Can manage whether town hall organizers with a Teams Premium license can turn on chat for their attendees.|Can decide whether attendees can chat during town halls if their admin's policy allows it.|
|[Chat for organizers, co-organizers, and presenters](manage-meeting-chat.md)|Can manage whether organizers, presenters, and co-organizers can read and write messages to each other during town halls.|Can chat with presenters and co-organizers. Attendees don't use this chat during town halls. To learn how attendees can use chat during town halls, see [Manage meeting chat for Microsoft Teams town halls](town-hall-chat.md).|
|[Compliance recording](teams-recording-policy.md)|Can implement an admin policy for automatic recording.|No control|
|[Content sharing](meeting-policies-content-sharing.md)|Can control sharing mode, who can request control, and can set a default for who can present.|Can control who can present among presenters, organizers, and co-organizers. Attendees can't share content in town halls.|
|[Convenience recording](meeting-recording.md)|Can allow or prevent recording and set recording expiration time.|If the admin allows recording, organizers can manage who can record (Teams Premium) and automatic recording.|
|[Custom backgrounds (Teams Premium)](custom-meeting-backgrounds.md)|Can upload images for organizers, co-organizers, and presenters with a Teams Premium license in your organization to display in the background of their video feed during meetings.|Internal organizers, co-organizers, and presenters with a Teams Premium license can use the backgrounds you upload.|
|[Decorate my background (Teams Premium)](https://support.microsoft.com/office/change-your-background-in-microsoft-teams-meetings-f77a2381-443a-499d-825e-509a140f4780)|No control|Teams Premium licensed organizers, co-organizers, and presenters can use AI to decorate their backgrounds.|
|[Download transcripts](https://support.microsoft.com/office/manage-town-hall-recordings-in-microsoft-teams-88ac3af7-db67-4556-a202-b73a1d6c2e46)|No control.|Can download transcripts from their town halls.|
|[eCDN](streaming-ecdn-enterprise-content-delivery-network.md)|Can manage and configure the availability of eCDN for organizers. You can also turn off the Microsoft eCDN for town hall organizers with a Premium license and switch to a partner eCDN provider.| No control.|
|[eCDN Analytics (Teams Premium)](streaming-ecdn-enterprise-content-delivery-network.md)|Can use the eCDN analytics dashboard to troubleshoot the attendee experience during live town halls.| No control.|
|[Email communications (Teams Premium)](manage-email-communications.md)|Can control if event organizers and co-organizers can edit email templates for their town halls.|Can edit email templates before they're sent out.|
|[External presenters](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c)|No control.|Can invite presenters from outside  of your organization. External presenters have a unique join link to join the town hall without waiting in the lobby.|
|[Green room](https://support.microsoft.com/office/green-room-for-teams-meetings-5b744652-789f-42da-ad56-78a68e8460d5) |No control.|Can choose if green room is used for a town hall. Can use the **End meeting** button to end the event for attendees while allowing organizers and presenters to stay in the green room until they're ready to leave.|
|[Intelligent recap (Teams Premium and Microsoft 365 Copilot)](intelligent-recap-calls-meetings.md) |Assigned licenses and transcription policies control this feature.|No control. Organizers, co-organizers, and presenters can access intelligent recap after the town hall ends. Attendees don't have access to intelligent recap.|
|[Limit presenter role permissions](presenter-role-reduction.md) |Can limit presenter role permissions for the tenant. |No control.|
|[Live stream with RTMP-Out](stream-teams-meetings.md) |Can decide whether organizers can stream town halls to external endpoints by providing a Real-Time Messaging Protocol (RTMP) URL and key to the built-in custom Streaming app in Teams.|Can stream town halls with through apps like Custom Streaming.|
|[Live transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.| Only AI generated captions are currently available. |
|[Live translated captions(Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated captions for their town halls. |Organizers can select six languages, or ten if they have a Premium license for attendees to use when translating captions during the town hall.|
|[Live translated transcription (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated transcription for their town halls. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription.|
|[Manage what attendees see](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16) |No control. |Can decide whose avatars or video feeds to spotlight during the town hall. |
|[Manage who can schedule town halls](set-up-town-halls.md)|Can disable town halls for users and groups, control which organizers can schedule town halls,  and decide whether organizers can schedule public town halls.|Can schedule town halls if allowed by admin.|
|[Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)|Can control the default values and enforce specific values for Microsoft 365 Copilot in Teams meetings and events in organizers’ meeting options.|Can control whether Microsoft 365 Copilot in Teams meetings and events is used **Only during the meeting**, **During and after the meeting**, or **Off** for their town halls.|
|[Microsoft Teams Rooms (Windows) can join as a presenter](https://support.microsoft.com/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2)|No control.| Can add Microsoft Teams Rooms on Windows with a Pro license as a presenter. Microsoft Teams Rooms see, but can't send chat messages. Organizers must add Microsoft Teams Rooms from external organizations as external presenters.|
|[Prevent copying or forwarding chat, captions, and transcripts (Teams Premium)](manage-chat-sensitive-meetings.md#prevent-copying-or-forwarding-chat-captions-and-transcripts)|Can prevent copying or forwarding of chat contents by using a meeting template or sensitivity label.|Can manage options if admin doesn't lock label or template settings. |
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in town halls.|Can decide if Q&A is available for their town halls if allowed by admins. Q&A is the only way attendees can interact and engage with presenters and organizers. Town hall organizers and co-organizers can export the event's questions and answers to a CSV file.|
|[Quality of service (QoS)](meetings-real-time-media-traffic.md)|Can prioritize real-time network traffic that's sensitive to network delays over traffic that's less sensitive.|No control.|
|[Recording](meeting-recording.md)|Can allow or prevent town hall recording. |Recordings start automatically for town halls, but organizers can turn this off. |
|[Recording expiration](meeting-recording.md)|Can manage whether recordings automatically expire. |By default, published recordings expire after 30 days. Organizers can extend the expiration date to 60 days. After the new date passes, they must reupload and republish the file to keep sharing.|
|[RTMP-In](meetings-rtmp-in.md)|Can control whether organizers can use RTMP-In for their town halls. |Can produce their Teams events directly from an external hardware or software-based encoder to integrate different types of media into the event. To start streaming from the encoder, organizers can choose RTMP-In from their meeting options and then access the RTMP link and key. |
|[Shared notes](meeting-policies-content-sharing.md)|Can manage whether organizers and co-organizers can use shared notes with other during town halls. |Can use shared notes with co-organizers during town halls |
|[Speaker coach](meeting-speaker-coach.md)|Can manage whether organizers, presenters, and co-organizers can use speaker coach during town halls. |Can use speaker coach for private real-time feedback and suggestions for improvement of themselves, co-organizers, and presenters. |
|[Streaming encoders](teams-encoder-setup.md)|Can control whether organizers can use RTMP.|Can use encoders to take audio and video content from sources such as a camera, a microphone, a desktop screen capture.|
|[Town hall insights for organizers](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741)|No control.|Organizers and co-organizers can see real-time event analytics like viewer count, attendees’ country or region, and more. The analytics consist of several data widgets, including charts and graphs, breakdowns tables, and a viewing experience timeline. |
|[Town hall usage report](teams-analytics-and-reports/teams-town-hall-usage-report.md)|View activity and usage trends for all town halls created in your organization.| No control. |
|[VOD publishing](manage-vod-publishing.md) |Can manage the types of recordings organizers can publish. |Can publish and modify town hall recordings. |
|[Voice isolation](voice-isolation.md)|Can control whether users can use voice isolation in town halls.|Can enable voice isolation.|

## Need help with your town hall?

Are you and your organizers are new to hosting town halls or just need some extra help? The Microsoft 365 Live Event Assistance Program (LEAP) can help you get more familiar with setting up and running town halls. The LEAP program is also available during the event to help if any questions or issues come up. For more information on the LEAP program, see [Microsoft 365 Live Event Assistance Program.](https://adoption.microsoft.com/virtual-event-guidance/assistance)
