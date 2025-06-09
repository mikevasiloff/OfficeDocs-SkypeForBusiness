---
title: Intelligent recap for Teams calls, meetings, and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: weizxue, nijait, benjamin.olson, harinlee
ms.date: 3/31/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: meetings
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
  - magic-ai-copilot
  - m365initiative-voice
description: Learn how to manage Intelligent recap for Teams calls and meetings. Understand the licenses your users need to use intelligent recap for VoIP and PSTN calls.
---

# Intelligent recap for Teams calls and meetings

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Calls

Intelligent recap for Microsoft Teams uses AI technology to improve your users’ productivity and efficiency. This article is designed to guide you, as an admin, in understanding intelligent recap’s prerequisites and capabilities.

To learn more about how your users use intelligent recap in their meetings, see [Meeting recap in Microsoft Teams](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef#bkmk_intelligent_meeting_recap).

> [!NOTE]
> For webinars and town halls, intelligent recap is available only to organizers, co-organizers, and presenters. Attendees don't have access to intelligent recap.

## Prerequisites

Intelligent recap is automatically available to users in your organization with the following required licenses and policies:

### Licensing

- You must assign your users a Microsoft 365 subscription that includes Teams or a Microsoft 365 (no Teams) subscription with a separate Teams license.
- You must assign a Teams Premium license or Microsoft 365 Copilot license to your users.
- For Public Switched Telephone Network (PSTN) calls, you must also assign a Teams Phone license and have a calling plan for your users. For information on Teams Phone licensing, see [Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing). To learn more about PSTN connectivity options, see [PSTN connectivity options](pstn-connectivity.md).

### Policies

#### Transcription

To allow your users to use intelligent recap, you must turn on transcription:

- **PSTN, 1:1 peer-to-peer Voice over Internet Protocol (VoIP) calls:** To turn on transcription, see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-transcription).
- **Meetings, events, and group VoIP calls:** To turn on transcription, see [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md#live-transcription).

#### Recording

For the full recap experience for meetings and events, you must assign a policy that allows recording for your users. If recording is turned off, users experience recap without the recording, speakers, topics, and chapters. To turn on recording for meetings and events, see [Manage Teams recording policies for meetings and events](meeting-recording.md#allow-or-prevent-users-from-recording).

## Intelligent call recap

Intelligent call recap uses AI to allow your users to focus during their calls and save time on follow-ups.

### PSTN calls

PSTN calls are made and received using a phone number. Your users can access AI generated notes and recommended tasks for PSTN calls through the **Recap** button in the Calls app in Teams.

:::image type="content" source="media/i-recap-pstn-small.png" alt-text="Screenshot of intelligent call for PSTN calls in the Calls app." lightbox="media/i-recap-pstn-expand.png":::

### 1:1 peer-to-peer and group VoIP calls

1:1 peer-to-peer and group VoIP calls are made between Teams users. Your users can access AI generated notes, recommended tasks, speakers, topics, mentions, and chapters for 1:1 and group peer-to-peer calls through the **Recap** button in the call’s chat in Teams.

:::image type="content" source="media/intelligent-call-recap-small.png" alt-text="Screenshot of the intelligent call recap button in the call's chat." lightbox="media/intelligent-call-recap-expand.png":::

:::image type="content" source="media/intelligent-call-recap-2-small.png" alt-text="Screenshot of the intelligent call recap tab from the call's chat." lightbox="media/intelligent-call-recap-2-expand.png":::

## Intelligent meeting recap

Intelligent meeting recap uses AI to help your users focus on the meeting discussion instead of taking notes. This feature allows them to find key information, access highlights, and save time on follow-ups.

After the meeting or event ends, your users can access the following AI powered features for their meetings through the **Recap** tab in the Teams calendar and chat:

- AI meeting notes
- AI recommended tasks
- Personalized timeline markers show when users' names were mentioned, when screens were shared, and when they joined or left the meeting.
- Speaker timeline markers show who spoke during the meeting, when they spoke, and allows your users to jump to that moment.
- Meeting chapters divide the meeting into chapters, and meeting topics that allow your users to jump to a point in the meeting when a certain topic was discussed.

:::image type="content" source="media/new-i-recap-meetings-small.png" alt-text="Screenshot of intelligent meeting recap from the recap tab." lightbox="media/new-i-recap-meetings-expand.png":::

### Intelligent recap for external meetings

Intelligent meeting recap for external meetings allows your users to share the meeting's recap with external attendees. To share the recap via Outlook with specified external attendees, after the meeting, in the **Recap** tab, users can select **Share** > **Share via Outlook**.

To manage policies that allow external attendees to attend meetings in your organization, see [IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

### Intelligent recap for multilingual meetings

> [!NOTE]
> This feature is currently in Public preview.

> [!NOTE]
> Intelligent meeting recap for multilingual meetings doesn't currently support town halls.

Intelligent meeting recap for multilingual meetings translates the meeting's recap into each participant's language. Once the meeting ends, the recap appears in the language each participant selected for live translated transcription. Intelligent meeting recap for multilingual meetings currently supports translation in the following languages: English, Spanish, Japanese, French, German, Portuguese, Italian, Mandarin (Simplified Chinese), and Korean.

To learn more about live translated transcription, see [View live transcription in Microsoft Teams meetings](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b#bkmk_livetranslated).

## Supported meetings and call types

Intelligent recap is supported on the following types of meetings and calls:

- Meetings: Meetings scheduled in the Teams client, meetings scheduled in Outlook, meet now, webinars, town halls
- Calls: PSTN, 1:1, group peer-to-peer

## Platform support

To view the list of platforms that support this feature, see [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md#platform-support-for-intelligent-meetings).

## Data and privacy

For details on data and privacy for intelligent recap, see [Data, privacy, and security for intelligent recap in Teams Premium](/microsoftteams/privacy/intelligent-recap).

## Related articles

- [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md)
- [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md#enable-call-transcription)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Plan for Teams meetings](plan-meetings.md)
- [Plan for Teams webinars](plan-webinars.md)
- [Plan for Teams town halls](plan-town-halls.md)
