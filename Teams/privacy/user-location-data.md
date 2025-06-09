---
title: User location consent experience in Microsoft Teams
ms.author: danbrown
author: DHB-MSFT
manager: dansimp
ms.topic: concept-article
ms.service: msteams
ms.reviewer: mimaisle
audience: ITPro
ms.collection: 
- privacy-teams
- must-keep
hideEdit: true
description: Learn about an updated user location consent experience in Microsoft Teams, including what dialogs and settings are available to Teams users and effect.
ms.localizationpriority: medium
ms.date: 04/24/2025
appliesto: Microsoft Teams
---

# User location consent experience in Microsoft Teams

Microsoft is updating its policies regarding the sharing of user location data to enhance privacy, improve data security, and ensure compliance with evolving regulatory standards.

To enhance transparency and user control, Teams is introducing a new location consent experience. This location consent experience gives users the choice of when and how Teams can use their location data (specifically [SSID & BSSID](/windows/win32/nativewifi/wi-fi-access-location-changes)).

All new and existing Teams for Work users will be prompted to specify if they want to keep location detection on for emergency calls only, or if they consent to allowing location access used for IT admin Insights or troubleshooting (for example, via tooling such as [Call Quality Dashboard](../CQD-what-is-call-quality-dashboard.md) or [Network and Location matching via BSSID](../configure-dynamic-emergency-calling.md)).

> [!IMPORTANT]
> The new Teams location consent flow doesn't affect managed devices where the operating system location settings are controlled by the device administrator. Whether the location setting is configured as on or off, existing policies will continue to function as expected, and users won't see any of the new location consent prompts. This behavior applies to Windows devices only; macOS doesn't allow full MDM control over Location Services toggles due to Apple's privacy model.

The new Teams location consent changes affect the following Teams features:

- Emergency Calling
- Location-Based Routing
- Network and Location matching via BSSID
- Call Quality Dashboard

## New Teams location consent experience

For all new Teams for Work users on Windows 11 version 24H2 or with macOS Ventura 13 or later, they'll first be prompted with an operating system level consent dialog requesting location permission granting, as shown in the following dialog.

:::image type="content" source="../media/privacy/dialog-precise-location-history.png" alt-text="A dialog asking the user if they want to let Teams access their precise location and location history. User has the choices of Yes or No.":::

For all existing Teams for Work users who previously accepted or denied operating system level consent for location, they won't see this dialog a second time.

The following table shows the outcomes you should be aware of based on a user’s consent choice at the operating system level.

|Operating system permission  |License type  |Outcome  |
|---------|---------|---------|
|Allowed (Yes)|Applies to all Teams for Work users.|Location consent granted. The user has explicitly agreed to share their location with the operating system and with Teams.<br/><br/>Dynamic emergency calling policies work as configured. <br/><br/> Users who are enabled for Location-Based Routing are able to make and receive PSTN calls. Location restriction based on a user's geographic location still applies.|
|Disallowed (No)|Applies to all Teams for Work users. |Several Teams [Call Quality Dashboard](../cqd-what-is-call-quality-dashboard.md) metrics become less accurate: wireless network analysis, call quality and connectivity, location based troubleshooting, and network performance reports. <br/><br/>Network and Location matching via BSSID from dynamic emergency calling policies won't work. [Network site matching via subnets](../cloud-voice-network-settings.md) can be defined and will work as expected.<br/><br/>Users who are enabled for Location-Based Routing, may not be able to make or receive PSTN calls. For more information, see [Plan Location-Based Routing for Direct Routing](../location-based-routing-plan.md).         |
|Disallowed (No)|Only applies to users who enabled for ExternalLocationLookupMode.|Users can still manually add their physical address and verify it for emergency calls via the Teams Calls app which routes them to the correct [Public Safety Answering Point (PSAP)](../emergency-calling-dispatchable-location.md).<br/><br/>If the user hasn't manually added an address via the Teams Calls app, emergency calls are routed to the National PSAP.<br/><br/>Dynamic emergency calling functionality is limited. Specifically, automatic location detection, on-site location detection, and security desk notifications based on BSSID won't be available for the specified user.|

After consenting to allow location access at the operating system level (or for those users who previously consented to location access), both new and existing Teams for Work users will be presented with the following new Teams app level location permission dialog.

:::image type="content" source="../media/privacy/dialog-teams-use-location.png" alt-text="A dialog asking the user how they want Teams to use their location. Provides the user with information about how Teams uses their location information and giving the user the choice of Allow all or Keep emergency only.":::

