---
title: Microsoft Teams Premium - Overview for admins
author: wlibebe
ms.author: wlibebe
manager: pamgreen
ms.reviewer: spraveen, margidesai
ms.date: 7/11/2024
ms.topic: overview
ms.service: msteams
ms.subservice: teams-premium
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
  - highpri
audience: Admin
appliesto:
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - Licensing
description: Learn about Microsoft Teams Premium for administrators and IT Professionals.
---

# Microsoft Teams Premium - Overview for admins

![Information icon](media/info.png) **The features described in this article require Teams Premium.** Teams Premium licenses aren't a replacement for Teams licenses. Users must have both a Teams license and a Teams Premium license for Teams and Teams Premium features to work properly. For more information about feature availability and licensing, see [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

Teams Premium is an add-on license that provides the following enhancements to Teams:  

- Enhanced meeting experiences for your end users
- Enhanced security and protection for meetings
- Enhanced administrative and telemetry support

This article, written for IT Pros and admins who are deploying and configuring Teams Premium, describes the available features and provides links to more detailed documentation.

> [!IMPORTANT]
> Now that Teams Premium has reached general availability, some features that were previously accessible with Teams now require a Teams Premium license for access.
>
> To manage Teams Premium features, your tenant needs at least one user with an active [Teams Premium license](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams).

For more general information about Teams meetings and premium events, see the following articles:

- [Meetings, webinars, and town halls](overview-meetings-webinars-town-halls.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)

> [!NOTE]
> We'll continue to update this article. Check back often for links to new content.

## Protection and advanced management

Teams Premium provides more ways to safeguard and monitor users' Teams experiences with the following key features:

- **Advanced collaboration analytics** - View your organization's external collaboration habits. These reports include information about your teams, trusted domains, channels, guests, and internal users. You can also find information on inactive teams and inactive external domains.

- **Audio quality alerts** - Set up alerts for in-progress meeting audio issues and get notified immediately when your specified users experience issues.

- **Custom user policy packages** - Create policy packages to simplify, streamline, and help provide consistency when managing policies for groups of users across your organization.

- **Microsoft eCDN** - **This feature is only supported for town halls and view-only meetings**. Optimize network performance for video streaming within an enterprise network. Microsoft eCDN allows millions of enterprise users around the world to communicate face-to-face efficiently and reliably. Organizers with a Teams Premium license use the Microsoft eCDN by default, but you can also select one of our partner providers for these organizers.

- **End-to-end encryption** - Enforced through a sensitivity label, end-to-end encryption provides increased security for meetings that require a higher level of protection.

- **External domain activity report** - Understand how your organization communicates with trusted external organizations over chat.

- **Manage what attendees see** - Meeting organizers can decide whose avatars or video feeds to spotlight during a Teams meeting while others are hidden from view.

- **Organizer can restrict participants from copying or forwarding meeting chat messages, live captions, and transcript** - Control whether organizers can restrict participants from copying or forwarding meeting chat messages, live captions, transcripts, and AI-generated insights in the meeting recaps. This setting also restricts forwarding and sharing messages to Outlook.

- **Screen sharing quality alerts** - Set up alerts for in-progress meeting screen sharing issues and get notified immediately when your specified users experience issues.

- **Sensitivity labels** - Extended capabilities for sensitivity labels to control meeting and event settings normally controlled by the organizer. These capabilities include new settings to control lobby, chat, chat copy, presentation, and recording functions. You can also automatically apply or recommend that the meeting is labeled with the highest priority sensitivity label from files shared for the meeting.

- **Real time telemetry and retention** - Real-time telemetry is gathered automatically for all users who have a Teams Premium license and retained for seven days.

- **Priority account chat controls​** - Assign a policy to specific users to allow them to block incoming 1:1 chats from users in your organization. 

- **Teams Premium feature usage report** - View aggregated usage of Teams Premium features by users in your org.

- **Video quality alerts** - Set up alerts for in-progress meeting video issues and get notified immediately when your specified users experience issues.

- **Watermarking** - Enforced through a sensitivity label, watermarks display the email address of a meeting or webinar participant. Watermarks are useful for protecting confidential information shared in meetings and webinars.

