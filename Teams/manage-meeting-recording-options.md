---
title: Manage Microsoft Teams meeting recording and transcription options for sensitive meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.subservice: meetings
ms.reviewer: lisma, ritikag
ms.date: 11/12/2024
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
description: Learn how to manage who can record and transcribe Teams meetings, automatic recording, and the recording lifecycle for sensitive meetings.
---

# Manage Microsoft Teams meeting recording and transcription options for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

> [!NOTE]
> When organizers turn off Microsoft 365 Copilot in Teams meetings and events, recording and transcription are also turned off. To learn more about Copilot, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

Teams is designed to allow easy recording and transcription for meeting participants and organizers. If you have compliance requirements around how meeting recordings and transcripts are used, there are several options available for you, as an admin and your meeting organizers to use meeting recordings and transcripts in a way that fits your needs.

The following table shows the features available to help you manage meeting recordings and transcripts, and where they're configured.

|Setting|Admin policy|Sensitivity label|Template|Meeting organizer|
|:------|:----------:|:---------------:|:------:|:---------------:|
|Block or allow download of channel meeting recordings|Yes|No|No|No|
|Microsoft 365 Copilot in Teams meetings and events|Yes|No|Yes|Yes|
|Meeting recording overall|Yes|No|No|No|
|Privacy and Security URL|Yes|No|No|No|
|Record and transcribe automatically|No<sup>1</sup>|Yes|Yes|Yes|
|Recordings and transcripts expiration|Yes|No|No|No|
|Transcription|Yes|No|No|Yes|
|Require participant agreement for recording|Yes|No|No|No|
|Who can record and transcribe **(Teams Premium)**|No|Yes|Yes|Yes|

<sup>1</sup> - There isn't an admin policy for **Record and transcribe automatically**. However, to control whether organizers have the **Record and transcribe automatically** setting in their **Meeting options**, you can use the **Auto recording** policy in PowerShell. To learn more, see [Manage Teams recording policies for meetings and events](meeting-recording.md#auto-recording).

You control whether the ability to record meetings is available in your organization. Through sensitivity labels, meeting templates, and meeting organizer settings, both you and your meeting organizers can manage who can record and transcribe and whether meetings are automatically recorded and transcribed.

## Block or allow download of channel meeting recordings

