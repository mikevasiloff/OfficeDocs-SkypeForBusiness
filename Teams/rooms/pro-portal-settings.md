---
title: Managing Teams Rooms on Windows settings
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 5/12/2025
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ai-usage: ai-assisted  
ms.localizationpriority: medium
search.appverid: MET150
description: This article provides guidance on how to manage your Teams Rooms on Windows devices. It outlines the application settings that can be applied directly on the device and synchronized with the Teams Rooms Pro management portal, or alternatively, configured from the Teams Rooms Pro management portal to the device.
---

# Managing Microsoft Teams Rooms on Windows devices

In the Microsoft Teams Rooms Pro management portal, you can configure application settings for individual Teams Rooms on Windows devices, provided you have the necessary role-based access control permissions for Rooms Management. For more information, see [role-based access control in the Microsoft Teams Rooms Pro Management portal](/microsoftteams/rooms/rooms-pro-rbac).

## How it works

Teams Rooms devices have application settings that can either be applied on the device and synchronized with the Teams Rooms Pro management portal, or applied from the Teams Rooms Pro management portal to the device.

In the Teams Rooms Pro management portal, certain Teams Rooms application settings can be changed from the **Rooms detail settings** pane. Applying these changes require restarting the Teams Rooms application on the device to apply the setting change.

The Microsoft Teams Rooms on Windows application uses a SkypeSettings.XML configuration file to manage application settings on the device. When settings are changed on the device, a synchronization task updates the Teams Rooms Pro management portal settings for that device.

> [!Note]
> Synchronization may take up to 15 minutes to reflect the changes.

## Changing settings

After changing a setting and pressing the **Apply** button, a dialog box will present two options:

- **Apply Now** - Queues a job to apply the setting and restarts the device as soon as possible to apply the setting changes. This process can take several minutes. A banner is displayed to indicate that a settings change has been initiated, along with the number of settings changes jobs that are queued. 
- **Schedule Later** - Schedules the settings change to be applied during the nightly maintenance window to avoid disrupting scheduled meetings during business hours.

> [!Note]
> The **Apply Now** option won't be available for devices actively in use.

## Settings job history

Since setting changes from the Teams Rooms Pro management portal to the Teams Rooms device aren't in real-time, there will be a delay. An indicator is visible next to any setting that is pending a change or pending verification of a change as a visual cue that a job is in progress for that device.

To provide visibility to the Teams Rooms Pro management technician, there's a **Settings Job History** activity under the **Activity** tab on the Rooms detail panel. This indicates the stage of settings change.

An entry is made for every setting change initiated by a user or by the Teams Rooms Pro management service.

|**Field name**|**Description**|
|:------|:------|
|Status|Indicates the stat of the settings job.|
|Submitted on|Indicates the timestamp of the status of the job.|
|Submitted by|Indicates the individual who initiated the settings change or the Teams Rooms Pro Managed Rooms Service|
|Completed on|Indicates that timestamp when the job completed.|

### Device settings job history detail

By selecting the **Settings Job history** row in the table, a **Device settings** job panel is displayed with details about the specific device setting changes.

|**Field name**|**Description** |
|:------|:------|
|Job ID|A unique ID assigned to the settings job.|
|Status|Contains one of the following values: Submitted, Running, Completed, Completed with errors, Canceled, or Failed.|
|Submitted on|Date and Time when the job was submitted.|
|Submitted by|Indicates the individual who initiated the settings change or the Teams Rooms Pro Managed Rooms Service.|
|Settings|Shows the name of the settings that was changed.|
|Reason| See the table below for details.|

### Settings job reasons

Use this table to understand the **Settings Job** reasons.

