---
title:  Troubleshooting the VDI 2.0 solution for Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 05/29/2025
ms.service: msteams
audience: admin
ms.collection: 
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: fklurfan
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about troubleshooting Teams for Virtualized Desktop Infrastructure (VDI) 2.0 issues.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# Troubleshooting VDI 2.0

When troubleshooting the new Slimcore-based optimization for Microsoft Teams, you need to know if users are optimized with the legacy WebRTC stack. They may also end up in the fallback mode "SlimCore Media Not Connected" (or server side rendering).

- Not optimized with SlimCore and instead you see:</br>"Azure Virtual Desktop Media Optimized" </br>"Citrix HDX Optimized"
  - Error Codes 2000 ("No Plugin") and 2001 ("Virtual Channel not available") are the most likely causes.

  1. Make sure your 'Virtual Channel Allow list' is properly configured to allow MSTEAMS, MSTEAM1, MSTEAM2.
  2. Make sure the endpoint has the plugin, and the VDI Client with Process Explorer loads it:
    - Run [process explorer](/sysinternals/downloads/process-explorer).
    - Enable the bottom pane and switch to the DLL tab.
    - On Azure Virtual Desktop, look for the msrdc.exe process and ensure the MsTeamsPluginAvd.dll is loaded.
    - On Citrix, look for the wfica32.exe process and ensure the MsTeamsPluginCitrix.dll is loaded.
  3. Restart the new Teams app. It requires two restarts to transition from WebRTC to SlimCore, when the plugin is detected for the first time.
  4. If the problem persists, check Event Viewer in the virtual machine (VM) for **Microsoft Teams VDI**-related errors (new Teams 24123.X.X.X or higher).

