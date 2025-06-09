---
title: Set up call priorities for call queues in Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
audience: admin
ms.date: 05/20/2025
ms.collection: 
- M365-voice
- m365initiative-voice
- Tier1
f1.keywords:
- CSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up call priorities for call queues in Microsoft Teams to ensure high-priority calls are answered first, while lower-priority calls are held in a queue until an agent's available.
---

# Set up call priorities for call queues

Call priorities for Call queues in Microsoft Teams allow you to set the order in which calls are routed to agents within a call queue. This functionality is useful for ensuring that high-priority calls are answered first, while lower-priority calls are held in a queue until an agent becomes available.

Before reading this article, make sure you have read [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md).

## Overview

Call queue call priorities provide a way for calls to be prioritized within the same call queue. The priority of the call controls the order in which the call is presented to the agents.

When an agent becomes available to take a call, they receive the highest-priority call that has been waiting the longest. If there are multiple calls with the same priority level, the one that has been waiting the longest is presented to the agent first.

As an IT admin, you can assign different levels of call priority on a scale of 1 to 5, with 1 being the highest priority and 5 being the lowest priority:

1. Very High
1. High
1. Normal (default priority)
1. Low
1. Very Low

### Call priority assignment conditions

Priority is assigned to a call in the following situations:

- Auto attendants can set the priority of a call when transferring to a Call queue or a resource account with a Resource account type set to Call queue.
- Resource accounts assigned to a Call queue can have a priority set.

When a transferred call arrives at a call queue, the call queue honors the priority that the transferring auto attendant or call queue had previously set. When a direct call arrives at a call queue, the call queue uses the priority assigned to the resource account.

## Configure call priorities