|**Status**|**Reason**|**Reason**|**Description** |**Action** |
|:------|:------|:------|:------|
|Submitted|PENDING CONNECTION|Device is disconnected, will execute the job after the device reconnects. | Ensure that the device is connected.|
|Submitted|SCHEDULED|Job was successfully created.| None. The job is scheduled and will run when the device is available or in the nightly maintenance window.|
|Running|IN PROGRESS|Job was sent down to the agent, and is pending a response back.||
|Completed |SUCCESS|Job successfully completed on the agent, and verification of settings application was done. | Settings validation can take up to 15 minutes to reflect in the Teams Rooms Pro management portal.|
|Canceled |CANCELED  | User canceled the Job. |  |
Completed With Errors| APP RESTART FAILED|XML with new settings has been written to the correct location, but an issue occurred in the app restart process. To complete the process, the device was rebooted. | Reapply the settings. |
|Completed With Errors | VERIFICATION FAILED | XML with new settings has been written, and the app was successfully restarted, but the settings weren't applied correctly | or the settings change couldn't be verified. Check that the settings changed. A retry will be scheduled by the Managed room service for the nightly maintenance window. |
|Failed |EXISTING XML FOUND| An existing XML was found on the device and the agent was unable to create a new XML due to conflicts.|Restart the device to apply the existing SkypeSettings.XML on the device or remove it. See [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file). |
|Failed|FAILED TO WRITE XML|The agent failed to write an XML to the correct location.| Reapply the settings change.|
|Failed|FAILED|General failures outside of the specified error codes.|Reapply the settings change.|
|Failed|SETTINGS FETCH FAILED|Unable to fetch the new settings from the service.| Reapply the settings change.|
|Failed |DEVICE IN MEETING | Device is currently in a meeting.| Try again later. |
| Failed |DEVICE DISCONNECTED | Device was disconnected when we attempted to execute the settings change, so no changes occurred.|Reapply the settings change.|

## Device Settings Jobs for bulk changes

[!INCLUDE[Preview-feature](../includes/preview-feature.md)]

For Teams Rooms Pro management administrators, a job can be created to apply one or more settings to one or more Teams Rooms on Windows devices through the Teams Rooms Pro management portal.   The device setting job acts as a parent container for each of the individual jobs that execute for the selected setting changes across the devices selected.  In this way, you'll have an overall status of the completion of the parent job, along with the status for each individual device settings job.  A filter has been added to easily sort on a parent job status (Submitted, Running, Completed, Completed with errors, Cancelled, and Failed).  

When selecting either the **Apply Now** or **Schedule during Nightly Maintenance window**, the parent job creates individual jobs for each room device selected.  At the individual room level, you can see the job under the **Room > Activity** pane.  If the device is in a call or unmonitored, the individual job can fail or be rescheduled for another attempt to apply the settings change.  If one of the individual jobs fails, the parent job is reflected as **Completed with Errors**.  An export button has been provided to download the entire job details along with statuses of each individual job.

### Create a Job

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Settings** > **Device Settings**.

1. Select **Create job**.  A wizard is presented to step through creating the job.

1. Select **Settings** changes to be applied to devices.

1. Add **rooms** or **groups of rooms** where the setting changes are to be applied.

1. **Schedule** whether the settings changes should **apply now** or **schedule in the nightly maintenance window**.

1. Give the job a **name** for reference in the Device Settings Job dashboard.

1. Review the job details.  When you're ready, select **Create job**.  The job will be queued to execute.

### Device Settings Job Detail (for bulk changes)

Details of the job created are available by selecting the job from list on the Device settings job dashboard. A Setting jobs detail pane is presents with three tabs: **General, Settings and Devices**, along with an Export button. Filters are also available to sort through devices for quick reference of individual job statuses. 

## Settings available

Teams Rooms devices have settings that can either be applied on the device and synchronized with the Teams Rooms Pro management portal or from the Teams Rooms Pro management portal to the device. Here are the settings that are visible in the portal.