You can set a Teams admin policy through PowerShell's **`-ChannelRecordingDownload`** parameter in the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) to control whether channel members can download meeting recordings. If you block the download of channel recordings, members can watch recordings, but can't download them. To learn more, see [Manage Teams recording policies for meetings and events](meeting-recording.md#block-or-allow-download-of-channel-meeting-recordings).

## Manage who can record and transcribe meetings (Teams Premium)

Organizers with a Teams Premium license have two options for who can record and transcribe a meeting:

- Organizers and co-organizers
- Organizers, co-organizers, and presenters

The meeting organizer normally makes this choice when they create the meeting. To restrict recording to organizers in meetings with sensitive information, use a meeting template or sensitivity label to enforce this setting.

If you need to prevent meetings, webinars, and town halls from being recorded entirely, you must use the [recording policies](meeting-recording.md#allow-or-prevent-users-from-recording) in the Teams admin center. This setting applies to the people or groups that you specify, but can't be applied through a meeting template or sensitivity label.

> [!NOTE]
> Meeting templates only allow you to manage who can record. To manage who can record and transcribe, use a Sensitivity label.

To learn more about how your organizers use this feature, see [Record a meeting in Microsoft Teams](https://support.microsoft.com/office/record-a-meeting-in-microsoft-teams-34dfbe7f-b07d-4a27-b4c6-de62f1348c24).

### Platform support

To view the list of platforms that support this feature, see [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md#platform-support-for-advanced-management-for-meetings).

## Microsoft 365 Copilot in Teams meetings and events

With a Teams admin policy or meeting template, you can manage how meeting transcripts are used with Copilot. The only Copilot policy setting that you can enforce is **On with saved transcript required**. The other settings create a default that your organizers can change. For details, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

## Privacy and security URL

With a Teams admin policy, you can add your custom privacy statement to Teams meeting recordings and transcripts in your organization. If your organization has a legal website that you want people to go to for any legal concerns, this policy allows you to display the URL. To learn more, see [Manage Teams recording policies for meetings and events](meeting-recording.md#set-a-custom-privacy-policy-url).

## Require participant agreement for recording

With a Teams meeting policy, you can require participants to agree to being recorded before they can unmute or turn on their camera. Consent results are stored in the meeting attendance report. For details, see [Require participant agreement for recording](meeting-recording.md#require-participant-agreement-for-recording-and-transcription).

## Record and transcribe automatically

> [!NOTE]
> Customers with a Microsoft 365 Education A1 subscription don't have the option to record and transcribe meetings automatically.

Meetings can be set to record automatically when they start. Normally, the meeting organizer makes this choice when they create the meeting.

If there are certain types of meetings that should always be recorded, you can enforce this option by using a meeting template or a sensitivity label.

If all of a particular type of meeting must be recorded (for example, all sensitive meetings), consider enforcing this option by using a sensitivity label. If only certain sensitive meetings need to be recorded, consider using meeting templates to configure this setting. You can create two templates that both use the same label, one which automatically records and another which doesn't.

For details on managing this option with meeting templates, see [IT admins - Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md#recording--transcription).

For details on managing this option with sensitivity labels, see [Use sensitivity labels to protect calendar items, Teams meetings, and chat](/purview/sensitivity-labels-meetings).

## Recording and transcription lifecycle

By default, meeting recordings and transcripts are deleted after 120 days. The following policies in the Teams admin center manage the recording lifecycle:

- **Recordings automatically expire** determines if meeting recordings and transcripts are automatically deleted after a specified time.
- **Default expiration time** specifies the number of days after which recordings and transcripts are deleted. The default is 120.

When a meeting participant records a meeting, the recording is stored in the organizer's OneDrive. Channel meetings are stored in the SharePoint site associated with the channel. Because meeting recordings are .mp4 files, they can be moved or deleted like any other file. If a meeting recording is moved from its original location, the expiration setting no longer affects it. For details, see [Teams meeting recording storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md).

The expiration feature removes old recordings and transcripts to save storage space, but doesn't enforce compliance requirements. If you have meeting recording retention and deletion compliance requirements, consider storing them in a SharePoint library where you can apply [Microsoft Purview retention policies](/microsoft-365/compliance/retention).

## Transcription

With a Teams admin policy, you can control whether captions and transcription features are available during playback of Teams meeting recordings.

Your organizers can manage which users can transcribe their meetings through the **Who can record and transcribe** setting in their **Meeting options**. To restrict transcription to organizers in meetings with sensitive information, use a meeting template or sensitivity label to enforce the **Who can record and transcribe** setting.

 For details on managing transcription, see [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md).

## Manage recording options for your organization

For information about configuring admin meeting policies for meeting recordings, see [Teams meeting recording](meeting-recording.md).

For details about enforcing settings by using meeting templates and sensitivity labels, see [Configure Teams meetings with protection for sensitive data](configure-meetings-sensitive-protection.md) and [Configure Teams meetings with protection for highly sensitive data](configure-meetings-highly-sensitive-protection.md).

## Related topics

- [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
- [Introduction to Teams policy-based recording for callings & meetings](teams-recording-policy.md)
- [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
- [Options for meeting organizers in Microsoft Teams](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e)
- [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md)
- [Use sensitivity labels to protect calendar items, Teams meetings, and chat](/purview/sensitivity-labels-meetings)
- [Meeting options in Microsoft Teams](https://support.microsoft.com/office/meeting-options-in-microsoft-teams-53261366-dbd5-45f9-aae9-a70e6354f88e)
