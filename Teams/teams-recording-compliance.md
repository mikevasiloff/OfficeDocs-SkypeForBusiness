---
title: Introduction to Microsoft Teams third-party compliance recording
ms.author: scottfrancis
author: sfrancis206
manager: pamgreen
ms.date: 11/11/2024
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: kkodali
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about Teams third-party compliance recording for calling, meetings, town halls, webinars, and live events.
f1.keywords:
- CSH
ms.custom: 
 - Adopt
 - seo-marvel-mar2020
ms.collection: 
- Teams_ITAdmin_Adopt
- M365-collaboration
- tier3
- m365initiative-meetings
- m365initiative-voice
- purview-compliance
appliesto: 
- Microsoft Teams
---

# Third-party compliance recording for Microsoft Teams calls and meetings

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Meetings ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Webinars ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Calls

## Compliance recording overview

Compliance recording is the process of recording and storing communications in a way that follows local, national, and global regulatory requirements.

Microsoft Teams is enhanced to offer compliance recording of call and meeting communications by supporting integrations with certified, third-party, compliance recording solutions.

Using a partner solution to record Teams calls, meetings, and events allow corporate compliance officers to securely collect necessary communications in the manner required to meet regulated compliance and legal obligations, such as MiFID II, Dodd-Frank, FDCPA, HIPAA, and GDPR.

Compliance recording partner solutions are integrated with Teams as shown in the following diagram:

:::image type="content" source="media/compliance-recorder-small.png" alt-text="Diagram of the flow for when a Teams meeting or call is sent and received." lightbox="media/compliance-recorder-expandable.png":::

The Graph API supporting the third-party application’s recording status is available in the following national cloud deployments:

|Global Service    |US Government L4    |US Government L5 (DOD)    |China operated by 21Vianet    |
|----------------------|------------------|---------------|-----------------|
|Yes    |Yes     |Yes    |No    |

This solution is designed specifically to turn on policy-based compliance recording with Teams. Any other use of this solution isn't supported.

## Supported compliance recording capabilities

As a Teams communications admin, with a third-party compliance recording solution, you can specify when to capture calls, meetings, and events for subsequent processing and retention, in accordance with relevant corporate or regulatory policies.
From the available APIs and third-party compliance recording solutions, the following capabilities are supported.

<table>
<thead>
<tr class="header">
<th>Persona</th>
<th>Capabilities</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Recorded users</td>
<td><ul>
<li><p>Be notified when recording is in progress.</p></li>
<li><p>Be informed when policy and/or recorder error is causing changes in calling behavior.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Communications admin</td>
<td><ul>
<li><p>Understand why and how to apply / enforce recording policies to Teams users / endpoints.</p></li>
<li><p>Configure and maintain Teams recording policies for the organization.</p></li>
<li><p>Monitor and troubleshoot recording-related issues with Teams calls and meetings.</p></li>
<li><p>Support internal compliance officer with operational analytics on usage, quality, and reliability.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Compliance officer</td>
<td><ul>
<li><p>Collect all Teams communications in the manner required to meet compliance obligations in appropriate regional boundaries.</p></li>
<li><p>Search for interactions based on communication-related metadata or interaction content. Common examples include:</p>
<ul>
<li><p><strong>Metadata</strong> - Participants, time, direction, dialed number, origin number, Custom business data.</p></li>
<li><p><strong>Content</strong> – Transcription, sentiment, phonetics, related interactions.</p></li>
</ul></li>
<li><p>Analyze and interact with collected communications, including the ability to monitor interactions as they're being collected.</p></li>
<li><p>Ensure security of collected communications and prevent tampering at all stages.</p></li>
</ul></td>
</tr>
</tbody>
</table>

For general Teams recording capabilities, see [Teams recordings](./teams-recording-policy.md)

#### Considerations

Compliance recording isn't supported for:

- E911 emergency calling services
- Users operating in Survivable Branch Appliance mode
- PSTN Calls for India users

**Large Meetings**

The Compliance Recording platform is optimized for meetings. However, performance might be impacted during meetings with over 250 users in paired bot mode. We're actively working on improvements in a future update to enhance the experience.
For extra-large meetings with over 250 users, it's recommended to use town halls as the meeting type.
Please contact your recording partner for more information.

**Call queues**

Inbound call queue calls are recorded where users have an assigned compliance recording policy. Some routing methods might involve usability concerns with multiple announcements.

**Licensing**

To be eligible for compliance recording, a user account must be equipped with any one of the following licenses:

- Microsoft 365 A3/A5/E3/E5/G3/G5/Business Premium/Business Standard
- Office 365 A3/A5/E3/E5
- Microsoft Teams Room (Pro or Basic) license
- Teams Shared Device license

## Supported notification methods

Users with an assigned compliance recording policy know that their digital interactions with Teams are being recorded. Depending on the third-party recording solution and how it's configured, users may not be able to disable the recording and may not have access to the recording.