- **Who can record and transcribe** - Organizers can control who can record and transcribe their meetings through their meeting options. You can must use a sensitivity label or meeting template to manage this feature.

  | Feature/Task  | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
  | --------- | -----------| ----------- | ------------ |
  | Advanced collaboration analytics |No, contact support for assistance.| [Advanced Collaboration Analytics for Microsoft Teams](advanced-collaboration-analytics.md) | No end-user control |
  | Audio quality alerts |Yes, you can add or remove users.| [Alerts for in-progress meeting audio quality issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-audio) | No end-user control |
  | Custom user policy packages |Yes| [Managing policy packages in Teams](manage-policy-packages.md) | No end-user control |
  | End-to-end encryption (E2EE) | Yes |[Encryption for sensitive meetings](end-to-end-encrypted-meetings.md) | [Use encryption](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-meetings-a8326d15-d187-49c4-ac99-14c17dbd617c)  |
  | External domain activity report|No, contact support for assistance.| [Microsoft Teams external domain activity report](/microsoftteams/teams-analytics-and-reports/external-domain-activity-report) | No end-user control |
  | Manage what attendees see | No, contact support for assistance.| No admin control | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
  | Manage which eCDN provider view-only meetings use |Yes |[Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md#manage-the-ecdn-solution-for-premium-town-halls-and-view-only-meetings)|No end user control |
  | Microsoft eCDN |Yes |[How to enable Microsoft eCDN](/ecdn/how-to/enable-microsoft-ecdn-for-your-tenant)|No end user control |
  | Organizer can restrict participants from copying or forwarding meeting chat messages, live captions, and transcript |Yes, use the Teams admin center to manage content copying restrictions in your meeting templates or policies. Use the Microsoft Purview portal to turn labels with chat content copying restrictions on or off.| [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md) | No end-user control |
  | Prevent users from sharing content in external meetings|Yes| [Prevent users from sharing content in external meetings](block-external-content-share.md) | No end-user control |
  | Priority account chat controls|Yes| [Allow users to block Microsoft Teams chat messages](block-incoming-chats.md) | No end-user documentation |
  | Real-time telemetry and retention|No, contact support for assistance.| [Use real-time telemetry to troubleshoot poor meeting quality](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md#where-to-find-per-user-real-time-troubleshooting-telemetry) | No end-user control |
  | Screen sharing quality alerts|Yes, you can add or remove users.| [Alerts for in-progress meeting screen sharing issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-screen-sharing) | No end-user control |
  | Sensitivity labels | Yes, use the Microsoft Purview portal to turn labels on or off.|[Use sensitivity labels to protect calendar items, Teams meetings and chat](/purview/sensitivity-labels-meetings) | [Sensitivity labels for Teams meetings](https://support.microsoft.com/office/sensitivity-labels-for-teams-meetings-2b244d1d-72d0-471e-8e58-c41079e190fb)|
  | Teams Premium feature usage report|No, contact support for assistance.| [Teams Premium feature usage report](/microsoftteams/teams-analytics-and-reports/teams-premium-usage-report) | No end-user control |
  | Templates, labels, and policies |Yes, use the Teams admin center to add or delete meeting templates. Use the Microsoft Purview portal to turn labels on or off.| [Templates, sensitivity labels, and policies](meeting-templates-sensitivity-labels-policies.md)  | [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
  | Video quality alerts|Yes, you can add or remove users.| [Alerts for in-progress meeting video quality issues](/MicrosoftTeams/alerts/alerts-in-progress-meeting-video) | No end-user control |
  | Watermarks | Yes | [Require a watermark for meetings](watermark-meeting-content-video.md) | [Watermarks for meetings](https://support.microsoft.com/office/watermark-for-teams-meetings-a9166432-f429-4a19-9a72-c9e8fdf4f589)|
  | Who can record and transcribe | Yes, use the Teams admin center to add or delete recording restrictions in your meeting templates. Use the Microsoft Purview portal to turn labels with recording restrictions on or off.|[Manage recordings for sensitive meetings](manage-meeting-recording-options.md) | [Record a meeting](https://support.microsoft.com/office/record-a-meeting-in-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24?storagetype=stage#bkmk_whocanstartorstoparecording) |

### Platform support for advanced management for meetings

The following table describes platform support for Teams Premium advanced management for meetings features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Advanced collaboration analytics|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|
| Audio quality alerts|Yes|Yes|Yes|Yes|Yes|Yes|Yes|N/A|N/A|Yes|N/A|N/A|Yes|Yes|Yes|
| Custom user policy packages |N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|
| End-to-end encryption (E2EE) |Yes|Yes|Yes|No (users can't join)|Yes|Yes|Yes|No (users can't join)|No (users can't join)|No (users can't join)|Yes|No|No|Yes|Yes|
| External domain activity report |N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|
| Manage what attendees see |Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|Yes|
| Organizer can restrict participants from copying or forwarding meeting chat messages, live captions, and transcripts |Yes|Yes|Yes<sup>1</sup>|Yes|N/A|N/A|N/A|No|N/A|N/A|Yes|Yes|Yes|Yes|Yes|
| Real-time telemetry and retention |N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|
| Screen sharing quality alerts |Yes|Yes|Yes|Yes|Yes|Yes|Yes|N/A|N/A|Yes|N/A|N/A|Yes|Yes|Yes|
| Sensitivity labels |Yes|Yes|Yes|Yes|Yes|Yes|Yes|No|No|No|No|No|Yes|Yes|No|
| Teams Premium feature usage report |N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|
| Video quality alerts|Yes|Yes|Yes|Yes|Yes|Yes|Yes|N/A|N/A|Yes|N/A|N/A|Yes|Yes|Yes|
| Watermarks|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|Yes|No|No|No|No|No|Yes|
| Who can record and transcribe|Yes|Yes|Yes|Yes|No|No|No|No|No|N/A|Yes|N/A|Yes|Yes|N/A|

## Personalized meetings

Teams Premium provides more ways to personalize your Teams meeting experiences with the following key features. For an overview on personalized meetings, see [Custom meetings overview](custom-meetings-overview.md):

- **Custom meeting backgrounds for organizations** - Create and define custom meeting backgrounds that your users can use during meetings and events.

- **Custom together mode scenes for organizations** - Customize, create, or accept together mode scenes to digitally combine participants into a single virtual scene.

- **Meeting templates** - Control meeting settings that the meeting organizer normally controls. With templates, you can create consistent meeting experiences in your organization and help enforce compliance requirements and business rules.

- **Meeting themes** - Set up and create meeting themes for various business units and departments within a single tenant.

- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams meetings directly from an external hardware or software-based encoder.

  | Feature/Task |  Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
  | -------------------- | ----------- | ----------- | ------------ |
  | Custom meeting backgrounds for organizations | Yes| [Meeting backgrounds](custom-meeting-backgrounds.md)| [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
  | Custom together mode scenes for organizations | No, contact support for assistance.|[Content for you and your developers](/microsoftteams/platform/apps-in-teams-meetings/teams-together-mode)| |
  | Meeting templates | Yes| - [Overview](custom-meeting-templates-overview.md)<br>- [Create a custom meeting template](create-custom-meeting-template.md)| [Use custom templates](https://support.microsoft.com/office/use-custom-templates-for-teams-meetings-78279be9-3283-4999-b24e-96fb0da2fb4f) |
  | Meeting themes | Yes| [Themes for Teams meetings](meeting-themes.md) | [Use meeting themes](https://support.microsoft.com/office/use-meeting-themes-for-teams-meetings-fbfd826d-1112-4790-918a-5a82cac8250e) |
  | RTMP-In | Yes| [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |

### Platform support for personalized meetings

The following table describes platform support for Teams Premium personalized meeting features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Custom meeting backgrounds for organizations|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|N/A|Yes|N/A|N/A|Yes|Yes|
| Custom together mode scenes for organizations|Yes|Yes|No|Yes|No|No|No|No|No|N/A|N/A|N/A|N/A|Yes|No|
| Meeting templates |Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|No|Yes|No|
| Meeting themes |Yes|Yes|Yes|Yes|No|No|No|No|No|N/A|Yes|Yes|N/A|Yes|Yes|
| RTMP-In |Yes|Yes|No|Yes|No|No|No|No|N/A|Yes|N/A|Yes|No|Yes|Yes|

## Intelligent meeting features

Teams Premium provides the following key AI-powered meetings features:

- **Decorate my background** - Your users can use AI to decorate their backgrounds.
- **Intelligent meeting recap** - Give your users a more personalized rundown of their meetings with intelligent meeting recap.
- **Live translated captions** -  For meetings, webinars, and town halls, your users can see captions translated into the language they’re most comfortable with.
- **Live translated transcripts** - For meetings, webinars, and town halls, your users can understand each other better during a meeting or event by translating the transcript into the language they're most comfortable with.

  | Feature/Task  | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
  | -------------------- | -----------| ----------- | ------------ |
  | Decorate my background | No, contact support for assistance. | No admin control | [Decorate your background](https://support.microsoft.com/office/change-your-background-in-microsoft-teams-meetings-f77a2381-443a-499d-825e-509a140f4780)|
  | Intelligent meeting recap| No, contact support for assistance.<sup>1</sup>|[Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md) | [Meeting recap in Microsoft Teams](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef#bkmk_intelligent_meeting_recap) |
  | Live translated captions | Yes | [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)|[Use live captions in Microsoft Teams meetings](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260) |
  | Live translated transcripts | Yes |  [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md) | [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b)|

<sup>1</sup>If you toggle the **Transcription** setting to **Off** in your **Meeting policies**, intelligent meeting recap isn't available for users with this policy.

### Platform support for Intelligent meetings

The following table describes platform support for Intelligent meeting features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
|Decorate my background|Yes|Yes|No|No|N/A|N/A|N/A|N/A|N/A|N/A|Yes|N/A|No|No|N/A|
|Intelligent meeting recap|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|N/A|Yes|N/A|Yes|Yes|N/A|
|Live translated captions|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|N/A|Yes|N/A|Yes|Yes|N/A|
|Live translated transcripts|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|N/A|Yes|N/A|Yes|Yes|N/A|

## Premium events

Teams Premium offers advanced features to enhance your town halls and webinars.

- **[Town halls](#town-halls)** bring interactive video streaming to a new level. Town halls are meant for one-to-many communications where the presenters, organizers, and co-organizers are leading the interactions. The audience participation is primarily to view and react to the content being shared.

- **[Webinars](#webinars)** provide a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants.

The following sections describe Teams Premium feature enhancements for town halls and webinars. For more information about planning for town halls, webinars, and meetings in general, see [Plan for town halls](plan-town-halls.md), [Plan for webinars](plan-webinars.md), and [Meetings, webinars, and town halls](overview-meetings-webinars-town-halls.md).

### Town halls

Teams Premium provides more ways to elevate Teams town halls in your organization with the following key features:

- **50,000 attendees** - Organizers can host town halls with up to 50,000 attendees. To create town halls with more than 20,000 attendees, organizers must work with the Microsoft 365 Live Event Assistance Program (LEAP). To learn more, see [Plan for town halls](plan-town-halls.md).
- **Chat for town hall attendees** - Organizers can allow attendees to use chat during town halls.
- **Custom emails for town halls** - Organizers and co-organizers can customize the town hall email templates sent to attendees.
- **Increased broadcast and Q&A capacity** - Organizers can broadcast their town halls to 20,000 attendees. All attendees can use Q&A to interact with presenters, organizers, and co-organizers.
- **Live translated captions**- Organizers can choose up to 10 languages for attendees to use when translating captions during the town hall.
- **Live translated transcripts** - Your users can understand each other better during a town hall by translating the meeting transcript into the language they're most comfortable with.
- **Microsoft eCDN** - Optimize network performance for video streaming within an enterprise network. Microsoft eCDN allows millions of enterprise users around the world to communicate face-to-face efficiently and reliably. You can use the Microsoft eCDN or select one of our partner providers for Premium town halls.
- **Real time monitoring of the attendee experience** - You can use the eCDN analytics dashboard to troubleshoot the attendee experience during live town halls.
- **Town hall attendee reactions** - Organizers can allow attendees to engage and provide feedback during a town hall with live reactions.
- **Town hall insights** - Organizers can monitor join and quality of the audio/video experience for their town hall attendees while they're live.

  | Feature/Task | Can admins turn this feature on/off? |Documentation for admins| Documentation for your end users |
  | -------------------- |  ----------- | ----------- | ----------- |
  | Chat for town hall attendees| Yes | [Manage event chat for Microsoft Teams town halls](town-hall-chat.md) |[Chat in a town hall in Microsoft Teams](https://support.microsoft.com/office/chat-in-a-town-hall-in-microsoft-teams-a4a0e102-ca45-4605-a0a8-83a884547338) |
  | Custom emails for town halls | Yes | [Manage email communications](manage-email-communications.md) |[Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_town_hall_invites) |
  | Manage which eCDN provider Premium town halls use |Yes |[Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md#manage-the-ecdn-solution-for-premium-town-halls-and-view-only-meetings)|No end user control |
  | Microsoft eCDN |Yes |[How to enable Microsoft eCDN](/ecdn/how-to/enable-microsoft-ecdn-for-your-tenant)|No end user control |
  | Real time monitoring of the attendee experience | No, contact support for assistance. |[eCDN Analytics](/ecdn/technical-documentation/analytics)|No end user control |
  | Town hall attendee reactions | No, contact support for assistance. | No admin control|[Schedule a town hall in Microsoft Teams](https://support.microsoft.com/office/schedule-a-town-hall-in-microsoft-teams-d493b5cc-9f61-4dac-8027-d837dafb7a4c#bkmk_townhall_reactions) |
  | Town hall insights | No, contact support for assistance. | No admin control|[Town hall insights in Microsoft Teams](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741) |

#### Platform support for Premium town halls

The following table describes platform support for Teams Premium town hall features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Custom emails for town halls|Yes|Yes|Yes|No|No|No|No|No|No|No|No|No|Yes|Yes|
| Event chat|Yes|Yes|Yes|Yes|No|No|N/A|N/A|No|N/A|Yes|N/A|No<sup>1</sup>|Yes|
| Live translated captions|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|Yes|N/A|Yes|Yes|N/A|
| Live translated transcripts|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|Yes|N/A|Yes|Yes|N/A|
| Microsoft eCDN, analytics, and provider management|Yes|Yes|No|Yes|No|No|No|No|No|No|No|Yes|Partial<sup>1</sup>|Yes|
| Town hall attendee reactions|Yes|Yes|Yes|Yes|No|No|N/A|N/A|No|N/A|Yes|N/A|Partial<sup>1</sup>|Yes|
| Town hall insights |Yes|Yes|Yes|Yes|No|No|N/A|N/A|No|No|Yes|N/A|Partial<sup>1</sup>|Yes|

<sup>1</sup> - Your users should join via web.

### Webinars

Teams Premium provides more ways to elevate Teams webinars in your organization with the following key features:

- **Custom emails for webinars** - Organizers and co-organizers can customize the webinar email templates sent to attendees.
- **Custom webinar reminder email send times** - Webinar reminder emails are automatically sent to registrants an hour before the event starts. With Teams Premium, organizers can edit the send time to notify attendees sooner.
- **Enable and manage the waitlist for webinars beyond capacity** - When the webinar's registration reaches capacity, organizers can manage overflow registration requests through a waitlist.
- **Limit registration start and end times** - Organizers can set a time window during which potential attendees can register for their webinar.
- **Manage what attendees see** - Webinar organizers can decide whose avatars or video feeds to spotlight during a Teams webinar while others are hidden from view.
- **Manually approve registrants** - Organizers can approve or deny requests to register for their webinar.
- **Real Time Messaging Protocol (RTMP)-In** - Organizers can produce their Teams webinar directly from an external hardware or software-based encoder.

  | Feature/Task | Can admins turn this feature on/off? | Documentation for admins | Documentation for your end users |
  | -------------------- | ----------- | ----------- | ----------- |
  | Custom emails for webinars| Yes| [Manage email communications](manage-email-communications.md) |[Manage webinar emails in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-emails-in-microsoft-teams-d0006848-f707-494f-b0a4-eeebcbc723be) |
  | Enable and manage the waitlist for webinars beyond capacity| No, contact support for assistance.| No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
  | Limit registration start and end times | No, contact support for assistance.| No admin control|[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
  | Manage what attendees see | No, contact support for assistance.| No admin control | [Manage what attendees see in Teams meetings](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|
  | Manually approve registrants |No, contact support for assistance.| No admin control |[Manage webinar registration in Microsoft Teams](https://support.microsoft.com/office/manage-webinar-registration-in-microsoft-teams-923f382a-0cca-433a-b38d-7461971192d1) |
  | RTMP-In | Yes| [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md)|[Use RTMP-In in a Teams meeting](https://support.microsoft.com/office/use-rtmp-in-in-a-teams-meeting-789d6090-8511-4e2e-add6-52a9f551be7f) |

#### Platform support for Premium webinars

The following table describes platform support for Teams Premium webinar features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Custom emails and reminders for webinars|Yes|Yes|N/A|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|No|Yes|Yes|
| Enable and manage the waitlist for webinars beyond capacity|Yes|Yes|N/A|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|No|Yes|Yes|
| Limit registration start and end times|Yes|Yes|N/A|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|No|Yes|Yes|
| Manage what attendees see |Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|Yes|
| Manually approve registrants |Yes|Yes|No|Yes|No|No|No|No|No|No|No|No|Yes|Yes|
| RTMP-In |Yes|Yes|No|Yes|No|No|No|No|N/A|N/A|Yes|No|Yes|Yes|

## Advanced Virtual Appointments

[!INCLUDE [va-app-retirement](includes/va-app-retirement.md)]

With any Microsoft 365 license, your end users can use basic Virtual Appointments capabilities to schedule and join business-to-customer meetings. For example, users can schedule appointments in the Bookings calendar and external attendees can join through a browser without having to download Teams.

To learn more about Virtual Appointments, see [Manage the Virtual Appointments app for your organization in Microsoft Teams](manage-virtual-appointments-app.md).

Teams Premium provides advanced Virtual Appointment capabilities, such as:

- Analytics at departmental and organizational levels
- Consumption and usage analytics for admins in the Teams admin center
- Custom lobby room with branding and logos​
- Queue of scheduled and on-demand appointments
- Short Message Service (SMS) notifications

  | Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |
  | -------------------- | ----------- | ----------- |
  | Reporting | No, contact support for assistance.| [Virtual Appointments usage report](/microsoft-365/frontline/virtual-appointments-usage-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json)<br>[Advanced Virtual Appointments activity report](/microsoft-365/frontline/advanced-virtual-appointments-activity-report?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json) |
  | SMS notifications  | Yes| [SMS text notifications](bookings-app-admin.md#sms-text-notifications) |

### Platform support for Premium advanced Virtual Appointments features

The following table describes platform support for Teams Premium Virtual Appointments features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| SMS|Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|Partial|
| SMS reminder in Queue|Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|No|
| Queue view|Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|No|
| OnDemand |Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|No|
| Analytics |Yes|Yes|No|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|N/A|Yes|Yes|N/A|

## Custom 3D Immersive Mesh Experiences

With a Teams Premium license, users can explore immersive 3D experiences for the workplace. Host customized single or multi-room immersive events in the Mesh app for up to 200 attendees, available cross-platform on PC and Meta Quest VR devices.

Teams Premium provides custom Mesh experience capabilities for your users, such as:

- **Host immersive events tailored to your business needs** - Elevate team engagement during employee onboardings, trainings, product showcases, or any hybrid business scenarios by creating engaging and interactive experiences with the Mesh app.
- **Create custom 3D experiences** - Creators can easily use no-code tools to add videos, and images to pre-created and custom environments. Developers and technical artists can leverage scripting, physics, and embedded web content within the Mesh toolkit in Unity to build custom 3D environments with enhanced interactivity.
- **Create custom avatars, explore environments, and communicate virtually** - Customizable avatars can navigate around 3D environments to experience content and have multiple simultaneous discussions with colleagues using spatial audio built-in to the experience.
- **Integrated with Microsoft 365** - Mesh provides enterprise-grade security and privacy, built on trusted platforms.

  | Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |Documentation for end users |
  | -------------------- | ----------- | ----------- |----------- |
  | Set up Mesh | Yes, use [App centric management](app-centric-management.md) to allow or prevent users from using Mesh.| [Configure Microsoft Mesh](/mesh/setup/content/setup-m365-mesh)<br>[Preparing your organization for Mesh](/mesh/setup/content/preparing-your-organization) | No end user control.|
  | Create your event | Yes| No admin control. |[Overview of Mesh events](/mesh/events-guide/events-overview) |
  | Customize your avatar | Yes| No admin control. |[Personalize your avatar](/mesh/user-guide/avatars) |
  | Develop a custom environment | Yes| No admin control. |[Mesh Development Overview](/mesh/develop/development-overview) |
  | Download the Mesh app | Yes| No admin control. |[Getting started with events in Microsoft Mesh](/mesh/user-guide/getting-started) |

### Platform support for Premium Mesh features

The following table describes platform support for Teams Premium Mesh features:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Mesh|Yes|No|No|No|No|No|No|No|No|No|No|No|No|No|No|

## Advanced Places workplace collaboration

Microsoft Places allows you and your organization to build a smart workplace. With a Teams Premium license, your users can experience advanced features that support the booking experience in Places. As an admin, you have access advanced management capabilities and reports.

Teams Premium provides the following advanced capabilities in Places:

- **Auto release and check-in for rooms** - If you create auto release for rooms, when a room that you enable for auto release isn't being used, Teams and Places free up the room for others to reserve.
- **Individual desk booking** - Allow users to select and book individual desks for their day in the office.
- **Places explorer** - Get a singular view of the people, spaces, and experiences at each workplace location.​
- **Places finder** - Your users can book and check into workspaces, as well as use seat assignments to sit near collaborators.
- **Quick book** - For in-office meetings without a space booked, your users can get intelligent suggestions for each meeting for the day and book at once in bulk.
- **Space analytics** - You can learn which desks and rooms are most frequently used, and get suggestions on how to optimize space management. You can also identify trends for key buildings, bookable rooms, and shared work spaces.
- **Team guidance** - Managers and leaders in your organization can find the best work patterns for teams by establishing expectations and adjusting the rhythm to meet the needs of the group.  

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |Documentation for end users |
| -------------------- | ----------- | ----------- |----------- |
| Auto release for rooms| Yes|[How to enable specific rooms for Auto Release](/microsoft-365/places/enable-auto-release) | [Overview of Auto Release](/microsoft-365/places/enable-auto-release#room-check-in-and-autorelease-experience)|
| Individual desk booking| Yes|[Configure desk pools and workspaces (optional)](/microsoft-365/places/setting-up-desk-workspaces-in-places-finder) | [Get started with Microsoft Places](https://support.microsoft.com/office/get-started-with-microsoft-places-49b7ea21-b9e1-4ccd-acd6-c600f3da633c)|
| Places finder| Yes| [Enabling Microsoft Places Finder in Outlook](/microsoft-365/places/enabling-places-finder) |[Get started with Microsoft Places](https://support.microsoft.com/office/get-started-with-microsoft-places-49b7ea21-b9e1-4ccd-acd6-c600f3da633c)|
| Space analytics| Yes, remove users from the Places Advanced and Analytics Users [security groups](/microsoft-365/places/places-analytics). |[Microsoft Places Analytics](/microsoft-365/places/places-analytics) | [Get started with Microsoft Places](https://support.microsoft.com/office/get-started-with-microsoft-places-49b7ea21-b9e1-4ccd-acd6-c600f3da633c)|

### Platform support for Places

The following table describes platform support for Places:

|Feature|Windows|MAC|Mobile|Web|Microsoft Teams Rooms- Windows|Microsoft Teams Rooms- Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Places|Yes|Yes|Yes|Yes|N/A|N/A|N/A|N/A|N/A|N/A|N/A|No|N/A|N/A|N/A|

## Calls

### Intelligent call recap

**Intelligent call recap** provides AI-powered insights and recaps to Public Switched Telephone Network (PSTN) and 1:1 Teams calls.

- To use this feature for PSTN calls, you must assign a Teams Phone license and either Teams Premium license or a Microsoft 365 Copilot license to users. For more information on Teams Phone licensing, see [Microsoft Teams add-on licenses](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
- To use this feature with 1:1 Teams calls, you must assign a Teams Premium license or Microsoft 365 Copilot license to users.

| Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |Documentation for end users |
  | -------------------- | ----------- | ----------- |----------- |
  | Intelligent call recap| No, contact support for assistance.<sup>1</sup>|[Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md) | No end user documentation |

<sup>1</sup>If you turn off **Transcription**, intelligent call recap isn't available for users with this policy.

### Queues app

Teams Premium and Teams Phone provide access to Queues app, a Teams-native solution that unlocks a set of advanced call functionalities for Teams Phone Call queues and Auto attendants, such as:

- **Call queue management**: Admins can now delegate authorized users, also known as leads or supervisors, to manage and configure Call queues and Auto attendants directly from the Teams client. Authorized users can configure Call queues and Auto attendants from Call settings and they can opt agents into and out of the queue from Queues app.
- **Real-time metrics**: The number of waiting calls, average wait time, longest call waiting time metrics, and more are included in real-time metrics within the Queues app. The analytics report shows activity made in the queue from 12:00 AM local time of the signed in user. For more information on real-time reports, see [Auto attendant and Call queue real-time reports](aa-cq-real-time-reports.md).
- **Historical reporting**: View historical metrics for call queues, and auto attendants, and agent queue actions. Historical metrics report up to the past 27 days. For more information on historical reports, see [Auto attendant and Call queue historical reports](aa-cq-cqd-historical-reports.md).
- **Monitor, Whisper, Barge, Takeover** - Authorized users can enter into a monitoring session with selected agents for private coaching. Authorized users can listen to customer calls, whisper to agents with private messages, even barge into or takeover the calls. For information about configuring Monitor, Whisper, Barge, and Takeover, see [Manage voice applications policies in Microsoft Teams](manage-voice-applications-policies.md).

  | Feature/Task  | Can admins turn this feature on/off? | Documentation for admins |Documentation for end users |
  | -------------------- | ----------- | ----------- |----------- |
  |Call queue management|Yes, with [voice application policies](manage-voice-applications-policies.md) for Authorized users|[Manage the Queues app for Microsoft Teams](manage-queues-app.md)|[Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9)|
  |Real-time metrics|Yes, with [voice application policies](manage-voice-applications-policies.md) for Authorized users|[Auto attendant and Call queue real-time reports](aa-cq-real-time-reports.md)|No, end users can view reports if authorized.|
  |Historical reporting|Yes, with voice application policies for Authorized users|[Auto attendant and Call queue historical reports](aa-cq-cqd-historical-reports.md)|No, end users can view reports if authorized.|
  |Monitor, Whisper, Barge, Takeover|Yes, with voice application policies for Authorized users|[Manage voice applications policies in Microsoft Teams](manage-voice-applications-policies.md)||

Queues app is now generally available and is enabled by default for all Teams users in your organization who are assigned both a Teams Premium and Teams Phone license and who and are voice enabled.

For more information about Queues app, see [Manage the Queues app for Microsoft Teams](manage-queues-app.md). For end user documentation, see [Use the Queues app for Microsoft Teams](https://support.microsoft.com/office/370ad83e-c2c1-4a9f-8a59-16c98be102e9).

#### Platform support for Queues app

The following table describes platform support for Queues app:

|Feature|Windows|Mac|Mobile|Web|Microsoft Teams Rooms - Windows|Microsoft Teams Rooms - Android|Touch boards for Teams Rooms|Direct guest join|CVI|View-only mode|External communication with unmanaged Teams users|Anonymous users support|VDI WebRTC classic optimization|VDI SlimCore-based optimization|Exchange on-premises|
| -------------------- | ----------- | ----------- | ------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |------------ |
| Queues app|Yes|Yes|No|No|No|No|No|N/A|No|N/A|N/A|N/A|Yes|Yes|Partial|

## More resources

You can find more resources here:

- [Microsoft Teams Premium product site](https://www.microsoft.com/microsoft-teams/premium)
- [Teams Premium deployment guide](https://aka.ms/TeamsPremiumDeployment)
- [Teams Premium user guide](https://adoption.microsoft.com/files/microsoft-teams/Microsoft-Teams-Premium-user-guide.pptx)
- [Microsoft Teams Premium blog](https://www.microsoft.com/en-us/microsoft-365/blog/2023/02/01/microsoft-teams-premium-cut-costs-and-add-ai-powered-productivity)

> [!TIP]
> As a companion to this article, we recommend using the [Teams Premium Advanced Deployment Guide](https://go.microsoft.com/fwlink/?linkid=2264339) when signed in to the Microsoft 365 admin center. This guide customizes your experience based on your environment. To review best practices without signing in and activating automated setup features, go to the [Microsoft 365 setup portal](https://go.microsoft.com/fwlink/?linkid=2263487).
