---
title: Export content with the Microsoft Teams Export APIs
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: reference
audience: admin
ms.service: msteams
ms.date: 01/29/2025
description: In this article, you learn about how to export Teams content using the Microsoft Teams Export APIs.
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - NewAdminCenter_Update
  - seo-marvel-apr2020
ms.collection:
  - M365-collaboration
appliesto:
  - Microsoft Teams
---

# Export content with the Microsoft Teams Export APIs

Teams Export APIs allow you to export 1:1, group chat, meeting chats, and channel messages from Microsoft Teams. If your organization needs to export Microsoft Teams messages, you're able to extract them using Teams Export APIs. *Chat Message* represents an individual chat message within a [channel](/graph/api/resources/channel) or [chat](/graph/api/resources/chat). The chat message can be a root chat message or part of a reply thread that is defined by the **replyToId** property in the chat message.

Here are some examples on how you can use these export APIs:

- **Example 1**: If you enabled Microsoft Teams in your organization and want to export all the Microsoft Teams messages to date programmatically by passing the date range for a given user or team.

- **Example 2**: If you want to programmatically export all user or team messages daily by providing a date range. Export APIs can retrieve all the messages created or updated during the given date range.

- **Example 3**: If you want to programmatically export the links to Teams meeting recordings for a given meeting organizer, and then download the actual recordings.

- **Example 4**: If you want to programmatically export the links to Teams meeting transcripts for a given meeting organizer, and then download the actual transcripts.

## What is supported by the Teams Export APIs?

- **Bulk Export of Teams Message:** Please refer to [Teams Export APIs throttling limits](/graph/throttling-limits). With these limits you should be able to bulk export Teams messages. 

- **Top Limit for Teams Meesage:** The TOP filter limit for Teams Message APIs is recommended to be set at 250 as the maximum limit beyond which the performance would be limited.
- **Application Context**: To call Microsoft Graph, your app must acquire an access token from the Microsoft identity platform. The access token contains information about your app and the permissions it has for the resources and APIs available through Microsoft Graph. To get an access token, your app must be registered with the Microsoft identity platform and be authorized by either a user or an administrator for access to the Microsoft Graph resources it needs.
    If you're already familiar with integrating an app with the Microsoft identity platform to get tokens, see the [Next Steps](/graph/auth/auth-concepts#next-steps) section for information and samples specific to Microsoft Graph.
- **Hybrid Environment:** Export APIs support messages sent by users who are provisioned on Hybrid Environment (on-premises Exchange and Teams). Any messages sent by users who are configured for hybrid environment are accessible using Export APIs.
- **User Deleted Messages:** Messages deleted by users from the Teams client can be accessed using export APIs up to 21 days from the time of deletion.
- **Message Attachments:** Export APIs include the links to the attachments sent as part of messages. Using Export APIs you can retrieve the files attached in the messages.
- **Reactions:** Export APIs support reactions initiated by a user on a Teams message. Reactions currently supported are heart, angry, like, sad, surprised, and laugh. In addition to Reactions, Export API also supports Reaction Edit History, which includes changes and updates made to a reaction on a message.

> [!NOTE]
> Reactions customized with color changes are currently not supported by Export API.

