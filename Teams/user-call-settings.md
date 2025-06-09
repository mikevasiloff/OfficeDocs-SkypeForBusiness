---
title: Configure call forwarding and delegation settings
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: roykuntz, jastark
ms.date: 12/19/2024
ms.topic: how-to
ms.assetid: 67ccda94-1210-43fb-a25b-7b9785f8a061
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
audience: Admin
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - ms.teamsadmincenter.callqueues.overview
  - Phone System
  - seo-marvel-apr2020
description: Learn how to configure user settings for call forwarding and delegation.
---
# Configure call forwarding and delegation settings

This article describes how you, the administrator, can change call forwarding and delegation settings for your users. The call delegation feature in Teams Phone is sometimes referred to in the industry as *shared line appearance*.

A shared line appearance in Teams allows an end user to configure their call forwarding and delegation settings so that they may assign another end user to manage calls on their behalf. This feature is helpful, for example, if someone has an administrative assistant to handle their telephone calls. In the context of call delegation, a delegator is the user authorizing a delegate to make or receive calls on their behalf. Put another way, a delegate can make or receive calls on behalf of the delegator.

As a Teams administrator, you may receive a service request to modify these user settings, for example, if:

- A user is out on sick leave, and you need to ensure that incoming calls to the user are forwarded to a colleague.
- You need to inspect the call forward settings for all users in a department and potentially correct them as appropriate.
- A new assistant is employed, and you need to add the assistant as a delegate for a manager.

You can use the Teams admin center or Teams PowerShell cmdlets to view and change call settings for users.

> [!IMPORTANT]
> This feature is only in Teams Only deployment mode. For more information on Teams deployment modes, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md)

## License required

To set call settings for a user, the user must have an assigned Microsoft Teams Phone license.
In the example where a manager is delegating calls to an administrative assistant, the manager and administrative assistant must each have a Teams Phone license.

Call delegation and is included with Teams Phone. To learn more, see [Teams Phone licensing](teams-phone-licensing.md).

 To receive external calls, managers must also have PSTN connectivity and a phone number assigned.

> [!NOTE]
> A delegate without a phone number assigned must be **EnterpriseVoiceEnabled** using the Teams PowerShell cmdlet `Set-CsPhoneNumberAssignment -Identity \<user\> -EnterpriseVoiceEnabled $true`, see [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment). If a Dial Pad shows in the Calls App of the Delegate, they're correctly configured for Enterprise Voice.  

## Dialing Permissions and Routing

When a delegate makes an outbound Public Switched Telephone Network (PSTN) call on behalf of a delegator, the delegator's settings control the checks for appropriate licensing, dial-out restrictions, and call routing.

In a scenario where the delegate and delegator have different calling policies assigned, the delegate is bound to the settings configured in their calling policy and the permissions of the delegator's calling policy are not transferred to the delegate. Therefore, it's recommended that delegates and delegators are assigned the same calling policy.

## Call delegation availability

The following apps and devices currently support call delegation:

| Capability | Teams Desktop | Teams Mac App | Teams Web App (Edge) | Teams mobile iOS/Android App | Teams IP phone |
|--|--|--|--|--|--|
| Set up delegation | Yes | Yes | Yes | Yes | Yes |
| Receive calls on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a phone number on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Call a Teams user on behalf of another | Yes | Yes | Yes | Yes | Yes |
| Join active calls | Yes | No | Yes | No | Yes |
| See the delegate view of shared lines | Yes | Yes | Yes | Yes | Yes |
| See the delegate view of manager's call activities | Yes | Yes | Yes | No | Yes |
| See the manager view of delegates | Yes | Yes | Yes | Yes | Yes |
| See shared call history | Yes | No | Yes | No | No|
| Delegate or manager can hold or resume | Yes | Yes | Yes | No | Yes |

## Enable delegation

You enable delegation by using the **TeamsCallingPolicy AllowDelegation** setting. You can use Teams admin center or Teams PowerShell. This setting is turned on by default.

