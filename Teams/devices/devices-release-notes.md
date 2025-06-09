---
title: Release notes for devices in Microsoft Teams
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 05/05/2025
ms.topic: release-notes
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto:
  - Microsoft Teams
ms.collection:
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords:
  - CSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about what's new in Microsoft Teams devices.
---

# What's new in Microsoft Teams devices

This article contains updates for Microsoft Teams devices. To view feature updates for Microsoft Teams desktop, web, or mobile, go to [What's new in Microsoft Teams](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-d7092a6d-c896-424c-b362-a472d5f105de).

To view feature updates for Microsoft Teams Rooms, go to:

- [Release notes for Microsoft Teams Rooms on Windows](../rooms/rooms-release-note.md)
- [Release notes for Microsoft Teams Rooms on Android](../rooms/rooms-release-note.md)

## [Teams panels](#tab/panels)

## April 24, 2025

**Applies to:** *Teams app version: 1449/1.0.97.2025086303*

> [!IMPORTANT]
> This update introduces a new versioning format, moving away from using dates. Going forward, this format will be used 1449/1.0.94.*year of release.internal codes*.

- **Occupancy state** Teams panels can now smartly utilize signals from Teams Rooms devices or occupancy sensors paired with panels to indicate when a room is in use (e.g. LED glow), so you’re not surprised to find an available room is actually occupied. Requires a Teams Rooms Pro or Shared Devices. For more information, see [Occupancy state on Teams panels](/microsoftteams/devices/teams-panels-occupancy). Note that this feature hasn't started to roll out to GCC. Stay tuned for updates. 

## April 2025

**Applies to:** *Teams app version: 1449/1.0.97.2025031901*

- AOSP resiliency fixes. 

## March 2025

**Applies to:** *Teams app version: 1449/1.0.97.2025021101*

- Fixes for check-in and auto-release.

## January 2025

**Applies to:** *Teams app version: 1449/1.0.97.2024122401*

> [!IMPORTANT]
> Required updates coming to the session flows. Starting June 2025, clients more than five months old will no longer work.

- **Custom name**  IT admins can customize the display name shown on Teams panels through the Teams Rooms Pro Management portal. This feature is only available with the Teams Rooms Pro and Teams Shared Device Licenses. To learn more about custom names, see [Add a custom name for Teams panels](custom-names.md).
- Fix for Room Equipment not populating.

### November 2024

**Applies to:** *Teams app version: 1449/1.0.97.2024102301*

- Authentication fixes and check-in reliability improvements.

### September 2024

**Applies to:** *Teams app version: 1449/1.0.972024081207*

- **Custom backgrounds**  IT admins can upload custom background images on the Teams Admin Center to reinforce company brand on Teams panels devices. PNG, JPG, and JPEG formats are supported. This feature is only available with the Teams Rooms Pro and Teams Shared Device Licenses. To learn more about custom backgrounds, see [Set up and manage custom backgrounds on Teams panels](custom-background-panels.md).

- **Daily device restart window**  By default, the device restarts anytime between 2:00 AM and 3:00 AM based on its local time zone. If the device is in use during this window and the restart-window period ends, the restart is rescheduled the following day. IT admins can turn off this functionality or change the restart window from the device settings or remotely in Teams Admin Center.
- Bug fix for remotely changing "Release room if no one checks in" syncing to the device.

### July 2024

**Applies to:** *Teams app version: 1449/1.0.97.2024071105 (Logitech, Crestron, Neat, EPOS, AudioCodes, Poly, Yealink with CP 5484 and 6061)*

- Authentication and other check-in bug fixes.

### June 2024

**Applies to:** *Teams app version: 1449/1.0.97.2024061108*

- Company Portal 6152 (available to Yealink, Crestron, Logitech, AudioCodes, EPOS, and Poly panels on Company Portal 5484, 5882, or 6061). Fixes for authentication issues, including a fix for sign-in failures immediately following sign out.
- Multi-panel check-in support. (Generally available and for GCC. GCCH and higher aren't supported at this time) If a resource account is being shared across multiple panels, the check-in status for the meeting will remain in sync across the panels. This ensures the room is released or not released correctly. To learn more on the check-in feature, see [Check-in and auto release on Microsoft Teams panels](check-in-and-auto-release.md).

> [!NOTE]
> For every panel device, regardless of whether it's part of a multi-panel room, when you initially download this app, the current setting for Release room, if no one checks in, will be updated in Exchange. Allow 48 hours for this sync to happen. Be sure you download the app when there are no meetings scheduled within the next 48 hours.
> [!NOTE]
> Going forward, when auto release is enabled, disabled, or adjusted, it can take up to 48 hours for this change to take effect. For this reason, it's recommended that you adjust the settings when no meetings are scheduled for the next 48 hours.

### April 2024

**Applies to:** *Teams app version: 1449/1.0.97.2024040202 (Logitech, Neat, AudioCodes, EPOS, Poly, Crestron, and Yealink Room Panel with CP 5.0.5484)*

- More bug fixes for room reservations.

### March 2024

**Applies to:** *Teams app version: 1449/1.0.97.2023121202 (Yealink Room Panel and Yealink Room Panel Plus with Company Portal 5.0.5882.0)*

- Significantly reduce sign-out errors due to Workplace Join failures, timeout issues, and memory leaks.

### February 2024

**Applies to:** *Teams app version: 1449/1.0.97.2024010401 (Crestron, Logitech, Neat, AudioCodes, EPOS, and Yealink Room Panel with Company Portal 5.0.5484.0)*

- Authentication fixes for room reservations

### December 2023

**Applies to:** *Teams app version: 1449/1.0.97.2023111003 (Crestron, Logitech, Neat, Poly, AudioCodes, EPOS)*

- Turn on and off the QR code remotely via the Teams Admin Center.

### August 2023

**Applies to:** *Teams app version: 1449/1.0.97.2023080401*

- **QR code reservations on Teams Panels**  Teams Panels with a Teams Shared Device License or a Teams Rooms Pro License allows people to reserve the room using a QR code on the Panel. If you're signed into your Teams app on mobile, upon scanning from your mobile device, you can schedule a new meeting with the room prepopulated. You can also easily see the room's availability for your meetings and book the room with one click. This feature is enabled by default and can be disabled under **Device settings** > **Admin settings** > **Meetings**. To learn more about using QR code reservations, see Reserve a room using a QR code on a Teams Panel.
- The recommended version of Teams on your Android phone is 1416/1.0.0.2023153001 and above. On iOS, the recommended version is 5.15.0 and above.

> [!NOTE]
> The following instructions are for an Android mobile phone with an Android work profile (AWP).

- You can scan the QR code using the camera app on your Android mobile phone. However, the feature may not work if you have both work and personal profiles on your Android phone. In this case, your admin must add a mobile system OS scanner in the work profile.

To add a mobile system OS scanner:

1. In the Intune Admin Center, go to **Apps** > **Android**, and add.

2. Select **Android enterprise system app**.

3. Enter the type of Android phone. Then, Google and paste the OS camera package name.

4. Assign to an individual or group.

5. Download and install the camera app from the app store in your work profile.

- **Loading sign when creating a reservation**  When making a reservation on the Panel using the green **Reserve** button, you see a loading sign after you confirm the end time of your reservation to let you know the reservation is being made.

### June 2023

**Applies to:** *Teams app version: 1449/1.0.97.2023060102*

- To align with Microsoft Teams Rooms on Windows calendar experience, with this update on panels, if a reservation is scheduled to begin within 10 minutes or less, you no longer can book the room in an ad-hoc fashion on the device.
- When an admin changes the panel display name in the Microsoft Admin Center, it updates without an admin needing to log in again on the device.
- Enabling and disabling room reservations on Panels remotely in Teams Admin Center.

### April 2023

#**Applies to:** *Teams app Version: 1449/1.0.97.2023041403*

- IT admins can use Teams panels with their Government Community Cloud High (GCC-H) accounts.
- Fix for settings syncing with the Teams Admin Center and reset issues.
- Other bug fixes and improvements.

### December 2022

**Applies to:** *Teams app version - 1449/1.0.97.2022748302*

- Bug fixes.

### December 2022

**Applies to:** *Teams app version - 1449/1.0.97.2022747803*

- After an admin pairs a panel to a supported occupancy sensor through Device settings, you can see whether a room is occupied and auto check-in when check-in is enabled by your admin. If the room is available and someone's in the room, a message is displayed that the room is occupied. If the room is reserved but no one is in the room, you see a message that the room is unoccupied.
- Yealink's Room Sensor and Crestron CEN-ODT-C-POE are supported. For more information, check with your OEM.
- Support for Teams Shared Device License.
- Improvements and bug fixes.

### September 2022

**Applies to:** *Teams app version - 1449/1.0.97.2022739908*

- Improvements and bug fixes.
- Support for Microsoft Teams Rooms Pro Licenses.

### July 2022

**Applies to:** *Teams App version: 1449/1.0.97.2022739901*

- If you finish a meeting early, you can check out of the meeting room. This makes it available so others can reserve and use the space. Select **Manage** > **Check out**. If you need a few more minutes, if the room is free after your scheduled meeting time, you can extend your reservation for up to 15 minutes. Select **Manage** > **Extend room reservation**.
- This feature is turned off by default and requires the admin to enable the setting in the Teams admin settings. The setting to control this feature in the Microsoft Teams Admin Center will be available at a later time.
- A new Admin setting was added to disable room reservation from the panel. When the setting is enabled, a banner on the panel notifies people that the room can't be reserved with the Teams panels device.
- You can tap and pull down on a meeting tile to manually refresh the Teams panel calendar.

### April 2022

**Applies to:** *Teams App version: 1449/1.0.97.2022733702*

- New warning when a room reaches max capacity. This requires pairing the panel to a Teams rooms device (currently supported on Teams Rooms on Android with app version 1449/1.0.96.2022011305 or later) that supports people counting. This can be enabled in admin settings. To learn more, see How to use Microsoft Teams panels.
- New calendar look to help you quickly see a room's availability.
- View a list of equipment available on a panel. Admins must enable this setting in the Device Teams Admin settings, then turn on the setting per device. Admins can use the following instructions to make sure that devices are properly to display available resources: [Set-Place](/powershell/module/exchange/set-place) and [Manage resource mailboxes in Exchange Online](/exchange/recipients-in-exchange-online/manage-resource-mailboxes).

### February 2022

**Applies to:** *Teams app version: 1449/1.0.97.2022730007*

- To help ensure your meeting spaces are getting maximum use, we're enabling a way to check in to claim a room from a Teams panel. Users can check into the room by tapping the "check in" button on the panel. If no one checks into the room, it's released back to the room inventory for others to reserve and use.
- When paired with a Microsoft Teams Rooms on Android, joining a meeting from the Teams Room is considered as checking in and the room won't be released (it requires the Teams Room on Android app version 1449/1.0.96.2022011305 or above). Support with Teams Rooms on Windows will be available at a later time.
- The room check-in notification provides the end user with the ability to check in to their meeting when the panel is paired with a Teams Rooms on Android. After the user checks in, when the scheduled meeting starts and the previous meeting is running over, a notification appears on the Teams Room front-of-room display to inform the in-room participants their meeting is over and people are waiting for the space. This feature will be initially available on Teams Rooms on Android (it requires Teams app version 1449/1.0.96.2022011305 or above) and will be available on Teams Rooms on Windows at a later date.
- Calendar layout update to combine consecutive available time slots into one time slot.
- The calendar layout is updated to combine consecutive available time  slots from an hourly view into a single time slot. For example, the 12-3 PM time slot is combined into a single time slot to improve readability.
- Wallpaper refresh.
- The preset wallpapers have been refreshed in this app release to align with our Teams devices family.

### August 2021

**Applies to:** *App version: 1449/1.0.97.2021070601*

- Teams Extensibility and Line of Business (LOB) app support to tailor the Teams panels experience.
- IT Admins can do remote provisioning and remote sign in of Teams panels from the Teams Admin Center.
- Hide meeting names for sensitive spaces. This setting is off by default (the **Show meeting names** setting is on). The tenant admin can enable it through **Settings** > **Device settings** > **Admin Settings** > **Panels App Settings** > **Meetings** > **Show meeting names**. When meeting names is turned off, the meeting name is replaced with the meeting organizer's name.

## [Teams phones](#tab/phones)

## May 27, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025042103 (Yealink MP52, Crestron UC-Px, UX-Px-I, UC-2 and Audiocodes C488HD, C450HD)*

- Authentication token and back-end calendar fixes 

This update also includes these features, which were already available for certified Teams Phones:

- Copilot-generated summaries for call transfers

- Line Keys for Shared Line, Collaborative call delegation, Call queues and Call transfers

- External Contacts Management

- Line keys on touch, non-touch and sidecar devices for speed dials

- Queues app 

- Shared line call history 

- App pinning on home screen using dedicated settings 

- Collaborative call delegation 

- Multi-banner updates 

- Critical bug fixes and improvements 

For a detailed and comprehensive list of capabilities available for these device models, review release notes after December 18, 2024 until May 27, 2025.

## May 26, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025165302 (Poly, Yealink and Audiocodes)*

- Copilot-generated summaries for call transfers: This feature provides agents with a copilot-generated summary of the call before transferring it. The summary includes key details such as caller information, call reason, prior actions, and next steps. Supports both consult and blind transfers, ensuring effective communication and improved efficiency. *Pre-requisite:* This feature requires an additional license when available in GA: M365 Copilot. Visit here for more details: [License options for Microsoft 365 Copilot](/copilot/microsoft-365/microsoft-365-copilot-licensing). Transcription needs to be enabled in Calling policies for both transferor and transferee.  

- Line Keys for Shared Line, Collaborative call delegation, Call queues and Call transfers: Line keys are now available for shared lines on Teams certified phone devices. Users can assign shared lines to a line key and view the boss/delegates and members of the group along with their presence. Delegates can pick up calls on behalf of the boss or group members by pressing the line key and join active calls. This is also supported for collaborative call delegation groups. Users can also now assign call queues to a line key and monitor their status if the call queue has an active ongoing call or is available. Users can pick up calls on the call queue by pressing the line key. Additionally, users can assign the transfer action to the line key, enabling them to transfer active calls to specific contacts by simply pressing that line key. This will also be supported on sidecars now, in addition to automatic syncing of speed dials, groups and shared line delegates users can now explicitly assign line keys. 

- External Contacts Management: This feature allows users to add and edit external contacts using the lightweight People app on Teams phone devices. Users can manage and interact with contacts outside of their organization.

- App also includes multiple bug fixes and improvements. Bug fixes impacting user experience are:

  - Fixed an issue where the count of enabled Call Queues was not displaying on the Queues App
  
  - Fixed an issue where the delegate of a selected boss was not appearing under the Delegates tab
  
  - Addressed a UI issue where the Search and Dial Pad icons appeared too small under the Speed Dial, Transfer, and Consult Transfer sections of the Assign Line Key page
  
## May 5, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025087003 (Poly, Yealink and Audiocodes)*

> [!IMPORTANT]
> Starting in June 2025, Teams applications that are older than five (5) months will no longer work be able to connect to the service. Refer to the Message Center Post, MC969451 for more details.

- Bug fixes for caller name resolution in certain scenarios, improvements for Multi-Factor Authentication using Device Code Flow (DCF) wherein user account name can be used to sign-in. 

- UI fixes for end call screen. Users will see a toast notification instead of a full screen view when a call ends. 

## March 28, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025084203 (Poly, Yealink and Audiocodes)*

> [!IMPORTANT]
> Starting in June 2025, Teams applications that are older than five (5) months will no longer work be able to connect to the service. Refer to the Message Center Post, MC969451 for more details.

> [!NOTE]
> This update introduces a new versioning format, moving away from using dates. Going forward, this format will be used **1449/1.0.94.*year of release.internal codes***

- This app is available for government clouds (GCCH and DoD).

- Line keys are now available on touch phone devices. They will appear as an app on the home screen alongside other apps such as Calls, People, Calendar, and more. Users can assign speed dials by long pressing. For assigned contacts, users can manage and remove assignments by long pressing as well. Once assigned, outgoing calls can be placed to speed dials by pressing the line key. Additionally, the line key app can now be pinned, making it the default view on the home screen.

> [!NOTE]
> This experience isn't applicable to sidecars and ONLY includes experience on the Teams app running on touch phone devices.

   ![Screenshot home screen.](media/phones-release-notes-1.png)

- Shared line history is now available on phone devices. With shared line history, a delegate can now view call history of the entire shared line in the “Shared line appearance” app. A delegator/boss can view call history of the entire shared line on the Calls app.  

- You can now pin apps of your choice to your home screen using settings named “Home screen”.  This is only available for touch phones.

App also includes multiple bug fixes and improvements. Bug fixes impacting user experience are:

- AOSP migration and back-end calendar fixes.

- With this release, you will be able to resume held calls using a single entry.
- Joining a meeting via dial-info on calendar is now fixed.
- Deleted groups from People app will now sync across clients.
- For non-touch phone devices, the Resume button will now be one of the four keys below the display. It can be triggered using the corresponding hard key on the device.
- Issue on walkie talkie app and Teams channel is fixed.
- Fixed auto-dial issue on emergency calls for non-touch devices.
- Fixed issue on blind transfer for non-touch devices.
- For Advanced calling experience on common area phones, issue on “Default to home screen” setting is fixed.

## February 25, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025021303 (Poly, Yealink, AudioCodes)*



- Back-end telemetry fixes and improvements  
- App is available for government clouds (GCCH and DoD). 

## February 11, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2025020301 (Poly, Yealink, AudioCodes)*

> [!IMPORTANT]
> Starting June 2025, Teams applications older than 5 months will no longer work. Refer to the Message Center Post, MC969451 for more details.

Bug fixes including improvements in font rendering on side cars among others   

Contacts on Teams app and sidecar will now be sorted alphabetically

### January 8, 2025

**Applies to:** *Teams app version: 1449/1.0.94.2024122303 (Poly, Yealink, AudioCodes)*

> [!IMPORTANT]
> Starting June 2025, Teams applications older than 5 months will no longer work. Refer to the Message Center Post, MC969451 for more details.

##### Queues app

We're excited to announce the Queues app for desk phones, a Teams solution that empowers organizations to efficiently manage customer engagements, starting with calls on certified Teams Phones. The experience is primarily for agents and includes a dedicated Queues app on the home screen. This app allows agents to view and opt in or out of all the call queues an agent is part of. Agents can also view others on the line along with call history of the call queue.

> [!NOTE]
> - The Queues app is enabled by default for all Teams users in your organization who are assigned both a Teams Premium and Teams Phone license and who are voice enabled. To learn more about managing the Queues app, see [Manage Queues app for Microsoft Teams](../manage-queues-app.md).

##### Collaborative call delegation

Circular delegation now allows users to share lines with each other as a group on Teams Phone devices. This feature is useful for scenarios where multiple users need to manage shared lines. In a typical circular delegation setup, User A delegates to User B, and User B delegates to User A, allowing them all to share the line with each other. This setup can be configured using cmdlets because the Teams client and Teams Admin Center don't currently support this feature.

##### Multi-banner updates

The multiple-banners feature improves the user experience by managing notifications more effectively on phone devices. When users receive multiple notifications, the system allows users to collapse all notifications or clear them in bulk, providing a cleaner and more organized interface.

### December 18, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024121004 (Poly, Yealink, AudioCodes)*

- This app is also available for government clouds (GCCH and DoD).

- Bug fixes related to transfer flow, among other issues.

### December 18, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024063004 (Yealink T5x/CP960, AudioCodes C488HD/450HD, Yealink MP52/VP59, Crestron UC-P8/ UC-P8-C/ UC-P10/ UC-P10-C/ UC-2)*

- Banner notifications to inform users about their device support coverage status.

### December 10, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024112802 (Poly, Yealink, AudioCodes)*

- Bug fixes on lock screen, password expiration, LED issues on nontouch devices, among others, are included.

### November 25, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024062906 (Yealink - T5x, CP960, MP52, VP59; AudioCodes - C488HD/450HD, Crestron -UC-P8x, UC-P10x, UC-2)*

- Bug fixes on several minor issues reported by customers.

### November 13, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024103101 (Touch phones - AudioCodes, Poly, Yealink)*

- Bug fixes and improvements to line keys, calls, and Enhanced 911 calls, among others.

### October 29, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024101709 (Yealink, Poly, AudioCodes)*

Today, on Teams Phone devices, you're able to configure custom contacts and speed dial on-the-line key buttons on nontouch phones and sidecars phone devices certified for Microsoft Teams. You can quickly access frequently dialed numbers and contacts, using one-touch dialing, as well as easy management of contact lists on both line keys and sidecars.

:::image type="content" source="media/new-in-microsoft-teams-devices/nontouch-linekeys-empty.png" alt-text="Screenshot showing how to assign phone lines and Teams desk phones.":::

- Bug fixes and improvements on live captions.
- Privacy link updates for recordings and transcription.

### October 1, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024092304 (Yealink, Poly, AudioCodes)*

- Bug fixes and improvements on contacts sync, presence, and transfer flows, among others.

### September 5, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024082806 (Yealink, Poly, AudioCodes)*

- Enhancements in the call parking and retrieval feature to make both faster.
- Lightweight calling experience on nontouch phones.
- Bug fixes and improvements for compliance, recording scenarios, and other issues.

### September 3, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024062811 (Yealink T5x, CP960 & Poly Trio 8800/8500)*

- Bug fixes and improvements for end-of-certification and end-of-best-effort support phones.

### August 27, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024062702 (Yealink T5x, CP960 & Poly Trio 8800/8500)*

- To support incoming call notifications and voicemail, migrate end-of-certification and end-of-best-effort support phones from the discontinued call-notification service to the new notification service.

This update also includes these features, which were already available for certified Teams Phones:

- Improvement was made to show caller information on incoming emergency call notification.
- The date-time format specified under Device Settings is the same on the home screen.
- When the **Explicit Recording Consent** policy is enabled, audio conference phones support auto consent.
- The Public Switched Telephone Network (PSTN) calling issue on the new shared-line-appearance experience is fixed.
- When there are fewer than four apps on a given account, they appear on the home screen instead of being hidden under the More menu.
- Caller ID now shows incoming PSTN calls on call queues.
- You can now continue dialing a number when there's an incoming call.
- When ending a call or turning off your speaker, you won't be navigated to the home screen. Instead, you can continue from the previous screen.
- A new back button was introduced on the calling screen so you can easily navigate away from an ongoing call.
- View and join active calls handled by delegates as a delegator.
- Grant delegates permission to join active calls and resume calls.
- A delegate can view shared call history per a delegator's line, easily switch between different lines, and view other delegates managing a line.
- The presence on the device and sidecar gets updated in near real time.
- Live captions are supported on PSTN calls.
- You can program Teams Phone devices to autodial a preconfigured PSTN number, or directory contact, when the handset is picked up. You can configure a common-area phone as a hotline phone by navigating to **Settings** > **Device Settings** > **Calling** > **Hotline**, and specifying the autodial contact and display name.
- A redesigned dial pad helps reduce unnecessary mistakes while dialing a phone number. It offers a new dial-pad-only view in large-screen landscape phones.
- Simplified navigation improves the performance and reduces page-navigation time by replacing the bottom navigation bar with a new home screen navigation experience. You can easily go to the home screen from any app and navigate to different apps from the home screen. You can also use **More** to reorder apps.
- The user experience on the calls app and sidecar was made lighter weight to improve performance.
- Date and time are now displayed on the title bar across apps.
- Support added for reverse number lookup of PSTN numbers on call-queue calls.
- The issue of autodialing on a partially entered number is fixed.
- Option to sign out on common area phones. Advanced calling experience requires an admin PIN.
- Lighter weight meeting reduces the time it takes users to get connected to a meeting on selecting **Join**.
- Support added for reverse number lookup of PSTN contacts added via the Teams desktop.
- Performance of the phones attached to expansion modules is improved.
- The "Resume call" reliability is improved on consult transfer.
- Audio conferencing isn't supported on Teams Phone devices with the Meeting Teams Room Basic license.
- You can add and edit your emergency location on phones.
- Emergency service disclaimers specified by admins in the Teams Admin Center (TAC) as part of emergency policy is shown on the desk phones.
- Busy-on-Busy when users are in a call setting enabled by admins in TAC will be honored on phone devices (excluding the User-controlled option).
- Admins can configure app restart settings from TAC for optimal phone performance (not currently available for Government cloud accounts).
- Record one-on-one PSTN calls.
- License enforcement.
- Faster call joining.

### August 16, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024080808*

- Bug fixes and improvements on transfer scenarios, contacts, among others, are included.

### July 16, 2024

**Applies to:** *Teams app version -1449/1.0.94.2024071104*

- This app is available for government clouds (GCCH and DoD).
- **Updates on user experiences** We changed the default home-screen experience for the meeting sign-in mode. It's now like the personal sign-in mode experience. Additionally, updates to remove the dial pad on the Calls app for touch phones with physical buttons.
- **Explicit Consent for Recording**  Users see a notification on Teams Phone devices when a participant starts recording or transcription, asking for participant consent. This feature is turned off by default but can be enabled by admins. Admins can turn on this policy for users in your tenant by clicking on the highlighted switch on "Require participant agreement for recording, transcription, and Copilot."

  :::image type="content" source="media/new-in-microsoft-teams-devices/recording-and-transcription.png" alt-text="Screenshot showing the option to require participant agreement for recording transcription." lightbox="media/new-in-microsoft-teams-devices/recording-and-transcription.png":::

- **Private Line**  The Private Line feature allows bosses to have a second private phone number on their Teams device, ensuring privacy for important calls. These calls are distinct in the call history. To learn more, see Configure private lines in Microsoft Teams.
- **Lightweight People App**  The updated People app provides a faster and simplified experience for managing contacts, allowing users to switch between different contact lists and to create contact groups.

- **Rich Call History**  Call-history updates include better logging for ignored, missed, and forwarded calls, with clear labeling for different call types.
- **Call Transfer Improvements**  Improvements to call transfers include viewing a list of speed dials during transfer, and better handling of keyboard overlap on touch phones. Also, for phones that don't have touch screens, there are improvements to finish transfers using call-transfer hard keys on phones.

### July 5, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024062301 (AUDC: C448HD, C450HD. Yealink: MP52, VP59. Crestron: UC-2, UC-P8, UC-P10, UC-P8-C, and UC-P10-C)*

- Intermittent issue on meeting join while using Better Together is fixed for touch phones
- Intermittent issue on a device getting locked out is fixed for nontouch phones.
- Issue of remote user not hearing music while on hold in nontouch phones is fixed.
- Fixes for authentication issues, including a fix for sign-in failures immediately following signing out.
- Issue of pin lock appearing when disabled is fixed.

### July 3, 2024

**Applies to:** *Teams app version - 1449/1.0.94.2024062010 (touch phones: AudioCodes, Poly, Yealink. For nontouch phones: AudioCodes C435, Poly CCX350)*

- Bug fixes and improvements on the enforce pin-lock feature.
- This app is also available for customers in government clouds (GCCH and DoD).

### June 18, 2024

**Applies to:** *Teams app version - 1449/1.0.94.2024061301*

- Minor updates in the people and calls apps.
- Bug fixes and improvements.

### June 4, 2024

**Applies to:** *Teams App version: 1449/1.0.94.2024051306 (Touch phones - AudioCodes, Poly, Yealink)*

- Bug fixes for crash issues.

### May 21, 2024

**Applies to:** *Teams App version: 1449/1.0.94.2024051306 (Nontouch phones - Poly CCX350, AudioCodes C435HD)*

- You can park and unpark a call.
- You can turn on the Advanced Calling and Auto Restart settings.
- You can add contacts and contact groups.
- Admin's can turn on call forwarding on home screens via **Teams Admin Center** > **Configuration** > **Display call forwarding on home screen**, allowing Teams Phone device users to setup call forwarding directly from their home screens.
- Admin's can turn off call-quality serveys on Teams Phone devices from **Teams Admin Center** > **Configuration**, and by turning off **Call quality survey**.

  :::image type="content" source="media/new-in-microsoft-teams-devices/turn-off-call-serveys.png" alt-text="Screenshot showing the option to turn off call quality serveys on Teams Phone devices." lightbox="media/new-in-microsoft-teams-devices/turn-off-call-serveys.png":::

- Send incoming calls to voicemail from the incoming call screen (configurable by calling a policy through PowerShell). You can control how you want to handle a secondary incoming call through the Busy-on-Busy setting (configurable by calling a policy in the Teams Admin Center).
- When a contact has multiple numbers, you can choose which one to call.
- People can control how they want to handle second incoming calls through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-Busy setting by selecting **Let users decide** in **Teams Admin Center** > **Calling policy**.

  :::image type="content" source="media/new-in-microsoft-teams-devices/how-to-handle-second-incoming-calls.png" alt-text="Screenshot showing how users can handle second incoming calls." lightbox="media/new-in-microsoft-teams-devices/how-to-handle-second-incoming-calls.png":::

### May 5, 2024

**Applies to:** *Teams app version: 1449/1.0.94.2024042905 (Touch Phones - AudioCodes, Poly, Yealink)*

- Send incoming calls to voicemail from the incoming call screen.

  :::image type="content" source="media/new-in-microsoft-teams-devices/incoming-call-screen.png" alt-text="Screenshot showing the incoming call screen.":::

> [!NOTE]
> Admins can control rollout of this option on selected accounts by configuring the AllowCallRedirect parameter in the Teams calling policy associated with the account: `PS C:\WINDOWS\system32> Set-CsTeamsCallingPolicy -Identity Global -AllowCallRedirect Enabled`

- People can control how they want to handle a second incoming call through the Busy-on-Busy setting. Admins can allow people to configure the Busy-on-Busy setting by selecting **Let users decide** in **Teams Admin Center** > **Calling policy**.

  :::image type="content" source="media/new-in-microsoft-teams-devices/busy-on-busy-setting.png" alt-text="Screenshot showing the Busy-on-Busy setting.":::

  :::image type="content" source="media/new-in-microsoft-teams-devices/busy-on-busy-let-users-decide.png" alt-text="Screenshot showing the Busy-on-Busy setting that lets users decide." lightbox="media/new-in-microsoft-teams-devices/busy-on-busy-let-users-decide.png":::

- Admins can allow call the forwarding option on home screens via **Teams Admin Center** > **Configuration** by turning on **Display call forwarding on home screen.** The same setting can be configured on the phone device. This allows people using a device (including common-area phones) to set up call forwarding directly from their home screen.

> [!NOTE]
> These features will be rolled out gradually.

- Admins can notify people to set or change their phone lock PIN by enabling a configuration profile setting in Teams Admin Center. They can also lock the phone device via the menu on home screen.

> [!NOTE]
> These features will be rolled out gradually.

- Survival Branch Office (SBA) will be supported on Voice over Internet Protocol (VoIP) calls.
- Admins have the option of disabling call-quality surveys on Teams Phone devices from **Teams Admin Center** > **Configuration**.

  :::image type="content" source="media/new-in-microsoft-teams-devices/disabling-call-quality-surveys.png" alt-text="Screenshot showing how to disable call-quality serveys." lightbox="media/new-in-microsoft-teams-devices/disabling-call-quality-surveys.png":::

> [!NOTE]
> These features will be rolled out gradually.

- The issue of Better Together on the new Teams desktop app is fixed.
- After consult transfer, the issue of an ongoing call going to the banner for the remote caller is fixed.

### March 15, 2024

**Applies to:** *Teams App version: 1449/1.0.94.2024031102 (Yealink, Poly, AudioCodes)*

> [!NOTE]
> For AudioCodes phones, this app update applies to firmware version 1.19.705.

- Improvement to show caller information on incoming emergency call notification.
- Issue of not ending hot-desk on timeout is fixed.
- Issue of showing an incorrect call-recording string and a localized calling string is fixed.
- Issue related to the hard-key hold button is fixed.

### March 12, 2024

**Applies to:** *Teams App version: 1449/1.0.94.2024011601, 1449/1.0.94.2024020601 (AudioCodes)*

> [!NOTE]
> The update applies to AudioCodes phones on firmware version 1.19.516 or higher.

- Significant reduction in sign-out and authentication errors due to Workplace Join failures, timeout issues, and memory leaks.

### January 24, 2024

**Applies to:** *Teams App version: 1449/1.0.94.2024011003 (Poly, Yealink, Crestron, AudioCodes)*

- The issue of active call moving to banner on merging a call is fixed.
- The issue of consult transfer icon not being clickable sometimes is fixed.

> [!NOTE]
> This update applies to AudioCodes phones on firmware versions 1.19.456 and earlier.

### December 5, 2023

**Applies to:** *Teams App version: 1449/1.0.94.2023112704 (Crestron, Poly, Yealink)*

- The date and time format specified under **Device Settings** is the same on the home screen.
- When the **Explicit Recording Consent** policy is enabled, audio conference phones support auto consent.
- The PSTN calling issue on the new shared line appearance experience is fixed.
- When there are fewer than four apps on a given account, they appear on the home screen instead of being hidden under the **More** menu.

### November 28, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023111407 (AudioCodes)*

> [!NOTE]
> This update applies to AudioCodes phones on firmware version 1.19.584.

- Improvements to reduce issues with workplace join authentication.

### November 6, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023100602 (AudioCodes)*

> [!NOTE]
> This update applies to AudioCodes firmware version 1.19.584 and is available for phones previously on firmware version 1.19.516. A Teams app release for AudioCodes phones currently on other firmware versions will be released soon.

- Enhanced call-delegation experience, faster presence update in the app, and live captions on PSTN calls. For a list of call-delegation updates, see the August 29, 2023, update.

### October 9, 2023

**Applies to:** *Teams App version: 1449/1.0.94.2023091801 (Yealink)*

- Caller ID shows for incoming PSTN calls on call queues.
- You can continue dialing a number when there's an incoming call.
- When ending a call or turning off your speaker, you won't be navigated to the home screen. Instead, you can continue from previous screen.
- A new back button on the calling screen which allows you to easily navigate away from an ongoing call.

### August 29, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023082303 (Crestron, Poly, and Yealink Audio Touch Phones)*

Today, on Teams Phone devices, delegators can share their phone line with their assistants and delegates to make and receive calls on their behalf. Call delegates can also:

- View and join active calls handled by delegates, as a delegator.
- Grant delegates permission to join active calls, and resume calls.
- View shared call history, per the delegator's line.
- Easily switch between different lines.
- View other delegates managing a line.
- The presence on the device and sidecar is updated in near real time.
- Live captions are supported on PSTN calls.
- The issue of resolving caller ID on call-queue calls is fixed.
- The issue of showing the "Add location" banner when the emergency policy "External location lookup mode" is turned off is fixed.

### July 31, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023072509 (AudioCodes, Crestron, and Poly audio phones)*

- You can program Teams Phone devices to autodial a preconfigured PSTN number or directory contact when the handset is picked up. You can configure a common area phone as a hotline phone by navigating to **Settings** > **Device Settings** > **Calling** > **Hotline** and specifying the auto-dial contact and display name.

> [!NOTE]
> To configure a phone as hotline phone, the logged in account on the phone device must have **Teams Shared Device License** assigned. **Sign In Mode** must be set to **CommonAreaPhoneSignIn**. The option to configure a hotline phone through the Teams Admin Center will be supported soon.

- Redesigned dial pad helps reduce unnecessary mistakes while dialing a phone number and offers a new dial-pad-only view in large-screen landscape phones.
- Simplified navigation improves performance and reduces page-navigation time by replacing the bottom navigation bar with a new home-screen navigation experience. You can easily go to the home screen from any app and navigate to different apps from the home screen. You can also use **More** to reorder apps.
- The user experience on the calls app and sidecar was made lightweight to improve performance.
- Date and time are now displayed on the title bar across apps.
- Support added for reverse number lookup of PSTN numbers on call-queue calls.
- The issue of autodialing on partially entered number is fixed.
- Option to sign out on common area phones. The advanced calling experience requires an admin PIN.
- Lightweight meeting reduces the time it takes users to get connected to a meeting by selecting **Join**.

### July 12, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023063003*

- Support added for reverse-number lookup of PSTN contacts added via Teams desktop.
- Performance of the phones attached to expansion modules is improved.

### June 15, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023060906*

- Audio Conferencing is supported on the Microsoft Teams Room Pro License.

> [!NOTE]
> When multiple licenses are assigned to a Teams Phone device account, configure IPPhonePolicy and SignInMode for the desired experience.

- Issue of displaying wrong caller information for incoming Auto Attendant Call Queue calls is fixed on nontouch screen phones.

### May 9, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023050205 (doesn't include TrioC60 on GCC-H cloud)*

- "Resume call" reliability is improved on consult transfer.
- Issue of persisting "Advanced calling" setting in common area phones when signing back in is fixed.
- The intermittent issue of an emergency location banner showing on the phone when "External location lookup mode" is disabled in the Teams Admin Center is fixed.
- Intermittent issue of badge notifications not clearing on the home screen is fixed.

### April 14, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023041203*

- Intermittent issue of the app restarting on F SKUs (frontline worker) and Business SKUs (SMB) is fixed.

### April 4, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023032903 (AudioCodes, Crestron, Poly)*

- Audio conferencing isn't supported on Teams Phone devices with the Meeting Teams Room Basic License.
- You can add and edit your emergency location on phones.
- Emergency service disclaimers specified by admins in the Teams Admin Center (TAC) as part of the emergency policy shown on desk phones.
- Busy-on-Busy when in a call setting enabled by admins in the Teams Admin Center is honored on phone devices (excluding the User controlled option).
- Admins can configure app-restart settings from the Teams Admin Center for optimal phone performance (not currently available for Government cloud accounts).
Record one-on-one PSTN calls
- Faster call joining.
- Issue of defaulting to alphanumeric characters on the Dialpad while dialing a number on Poly CCX 350 is fixed.
- Intermittent issue of boss not getting notification when delegates put a call on hold is fixed.
- Intermittent issue of screen freezing while in a call is fixed.

### February 21, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023020602*

- Dial tone and mute LED sync issue is fixed on audio-conferencing phones.
- Calling resiliency is improved.
- Intermittent issue around graying out of call controls is fixed.
- Intermittent issue around not being able to end calls is fixed.

### January 25, 2023

**Applies to:** *Teams app version: 1449/1.0.94.2023010607*

> [!NOTE]
> This update is for public cloud deployments and non-audio-conferencing phones.

- Reliability improvements around authentication.
- Showing detailed error messages around authentication.
- Call button display issue is fixed.
- Emergency notification issue is fixed.

### November 30, 2022

#**Applies to:** *Teams app version: 1449/1.0.94.2022110803*

- Fixes sign-in issues on nontouch devices.
- Fixes caller ID and caller display name issues.
- Fixes calling related issues on GCCH deployments.

### September 21, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022090705 (for nonvideo touch phones only)*

- Simplified look for incoming and outgoing calls with improved performance.

### July 14, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022062103*

- Several intermittent app-crash issues have been resolved.

### July 6, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022061702 (Crestron, Poly, Yealink)*

- We're enhancing the existing Common Area Phone offering to include all advanced calling features at no extra cost or changes to the original purchased license. Common Area Phone supports calling features including call park, call queues, auto attendants, Intune enrollment into Endpoint Manager, and more, when the device is updated to the minimum app version: 1449/1.0.94.2022061702.
- Emergency calling on GCC-H deployments is supported.

### April 13, 2022

#**Applies to:** *Teams app version: 1449/1.0.94.2022041102*

- Fixes missing names on phone sidecars.
- Fixes common-area phone dial pad and audio routing issues between the handset and speaker.
- Fixed issues occurring in the Teams Admin Center.

### March 24, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022030501*

- Support end-to-end encryption in one-on-one calls.
- Contact name along with phone number for saved contacts show on calls made via PSTN (Public Switched Telephone Network).
- Hold music during blind-call transfers and consultative-call transfers made via VoIP (Voice over Internet Protocol).
- Customize app restart time from **Settings**.

### March 3, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022022305*

- Resiliency added for location fetch mechanism on devices.

### February 7, 2022

**Applies to:** *Teams app version: 1449/1.0.94.2022020202*

- Teams Phones with touch screen have instant push-to-talk communication via the new Walkie-Talkie feature.
- Teams Phones with touch screen improvements for multiple incoming, held, and parked calls.
- Teams conference phones in portrait mode updates for better meeting experience.
- Performance enhancements for screen navigation and sidecar issues.
- Bug fixes for Teams Android devices showing as offline in Teams Admin Center.
- Bug fix to held calls when placing the handset back in the cradle.
- Known issues with ongoing calls when Walkie-Talkie calls interrupt.

### December 16, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021121302*

- More improvements in dial-pad experience for touch-screen phones.
- Improvements in dial-tone management.
- Improvements to audio routing when switching between handset and speaker.

### December 6, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021112302*

- More improvements in dial-pad experience for touch-screen phones.
- Improvements in dial-tone management.
- Improvements to audio routing when switching between handset and speaker.

### November 22, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021110101*

- Improvements in dial-pad and dial-tone experiences for touch-screen phones.

### November 3, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021101205*

- Admins can provision devices from the Teams Admin Center to remotely sign in and sign out from devices.
- Branch office survivability for Teams Phones to make PSTN calls even when the internet connection is down.
- Admins can download all (company portal, device management, and media) logs from the Teams Admin Center.
- Bug fixes related to authentication.
- Bug fixes preventing devices from going offline in the Teams Admin Center.

### June 10, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021052803*

- Performance updates for meeting experiences on low-end hardware.

### June 8, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021051303*

- Transfer a Teams call to another device without hanging up.
- Change your background during a video call or meeting from a set of pictures available in phones with video capability.
- Contacts whose numbers are saved in Outlook are available in the People section of Teams Phones with read-only access. You need to manually dial the number.
- Enforcement of authentication policies and tenant-based policies set by your admin. Login is blocked if the device doesn't meet the necessary policy requirements.
- During a call, select the active-call icon to show more options. Additionally, when a contact has multiple numbers saved, you can choose the number you want to dial from the dropdown list.
- To facilitate quick responses for autoattendant scenarios, dial pad is available for early media scenarios.
- Extending the live captions feature to calls, Teams detects what's said in a call and presents real-time captions in one-on-one calls.
- Ongoing enhancements to improve user experience when using a delegate on touch screens.
- Bug fixes for Link Layer Discovery Protocol (LLDP) for Enhanced 911 (E911) and authentication.

### March 30, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021033002*

- Fixed authentication library crash.

### March 26, 2021

**Applies to:** *Teams app version: 1449/1.0.94.2021022403*

- New and improved sign-in experience. Sign in from any browser or smartphone with a prominent device code. Or you can sign in from the device with your username and password.
- Sign-in support and authentication into specialized clouds is available. Choose the **Settings** gear on the sign-in page to see the options for your account.
- IT admins can remotely provision and sign in to a Teams device that's previously not been provisioned.
- Call controls now visible during meetings. You can also switch between Gallery and Together mode and send reactions during meetings.
- Teams devices connected to the network via ethernet will dynamically update location information for emergency calling services based on changes to network attributes, including chassis ID and port ID.
- On video phones, you can change your background during meetings and calls from a select set of images.
- Calling enhancements that improve the usability of touch screens.
- All phone numbers that are part of meeting invites, or from a person's contact card, can be dialed by selecting them on screen.
- Directly transfer a call to someone's work voicemail without ringing them.

### December 8, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020111101*

- Video features including 3x3 layout support, gallery view and together mode, background blur, and spotlight.
- Meeting features including request-to-speak and the ability to view screen sharing on select models of audio phones.
- Proximity joining on conference phones.
- Beta release for Sidecars on AudioCodes and Yealink phones.
- Meet-now button on phones.
- Policy support for enabling and disabling home screen and syncing a phone to a computer.
- Support for M365 Government (GCC deployments).

### October 12, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020091801*

- Better-together feature with meeting support.
- Bug fix related to authentication after signing in.
- Bug fix related to device automatically signing out after 90 days.

### August 31, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020071702*

- Home screen shows meeting reminders.
- Ability to customize default apps in the phone and the default view in Calls.
- Support for a Teams button on specific phone models.
- Enable auto accept with video for prescheduled meeting requests.
- Sign-in enhancements with the Company Portal application.
- Bug fixes to the Teams application and the Device management admin-agent application.

> [!NOTE]
> If the phone is stuck on the "Verifying a few things" screen, try turning the phone off and on again.

### June 27, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020051601*

- Contacts and contact groups management in People.
- Live captions for meetings.
- Raise virtual hand in meetings.
- Transfer directly to speed dial.
- Connect to computer for simultaneous lock and unlock.
- Auto dismiss for a call ended and rate-my-call screens.
- Network banner at the top of screen to show network loss.
- Bug fixes to the Teams application and the Device management admin-agent application.

### April 23, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020031901*

- Favorites (speed dial) added to Calls.
- New settings support on Teams Phones for: Custom ringtone, Manage Delegates, and auto dial for extension dialing.
- Device-management updates to support device categorization in Teams Admin Center.
- Bug fixes to the Teams application and the Company Portal application.

### February 18, 2020

**Applies to:** *Teams app version: 1449/1.0.94.2020020601*

- Support for dynamic emergency calling on the phone lock screen.
- Hot-desk feature bug fixes to address network-outage scenarios.
- Sign-in improvements.
- Device-management bug fixes to address firmware version reporting.
- Bug fixes to the Teams application.

## [Teams displays](#tab/displays)

> [!IMPORTANT]
> End of certification for Teams display devices is September 3, 2025. Microsoft will make commercially reasonable best efforts to maintain compatibility with the most recent version of the Teams apps provided to manufacturers for a period of two (2) years from this date. For details, see the [Microsoft Product and Services Lifecycle](/lifecycle/products/).

### September 2024

**Applies to:** *Teams app version: 1449/1.0.95.2024062804*

- Bug fixes.

### November 2023

**Applies to:** *Teams app version: 1449/1.0.95.2023101102*

- Support for QR code sign in for scenarios without reserving the hot desk.
- Improvements to support meeting continuity through hot-desk reservation end times.
- UI and layout enhancements to the hot-desk ambient and display screen.
- Bug fixes and other enhancements.

### June 2023

**Applies to:** *Teams app version: 1449/1.0.95.2023061601*

- Streamlined experiences on Teams-certified displays based on assigned licenses.
- Bug fixes and improvements on meeting and calling experiences.

### May 2023

**Applies to:** *Teams displays app version: 1449/1.0.95.2023042701*

> [!NOTE]
> This release is an app-only update. Work with device manufacturers to confirm timelines on full feature functionality on your devices.

- QR code sign in on Teams-certified displays for hot-desking. All Teams Displays with hot-desking capability allow people to sign in using a QR code for a reserved time slot. This feature is enabled by default and can be disabled under **Device settings** > **Admin settings** > **Meetings**. While hot-desking, you can seamlessly sign in to the Teams display during your session by scanning a QR code using the Teams app on your mobile phone.

The recommended version of Teams on your Android phone is 1416/1.0.0.2023092901 and above. On iOS, the recommended version is 5.9.1, it's (100772023093201), and above.

> [!NOTE]
> The following instructions are for those who use an Android mobile phone with an Android work profile (AWP).

- You can scan a QR code using the camera app on your Android mobile phone. However, the sign-in might not work if you have both work and personal profiles on their Android phones. If so, you need to add a mobile system OS scanner in your work profile.

To add a mobile system OS scanner:

1. In the Intune Admin Center go to **Apps** > **Android**, and add.

2. Select **Android enterprise system app**.

3. Enter the type of Android phone, Google, and paste OS camera package name.

4. Assign it to an individual or group.

5. Download and install the camera app from the app store in your work profile.

- **Virtual front-desk experience on Teams-certified displays**  The Virtual front desk enables staff to greet and serve visitors or employees via video call on a Teams display. It can be used for virtual reception, helpdesk, and various use cases across industries. IT admins can easily configure the Virtual front desk with contact and routing information. This feature is available on Teams certified displays on the Teams Shared Devices License. Recommended for accounts without CA policies.
- Admins can now customize the message on display screens and the call button, in addition to configuring a PSTN or VoIP contact on the device itself via **Settings**. They can also use Teams advanced calling capabilities such as call transfer, call forwarding, call queues, etc., if enabled for the configured contact account.
- Improvements to handle multi-call banner scenarios and to ambient UI.
- Bug fixes and improvements.

### January 2023

**Applies to:** *Teams app version: 1449/1.0.95.2023011001 (Crestron)*

- Fix for intermittent app crashes occurring in the previous app update (1449/1.0.95.2022102603) for Crestron devices.

### December 2022

**Applies to:** *Teams app version: 1449/1.0.95.2022120505 (Neat Frame)*

- Hot desking in portrait mode is  supported. Hotdesking on a Teams display makes finding a space to work easier by allowing you to locate and reserve flexible workspaces.
- Teams Shared Devices License on Teams displays offers hot desking experience. The Teams IP Phone policy setting for hot desking is disabled for displays. You can invoke hot desking using Teams accounts with the Teams Shared Device Licenses.
- Bug fixes and improvements for app crashes.

### November 2022

**Applies to:** *Teams app version: 1449/1.0.95.2022102603 (Crestron)*

- Teams Shared Devices License on Teams displays offers a hot-desking experience. The Teams IP Phone policy setting for hot desking is disabled for displays. You can invoke hot desking using Teams accounts with the Teams Shared Device Licenses.
- Bug fixes and improvements for app crashes, reliability of muting and unmuting your microphone during a call, and more.

### December 2021

**Applies to:** *Teams app version: 1449/1.0.95.2021111203*

- Teams displays support portrait mode for all calling and meeting screens. Meeting layouts are optimized for portrait videos of individual people. All incoming videos always fit-to-frame when the device is used in portrait orientation.
- Teams displays enabled live event attendee view to allow producer and presenter to join with a quick join link. They have the same capability in displays as in the Teams mobile app. The attendee can access the live event with the event link provided in the calendar details.
- Organizers, presenters, and attendees have the webinar invite on calendar, and can join directly from the calendar event through the **Join** button, which appears on the event when it's about to start.
- The following Teams display settings moved under **Teams Admin Settings** while using a shared account: calling, sign out, and wallpaper.
- Teams displays have the ability to use end-to-end encryption for calls (must be enabled by IT admin).
- IT admins can remotely provision, sign in, and sign out of a Teams device that has previously not been provisioned.

### June 2021

**Applies to:** *Teams app version: 1449/1.0.95.2021042103*

- Contact phone numbers created in Outlook are available in the People section of Teams displays with read-only access.
- During a call, select the active-call icon to show more options. Additionally, when a contact has multiple numbers saved, you can choose the number you want to dial from the dropdown list.
- Choose a background for your video calls and meetings from a select set of images in Teams.
- Extending the live-captions feature to calls. Teams can now detect what's said in a call and present real-time captions in one-on-one calls.
- On Android devices, presenters can control a participant's camera and mic. Participants no longer need to use Raise hand to request to be unmuted.
- New wallpaper images.
- Bug fixes related to authentication.

### March 2021

**Applies to:** *Teams app version: 1449/1.0.95.2021021104*

- Sign in from any browser or smartphone with a device code. Or sign in from the device with a username and password directly on the device.
- Call controls are docked at the bottom of the screen. You can also switch between gallery and together mode views and send reactions during meetings.
- Producer, presenter, and attendee can join live events as attendees on Teams displays. Producer and presenter can join the live event through the ****Join button in the calendar. Everyone else can join through the attendee link shared in a Teams channel, chat, or on the invite details tab.
- Change your background during meetings or calls from a select set of images.
-All phone numbers that are a part of a meeting invite or a person's contact card can be dialed directly by tapping on them.
- Directly transfer a call to someone's work voicemail without ringing them.
- Zero calendar events page is displayed for days with no meetings.
- Dots on dates are displayed for days that have meetings.
- Send reactions from the ambient screen.
- Suggested replies to messages from the ambient screen.
- Call someone back from the ambient screen after you miss their call.
- Indicator of important and urgent messages on the ambient screen.
- Notification badges on the home icon indicate that there are new notifications coming in when in another app on the device.
- Sent messages are displayed in your notifications.
- Set quiet hours for notifications.
- Ask Cortana and get answers to questions about topics such as current weather, calculations, currency conversions, language translations, and time conversions.
- Cortana voice support expanded to new English locales: United Kingdom, Canada, India, and Australia. Use your voice to join meetings, make phone calls, send messages, and check your schedule.
