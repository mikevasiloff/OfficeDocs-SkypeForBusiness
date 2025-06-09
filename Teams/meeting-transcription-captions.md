---
title: Admins- Manage transcription and captions for Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.subservice: meetings
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
  - magic-ai-copilot
ms.reviewer: harinlee, fezuo
ms.date: 5/13/2025
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to configure transcription and caption policies for Teams meetings and events.
appliesto: 
  - Microsoft Teams
---

# Admins- Manage transcription and captions for Teams meetings

[!INCLUDE[Teams Premium](includes/teams-premium-ecm.md)]

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Town halls

> [!NOTE]
> When organizers turn off Microsoft 365 Copilot in Teams meetings and events, recording and transcription are also turned off. To learn more about Copilot, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

Microsoft Teams offers transcription and live captions to enhance accessibility and engagement during meetings and events. Transcription creates a real-time written record of what was said during a meeting or event. Participants can view the transcript after the meeting along with timestamps and speaker attribution. Live captions provide real-time subtitles during the meeting, but Teams doesn't save captions.

As an admin, you can manage whether your users can use and access transcripts and captions for Teams meetings and events.

Transcripts are stored together with meeting recordings in OneDrive and SharePoint storage. To learn more about how transcripts are stored, see [Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md) and [View, edit, and manage video transcripts and captions](https://support.microsoft.com/office/3cb9acb6-05b2-4f59-a50d-7df61123aa20#bkmk_how-captions-and-transcripts-are-stored).

For information on how your users can use transcription, see [View live transcription in a Teams meeting](https://support.microsoft.com/office/dc1a8f23-2e20-4684-885e-2152e06a4a8b). To learn how your end users can use live captions for meetings and webinars, see [Use live captions in a teams meeting](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260).

For details on how your organizers can create human-generated captions, see [Use CART captions in a Microsoft Teams meeting](https://support.microsoft.com/office/2dd889e8-32a8-4582-98b8-6c96cf14eb47).

## Live transcription

Transcription is both a per-organizer and per-user policy setting. For meetings, webinars, and town halls to include transcripts, the organizer must have this setting turned on. The user who starts the recording or transcript must also have this setting turned on.

When live transcription is turned on, users have a real-time written copy of the meeting's conversation. After the meeting, users can find the searchable transcription stored with the meeting recording. If transcription was turned on for the recording, Stream plays the video with the transcript next to the recording, and shows who is speaking and when as the video plays.

If recording is turned on, but transcription is turned off, the recording doesn't have a transcript file stored next to it. Also, when viewing the recording playback in Stream, captions can't be turned on.

The transcription link remains for the lifetime of the file in most cases, but can be broken if the video file is copied within the same OneDrive or SharePoint site. This action would result in captions not displaying on the copied video file.

> [!NOTE]
> Transcription for recorded meetings is currently only supported for English (US), English (Canada), English (India), English (UK), English (Australia), English (New Zealand), Arabic (Saudi Arabia), Arabic (United Arab Emirates), Bulgarian (Bulgaria), Catalan (Catalan), Chinese (Simplified, China), Chinese (Traditional, Hong Kong SAR), Chinese (Traditional, Taiwan), Croatian (Croatia), Czech (Czechia), Danish (Denmark), Dutch (Belgium), Dutch (Netherlands), Estonian (Estonia), Finnish (Finland), French (Canada), French (France), German (Germany), German (Switzerland), Greek (Greece), Hebrew (Israel), Hindi (India), Hungarian (Hungary), Indonesian (Indonesia), Italian (Italy), Japanese (Japan), Korean (Korea), Latvian (Latvia), Lithuanian (Lithuania), Norwegian (Norway), Polish (Poland), Portuguese (Brazil), Portuguese (Portugal), Romanian (Romania), Russian (Russia), Serbian (Cyrillic, Serbia), Slovak (Slovakia), Slovenian (Slovenia), Spanish (Mexico), Spanish (Spain), Swedish (Sweden), Thai (Thailand), Turkish (Türkiye), Ukrainian (Ukraine), Vietnamese (Vietnam), Welsh (United Kingdom).

### Meetings

You can use the Teams admin center or PowerShell to manage transcription for meetings.

To allow or prevent meeting transcription using the Teams admin center, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Meeting policies**.
1. Select the policy that you want to edit or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom meeting policy.
1. Toggle **Transcription** **On** or **Off**. This setting is **On** by default for new policies.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage meeting transcription using PowerShell, use the **`-AllowTranscription`** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy). For details, see the [PowerShell section](#powershell) in this article.

### Webinars

You can use the Teams admin center or PowerShell to manage transcription for webinars. This policy controls whether users can start transcripts when attending webinars and whether webinars they organize can be transcribed.

To allow or prevent transcription for webinars using the Teams admin center, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Events policies**.
1. Select the policy that you want to edit or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom events policy.
1. Toggle **Transcription for webinar** **On** or **Off**. This setting is **On** by default.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage webinar transcription using PowerShell, use the **`-TranscriptionForWebinar`** parameter in [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy). For details, see the [PowerShell section](#powershell) in this article. The default value for the **`-TranscriptionForWebinar`** parameter is *Enabled*.

### Town halls

You can use the Teams admin center or PowerShell to manage transcription for town halls. This policy controls whether users can start transcripts when attending town halls and whether town halls they organize can be transcribed.

To allow or prevent transcription for town halls using the Teams admin center, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Events policies**.
1. Select the policy that you want to edit or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom events policy.
1. Toggle **Transcription for town hall** **On** or **Off**. This setting is **On** by default.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage town hall transcription using PowerShell, use the **`-TranscriptionForTownhall`** parameter in [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy). For details, see the [PowerShell section](#powershell) in this article. The default value for the **`-TranscriptionForTownhall`** parameter is *Enabled*.

## Live translated transcription (Teams Premium)

By default, transcripts are shown in the language spoken that's during a meeting or event. Live translated transcription allows your users to translate the meeting or event transcript into the language they're most comfortable with. The meeting or event organizer must have a Teams Premium license for attendees to use live translated transcription.

To turn on **Live translated transcription**, **Transcription** must be set to '**On**' in the corresponding meeting policy in the Teams admin center. To turn off **Live translated transcription**, set **Transcription** to **Off**.

## Platform support for live translated transcription

To view the list of platforms that support live translated transcription, see [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md#platform-support-for-intelligent-meetings).

## Live captions

Teams can detect what was said in a meeting, webinar, or town hall and present real-time captions along with speaker attribution.

This setting is a per-user policy and applies during a meeting. This setting controls whether the **Turn on live captions** option is available for the user to turn automatically generated live captions on or off in meetings that the user attends. These captions aren't saved alongside the video file.

:::image type="content" alt-text="This screenshot shows the menu initiated by selecting the ellipses icon. The option to Turn on live captions is highlighted." source="media/meeting-policies-live-captions.png" lightbox="media/meeting-policies-live-captions.png":::

|Teams admin center policy option|Parameter value in PowerShell| Behavior|
|---|---|---|
| Not enabled, but users can enable | DisabledUserOverride| **This value is the default setting.** Live captions are off by default, but users with this assigned policy can turn on live captions during meetings or events. |
| Off | Disabled | Users with this assigned policy can't use live captions in meetings or events.|

### Use the Teams admin center to manage live captions

To allow or prevent live captions in meetings, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Meeting policies**.
1. Select the policy that you want to edit or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom meeting policy.
1. From the drop-down for **Live captions**, select **Not enabled, but users can enable**(default value) or **Off**.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage live captions using PowerShell, use the **`-LiveCaptionsEnabledType`** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy). For details, see the [PowerShell section](#powershell) in this article.

## Live translated captions (Teams Premium)

Live translated captions allow your users to see captions translated into the language they’re most comfortable with. By default, live captions are displayed in the language spoken during a meeting or event. For town halls, organizers can preselect up to 6 languages for attendees to use during the event. With a Teams Premium license, this limit increases to 10 languages. The meeting or event organizer must have a Teams Premium license for attendees to use live translated captions.

To turn on live translated captions, you must set **Live captions** to **Not enabled, but users can enable** in the corresponding meeting policy in the Teams admin center. To turn off live translated captions, set **Live captions** to **Off**.

### Platform support for live translated captions

To view the list of platforms that support live translated captions, see [Microsoft Teams Premium - Overview for admins](enhanced-teams-experience.md#platform-support-for-intelligent-meetings).

## Manage whether organizers can prevent participants from copying or forwarding meeting chat messages, live captions, and transcripts

As an admin, you can choose whether organizers in your organization can restrict participants from copying or forwarding meeting chat messages, live captions, transcripts, and AI-generated insights in the meeting recaps. This setting also restricts forwarding and sharing messages to Outlook. By default, this per-organizer setting is set **On**. To learn more, see [Manage chat for sensitive Teams meetings](manage-chat-sensitive-meetings.md).

## Check user's transcription permissions

You can run the Teams transcripts diagnostic tool in the Microsoft 365 admin center to verify if a user’s account meets the requirements to transcribe a Teams meeting.

> [!NOTE]
> Diagnostics in the Microsoft 365 admin center aren't available for Microsoft 365 Government, Microsoft 365 operated by 21Vianet, or Microsoft 365 Germany.

To run the diagnostic tool for transcripts, follow these steps:

1. Select the **Run Tests** button to populate the diagnostic in the Microsoft 365 admin center:

   > [!div class="nextstepaction"]
   > [Run Tests](https://aka.ms/MeetingTranscribeDiag)

2. In the **Username or Email** field, enter the email address of the affected user.
3. In the **Teams Meeting URL** field, enter the meeting URL.
4. Select **Run Tests**.
5. After the diagnostic runs, select the provided links to resolve the issues that were found.

## Manage whether transcripts automatically expire

To manage whether transcripts automatically expire, see [Manage Teams recording policies for meetings and events](meeting-recording.md#expiration-policy).

## PowerShell

For details on assigning policies to users and groups using PowerShell, see [Assign policies to users and groups](assign-policies-users-and-groups.md).

### Manage transcription in PowerShell

You can use PowerShell to manage transcription for meetings, webinars, and town halls in your organization.

#### Transcription for meetings

To allow everyone in your organization to transcribe meetings, events, and group calls, except users with an assigned custom meeting policy, run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowTranscription $true
```

To allow specific users in your organization to transcribe, run the following commands:

1. Create a new policy:

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity "Your Policy Name" -AllowTranscription $true
    ```

1. Assign specific users the policy:

    ```powershell
    Grant-CsTeamsMeetingPolicy -Identity "user@contoso.onmicrosoft.com" -PolicyName "Your Policy Name"
    ```

To allow specific groups in your organization to transcribe, run the following commands:

1. Create a new policy:

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity "Your Policy Name" -AllowTranscription $true
    ```

1. Assign specific groups the policy:

    ```powershell
    Grant-CsTeamsMeetingPolicy -Group "Group ID" -PolicyName "Your Policy Name"
    ```

#### Transcription for webinars

Use the following script to allow users with this policy to transcribe webinars. When these users organize webinars, they can be transcribed:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -TranscriptionForWebinar $true
```

Use the following script to prevent users with this policy from transcribing webinars. When these users organize webinars, they can't be transcribed:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -TranscriptionForWebinar $false
```

#### Transcription for town halls

Use the following script to allow users with this policy to transcribe town halls. When these users organize town halls, the event can be transcribed:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -TranscriptionForTownhall $true
```

Use the following script to prevent users with this policy from transcribing town halls. When these users organize town halls, the event can't be transcribed:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -TranscriptionForTownhall $false
```

### Manage live captions in PowerShell

To turn off live captions for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -LiveCaptionsEnabledType Disabled
```

To turn on live captions for users with this policy, run the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -LiveCaptionsEnabledType DisabledUserOverride 
```

## Related topics

- [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
- [Block the download of Teams meeting recording and transcript files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md)
- [Manage Teams recording policies for meetings and events](meeting-recording.md)
- [Accessibility guide for Microsoft Teams Admins](accessibility-guide-admin.md)
- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
