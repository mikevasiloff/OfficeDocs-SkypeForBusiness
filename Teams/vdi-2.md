---
title:  New VDI solution for Teams
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
description: Learn about Teams for Virtualized Desktop Infrastructure (VDI) 2.0.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# New VDI solution for Teams

The new VDI solution for Teams is a new architecture for optimizing the delivery of multimedia workloads in virtual desktops.

## Components

|Component |Role |Update |Size |Notes |
|----------|-----|-------|-----|------|
|New Teams **vdiBridge**     |Server-side virtual channel module. |New version with every new Teams version. |Bundled with new Teams. | |
|Custom virtual channel (VC) |Custom VC owned by Microsoft Teams. |Stable API - no updates foreseen. | |Check the Citrix Studio policy **Virtual channel allow list**. |
|Plugin                      |Client-side VC dll. Responsible also for SlimCore download and clean-up. |Not frequent (ideally no updates). |Approximately 200 KB. |Bundled with [RD Client 1.2.5405.0](/azure/virtual-desktop/whats-new-client-windows) or Windows App 1.3.252 or higher. Citrix CWA 2402 or higher can fetch and install the plugin. |
|SlimCore                    |Media engine (operating system specific, not VDI vendor specific). |Auto-updated to a new version with each new Teams version. |Approximately 50 MB. |MSIX package hosted on Microsoft's public Content Delivery Network|

## System requirements

