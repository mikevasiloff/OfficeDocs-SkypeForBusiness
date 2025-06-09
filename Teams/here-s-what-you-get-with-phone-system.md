---
title: "Teams Phone features"
ms.reviewer: 
ms.date: 04/25/2025
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
msreviewer: jastark, roykuntz
ms.topic: article
ms.assetid: bc9756d1-8a2f-42c4-98f6-afb17c29231c
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn about the features, availability, and how to plan and set up Microsoft Teams Phone for your business."
---

# Teams Calling features

This article describes Microsoft Teams calling and Teams Phone features. For more information about using Teams Phone as your Private Branch Exchange (PBX) replacement, and options for connecting to the Public Switched Telephone Network (PSTN), see [What is Teams Phone](what-is-phone-system-in-office-365.md). This article is for administrators and IT professionals.

Clients are available for PC, Mac, and mobile, which provides features on devices from tablets and mobile phones to PCs and desktop IP phones. For more information, see [Get clients for Microsoft Teams](get-clients.md).

> [!NOTE]
> For details about Teams phone systems on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Licensing

The features listed below indicate whether or not a license for Teams Phone is required.

The Microsoft Teams Enterprise license includes native calling features, and the Teams Phone license unlocks even more features.

To review licensing scenarios, see [Teams Phone licensing](teams-phone-licensing.md).

For features where a Teams Phone license is required, a connection with the Public Switched Telephone Network (PSTN) and phone number is also required.

> [!NOTE]
> A PSTN solution is separate from a Teams Phone license. A PSTN solution provides a customer's tenant with phone numbers and PSTN access to domestic, international, and emergency calling. The Teams Phone license entitles a Teams user to enhanced calling capabilities within the tenant and access to the PSTN solution.
  
## Teams calling features

**Microsoft Teams Enterprise** provides the following calling features:

