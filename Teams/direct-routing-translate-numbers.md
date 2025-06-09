---
title: "Translate phone numbers for Direct Routing"
ms.reviewer: filippse
ms.date: 04/25/2025
ms.author: scottfrancis
author: sfrancis206
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to configure Microsoft Phone System Direct Routing."
---

# Translate phone numbers to an alternate format

This article describes how to translate numbers for outbound and inbound calls to an alternate format. This is step 4 of the following steps for configuring Direct Routing:

- Step 1. [Connect the SBC with Microsoft Phone System and validate the connection](direct-routing-connect-the-sbc.md) 
- Step 2. [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)   
- Step 3. [Configure voice routing](direct-routing-voice-routing.md)
- **Step 4. Translate numbers to an alternate format**   (This article)

For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

Sometimes tenant administrators may want to change the number for outbound and/or inbound calls based on the patterns they created to ensure interoperability with Session Border Controllers (SBCs). This article describes how you can specify a Number Translation Rules policy to translate numbers to an alternate format. 

You can use the Number Translation Rules policy to translate numbers for the following:

- Outbound calls: Calls from a Teams client (caller) to a PSTN endpoint (callee)
- Inbound calls: Calls from a PSTN endpoint (caller) to a Teams client (callee)

## Route-based number translations - for outbound calls

Number translation rules are optionally applied to called numbers that are passed through this route, to keep number formats synchronized between your tenant and your Direct Routing PSTN solution.

Once a user dials a number, it processes through the user's effective dial plan. To learn more about the user's effective dial plan, see [Dial Plan overview](dial-plans-routing-overview.md). Teams matches the dial plan-normalized number to an approved PSTN usage for routing to the PSTN, and the call is directed to a voice route. The voice route is associated with an SBC (Session Border Controller), and there may be instances where you want to manage the format in which your SBC receives the called number-string.

To translate a called number-string into an alternate format, create an outbound number translation rule and apply it to the SBC's profile (also known as PSTN gateway) in Teams. See [Configuring translation rules with PowerShell](#configuring-translation-rules-with-powershell).

> [!NOTE]
> In the scenario where the user's effective dial plan doesn't apply normalization rules to the dialed number, the Teams service dial plan prepends "+CC" to the number, where CC is the country/region code of the dialing user's usage location. This applies to Calling Plans, Direct Routing, and PSTN Conference dial-out scenarios. </br>To avoid double normalization (from the user's effective dial plan and a route-based number translation rule), it's recommended that Direct Routing customers use dial plans, normalize numbers to include a +, and then remove the + using a route-based translation rule.

## Route-based number translations - for inbound calls

