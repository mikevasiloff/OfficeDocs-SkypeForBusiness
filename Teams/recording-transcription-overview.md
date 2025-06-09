---
title: Overview- Recording and transcription for Teams meetings, events, and calls
ms.reviewer: lisma, harinlee, wanqincao, yujin1
ms.date: 3/19/2025
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
- m365initiative-voice
- enabler-strategic
- highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
description: Understand recording and transcription policies available for meetings, events, and calls in Microsoft Teams.
---

# Overview- Recording and transcription for Teams meetings, events, and calls

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Group and 1:1 calls

In Microsoft Teams, your users can record and transcribe their meetings, events, and calls. Transcription automatically turns spoken dialogue into written text, making it easy to review or share key discussions later. Recording captures audio, video, and screen-sharing activities, allowing users to revisit or share the full meeting experience as needed. The user's ability to manage the recording of their meetings, events, and calls is referred to as convenience recording. To understand the different types of recordings in Teams, see [Introduction to recording Microsoft Teams calls and meetings](teams-recording-policy.md).

As an admin, you can manage convenience recording and transcription for meetings and calls in your organization through policy settings.

## Meeting, events, and calling policies

- **Meeting policies:** These policies control user permissions for recording and transcription in Teams meetings and group calls.
- **Events policies:** These policies control user permissions for recording and transcription in Teams webinars and town halls. Webinars and town halls have their own separate recording and transcription policies.
- **Voice calling policies:** These policies control user permissions for 1:1 calls, including both internal and external native Teams calls and Public Switched Telephone Network (PSTN) calls.

If your users use Teams meetings, events, and calls, it’s important to align policy settings across these scenarios.

For example, let’s say your organization’s finance team shouldn’t record or transcribe calls, meetings, webinars, or town halls. You turn off recording and transcription in the calling policy and assign it to users in the finance team. However, because you didn’t update or assign a specific meeting or events policy to those users, they default to the global policies. In the global policy for both meetings and events, recording and transcription are on by default.

The finance team can record and transcribe meetings, group calls, webinars, and town halls, but not 1:1 calls, because you didn't assign a custom meeting or event policy. For a consistent recording and transcription experience across all call, events, and meeting types, configure and assign the appropriate policies.

To learn more about assigning policies to both users and groups in your organization, see [Assign policies to users and groups](assign-policies-users-and-groups.md).

The following sections outline the policy settings and features you can use to manage recording and transcription in your organization.

> [!NOTE]
> When you make changes to the Global policy, they apply to everyone in your organization, except for users with an assigned custom meeting or calling policy.

## Manage recording and transcription for meetings, events, and group calls