Compliance recording notifications are supported for the Teams client experiences. The experiences can be both visual and audio.

### Teams clients - visual notice

- Desktop/web
- Mobile (iOS/Android)
- Teams Phones
- Teams rooms

### Other endpoints - audio notice

- SIP phones
- Skype for Business
- Audio conferencing (audio notice in dial-in number's default or user-selected language)
- PSTN callers (audio notice in Teams user's default language)

## Recorder development

The solution for Teams compliance recording is achieved through Microsoft’s third-party partners who develop compliance recording bots, and pair the bot with their recording solution. Each partner solution varies, but each partner uses the same key Graph APIs, an application instance, and a compliance recording policy.

The recording bot has the following requirements:

- Recorder bot must run on a Windows Virtual Machine and be deployed in Azure
- Recorder bot outbound firewall destination IP address must be open to the [Azure public IP range](https://www.microsoft.com/download/details.aspx?id=56519)
- Recorder bot inbound firewall source IP address must be open to the [Teams IP range](https://www.learn.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges)

For a sample of developing a compliance recording bot, see [deploying and testing a sample bot](https://github.com/microsoftgraph/microsoft-graph-comms-samples/tree/a3943bafd73ce0df780c0e1ac3428e3de13a101f/Samples/BetaSamples/LocalMediaSamples/ComplianceRecordingBot#bot-registration).

## Third-party compliance recording partners

Microsoft created a compliance recording for Microsoft Teams certification program while making Teams APIs available for partners to develop and integrate compliance recording solutions. This program provides customers with the assurance that each participating partner's solution is tested and verified to provide the quality, compatibility, and reliability expected from a Microsoft solution.

If you're a vendor seeking to join the certification program, fill out the calling platform intake as the next step.
[Calling Platform Intake](https://aka.ms/CallingPlatformIntake).

The following list includes partners certified to deliver a compliance recording solution with Microsoft Teams:

|Partner|Solution website |
|:--|:--|
|ASC Technologies |[https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html](https://www.asctechnologies.com/english/ASC_Recording_Insights_Compliance_Recording_for_Microsoft_Teams.html) |
|AudioCodes SmartTAP|[https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams](https://online.audiocodes.com/smarttap-360-live-for-microsoft-teams) |
|CallCabinet |[https://www.callcabinet.com/compliance-microsoft-teams-call-recording](https://www.callcabinet.com/compliance-microsoft-teams-call-recording ) |
|Cloud World Wide Services |[https://recordia.net/microsoft-teams-call-recording/](https://recordia.net/microsoft-teams-call-recording/) |
|Dubber |[https://www.dubber.net/call-recording/](https://www.dubber.net/call-recording/) |
|Imagicle |[https://www.imagicle.com/en/products/call-recording/](https://www.imagicle.com/en/products/call-recording/) |
|Insightful Technology |[https://insightfultechnology.com/teams/](https://insightfultechnology.com/market-place/) |
|Luware |[https://luware.com/en/solution/microsoft-teams-recording/](https://luware.com/en/solution/microsoft-teams-recording/) |
|Mida Solutions |[https://www.midasolutions.com/recorder-for-teams/](https://www.midasolutions.com/recorder-for-teams/) |
|NICE Engage |[https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage](https://www.nice.com/products/workforce-engagement/call-recording/air-and-engage) |
|NICE NTR-X |[https://www.niceactimize.com/compliance/ms-teams-recording.html](https://www.niceactimize.com/compliance/ms-teams-recording.html) |
|Numonix |[https://numonix.cloud](https://numonix.cloud)    |
|Oak Innovation |[https://www.oakinnovate.com/clarify](https://www.oakinnovate.com/clarify) |
|Red Box |[https://www.redboxvoice.com/compliance-recording-for-microsoft-teams](https://www.redboxvoice.com/red-box-partners/microsoft-integration/compliance-recording-for-microsoft-teams)  |
|Theta Lake |[https://thetalake.com/integrations/microsoft/](https://thetalake.com/integrations/microsoft/) |
|Touch Call Recording (GuardRec Compliance 2022.10.3) |[https://touchcallrecording.com/teams-policy-based-recording-for-callings-and-meetings](https://touchcallrecording.com/teams-policy-based-recording-for-callings-and-meetings) |
|Verint Verba |[https://www.verba.com/solutions/microsoft-teams-recording](https://www.verba.com/solutions/microsoft-teams-recording) |
|Verint EDM |[https://www.verint.com/enterprise-recording-engagement-data-management/](https://www.verint.com/enterprise-recording-engagement-data-management/) |

The following partners are in the process of certifying their solution for Microsoft Teams:

|Partner|Solution website |
|:--|:--|
|AudioCodes Interaction Insights|[https://www.audiocodes.com/solutions-products/saas/audiocodes-live-platform/interaction-insights-recording-services](https://www.audiocodes.com/solutions-products/saas/audiocodes-live-platform/interaction-insights-recording-services) |
|CreaLog |[https://www.crealog.com/en/products-solutions/recording/](https://www.crealog.com/en/products-solutions/recording/) |
|Landis Technologies |[https://landistechnologies.com/](https://landistechnologies.com/) |
|Liquid Voice |[https://www.liquidvoice.com/microsoft-teams-recording/](https://www.liquidvoice.com/microsoft-teams-recording/) |
|Redwood Technologies |[https://www.contentguru.com/en-us/solutions/needs/compliance-recording-ms-teams/](https://www.contentguru.com/en-us/solutions/needs/compliance-recording-ms-teams/) |
|TollRing |[https://www.analytics-365.com/call-recording/](https://www.analytics-365.com/call-recording/) |

This list gets updated as more partners join and meet the certification criteria.

## Create and manage your compliance recording policy

Once a compliance recording solution is in place, a Teams admin can create and assign recording policies to control which users are recorded and which recorder is used for each user. Recorders are automatically invited to participate in conversations based on the configuration of these policies when a communication interaction takes place.
Compliance
recording policies are managed using [Microsoft
PowerShell](./teams-powershell-overview.md)
and can be applied at the tenant, per-user, and security group level for each
organization. You can find more information on Microsoft Learn for
[Meeting
policies](./meeting-policies-overview.md),
 [calling
policies](./teams-calling-policy.md) and  [group
policies](./assign-policies-users-and-groups.md#assign-a-policy-to-a-group).

1. Create an application instance in your tenant.

   ```powershell
   New-CsOnlineApplicationInstance -UserPrincipalName cr.instance@contoso.onmicrosoft.com -DisplayName ComplianceRecordingBotInstance -ApplicationId fcc88ff5-a42d-49cf-b3d8-f2e1f609d511
   ```

    Example results
    - RunspaceId        : 4c13efa6-77bc-42db-b5bf-bdd62cdfc5df
    - ObjectId          : 5069aae5-c451-4983-9e57-9455ced220b7
    - TenantId          : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
    - UserPrincipalName : cr.instance@contoso.onmicrosoft.com
    - ApplicationId     : fcc88ff5-a42d-49cf-b3d8-f2e1f609d511
    - DisplayName       : ComplianceRecordingBotInstance
    - PhoneNumber       :
      
   ```powershell
   Sync-CsOnlineApplicationInstance -ObjectId 5069aae5-c451-4983-9e57-9455ced220b7
   ```

2. Create a Compliance Recording policy.

   ```powershell
   New-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy -Enabled $true -Description "Test policy created by tenant admin"
   ```
  
    Example results
    - Identity                        : Global
    - ComplianceRecordingApplications : {}
    - Enabled                         : True
    - WarnUserOnRemoval               : True
    - Description                     : Test policy created by tenant admin

   ```powershell
   Set-CsTeamsComplianceRecordingPolicy -Identity TestComplianceRecordingPolicy `
   -ComplianceRecordingApplications @(New-CsTeamsComplianceRecordingApplication -Id 5069aae5-c451-4983-9e57-9455ced220b7 -Parent TestComplianceRecordingPolicy)
   ```

   See [Set-CsTeamsComplianceRecordingPolicy](/powershell/module/teams/set-csteamscompliancerecordingpolicy).

3. Assign the Compliance Recording policy to a user.

   ```powershell
   Grant-CsTeamsComplianceRecordingPolicy -Identity testuser@contoso.onmicrosoft.com -PolicyName TestComplianceRecordingPolicy
   ```

   See [Grant-CsTeamsComplianceRecordingPolicy](/powershell/module/teams/grant-csteamscompliancerecordingpolicy).

   ```powershell
   Get-CsOnlineUser testuser@contoso.onmicrosoft.com | select SipAddress, TenantId, TeamsComplianceRecordingPolicy | fl
   ```

    Example
    - UserPrincipalName              : testuser@contoso.onmicrosoft.com
    - TenantId                       : 5b943d7c-5e14-474b-8237-5022eb8e0dc9
    - TeamsComplianceRecordingPolicy : TestComplianceRecordingPolicy

## Support boundaries

Microsoft only supports compliance recording solutions from the listed, certified partners. If there are enablement or operational issues, you must contact your compliance recording partner first. If the partner determines the issue is with Microsoft, they might ask you to raise a case with Microsoft, providing context of the investigation completed by the partner. If needed, the partner can bring the issue to Microsoft through their Microsoft support channel. Microsoft reserves the right to reject support cases where a non-certified Compliance Recording solution is used. If Microsoft determines that the issue is originating with a partner's compliance recording solution, the customer needs to re-engage the compliance recording partner for further support.

### Related topics  

- [Teams Recordings - Microsoft Teams | Microsoft Learn](./teams-recording-policy.md)
- [Overview- Recording and transcription for Teams meetings and calls](recording-transcription-overview.md)