Routing an inbound phone call to a Teams user uses a process called [Reverse Number Lookup (RNL)](dial-plans-routing-overview.md#number-lookup-for-inbound-calls). Instead of referencing a Teams user's contact name to look up their number, RNL looks in your directory for the dialed number-string of a call, finds the user or resource account in your tenant that is assigned with the same number-string, and sets up the incoming call with that user or resource.

In a Direct Routing deployment you could have a scenario where there's no digit translation rules configured in the SBC, and the SBC is just passing through the dialed number-string received from the PSTN. If the inbound call's number-string isn't offering a format matched to the standardized number-string assigned to your Teams user and resource accounts, you can use Teams to apply a route-based, inbound-number translation rule to the SBC's configuration profile and translate the inbound, called number into your expected number-string format. See [Configuring translation rules with PowerShell](#configuring-translation-rules-with-powershell).

## Considerations

The number translation rules are applied at the SBC level. You can assign multiple translation rules to an SBC, which are applied in the order that they appear when you list them in PowerShell. You can also change the order of the rules in the policy.

> [!NOTE]
> The maximum total number of translation rules is 400, maximum translation parameter-name length is 100 symbols, maximum translation parameter-pattern length is 1024 symbols, and maximum translation parameter-translation length is 256 symbols.

### Configuring translation rules with PowerShell

To create, modify, view, and delete number manipulation rules, use the [New-CsTeamsTranslationRule](/powershell/module/teams/new-csteamstranslationrule), [Set-CsTeamsTranslationRule](/powershell/module/teams/set-csteamstranslationrule), [Get-CsTeamsTranslationRule](/powershell/module/teams/get-csteamstranslationrule), and [Remove-CsTeamsTranslationRule](/powershell/module/teams/remove-csteamstranslationrule) cmdlets.

To assign, configure, and list number manipulation rules on SBCs, use the [New-CSOnlinePSTNGateway](/powershell/module/teams/new-csonlinepstngateway) and [Set-CSOnlinePSTNGateway](/powershell/module/teams/set-csonlinepstngateway) cmdlets together with the InboundTeamsNumberTranslationRules, InboundPSTNNumberTranslationRules, OutboundTeamsNumberTranslationRules, and OutboundPSTNNumberTranslationRules parameters.

## Example SBC configuration

For this scenario, the New-CsOnlinePSTNGateway cmdlet is run to create the following SBC configuration:

```PowerShell
New-CSOnlinePSTNGateway -Identity sbc1.contoso.com -SipSignalingPort 5061 –InboundTeamsNumberTranslationRules ‘AddPlus1’, ‘AddE164SeattleAreaCode’ -InboundPSTNNumberTranslationRules ‘AddPlus1’ -OutboundPSTNNumberTranslationRules ‘AddSeattleAreaCode’,‘StripPlus1’  -OutboundTeamsNumberTranslationRules ‘StripPlus1’
```

The translation rules assigned to the SBC are summarized in the following table:

|Name  |Pattern |Translation  |
|---------|---------|---------|
|AddPlus1     |^(\d{10})$          |+1$1          |
|AddE164SeattleAreaCode      |^(\d{4})$          | +1206555$1         |
|AddSeattleAreaCode    |^(\d{4})$          | 425555$1         |
|StripPlus1    |^\\+1(\d{10})$          | $1         |

In the following examples, there are two users, Alice and Bob. Alice is a Teams user whose number is +1 206 555 0100. Bob is a PSTN user whose number is +1 425 555 0100.

## Example 1: Inbound call to a 10-digit number

Bob calls Alice using a non-E.164 10-digit number. Bob dials 2065550100 to reach Alice.
SBC uses 2065550100 in the RequestURI and To headers and 4255550100 in the From header.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:2065550100@sbc.contoso.com|INVITE sip:+12065550100@sbc.contoso.com|InboundTeamsNumberTranslationRules ‘AddPlus1’|
|TO    |TO: \<sip:2065550100@sbc.contoso.com>|TO: \<sip:+12065550100@sbc.contoso.com>|InboundTeamsNumberTranslationRules ‘AddPlus1’|
|FROM   |FROM: \<sip:4255550100@sbc.contoso.com>|FROM: \<sip:+14255550100@sbc.contoso.com>|InboundPSTNNumberTranslationRules ‘AddPlus1’|

## Example 2: Inbound call to a four-digit number

Bob calls Alice using a four-digit number. Bob dials 0100 to reach Alice.
SBC uses 0100 in the RequestURI and To headers and 4255550100 in the From header.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:0100@sbc.contoso.com          |INVITE sip:+12065550100@sbc.contoso.com           |InboundTeamsNumberTranslationRules ‘AddE164SeattleAreaCode’        |
|TO    |TO: \<sip:0100@sbc.contoso.com>|TO: \<sip:+12065550100@sbc.contoso.com>|InboundTeamsNumberTranslationRules ‘AddE164SeattleAreaCode’         |
|FROM   |FROM: \<sip:4255550100@sbc.contoso.com>|FROM: \<sip:+14255550100@sbc.contoso.com>|InboundPSTNNumberTranslationRules ‘AddPlus1’        |

## Example 3: Outbound call using a 10-digit non-E.164 number

Alice calls Bob using a 10-digit number. Alice dials 425 555 0100 to reach Bob.
SBC is configured to use non-E.164 10-digit numbers for both Teams and PSTN users.

In this scenario, a dial plan translates the number before sending it to the Direct Routing interface. When Alice enters 425 555 0100 in the Teams client, the number is translated to +14255550100 by the country/region dial plan. The resulting numbers are a cumulative normalization of the dial plan rules and Teams translation rules. The Teams translation rules remove the "+1" that was added by the dial plan.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:+14255550100@sbc.contoso.com          |INVITE sip:4255550100@sbc.contoso.com       |OutboundPSTNNumberTranslationRules ‘StripPlus1’         |
|TO    |TO: \<sip:+14255550100@sbc.contoso.com>|TO: \<sip:4255555555@sbc.contoso.com>|OutboundPSTNNumberTranslationRules ‘StripPlus1’       |
|FROM   |FROM: \<sip:+12065550100@sbc.contoso.com>|FROM: \<sip:2065550100@sbc.contoso.com>|OutboundTeamsNumberTranslationRules ‘StripPlus1’         |

## Example 4: Outbound call using a four-digit non-E.164 number

Alice calls Bob using a four-digit number. Alice uses 0100 to reach Bob from Calls or by using a contact.
SBC is configured to use non-E.164 four-digit numbers for Teams users and 10-digit numbers for PSTN users. The dial plan isn't applied in this scenario.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:0100@sbc.contoso.com           |INVITE sip:4255550100@sbc.contoso.com       |InboundTeamsNumberTranslationRules ‘AddSeattleAreaCode’         |
|TO    |TO: \<sip:0100@sbc.contoso.com>|TO: \<sip:4255555555@sbc.contoso.com>|InboundTeamsNumberTranslationRulesList ‘AddSeattleAreaCode’       |
|FROM   |FROM: \<sip:+12065550100@sbc.contoso.com>|FROM: \<sip:2065550100@sbc.contoso.com>| InboundPSTNNumberTranslationRules ‘StripPlus1’ |

## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)

[Dial plans and routing](dial-plans-routing-overview.md)