|Feature/setting|Admin controls|Documentation|
|:------|:-----|:---------|
|Recording for meetings|Allow or prevent meeting and group call recording for users, groups, or your entire organization.|[Manage Teams recording policies for meetings and events](meeting-recording.md#meetings)|
|Record a webinar|Allow or prevent webinar recording for users, groups, or your entire organization.|[Manage Teams recording policies for meetings and events](meeting-recording.md#webinars)|
|Record a town hall|Allow or prevent town hall recording for users, groups, or your entire organization.|[Manage Teams recording policies for meetings and events](meeting-recording.md#town-halls)|
|Transcription for meetings|Allow or prevent meeting and group call transcription for users, groups, or your entire organization.|[Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md#meetings)|
|Transcription for webinars|Allow or prevent webinar transcription for users, groups, or your entire organization.|[Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md#webinars)|
|Transcription for town halls|Allow or prevent town hall transcription for users, groups, or your entire organization.|[Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md#town-halls)|
|Auto recording |Control whether organizers have the **Record and transcribe automatically** setting in their **Meeting options** for meetings, webinars, and town halls. If you allow auto recording, your users’ **Record and transcribe automatically** setting is **Off** by default for meetings and **On** for webinars and town halls. When organizers want their meetings to be recorded and transcribed automatically, they must toggle this setting to **On** for each meeting.</br> With a Teams Premium license, you can use [Meeting templates or Sensitivity labels](manage-meeting-recording-options.md#record-and-transcribe-automatically) to enforce a value for this setting.|[Manage Teams recording policies for meetings and events](meeting-recording.md#auto-recording)|
|Explicit recording consent|Control whether meeting participants must provide consent to be recorded.|[Manage Teams recording policies for meetings and events](meeting-recording.md#require-participant-agreement-for-recording-and-transcription)|
|Recording and transcript expiration|Manage when recordings and transcripts expire for your organization.|[Manage Teams recording policies for meetings and events](meeting-recording.md#expiration-policy)|
|Privacy and security URL|Replace the default Teams meeting recording and transcription privacy statement with URL to your organization’s legal website.|[Manage Teams recording policies for meetings and events](meeting-recording.md#set-a-custom-privacy-policy-url)|
|Microsoft 365 Copilot in Teams meetings and events|Manage how transcripts are used in Microsoft 365 Copilot in Teams meetings and events.|[Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)|
|Shared mailbox meeting recordings|Understand storage and permissions for meetings scheduled through a shared mailbox.|[Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md#shared-mailbox-scheduled-meetings)|
|Block or allow download of channel recording and transcript files|Control whether your users can download channel meeting recordings and transcripts.|[Manage Teams recording policies for meetings and events](meeting-recording.md#block-or-allow-download-of-channel-meeting-recordings)|
|Block download of meeting recording and transcript files from SharePoint or OneDrive| Prevent users from downloading meeting recording and transcript files saved in SharePoint and OneDrive.|[Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)|
|Verify transcription requirements|Verify if a user’s account meets the requirements to transcribe a Teams meeting.|[Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md#check-users-transcription-permissions)|
|Organizer can restrict participants from copying or forwarding meeting chat messages, live captions, and transcript|Control whether organizers can restrict participants from copying or forwarding meeting chat messages, live captions, transcripts, and AI-generated insights in the meeting recaps.|[Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md)|
|Intelligent recap for meetings **(Teams Premium and Copilot)**|Licensing and the transcription policy control this feature. Users with a Teams Premium or Microsoft 365 Copilot license automatically have access to this feature.|[Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md)|
|eDiscovery Search for recordings and transcripts|View meeting recordings video and transcription text.|[Manage Teams recording policies for meetings and events](meeting-recording.md#ediscovery-search-for-recordings-and-transcripts)|
|Recording and transcript storage|Manage where meeting recordings and transcripts are stored.|[Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md)|
|Who can record and transcribe **(Teams Premium)**|Use sensitivity labels or a meeting template to control who can record and transcribe meetings created by organizers with a Teams Premium license.|[Manage Microsoft Teams meeting recording and transcription options for sensitive meetings](manage-meeting-recording-options.md)|

## Manage recording and transcription for 1:1 calls

|Feature/setting|Admin controls|Documentation|
|:------|:-----|:---------|
|Recording|Allow or prevent 1:1 and PSTN call recording for users, groups, or your entire organization.|[Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-recording)|
|Transcription|Allow or prevent 1:1 and PSTN call transcription for users, groups, or your entire organization.|[Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-transcription)|
|Intelligent recap for calls|Licensing and the transcription policy control this feature. Users with a Teams Premium or Microsoft 365 Copilot license automatically have access to this feature.|[Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md)|

## Teams Premium

If you have a Teams Premium license, you can use meeting  sensitivity labels and templates to manage and enforce different recording and transcription settings for your organization. To learn more, see [Manage Microsoft Teams meeting recording and transcription options for sensitive meetings](manage-meeting-recording-options.md).

## Troubleshooting and diagnostics

If you or your users are having any issues or errors with recordings and transcripts, check out the following troubleshooting and end user articles:

- If your users are having issues with recording meetings, see [I can't record a meeting in Microsoft Teams](https://support.microsoft.com/office/i-can-t-record-a-meeting-in-microsoft-teams-f35329c2-57b1-487f-b5e3-70a7efb0945b).
- To understand issues that affect meeting recordings, see [Issues that affect meeting recordings](/microsoftteams/troubleshoot/meetings/troubleshoot-meeting-recording-issues).
- If your users are having issues with transcribing meetings, see [I can't transcribe a meeting in Microsoft Teams](https://support.microsoft.com/office/i-can-t-transcribe-a-meeting-in-microsoft-teams-61f4c8e4-f2d1-4aeb-9b20-244c20fc3faa).

## Related articles

- [Calling policies in Teams](teams-calling-policy.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md)
- [Overview of meetings, webinars, and town halls](quick-start-meetings-live-events.md)