### About

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Device ID|Number|Unique device identifier|Information only|
|Agent version|Number|Current Teams Rooms Pro Management agent version number.|Information only|
|Last agent activity|Date/Time|Last known time the Teams Rooms Pro Management agent connected with the Service.|Information only|
|OS version|Number| Current Windows operating system build|Information only|
|IP address|Number| Device IP address detected| Information only|
|BIOS manufacturer|Text|Name of BIOS manufacturer |Information only|
|BIOS name|Text|BIOS update name |Information only|
|SMBIOSBIOSVersion|Number|||
|Latitude|Number|Coordinates of the device derived by Windows location settings on device.|Information only|
|Longitude|Number| Coordinates of the device derived by Windows location settings on device.|Information only|
|Time zone|Text| Provided by Microsoft for use with Windows and the .NET TimeZoneInfo class.|Information only|
|Time zone (IANA)|Text| Time zones provided by IANA. |Information only|

### Account

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Exchange sign in address|Text| Device's resource account sign-in address.|Information only|
|Supported meeting mode|Text|Teams only are displayed.|Information only|
|Public Preview|Text| Enrolls the device into Teams Ring 3.6 Public Preview. |Enabling this setting enables Public Preview features on your Teams Rooms device. Use caution as devices in early preview rings aren't supported by Microsoft Support. Available for Individual or bulk changes.|

### Meetings

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Default content layout in single display mode|Radio buttons|Focus on Content and People OR Focus on Content only|Set the default content layout for single display mode. Meeting participants can change the default content layout during meetings. Available for Individual or bulk changes.|
|Show Meeting Chat|Toggle| Enabled by default. |If disabled, meeting chat functionality (including chat bubbles and chat selection) isn't available in any meeting layout on the Teams Rooms device. Available for Individual or bulk changes.|
|Open Chat by Default|Checkbox| Enabled by default. |Checkbox won't be visible if Show Meeting Chat is disabled. If disabled, chat panel won't show by default in meetings using Gallery view.  Available for Individual or bulk changes.|
|Front Row Experience|Toggle|Enabled by default. |If false, Front row is disabled. For more information, see [Remotely configure Front Row on Teams Rooms](/microsoftteams/rooms/manage-front-row).  Available for Individual or bulk changes.|
|Default Layout Experience|Radio button|Front row default|Select the default meeting join layout as Gallery or Front Row.  Available for Individual or bulk changes.  Available for Individual or bulk changes.|
|Front Row Video Size|Dropdown|Medium (default), Small, Large|Sets the size of Front row to provide more or less space for remote participant video and shared content. Available for Individual or bulk changes.|
|Right front row panel|Dropdown|Show raised hand list, Show meeting chat, Hide the panel|Configure the position of the raised hand and chat components in the meeting panels to the left and right of meeting content on front-of-room displays. Available for Individual or bulk changes.|
|Left front row panel|Dropdown|Show raised hand list, Show meeting chat, Hide the panel|Configure the position of the raised hand and chat components in the meeting panels to the left and right of meeting content on front-of-room displays. Available for Individual or bulk changes.|
|Automatic Screen sharing|Toggle| Disabled by default.| If true, a connected HDMI ingest will be automatically shared on the Front of Room display and when in a Teams Meeting it's automatically shared to remote participants. If false, a connected HDMI ingest will be automatically shared on the Front of Room display in and out of a Teams meeting but it will not be shared to remote participants in the meeting automatically, users need to select the share icon to shared content to remote participants. Available for Individual or bulk changes.|
|Show meeting name|Toggle| Enabled by default.| If disabled, the meeting name is hidden from the console and Front of Room calendar displays. Available for Individual or bulk changes.|
|Autoleave if everyone else left the meeting|Toggle|Disabled by default.|If true, device will automatically leave the meeting if it's the only participant in the meeting for more than 5 minutes before or after the scheduled meeting time. Available for Individual or bulk changes.|
|HDMI ingest audio sharing|Toggle|Disabled by default. |When disabled, audio from a connected HDMI ingest isn't shared to Teams Meeting participants. Available for Individual or bulk changes.|
|Enable room capacity notifications|Toggle|Enabled by default. |Enabled by default to provide warnings to in room participants that the room has reached capacity (this requires the room capacity be set in Exchange and a camera capable of people counting). Set to false if you wish to disable these warnings. Available for Individual or bulk changes.|
|Show Captions|Toggle|Disabled by default. |When enabled, captions will be displayed.|
|Filter Profane words in captions and transcripts|Toggle| Enabled by default. |When captions are on, use of profane words are redacted.|
|Enable People Count|Toggle|Enabled by default. |If true, people count will be enabled for Teams Rooms. Available for Individual or bulk changes.|
|Require passcode for all Teams meetings|Toggle| Disabled by default. If true, users are required to enter the correct meeting ID and passcode to join all Teams meetings scheduled in the room with a Microsoft Teams Room Pro license.|Available for Individual or bulk changes.|
|Require passcode for all Private Teams meetings|Toggle| Disabled by default.| If true, users are required to enter the correct meeting ID and passcode to join all private Teams meetings scheduled in the room with a Microsoft Teams Room Pro license. Available for Individual or bulk changes.|
|Join third-party meetings|Checkbox|Cisco Webex, Zoom, GotoMeetings, RingCentral Meetings, Amazon Chime|May require calling plan to enable. For more information, see [Join third-party meetings](/microsoftteams/rooms/third-party-join?tabs=MTRW). Available for Individual or bulk changes.|
|Join with room info|Radio button|Uses conference room account info to join third party meetings.|Available for Individual or bulk changes.|
|Join with custom info|Radio button| Disabled by default.|If this value is set to true, you must specify both *CustomDisplayNameForThirdPartyMeetings* and *CustomDisplayEmailForThirdPartyMeetings* must be specified. Available for Individual or bulk changes.|
|Show Room Facilitator QR code|Toggle|Disabled by default.|Available for Individual or bulk changes.|

