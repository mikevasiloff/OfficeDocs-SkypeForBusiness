---
title: Manage Teams recording policies for meetings and events
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: how-to
ms.service: msteams
ms.subservice: meetings
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
ms.reviewer: ritikag,lisma
ms.date: 06/27/2024
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
description: Learn how to deploy features in Teams meetings to record audio, video, and screen sharing activity.
---

# Manage Teams recording policies for meetings and events

> [!NOTE]
> When organizers turn off Microsoft 365 Copilot in Teams meetings and events, recording and transcription are also turned off. To learn more about Copilot, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Group calls

In Microsoft Teams, your users can record their Teams meetings, webinars, and town halls to capture audio, video, and screen sharing activity. This type of recording is called [convenience recording](teams-recording-policy.md). The recording happens in Microsoft 365 and is saved to OneDrive or SharePoint, which must be turned on for the user. For details on OneDrive and SharePoint recording storage, see [Use OneDrive and SharePoint for meeting recordings](tmr-meeting-recording-change.md).

Many users use meetings and 1-1 calls interchangeably depending on their needs. We recommend that you check your call recording policy settings as well. If the settings are different for meetings and calls, it might cause confusion for your users. To learn about managing recording for Public Switched Telephone Network (PSTN calls), see [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md).

When a meeting is recorded:

- It gets uploaded to the meeting organizer's OneDrive (private meetings) or SharePoint (channel meetings). To learn more about recordings in OneDrive and SharePoint, see [Teams meeting recording storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md).
- People invited to the meeting have permissions to view the recording (guests and external attendees can view the recording only if the recording is explicitly shared with them).
- Microsoft Purview, OneDrive file storage, and access permissions apply to the meeting recording files the same as with other files.
- It's linked in the chat for the meeting.
- It's displayed in the **Recordings and Transcripts** tab for the meeting in Teams calendar.
- It's added to various file lists across Microsoft 365: Shared with me, office.com, Recommended, Recent, etc.
- Microsoft 365 Search indexes it

Town halls and webinars follow the same process for recording. However, there are a few key differences:

- In town halls, attendees can't access the recording through the chat.
- By default, town halls and webinars are recorded automatically. Your users can stop their events from being automatically recorded with the **Record and transcribe** setting in their meeting options.
- Webinars and town halls use video on demand (VOD) to publish recordings. To learn more about VOD, see [Manage VOD publishing for webinars and town halls](manage-vod-publishing.md).

There's an option for recordings to have automatic transcription, so users can play back meeting recordings with closed captions and review important discussion items in the transcript. For more information about transcription and captions, see [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md).

For an overview of recording and transcription policies available for Teams meetings, events, and calls, see [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md).

## External participants

External participants can't record meetings except when it's a [Teams third party compliance recording](teams-recording-policy.md). If an external Teams user that's enabled for compliance recording joins a meeting or call hosted by your organization, the other organization records that meeting or call for compliance purposes, regardless of the **Meeting recording** setting in your organization. Organizers, co-organizers, and presenters in that meeting are notified and can remove the external participant from the meeting if they don't want the other org to capture recordings.

## Allow or prevent users from recording

You can use the Microsoft Teams admin center or PowerShell to control whether your users can record meetings, webinars, and town halls. Meetings, webinars, and town halls each have their own recording policies that you can manage. Both the organizer and recording initiator need to have recording permissions to record the meeting, webinar, or town hall. Organizers with a Teams Premium license can use their meeting options to control who can record and transcribe.

### Meetings