- **Shared Channel Messages:** Export APIs support capturing messages from a Shared Channel.
- **Deleted Teams:** Export API supports [capturing messages from deleted Teams](/graph/api/deletedteam-getallmessages) and deleted standard, private, and shared channels.
- **Deleted Users**: Export API supports capturing messages for deleted users up to 30 days from the time the user was deleted. To find the list of deleted users, see [Deleted Items](/graph/api/directory-deleteditems-list).
- **Inactive Users**: Export API supports capturing messages for inactive users up to 30 days from the time the user becomes inactive. To find the list of inactive mailboxes, see [Inactive mailboxes](/purview/create-and-manage-inactive-mailboxes#view-a-list-of-inactive-mailboxes).
- **Chat Message Properties:** Refer to the [complete list of properties that Teams Export APIs support](/graph/api/resources/chatmessage#properties).
- **Control Messages:** Export API supports capturing control messages in addition to the user generated messages. Control Messages are system generated messages that appear on the Teams client and carry important information such as "User A added User B to the chat and shared all chat history" along with the timestamp. System messages enable the caller to have insights about events that happened in a team, a channel, or a chat. Refer to [the list of control messages](/graph/system-messages#supported-system-message-events) that Export API currently supports.

> [!NOTE]
> Meeting related control messages are currently not supported by Export API.

- **Edited History:** If [your tenant is setup with Teams Retention Policy](/purview/create-retention-policies?tabs=teams-retention), Export API supports capturing messages' edited history for [individual & group chat](/graph/api/chat-getallretainedmessages), and [posts, comments in Public & Shared channels](/graph/api/channel-getallretainedmessages).

    To learn more about Teams Retention policy, see the [Manage retention policies for Microsoft Teams](/microsoftteams/retention-policies) for further details.
  
- **Meeting Transcripts:** Get all transcripts from scheduled online meeting instances for which the specified user is the organizer. This API currently only supports private scheduled meetings.

- **Meeting Recordings:** Get all recordings from scheduled online meeting instances for which the specified user is the organizer. This API currently only supports private scheduled meetings.

## How to access Teams Export APIs

- **Example 1** is a simple query to retrieve all the messages of a user or team without any filters:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages
  ```

  ```HTTP
  GET https://graph.microsoft.com/v1.0/teams/{id}/channels/getAllMessages
  ```

- **Example 2** is a sample query to retrieve all the messages of a user or team by specifying date time filters and top 50 messages:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages?$top=50&$filter=lastModifiedDateTime gt 2020-06-04T18:03:11.591Z and lastModifiedDateTime lt 2020-06-05T21:00:09.413Z
  ```

  ```HTTP
  GET https://graph.microsoft.com/v1.0/teams/{id}/channels/getAllMessages?$top=50&$filter=lastModifiedDateTime gt 2020-06-04T18:03:11.591Z and lastModifiedDateTime lt 2020-06-05T21:00:09.413Z
  ```

- **Example 3** is a sample query to retrieve the links to all the available Teams meetings recordings of a user. Date-range filtering is supported. TOP n filter is supported similar to Chat messages:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/onlineMeetings/getAllRecordings?$filter=MeetingOrganizer/User/Id eq ‘{id}’
  ```

  ``` http
  GET  https://graph.microsoft.com/v1.0/users/{id}/onlineMeetings/getAllRecordings(meetingOrganizerUserId='{userId}',startDateTime={startDateTime},endDateTime={endDateTime})
  ```
- **Example 4** is a sample query to retrieve the links to all the available Teams meetings transcripts of a user. Date-range filtering is supported. TOP n filter is supported similar to Chat messages:

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/onlineMeetings/getAllTranscripts?$filter=MeetingOrganizer/User/Id eq ‘{id}’
  ```

  ```HTTP
  GET https://graph.microsoft.com/v1.0/users/{id}/onlineMeetings/getAllTranscripts(meetingOrganizerUserId='{userId}',startDateTime={startDateTime},endDateTime={endDateTime})
  ```

> [!NOTE]
> The API returns response with next page link in case of multiple results. For getting next set of results, simply call GET on the url from @odata.nextlink. If @odata.nextlink isn't present or null, then all messages are retrieved.

> [!NOTE]
> The order of messages in the response isn't guaranteed to be sorted by any datetime, such as createdDateTime nor lastModifiedDateTime.

## Prerequisites to access Teams Export APIs

- Microsoft Teams APIs in Microsoft Graph that access sensitive data are considered protected APIs. You can call these APIs as long as the requirements for [accessing without a user](/graph/auth-v2-service) are met.

- Application permissions are used by apps that run without a signed-in user present; application permissions can only be approved by an administrator. The following permissions are needed:
  
  - *Chat.Read.All*: enables access to all 1:1, Group chat, and meeting chat messages.
  
  - *ChannelMessage.Read.All*: enables access to all channel messages.
  
  - *User.Read.All*: enables access to the list of users for a tenant.
  
  - *OnlineMeetingTranscript.Read.All*: enables access to transcripts for all 1:n scheduled Teams meetings.
  
  - *OnlineMeetingRecording.Read.All*: enables access to recordings for all 1:n scheduled Teams meetings.

## License requirements for Teams Export APIs

Export API supports Security and Compliance (S+C) and general usage scenarios through a model query parameter. S+C scenarios (Model A) include seeded capacity and require an E5 subscription and general usage scenarios (Model B) are available for all subscriptions and is consumption only. For more information about seeded capacity and consumption fees, see [Licensing and payment requirements for Microsoft Graph Teams APIs](/graph/teams-licenses).

For Beta APIs, there are currently no Model A or Model B licensing or usage enforcements. However, there may be licensing or usage enforcements in the future.

### S+C/Model A scenarios

Restricted to applications performing security and/or compliance functions, users must have specific E5 licenses to use this functionality and receive seeded capacity. Seeded capacity is per user and is calculated per month and is aggregated at the tenant level. For usage beyond the seeded capacity, app owners are billed for API consumption. Model A can only access messages from users with an assigned E5 license.

|Partner Name|Partner Solution|
|---|---|
|![logo-of-smarsh](media/smarsh-logo.png) |[Microsoft Teams Archiving and Compliance](https://www.smarsh.com/channel/microsoft-teams/)|
|:::image type="content" source="media/export-API-teams/proofpoint-logo-blacktype-final-5b.png" border="false" alt-text="Screenshot of logo of Proofpoint.":::|[Proofpoint Content Capture for Microsoft Teams](https://www.proofpoint.com/resources/data-sheets/proofpoint-content-capture-microsoft-teams)|

### General usage/Model B scenarios

Available for all non-S+C related scenarios, there are no license requirements or seeded capacity. When consumption meters become available, app owners are charged for all monthly API calls.

The following partners are certified. Your company may choose to work with any combination of these partners within your enterprise.

|Partner Name|Partner Solution|
|---|---|
|![logo-of-rubrik](media/rubrik.png) |[Microsoft Teams backup and recovery](https://www.rubrik.com/solutions/microsoft-365) |
|![logo-of-veeam](media/veeam.png) |[Microsoft Teams backup and recovery](https://www.veeam.com/backup-microsoft-office-365.html) |

### Next steps
If you're a vendor seeking to join the certification program, fill out [this form](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbRymC9dkiqEZFkLXIAijLzONUREtFR1JKR1lQVFJCVFc5QlJaS1FDWEhaSS4u) as the next step. If you need to provide more context and details, mail to MS Teams Ecosystem Team (TeamsCategoryPartner@microsoft.com).

### Evaluation Mode (default)

No model declaration enables access to APIs with limited usage per each requesting application for evaluation purposes.

## JSON representation

1. The following example is a JSON representation of the chat resource:

   Namespace: microsoft.graph

   ```JSON
   {
    "id": "string (identifier)",
    "replyToId": "string (identifier)",
    "from": {"@odata.type": "microsoft.graph.identitySet"},
    "etag": "string",
    "messageType": "string",
    "createdDateTime": "string (timestamp)",
    "lastModifiedDateTime": "string (timestamp)",
    "deletedDateTime": "string (timestamp)",
    "subject": "string",
    "from": {
                "application": null,
                "device": null,
                "conversation": null,
                "user": {

                    "id": [{"@odata.type": "microsoft.graph.user"}],
                    "displayName": "User Name",

                    "userIdentityType": "aadUser"                }
            },
    "body": {"@odata.type": "microsoft.graph.itemBody"},
    "summary": "string",

    "chatId": [{"@odata.type": "microsoft.graph.chat"}]

    "attachments": [{"@odata.type": "microsoft.graph.chatMessageAttachment"}],
    "mentions": [{"@odata.type": "microsoft.graph.chatMessageMention"}],
    "importance": "string",
    "locale": "string",
    }
    ```

    > [!NOTE]
    > For more information on chatMessage resource, see the [chatMessage resource type](/graph/api/resources/chatmessage) article.

2. The following example is a JSON representation of the recording resource:

    Namespace: microsoft.graph

    ```JSON
    {
     "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(meetingRecording)", 
     "@odata.count": 2, 
     "@odata.nextLink": "https://graph.microsoft.com/v1.0/users('{userId}')/onlineMeetings/getAllRecordings?$filter=MeetingOrganizer%2fUser%2fId+eq+%27{userId}%27&$skiptoken=MSMjMCMjTkNaYVNIQjVVbXRPYWxaV1dscGFWVGg1V2pOb1IxUXpRWGxrUm1oTFVrWmtTV1ZyYkhwUlZVWm9UMWR3VEdWWGRFTlJWVVpDVVZFOVBRPT0%3d", 
     "value":
       [ 
         { 
          "@odata.type": "#microsoft.graph.meetingRecording", 
          "id": "6263af16-b660-41d0-a17b-83fbd15a39c7", 
          "meetingId": "MSoxMjczYTAxNi0yMDFkRLTmOTUtODA5My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19aR1F3WTJZNE9XTXROekppWlMwME1XWTRMVGc0TWpBdE1BBXdOV1kzWlRsak9UTXlAdGhyZWFkLnYy", 
          "meetingOrganizerId": "{userId}", 
          "createdDateTime": "2022-08-03T20:43:36.2573447Z", 
          "recordingContentUrl":    "https://graph.microsoft.com/v1.0/users/{userId}/onlineMeetings/MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19aR1F3WTJZNE9XTXROekppWlMwME1XWTRMVGc0TWpBdE1ERXdOV1kzWlRsak9UTXlAdGhyZWFkLnYy/recordings/MSMjMCMjMGFjNmUwZTgtYmZjYy00NDQxLTk2MGYtZjllNjVhNjI0NzBh/content" 
         }, 
         { 
          "@odata.type": "#microsoft.graph.meetingRecording", 
          "id": "{recordingId}", 
          "meetingId": "{meetingId}", 
          "meetingOrganizerId": "{userId}", 
          "createdDateTime": "2022-08-03T20:44:11.2635254Z", 
          "recordingContentUrl": " https://graph.microsoft.com/v1.0/users/{userId}/onlineMeetings/{meetingId}/recordings/{recordingId}/content" 
          },
        ] 
       }
     ```

   Where: 

   - `<id>` represents a single recording.

   - `<meetingId>` represents a meeting or call identifier.

   - `<meetingOrganizer/user/id>` represents the organizer of the meeting.

   - `<createdDateTime>` indicates the start time of the meeting.

   - `<recordingContentUrl>` value indicates URL to the recording content.

   - Recordings are in MP4 format.

   - The average size of the recording content itself is about 350 MB on disk, based on averages we're seeing for meetings that are in range of 30 mins – 60 mins.

   - Results aren't guaranteed to be sorted by `createdDateTime`. However, when multiple recordings are present for a single meeting, they share the same `meetingId` value. Additionally, the entries for the multiple recordings are correctly sequenced for the meeting in question.

   - Results are guaranteed to be present only after the associated meeting recordings are available. In other words, the caller requires no additional polling for availability.

   - Paginating through the results is supported as per current patterns in the Teams Export API. Pagination is supported via the presence of the `@oData.nextLink` property in the response. The nextLink property contains a `skipToken` value, as indicated below. If no `skipToken` is present, it means that there are no more results to retrieve in the current batch:

     |Request                               |Response      |@nextLink        |Comments                                      |
     |--------------------------------------|--------------|-----------------|----------------------------------------------|
     |`/getAllRecordings`                   |Count: 10     |`?skipToken=ABC` |Initial request without `skipToken`           |
     |`/getAllRecordings?skipToken=ABC`     |Count: 10     |`?skipToken=DEF` |`SkipToken` returned, request to get next page|
     |`/getAllRecordings?skipToken=DEF`     |Count: 7      |                 |No `skipToken`, no more data available        |

   - `$top` parameter is also supported as per current patterns in the Teams Export API.

   - `DeltaToken` to enable change tracking and syncing scenarios is supported. For an overview and examples of existing delta queries, see [Use delta query to track changes in Microsoft Graph data.](/graph/delta-query-overview)

   - The following API can be used to get the actual recording content of the selected `userId`, `meetingId` and `recordingId` that was obtained in the response of the GET `getAllRecordings` API. It returns the content of the recording:

   ```http
   GET users('{userId}')/onlineMeetings('{meetingId}')/recordings('{recordingId}')/content 
   ```
   
3. The following example is a JSON representation of the transcript resource:

   Namespace: microsoft.graph

   ```JSON
   {
     "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(callTranscript)",  
     "@odata.count": 2, 
     "@odata.nextLink": "https://graph.microsoft.com/v1.0/users('{userId}')/onlineMeetings/getAllTranscripts?$filter=MeetingOrganizer%2fUser%2fId+eq+%27{userId}%27&$skiptoken=MSMjMCMjTkNaYVNIQjVVbXRPYWxaV1dscGFWVGg1V2pOb1IxUXpRWGxrUm1oTFVrWmtTV1ZyYkhwUlZVWm9UMWR3VEdWWGRFTlJWVVpDVVZFOVBRPT0%3d",  
     "value":
       [ 
         { 
          "@odata.type": "#microsoft.graph.callTranscript", 
          "id": "MSMjMCMjMGFjNmUwZTgtYmZjYy00NDQxLTk2MGYtZjllNjVhNjI0NzBh", 
          "meetingId": "MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19aR1F3WTJZNE9XTXROekppWlMwME1XWTRMVGc0TWpBdE1ERXdOV1kzWlRsak9UTXlAdGhyZWFkLnYy", 
          "meetingOrganizerId": "{userId}", 
          "transcriptContentUrl": "https://graph.microsoft.com/v1.0/users/{userId}/onlineMeetings/MSoxMjczYTAxNi0yMDFkLTRmOTUtODA4My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19aR1F3WTJZNE9XTXROekppWlMwME1XWTRMVGc0TWpBdE1ERXdOV1kzWlRsak9UTXlAdGhyZWFkLnYy/transcripts/MSMjMCMjMGFjNmUwZTgtYmZjYy00NDQxLTk2MGYtZjllNjVhNjI0NzBh/content", 
         "createdDateTime": "2022-08-03T20:43:36.6248355Z" 
         }, 
         { 
          "@odata.type": "#microsoft.graph.callTranscript", 
          "id": "{transcriptId}", 
          "meetingId": "{meetingId}", 
          "meetingOrganizerId": "{userId}", 
          "transcriptContentUrl": "https://graph.microsoft.com/v1.0/users/{userId}/onlineMeetings/{meetingId}/transcripts/{transcriptId}/content",   
          },
        ] 
       }
     ```

   Where:

   - `<id>` represents a single recording.

   - `<meetingId>` represents a meeting or call identifier.

   - `<meetingOrganizer/user/id>` represents the organizer of the meeting.

   - `<createdDateTime>` indicates the start time of the meeting.

   - `<transcriptContentUrl>` value indicates URL to the transcript content.

   - Transcript content, by default, is in VTT format. But, using an Accept header value of `application/vnd.openxmlformats-officedocument.wordprocessingml.document`, DOCX format can also be obtained.

   - The average size of the transcript content itself in JSON/VTT format is about 300 KB, based on averages we're seeing for meetings that are in range of 30 mins – 60 mins.

   - Results aren't guaranteed to be sorted by `createdDateTime`. However, when multiple recordings are present for a single meeting, they share the same `meetingId` value. Additionally, the entries for the multiple recordings is correctly sequenced for the meeting in question.

   - Results are guaranteed to be present only after the associated meeting recordings are available. In other words, the caller requires no additional polling for availability.

   - Paginating through the results are supported as per current patterns in the Teams Export API. Pagination is supported via the presence of `@oData.nextLink` property in the response. The `nextLink` property contains a `skipToken` value, as indicated below. If no `skipToken` is present, it means that there are no more results to retrieve in the current batch:
   
     |Request                               |Response      |@nextLink        |Comments                                      |
     |--------------------------------------|--------------|-----------------|----------------------------------------------|
     |`/getAllTranscripts`                   |Count: 10     |`?skipToken=ABC` |Initial request without `skipToken`           |
     |`/getAllTranscripts?skipToken=ABC`     |Count: 10     |`?skipToken=DEF` |`SkipToken` returned, request to get next page|
     |`/getAllTranscripts?skipToken=DEF`     |Count: 7      |                 |No `skipToken`, no more data available        |

   - `$top` parameter is also supported as per current patterns in the Teams Export API. 

   - `DeltaToken` to enable change tracking and syncing scenarios is supported. For an overview and examples of existing delta queries, see [Use delta query to track changes in Microsoft Graph data](/graph/delta-query-overview).
   
   - The following API can be used to get the actual transcript content of the selected userId, meetingId and transcriptId that was obtained in the response of the GET getAllTranscripts API. It returns the content of the recording.

   ```http
   GET users('{userId}')/onlineMeetings('{meetingId}')/transcripts('{transcriptId}')/content
   ``` 

For more information, see [Use Graph APIs to fetch transcript](/microsoftteams/platform/graph-api/meeting-transcripts/api-transcripts#get-calltranscript-content).

## Export API filters

Export API hosted on the Teams Graph Service gets all user messages from the Substrate user mailbox using `users/{userId}/chats/getAllMessages`. Export API retrieves both sent and received messages for a user which leads to export of duplicate messages when calling the API for all users in the chat thread.

Export API has filter parameters that help optimize the messages returned for a chat thread. The [API GET](https://graph.microsoft.com/v1.0/users/{id}/chats/getAllMessages) supports new filter parameters that allow a way to extract messages based on the sent user, bot, application and system event messages. The filter parameter supports messages sent by the following:

- users (multiple user Ids supported in the same request).

 - applications (bots, connectors, and so on).

 - All [userIdentityTypes](/graph/api/resources/teamworkuseridentity) except emailUser and unknownFutureValue.
   
 - system event messages (control messages).
   
These parameters are part of the request’s `$filter`. If none of these parameters are present in the request, the messages from all the users present in the specified user chats is returned.

The filtering scenarios that are supported are as follows: 

```
$filter=from/application/applicationIdentityType eq '<appType>' (bots/tenantBots/connectors, etc.)  
  
$filter=from/user/id eq '<oid>' (any number of id filters)  
  
$filter=from/user/userIdentityType eq '<userIdentityType>'  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' (sent by app or userid)  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'anonymousGuest' (sent by app or anonymous)  

$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'federatedUser' (sent by app or federated)  
  
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by app, anonymous or federated)  
  
$filter=from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' (sent by any number of userid or anonymous)  
  
$filter=from/user/id eq '<oid>' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated)  

$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated or anonymous)
 
$filter=from/application/applicationIdentityType eq '<appType>' or from/user/id eq '<oid>' or from/user/userIdentityType eq 'anonymousGuest' or from/user/userIdentityType eq 'federatedUser' (sent by any number of userid or federated or anonymous) or messsageType eq 'systemEventMessage'

(<any of the previous filters>) and (lastModifiedDateTime+gt+<date>+and+lastModifiedDateTime+lt+<date>)  
```

- The query returns messages sent by the specified user if `from/user/id eq ‘{oid}’` is present.
   
 - The query returns messages sent by the federated users that are part of the user chats, if `from/user/userIdentityType eq ‘federatedUser’` is present.

 - the query returns messages sent by the specified application type if `from/application/applicationIdenitytyType eq '{appType}'` is present.
   
 - the query returns messages sent by the system if `messageType eq 'systemEventMessage'` is present.

These parameters can be combined between them using the OR operators as well as by combining with the `lastModifiedDateTime` `$filter` parameter.

## Teams Export APIs for Retained Messages
If [your tenant is setup with Teams Retention Policy](/purview/create-retention-policies?tabs=teams-retention), Export API supports capturing messages' from holds folder for [individual & group chat](/graph/api/chat-getallretainedmessages), and [posts, comments in Public & Shared channels](/graph/api/channel-getallretainedmessages).

## How to access Retained Messages API

- **Example 1** is a simple query to retrieve all the retained messages of a user:

 ```HTTP
  GET https://graph.microsoft.com/v1.0/users/8b081ef6-4792-4def-b2c9-c363a1bf41d5/chats/getAllRetainedMessages
  ```
- **Example 2** is a simple query to retrieve all the retained messages of a team:

 ```HTTP
  GET https://graph.microsoft.com/v1.0/teams/8b081ef6-4792-4def-b2c9-c363a1bf41d5/channels/getAllRetainedMessages
  ```

## What is supported by the getAllRetainedMessages API

- **Message is soft deleted by a user in a chat or a channel** If the user is on hold, then beyond the 21 days of deletion period, the message can be exported through the API.
- **Message is soft deleted by a user in a chat or a channel** If there's a valid retention policy set, then beyond the 21 days of deletion period, the message can be exported through the API.
- **Message is edited by a user in a chat or a channel** If there's a valid retention policy set, the previous edited versions of the message can be exported.

## Microsoft 365 Copilot Interactions & Microsoft 365 Chat (Preview)

The new Copilot Activity Export API allows you to export Copilot interactions data which includes the user prompt to Copilot and the Copilot response back to the user. This API captures the user intent and Copilot accessed resources and the response back to the user across Microsoft 365 Copilot apps such as Teams, Word and Outlook. 

## How to access Copilot Activity Export APIs (Preview)

- **Example 1** is a simple query to retrieve all the copilot interactions without any filters (beta):

  ```HTTP
  GET https://graph.microsoft.com/beta/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions 
  ```
- **Example 2** is a simple query to retrieve all the copilot interactions with appclass filters (beta):

  ```HTTP
  GET https://graph.microsoft.com/beta/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions?$filter=appClass eq 'IPM.SkypeTeams.Message.Copilot.Teams or appClass eq 'IPM.SkypeTeams.Message.Copilot.BizChat' (beta)
  ```
## Prerequisites to access Copilot Activity Export APIs (Preview)

Application permissions are used by apps that run without a signed-in user present; application permissions can only be approved by an administrator. The following permissions are needed:
- *AiEnterpriseInteraction.Read.All*: enables access to all copilot interactions across Microsoft 365 apps and Microsoft 365 Chat
- A **Microsoft 365 Copilot license** is required for accessing the new Copilot Activity Export API.