### Device

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Dual Monitor mode|Toggle|Disabled by default. |Dual screen mode is enabled. Otherwise, the device uses single screen mode. Available for Individual or bulk changes.|
|Allow content duplication|Checkbox|Disabled by default.|When checkbox is selected, content is shown on both screens in dual screen mode, when out of meeting. Available for Individual or bulk changes.|
|Enable Resolution and Scaling:|Toggle|Disabled by default. |If true, the display resolution and scale setting will be applied. This setting affects both the main front-of-room display and extended front-of-room display once this setting is enabled. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](/microsoftteams/rooms/manage-front-room-scale-res). Available for Individual or bulk changes.|
|Main Front of Room Display Resolution (Width)|Number| Enter a value. |The width entered could be unsupported. Valid resolutions (width x height) are: 1920x1080, 2560x1080, 3840x2160, 3840x2560, 5120x2160.  Available for Individual or bulk changes.   **Note**: *Changes are applied to the device. However, in the Settings Job History, it results in a Completed with Errors message.  This is normal.*|
|Main Front of Room Display (Height)|Number|Enter a value.|The height entered could be unsupported. Valid resolutions (width x height) are: 1920x1080, 2560x1080, 3840x2160, 3840x2560, 5120x2160. Available for Individual or bulk changes. **Note**: *Any changes are applied to the device. However, in the Settings Job History, it results in a Completed with Errors message.  This is normal.*|
|Main Front of Room scaling|Slider|Input numeric value of scaling.|Valid values are 100 (recommended), 125, 150, 175, 200, 225, 250, and 300. If you input greater than 300 and your front-of-room display only supports up to 300, it's set to 300. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](/microsoftteams/rooms/manage-front-room-scale-res).   Available for Individual or bulk changes.|
|Extended Front of Room Display Resolution (width)|Number|Enter a value.|The width entered could be unsupported. Valid resolutions (width x height) are: 1920x1080, 2560x1080, 3840x2160, 3840x2560, 5120x2160. Note: Any changes are applied to the device. However, in the Settings Job History, it results in a Completed with Errors message.  This is normal. Available for Individual or bulk changes.|
|Extended Front of Room Display Resolution (height)|Number|Enter a value.|The height entered could be unsupported. Valid resolutions (width x height) are: 1920x1080, 2560x1080, 3840x2160, 3840x2560, 5120x2160. Available for Individual or bulk changes. **Note**: *Any changes are applied to the device. However, in the Settings Job History, it results in a Completed with Errors message.*  |
|Extended Front of Room scaling|Slider|Input numeric value of scaling.|Valid values are 100 (recommended), 125, 150, 175, 200, 225, 250, and 300. If you input greater than 300 and your front-of-room display only supports up to 300, it's set to 300. For more information, see [Remotely configure layout, scale, and resolution on Teams Rooms displays](/microsoftteams/rooms/manage-front-room-scale-res). Available for Individual or bulk changes. **Note**: *Any changes are applied to the device. However, in the Settings Job History, it results in a Completed with Errors message.*|
|Disable Split video gallery|Toggle| Default is false. |This setting is only applicable to dual-display rooms. Specify true to disable splitting video gallery across both screens. This will also disable Front row layout, and any settings associated with Front row layout.  Available for Individual or bulk changes.|
|Remove Front of room calendar|Toggle|Disabled by default.|Remove the calendar on front-of-room displays. Available for Individual or bulk changes.|
|Allow Bluetooth beaconing|Toggle|Enabled by default.|When checked, proximity-based meeting invitations using Bluetooth are automatically accepted. Available for Individual or bulk changes.|
|Remote control from personal devices|Checkbox|Enabled by default.|Allow Bluetooth beaconing must be true. When checked, room remote connections are allowed. Room Remote won't work if only ultrasound is turned on.  Available for Individual or bulk changes.|
|Enable Ultrasound beacon|Toggle|Enabled by default.|Enables Ultrasound signaling beacons from compatible consoles. For more information [Proximity Join using Bluetooth and ultrasound](/microsoftteams/rooms/proximity-join?tabs=portal)|
|Automatically accept proximity-based meeting invites|Checkbox|Enabled by default.|When checked, proximity-based meeting invitations using Bluetooth are automatically accepted. Available for Individual or bulk changes.|
|Show Room QR Code|Toggle|Enabled by default.|When toggled on, Proximity-based meeting invitations via QR code are automatically accepted. For more information, see [Join meetings with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes). Available for Individual or bulk changes.|
|Send feedback to the Teams Rooms Pro Management portal|Toggle|Enabled by default.|Allows logs to be sent with feedback submitted using Report a problem. To ensure logs and feedback with larger sizes are delivered, adjust the message size restriction for your mailboxes on the Exchange admin center.  Available for Individual or bulk changes.|