When enabled, the end user can configure their delegation relationships directly in Teams.

> [!IMPORTANT]
> When you turn off delegation for a user, you also need to clean up delegation relationships for that user in the Teams admin center to avoid incorrect call routing.

## Use the Teams admin center

You can use the Teams admin center to configure call forward and unanswered settings, group call pickup, and call delegation for your users.

1. In the navigation menu of the Microsoft Teams admin center, select **Voice** > **Calling policies**.

1. Choose the policy you would like to update or select **Add** to create a new policy.

1. Toggle **Delegation for inbound and outbound calls** on.  

1. Select **Save**.

1. In the Teams admin center, go to **Users** > **Manage users** and select a licensed user.

1. On the user details page, go to the **Voice** tab. If the **Voice** tab isn't visible, the user doesn't have a Microsoft Teams Phone license assigned. For more information, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

1. To configure immediate call forward settings, under **Call answering rules**, select:
  
   - **Be immediately forwarded** so that calls to the user don't ring their devices.
   - **Ring the user's devices** to use simultaneous ringing and ring the user's devices first. In the **Also allow** drop-down, select the appropriate simultaneous ringing setting.

     > [!NOTE]
     > You must turn on the **Voice** > **Calling policies** settings for **Call forwarding and simultaneous ringing to people in organization** or **Call forwarding and simultaneous ringing to external phone numbers** for these call forward types and destinations to be available for simultaneous ringing. These settings are on by default.

1. To configure unanswered settings, select the appropriate setting in the **If unanswered** drop-down. In the **Ring for this many seconds before redirecting** drop-down, specify the number of seconds to wait.

1. Select **Save**.

The configuration of call delegation and group call pickup is integrated into the call forward and unanswered settings by selecting the appropriate type. For example, to configure calls to also ring the user's delegates, select **Call delegation** under **Also allow**. Then add the appropriate delegates by selecting **Add people** and selecting **Save**. For more information, see [Call sharing and group call pickup](call-sharing-and-group-call-pickup.md).

This video shows the steps to view and edit the voice settings for a user.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=de43703c-a600-410b-bf30-0385ef726acf]

## Use PowerShell

You can use PowerShell to configure call forward and delegation settings for your users. You use the following cmdlets, which are available in Teams PowerShell module version 4.0 or later:

- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings) - shows call forwarding settings, delegates, and delegator information for a user.
- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings) - sets call forwarding settings for a user.
- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate) - adds a new delegate with permissions for a user.
- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate) - changes permissions for an existing delegate.
- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate) - removes a delegate from a user.

### Display call forward and delegation settings for a user

To display the current call forward and delegation settings for a user, use the  Get-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Get-CsUserCallingSettings -Identity user1@contoso.com
SipUri                    : sip:opr1@contoso.com
IsForwardingEnabled       : True
ForwardingType            : Simultaneous
ForwardingTarget          :
ForwardingTargetType      : MyDelegates
IsUnansweredEnabled       : True
UnansweredTarget          :
UnansweredTargetType      : Voicemail
UnansweredDelay           : 00:00:20
Delegates                 : Id:sip:user2@contoso.com
Delegators                :
CallGroupOrder            : InOrder
CallGroupTargets          : {}
GroupMembershipDetails    :
GroupNotificationOverride : Ring

(Get-CsUserCallingSettings -Identity user1@contoso.com).Delegates

Id             : sip:user2@contoso.com
MakeCalls      : True
ManageSettings : True
ReceiveCalls   : True
```

The output shows that user1 has simultaneous ringing to delegates configured. Unanswered calls are sent to voicemail after 20 seconds. User2 is defined as the delegate with all delegate permissions.

### Set call forward settings for a user

To forward all calls for user1 to user2, use the Set-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Set-CsUserCallingSettings -Identity user1@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType SingleTarget -ForwardingTarget user2@contoso.com
```

To simultaneously ring all delegates for user3, use the Set-CsUserCallingSettings cmdlet, as shown in the following example:

