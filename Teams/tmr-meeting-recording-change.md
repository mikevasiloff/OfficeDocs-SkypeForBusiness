---
title: Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint
ms.author: wlibebe
author: wlibebe
ms.reviewer: yudma, yujin1, lisma, ritikag
ms.date: 7/19/2024
manager: pamgreen
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: meetings
search.appverid: MET150
description: Learn about how meeting recordings are stored in OneDrive and SharePoint, and permissions.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
---

# Teams meeting recording and transcript storage and permissions in OneDrive and SharePoint

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Town halls ![Image of a checkmark for yes](/office/media/icons/success-teams.png) Calls

> [!NOTE]
> When organizers turn off Microsoft 365 Copilot in Teams meetings and events, recording and transcription are also turned off. To learn more about Copilot, see [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md).

When users in your organization record and transcribe Teams meetings, the recordings and transcripts are stored in either OneDrive for work or school and SharePoint. Depending on where your users access the file, the recording plays on the video player in OneDrive or SharePoint. This article helps you, as an admin, understand recording and transcript storage and permissions for OneDrive and SharePoint.

To learn about your recording policies, see [Teams meeting recording](meeting-recording.md). To learn how to block the download of Teams meeting recording files from SharePoint or OneDrive, see [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md).

## Recording storage

### Meetings and events

For **meetings and events**, you can use the per-organizer **`-MeetingRecordingOwnership`** parameter within the PowerShell [**CsTeamsRecordingRolloutPolicy**](/powershell/module/teams/set-csteamsrecordingrolloutpolicy) cmdlet to decide if the recording is saved to the organizer's or recording initiator's OneDrive. This policy applies to the following types of meeting and events:

- Automatically recorded meetings
- Delegate-created meetings
- Manually recorded meetings
- Meet now meetings
- Meetings scheduled in Outlook
- Meetings scheduled in the Teams client
- Recurring meetings
- Town halls
- Webinars

If **`-MeetingRecordingOwnership`** is set to **`MeetingOrganizer`**, which is the **default value**, the recording saves to the organizer's OneDrive, even if the organizer didn't attend the meeting or event. All recording files are saved to the organizer's OneDrive **Recordings** folder. Co-organizers have the same editing permissions as organizers for recording files. To understand what happens if an organizer doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

If **`-MeetingRecordingOwnership`** is set to **`RecordingInitiator`**, the recording saves to the OneDrive of the user who starts the recording. If the recording initiator doesn't have a OneDrive, the recording is temporarily saved to async media storage.

#### Delegate-created meetings

For meetings in which an organizer appoints a **delegate** who has permission to act on the organizer's behalf, all recording files are automatically saved to the organizer's **Recordings** folder in OneDrive. When delegates are added as co-organizers, they have the same editing permissions as organizers for recording files.

### 1:1 and group calls

For 1-1 call and group calls, recording files go to the OneDrive account of the user who selected **Record**.

### Channel meetings

For **Channel meetings**, the recording is stored in the SharePoint Teams site documentation library in a folder named **Recordings**. For example: *Teams name - Channel name*/**Documents**/**Recordings**.

### Shared mailbox scheduled meetings

For **meetings scheduled using a shared mailbox**, the shared mailbox is considered the organizer. If the shared account has a OneDrive, the recording is uploaded there. However, since shared mailboxes typically don’t have a OneDrive, the recordings are uploaded to the co-organizer’s or recording initiator's OneDrive instead. To understand what happens if an organizer doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

For details on shared mailboxes, see [About shared mailboxes - Microsoft 365 admin](/microsoft-365/admin/email/about-shared-mailboxes).

> [!NOTE]
> When shared mailboxes don't have a Teams license, they follow the global identity's meeting policy. If a shared mailbox without a Teams license organizes a meeting and you set **`-allowCloudRecording`** to false in the global policy, your users can't record. If you want to set a custom meeting policy for a shared mailbox, you must assign a Teams license first.

### Video on Demand (VOD)

When organizers record webinars and town halls, the recordings are stored in OneDrive. Once an organizer uses VOD to publish event recordings, the recordings are stored in SharePoint Embedded File Storage Containers. Only the event organizers can manage the recordings of past town halls in their calendar.

> [!NOTE]
> As an admin, although you can find the event recording in the SharePoint Embedded Container, you can only delete the recording in the Teams admin center.

To learn more about SharePoint Embedded File Storage Containers, see [Overview of SharePoint Embedded](/sharepoint/dev/embedded/overview).

#### Delete a VOD event recording

1. Open the Teams admin center.
2. Expand **Analytics and reports** from the navigation pane.
3. Under **Analytics and reports**, select **Usage reports**.
4. On the **View reports** tab, under Report, either select **Town hall usage reports** or **Webinar usage reports**.
5. In the table, find the event that you want to delete the recording for and select the row. The names of recordings follow this pattern of *'Teams Virtual Event VOD Container evt_{EventId}_rec_{RecordingId}'*.
6. Select **Delete event data**.

