---
title: Routing calls with Auto attendants and Call queues for Microsoft Teams
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 12/13/2024
ms.topic: article
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - tier1
audience: Admin
appliesto: 
  - Microsoft Teams
  - Skype for Business
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: Learn how to plan your call routing flow for Auto attendants and Call queues in Microsoft Teams.
--- 

# Routing calls with Auto attendants and Call queues

As part of the planning process, we recommend that you work out the call routing for your organization in a diagram. The diagram helps determine the most efficient routing for people calling in to your organization. You can also use the diagram to determine the Auto attendants and Call queues that you need to create, along with related requirements such as service numbers, licenses, and resource accounts.

Let's look at how Auto attendants and Call queues route calls.

## Auto attendants 

Auto attendants route all calls in one of the following ways:

- **Redirect immediately** - calls can be redirected to one of the call routing destinations (listed below) immediately upon answering or after an initial greeting.
- **Redirect based on dial options** - callers can be directed to choose between options that are assigned to the numbers on their telephone keypad, 0-9, \* and \#. Each dial key can be assigned a call routing destinations.
- **Dial people by name or extension** - callers can be directed to dial the extension number of the person they're trying to reach in your organization's directory, or by spelling the person's name.
- **Disconnect** - an Auto attendant can hang up the call.

An Auto attendant can redirect calls to the following destinations:

- **Operator** - the operator defined for the Auto attendant.
  - Defining an operator is optional but recommended.
  - An operator can be any of the other destinations in this list.
- **Person in the organization** - a person in your organization who is able to receive voice calls. This person can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another Auto attendant or a Call queue. The call priority can be set when the destination is a call queue.
- **Resource account** - the resource account associated with another Auto attendant or Call queue. The call priority can be set when the resource account is associated with a call queue.
- **Voicemail** - the voice mailbox associated with a Microsoft 365 group, distribution list, or mail-enabled security group that you specify.
  - You can choose if you want voicemail transcriptions and the "Please leave a message after the tone." system prompt.
- **External phone number** - any phone number. See [external transfer technical details](create-a-phone-system-auto-attendant.md?tabs=additional-resources).
- **Announcement** - play a recorded audio file or text to speech
   - the caller returns to the auto attendant menu when the announcement finishes playing
 
Auto attendants offer separate call routing options for calls received outside of business hours and on holidays.

For more information on when to use **Voice app** or **Resource account** as the routing destination, see [Nested Auto attendants and Call queues](plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues)

> [!NOTE]
> A single Auto attendant can only support a single "dial by" method. To allow callers to dial by name and by number, you need to create an Auto attendant that has an option for dial by name and another Auto attendant for dial by extension. Each of these options route to separate Auto attendants configured for these "dial by" scenarios.

## Call queues 

Call queues place the caller on hold until an agent assigned to the queue is available to take their call. There are three situations where a caller might be directed out of the queue:

- **Call overflow** - if the number of calls waiting in the queue exceeds the limit that you set, then new callers are redirected out of the queue. 
- **Call timeout** - if a caller stays in the queue longer than the configured timeout setting, they're redirected out of the queue.
- **No agents** - if there are no agents opted or logged into the queue, callers may be redirected out of the queue.

Calls redirected out of a queue can be sent to the following destinations:

- **Person in the organization** - a person in your organization who is able to receive voice calls. This person can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another Auto attendant or a Call queue.
- **Resource account** - the resource account associated with another Auto attendant or Call queue.
- **External phone number** - any phone number. For more information, see [external transfer technical details](create-a-phone-system-auto-attendant.md?tabs=additional-resources).
- **Voicemail (personal)** - the voice mailbox associated with a specific user.
- **Voicemail (shared)** - the voice mailbox associated with a Microsoft 365 group, distribution list, or mail-enabled security group.
  - You can choose if you want voicemail transcriptions and the "Please leave a message after the tone" system prompt.

For more information on when to use **Voice app** or **Resource account** as the routing destination, see [Nested Auto attendants and Call queues](plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues).

## Call flow diagram

The following call flow diagrams show 3 different examples of call routing using Auto attendants and Call queues.

:::image type="content" source="media/cq-call-priorities-scenario-1.svg" alt-text="Screenshot showing the call flow for call priority based on dialed resource account phone number.":::

In this example:

- The call queues are open 24/7.
- Call priorities are assigned based on the resource account phone number dialed by the caller.

:::image type="content" source="media/cq-call-priorities-scenario-2.png" alt-text="Screenshot showing the call flow for call priority based on auto attendant menu choices.":::

In this example:

- The auto attendant assigns the call priority based on the menu option selected by the caller.

:::image type="content" source="media/cq-call-priorities-scenario-3.svg" alt-text="Screenshot showing the call flow for call priority call queue transfers.":::

In this example:

- The auto attendant assigned a call priority of 3 to all callers
- Call transfers to the Tier 2 Support call queue can be prioritized over regular callers

We recommend that you create one or more diagrams similar to the example given to map out your call routing. Be sure your diagram or accompanying documentation includes the following:

- The Auto attendants and Call queues that have direct access via phone numbers (these will require resource accounts).
- The off-hours and holiday routing requirements for each Auto attendant.
- The membership for each Call queue. (You can add users individually or map the queue to different kinds of groups. Mapping a queue to a team provides the most versatile experience.)

## Call routing best practices

Here are some call routing best practices:

- Look at your existing calling system and analyze the types and frequency of incoming calls. Use this information to help inform your Auto attendant and Call queue structure.
- Put the most common options earliest in the menu to route calls as quickly as possible.
- Avoid connecting service numbers directly to Call queues unless the queues are available 24/7. Call queues don't allow for separate call handling for off hours or holidays. If you want to have a queue with a direct number, assign the number to an Auto attendant that automatically redirects to the queue during business hours.
- If you receive numerous calls requesting basic information about your company, such as business hours, location, or web site address, consider creating an Auto attendant to answer these questions with recorded messages.
- Keep the list of menu items to five or fewer. Callers can have trouble remembering more than five options. Use [nested Auto attendants](plan-auto-attendant-call-queue.md#nested-auto-attendants-and-call-queues) if more options are needed to properly route a call.
- Describe the service first, followed by the option to press (for example: For Sales press 1) rather than the other way around (for example: Press 1 for Sales).
- User terminology your callers understand rather than what you might use internally.
- Avoid frequent updates to call routing. If you change your menu options for an Auto attendant in the future, call that out in the voice prompts for the first 30 days.

> [!IMPORTANT]
> The maximum number of transitions a single call is permitted to make through Auto attendants and Call queues is twenty-five (25). After this, the call is disconnected. This is done to prevent a call from infinitely looping through a series of Auto attendants and Call queues.
>  
> For example, if a call arrives on Auto attendant #1 and the caller selects an option that sends them to Auto attendant #2, this counts as one transition. If the caller selects an option on Auto attendant #2 that returns them to Auto attendant #1 or sends them to Call queue #1, then this would count as a second transition.
>  
> Calls that remain in the same Auto attendant but return to the main menu multiple times, for example when an announcement is played or there's a configured menu option to repeat, are also counted as a transition and are impacted by this maximum transition limit.

## Related articles

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)

[Call priorities](aa-cq-call-priorities.md)

[Set up Auto attendants](create-a-phone-system-auto-attendant.md)

[Set up Call queues](create-a-phone-system-call-queue.md)