- Not optimized with SlimCore and instead you see: "Azure Virtual Desktop SlimCore Media Not Connected" or "Citrix SlimCore Media Not Connected".
  - Check the [Troubleshooting SlimCoreVdi MSIX deployment errors](#troubleshooting-slimcorevdi-msix-deployment-errors) section. MSIX or AppX-related errors are the most likely reasons for this error.

## New Teams logs for VDI

Teams logs can be collected by selecting Ctrl+Alt+Shift+1 while running Teams on a VM. This action produces a ZIP folder in the Downloads folder. Inside the PROD-WebLogs-*.zip file, look for the Core folder.

## Vdi_debug.txt (main file for VDI-related information)

|Azure Virtual Desktop/W365 |Citrix   |
|---------------------------|---------|
|"vdiConnectedState": {"connectedStack": "remote"}, "vdiVersionInfo": {"bridgeVersion": "2024.18.1.11", "remoteSlimcoreVersion": "2024.18.01.11", "nodeId": "1051a908af6b160e", "clientOsVersion": "10.0.22631", "rdClientVersion": "1.2.5405.0", "rdClientProductName": "Microsoft® Remote Desktop", "pluginVersion": "2024.14.01.1", "screenShareFallback": true} |"vdiConnectedState": {"connectedStack": "remote"}, "vdiVersionInfo": {"bridgeVersion": "2024.18.1.14", "remoteSlimcoreVersion": "2024.18.01.14", "nodeId": "ffffffff93eaee6a", "clientOsVersion": "10.0.22631", "rdClientVersion": "24.3.0.64", "rdClientProductName": "Citrix Workspace", "pluginVersion": "2024.15.01.3", "screenShareFallback": true} |

- **vdiConnectedState** shows the current active calling stack.
  - **connectedStack**: **remote** indicates Teams successfully connected to the remote endpoint through the virtual channel. It doesn't necessarily mean the calling stack is successfully initialized, so the user can still encounter calling-related failures, such as being unable to start a call.
  - **connectedStack**: **local** indicates the virtual channel connection failed. The user is now on fallback mode.
- **vdiVersionInfo** provides useful information for the Teams client and the endpoint.
  - **bridgeVersion** is tied to the version of the Teams desktop client running on the VM.
  - **remoteSlimcroreVersion** is the version of the SlimCore VDI that's available on the endpoint.
  - **nodeId** is a unique ID tied to the endpoint.
  - **clientOsVersion** is the OS version for the endpoint.
  - **rdClientVersion** is the version of the remote desktop client running on the endpoint, which is used to connect to the VM.
  - **rdClientProductName** is the name of the remote desktop client running on the endpoint.
  - **pluginVersion** is the version of the plugin that is integrated into the remote desktop client.

## Diagnostics-logs.txt could be on weblogs\user(..)

To further investigate VDI connection-related issues, using keyword **vdiBRidgeEventsHandler** provides the logs from the vdiBridge connection and disconnection event handlings, as shown (onConnected event handling) in the following example of a successful connection with the new optimization stack:

`7432 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: end, currentStack=remote
7435 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - new calling stack type set: currentStack=remote
7436 2024-03-01T17:51:22.032Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - deviceManagerService reloaded
7445 2024-03-01T17:51:22.031Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - calling stack reinit complete with nextStack=remote
7464 2024-03-01T17:51:21.785Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - starting calling stack reinit with nextStack=remote
7465 2024-03-01T17:51:21.785Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - SlimCore replacement complete, remote is now available
7467 2024-03-01T17:51:21.783Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - setVDIOptimizationModeOverride: from SlimCore to SlimCore
7468 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: isVersionMismatch=false, forceVersion=undefined, bridgeVersion=2024.5.1.11
7469 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - cached local SlimCore for future (fallback), currentStack=local
7470 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - onConnected: start, vendorType=1, remoteSlimcoreVersion=2024.05.01.11, platform=win-x86, loadErrc=1, deployErrc=24002, nodeId=ffffffffbd7d5e77
7471 2024-03-01T17:51:21.782Z Inf    vdiBridgeEventsHandler: VDI Mode: slimcore - enqueueBridgeCallback: adding onConnected to queue, 0 bridge callbacks in queue, isBridgeCallbacksQueueProcessing=false`

## Connection error

If there's a connection error, the error code can be found from the log line containing "loadErrc" and "deployErrc". A deploy error (also known as install_error) is an error that happens when the plugin was trying to download the SlimCore MSIX package from Microsoft's Content Delivery Network. The plugin then tries to stage or provision the package to the endpoint using the App Readiness Service for AppX. A load error is an error that happens when the plugin tried to start MsTeamsVdi.exe and establish a Remote Procedure Call (RPC) to it.

The code logged here needs to be mapped using this table:

|loadErrc   |deployErrc |Definition                         |Notes |
|-----------|-----------|-----------------------------------|------|
|0          |0          |OK                                 |Not an error. 'SlimCore Connected' success|
|5          |43         |ERROR_ACCESS_DENIED                |MsTeamsVdi.exe process failed at startup. BlockNonAdminUserInstall being enabled could cause this error. Or the endpoint could be busy registering multiple MSIX packages after a user logon and it didn't finish registering SlimCoreVdi. |
|404        |3235       |HTTP_STATUS_NOT_FOUND              |Publishing issue: SlimCore MSIX package isn't found on Content Delivery Network. |
|1260       |10083      |ERROR_ACCESS_DISABLED_BY_POLICY    |This error usually means that Windows Package Manager can't install the SlimCore MSIX package. Event Viewer can show the hex error code 0x800704EC. AppLocker Policies can cause this error code. You can either disable AppLocker, or add an exception for SlimCoreVdi packages in Local Security Policy -> Application Control Policies -> AppLocker. Check [Step 3](vdi-2.md#step-3-slimcore-msix-staging-and-registration-on-the-endpoint) under "Optimizing with new VDI solution for Teams". |
|1460       |11683      |ERROR_time-out                      |MsTeamsVdi.exe process failed at startup (60-second time-out). |
|1722       |           |RPC_S_SERVER_UNAVAILABLE           |'The RPC server is unavailable' MsTeamsVdi.exe related error. |
|2000       |16002      |No Plugin                          |Endpoint doesn't have the MsTeamsPlugin, or if it has it, it didn't load (check with Process Explorer). |
|2001       |           |Virtual Channel Not Available      |Error on the Citrix VDA (virtual delivery agent) WFAPI. |
|2003       |16026      |Custom Virtual Channels (MSTEAMS, MSTEAM1 and MSTEAM2) are blocked due to a Citrix Studio policy |Review the [Citrix virtual channel allow list](vdi-2.md#citrix-virtual-channel-allow-list) section of the VDI 2.0 article. |
|2005       |16043      |Teams is running as a Published App (Citrix) or RemoteApp (AVD/Windows 365) |This mode is currently not supported - Teams doesn't load SlimCore in this case, and users are always optimized with WebRTC. |
|3000       |24002      |SlimCore Deployment not needed     |This code isn't really an error. It's a good indicator that the user is on the new optimization architecture with SlimCore. |
|3001       |24010      |SlimCore already loaded            |This code isn't really an error. It's a good indicator that the user is on the new optimization architecture with SlimCore. |
|3004       |24035      |Plugin irresponsive                |Try restarting RDP (remote desktop protocol) or ICA (independent computing architecture) session. |
|3005       |24043      |Plugin time-out while downloading   |Failure to download the MSIX within 2 minutes. |
|3007       |24058      |Load time-out                       |SlimCore download or installation timed out (slow internet or App Readiness Service is busy). |
|4000       |           |ERROR_WINS_INTERNAL                |WINS encountered an error while processing the command. |
|15615      |1951       |ERROR_INSTALL_POLICY_FAILURE       |SlimCore MSIX related error. To install this app, you need either a Windows developer license, or a sideloading-enabled system. AllowAllTrustedApps regkey might be set to 0? |
|15616      |           |ERROR_PACKAGE_UPDATING             |SlimCore MSIX related error 'The application cannot be started because it is currently updating'. |
|15700      |           |APPMODEL_ERROR_NO_PACKAGE          |The process has no package identity. There's no alias for MsTeamsVdi in %LOCALAPPDATA%\Microsoft\WindowsApps. [Feedback Hub](https://support.microsoft.com/windows/send-feedback-to-microsoft-with-the-feedback-hub-app-f59187f8-8739-22d6-ba93-f66612949332) logs are needed while reproducing the error (make sure you select **Developer Platform** as the category and **App deployment** as the subcategory) |
|16389      |           |E_FAIL reported by Package Manager |Usually the same as Load error code 5 (ERROR_ACCESS_DENIED). Most likely caused by the BlockNonAdminUserInstall policy when the user isn't an Admin. Check [this link](/windows/client-management/mdm/policy-csp-applicationmanagement#blocknonadminuserinstall) for more details. |

## Using Event Viewer on the VM for troubleshooting

Every connect/disconnect event gets logged in the Event Viewer running on the Virtual Machine. The Event Viewer can also display client-side related errors. Filter by Source (Microsoft Teams VDI) and Event ID (0) under Windows Logs\Application. Error codes can be found in the [New Teams logs for VDI](#new-teams-logs-for-vdi) section.

> [!NOTE]
> In order to be able to filter by Source, you need to run this command from an elevated PowerShell window:
>
> PS C:\Windows\system32> New-EventLog -LogName Application -Source "Microsoft Teams VDI"

## Troubleshooting Plugin deployment errors

Diagnostic information can be found in the detailed event logs on the user's device. After install, MsTeamsPluginCitrix.dll is written into the CWA (Citrix Workspace app) folder. Only for the Citrix platform, the following keys on the Endpoint (not VM) are created:

|Key |Key type |Key name |Key value |
|---------|---------|---------|---------|
|HKLM\SOFTWARE\WOW6432Node\Citrix\ICA Client\Engine\Configuration\Advanced\Modules\ICA 3.0 |String |VirtualDriverEx |MicrosoftTeamsVDI |
|HKLM\SOFTWARE\WOW6432Node\Citrix\ICAClient\Engine\Configuration\Advanced\Modules\MicrosoftTeamsVDI |String |DriverNameWin32 |MsTeamsPluginCitrix.dll |

To debug installations, you can enable installer logging, but then you must use msiexec manually, and pass correct flags. For example, if the plugin isn't currently installed, it can be installed with logs like this: msiexec.exe /i MsTeamsPluginCitrix.msi /l*vx installer.log.txt.

## Troubleshooting SlimCoreVdi MSIX deployment errors

Make sure you review the [SlimCore MSIX staging and registration on the endpoint](vdi-2.md#step-3-slimcore-msix-staging-and-registration-on-the-endpoint) section, as certain GPOs (group policies) can prevent MSIX installations.

Diagnostic information can be found in the detailed event logs on the user's device.

1. Go the Event Viewer (Local) > Applications and Services Logs > Microsoft > Windows.
1. Check for available logs under these categories:
   - AppxPackagingOM > Microsoft-Windows-AppxPackaging/Operational
   - AppXDeployment-Server > Microsoft-Windows-AppXDeploymentServer/Operational

1. Review the logs under AppXDeployment-Server.

## Error 15615

Error 15615 usually means that the Windows Package Manager can't install the MSIX package with SlimCoreVdi.

- Make sure the Endpoint trusts the digital signature of that MSIX (Go to MSIX > Properties > Digital signatures > Details). It's a valid store-friendly Microsoft signature, but customers may have something special configured.
- Try enabling the [AllowAllTrustedApps policy](/windows/client-management/mdm/policy-csp-applicationmanagement).
- Try to allow sideloading apps from trusted nonstore sources.
  - On Windows 10, this setting is enabled by default, so modify it here if you find it disabled: Settings > Update and Security > For developers > Sideload apps.
  - On Windows 11, this setting is enabled by default: Settings > Apps > Advanced app settings > Choose where to get apps > Anywhere.

## Log collection

Logging can be found in the following locations:

- On the client:
  - `AppData\Local\Microsoft\TeamsVDI\<vdi_vendor>-default-<cloudname>\skylib`
  - `AppData\Local\Microsoft\TeamsVDI\<vdi_vendor>-default-<cloudname>\media-stack`
- On the Server:
  - `AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\Logs\skylib`