```PowerShell
Set-CsUserCallingSettings -Identity user3@contoso.com -IsForwardingEnabled $true -ForwardingType Simultaneous -ForwardingTargetType MyDelegates
```

The following example uses the Set-CsUserCallingSettings cmdlet to configure a call group for user4 with user5 and user6 as members. All calls to members of the group are forwarded in the order they're defined:

```PowerShell
$cgm = @("user5@contoso.com","user6@contoso.com")

Set-CsUserCallingSettings -Identity user4@contoso.com -CallGroupOrder InOrder -CallGroupTargets $cgm

Set-CsUserCallingSettings -Identity user4@contoso.com -IsForwardingEnabled $true -ForwardingType Immediate -ForwardingTargetType Group
```

For more examples, see [Set-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings).

### Add a calling delegate for a user

To add user2 as a delegate for user1 with all permissions allowed, use the New-CsUserCallingDelegate cmdlet, as shown in the following example:

```PowerShell
New-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $true -ReceiveCalls $true -ManageSettings $true
```

### Change calling delegate permissions

To change delegate permissions--for example to not allow user2 to make calls for user1--use the Set-CsUserCallingDelegate cmdlet as shown in the following example:

```PowerShell
Set-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com -MakeCalls $false
```

### Remove a calling delegate for a user

To remove user2 as a delegate for user1, use the Remove-CsUserCallingDelegate cmdlet, as shown in the following example:

```PowerShell
Remove-CsUserCallingDelegate -Identity user1@contoso.com -Delegate user2@contoso.com
```

## Diagnosing issues with Call Forwarding

If you’re an administrator, you can use the following diagnostic tool to validate that a user is properly configured to forward calls received in Teams to a specific number.

1. Select **Run Tests: Teams Call Forwarding** to populate the diagnostic in the Microsoft 365 admin center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Call Forwarding](https://aka.ms/TeamsCallForwardingDiag)

2. In the Run diagnostic pane, enter the email of the user who's having issues forwarding calls in the **Username or Email** field. Enter the phone number (in E.164 format) that the user wants calls to be forwarded to and then select **Run Tests**.
3. The tests will return the best next steps to address any user settings or configurations to validate that the user is properly configured to forward calls to a specific number in Teams.

## Limitations

Managers can add up to 25 delegates, and delegates can have up to 25 managers. There's no limit to the number of delegation relationships that can be created in a tenant.

If the delegator and delegate aren't in the same geographic location, the PSTN provider must allow caller ID to show up from a different geographic location for a delegated call.

Circular delegation configuration is only permitted for Teams phone devices. If the delegated users also have delegations between them, they'll only be able to see their delegation and not the initial delegation.

## Additional notes

If a user or tenant admin doesn't modify their call answering rules, unanswered calls are forwarded to voicemail after 30 seconds by default. The settings displayed for the user in Teams admin center or Teams PowerShell show the unanswered target as none and a delay of 20 seconds.

## Related articles

- [Configure Teams calling policy](teams-calling-policy.md)
- [New-CsTeamsCallingPolicy](/powershell/module/teams/new-csteamscallingpolicy)
- [Set-CsTeamsCallingPolicy](/powershell/module/teams/set-csteamscallingpolicy)
- [Call sharing and group call pickup](call-sharing-and-group-call-pickup.md)
- [Get-CsUserCallingSettings](/powershell/module/teams/get-csusercallingsettings)
- [Set-CsUserCallingSettings](/powershell/module/teams/set-csusercallingsettings)
- [New-CsUserCallingDelegate](/powershell/module/teams/new-csusercallingdelegate)
- [Set-CsUserCallingDelegate](/powershell/module/teams/set-csusercallingdelegate)
- [Remove-CsUserCallingDelegate](/powershell/module/teams/remove-csusercallingdelegate)
- [Share a phone line with a delegate](https://support.office.com/article/16307929-a51f-43fc-8323-3b1bf115e5a8)