### Coordinated meetings

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Coordinated Meetings|Toggle|Container for the configuration elements for Coordinated Meetings.|Determines whether Teams is configured to participate in Coordinated Meetings with other devices. Available for Individual or bulk changes.|
|Turn on this device’s microphone|Toggle|Disabled by default.|To avoid causing an echo effect, make sure only one device's microphone is enabled. Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Let people enable when joining a meeting|Checkbox|Disabled by default.|Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Turn on this device’s camera|Toggle|Disabled by default.|Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Let people enable when joining a meeting|Toggle|Disabled by default.|Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Turn on whiteboarding for this device|Toggle|Disabled by default.|Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Let people enable when joining a meeting|Checkbox|Disabled by default.|Available for Individual or bulk changes when coordinated meetings toggle is on.|
|Trusted device accounts|String|Separate with commas.|This is a comma-separated list of UPNs for each Teams Rooms device or Surface Hub that the device should accept meeting join requests from, or to which meeting join requests should be sent.|

### Peripherals

|**Field**|**Input**|**Description**|**Note**|
|:------|:------|:------|:------|
|Conference Microphone|Dropdown|Select option|Set the microphone used as the recording device in a conference.  Available for Individual setting changes. Not available for bulk setting changes|
|Conference audio speaker|Dropdown|Select option|Set the device to be used as speaker for the conference. This setting is used to set the speaker device used in a call. Available for Individual setting changes. Not available for bulk setting changes.|
|Conference audio speaker default volume|Slider||Adjusts the conference audio speaker volume. Available for Individual or bulk changes.|
|Default Speaker|Dropdown||Set the device to be used to play the audio from an HDMI ingest source. Available for Individual setting changes. Not available for bulk setting changes.|
|Default Speaker volume|Slider||Adjusts the default speaker volume.  Available for Individual or bulk changes.|
|Ultrasound Speaker|Toggle||This field won't appear unless there's a supported ultrasonic device discovered.  |
|Default Camera|Dropdown||Set the default camera.  Available for Individual setting changes. Not available for bulk setting changes.|
|Enable Cloud intelliframe|Toggle|Disabled by default.|Allows Teams Rooms to break up the single video feed of the room into a composite view made up of focused and framed video tiles that feature in-room attendees. Available for Individual or bulk changes.|
|Multiple Camera views|Toggle|Disabled by default.|Enable to set up multiple cameras. For more information, see [Multi Camera](/microsoftteams/rooms/multicamera-view).  Available for Individual setting changes. Not available for bulk setting changes.|
|Additional Camera(s)|Dropdown||Add up to three cameras.  Available for Individual setting changes. Not available for bulk setting changes.|
|Content camera|Dropdown||Select the camera configured in room to share analog whiteboard content in a meeting. Available for Individual setting changes. Not available for bulk setting changes.|
|Allow content enhancement|Checkbox||When set to true (the default), the content camera image is digitally enhanced: the whiteboard edge is detected and an appropriate zoom is selected, ink lines are enhanced, and the person writing on the whiteboard is made transparent. Set to false if you intend to send a raw video feed to meeting participants for spaces where a whiteboard isn't drawn on with a pen and instead the camera is used to show sticky notes, posters, or other media.  Available for Individual setting changes. Not available for bulk setting changes.|
|Content camera inverted|Checkbox||Specify if the content camera is physically installed upside down. For content cameras that support automatic rotation, specify false.  Available for Individual setting changes. Not available for bulk setting changes.|
|Enable noise suppression|Toggle|Disabled by default.|Controls noise suppression levels in Teams. **Off** Use OEM-provided noise suppression only. **On** Suppresses all background noises (stationary and nonstationary) that aren't speech.  Available for Individual or bulk changes.|

