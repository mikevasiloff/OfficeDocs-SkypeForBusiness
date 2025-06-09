---
title: Create a Call queue in Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 2/5/2025
ms.topic: how-to
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - tier1
audience: Admin
appliesto:
  - Microsoft Teams
  - Skype for Business
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview
  - Phone System
description: Learn how to set up Call queues in Microsoft Teams. Call queues provide a greeting message, hold music, call redirecting, and other features.
---

# Create a Call queue in Microsoft Teams

Call queues route callers to people in your organization who can help with a particular issue or question. Calls are distributed one at a time to the people in the queue, who are known as *agents*.

Call queues provide:

- A greeting message.
- Music while people are waiting on hold in a queue.
- Call priority routing - in *First In, First Out* (FIFO) order - to agents.
- Handling options for queue overflow and timeout.

Before following the procedures in this article, make sure you read [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md) and complete the [getting started steps](plan-auto-attendant-call-queue.md#getting-started).

## What's new for Call queues in the past six months

- May 20
  - [Call priorities](aa-cq-call-priorities.md) for call queues allows you to prioritize one type of call over others, controlling which call type gets presented to agents first.
    
- December 11
  - [Nested Auto attendants and Call queues](./plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues) no longer require a resource account and associated licensing are now supported in the Teams admin center.

## Steps to create a Call queue

The steps to set up a Call queue includes:

1. Set up general information
1. Set the greeting and music
1. Set up call answering
1. Choose and assign agents
1. Set up callback
1. Set up call exception handling
1. Set up authorized users

The steps outlined in the article create Call queues using the Teams admin center. For instructions to create Call queues using PowerShell, see [Creating Call queues with PowerShell cmdlets](create-a-phone-system-call-queue-via-cmdlets.md).

## Follow these steps to set up your Call queue

## [Step 1: General info](#tab/general-info)

## Step 1: Set up general information

To set up a Call queue, in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851), expand **Voice**, select **Call queues**, and then select **Add**.

Type a name for the Call queue in the box at the top.

### Add an existing resource account

Before you can create and manage resource accounts, you must do the following actions:

- [Obtain Microsoft Teams Phone Resource Account licenses](manage-resource-accounts.md#obtain-microsoft-teams-phone-resource-account-licenses)
- [Obtain phone numbers](manage-resource-accounts.md#obtain-phone-numbers)
- [Assign permissions for managing a resource account](manage-resource-accounts.md#assign-permissions-for-managing-a-resource-account)

All Call queues that directly answer calls must have an associated resource account. All resource accounts must be assigned a [Microsoft Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md). If you wish, you can assign several resource accounts to a Call queue.

Nested Auto attendants and Call queues that receive calls from an auto attendant or call queue that already answered the call don't require a resource account. For more information, see [Nested Auto attendants and Call queues](./plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues).

For details on how to create resource accounts and ready them for use with auto attendants or call queues, see [Manage Teams resource accounts](manage-resource-accounts.md).

Agents see the resource account name or call queue name when they receive an incoming call.

### Assign a calling ID (optional)

Assign outbound caller ID numbers for the agents by specifying one or more resource accounts with a phone number. Agents can select which outbound caller ID number to use with each outbound call they make. Within the Calls App, agents can use their Call Queue (CQ) / Auto Attendant (AA) number or their own personal Direct InWard Dial (DID).

> [!NOTE]
> The resource account used for calling ID purposes must have a **Microsoft Teams Phone Resource Account** license and one of the following assigned:
>
> - A Calling Plan license and a phone number assigned
> - An Operator Connect phone number assigned
> - An online voice routing policy (phone number assignment is optional when using Direct Routing)

1. Under **Assign calling ID**, select the **Add** button.
1. On the **Add accounts** pane, search for one or more resource accounts you want to allow agents to use for outbound caller ID purposes.
1. Select the **Add** button next to the resource account with an assigned phone number.
1. Select the **Add** button at the bottom of the pane.

If you don't have a resource account with an assigned phone number, you must create a resource account. For more information, see [Create a Teams resource accounts](manage-resource-accounts.md#create-a-resource-account).

After you create this new resource account for calling ID, you still need to:

- Assign a [Microsoft Teams Phone Resource Account license](manage-resource-accounts.md#assign-a-license).
- Assign a Microsoft Calling Plan license, assign an Operator Connect phone number, or assign an online voice routing policy for Direct Routing.
- Assign the [phone number to the resource account](manage-resource-accounts.md#assign-a-phone-number), if you're using Microsoft Calling Plan.

### Set the Service level threshold

Service level measures the efficiency and responsiveness to incoming customer requests within a specific Service level threshold.

You can set the threshold target to any value from 0 to 40 minutes (2,400 seconds). The value should be less than the value set for [Call timeout](#call-timeout-set-how-to-handle-call-timeouts), however, this value difference isn't enforced. Setting the threshold value higher than the call timeout results in the service level always being 100% if there are answered calls or 0% if there are no answered calls. Setting the value to blank (empty) disables the service level metric calculation for the call queue.

>[!NOTE]
> Service level metrics aren't currently available in historical reporting.
>
> Changing the service level threshold during business hours causes inaccurate service level calculations for the whole day because previous calls won't be reassessed with the new target.

### Set the Call queue language

Choose a [supported language](create-a-phone-system-call-queue-languages.md).

This language is used for system-generated voice prompts and voicemail transcription, if you enable them.

After you select a language, select the **Next** button at the bottom of the **Add a Call queue** page.

### General via PowerShell

<!-- markdownlint-disable MD020 -->
<details>
<summary>Expand to see PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-Name](/powershell/module/teams/new-cscallqueue#-Name) | [-Name](/powershell/module/teams/set-cscallqueue#-Name) |
| [-OboResourceAccountIds](/powershell/module/teams/new-cscallqueue#-OboResourceAccountIds) | [-OboResourceAccountIds](/powershell/module/teams/set-cscallqueue#-OboResourceAccountIds) |
| [-ServiceLevelThresholdResponseTimeInSecond](/powershell/module/teams/new-cscallqueue#-ServiceLevelThresholdResponseTimeInSecond) | [-ServiceLevelThresholdResponseTimeInSecond](/powershell/module/teams/set-cscallqueue#-ServiceLevelThresholdResponseTimeInSecond) |
| [-LanguageId](/powershell/module/teams/new-cscallqueue#-LanguageId) | [-LanguageId](/powershell/module/teams/set-cscallqueue#-LanguageId) |

#### PowerShell Examples

##### Example 1

In the following example, this script assigns a calling line ID and sets a 45-second service level threshold:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -OboResourceAccountIds @("Resource Account 01 GUID", "Resource Account 02 GUID") -ServiceLevelThresholdResponseTimeInSecond 45 -LanguageID en-US -U
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

##### Example 2

In the following example, this script modifies an existing call queue and uses the Set-CsCallQueue cmdlet:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -OboResourceAccountIds @("Resource Account GUID 01", "Resource Account GUID 02") -ServiceLevelThresholdResponseTimeInSecond 45 -LanguageID en-US
````

</details>
<!-- markdownlint-enable MD020 -->

## [Step 2: Greeting and music](#tab/greeting-music)

## Step 2: Add a greeting and on-hold music

Specify if you want to play a *greeting* to callers when they arrive in the queue.

- If you select **Play an audio file**, you must upload an MP3, WAV, or WMA file containing the greeting that you want to play. See [Supported audio file formats](plan-auto-attendant-call-queue.md#supported-audio-file-formats).
- If you select **Type a greeting message**, the system reads the text that you type (up to 1,000 characters) when the Call queue answers a call.

>[!NOTE]
> *Text to Speech* text must be entered in your selected language as the system doesn't perform translation.
>
> All words are pronounced in the selected language.

Teams provides default music to callers while they're *on hold in a queue*.

- The default music supplied in Teams Call queues is free of any royalties payable by your organization.
- If you want to play a specific audio file, choose **Play an audio file** and upload an MP3, WAV, or WMA file. See [Supported audio file formats](plan-auto-attendant-call-queue.md#supported-audio-file-formats).

> [!IMPORTANT]
> You're responsible for independently clearing and securing all necessary rights and permissions to use any music or audio file with your Microsoft Teams service, which might include intellectual property and other rights in any music, sound effects, audio, brands, names, and other content in the audio file from all relevant rights holders, which might include artists, actors, performers, musicians, songwriters, composers, record labels, music publishers, unions, guilds, rights societies, collective management organizations, and any other parties who own, control, or license the music copyrights, sound effects, audio, and other intellectual property rights.

After you select a greeting and on-hold music, select the **Next** button at the bottom of the **Add a Call queue** page.

### Greeting and on-hold music via PowerShell

<!-- markdownlint-disable MD025 -->
<details>
<summary>Expand to see greeting and on-hold music PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-WelcomeMusicAudioFileId](/powershell/module/teams/new-cscallqueue#-WelcomeMusicAudioFileId) | [-WelcomeMusicAudioFileId](/powershell/module/teams/set-cscallqueue#-WelcomeMusicAudioFileId) |
| [-WelcomeTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-WelcomeTextToSpeechPrompt) | [-WelcomeTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-WelcomeTextToSpeechPrompt) |
| [-UseDefaultMusicOnHold](/powershell/module/teams/new-cscallqueue#-UseDefaultMusicOnHold) | [-UseDefaultMusicOnHold](/powershell/module/teams/set-cscallqueue#-UseDefaultMusicOnHold) |
| [-MusicOnHoldAudioFileId](/powershell/module/teams/new-cscallqueue#-UseDefaultMusicOnHold) | [-MusicOnHoldAudioFileId](/powershell/module/teams/set-cscallqueue#-UseDefaultMusicOnHold) |

#### PowerShell Examples

##### Example 1

In the following example, this script uses a text to speech greeting and uses the default music on hold file:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -WelcomeTextToSpeechPrompt "Welcome to the call queue " -UseDefaultMusicOnHold $true
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -WelcomeTextToSpeechPrompt "Welcome to the call queue " -UseDefaultMusicOnHold $true
````

##### Example 2

In the following example, this script uses an audio file greeting and uses an audio file for music on hold:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -WelcomeMusicAudioFileId <FILE ID> -MusicOnHoldAudioFileId <FILE ID>
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -WelcomeMusicAudioFileId <FILE ID> -MusicOnHoldAudioFileId <FILE ID>
````
See [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile) to get the `<FILE ID>` information.

</details>
<!-- markdownlint-enable MD025 -->

## [Step 3: Call answering](#tab/call-answering)

## Step 3: Set up who answers incoming calls

Review the [prerequisites for adding agents to a Call queue](plan-auto-attendant-call-queue.md#prerequisites).

### Teams channel

You can add up to 200 agents via a Teams channel. You must be a member of the team or the creator or owner of the channel to add a channel to the queue.

[Using a Teams channel to manage the queue](https://support.microsoft.com/office/9f07dabe-91c6-4a9b-a545-8ffdddd2504e):

1. Select the **Choose a team** radio button and select **Add a channel**.
1. Search for the team that you want to use, select it, and select **Add**.
1. Select the channel that you want to use (only standard channels are fully supported) and select **Apply**.

The following clients are supported when using a Teams channel for Call queues:

- Microsoft Teams Windows client
- Microsoft Teams Mac client

> [!NOTE]
> If you use this option, it can take up to 24 hours for the Call queue to be fully operational.
>
> If there are more than 200 members in the team, only the first 200 members, in alphabetical order, are added as agents to the Call queue.

### Users and groups

You can add up to 20 agents individually and up to 200 agents via groups.

If you want to add individual users or groups to the queue:

1. Select the **Choose users and groups** radio button.

To **add a user** to the queue:

1. Select **Add users**, search for the user, select **Add**, and then select **Add**.

To **add a group** to the queue:

1. Select **Add groups**, search for the group, select **Add**, and then select **Add**.
    - You can use distribution lists, security groups, and Microsoft 365 Groups or Microsoft Teams teams.

> [!NOTE]
> New users added to a group can take up to eight hours for their first call to arrive.
>
> If there are more than 200 members in the group, only the first 200 members, in alphabetical order, are added as agents to the Call queue.

> [!IMPORTANT]
> Only standard channels are fully supported.
>
> Known issues:
> 1. Assigning private channels to Call queues
>     - When using a private channel, calls are distributed to all members of the team even if the private channel only has a subset of team members.
>     - Assigning a private channel to a call queue might fail, even if the call queue previously had a private channel assigned or if the private channel was previously assigned to a Call queue.
>
> 2. Only the global administrator role can fully manage a call queue with a Teams channel assigned.

### Conference mode

**Conference mode** reduces the amount of time it takes for a caller to be connected to an agent after the agent accepts the call. 
  
Agents' Teams accounts must be set to TeamsOnly mode. Agents who don't meet the requirements aren't included in the call routing list.

> [!TIP]
> Setting **Conference mode** to **On** is the recommended setting.

Once you select your call answering options, select the **Next** button at the bottom of the **Add a Call queue** page.

Keep the following conditions in mind:

- Conference mode isn't supported for calls routed to the queue from a Direct Routing gateway enabled for Location Based Routing.
- Conference mode is required if Teams users need to consult/transfer calls with Call queues.
- Agents can hear the configured music on hold in queue for up to two seconds when first joining the call.

> [!IMPORTANT]
> Transfer mode (when conference mode is disabled) is now in legacy mode. A Message Center post will be made at least 3 months before the scheduled removal date.

### Call answering via PowerShell

<!-- markdownlint-disable MD030 -->
<details>
<summary>Expand to see call answering PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-User](/powershell/module/teams/new-cscallqueue#-User) | [-User](/powershell/module/teams/set-cscallqueue#-User) |
| [-DistributionLists](/powershell/module/teams/new-cscallqueue#-DistributionLists) | [-DistributionLists](/powershell/module/teams/set-cscallqueue#-DistributionLists) |
| [-ChannelId](/powershell/module/teams/new-cscallqueue#-ChannelId) | [-ChannelId](/powershell/module/teams/set-cscallqueue#-ChannelId) |
| [-ChannelUserObjectId](/powershell/module/teams/new-cscallqueue#-ChannelUserObjectId) | [-ChannelUserObjectId](/powershell/module/teams/set-cscallqueue#-ChannelUserObjectId) |
| [-UseDefaultMusicOnHold](/powershell/module/teams/new-cscallqueue#-UseDefaultMusicOnHold) | [-UseDefaultMusicOnHold](/powershell/module/teams/set-cscallqueue#-UseDefaultMusicOnHold) |
| [-MusicOnHoldAudioFileId](/powershell/module/teams/new-cscallqueue#-MusicOnHoldAudioFileId) | [-MusicOnHoldAudioFileId](/powershell/module/teams/set-cscallqueue#-MusicOnHoldAudioFileId) |
| [-ConferenceMode](/powershell/module/teams/new-cscallqueue#-ConferenceMode) | [-ConferenceMode](/powershell/module/teams/set-cscallqueue#-ConferenceMode) |

#### PowerShell Examples

##### Example 1

To assign individual users to a call queue, use the default music on hold, and disable conference mode, see the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -User @("User 01 GUID", "User 02 GUID") -UseDefaultMusicOnHold $true -ConferenceMode $false
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -User @("User 01 GUID", "User 02 GUID") -UseDefaultMusicOnHold $true -ConferenceMode $false
````

##### Example 2

To assign distribution lists to a call queue, use an audio file for music on hold, and enable conference mode, see the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -DistributionLists @("Distribution List 01 GUID", "Distribution List 02 GUID") -UseDefaultMusicOnHold $false -MusicOnHoldAudioFileId <FILE ID> -ConferenceMode $true
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -DistributionLists @("Distribution List 01 GUID", "Distribution List 02 GUID") -UseDefaultMusicOnHold $false -MusicOnHoldAudioFileId <FILE ID> -ConferenceMode $true
````
See [Import-CsOnlineAudioFile](/powershell/module/teams/import-csonlineaudiofile) to get the `<FILE ID>` information.

##### Example 3

To assign a Teams channel to a call queue, use the default music on hold, and enable conference mode, see the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -ChannelId <Channel GUID> -ChannelUserObjectId <Team Owner GUID> -UseDefaultMusicOnHold $true -ConferenceMode $true
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -ChannelId <Channel GUID> -ChannelUserObjectId <Team Owner GUID> -UseDefaultMusicOnHold $true -ConferenceMode $true
````

</details>
<!-- markdownlint-enable MD030 -->

## [Step 4: Agent selection](#tab/agent-selection)

## Step 4: Select your agent routing options

> [!IMPORTANT]
> Call presentation to agents might conflict with Location-Based Routing restrictions. In this case, the agent receives a call toast but can't answer the call. This continues until an agent answers, the caller hangs up, or the call queue times out. For more information on Location-Based Routing, see [Plan Location-Based Routing for Direct Routing](./location-based-routing-plan.md).  

**Routing method** determines the order in which agents receive calls from the queue.

Choose from these options:

- **Attendant routing** rings all agents in the queue at the same time. The first call agent to pick up the call gets the call.

- **Serial routing** rings all call agents one by one in the order specified in the **Call agents** list. If an agent dismisses or doesn't pick up a call, the call rings the next agent. This cycle repeats until the call is answered, times out, or the caller hangs up.

- **Round robin** balances the routing of incoming calls so that each call agent gets the same number of calls from the queue.

- **Longest idle** routes calls to the agent who is idle the longest. An agent is considered idle if their presence state is *Available*. Agents who aren't available don't receive calls until they change their presence to *Available*.

> [!TIP]
> Setting the **Routing Method** to **Round robin** or **Longest idle** is the recommended setting.

### Presence-based call routing

**Presence-based call routing** uses the availability status of call agents to determine whether an agent should be included in the call routing list for the selected routing method.

Call agents whose availability status is set to **Available** are included in the call routing list and can receive calls. Agents whose availability status is set to any other status are excluded from the call routing list and can't receive calls until their availability status changes back to **Available**.

You can enable **presence-based call routing** with any of the routing methods.

If an agent opts out of getting calls, they can't receive calls regardless of their availability status.

> [!TIP]
> Setting the **Presence-based routing** to **On** is the recommended setting.

> [!NOTE]
> When **Longest idle** is selected as the routing method:
> - Presence-based routing is required and automatically enabled even though the Presence-based routing toggle is **Off** and grayed out.
> - When there are fewer calls in the queue than available agents, only the first two longest idle agents are presented with calls from the queue.
>
> If **Presence-based routing** isn't enabled and there are multiple calls in the queue, the system presents these calls simultaneously to the agents, regardless of their presence status. This action results in multiple call notifications to agents, particularly if some agents don't answer the initial call presented to them. For more information, see [Configure Busy Options](./inbound-call-routing.md) for Busy on Busy alternatives to presence-based routing.
>
> There might be times when an agent receives a call from the queue shortly after becoming unavailable or a short delay in receiving a call from the queue after becoming available when using **Presence-based routing**.
>
> Agents who use the Skype for Business client aren't included in the call routing list when presence-based routing is enabled. If you have agents who use Skype for Business, don't enable presence-based call routing.

### Call agents can opt out of taking calls

You can specify whether call agents have the ability to opt out of taking calls or not.

We recommend turning on **Call agents can opt out of taking calls**.

### Agent alert time

**Agent alert time** specifies how long an agent's phone rings before the queue redirects the call to the next agent.

> [!TIP]
> Setting the **Agent alert time** to a minimum **20 seconds** is the recommended setting.

Once you select your agent call routing options, select the **Next** button at the bottom of the **Add a Call queue** page.

### Agent selection via PowerShell

<!-- markdownlint-disable MD035 -->
<details>
<summary>Expand to see agent selection PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-RoutingMethod](/powershell/module/teams/new-cscallqueue#-RoutingMethod) | [-RoutingMethod](/powershell/module/teams/set-cscallqueue#-RoutingMethod) |
| [-PresenceBasedRouting](/powershell/module/teams/new-cscallqueue#-PresenceBasedRouting) | [-PresenceBasedRouting](/powershell/module/teams/set-cscallqueue#-PresenceBasedRouting) |
| [-AllowOptOut](/powershell/module/teams/new-cscallqueue#-AllowOptOut) | [-AllowOptOut](/powershell/module/teams/set-cscallqueue#-AllowOptOut) |
| [-AgentAlertTime](/powershell/module/teams/new-cscallqueue#-AgentAlertTime) | [-AgentAlertTime](/powershell/module/teams/set-cscallqueue#-AgentAlertTime) |

#### PowerShell Examples

##### Example 1

To use Attendant Routing, disable Presence Based Routing, don't allow agents to opt-out, and set the agent alert time to 20 seconds, see the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -RoutingMethod Attendant -PresenceBasedRouting $false -AllowOptOut $false -AgentAlertTime 20
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -RoutingMethod Attendant -PresenceBasedRouting $false -AllowOptOut $false -AgentAlertTime 20
````

##### Example 2

To use Round Robin, enable Presence Based Routing, allow agents to opt-out, and set the agent alert time to 60 seconds, use the New-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -RoutingMethod RoundRobin -PresenceBasedRouting $true -AllowOptOut $true -AgentAlertTime 60
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID>  -RoutingMethod RoundRobin -PresenceBasedRouting $true -AllowOptOut $true -AgentAlertTime 60
````

</details>
<!-- markdownlint-enable MD035 -->


## [Step 5: Callback](#tab/callback)

## Step 5: Callback

**Callback** allows *eligible* callers waiting in a call queue to receive a callback to the number they're calling from when an agent becomes available.

A caller becomes eligible for callback based on any one of the following configured conditions coming true:

- **Wait time in queue**: Once a caller in queue exceeds this configured wait time, they become eligible for callback. This option applies to callers at the front of the queue.

- **Number of calls in queue**: Once the number of callers in queue reaches this level, new callers arriving in the queue become eligible for callback. This option applies to callers arriving in the queue. Callers that arrived in the queue before this limit was reached aren't eligible for callback.

- **Calls to agent ratio**: Once the number of callers waiting in queue exceeds the ratio, new callers arriving in the queue become eligible for callback. This option applies to callers arriving in the queue.

Additionally, for a call to become eligible for callback, its inbound phone number must be a publicly dialable, non-premium phone number in E.164 format, and it must not be presenting to an agent.

After the music on hold finishes playing, eligible callers receive an option to request callback.

As an admin, you can also set the messaging a caller hears, the key they need to press, and an email address to be notified at if the callback fails.

#### Callback and Call queue timeouts

In order for an *eligible* call to be offered callback, the [Call timeout](#call-timeout-set-how-to-handle-call-timeouts) value must be set high enough to allow the call to become eligible for callback and for the music to finish playing after the call becomes eligible.

Consider the following call queue configuration:

- Call back wait time in queue: 60 seconds
- Call Queue Timeout: 120 seconds
- Call Queue Music: Default

After a caller waits in the queue for 60 seconds, they become eligible for callback. However, since the default music is two minutes long, the call queue timeout occurs first, and callback isn't offered.

Once a caller successfully requests a callback, the callback request is also subject to the call queue timeout configuration. If a callback request times out, the information about the caller is sent to the configured email notification address.

For a callback to work, the call queue timeout must be long enough for the call to become eligible, the music to stop, the caller to request a callback, and the callback to wait until an agent is available.

> [!NOTE]
> For callers in North America, in addition to the other listed requirements, the inbound phone number must not start with:
>
> |Starting Digits                                   |
> |:-------------------------------------------------|
> | 1-242, 246, 264, 268, 284                        |
> | 1-340, 345                                       |
> | 1-441, 473                                       |
> | 1-500                                            |
> | 1-600, 649, 658, 664, 670, 671, 684              |
> | 1-700, 721, 758, 767, 784, 787                   |
> | 1-800, 811, 822, 833, 844, 855, 866, 877, 888    |
> | 1-809, 829, 849, 868, 869, 876                   | 
> | 1-900, 939                                       |
> | 1-nnn-555-1212                                   |
> | 1-nnn-555,0100-0199                              |

Once you select your callback options, select the **Next** button at the bottom of the **Add a Call queue** page.

### Callback via PowerShell

<!-- markdownlint-disable MD040 -->
<details>
<summary>Expand to see callback PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-IsCallbackEnabled](/powershell/module/teams/new-cscallqueue#-IsCallbackEnabled) | [-IsCallbackEnabled](/powershell/module/teams/set-cscallqueue#-IsCallbackEnabled) |
| [-CallbackRequestDtmf](/powershell/module/teams/new-cscallqueue#-CallbackRequestDtmf) | [-CallbackRequestDtmf](/powershell/module/teams/set-cscallqueue#-CallbackRequestDtmf) |
| [-WaitTimeBeforeOfferingCallbackInSecond](/powershell/module/teams/new-cscallqueue#-WaitTimeBeforeOfferingCallbackInSecond) | [-WaitTimeBeforeOfferingCallbackInSecond](/powershell/module/teams/set-cscallqueue#-WaitTimeBeforeOfferingCallbackInSecond) |
| [-NumberOfCallsInQueueBeforeOfferingCallback](/powershell/module/teams/new-cscallqueue#-NumberOfCallsInQueueBeforeOfferingCallback) | [-NumberOfCallsInQueueBeforeOfferingCallback](/powershell/module/teams/set-cscallqueue#-NumberOfCallsInQueueBeforeOfferingCallback) |
| [-CallToAgentRatioThresholdBeforeOfferingCallback](/powershell/module/teams/new-cscallqueue#-CallToAgentRatioThresholdBeforeOfferingCallback) | [-CallToAgentRatioThresholdBeforeOfferingCallback](/powershell/module/teams/set-cscallqueue#-CallToAgentRatioThresholdBeforeOfferingCallback) |
| [-CallbackOfferAudioFilePromptResourceId](/powershell/module/teams/new-cscallqueue#-CallbackOfferAudioFilePromptResourceId) | [-CallbackOfferAudioFilePromptResourceId](/powershell/module/teams/set-cscallqueue#-CallbackOfferAudioFilePromptResourceId) |
| [-CallbackOfferTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-CallbackOfferTextToSpeechPrompt) | [-CallbackOfferTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-CallbackOfferTextToSpeechPrompt) |
| [-CallbackEmailNotificationTarget](/powershell/module/teams/new-cscallqueue#-CallbackEmailNotificationTarget) | [-CallbackEmailNotificationTarget](/powershell/module/teams/set-cscallqueue#-CallbackEmailNotificationTarget) |

#### Callback PowerShell Examples

##### Example 1

To make calls become eligible after waiting 60 seconds, see the following example:

````PowerShell
New-CsCallQueue -Name "Callback Eligible After 60 seconds" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Example 2

To make calls become eligible for callback when there are more than 50 calls in queue, see the following example:

````PowerShell
New-CsCallQueue -Name "Callback Eligible After 50 calls" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 "Tone1" -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Example 3

To make calls become eligible for callback when there are two times more calls than agents, see the following example:

````PowerShell
New-CsCallQueue -Name "Callback Eligible After 2x calls to agents" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -CallToAgentRatioThresholdBeforeOfferingCallback 2 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf
 "Tone1" -CallToAgentRatioThresholdBeforeOfferingCallback 2 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

##### Example 4

To make calls become eligible for callback after waiting 60 seconds or when there are more than 50 calls in queue, see the following example:

````PowerShell
New-CsCallQueue -Name "Callback Eligible After 60s or 50 calls" -UseDefaultMusicOnHold $true -LanguageID en-US -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <Call Queue GUID> -IsCallbackEnabled $true -CallbackRequestDtmf "Tone1" -WaitTimeBeforeOfferingCallbackInSecond 60 -NumberOfCallsInQueueBeforeOfferingCallback 50 -CallbackOfferTextToSpeechPrompt "If you would like to have a callback when an agent becomes available, press 1" -CallbackEmailNotificationTarget <Team or DL GUID>
````

</details>
<!-- markdownlint-enable MD040 -->

## [Step 6: Exception Handling](#tab/call-exception-handling)

## Step 6: Exception handling

**Exception handling** determines how calls are handled when certain exceptions occur.

Each exception allows you to **disconnect** the call or **redirect** it to any of the call routing destinations.

For example, when **Overflow** occurs, you might send calls to a backup Call queue, but when **Timeout** or **No Agents** occurs, you might want the callers to leave a shared voicemail.

> [!NOTE]
> For external transfers, see [Prerequisites](./plan-auto-attendant-call-queue.md#prerequisites) and the [external phone number transfers - technical details](./create-a-phone-system-auto-attendant.md?tabs=general-info#external-phone-number-transfers---technical-details) for number formatting.

### Overflow: Set how to handle call overflow

**Maximum calls in the queue** specifies the maximum number of calls that can wait in the queue at any given time.

The default is 50, but it can range from 0 to 200.

When this limit is reached, the call is handled as specified by the **When the maximum number of calls is reached** setting.

This limit applies only to calls that are waiting in queue to be answered.

> [!NOTE]
> If the maximum number of calls is set to 0, the greeting message can't play.

### Call timeout: Set how to handle call timeouts

**Call Timeout: maximum wait time** specifies the maximum time a call can be on hold in the queue before it's redirected or disconnected.

You can specify a value from 0 seconds to 45 minutes.

### No Agents Opted/Logged In: Set how to handle calls when no agents are opted/logged into the queue

This call exception handling option handles calls when no agents are opted into the queue or all agents are logged out of the queue.

**Apply to All or New Calls** controls whether or not the no agents call treatment applies to:

- ***All Calls*** (default) - calls already in queue and new calls arriving to the queue, or
- ***New Calls Only*** - only new calls that arrive once the No Agents condition occurs, existing calls in queue remain in queue

> [!NOTE]
> The **No Agents** handling exception occurs under the following conditions:
>
> - Presence based routing off: No agents are opted into the queue.
> - Presence based routing on: No agents logged in, or all agents are in *Appear Offline*.
>
> If agents are logged in or opted in, then calls are queued.

>[!IMPORTANT]
> Known Issues:
> 1. When **Longest idle** is selected as the routing method, the **No Agents** treatment doesn't work when ***New Calls Only*** is selected and new calls are queued. The ***All Calls*** option works as expected. Support is investigating.
> 1. Don't include any special characters in the greeting message when redirecting to **Voicemail (shared)** as these aren't spoken by the system.

### Nested Auto attendants and Call queues

**Nested Auto attendants and Call queues**, or auto attendants and call queues that don't directly answer phone calls, no longer require a Resource Account and associated licensing.

Existing configurations that use Resource Accounts continue to function and remain fully supported. A combination of both methods can be used at the same time.

When call queue [Exception handling](#step-6-exception-handling-1) occurs, the `Voice app` destination for Overflow, Timeout, and No Agents can refer to an auto attendant or call queue directly instead of the Resource Account for that auto attendant or call queue.

For more information, see [Nested Auto attendant and Call Queue](./plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues)

Once you select your call overflow, call timeout, and no agents handling options, select the **Next** button at the bottom of the **Add a Call queue** page.

### Exception handling via PowerShell
<!-- markdownlint-disable MD045 -->
<details>
<summary>Expand to see exception handling PowerShell options and examples</summary>

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-OverflowAction](/powershell/module/teams/New-CSCallQueue#-OverflowAction) | [-OverflowAction](/powershell/module/teams/Set-CSCallQueue#-OverflowAction) |
| [-OverflowActionTarget](/powershell/module/teams/New-CSCallQueue#-OverflowActionTarget) | [-OverflowActionTarget](/powershell/module/teams/Set-CSCallQueue#-OverflowActionTarget) |
| [-TimeoutAction](/powershell/module/teams/New-CSCallQueue#-TimeoutAction) | [-TimeoutAction](/powershell/module/teams/Set-CSCallQueue#-TimeoutAction) |
| [-TimeOutActionTarget](/powershell/module/teams/new-cscallqueue#-timeoutactiontarget) | [-TimeOutActionTarget](/powershell/module/teams/set-cscallqueue#-timeoutactiontarget) |
| [-NoAgentAction](/powershell/module/teams/New-CSCallQueue#-NoAgentAction) | [-OverflowAction](/powershell/module/teams/Set-CSCallQueue#-NoAgentAction) |
| [-NoAgentActionTarget](/powershell/module/teams/new-cscallqueue#-noagentactiontarget) | [-NoAgentActionTarget](/powershell/module/teams/set-cscallqueue#-noagentactiontarget) |

#### PowerShell Examples

##### Example 1

While creating a new call queue, configure the Overflow to an Auto attendant or Call queue directly, as shown in the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -OverflowAction Forward -OverflowActionTarget <Auto Attendant or Call Queue GUID>
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <CallQueue GUID> -OverflowAction Forward -OverflowActionTarget <Auto Attendant or Call Queue GUID>
````

##### Example 2

While creating a new call queue, configure Timeout to an Auto attendant or Call queue via a Resource account, as shown in the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -TimeoutAction Forward -OverflowActionTarget <Resource Account GUID>
````
*Note: This example doesn't contain the minimum number of parameters required to create a new call queue.*

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <CallQueue GUID> -TimeoutAction Forward -TimeoutActionTarget <Resource Account GUID>
````

##### Example 3

While creating a new call queue, set No agents logged in to an external phone number, as shown in the following example:

````PowerShell
New-CsCallQueue -Name "Call Queue Name" -NoAgentAction Forward -NoAgentActionTarget tel:+<phone number>
````

To modify an existing call queue, use the Set-CsCallQueue cmdlet, as shown in the following example:

````PowerShell
Set-CsCallQueue -Identity <CallQueue GUID> -NoAgentAction Forward -NoAgentActionTarget tel:+<phone number>
````

</details>
<!-- markdownlint-enable MD045 -->

### Additional messaging

The Overflow, Call timeout, and No Agents exception redirect options for **Person in organization** and **Voicemail personal** support additional prompting just like the other redirect options. 

#### Additional messaging via PowerShell
<!-- markdownlint-disable MD050 -->
<details>
<summary>Expand to see PowerShell options</summary>

> [!CAUTION]
> These configuration options are currently only available through PowerShell cmdlets and they don't appear in Teams admin center. If these options are configured through PowerShell, any changes to the Call queue through Teams admin center erases these settings.

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-OverflowRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectPersonTextToSpeechPrompt)        | [-OverflowRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectPersonTextToSpeechPrompt)        |
| [-OverflowRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectPersonAudioFilePrompt)              | [-OverflowRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectPersonAudioFilePrompt)              |
| [-OverflowRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectVoicemailTextToSpeechPrompt)  | [-OverflowRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectVoicemailTextToSpeechPrompt)  |
| [-OverflowRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-OverflowRedirectVoicemailAudioFilePrompt)        | [-OverflowRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-OverflowRedirectVoicemailAudioFilePrompt)        |
| [-TimeoutRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectPersonTextToSpeechPrompt)          | [-TimeoutRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectPersonTextToSpeechPrompt)          |
| [-TimeoutRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectPersonAudioFilePrompt)                | [-TimeoutRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectPersonAudioFilePrompt)                |
| [-TimeoutRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectVoicemailTextToSpeechPrompt)    | [-TimeoutRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectVoicemailTextToSpeechPrompt)    |
| [-TimeoutRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-TimeoutRedirectVoicemailAudioFilePrompt)          | [-TimeoutRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-TimeoutRedirectVoicemailAudioFilePrompt)          |
| [-NoAgentRedirectPersonTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectPersonTextToSpeechPrompt)          | [-NoAgentRedirectPersonTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectPersonTextToSpeechPrompt)          |
| [-NotAgentRedirectPersonAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectPersonAudioFilePrompt)               | [-NotAgentRedirectPersonAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectPersonAudioFilePrompt)               |
| [-NoAgentRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectVoicemailTextToSpeechPrompt)    | [-NoAgentRedirectVoicemailTextToSpeechPrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectVoicemailTextToSpeechPrompt)    |
| [-NoAgentRedirectVoicemailAudioFilePrompt](/powershell/module/teams/new-cscallqueue#-NoAgentRedirectVoicemailAudioFilePrompt)          | [-NoAgentRedirectVoicemailAudioFilePrompt](/powershell/module/teams/set-cscallqueue#-NoAgentRedirectVoicemailAudioFilePrompt)          |

</details>
<!-- markdownlint-enable MD050 -->

## [Step 7: Authorized users](#tab/authorized-users)

## Step 7: Authorized users

**Authorized users** specifies the users who are authorized to make changes to this Call queue. You can determine the capabilities that the users have through [Teams voice applications policies](./manage-voice-applications-policies.md) assigned to your users.

To **add a user** to the authorized users:

1. Select **Add**, search for the user, select **Add**, and then select **Add**.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one Auto attendant or Call queue.
>
> A user can't make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one Auto attendant or Call queue.
> - The user is assigned as an authorized user to at least one Auto attendant or Call queue but doesn't have a policy assigned.

> [!NOTE]
> A maximum of 15 authorized users can be assigned to the Call queue.

For more information, see [Set up authorized users](./aa-cq-authorized-users.md).

Once you select your authorized users, select the **Submit** button at the bottom of the **Add a Call queue** page.

### Authorized users via PowerShell
<!-- markdownlint-disable MD055 -->
<details>
<summary>Expand to see authorized user PowerShell examples</summary>

#### PowerShell Examples

##### Example 1

To add an authorized user to an existing call queue, see the following example:

````PowerShell
Set-CsCallQueue -Identity <CallQueue GUID> -AuthorizedUsers @("User 01 GUID", "User 02 GUID")
````

> [!CAUTION]
> These configuration options are currently only available through PowerShell cmdlets and they don't appear in Teams admin center. If these options are configured through PowerShell, any changes to the Call queue through Teams admin center erases these settings.

### Hiding authorized users

Hidden authorized users aren't visible to Queues app users.

|New-CsCallQueue (For new call queues)   |Set-CsCallQueue (For existing call queues) |
|:---------------------------------------|:------------------------------------------|
| [-HideAuthorizedUsers](/powershell/module/teams/new-cscallqueue#-hideauthorizedusers) | [-HideAuthorizedUsers](/powershell/module/teams/set-cscallqueue#-hideauthorizedusers) |

##### Example 1

To hide an authorized user in a call queue, see the following example:

````PowerShell
Set-CsCallQueue -Identity <CallQueue GUID> -AuthorizedUsers @("User 01 GUID", "User 02 GUID") -HideAuthorizedUsers @("User 02 GUID")
````

</details>
<!-- markdownlint-enable MD055 -->

---

## Summary of recommended Call queue settings

The following settings are recommended:

- **Conference mode** to **On**
- **Routing method** to **Round robin** or **Longest idle**
- **Presence-based routing** to **On**
- **Agent alert time:** to a minimum of **20 seconds**

## Resources for complex scenarios

### Call queue feature compatibility

| Feature | Teams Desktop<sup>1</sup> | Teams Web | Teams Mobile App<sup>2</sup> | Teams Phone Mobile<sup>3</sup> | Skype for Business | IP Phones | Standard Call Queues | Channel Based Call Queues | Comment |
|:-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-|
| **Agent Routing Methods** |  |  |  |  |  |  |  |  |  |
| Attendant Routing | Y | Y | Y | Y | Y | Y | Y | Y | *Default* |
| Longest Idle<sup>4</sup> | Y | Y | Y | Y | N | Y | Y | Y | *Recommended* |
| Round Robin | Y | Y | Y | Y | Y | Y | Y | Y | *Recommended* |
| Serial | Y | Y | Y | Y | Y | Y | Y<sup>5</sup> | Y<sup>5</sup> |  |
| **Agent Routing Options** |  |  |  |  |  |  |  |  |  |
| Presence Based Routing<sup>4</sup> | Y | Y | Y | Y<sup>11</sup> | N | Y | Y | Y | *Default* |
| Agents can opt out | Y | Y | Y | Y<sup>11</sup> | Y<sup>8</sup> | Y<sup>8</sup> | Y | Y | *Default* |
| **Transfer Modes** |  |  |  |  |  |  |  |  |  |
| Conference Mode<sup>6</sup> | Y | Y | Y | Y | Y | Y | Y | Y | *Default* |
| Transfer Mode | Y | Y | Y | Y | Y | Y | Y | Y |  |
| **Collaborative Calling** |  |  |  |  |  |  |  |  |  |
| Channel Based Queues | Y | N | N | N | N | N | N/A | Y<sup>9</sup> | Agents on non-supported devices can still answer calls however they won't have the collaborative calling user interface |
| **Dynamic caller ID** |  |  |  |  |  |  |  |  |  |
| Standard Call queue | Y | Y | Y | N | N | N | Y | N/A |  |
| Channel based Call queue | Y | N/A | N/A | N/A | N/A | N/A | N/A | Y |  |
| **PSTN Connectivity Methods** |  |  |  |  |  |  |  |  | See Note 10 |
| Calling Plans | Y | Y | Y | Y | Y | Y | Y | Y |  |
| Direct Routing | Y | Y | Y | Y | N<sup>12</sup> | Y | Y<sup>7</sup> | Y |  |
| Operator Connect | Y | Y | Y | Y | N | Y | Y<sup>7</sup> | Y |  |
| **Miscellaneous** |  |  |  |  |  |  |  |  |  |
| Call toast shows Resource Account Name | Y | N | Y | N | Y |  | Y | Y |  |
| Click-to-call | Y | N | N | N | N | N | Y | Y |  |
| Compliance recording |  |  |  |  |  |  |  |  | See [Compliance recording](teams-recording-policy.md) |
| [Location based routing](location-based-routing-plan.md#inbound-calls-through-auto-attendants) | N/A | N/A | N/A | N/A | N/A | N/A | N/A | N/A | Not supported |

#### Notes

1. Microsoft Teams Windows client, Microsoft Teams Mac Client, Microsoft Teams on Virtualized Desktop Infrastructure.
2. Microsoft Teams iPhone app, Microsoft Teams Android app.
3. Teams Phone Mobile Cellular Phone Dialer.
4. Selecting *Longest Idle* for the agent routing method automatically enables Presence based routing.
5. It's not possible to set the order the agents are presented with calls when using a group or channel for membership.
6. Conference mode isn't supported if phone calls are routed to the queue from a Direct Routing gateway enabled for Location-Based Routing.
    - Location based routing isn't supported with Call queues. For more information, see [Voice apps (Auto Attendant or Call Queue)](location-based-routing-plan.md#inbound-calls-through-auto-attendants).
7. Microsoft Teams Phone only.
8. Through the User Settings Portal page at [https://aka.ms/vmsettings](https://aka.ms/vmsettings).
    - GCCH: [https://dialin.cpc.gov.teams.microsoft.us/usp](https://dialin.cpc.gov.teams.microsoft.us/usp)
    - DOD: [https://dialin.cpc.dod.teams.microsoft.us/usp](https://dialin.cpc.dod.teams.microsoft.us/usp)
9. Only standard channels are supported.
10. Transferring calls between Public Switched Telephone Network (PSTN) connectivity methods isn't supported.
11. Performed through Team Phone Mobile app or see #8.
12. Call queues that are assigned a Direct Routing number don't support Skype for Business clients, Lync clients, or Skype for Business IP Phones as agents. The Teams client is only supported with a [coexistence mode of Teams Only](setting-your-coexistence-and-upgrade-settings.md).

### Supported clients

The following clients are supported for call agents in a Call queue:

- Skype for Business desktop client 2016 (32-bit and 64-bit versions)
- All IP phone models supported for Microsoft Teams.
- Mac Skype for Business Client (version 16.8.196 and later)
- Android Skype for Business Client (version 6.16.0.9 and later)
- iPhone Skype for Business Client (version 6.16.0 and later)
- iPad Skype for Business Client (version 6.16.0 and later)
- Microsoft Teams Windows client (32-bit and 64-bit versions)
- Microsoft Teams Mac client
- Microsoft Teams on [Virtualized Desktop Infrastructure](teams-for-vdi.md) (Windows Virtual Desktop, Citrix, and VMware)
- Microsoft Teams iPhone app
- Microsoft Teams Android app

### Call Queue Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that a Call queue is able to receive calls:

1. Select **Run Tests**, which populates the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Queue](https://aka.ms/TeamsCallQueueDiag)

2. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

3. The tests return the best next steps to address any tenant, policy, and resource account configurations to validate that the Call queue is able to receive calls.

## Related articles

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)

[Here's what you get with Microsoft Teams Phone](here-s-what-you-get-with-phone-system.md)

[Getting service phone numbers](getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