The user must decide how Teams can specifically use their location. The user must choose between these two choices:

- **Allow all**, which grants Teams full location access used for emergency calls and for IT Admin insights and troubleshooting.

- **Keep emergency only**, which restricts location usage to emergency calls only, which means location data is no longer sent for IT Admin insights and troubleshooting.

The following table shows the outcomes you should be aware of based on a user’s consent choice at the Teams app level.

|Permission type |License type |Outcome  |
|---------|---------|---------|
|Keep emergency only|Only applies to users who are enabled for ExternalLocationLookupMode.|Several Teams [Call Quality Dashboard](../cqd-what-is-call-quality-dashboard.md) metrics become less accurate: wireless network analysis, call quality and connectivity, location based troubleshooting, and network performance reports. <br/><br/>Dynamic emergency calling will be enabled and work as expected<br/><br/>Users who are enabled for Location-Based Routing can make and receive PSTN calls. |
|Allow all|Only applies to users who are enabled for ExternalLocationLookupMode. |Dynamic emergency calling will be enabled and work as expected<br/><br/>Users who are enabled for Location-Based Routing can make and receive PSTN calls.<br/><br/>Users’ location data is sent to the Call Quality Dashboard for analysis and troubleshooting.|

For information about ExternalLocationLookupMode, see [Emergency addresses for remote locations](../emergency-calling-dispatchable-location.md).

Users who aren't enabled for ExternalLocationLookupMode will see a slightly different version of this in-app consent dialog that excludes emergency calling, as shown in the following dialog.

:::image type="content" source="../media/privacy/dialog-location-detection-on.png" alt-text="A dialog informing the user they have already opted into location access in their system settings and providing information about how Teams is using their location.":::

The following table shows the impacts you should be aware of based on a user’s consent choice at the Teams app level:

|Permission type |License type |Outcome  |
|---------|---------|---------|
|OK|Users who aren't enabled for ExternalLocationLookupMode.|Users’ location data is sent to the Call Quality Dashboard for analysis and troubleshooting.<br/><br/>Network and Location matching via BSSID functions as expected.|

## Modifying consent options

Users are able to modify their operating system or app level location detection preferences at any time via Teams settings under **Privacy** > **Location**.

> [!IMPORTANT]
> On fully managed devices, these settings are ON by default and can only be disabled via the operating system level location setting.

For users who are enabled for ExternalLocationLookupMode, the **Emergency calls** toggle isn't available, as shown in the following screenshot. That's because it's controlled by the operating system level setting and can only be turned off by disabling the operating system level location settings.

:::image type="content" source="../media/privacy/privacy-settings-emergency-calls.jpg" alt-text="Screenshot of the Privacy settings page in Teams, with the Emergency calls toggle not available.":::

For users who aren't enabled for ExternalLocationLookupMode, users only see the **Insights for IT admins** toggle which they can turn on or off, as showing in the following screenshot.

:::image type="content" source="../media/privacy/privacy-settings-insights-it-admins.jpg" alt-text="Screenshot of the Privacy settings page in Teams showing the Insights for IT admins toggle.":::

If a user turns off the **Insights for IT admins** toggle, several Teams [Call Quality Dashboard](../CQD-what-is-call-quality-dashboard.md) metrics become less accurate: wireless network analysis, call quality and connectivity, location based troubleshooting, and network performance reports.

## What you need to do to prepare

To prepare your organization, educate your users on these selections and what works best for your organization.

If you regularly use the Call Quality Dashboard or use Network and Location matching via BSSID, you may want to recommend that users allow location access for those options. Otherwise a user’s location data will no longer flow through to these services.

For emergency calling, you can communicate these changes by setting the emergency service disclaimer with a custom message that displays in the Calls App in Teams. Ensuring that users have location turned on is crucial for proper functioning of emergency calls and their safety. For more information about sending a custom message, see [Manage emergency calling policies in Microsoft Teams](../manage-emergency-calling-policies.md).

To learn more about the changes to location services and privacy policies, see the following articles:

- [Windows location service and privacy](https://support.microsoft.com/windows/3a8eee0a-5b0b-dc07-eede-2a5ca1c49088)
- [Manage location sharing in Microsoft Teams](https://support.microsoft.com/office/583dd649-87fc-4b23-aed6-f4e2279297f9)
- [Changes to API behavior for Wi-Fi access and location](/windows/win32/nativewifi/wi-fi-access-location-changes)