To allow or prevent meeting recordings, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Meeting policies**.
1. Either select an existing policy or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom meeting policy.
1. Toggle **Meeting recording** **On** or **Off**.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage meeting recording using PowerShell, use the **`-AllowCloudRecording`** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy). For details, see the [PowerShell section](#manage-recording-for-meetings) in this article.

### Webinars

To allow or prevent webinar recordings, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Events policies**.
1. Either select an existing policy or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom events policy.
1. Navigate to the **Recording & transcription** section.
1. Toggle **Record a webinar** **On** or **Off**.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage webinar recording using PowerShell, use the **`-RecordingForWebinar`** parameter in [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy). For details, see the [PowerShell section](#manage-recording-for-webinars) in this article.

### Town halls

To allow or prevent town hall recordings, follow these steps:

1. In the Microsoft Teams admin center, expand **Meetings** > **Events policies**.
1. Either select an existing policy or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom events policy.
1. Navigate to the **Recording & transcription** section.
1. Toggle **Record a town hall** **On** or **Off**.
1. Select **Save**.
1. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

To manage town hall recording using PowerShell, use the **`-RecordingForTownhall`** parameter in [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy). For details, see the [PowerShell section](#manage-recording-for-webinars) in this article.

## Auto recording

You can control whether organizers have access to the **Record and transcribe automatically** setting for meetings, webinars, and town halls. You can only apply this policy setting to users and groups.

When you turn on the auto recording policy for an organizer, the **Record and transcribe automatically** setting in their **Meeting options** for meetings is **Off** by default. Organizers must manually turn on this setting for each meeting they want recorded and transcribed. If you turn off auto recording, organizers don't see the setting and can’t set meetings to record automatically.

For webinars and town halls, the setting is **On** by default.

> [!NOTE]
> This setting doesn't apply to transcripts.

You must use PowerShell or a meeting template to manage this setting for organizers.

To manage this setting with meeting templates, see [IT admins - Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md). Only organizers with a Teams Premium license can use assigned meeting templates. If you prefer to prevent the organizers from changing your settings, you can lock the value you selected. Once the template is activated, users see it when scheduling meetings. If they choose to use this template, recording and transcription starts automatically without any user interaction.

To manage this setting using PowerShell, use the **`-AutoRecording`** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy). For details, see the [PowerShell section](#manage-auto-recording-in-powershell) in this article.

## Block or allow download of channel meeting recordings

**`-ChannelRecordingDownload`** is an org-wide policy parameter that controls the folder where recordings and transcripts are stored to determine whether users can download channel meeting recordings and transcripts.

The two values for this setting are:

- **Allow** (default value) - Channel meeting recordings and transcripts are saved to a **Recordings** folder in the channel's SharePoint site. The recording and transcript file permissions follow the Channel SharePoint permissions. This is the same as any other file uploaded for the channel.
- **Block** -  Channel meeting recordings and transcripts are saved to a **Recordings\View only** folder in the channel's SharePoint site. Channel owners have full access and rights to the recordings and transcripts in this folder, while channel members can only view them without the option to download or edit.

To manage this setting using PowerShell, use the **`-ChannelRecordingDownload`** parameter in [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy). For details, see the [PowerShell section](#manage-download-of-channel-meeting-recordings-in-powershell) in this article.

## Expiration policy

> [!NOTE]
> Expiration policies don't apply to webinars and town halls.

### Recordings and transcripts automatically expire

This setting allows you to manage storage by reducing the space that older recordings and transcripts use. OneDrive and SharePoint automatically monitor the expiration settings for all recordings and transcripts, moving them to the recycle bin once they reach their expiration date.

You can turn off the **Recordings and transcriptions automatically expire** setting in the Teams admin center under **Meetings** > **Meeting policies** > **Recording & transcription**.

### Default expiration time

This setting controls whether recordings and transcripts automatically expire. After turning on **Recordings and transcriptions automatically expire**, you'll get the option to set the **Default expiration time**, measured in days. Meeting recordings and transcripts have a default expiration time of 120 days.

Any changes to this setting only affect newly created recordings and transcripts. You can't change the expiration time on existing meeting recordings and transcripts.

The expiration value is an integer for days that you can set as follows:

- Minimum value: 1
- Maximum value: 99999
- -1 (PowerShell only) so the recordings and transcripts never expire

> [!NOTE]
> The maximum default expiration time for A1 users is 30 days.

To set the expiration time using PowerShell, run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -NewMeetingRecordingExpirationDays <days>
```

## Set a custom privacy policy URL

To update the Teams recording and transcription privacy policy URL with a custom link for users in and outside your org, you must use one of the following options:

- The **`-LegalURL`** parameter within the [CsTeamsMeetingConfiguration](/powershell/module/skype/set-csteamsmeetingconfiguration) PowerShell cmdlet.
- The Teams admin center through **Meeting settings** > **Email invitation** > **Privacy and Security URL**. For detailed instructions, see [Customize meeting invitations (IT admins)](customize-meeting-invitations.md).

If you don't enter a privacy and security URL in Teams meeting settings or PowerShell, we display Microsoft Entra ID's privacy policy. For more information on Microsoft Entra ID's privacy policy, see [Add your organization's privacy info using Microsoft Entra ID](/entra/fundamentals/properties-area). If there's no Microsoft Entra ID, we display the Microsoft Privacy policy.

Once you add your privacy policy URL, your URL replaces the default Teams meeting recording and transcription privacy statement.

## Require participant agreement for recording and transcription

You can use the Teams admin center or PowerShell to manage whether meetings created by organizers with this assigned policy can require participants to provide explicit consent to be recorded and transcribed. This policy also applies to channel meetings.

When the recording agreement policy is turned on, once a user either starts the meeting recording, transcription, or both, all participants are muted, with their cameras and content-share off. When a participant decides to un-mute, turn on their camera, or share content, they’re asked to respond **'Yes'** or **'No'** to consent to be included in the meeting recording and transcription. If a participant responds **'No'** to the question, they have a view-only meeting experience. View-only participants can't start recording or transcription for any meetings that require explicit consent.

The consent choice for each participant is included in the attendance report. Participants who aren't in the attendance report—due to the admin policy or opting out—are required to provide consent. When the attendance report is disabled or participants aren't in the attendance report, organizers and co-organizers don't see consent data. However, as an admin, you can still see consent data in the audit logs.

### Manage recording consent

You can use the Teams admin center or the **`-ExplicitRecordingConsent`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to manage recording consent. This parameter also manages recording consent for Audio Conferencing. To learn about recording consent for Audio Conferencing, see [Explicit recording consent for Audio Conferencing](conferencing-recording-consent.md).

To manage this feature using PowerShell, see the [PowerShell section](#manage-whether-meetings-require-participant-agreement-for-recording-and-transcription) in this article.

The following table shows the behaviors of the settings for explicit consent:

|Teams admin center value|PowerShell value| Behavior|
|---------|---------------|---------------|
|On|Enabled| For organizers with this policy, all their meetings require participants to provide consent to be recorded and transcribed.|
|Off|Disabled| **This setting is the default value.** For organizers with this policy, participants aren't asked for consent to be recorded and transcribed. All participants are included in recordings and transcripts from these organizers' meetings.|

To manage recording consent for your organization in the Teams admin center, follow these steps:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one. To apply changes to all users in your organization who don't have an existing policy assignment, use the **Global policy**. To exclude certain users from the global policy, create and assign a custom meeting policy.
5. Within your chosen policy, navigate to the **Recording & Transcription** section.
6. Toggle the **Require participant agreement for recording and transcription** setting **On** or **Off**.
7. Select **Save**.
8. To assign the policy:
    - **To specific users**: Select your policy > select **Manage users** > **Assign users** > enter in the search bar the names of specific users and select **Add** > select **Apply**.
    - **To groups**: Select **Group policy assignment** > select **Add** > enter the group's name and enter the policy's name > select **Apply**.

### View consent data

There are two ways for you to view consent data. The first way is in the [Teams meeting attendance and engagement report](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report). The second is with the **Added information about meeting participants** filter in the Teams meeting audit logs in Purview. Consent data is in the audit logs regardless of your policy that manages the attendance and engagement report or your users' option for tracking attendance. To learn more about audit logs in Purview, see [Audit log activities](/purview/audit-log-activities#microsoft-teams-activities).

:::image type="content" source="media/audit-rec-small.png" alt-text="Screenshot of Teams meeting audit logs in Purview that show consent data." lightbox="media/audit-rec-expand.png":::

### Supported and unsupported endpoints and platforms

#### Auto consent endpoints and platforms

The following user types are auto consented for recording and transcription without any participant interaction. They get a consent notification, and their consent data is logged as 'not applicable' or 'auto consent':

- Teams Rooms on Android
- Teams Rooms on Windows
- Third party video conferencing devices via Cloud Video Interop (CVI)
- Third party video conferencing devices connecting via Direct Guest Join (DGJ)

#### Supported endpoints and platforms

Explicit consent is supported on the following endpoints:

- Mobile Teams (Android and iOS)
- Meeting participants dialing in using [Audio Conferencing](conferencing-recording-consent.md)
- PSTN calls
- Shared devices
- Teams native Mac
- Teams native Windows
- Teams Phone devices (including audio conferencing phone devices)
- Teams Web
- VDI

#### Unsupported endpoints and platforms

In meetings requiring explicit consent, users joining from unsupported endpoints have the view-only experience. Explicit consent isn’t supported on the following endpoints, along with any endpoints not listed under supported endpoints:

- CarPlay
- Old version native clients
- Teams Displays

## Compliance

End users can modify the expiration date of any recordings they control, so you shouldn't rely on meeting expiration settings for legal protection.

### Recording expiration settings and Microsoft 365 retention policies in Microsoft Purview

#### File retention vs expiration policies

File retention takes precedence over file deletion. A Teams meeting recording expiration policy can't delete a Teams meeting recording with a Purview retention policy until after the retention period is completed. For example, if you have a Purview retention policy that says a file will be kept for five years and a Teams meeting recording expiration policy set for 60 days, the Teams meeting recording expiration policy permanently deletes the recording after five years.

Once the recording reaches the expiration date, it gets deleted from the user's OneDrive, and is copied to the organization's Preservation Hold library. Your users can't see the recording in OneDrive anymore, but as an admin, only you can find the recording in the Preservation Hold library. To learn more about the Preservation Hold library, see [Learn about retention for SharePoint and OneDrive](/purview/retention-policies-sharepoint#how-retention-works-for-sharepoint-and-onedrive).

#### Expiration vs deletion policies

If you have a Teams meeting recording expiration policy and Purview deletion policy with different deletion dates, the file is deleted at the earliest of the two dates. For example, if you have a Purview deletion policy that says a file will be deleted after one year and a Teams meeting recording expiration set for 120 days, the Teams meeting recording expiration policy will delete the file after 120 days.

#### Deleting recordings before the expiration date

Users can manually delete their recordings before the expiration date unless there's a Purview retention policy that prevents it. If a user manually deletes a recording that's still in the retention period, the recording is held in the Preservation Hold library. However, the recording shows as deleted to the end user. To find out more, see [Learn about retention for SharePoint and OneDrive](/microsoft-365/compliance/retention-policies-sharepoint).

### Deletion of recordings

On the expiration date, the recording is moved into the recycle bin and the expiration date field is cleared. If a user recovers a recording from the recycle bin, the meeting expiration setting doesn't delete it again.

Usually, the recording is deleted within a day after the expiration date but in rare instances could take as long as five days. The file owner receives an email notification when the recording expires and is directed to the recycle bin if they want to recover the recording.

### Expiration of migrated recordings from Stream (Classic)

Migrated recordings from Stream (Classic) don't come with an expiration set on them. Instead, we encourage you to only migrate recordings that they want to retain.

## Permissions and storage

Teams meeting recordings are stored in the organizer's OneDrive and SharePoint storage. The location and permissions depend on the type of meeting and the role of the user in the meeting. Users that have full edit rights on the video recording file can change the permissions and share it later with others as needed. To understand permissions and storage in OneDrive and SharePoint, see [Use OneDrive and SharePoint for meeting recordings](tmr-meeting-recording-change.md).

## eDiscovery search for recordings and transcripts

To find your users' recording and transcript files using eDiscovery, follow these steps:

1. Navigate to the [Microsoft Purview portal](https://purview.microsoft.com/).
1. In the search box, enter 'eDiscovery'
1. Follow the steps in the linked article to create an eDiscovery case: [Create and manage an eDiscovery (Premium) case](/purview/ediscovery-create-and-manage-cases).
1. Open the case and on the **Collections** tab and select **New collection**.
1. Commit the new collection.
1. Open **Review set**, and use the filter to find the recordings and transcripts you're looking for.

## Troubleshooting

To learn about why users can't record meeting, see [I can't record a meeting in Microsoft Teams](https://support.microsoft.com/office/i-can-t-record-a-meeting-in-microsoft-teams-f35329c2-57b1-487f-b5e3-70a7efb0945b).</br>
To learn how to use diagnostic tools, see [Issues that affect meeting recordings](/microsoftteams/troubleshoot/meetings/troubleshoot-meeting-recording-issues).

## PowerShell

Start by connecting to Windows PowerShell.

After you create or update new policies, you can assign them to users or groups. For more information on assigning policies to users and groups using PowerShell, see [Assign policies to users and groups](assign-policies-users-and-groups.md).

### Manage recording for meetings

To allow everyone in your organization to record, except users with an assigned custom meeting policy, run the following command:

```powershell
Set-CsTeamsMeetingPolicy -Identity Global -AllowCloudRecording $true
```

To allow specific users in your organization to record, run the following commands:

1. Create a new policy.

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity "Your Policy Name" -AllowCloudRecording $true
    ```

2. Assign specific users the policy.

    ```powershell
    Grant-CsTeamsMeetingPolicy -Identity "user@contoso.onmicrosoft.com" -PolicyName "Your Policy Name"
    ```

To allow specific groups in your organization to record, run the following commands:

1. Create a new policy.

    ```powershell
    Set-CsTeamsMeetingPolicy -Identity "Your Policy Name" -AllowCloudRecording $true
    ```

2. Assign specific groups the policy.

    ```powershell
    Grant-CsTeamsMeetingPolicy -Group "Group ID" -PolicyName "Your Policy Name"
    ```

### Manage recording for webinars

Use the following script to allow users with this policy to record webinars:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -RecordingForWebinar Enabled
```

Use the following script to prevent users with this policy from recording webinars:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -RecordingForWebinar Disabled 
```

### Manage recording for town halls

Use the following script to allow users with this policy to record town halls:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -RecordingForTownhall Enabled
```

Use the following script to prevent users with this policy from recording town halls:

```PowerShell
Set-CsTeamsEventsPolicy -Identity <policy name> -RecordingForTownhall Disabled 
```

### Manage whether meetings require participant agreement for recording and transcription

The **`-ExplicitRecordingConsent`** parameter also controls recording consent for Audio Conferencing. To learn about explicit consent for Audio Conferencing, see [Explicit recording consent for Audio Conferencing](conferencing-recording-consent.md).

To require participants to give their explicit consent to be recorded or transcribed in any meeting that organizers with this policy create, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -ExplicitRecordingConsent Enabled
```

### Manage auto recording in PowerShell

To give organizers with this policy the option to record their meetings, webinars, and town halls automatically, follow this script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AutoRecording Enabled
```

To prevent organizers with this policy from recording their meetings, webinars, and town halls automatically, follow this script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AutoRecording Disabled
```

### Manage download of channel meeting recordings in PowerShell

To prevent users in your organization from downloading channel meeting recordings and transcripts from OneDrive and SharePoint, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -ChannelRecordingDownload Block
```

To allow users in your organization to download channel meeting recordings and transcripts from OneDrive and SharePoint, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -ChannelRecordingDownload Allow
```

## Related topics

- [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
- [Use OneDrive and SharePoint to store meeting recordings](tmr-meeting-recording-change.md)
- [Introduction to Microsoft Teams third party compliance recording](teams-recording-policy.md)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Live event recording policies in Teams](teams-live-events/live-events-recording-policies.md)
- [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019)
- [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Configure call recording, transcription, and captions in Teams](call-recording-transcription-captions.md)