|Teams calling features  |Description |With Microsoft Teams Enterprise license|With Microsoft Teams Enterprise license + Teams Phone license|
|:-----|:-----|:-----|:-----|
|[Auto attendants](what-are-phone-system-auto-attendants.md)  |Lets you create a menu system that enables external and internal callers to locate and place or transfer calls to company users or departments in your organization.  <br/> Note that users don't need to be voice enabled to receive calls from the auto attendant dial by name or dial by number directory search. However, you must voice enable users to receive calls from the auto attendant menu options. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)</br>See [Teams Phone Resource Account licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)|
|[Call queues](create-a-phone-system-call-queue.md)|Lets you configure how call queues are managed for your organization. For example, set up greetings and music on hold, search for the next available call agent to handle the call, and so on. You must voice enable users to receive calls from a call queue.|![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)</br>See [Teams Phone Resource Account licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)|
|[Voicemail](set-up-phone-system-voicemail.md)  | When a user receives a voicemail, it's delivered to their Exchange mailbox as an email with the voicemail message as an attachment. Users can listen to their messages on their certified desktop phone, and on all Teams applications.|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Voicemail user settings](https://support.office.com/article/456cb611-3477-496f-b31a-6ab752a7595f?ui=en-US&rs=en-US&ad=US)  | Lets users configure their client settings for voicemail greetings, call answering rules, and greeting language, including out-of-office greetings.   |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Music on hold](music-on-hold.md) | Plays default music defined by the service, streaming music, or custom music uploaded by the tenant administrator when a call is placed on hold. This feature provides on-hold notification parity with other platforms.  |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Call answer/initiate (by name)   |Lets users answer inbound calls with a touch, and place native Teams calls by selecting a name in the client.|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Call answer/initiate (by extension or PSTN phone number)   |Lets users answer inbound calls with a touch, and place calls by dialing a PSTN phone number, an internal extension, or by selecting a name in the client.  |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call forwarding to voicemail](user-call-settings.md)  |Lets users redirect calls to voicemail with immediate redirect or with customized delay before redirecting.   |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call forwarding options and simultaneous ring](user-call-settings.md)  |Lets users set up rules for forwarding and simultaneous ring, so they can direct their calls to (and their calls can be answered by) any Teams colleague or PSTN number. Delayed simultaneous ring is supported. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call Groups](call-sharing-and-group-call-pickup.md)|Lets users create a group of members who can receive calls on the user's behalf. A user can designate their call group for simultaneous ring or for call forwarding. Call groups can be configured by users to ring everyone at once, or in the order defined by the user.  |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call delegation](user-call-settings.md)  | Also known as shared line appearance. Share a user's phone line with other users so that they can make and receive calls on the delegator's behalf. Less disruptive to recipients than other forms of call sharing (such as call forwarding and simultaneous ringing) because users can configure how they want to be notified of an incoming delegated call. Also supports barge and shared history. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Member of call group or call delegation](call-sharing-and-group-call-pickup.md)  | Lets users answer incoming calls for a colleague if they are designated as a member of that colleague's call group, or designated as a call delegate.  |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Transfer a call, including consultative transfer to another user](https://support.office.com/article/b7f40f14-e083-46b9-b739-68038c8f73a0)  |Lets users transfers calls to another person or their voicemail.<br/>Users *do not* need a Teams Phone license to receive any transferred calls from another user, but they *do* need a Teams Phone license if they require transferring to PSTN numbers. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Transfer a call in progress to another device](https://support.microsoft.com/office/join-a-microsoft-teams-call-on-a-second-device-42ceae44-a470-4c93-9496-f1905c000d82)  |Lets users transfer a call in progress from one device to another, without interruption. If they need to leave their office but want to continue the conversation, they can transfer the call from their PC to the mobile app on their cell phone. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call park and retrieve](call-park-and-retrieve.md)   | Lets users park a call on hold in the Teams service. When a call is parked, the service generates a unique code for call retrieval. The user who parked the call or someone else can then use that code and a supported app or device to retrieve the call.  |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[External Caller ID](caller-id-policies.md)   |Calls from inside the company display a detailed caller ID that pulls information from the corporate directory, showing picture ID and job title instead of just a phone number. For calls from external phone numbers, the caller ID as provided by the phone service provider is displayed. If the external phone numbers are secondary numbers in the corporate directory, then the information from the corporate directory will be displayed.   |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Device switching](https://support.microsoft.com/office/connect-a-microsoft-teams-display-or-desk-phone-to-microsoft-teams-windows-desktop-fa390a48-5df8-4784-a49d-a78e2619f9da)   |Lets users play a call or meeting on another HID device that is connected to Teams; for example, switching from their PC speakers to a Teams display.    |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Presence-based call routing  |Controls inbound communications with presence, enabling the user to block all incoming communication except from those specifically indicated.   |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Integrated dial pad](https://support.office.com/article/27bc60b5-74c0-4e9c-808b-da4db9514d89)  | Lets users dial by name or by number anywhere in the search bar and in the dial pad, speeding up the process of making outbound calls.   |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|Federated calling   |Lets users securely connect, communicate, and collaborate with users in federated tenants.   |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Make and receive a video call](https://support.office.com/article/abf62493-670f-4b0d-b2cf-fe03b49caf42)  | If the user's account is enabled for video calls, the user can make face-to-face video calls with their contacts. All they need is a camera, their computer’s speakers and microphone. Users can also use a headset if their computer doesn’t have a built-in audio device. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Secondary ringer](https://support.office.com/article/456cb611-3477-496f-b31a-6ab752a7595f)  | Users with multiple speaker devices connected to their PC can choose to set a secondary device to ring in addition to their default speaker. For example, a user with a headset connected to the PC and desk speakers can choose to have both headset and desk speakers ring when a call comes in so that they don’t miss a call. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Distinctive ring alerts](https://support.office.com/article/456cb611-3477-496f-b31a-6ab752a7595f) |Lets users choose separate ringtones for  normal calls, forwarded calls, and delegated calls so they can distinguish the type of call.    |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Busy on Busy](inbound-call-routing.md)| A calling policy that lets you configure how incoming calls are handled when a user is: <ul><li>in a call </li><li>in a conference</li><li>has a call placed on hold. </li></ul> The caller will receive one of the following responses: <ul><li>hear a busy signal when the callee is on the phone</li> <li>will be routed accordingly to the user's unanswered settings. One option lets the caller leave a voicemail for the user who is already on a call.</li></ul> The callee gets a missed call notification but isn't able to answer incoming calls. This feature is disabled by default, but can be turned on by the tenant admin. </br> Users can control this setting from their client if permitted in calling policy. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Call blocking](https://support.office.com/article/456cb611-3477-496f-b31a-6ab752a7595f)  | Lets users add PSTN phone numbers to a blocked list so that the next call from that number is blocked from ringing the user. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Common area phones](set-up-common-area-phones.md)  | A common area phone is typically placed in an area like a lobby or conference room making it available to multiple people. Common area phones are set up as devices rather than users, and can automatically sign into a network. |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Media bypass support](direct-routing-plan-media-bypass.md) (for Teams Direct Routing only)  | For better performance, media is kept between the Session Border Controller (SBC) and the client instead of sending it through  Teams Phone.  |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Unassigned number routing](routing-calls-to-unassigned-numbers.md) | Allows routing of unassigned numbers to users, auto attendants, call queues or a custom announcement.  |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) | Provides location support for first responders when emergency calls are made from Teams. Emergency calling event notification. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md) | Administer number types, number acquisition, and number management. |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Dial plans](dial-plans-routing-overview.md) | Process and route telephone calls based on customizable dial plans |![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Redirect external phone calls](https://support.microsoft.com/office/call-forwarding-call-groups-and-simultaneous-ring-in-microsoft-teams-a88da9e8-1343-4d3c-9bda-4b9615e4183e) | Send inbound calls from external callers to user's forwarding settings (for example, voicemail) while not impacting internal calls. | ![Image of a x for no](/office/media/icons/cancel-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|
|[Teams Phone extensibility](teams-contact-center.md) | Supporting contact center integrations with several integration models |![Image of a checkmark for yes](/office/media/icons/success-teams.png)|![Image of a checkmark for yes](/office/media/icons/success-teams.png)|

## Additional Teams Phone functionality

Optional features are available to enhance your organization's Teams Phone experience, including the following:

**[SMS in Teams overview](sms-overview.md)**

- Assign users with a number acquired through a Microsoft Calling Plan license in the United States (including Puerto Rico) or Canada to provide SMS support.

**[Teams Premium](intelligent-recap-calls-meetings.md)**

- Add Teams Premium and Microsoft 365 Copilot to Teams Phone to give end users enhanced capabilities:
  - Additional AI capabilities
  - Greater administrative insights to reporting, with alerting
  - Enhanced supervisory capabilities and insights into Call Queues with the Microsoft [Queues app](manage-queues-app.md).

## Availability in GCC High and DoD clouds

The following capabilities aren't yet available in GCC High and DoD Clouds.

- [Call settings for secondary ringer, voicemail, and enhanced delegation](https://support.office.com/article/Manage-your-call-settings-in-Teams-456cb611-3477-496f-b31a-6ab752a7595f)
- [Transfer to voicemail mid call](https://support.office.com/article/Transfer-a-call-in-Teams-b7f40f14-e083-46b9-b739-68038c8f73a0)
- Call phone number from search bar
- Microsoft Entra ID reverse number lookup

## Related articles

- [What is Teams Phone](what-is-phone-system-in-office-365.md)
- [Cloud voice in Microsoft Teams](cloud-voice-landing-page.md)
- [Set up Teams Phone](setting-up-your-phone-system.md)
- [Which Calling Plan is right for you?](calling-plan-landing-page.md)
- [Monitor and manage call quality](monitor-call-quality-qos.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Pricing for Teams Phone](https://products.office.com/microsoft-teams/voice-calling#requirements)
- [Teams for Virtualized Desktop Infrastructure with callings and meetings](teams-for-vdi.md#teams-on-vdi-with-calling-and-meetings)