### Theming

|**Field**|**Input**|**Description**|
|:------|:------|:------|
|Theming|Dropdown|Select a default background.  Available for Individual or bulk changes.|

> [!Note]
> Currently, managing custom backgrounds from Teams rooms on windows isn't supported in the Teams Rooms Pro management portal.

### Digital Signage

The ability to change specific digital settings is permission based.  If you don't have access to change these settings, please check with your Teams Rooms Pro manager administrator.  Learn more by seeing [Digital Signage](/microsoftteams/rooms/digital-signage).

|**Field**|**Input**|**Description**|
|:------|:------|:------|
|Digital Signage|Toggle|Whether the toggle is enabled or editable will be determined by the Digital Signage tenant level settings. When enabled, it determines whether digital signage will be displayed in the room.|
|Reset Digital Signage|Checkbox|Resetting digital signage reverts the digital signage settings of this room to system defaults, including disabling digital signage and unregistering the room from trusted third-party signage sources where the room is enrolled in, if applicable. This action is irreversible.|
|Show Teams Rooms banner|Toggle|Enable to display date, time, room name, and calendar preview while digital signage is active. Disable to hide room information.|
|Display Period|Header||
|Activate signage when device has been idle for X minutes|Number|Set the activation time in range of 1 to 100 minutes.|
|Deactivate signage with meeting is starting in X minutes|Number|Set the deactivation time in range of 1 to 100 minutes.|
|Allow screen time out when device is idle|Toggle|Enable to respect OS screen time out settings. Disable to keep signage active on idle devices.|
|Signage source|Selection|Reflects the trusted third-party signage sources where the room is enrolled in.|

## Related articles
- [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file)
- [Set up Remote Access in Microsoft Teams Rooms Pro Management portal](/microsoftteams/rooms/remotely-access-teams-rooms)
- [Accessing the Pro Management portal](/microsoftteams/rooms/enrolling-mtrp-managed-service)
