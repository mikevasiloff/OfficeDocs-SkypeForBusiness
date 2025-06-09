---
title: Plan for Teams meetings
ms.reviewer: bryanyce
ms.date: 10/25/2024
ms.topic: article
ms.author: wlibebe
author: wlibebe
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
description: Learn how to plan for meetings in Microsoft Teams.
---

# Plan for Teams meetings

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a x for no](/office/media/icons/cancel-teams.png)Webinars ![Image of a x for no](/office/media/icons/cancel-teams.png)Town halls

This article, designed for admins, introduces types of meetings, features and functionality, and provides links to more information.

> [!NOTE]
> While meetings with registration are no longer supported, you and your users can use webinars. To learn more about setting up webinars for your org, see [Plan for Teams webinars](plan-webinars.md). Meetings with registration that were previously scheduled, or created with Graph API are still supported until December 31st, 2024.

## Meetings

Meetings in Teams include audio, video, and screen sharing capabilities for up to around 1,000 people. If you turn on the view-only experience for your organizers, view-only capabilities start when around 900 participants join the meeting.

Participants can be users in your organization, or if you allow it, people outside your organization. Meeting organizers can control which features are available in a given meeting. You as the administrator, can control the availability and default value for many of these features by using [meeting policies](#meeting-policies).

The following types of meetings are available:

- Private meetings - Meetings that individual users schedule with specific people.
- Channel meetings - Meetings that are visible to everyone in a channel.
- Meet now meetings - A method of starting an unscheduled meeting with people through a chat.

To specify which users in your organization can start or schedule meetings, see [Manage who can start instant meetings and schedule meetings](manage-who-can-schedule-meetings.md).

### Meeting policies

Meeting policies define who can join meetings, the meeting join experience, what features can be set by the meeting organizer, closed caption settings, recording and transcription policies, and more.

Teams administrators and organizers have different policies and settings to control the meeting experience. For more information, see [Admin and meeting organizer options](#admin-and-meeting-organizer-meeting-options) later in this article.

For a complete list of meeting policies, see [Teams setting and policies reference](settings-policies-reference.md).

## Customization with Teams Premium

With a Teams Premium license, you can extend your organization's visual identity and compliance requirements across the meeting experience by adding logos and backgrounds that can be displayed in the meeting's pre-join screen, lobby, and during the meeting experience. To learn more, see [Custom meetings overview](custom-meetings-overview.md).

## Audio Conferencing for meetings

You can assign an Audio Conferencing license to meeting organizers so they can create meetings where attendees can join by dialing in from their phones. These meeting organizers can also dial-out to attendees to connect them to the meeting's audio portion. To learn more about Audio Conferencing, see [Audio Conferencing in Microsoft Teams](audio-conferencing-in-office-365.md).

## Meeting options for guests and external participants

People outside your organization can attend meetings hosted by your organizations as guests, people from trusted organization, or anonymous participants. You can configure each of these access methods separately.

### Guest access for meetings

As long as guest access is turned on in Teams, guests in your organization can attend meetings. Several meeting features, including screen sharing options and the ability to start instant meetings, can be controlled separately for guests. For details, see [Turn guest access in Microsoft Teams on or off](set-up-guests.md).

Lobby settings affect how people outside your organization join meetings. You can set the following lobby settings by using meeting policies:

- Who can bypass the lobby
- Whether anonymous participants can start a meeting
- Whether people dialing in can bypass the lobby

The meeting organizer can change the settings for who can bypass the lobby, including people dialing in by phone

For complete details about the meeting lobby, see [IT Admins - Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

Meeting participants who can't be validated can attend meetings as anonymous participants. Depending on your business rules or compliance requirements, you might want to allow or prevent anonymous participants accessing meetings. See [Manage anonymous participant access to Teams meetings (IT admins)](anonymous-users-in-meetings.md) for information on how to configure anonymous access for meetings.

People from other trusted Microsoft 365 organizations can attend meetings without having to sign in to your organization. Both organizations must trust each other and users must be enabled for external access. For more information, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

## Attendee limits and streaming options

Up to 10,000 attendees can join a Teams meeting, however, after around 900 users enter a meeting, extra attendees join with a view-only experience. View-only attendees don't have access to the meeting chat or be able to share content or video.

You can allow or prevent the view-only experience for meetings with more than 900 attendees. If you turn off the view-only experience, meeting attendance is limited to the first 1,000 attendees.

For more information about the view-only meeting experience, see [Teams view-only meeting experience](view-only-meeting-experience.md).

## Recordings

You can specify which meeting organizers and attendees can record meetings. For someone to record a meeting, admin policies must allow both the person who starts the recording and the meeting organizer to record.

Organizers can't disable recording for a meeting if admin policies permit it, but they can limit recording to organizers and co-organizers if they have a Teams Premium license.

You can set meeting recordings to expire after a specified time. Managing the expiration date can help save storage space in organizations where many meetings are recorded. When a recording expires, it's moved to the recycle bin, and the file owner is notified. They can restore the recording if they need to.

Recording files are saved to OneDrive (for private meetings) or SharePoint (for channel meetings). Users who attended the meeting have permissions to view the recording by default. You can [block the download of meeting recording files](block-download-meeting-recording.md) if you need to.

To learn more about meeting recording and expiration and to configure recording policies for your organization, see [Teams meeting recording](meeting-recording.md).

If you have compliance requirements around meeting recordings, see [Manage Microsoft Teams meeting recording options for sensitive meetings](manage-meeting-recording-options.md).

## Compliance features

You can use Teams meeting policies to control meeting recording, the lobby, and content sharing for different groups of users in your organization. Teams Premium offers various compliance-related meeting features, including sensitivity label capability, watermarks, encryption, and meeting templates. For details, see [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) and [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md).

## Apps for meetings

You can enhance meeting experiences by integrating and using meeting apps. You can add meetings apps to your Teams deployment by using the apps provided with Teams, using certified third-party apps and templates, and creating your own custom apps. For details, see [Apps for Teams meetings](/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).

For information about how meeting organizers can set meeting options, see [Participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e).

## Admin and meeting organizer meeting options

Teams admins and organizers have different policies and settings to control the meeting experience. The following table lists the types of features available for meetings and how the admin and organizer controls interact.

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Announce when callers join or leave](turn-on-or-off-entry-and-exit-announcements-for-meetings-in-teams.md)|Control whether an entry and exit announcement is played when participants who dialed into the meeting join or leave.|No control|
|[Anonymous participants](anonymous-users-in-meetings.md)|Manage how anonymous attendees access Teams meetings in your org.|Can prevent anonymous users from joining specific meetings if admin allows.|
|[Anonymous users can join a meeting after verifying (Teams Premium)](anonymous-users-in-meetings.md#anonymous-users-can-join-a-meeting-after-verifying-with-an-email-code-teams-premium)|Manage whether anonymous users can verify themselves with a one-time passcode to join meetings in your org.|If admin allows, can require anonymous to verify themselves with a one-time passcode to join specific meetings.|
|[Attendance and engagement reports](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose.|Can turn on or off if allowed by admin.  Organizers with a Teams Premium license can also see engagement information that captures how attendees reacted and interacted during the meeting or event.|
|[Audio and video](meeting-policies-audio-and-video.md)|Can set audio and video modes and network settings.|Can allow or prevent attendee mic and cameras.|
|[Best practice configurations dashboard](best-practice-dashboard.md)|Manage and monitor your environment for Teams meetings and highlight locations that aren't following best practice configurations.|No control.|
|[Breakout rooms](https://support.microsoft.com/office/use-breakout-rooms-in-microsoft-teams-meetings-7de1f48a-da07-466c-a5ab-4ebace28e461)|No control|Can create and manage breakout rooms.|
|[CART captions](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47)|No control|Can set up and offer Communication access real-time translation(CART) captioning to participants instead of the Microsoft Teams built-in live captions that are automatically generated.|
|[Channel meeting scheduling](https://support.microsoft.com/office/schedule-a-meeting-in-microsoft-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5)|No control|Can schedule meetings from channels.|
|[Chat](manage-meeting-chat.md)|Can manage whether users in the org can read and write chat messages. You can also manage chat messages in Teams meetings hosted by other organizations that you don’t have a trusted relationship with.|Can manage whether chat is available for their meetings.|
|[Choose co-organizers](https://support.microsoft.com/office/schedule-a-meeting-in-microsoft-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5)|No control|Can assign different meeting roles in a Teams meeting to give users specific permissions.|
|[Collaboration features](meeting-policies-content-sharing.md)|Can control the availability of PowerPoint Live, whiteboard, and shared notes.|No control|
|[Compliance recording](teams-recording-policy.md)|Can implement an admin policy for automatic recording.|No control|
|[Content sharing](meeting-who-present-request-control.md)|Can control sharing mode and who can request control and can set a default for who can present.|Can control who can present.|
|[Convenience recording](meeting-recording.md)|Can allow or prevent meeting recording and set recording expiration time.|If the admin allows recording, organizers can manage who can record (Teams Premium) and automatic recording.|
|[Custom backgrounds (Teams Premium)](custom-meeting-backgrounds.md)|Can upload images for your users to display in the background of their video feed during meetings.|Can use the backgrounds you upload.|
|[Decorate my background (Teams Premium)](https://support.microsoft.com/office/change-your-background-in-microsoft-teams-meetings-f77a2381-443a-499d-825e-509a140f4780)|No control|Organizers and participants can use AI to decorate their backgrounds.|
|[eCDN for view-only meetings](streaming-ecdn-enterprise-content-delivery-network.md)|Can manage and configure the availability of eCDN for organizers. Admins can also turn off the Microsoft eCDN for view-only meeting organizers with a Premium license and switch to a partner eCDN provider.| No control|
|[End-to-end encryption (Teams Premium)](end-to-end-encrypted-meetings.md) |Can allow or prevent end-to-end encryption.|Can enforce end-to-end encryption if allowed by the admin.|
|[Feedback surveys for anonymous participants](meeting-surveys-anonymous-participants.md)| Manage whether anonymous participants who join meetings hosted in your org can rate their meeting experience through surveys.  |No control|
|[Green room](https://support.microsoft.com/office/5b744652-789f-42da-ad56-78a68e8460d5)|No control|Can choose if green room is used for a meeting. Can use the **End meeting** button to end the meeting for attendees while allowing organizers and presenters to stay in the green room until they're ready to leave.|
|[Intelligent meeting recap (Teams Premium or Microsoft 365 Copilot)](intelligent-recap-calls-meetings.md) |Assigned licenses and transcription policies control this feature.|No control. Organizers, co-organizers, presenters, and participants can access intelligent recap after the meeting ends.|
|[Interpreter agent (Microsoft 365 Copilot)](interpreter-agent-teams.md) |Can control whether users with a Microsoft 365 Copilot license can use Interpreter agent. You can also select the default setting for voice representation.|No control for organizers. Users can control which language they want to hear how their voice is represented to others.|
|[Join verification check](join-verification-check.md) | Can require human verification checks for anonymous users to join meetings in your org.|No control|
|[Language interpretation](https://support.microsoft.com/office/use-language-interpretation-in-microsoft-teams-meetings-b9fdde0f-1896-48ba-8540-efc99f5f4b2e) |No control |Can turn on language interpretation settings for a meeting, add interpreters before the meeting, and designate interpreters during the meeting.|
|[Limit presenter role permissions](presenter-role-reduction.md) |Can limit presenter role permissions for the tenant. |No control|
|[Live stream with RTMP-Out](stream-teams-meetings.md) |Can decide whether organizers can stream town halls to external endpoints by providing a Real-Time Messaging Protocol (RTMP) URL and key to the built-in custom Streaming app in Teams.|Can stream town halls with through apps like Custom Streaming.|
|[Live translated captions (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated captions for their meetings. |Can turn on live translated captions for themselves; attendees can always turn on live translated captions. |
|[Live translated transcription (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated transcription for their meetings. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
|[Manage what attendees see (Teams Premium)](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|No control|Can decide whose avatars or video feeds to spotlight during the town hall.|
|[Manage who can present and request control](meeting-who-present-request-control.md) |Control who can present in meetings and whether participants and external participants can request control of the presentation.|Can manage who can present in their meeting options.|
|[Meeting join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings.|Can choose meeting join and lobby settings for each meeting.|
|[Meeting themes (Teams Premium)](meeting-themes.md)|Can define meeting themes, including colors, images, and logo.|Can turn the admin-defined theme on or off.|
|[Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)|Can control the default values and enforce specific values for Microsoft 365 Copilot in Teams meetings and events in organizers’ meeting options.|Can control whether Microsoft 365 Copilot in Teams meetings and events is used **Only during the meeting**, **During and after the meeting**, or **Off** during their meetings.|
|[Microsoft Teams Rooms (Windows) can join as a presenter](https://support.microsoft.com/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2)|No control.| Can add Microsoft Teams Rooms on Windows with a Pro license as a presenter when they set **Who can present** to **Organizer or co-organizer only** or **Specific people**. Microsoft Teams Rooms see, but can't send chat messages. Organizers must add Microsoft Teams Rooms from external organizations as external presenters.|
|[Outlook add-in](outlook-add-in-authentication-policy-requirements.md)|Can control whether users can schedule meetings from Outlook.|If admin allows, can schedule meetings from Outlook.|
|[Prevent copying or forwarding chat, captions, and transcripts (Teams Premium)](manage-chat-sensitive-meetings.md#prevent-copying-or-forwarding-chat-captions-and-transcripts)|Can prevent copying or forwarding of chat contents by using a meeting template or sensitivity label.|Can manage options if admin doesn't lock label or template settings. |
|[Prevent users from joining external meetings](external-meeting-join.md)|Can control which types of Microsoft Teams meetings your users can join.|No control|
|[Prevent users from sharing content in external meetings (Teams Premium)](block-external-content-share.md)|Can control which types of external Microsoft Teams meetings your users share content in.|No control|
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in meetings.|Can decide if Q&A is available for their meetings if allowed by admins.|
|[Quality of service (QoS)](meetings-real-time-media-traffic.md)|Can prioritize real-time network traffic that's sensitive to network delays over traffic that's less sensitive.|No control|
|[Reactions](manage-reactions-meetings.md)| Manage whether reactions can be used in meetings created by organizers with this policy. |Can control whether reactions can be used in their meetings. |
|[Recording storage and permissions](manage-reactions-meetings.md)| Manage recording storage and permissions. |Permissions depend on admin settings. |
|[Real time telemetry](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md)|Can look at your users’ scheduled meetings and see audio, video, content sharing, and network-related issues. You can use this telemetry to investigate these issues during meetings and troubleshoot in real time.|No control|
|[Restrict who can record and transcribe (Teams Premium)](manage-meeting-recording-options.md#manage-who-can-record-and-transcribe-meetings-teams-premium)| Can restrict which users can record by using a meeting template or sensitivity label. |Can manage options if admin doesn't lock label or template settings. |
|[RTMP-In (Teams Premium)](meetings-rtmp-in.md)|Can control whether organizers can use RTMP-In for their meetings. |Can produce their Teams meetings directly from an external hardware or software-based encoder to integrate different types of media. To start streaming from the encoder, organizers can choose RTMP-In from their meeting options and then access the RTMP link and key. |
|[Scheduling](manage-who-can-schedule-meetings.md)|Can define who can schedule private and channel meetings.|Can schedule meetings if allowed by admin.|
|[Sensitivity labels](manage-who-can-schedule-meetings.md)|Can create sensitivity labels for Teams meetings.|Can apply your sensitivity label to meeting invites from Outlook or Teams. Recipients in your organization see the sensitivity label and all recipients see any headers or footers as configured content markings. Optionally, the meeting invite can be encrypted so only authorized people can see it and access the meeting link. Usage rights can further restrict access, for example, preventing the invite from being forwarded.|
|[Speaker Coach](meeting-speaker-coach.md)|Manage whether users in your organization can use Speaker Coach during meetings and events.|No control- all participants can use Speaker Coach if the admin allows.|
|[Streaming encoders](teams-encoder-setup.md)|Can control whether organizers can use RTMP.|Can use encoders to take audio and video content from sources such as a camera, a microphone, a desktop screen capture.|
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.|Can enable captions.|
|[Video effects](meeting-policies-audio-and-video.md#participants-can-use-video-effects)|Control whether users can customize their video background.|If the admin allows, organizers and meeting participants can blur their video background, choose from the default set of images, or upload custom images to use as their background.|
|[View-only](view-only-meeting-experience.md)|Allow organizers to host large meetings where after the meeting reaches around 900 users, additional attendees join with a view-only experience.|No control|
|[Voice isolation](voice-isolation.md)|Can control whether users can use voice isolation in meetings and calls.|Can enable voice isolation.|
|[Watermarks (Teams Premium)](watermark-meeting-content-video.md)|Can allow or prevent watermarks for attendee video and shared content|Can enforce watermarks if the admin allows.|

## Related articles

- [Meetings, webinars, and town halls feature comparison](meeting-webinar-town-hall-feature-comparison.md)

- [Plan for Teams webinars](plan-webinars.md)

- [Plan for Teams town halls](plan-town-halls.md)

- [Overview of meetings, webinars, and town halls](quick-start-meetings-live-events.md)