To learn more about VOD, see [Manage VOD publishing for webinars and town halls](manage-vod-publishing.md).

### Microsoft Teams Rooms meetings

For **Microsoft Teams Rooms meetings**, when a user creates a meeting using the **Meet now** button in a Teams Room, the Teams Room itself becomes the meeting organizer, and by default, the recording is stored in the Teams Room's OneDrive account, if available. However, none of the meeting participants have full permissions to the file. To give meeting participants full permissions to the recording file, avoid assigning a OneDrive license to your Teams Room's resource account.

When a Teams Room's resource account doesn't have a OneDrive license and storage, the recording gets saved to the co-organizer's or recording initiator's OneDrive. For details on what happens if a co-organizer or recording doesn't have a OneDrive account, see the **Recording storage for organizers without OneDrive accounts** section in this article.

To learn more about Microsoft Teams Rooms meetings, see [Microsoft Teams Rooms (Windows)](https://support.microsoft.com/office/microsoft-teams-rooms-windows-e667f40e-5aab-40c1-bd68-611fe0002ba2).

### Recording storage for organizers without OneDrive accounts

When the organizer doesn’t have a OneDrive account, here's what happens, in order, to the meeting recording:
  
1. The recording is saved to the co-organizer's OneDrive, while the meeting or event organizer retains permissions to edit and share the recording. When there are multiple co-organizers, the recording saves to the co-organizers' OneDrive, ordered by the first letter or number of each co-organizer's Microsoft Entra object ID. To find the object IDs for users in your org, see [Locate important IDs for a user](/partner-center/account-settings/find-ids-and-domain-names#find-the-user-object-id).

   Let's take a look at the following example with three co-organizers:

   :::image type="content" source="media/mr-objectid-small.png" alt-text="Screenshot of the object IDs for three organizers. The first organizer's object ID starts with the letter one, the first character in the second organizer's object ID is the letter d, and the first letter in the third organizer's object ID is the letter a." lightbox="media/mr-objectid-expand.png":::

   In this example, the recording is saved to co-organizer 1’s OneDrive account. If co-organizer 1 doesn’t have a OneDrive account, the recording is saved to co-organizer 3’s OneDrive. If co-organizer 3 also doesn’t have a OneDrive account, the recording is then saved to co-organizer 2’s OneDrive.

1. If none of the co-organizers have OneDrive accounts, the recording is saved to the OneDrive account of the user who initiated the recording.
1. If the user who initiated the recording doesn’t have a OneDrive, the recording gets temporarily stored to async media storage.

### Async media storage

If a Teams meeting recording fails to successfully upload to OneDrive because the organizer, co-organizers and recording initiator don’t have OneDrive accounts, or the storage quota is full, an error message appears. The recording is instead temporarily saved to async media storage. Once the recording is in async media storage, no retry attempts are made to automatically upload the recording to OneDrive or SharePoint. During that time, the organizer must download the recording. The organizer can try to upload the recording again if they get a OneDrive or SharePoint license, or clear some space in their storage quota. If not downloaded within 21 days, the recording is deleted.

### Videos

Videos are just like any other file in OneDrive and SharePoint. Handling ownership and retention after someone leaves follows the standard [OneDrive and SharePoint process](/onedrive/retention-and-deletion).

### Retention labels

To learn how to apply retention labels to Teams meeting recordings, see [How to auto-apply a retention label](/microsoft-365/compliance/apply-retention-labels-automatically).

### Planning for storage

The size of a one-hour recording is 400 MB. Make sure you understand the capacity required for recorded files and have sufficient storage available in OneDrive and SharePoint. Read [Set the default storage space for OneDrive](/sharepoint/set-default-storage-space) and [Manage SharePoint site storage limits](/sharepoint/manage-site-collection-storage-limits) to understand the base storage included in the subscription and how to purchase more storage.

## Viewing permissions

For **non-Channel meetings**:

- All meeting invitees, except for external participants, automatically get a personally shared link. The meeting organizer must add external participants to the shared list.
- If the meeting is forwarded, only participants who are automatically added to the meeting chat thread receive the recording link.
- For optimal performance, the total number of users in a chat shouldn't exceed 1,000.
- If a meeting is forwarded to a group, only some users are added to the chat. If forwarded to an individual user, they're added to the meeting chat unless there are more than 1,000 users in the chat. 
- For **large meetings**, if a meeting has more than 250 participants, some participants don't automatically have file permissions. Excluded participants should ask the recording owner to add them to the shared list.

For **Channel meetings**, permissions are inherited from the owners and members list in the channel.

## Recording quotas

Teams meeting recording files live in OneDrive and SharePoint and are included in your quota for those services. To learn more, see
[SharePoint quota](/sharepoint/sites/plan-site-maintenance-and-management#quotas), [Sharepoint limits](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits), and [OneDrive quota](/onedrive/set-default-storage-space).

## Transcripts and captions

### Transcripts

You can choose to delete Teams meeting recordings along with their accompanying transcripts by using an *auto-apply retention label policy* that identifies these files from OneDrive and SharePoint transcript or OneDrive transcript. For more information, see [Automatically apply a retention label to Microsoft 365 items](/purview/apply-retention-labels-automatically).

Here are the most relevant sections to help you get started:

- [How to create an auto-apply retention label policy](/purview/apply-retention-labels-automatically#how-to-create-an-auto-apply-retention-label-policy)
- [Auto-apply labels to content with keywords or searchable properties](/purview/apply-retention-labels-automatically#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Identifying Teams meeting recordings and accompanying transcripts in OneDrive and SharePoint](/purview/apply-retention-labels-automatically#microsoft-teams-meeting-recordings)
- [How long it takes for retention labels to take effect](/purview/apply-retention-labels-automatically#how-long-it-takes-for-retention-labels-to-take-effect)

> [!NOTE]
> When you create a retention label policy in Microsoft Purview, the minimum retention period is one day. The recordings and accompanying transcripts are deleted after one day.

### Captions

Captions help create inclusive content for viewers of all abilities. Closed captions for Teams meeting recordings are available during playback if transcription was turned on at the time of recording. To allow users to record meetings with transcripts, you must assign a policy with transcription turned on. To learn more about managing transcription for your users, see [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md).

Closed captions aren't fully supported if the Teams meeting recording is moved or copied from its original location in OneDrive or SharePoint.

You can use the **Meetings automatically expire** setting in the Teams admin center to control when captions expire. To learn more, see [Manage Teams recording policies for meetings and events](meeting-recording.md#expiration-policy).

## Permissions or role-based access

> [!NOTE]
> We recommend that the recipient is required to be a logged-in user when sharing Teams meeting recordings. Select the **People in (Your Organization)** option when you share the file as documented in [Share SharePoint files or folders](https://support.microsoft.com/office/1fe37332-0f9a-4719-970e-d2578da4941c). External sharing isn't designed for the distribution of large files or a large number of files.

|Meeting type                               | Who selected Record?| Where does the recording land?                               |Who has access? R/W, R, or sharing                                                                                                                                                                                                                                                     |
|-------------------------------------------|-----------------------|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|1:1 call with internal parties             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full permissions. <br /><br />Callee has read-only access, but no sharing or download permissions. <br /><br />|
|1:1 call with internal parties             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full permissions. <br /><br />Caller has read-only access, but no sharing or download permissions. <br /><br />|
|1:1 call with an external call             |Caller                 |Caller’s OneDrive account                        |Caller is owner and has full permissions.<br /> <br />Callee has no access. Caller must share it to the Callee.|
|1:1 call with an external call             |Callee                 |Callee’s OneDrive account                        |Callee is owner and has full permissions.<br /><br />Caller has no access. Callee must share it to the Caller.|
|Group call                                 |Any member of the call |Group member who selected Record’s OneDrive account  |Member who selected Record has full permissions. <br /><br /> Other group members from the same organization have Read rights. <br /><br /> Other group members from different organization have no permissions to it.|
|Adhoc/Scheduled meeting                    |Organizer              |Organizer’s OneDrive account                     |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same organization as the organizer have read access, but no sharing and download permissions.|
|Adhoc/Scheduled meeting                    |Other meeting member   |Organizer’s OneDrive account                                  |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same organization as the organizer have read access.|
|Adhoc/Scheduled meeting with external participants|Organizer              |Organizer’s OneDrive account                     |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /> <br />  All other members of the meeting from the same organization as the organizer have read access. <br /><br /> All other external participants have no access, and the Organizer must share it to them.|
|Adhoc/Scheduled meeting with external participants|Other meeting member   |Organizer’s OneDrive account                                  |Organizer has full permissions to the recording. Co-organizers and organizer have edit permissions and can share. <br /><br /> All other members of the meeting from the same organization as the organizer have read access. <br /><br />All other external participants have no access, and the Organizer must share it to them.|
|Channel meeting                            |Channel Member         |Teams SharePoint location for that channel. Channel meeting recording upload to SharePoint isn't supported for IP-based restrictions. We recommend using [Azure conditional access](/azure/active-directory/conditional-access/overview). |Member who selected on Record has edit permissions to the recording. <br /> <br />Every other member’s permissions are based on the Channel SharePoint permissions.|

## Related topics

- [Overview- Recording and transcription for Teams meetings, events, and calls](recording-transcription-overview.md)
- [Which policy takes precedence?](./policy-assignment-overview.md#which-policy-takes-precedence)
- [Teams meeting recording](meeting-recording.md)
- [Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)
- [Policy recommendations for securing SharePoint sites and files](/security/zero-trust/zero-trust-identity-device-access-policies-sharepoint)