Call priorities can currently only be configured using PowerShell. See the following [call priority call flow scenarios](#call-priority-call-flow-scenarios) for PowerShell examples.

> [!IMPORTANT]
> If you make changes through the Teams admin center to Auto attendants or Call queues that you configured with call priorities, the call priority configuration is removed. Once you configure an Auto attendant or Call queue with call priorities via PowerShell, all future changes to that Auto attendant or Call queue must be done through PowerShell until the functionality becomes available in Teams admin center.

## Call priority call flow scenarios

### Scenario 1: Priority to callers based on dialed number

In this scenario, Contoso Support has a single Technical Support call queue that's open 24/7. Contoso's website and documentation provides their customers with the general number for all support requests. However, customers who sign up for "enhanced support" are given a dedicated number to call. The enhanced support customers are given priority over other customers based on the level of enhanced support purchased (or not purchased).

Constoso Support defines the following call priorities for their resource accounts:

- **Priority 4** - Any customer calling the general support phone number.
- **Priority 3** - Customers call the Bronze level support phone number.
- **Priority 2** - Customers calling the Silver level support phone number.
- **Priority 1** - Customers calling the Gold level support phone number.

Customers in the call queue are presented to agents in the order of their priority. The Gold level customers are all presented first, followed by Silver, Bronze, and finally General support customers.

:::image type="content" source="media/cq-call-priorities-scenario-1.svg" alt-text="Screenshot showing the call flow for Scenario 1.":::

The following command uses the [New-CsOnlineApplicationInstanceAssociation](/powershell/module/teams/new-csonlineapplicationinstanceassociation) cmdlet with the `-CallPriority` parameter to set the call priority for a call queue based on the dialed number (Gold, Silver, Bronze, General):

<!-- markdownlint-disable MD040 -->
<details>
<summary>Expand to see the PowerShell example</summary>

```powershell
# Assign resource accounts to call queue
$callQueueID = (Get-CsCallQueue -NameFilter "Support").Identity
$goldID = (Get-CsOnlineUser -Identity contoso-support-gold@contoso.com).Identity
$silverID = (Get-CsOnlineUser -Identity contoso-support-silver@contoso.com).Identity
$bronzeID = (Get-CsOnlineUser -Identity contoso-support-bronze@contoso.com).Identity
$generalID = (Get-CsOnlineUser -Identity contoso-support-general@contoso.com).Identity

New-CsOnlineApplicationInstanceAssociation -Identities @($goldID) -ConfigurationID $callQueueID -ConfigurationType CallQueue -CallPriority 1
New-CsOnlineApplicationInstanceAssociation -Identities @($silverID) -ConfigurationID $callQueueID -ConfigurationType CallQueue -CallPriority 2
New-CsOnlineApplicationInstanceAssociation -Identities @($bronzeID) -ConfigurationID $callQueueID -ConfigurationType CallQueue -CallPriority 3
New-CsOnlineApplicationInstanceAssociation -Identities @($generalID) -ConfigurationID $callQueueID -ConfigurationType CallQueue -CallPriority 4
```

</details>
<!-- markdownlint-enable MD040 -->

### Scenario 2: Priority to callers based on Auto attendant menu choices

In this scenario, Contoso Travel has a single Travel Support call queue for all travel inquiries. This call queue is associated with an auto attendant that provides callers with the following options:

> Thank you for calling Contoso Travel.
> If you are currently traveling and need immediate assistance, press 1.
> If you are calling to inquire about an existing booking, press 2.
> To make a new booking, press 3.
> For all other inquiries, press 4.

Callers who press 1 get top priority and connect to agents first, followed by callers who press 2, 3, and 4 in decreasing order of priority.

:::image type="content" source="media/cq-call-priorities-scenario-2.png" alt-text="Screenshot showing the call flow for Scenario 2.":::

The following command uses the [New-CsAutoAttendantCallableEntity](/powershell/module/teams/new-csautoattendantcallableentity) cmdlet with the `-CallPriority` parameter to set the call priority for a call queue based on the Auto attendant menu choices (immediate assistance, existing booking, new booking, other inquiries):

<!-- markdownlint-disable MD041 -->
<details>
<summary>Expand to see the PowerShell example</summary>

```powershell
# Create the Auto Attendant
$callQueueID = (Get-CsCallQueue -NameFilter "Travel").Identity
$callableEntity1 = New-CsAutoAttendantCallableEntity -Identity $callQueueID -Type ConfigurationEndpoint -CallPriority 1
$callableEntity2 = New-CsAutoAttendantCallableEntity -Identity $callQueueID -Type ConfigurationEndpoint -CallPriority 2
$callableEntity3 = New-CsAutoAttendantCallableEntity -Identity $callQueueID -Type ConfigurationEndpoint -CallPriority 3
$callableEntity4 = New-CsAutoAttendantCallableEntity -Identity $callQueueID -Type ConfigurationEndpoint -CallPriority 4

$greetingPrompt = New-CsAutoAttendantPrompt -TextToSpeechPrompt "Thank you for calling Contoso Travel"
$menuPrompt = New-CsAutoAttendantPrompt -TextToSpeechPrompt "If you are currently traveling and require immediate assistance, press 1. If you are calling to inquire about an existing booking, press 2. To make a new booking, press 3. For all other inquiries press 4."

$menuOption1 = New-CsAutoAttendantMenuOption -Action TransferCallToTarget -DtmfResponse Tone1 -CallTarget $callableEntity1
$menuOption2 = New-CsAutoAttendantMenuOption -Action TransferCallToTarget -DtmfResponse Tone2 -CallTarget $callableEntity2
$menuOption3 = New-CsAutoAttendantMenuOption -Action TransferCallToTarget -DtmfResponse Tone3 -CallTarget $callableEntity3
$menuOption4 = New-CsAutoAttendantMenuOption -Action TransferCallToTarget -DtmfResponse Tone4 -CallTarget $callableEntity4

$defaultMenu = New-CsAutoAttendantMenu -Name "Default menu" -Prompts @($menuPrompt) -MenuOptions @($menuOption1, $menuOption2, $menuOption3, $menuOption4)
$defaultCallFlow = New-CsAutoAttendantCallFlow -Name "Default call flow" -Greetings @($greetingPrompt) -Menu $defaultMenu
New-CsAutoAttendant -Name "Contoso Travel" -LanguageId en-US -TimeZoneId "Eastern Standard Time" -DefaultCallFlow $defaultCallFlow 
```

</details>
<!-- markdownlint-enable MD041 -->

### Scenario 3: Priority to agents transferring calls to another call queue

In this scenario, Contoso Finance Customer Service agents triage calls and they often transfer these calls to Tier 2 Support groups. Tier 2 Support groups can also take calls directly from customers. Constoso wants calls transfers from Customer Service to have higher priority than calls that are directly dialed into Tier 2 Support, as these callers have already waited and spoken with an agent.

:::image type="content" source="media/cq-call-priorities-scenario-3.svg" alt-text="Screenshot showing the call flow for Scenario 3.":::

## Considerations

Keep in mind the following considerations when configuring call priorities:

- Agents always receive calls with the highest priority first, regardless of how long lower priority calls have been waiting.
- Call priorities aren't supported for [Authorized users](/microsoftteams/aa-cq-authorized-users-plan).
- Keep the highest and lowest call priorities available for future use.
- Agents don't receive notifications about which calls are what priority. The priority is only used to determine the order in which calls are presented to agents.

## Related articles

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)

[Routing calls with Auto attendants and Call queues](plan-your-call-routing-flow.md)

[Set up Auto attendants in Microsoft Teams](create-a-phone-system-auto-attendant.md)

[Set up call queues in Microsoft Teams](create-a-phone-system-call-queue.md)

[Manage resource accounts in Microsoft Teams](manage-resource-accounts.md)

[Call flows in Microsoft Teams](microsoft-teams-online-call-flows.md)