|Requirement                       |Minimum version |
|----------------------------------|----------------|
|New Teams                         |24193.1805.3040.8975 (for Azure Virtual Desktop/Windows 365) </br>24295.605.3225.8804 (for Citrix) |
|Azure Virtual Desktop/Windows 365 |Windows App: 1.3.252</br>Remote Desktop Client: 1.2.5405.0 |
|Citrix                            |VDA: 2203 Long Term Service Release (LTSR) CU3 or 2305 Current Release</br>Citrix Workspace app: 2203 LTSR (any cumulative update), 2402 LTSR, or 2302 CR. [Only versions not at End of Life are supported](https://www.citrix.com/support/product-lifecycle/workspace-app.html) </br>MsTeamsPluginCitrix: 2024.41.1.1 |
|Endpoint                          |Windows 10 1809 (SlimCore minimum requirement)</br>[Windows Enterprise LTSC](/windows/whats-new/ltsc/overview#the-long-term-servicing-channel-ltsc) Thin clients on Windows 10 2019/2021, or Windows 11 2024 are supported</br>GPOs must not block MSIX installations (see [Step 3: SlimCore MSIX staging and registration on the endpoint](#step-3-slimcore-msix-staging-and-registration-on-the-endpoint)) </br>Minimum CPU: Intel Celeron (or equivalent) @ 1.10 GHz, 4 Cores, Minimum RAM: 4 GB |

## Optimizing with new VDI solution for Teams

### Step 1: Confirm prerequisites

1. Make sure you have the new Microsoft Teams version 24193.1805.3040.8975 or higher (for Azure Virtual Desktop/Windows 365), and 24295.605.3225.8804 or higher for Citrix.
1. [Enable the new Teams policy](#microsoft-teams-powershell-policy-for-optimization) **if necessary** for a specific user group (it's enabled by default at a Global org-wide level).
1. For Citrix, you must configure the **Virtual channel allow list** as described in the [Citrix Virtual channel allow list](#citrix-virtual-channel-allow-list) section of this article.

### Step 2: Plugin installation on the endpoint

1. For Azure Virtual Desktop and Windows 365, MsTeamsPluginAvd.dll is bundled with the Remote Desktop Client for Windows 1.2.5405.0, or with the Windows App Store app 1.3.252 or higher.
   - The plugin is found in the same folder location where the Remote Desktop Client is installed. You can find the plugin at AppData\Local\Apps\Remote Desktop or C:\Program Files (x86), depending on the mode in which it was installed.
   - The [Windows App Store](/windows-app/overview) app, which is MSIX-based, is found in C:\Program Files\WindowsApps. Access to this folder is restricted.

1. For Citrix Workspace app 2402 or higher, MsTeamsPluginCitrix.dll can be installed either:

   - Using the user interface when installing Citrix Workspace app:

     On the **Add-on(s)** page, select the **Install Microsoft Teams VDI plug-in** checkbox, and then select **Install**.
 
     Agree to the user agreement that pops up and proceed with the installation of the Citrix Workspace app.

     > [!NOTE]
     > Citrix Workspace app 2402 only presents the plugin installation UI on a fresh install.
     > For in-place upgrades to also present this option, Citrix Workspace app 2405 or higher is required.

   - Via command line or scripts for managed devices using:

     `C:\>CitrixWorkspaceApp.exe /installMSTeamsPlugin`

   - Admins can also install the plugin manually on top of any existing supported Citrix Workspace app (see [System Requirements](#system-requirements)) using tools like SCCM (use the Windows app package deployment type) or Intune (use the Line-of-Business app).

     Admins can use **msiexec** with appropriate flags, as discussed in [msiexec](/windows-server/administration/windows-commands/msiexec).

     > [!IMPORTANT]
     > Plugin MSI download link for Citrix customers: [aka.ms/plugin](https://download.microsoft.com/download/3/0/e/30e54a38-eb74-44dc-9755-36dcac09656d/MsTeamsPluginCitrix.msi).

The plugin MSI automatically detects the CWA installation folder and places MsTeamsPluginCitrix.dll in that location:

|User type     |Installation folder                                                                             |Installation type |
|--------------|------------------------------------------------------------------------------------------------|------------------|
|Administrator |64-bit: C:\Program Files (x86)\Citrix\ICA Client</br>32-bit: C:\Program Files\Citrix\ICA Client |Per-system installation |

- Plugins can't be downgraded, only upgraded or reinstalled (repaired).
- Per-user installation of CWA isn't supported.
- If no CWA is found on the endpoint, installation is stopped.

|Release note version |Details  |
|---------------------|---------|
|2025.14.1.8          |May 2025</br>-The plugin can now download SlimCore packages that are 64-bit, increasing performance.|
|2024.41.1.1          |October 2024</br>-When using SlimCore in multimonitor setups, a Citrix user is unable to share entire screen or individual monitors.</br>-Attempts a [Reset-AppxPackage](/PowerShell/module/appx/reset-appxpackage) if SlimCoreVdi MSIX package registrations fail after the virtual channel is established. |
|2024.32.X.X          |August 2024</br>-The plugin now attempts a Reset-AppxPackage for SlimCoreVdi MSIX package in the event the AppExecution alias is missing. |

### Step 3: SlimCore MSIX staging and registration on the endpoint

The plugin silently executes this step, without user or admin intervention. The staging and registration relies on the App Readiness Service (ARS) on the endpoint. It's possible that registry keys set by a Group Policy or a third-party tool block the MSIX package installation. For a complete list of applicable registry keys, see [How Group Policy works with packaged apps - MSIX](/windows/msix/group-policy-msix).

The following registry keys could block new media engine MSIX package installation:

- [BlockNonAdminUserInstall](/windows/client-management/mdm/policy-csp-applicationmanagement#blocknonadminuserinstall)
- [AllowAllTrustedApps](/windows/client-management/mdm/policy-csp-applicationmanagement#allowalltrustedapps)
- AllowDevelopmentWithoutDevLicense

> [!IMPORTANT]
> Managed endpoints/thin clients with BlockNonAdminUserInstall enabled can still allow SlimCore packages to install. Apply KB5052094 (Windows 11 23H2 and 22H2), KB5052093 (Windows 11 24H2), KB5055612 (Windows 10 22H2), or any subsequent KB.
> This installation introduces a new Group Policy called "Allowed package family names for non-admin user install" in the Local Group Policy Editor.
>
>Administrators can then Allow list SlimCore packages by allowing a complete package familyName (for example, Microsoft.Teams.SlimCoreVdi.win-x64.2024.43_8wekyb3d8bbwe) or use Regex (for example, Microsoft.Teams.SlimCoreVdi.*_8wekyb3d8bbwe)

> [!IMPORTANT]
> If AllowAllTrustedApps is disabled, the new media engine (MSIX) installation fails. This issue is fixed in the following Windows cumulative updates:
>
> - [Windows 10: October 26, 2023—KB5031445 (OS Build 19045.3636)](https://support.microsoft.com/topic/october-26-2023-kb5031445-os-build-19045-3636-preview-03f350cb-57f9-45e6-bfd7-438895d3c7fa)
> - [Windows 11: October 26, 2023—KB5031455 (OS Build 22621.2506)](https://support.microsoft.com/topic/october-26-2023-kb5031455-os-build-22621-2506-preview-6513c5ec-c5a2-4aaf-97f5-44c13d29e0d4)
> - [Windows 10 1809: April 8, 2025—KB5055519 (OS Build 17763.7136)](https://support.microsoft.com/en-us/topic/april-8-2025-kb5055519-os-build-17763-7136-417d1340-ce40-4d0b-98ac-637c0f6dca35)

These three registry keys can be found at either of the following locations on the user's device:

- HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock
- HKLM\SOFTWARE\Policies\Microsoft\Windows\Appx

Some policies might change these registry keys and block app installation in your organization because the admins set a restrictive policy. Some of the known GPO policies that could prevent installation include:

- Prevent nonadmin users from installing packaged Windows apps.
- Allow all trusted apps to install (disabled).

> [!NOTE]
> [AppLocker](/windows/security/application-security/application-control/windows-defender-application-control/applocker/applocker-overview) or [Windows Defender Application Control](/windows/security/application-security/application-control/windows-defender-application-control/wdac-and-applocker-overview) can also prevent MSIX package installation.
>
> AppLocker is a defense-in-depth security feature and not considered a defensible [Windows security feature](https://www.microsoft.com/msrc/windows-security-servicing-criteria). Use [Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/wdac-and-applocker-overview) when the goal is to provide robust protection against a threat and there you expect no by-design limitations to prevent the security feature from achieving this goal.

> [!IMPORTANT]
> Make sure there's no blocking configuration or policy, or add an exception for SlimCore MSIX packages in Local Security Policy -> Application Control Policies -> AppLocker.
>
> AppLocker can't process trailing wildcards, unlike Windows Defender Application Control. Since SlimCoreVdi Packages contain a version-specific PackageFamilyName (for example, Microsoft.Teams.SlimCoreVdi.win-x64.2024.36_8wekyb3d8bbwe), customers can add AppX or MSIX exclusions by relying on the PublisherID 8wekyb3d8bbwe instead.
>
> Administrators using the more granular per-application ['AllAppList'](/windows/configuration/assigned-access/configuration-file#allapplist) to define the list of applications that are allowed to run need to add exceptions in this manner (since SlimCore follows the UWP model):
>
> &lt;App AppUserModelId="Microsoft.Teams.SlimCoreVdi.&lt;platform&gt;-&lt;architecture&gt;.&lt;release_version>_8wekyb3d8bbwe!MsTeamsVdi" /&gt;
>
> For example: &lt;App AppUserModelId="Microsoft.Teams.SlimCoreVdi.win-x86.2025.12_8wekyb3d8bbwe!MsTeamsVdi" /&gt;.
>
> To find a list of released SlimCore packages, [check this table](/officeupdates/teams-app-versioning#vdi-slimcore-version-2-msix-packages).


## Verifying that the end point is optimized

Once you meet all the minimum requirements, launching new Teams for the first time finds it still in WebRTC optimized mode by default.

> [!IMPORTANT]
> For first run experiences, two app restarts are required to get the new optimization.

You can check in the Teams client that you optimized with the new architecture by going to the ellipsis (three dots ...) on the top bar, then selecting Settings > About. The Teams and client versions are listed there.

- AVD SlimCore Media Optimized = New optimization based on SlimCore.
- AVD Media Optimized = Legacy optimization based on WebRTC.

The plugin (MsTeamsPluginAvd.dll or MsTeamsPluginCitrix.dll) is responsible for eventually downloading the media engine, and SlimCore, which is an MSIX package. It installs silently without admin privileges or reboots in (example, exact path varies):

`C:\Program Files\WindowsApps\Microsoft.Teams.SlimCoreVdi.win-x64.2024.15_2024.15.1.5_x64__8wekyb3d8bbwe`

The remote desktop client downloads the x64 or x86 SlimCore package, and the Citrix CWA downloads an x86 package. This folder is locked down, so users don't have access to it. Admins modify ACLs to take ownership, though this action isn't recommended. Instead, use PowerShell to list the MSIX apps in the endpoint:

```PowerShell
PowerShellCopy

Get-AppxPackage Microsoft.Teams.SlimCore*
```

A sample of the results that can be returned from running this PowerShell is:

```PowerShell
Name              : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32
Publisher         : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Architecture      : X64
ResourceId        :
Version           : 2024.32.1.7
PackageFullName   : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_2024.32.1.7_x64__8wekyb3d8bbwe
InstallLocation   : C:\Program
                    Files\WindowsApps\Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_2024.32.1.7_x64__8wekyb3d8bbwe
IsFramework       : False
PackageFamilyName : Microsoft.Teams.SlimCoreVdi.win-x64.2024.32_8wekyb3d8bbwe
PublisherId       : 8wekyb3d8bbwe
IsResourcePackage : False
IsBundle          : False
IsDevelopmentMode : False
NonRemovable      : False
IsPartiallyStaged : False
SignatureKind     : Developer
Status            : Ok
```

> [!IMPORTANT]
> Microsoft stores up to 12 versions of SlimCoreVdi for compatibility purposes. We store these versions in case the user accesses different VDI environments, such as persistent, where new Teams auto-updates itself, and non-persistent, where new Teams auto-updates are disabled.

If you're optimized, you can see MsTeamsVdi.exe running on your endpoint for Azure Virtual Desktop/W365 (as a child process of msrdc.exe) or Citrix (as a child process of wfica32.exe). When using Process Explorer, If you select msrdc.exe (or wfica32.exe), select **Show the lower pane** under **View** and switch to the DLL tab, you can also see the Plugin (MsTeamsPluginAvd.dll or MsTeamsPluginCitrix.dll) being loaded. This action is a useful troubleshooting step in case you're not getting the new optimization.

If you enable the bottom pane and switch to the DLL tab, you can also see the Plugin being loaded. This action is a useful troubleshooting step in case you're not getting the new optimization.

## VDI Status Indicator

Microsoft Teams displays information about the optimization status, helping the user understand if they're optimized or not. It also shows if they're using the legacy WebRTC optimization or the new Slimcore-based one by hovering their cursor over the **Optimized** banner.

In cases where Microsoft Teams isn't optimized, the user sees a warning icon.

![Screenshot of the Teams app showing it's not optimized.](media/Status_Indicator_Not_Optimized_2.png)

Users can select the three dots and choose **Optimize virtual desktop and restart** to attempt a repair.

This selection triggers a Teams restart, which can solve some known issues. If the user is still unoptimized, an error code displays for quick diagnosis by IT Admins based on the [connection error table](vdi-2-troubleshooting.md#connection-error).

Users are presented with a [link](https://go.microsoft.com/fwlink/?linkid=2295247) to receive more information about the error, and if it's actionable, they can try a self-remediation.

## Session roaming and reconnections

New Teams loads WebRTC or SlimCore at launch time. If virtual desktop sessions are disconnected (not logged off, Teams is left running on the virtual machine), Teams can't switch optimization stacks unless restarted. As a result, users might be in fallback mode (not optimized) if they roam between different devices that don't support the new optimization architecture. For example, a MAC device used in BYOD (bring your own device) while working from home, and a corporate-managed thin client in the office. In order to avoid this scenario, Teams prompts the user with a modal dialogue asking to restart the app. After the restart, users are in WebRTC optimization mode.

Additionally, users can roam from a device that only supports WebRTC to a device that supports SlimCore. In this scenario, Teams also prompts the user with a modal dialogue asking to restart the app. After the restart, users are in SlimCore optimization mode.

|Reconnecting options                                        |If current optimization is WebRTC |If current optimization is SlimCore  |
|------------------------------------------------------------|----------------------------------|-------------------------------------|
|Reconnecting from an endpoint **without** the MsTeamsPlugin |Then WebRTC classic optimization. </br>("AVD Media Optimized"). </br>("Citrix HDX Media Optimized"). |Then restart dialogue prompt. </br>After restart, the user is on WebRTC classic optimization. Otherwise, Teams isn't restarted and the user is in fallback mode (server -side rendering). |
|Reconnecting from an endpoint **with** the MsTeamsPlugin    |Then restart dialogue prompt. </br>After restart, the user is on new SlimCore optimization. Otherwise, Teams isn't restarted and the user is still in WebRTC. |Then new SlimCore-based optimization. |

## Networking considerations

> [!NOTE]
> MsTeamsVdi.exe is the process that makes all the TCP/UDP network connections to the Teams relays/conference servers or other peers.
>
> SlimCore MSIX manifest adds the following rules to the Firewall:
> `<Rule  Direction="in" IPProtocol="TCP"  Profile="all" />`
> `<Rule Direction="in" IPProtocol="UDP" Profile="all" />`

Make sure the user's device has network connectivity (UDP and TCP) to endpoint ID 11, 12, 47 and 127 described in [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

|ID  |Category          |ER  |Addresses    |Ports                       |Notes |
|----|------------------|----|-------------|----------------------------|------|
|11  |Optimize required |Yes |52.112.0.0/14, 52.122.0.0/15, 2603:1063::/38 |UDP: 3478, 3479, 3480, 3481 |Media Processors and Transport Relay 3478 (STUN), 3479 (Audio), 3480 (Video), 3481 (Screen share) |
|12  |Allow required    |Yes |`*.lync.com`, `*.teams.microsoft.com`, `teams.microsoft.com` 52.112.0.0/14, 52.122.0.0/15, 52.238.119.141/32, 52.244.160.207/32, 2603:1027::/48, 2603:1037::/48, 2603:1047::/48, 2603:1057::/48, 2603:1063::/38, 2620:1ec:6::/48, 2620:1ec:40::/42 |TCP: 443, 80                |      |
|47  |Default required  |No  |*.office.net |TCP: 443, 80                |Used for SlimCore downloads and background effects |
|127 |Default required  |No  |*.skype.com  |TCP: 443, 80                |      |

### Network architecture

:::image type="content" source="media/teams-vdi-2-network-architecture.png" alt-text="The network architecture of Teams VDI 2.":::

A walkthrough of the architecture in the diagram:

1. Start new Teams.​
2. Teams client authenticates to Teams services. Tenant policies are pushed down to the Teams client, and relevant configurations are relayed to the app.​
3. Teams detects that it's running in a virtual desktop environment and instantiates the internal vdibridge service​.
4. Teams opens a secure virtual channel on the server​.
5. The RDP or HDX protocol carries the request to the RD Client or Citrix Workspace app that previously loaded MsTeamsPlugin (client-side virtual channel component)​.
6. The RD Client or Citrix Workspace app spawns a new process called MsTeamsVdi.exe, which is the new media engine (SlimCore) used for the new optimization​.
7. SlimCore media engine (on the client) and msteams.exe (on the virtual desktop) now have a bidirectional channel and can start processing multimedia requests.​

User calls

8. Peer A selects the call button. MsTeamsVdi.exe communicates with the Microsoft Teams services in Azure, establishing an end-to-end signaling path with Peer B. MsTeamsVdi.exe collects a series of supported call parameters (codecs, resolutions, and so forth, which is known as a Session Description Protocol (SDP) offer). These call parameters are then relayed using the signaling path to the Microsoft Teams services in Azure and from there to the other peer.​
9. The SDP offer/answer (single-pass negotiation) takes place through the signaling channel, and the ICE connectivity checks (NAT and Firewall traversal using STUN bind requests) complete. Then, Secure Real-time Transport Protocol (SRTP) media flows directly between MsTeamsVdi.exe and the other peer (or Teams Transport Relays or Conference servers).

IP blocks for signaling, media, background effects, and other options are described in [this article](/microsoft-365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams).

### Types of traffic handled by SlimCore on the endpoint

1. Teams media flows connectivity is implemented using standard IETF Interactive Connectivity Establishment (ICE) for STUN and TURN procedures.
1. Real-time media. Data encapsulated within Real-time Transport Protocol (RTP) that supports audio, video, and screen sharing workloads. In general, media traffic is highly latency sensitive. This traffic must take the most direct path possible and use UDP versus TCP as the transport layer protocol, which is the best transport for interactive real-time media from a quality perspective.
    - As a last resort, media can use TCP/IP and also be tunneled within the HTTP protocol, but we don't recommend it due to bad quality implications.
    - RTP flow is secured using SRTP, in which only the payload is encrypted.
1. Signaling. The communication link between the endpoint and Teams servers, or other clients, used to control activities (for example, when a call is initiated). Most signaling traffic uses UDP 3478 with fallback to HTTPS, though in some scenarios (for example, the connection between Microsoft 365 and a Session Border Controller) it uses SIP protocol. It's important to understand that this traffic is much less sensitive to latency but may cause service outages or call timeouts if latency between the endpoints exceeds several seconds.

### Bandwidth consumption

Teams is designed to give the best audio, video, and content sharing experience regardless of your network conditions. When bandwidth is insufficient, Teams prioritizes audio quality over video quality. Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30 fps (frames per second) for video and content. To learn more, read [Bandwidth requirements](prepare-network.md#bandwidth-requirements).

### Quality of services (QoS)

Implement QoS settings for endpoints and network devices and determine how you want to handle media traffic for calling and meetings.

- As a prerequisite, enable QoS globally in the Teams Admin Center. See [Configure QoS in the Teams admin center](meetings-real-time-media-traffic.md) for details on enabling the **Insert Quality of Service (QoS) markers for real-time media traffic** settings.

  Recommended initial port ranges:

  |Media traffic type    |Client source port range |Protocol |DSCP value |DSCP class                |
  |----------------------|-------------------------|---------|-----------|--------------------------|
  |Audio                 |50,000 - 50,019          |TCP/UDP  |46         |Expedited Forwarding (EF) |
  |Video                 |50,020 - 50,039          |TCP/UDP  |34         |Assured Forwarding (AF41) |
  |App or screen sharing |50,040 = 50,059          |TCP/UDP  |18         |Assured Forwarding (AF41) |
- For information on configuring DSCP markings for Windows endpoints, see [Implement QoS in Teams clients](QoS-in-Teams-clients.md).
  > [!NOTE]
  > Any endpoint-based marking must be applied to MsTeamsVdi.exe, the process that handles all multimedia offloading on the user's device. Refer to the [Playbook document](https://aka.ms/teams-vdi-2.0-playbook) for more info on QoS.
- For information on implementing QoS for routers, see your manufacturer's documentation.
- Setting QoS on network devices might include some or all of:
  - using port-based Access Control Lists (ACLs)
  - defining the QoS queues
  - defining DSCP markings

> [!IMPORTANT]
> We recommend implementing these QoS policies using the endpoint source ports and a source and destination IP address of "any". These policies catch both incoming and outgoing media traffic on the internal network.

### Technologies that aren't recommended with Microsoft Teams in VDI

1. **VPN network**. Not recommended for media traffic.
1. **Packet shapers**. Any kind of packet sniffer, packet inspection, proxies, or packet shaper devices aren't recommended for Teams media traffic and may degrade quality significantly.

## Microsoft Teams PowerShell policy for optimization

The CsTeamsVdiPolicy cmdlets enabled administrators to control the type of meetings that users can create or the features that they can access while in a meeting specifically on a VDI environment, where WebRTC optimization was disabled using the VDI Partner's policy engine ([Citrix Studio](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html#enable-optimization-of-microsoft-teams), [VMware HTML5 ADMX template](https://docs.vmware.com/en/VMware-Horizon/2203/horizon-remote-desktop-features/GUID-8557C3D7-4B08-4C98-B474-97B795300A6E.html#GUID-8557C3D7-4B08-4C98-B474-97B795300A6E), or [this registry key](/azure/virtual-desktop/teams-on-avd) for AVD and Windows 365).

The default policy configurations are:

- DisableCallsAndMeetings: False
- DisableAudioVideoInCallsAndMeetings: False

This policy now has an additional argument as the only configuration point to control whether or not a user can get the new optimization mode based on SlimCore. In other words, the VDI Partner's policy engines don't control the new optimization mode:

- VDI2Optimization: Enabled  (default value)

|Name                    |Definition |Example |Notes |
|------------------------|-----------|--------|------|
|New-CsTeamsVdiPolicy    |Allows administrators to define new VDI policies that can be assigned to users for controlling Teams features related to meetings on a VDI environment. |`PS C:\> New-CsTeamsVdiPolicy -Identity RestrictedUserPolicy -VDI2Optimization "Disabled"` |The command shown here uses the New-CsTeamsVdiPolicy cmdlet to create a new VDI policy with the identity RestrictedUserPolicy. This policy uses all the default values for a VDI policy except one: VDI2Optimization. In this example, users with this policy can't be optimized with SlimCore. |
|Grant-CsTeamsVdiPolicy  |Allows administrators to assign a Teams VDI policy at a per-user scope. Admins can control the type of meetings that a user can create, the features they can access on an unoptimized VDI environment, and whether a user can be optimized with the new optimization mode based on SlimCore. |`PS C:\> Grant-CsTeamsVdiPolicy -identity "Ken Myer" -PolicyName RestrictedUserPolicy` |In this example, a user with identity "Ken Myer" is assigned the RestrictedUserPolicy. |
|Set-CsTeamsVdiPolicy    |Allows administrators to update existing VDI policies. |`PS C:\> Set-CsTeamsVdiPolicy -Identity RestrictedUserPolicy -VDI2Optimization "Disabled"` |The command shown here uses the Set-CsTeamsVdiPolicy cmdlet to update an existing VDI policy with the Identity RestrictedUserPolicy. This policy uses all the existing values except one: VDI2Optimization; in this example, users with this policy can't be optimized with SlimCore. |
|Remove-CsTeamsVdiPolicy |Allows administrators to delete a previously created Teams VDI policy. Users with no explicitly assigned policy fall back to the default policy in the organization. |`PS C:\> Remove-CsTeamsMeetingPolicy -Identity RestrictedUserPolicy` |In the example shown previously, the command deletes the restricted user policy from the organization's list of policies and removes all assignments of this policy from users with the policy assigned. |
|Get-CsTeamsVdiPolicy    |Allows administrators to retrieve information about all the VDI policies configured in the organization. |`PS C:\> Get-CsTeamsVdiPolicy -Identity SalesPolicy` |In this example, Get-CsTeamsVdiPolicy is used to return the per-user meeting policy that has an Identity SalesPolicy. Because identities are unique, this command doesn't return more than one item. |

## Feature list with the new optimization

|Feature                           |Available on SlimCore (Windows)                                 |Available on WebRTC (Windows) |
|----------------------------------|----------------------------------------------------------------|------------------------------|
|1080p                             |Yes                                                             |No                            |
|Hardware acceleration on endpoint |Yes <sup>2</sup>                                                |No                            |
|Gallery View 3x3 and 7x7          |Yes                                                             |No                            |
|Quality of Service                |Yes                                                             |No                            |
|Noise suppression                 |Yes                                                             |Yes (AVD)                     |
|Voice isolation                   |Yes                                                             |No                            |
|HID                               |Yes                                                             |Yes (AVD and Omnissa)         |
|Presenter mode                    |Yes                                                             |No                            |
|Teams Premium                     |Check the Teams Premium page                                    |Check the Teams Premium page  |
|Organizational custom backgrounds |Yes (Teams Premium license required)                            |No                            |
|User-uploaded background effect   |Yes <sup>3</sup>                                                            |No                            |
|Zoom +/-                          |Yes                                                             |No                            |
|Media bypass, Location-based routing, Operator Connect <sup>1</sup> |Yes                           |No                            |
|Call quality dashboard and Teams admin center|Yes                                                  |Limited                       |
|Published app/Remote app          |No                                                              |Yes                           |
|Give/Take control                 |Yes                                                             |Yes                           |
|App sharing                       |Yes                                                             |Yes                           |
|e911                              |Yes                                                             |Yes                           |
|Simulcast                         |Yes                                                             |Yes                           |
|Share system audio                |Yes                                                             |Yes                           |
|Secondary ringer                  |Yes                                                             |Yes                           |
|Background blurring               |Yes                                                             |Yes                           |
|Annotations                       |Only as presenter. <sup>4</sup>                                 |No                            |

<sup>1</sup> Operator Connect in India with mobile numbers requires latitude and longitude access from the endpoint's OS and local internet breakout. Operator Connect with wireline numbers can use IP or subnet to map to a location. For more details, check [Wireline and Wireless number types in India](operator-connect-india-plan.md#wireline-and-wireless-number-types-in-india).
<sup>2</sup> Graphics hardware acceleration requires DirectX 9 or later, with WDDM 2.0 or higher for Windows 10 (or WDDM 1.3 or higher for Windows 10 Fall Creators Update).
<sup>3</sup> If you join a meeting as a guest, this feature isn't supported.
<sup>4</sup> Viewers will not see the annotations (they are hidden by the incoming video window overlay)

## SlimCore user profile on the endpoint

The new solution for VDI stores user-specific data on the endpoint in the following locations, depending on your vendor:

- `C:\users\<user>\AppData\Local\Microsoft\TeamsVDI\avd-default-<cloudname>\`
- `C:\users\<user>\AppData\Local\Microsoft\TeamsVDI\citrix-default-<cloudname>\`

> [!IMPORTANT]
> Locked-down thin clients must allow these locations to be read/write. Otherwise the new optimization might fail. For older Windows 10 1809 Thin Clients (such as Dell Wyse 5070 and similar models), the folder location for SlimCore profile is
`C:\Users\<user>\AppData\Local\Packages\Microsoft.Teams.SlimCoreVdi.win-<architecture>.<version>_8wekyb3d8bbwe\LocalCache\`.

Logs, configurations, and AI or ML models (used in noise suppression, bandwidth estimation, etc.) are saved in this location. If these folders are purged after a user signs out (for example, locked-down thin clients without roaming profiles), MsTeamsVdi.exe recreates them and downloads the user-specific configuration (about 12 MB of data). User-specific data can grow to ~100 MB (including ~60 MB for logs).

### SlimCore installation and upgrade process in locked down Thin Client environments (optional)

By default, the MsTeamsPlugin automatically downloads and installs the right SlimCore media engine version without user or Admin intervention. But customers on restricted network environments in the branch office can opt for an alternative SlimCore distribution process, without requiring the endpoint be able to fetch SlimCore packages using https from Microsoft's public Content Delivery Network.

> [!NOTE]
> For an updated list of SlimCore packages that match their corresponding new Teams version, [check this table](/officeupdates/teams-app-versioning#vdi-slimcore-version-2-msix-packages).

> [!IMPORTANT]
> If you must choose this method, you must guarantee that:
>
> 1. [Teams auto-update is disabled](new-teams-vdi-requirements-deploy.md#disable-new-teams-autoupdate-in-non-persistent-vdi) in the virtual desktop.
> 2. The SlimCore packages are pre-provisioned to the endpoint's local storage or network share before you upgrade new Teams in the virtual desktop. Any newer Teams version requests a matching new version of SlimCore and if the plugin can't find it, the user is in fallback mode (server-side rendering).
>
> This circumstance happens because the new Teams and SlimCore versions must match.

#### Configuration steps

1. On the user's endpoint (thin client/fat client), you must create the following regkey:

   - Location for Citrix: HKLM\SOFTWARE\WOW6432Node\Microsoft\Teams\MsTeamsPlugin
   - Location for Azure Virtual Desktop/W365: HKLM\SOFTWARE\Microsoft\Teams\MsTeamsPlugin
   - Name: MsixUrlBase
   - Type: REG_SZ
   - Data: Either local storage or network storage UNC path, such as file://C:/Temp or file://ComputerName/SharedFolder.
   
   The regkey defines the Base URL.

2. Additionally, admins must download the exact SlimCore MSIX Package version from Microsoft's Content Delivery Network that matches the new Teams version you're planning to deploy in the future.

   > [!IMPORTANT]
   > The MSIX package needs to match the architecture or bitness of the Citrix Workspace app (x86 only) or Remote Desktop or Windows App clients: `Microsoft.Teams.SlimCoreVdi.<platform>-<architecture>.msix`.

3. To preserve the structure, place the MSIX in a specific folder with the version within the location specified in the registry key. For example, C:\Temp\2024.4.1.9\Microsoft.Teams.SlimCoreVdi.win-x86.msix or //ComputerName/SharedFolder/2024.4.1.9/.
  
   > [!NOTE]
   > If the Plugin can't find a SlimCore MSIX package in the local or network storage, it automatically attempts to download it from the Microsoft public Content Delivery Network as a fallback.

### Unified Write Filters (UWF)

Customers with Thin Clients with [Unified Write Filters](/windows/configuration/unified-write-filter/) applied should create the following exclusions in order to allow SlimCore MSIX packages to be provisioned:

- uwfmgr.exe file Add-Exclusion "C:\Program Files\WindowsApps"
- uwfmgr.exe file Add-Exclusion "C:\Users\User\AppData\Local\Packages"
- uwfmgr.exe file Add-Exclusion "C:\Users\User\AppData\Local\Microsoft\WindowsApps"
- uwfmgr.exe file Add-Exclusion "C:\Users\User\AppData\Local\Microsoft\TeamsVDI"

## Known issues

- AVD RemoteApps and Citrix Published Apps aren't supported at this time.
- Screen Capture Protection (SCP) causes the presenter's screen to show as a black screen with only the mouse cursor on top (as seen by the receiving side). This issue's fixed in Teams 25060.205.3499.6849 and Remote Desktop client 1.2.6081 or Windows app 2.0.379.
- If you lock the virtual machine (VM) during an active call, the call disconnects. This issue's fixed in 25094.303.3554.9058 or higher versions.
- Calls drop on Teams running on the local machine that has an HID peripheral connected if a user launches a virtual desktop from that same local machine and logs into Teams. This issue can also happen if the user had an active virtual desktop and launches a second one that has Teams installed (or other Unified Communications apps that use optimization).
- Camera self preview isn't supported at this time (either under Settings/Devices, or while on a call when selecting the down arrow on the camera icon).
- In the Control Panel/Apps/Installed apps of the endpoint, users see multiple "Microsoft Teams VDI" entries (one for every Slimcore package installed).
- When doing full monitor screen sharing, the call monitor window is visible for the other participants (without any video content inside).
- In Citrix, app sharing sessions might freeze for the other participants if the presenter is on both VDA (virtual delivery agent) version 2402 and CWA for Windows 2309.1 (or higher versions).
  - The issue happens when a video element is destroyed.
       - For example, a participant turns off their camera in the middle of the app sharing session.
       - If someone turns their camera **on** only, there's no issue because the video element is created, not destroyed.
       - If the presenter maximizes the call monitor (which destroys the self preview of what the presenter is sharing).
  - Stopping and resharing the window should resolve the issue.
  - This issue is resolved in new Teams 24335.206.X.X or higher versions.
- If you're on a video call and you open the Start menu on the virtual machine, a blank screen shows in the Teams meeting window instead of the video feed.
- In CQD, VdiMode (x2xx) represents both VDI SlimCore Optimized and Unoptimized Fallback, which may misattribute poor call quality.
  
## Cross Cloud Collaboration
 
Organizations in Microsoft’s Public, GCC (Government Community Cloud), GCCH (Government Community Cloud High), and DoD (Department of Defense) clouds can now collaborate with each other efficiently in with the new optimization (this collaboration applies to both intra-company and inter-company). This collaboration often involves access to shared content which requires authenticated access. Previously, collaboration across clouds via Teams was limited due to the lack of optimization in audio/video. With new Teams and Slimcore based optimization, users can now enjoy a high definition user experience. For more information on Cross Cloud, check [this link](/microsoftteams/cross-cloud-meetings).

The following scenarios are supported:

- **Cross Cloud Anonymous** allows the scenario where a user is signed into Cloud A in Teams, and joins a meeting in a different Cloud B anonymously. Check [Manage anonymous participant access to Teams meetings, webinars, and town halls (IT admins)](/microsoftteams/anonymous-users-in-meetings) for more details.
- **Cross-cloud Guest Access** extends functionality to allow a user to participate in rich collaboration experiences in teams, channels, documents, and Teams meetings for a full experience including audio/video optimization, screen share, file share and both 1:1 and 1:n chat. Check [here](/microsoft-365/solutions/collaborate-guests-cross-cloud?view=o365-worldwide&preserve-view=true) for more details.
- **Cross-cloud authenticated meeting join** delivers the ability for a Teams user to join a meeting in another cloud while signed into their account in their home tenant. This feature provides the meeting host the ability to validate the identities of meeting participants without granting those participants any access to the host tenant.

Minimum versions: Teams 25060.205.3499.6849. Remote Desktop Client 1.2.6186. Citrix Plugin 2024.41.1.1.

Known issues: 
-	HID only works in the primary Cloud.
-	Muting from Teams UI doesn't play the "Mute/Unmuted" voice command in the nonprimary Cloud.
-	More Peripherals limitations are described [here](/microsoftteams/troubleshoot/meetings/known-issues-teams-certified-peripherals)
-	Any user signed into multiple clouds (Multi Cloud or Cross Cloud), can't get optimized with WebRTC. If the user roams to a device which doesn't support SlimCore, they're in fallback mode (server-side rendering) until they roam back to a SlimCore capable device. This issue happens because WebRTC doesn't support any Cross Cloud features.
-	If Cross Cloud features don't appear to work even though the user meets the minimum requirements, you can quit Teams (after it gets optimized with SlimCore) and try to delete a file called ecs_settings.dat64 at the following path: %localappdata%\packages\MSTeams_8wekyb3d8bbwe\LocalCache\microsoft\MSTeams. Restart Teams.

## Citrix virtual channel allow list

The [Virtual channel allow list](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/secure/virtual-channel-security#adding-virtual-channels-to-the-allow-list) policy setting in CVAD enables the use of an allow list that specifies which virtual channels can be opened in an ICA session. When enabled, all processes except the Citrix built-in virtual channels must be stated. As a result, more entries are required for the new Teams client to be able to connect to the client-side plugin (MsTeamsPluginCitrix.dll).

With Citrix Virtual Apps and Desktops 2203 or later, the virtual channel allow list is **enabled by default**. These default settings deny access to the new Teams custom virtual channels as the allow list **doesn't** include the new Teams main process name.

The new Teams client requires three custom virtual channels to function: MSTEAMS, MSTEAM1 and MSTEAM2. Ms-teams.xes accesses these channels. You can use wildcards to allow the ms-teams.exe executable and custom virtual channel:

- MSTEAMS,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM1,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe
- MSTEAM2,C:\Program Files\WindowsApps\MSTeams*8wekyb3d8bbwe\ms-teams.exe

1. Wildcard support is available in:
   - VDA 2206 CR.
   - VDA 2203 LTSR from CU2 onwards.

2. The VDA machines must be rebooted for the policy to take effect.

## Screen sharing

Both outgoing screen sharing and app sharing behave differently in optimized VDI when compared to the nonoptimized Teams desktop client. As such, these activities require encoding that employs the user's device resources (for example CPU, GPU, RAM, network, and so on). From a network perspective, sharing is done directly between the user's device and the other peer or conference server.

A full monitor screen share captures the Teams call monitor and makes it visible to the other participants. The video elements inside aren't visible and instead are seen as blank squares. When doing app sharing, only the application being shared is visible to the other participants and the call monitor isn't captured.

### Citrix App Protection and Microsoft Teams compatibility

Users with App Protection enabled can still share their screen and apps while using the new optimization. Sharing requires VDA version 2402 or higher, and CWA for Windows 2309.1 or higher. Users on lower versions end up sharing a black screen instead when the App Protection module is installed and enabled.

### AVD Screen Capture Protection and Microsoft Teams compatibility

Users with [Screen Capture Protection](/azure/virtual-desktop/screen-capture-protection?tabs=intune) (SCP) enabled to block screen capture on the remote desktop client (**Block screen capture on client**) can still share their screen and apps while using the new SlimCore-based optimization for Microsoft Teams. Sharing requires the following minimum versions: Teams 25060.205.3499.6849, and Remote Desktop client 1.2.6081 or Windows App 2.0.379.

Users on lower versions end up sharing a black screen instead with SCP enabled.

## Peripherals in VDI

When Teams is optimized with SlimCore, Cameras, microphones, and speakers connected to your physical device are mapped on your virtual desktop. Teams enumerates all the detected devices, prioritizing Default Communication Devices (as seen in the mmsys.cpl panel when run on the user's device).
SlimCore-based optimization supports Human Interface Devices (HID) for [Teams certified headsets](https://aka.ms/teamsdevices), allowing users to mute/umute and increase/decrease volume themselves directly from their headset. A Microsoft Teams button on a certified Teams device isn't currently supported.

> [!NOTE]
> With some peripherals, two Unified Communications apps running side by side can cause HID collisions where active calls get disconnected.
>
> See the Known Issues section.
>
> As a workaround, HID can be disabled via registry key on Teams 25060.205.3499.6849 or higher, where the key can be created on the endpoint.
> (The key can also be created on the VM if you have the 2025.14.1.8 Plugin (Citrix), or the Remote Desktop client 1.2.6275 / Windows App 2.0.550.0).
>
> HKEY_CURRENT_USER\Software\Microsoft\Teams\HID
>
> Name: DisableHidManagerV1 
>
> Type: DWORD
>
> Value: 1 (when set to 1, it disables HID) (If set to 0 or the key isn't present, HID is enabled)

## Monitoring API

Administrators can create custom scripts to [query](/windows/win32/fileio/obtaining-directory-change-notifications) vdi_connection_info.json - this file in the virtual machine contains information about the current and last session, such as optimization status, peripherals, and software versions of the different components.

Location (in the VDA or RD Host): C:\Users\<username>\AppData\Local\Packages\MSTeams_8wekyb3d8bbwe\LocalCache\Microsoft\MSTeams\tfw

Typical use cases for the monitoring API are:
- Administrators deploying an automation script in a VDA or RD Host to detect whether the client endpoint operating system changed since the last connection. The script consumes the contents of the JSON file to compare the last two sessions' values, and issue their own alerts/pop-up messages.
- Developers creating third-party apps that report the current state of the VDI optimization connection. The script consumes the contents of the JSON file to retrieve all available connection, optimization, and device information of the current Teams session.

Json File Structure:
-	Timestamp - vdiConnectedState.timestamp indicates the timestamp of the session connection
-	VDI Optimization - vdiConnectedState.vdiMode indicates the optimization version (remains static throughout the VDI session)  
-	Connected State - connectedStack (remote = optimized, local = not optimized) (remains static throughout the VDI session)
-	SlimCore Version on the endpoint - remoteSlimcoreVersion
-	VdiBridge Version on the VM - bridgeVersion
-	MS Teams Plugin Version on the endpoint - pluginVersion
-	Teams Version - vdiVersionInfo.teamsVersion
-	Client Platform - vdiVersionInfo.clientPlatform
-	VDI Client (CWA or Windows App) version - vdiVersionInfo.rdClientVersion	
-	VM OS Version - vdiVersionInfo.vmVersion
-	Available Peripheral Devices - devices.speakers.available, devices.cameras.available, devices.microphones.available (real time update to the json file)
-	Selected Peripheral Devices - devices.speakers.selected, devices.cameras.selected, devices.microphone.selected (real time update to the json file)
-	Secondary Ringer - devices.secondaryRinger (real time update to the json file)

> [!NOTE]
> When in WebRTC optimization, only the vdiConnectedState is populated, indicating which optimization the session is currently in. There's no vdiVersionInfo and device information stored in the JSON file for the session. When no optimization is available, there aren't updates made to the JSON file.

## Call Quality Dashboard in VDI

Call Quality Dashboard (CQD) allows IT Pros to use aggregate data to identify problems creating media quality issues by comparing statistics for groups of users to identify trends and patterns. CQD isn't focused on solving individual call issues, but on identifying problems and solutions that apply to many users.

VDI user information is now exposed through numerous dimensions and filters. Check [this page](dimensions-and-measures-available-in-call-quality-dashboard.md) for more information about each dimension.

> [!NOTE]
> The new Quality of Experience (QER) template is available in the Power BI query templates for CQD download. Version 8 now includes templates for reviewing VDI client-focused metrics.

> [!IMPORTANT]
> In CQD, the VdiMode value (x2xx) represents both VDI SlimCore Optimized and VDI SlimCore Not Connected (Unoptimized Fallback). This duplication can lead to misinterpretation, as poor call quality in an unoptimized session may appear to be an issue with VDI SlimCore Optimization. We're working to address this limitation in telemetry. For now, we recommend you use Teams logs to verify the actual optimization status.

#### Query fundamentals

A well-formed CQD query/report contains all three of these parameters:

- [Measurement](dimensions-and-measures-available-in-call-quality-dashboard.md#measurements)
- [Dimension](dimensions-and-measures-available-in-call-quality-dashboard.md#dimensions)
- [Filter](dimensions-and-measures-available-in-call-quality-dashboard.md#filters)

Some examples of a well-formed query would be:

1. "Show me Poor Streams [Measurement] for VDI Users with the new Optimization [Dimension] for Last Month [Filter]."
1. "Show me Poor App sharing [Measurement] by Total Stream Count [Dimension] for Last Month AND where First OR Second Client VDI mode was optimized [Filters]." 

You can use many Dimension and Measurement values as filters too. You can use filters in your query to eliminate information in the same way you'd select a Dimension or Measurement to add or include information in the query.

#### What UNION does

By default, Filters allow you to filter conditions with the AND operator. But there are scenarios where you might want to combine multiple Filter conditions together to achieve a result similar to an OR operation. For example: To get all streams from VDI Users, UNION provides a distinct view of the merged dataset. To use the UNION, insert common text into the UNION field on the two filter conditions you want to UNION.

#### Caller and Callee location

CQD doesn't use Caller or Callee fields, instead it uses **First** and **Second** because there are intervening steps between the caller and callee.

- **First** is always the server endpoint (for example, AV MCU or the Media Processor Server) if a server is involved in the stream.
- **Second** is always the client endpoint, unless it's a server-server stream.

If both endpoints are the same type (for example a person-to-person call), first versus second is set based on the internal ordering of the user agent category to make sure the ordering is consistent.
