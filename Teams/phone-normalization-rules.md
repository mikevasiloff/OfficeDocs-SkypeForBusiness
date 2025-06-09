---
title: "Normalization rules for Microsoft Teams dial plans"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 04/25/2025
ms.topic: article
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
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.voice.dialplans.overview
  - Calling Plans
description: "Learn normalization rules for Microsoft Teams user dial plans and trunk dial plans. "
---

# Normalization rules

This article is for IT Admins and IT Pros who are applying normalization rules to Teams dial plans.

For more on Teams dial plans, see [Routing with dial plans](dial-plans-routing-overview.md).

Normalization rules are the translation properties of a Teams dial plan and define how phone numbers expressed in various formats are to be translated. The same number string may be interpreted and translated differently, depending on the locale from which it's dialed. Normalization rules may be necessary if users need to be able to dial abbreviated internal or external numbers.

One or more normalization rules must be assigned to the dial plan. Normalization rules are matched from top to bottom, so the order in which they appear in a tenant dial plan is important. For example, if a tenant dial plan has 10 normalization rules, the dialed number matching logic is tried starting with the first normalization rule. If there isn't a match with the first rule, then a match is attempted with the second rule, and so forth. If a match is made, that rule is used and there's no effort to match any other rules that are defined.

> [!NOTE]
> Microsoft now enforces the rule that there can be no more than 50 normalization rules in a given dial plan.

### Determining the required normalization rules

Because a tenant dial plan is merged with a given user's service country/region dial plan, it's likely that the service country/region dial plan's normalization rules need to be evaluated. The evaluation determines which tenant dial plan normalization rules are needed.

The **Get-CsEffectiveTenantDialPlan** cmdlet can be used for this purpose. The cmdlet takes the user's identity as the input parameter and returns all normalization rules that are applicable to the user.

### Creating normalization rules

Normalization rules use .NET Framework regular expressions to specify numeric match patterns that the server uses to translate dial strings to E.164 format. Normalization rules can be created by specifying the regular expression for the match and the translation to be done when a match is found. When you finish, you can enter a test number to verify that the normalization rule works as expected.

For details about using .NET Framework regular expressions, see [.NET Framework Regular Expressions](/dotnet/standard/base-types/regular-expressions).

For validating regular expressions, see [Regex101 (an interactive tool for testing and learning regular expressions)](https://regex101.com)

See [Create and manage dial plans](create-and-manage-dial-plans.md) to create and manage normalization rules for your tenant dial plans.

> [!NOTE]
> Normalization rules with the first token as optional are currently not supported on 3pip devices (for example, Polycom VVX 601 model). If you want to apply normalization rules with optionality on 3pip devices, you should create two normalization rules instead of one. For example, the rule ^0?(999)$ should be replaced by the following two rules: (999)$ (Translation:$1) and ^0(999)$ (Translation:$1).
>
> Validate all regular expressions used in dial plan normalization rules as invalid expressions may result in client or service issues. 


### Sample normalization rules

The following table shows sample normalization rules that are written as .NET Framework regular expressions. The samples are examples only and aren't meant to be a prescriptive reference for creating your own normalization rules.

<a name="regularexpression"> </a>
**Normalization rules using .NET Framework regular expressions**

| Rule name<br/> | Description<br/> | Number pattern<br/> | Translation<br/> | Example<br/> |
|:-----|:-----|:-----|:-----|:-----|
|4digitExtension  <br/> |Translates 4-digit extensions.  <br/> |^(\\d{4})$  <br/> |+1425555$1  <br/> |0100 is translated to +14255550100  <br/> |
|5digitExtension  <br/> |Translates 5-digit extensions.  <br/> |^5(\\d{4})$  <br/> |+1425555$1  <br/> |50100 is translated to +14255550100  <br/> |
|7digitcallingRedmond  <br/> |Translates 7-digit numbers to Redmond local numbers.  <br/> |^(\\d{7})$  <br/> |+1425$1  <br/> |5550100 is translated to +14255550100  <br/>|
|RedmondOperator  <br/> |Translates 0 to Redmond Operator.  <br/> |^0$  <br/> |+14255550100  <br/> |0 is translated to +14255550100  <br/> |
|RedmondSitePrefix  <br/> |Translates numbers with on-net prefix (6) and Redmond site code (222).  <br/> |^6222(\\d{4})$  <br/> |+1425555$1  <br/> |62220100 is translated to +14255550100  <br/> |
|5digitRange  <br/> |Translates 5-digit extensions starting with the digit range between 3-7 inclusive.  <br/> |^([3-7]\\d{4})$  <br/> |+142555$1 <br/> |54567 is translated to +14255554567  <br/> |
|PrefixAdded  <br/> |Adds a country prefix in front of a 9 digit number with restrictions on the first and third digits.  <br/> |^([2-9]\\d\\d[2-9]\\d{6})$  <br/> |1$1  <br/> |4255554567 is translated to 14255554567  <br/> |
|NoTranslation  <br/> |Match 5 digits but no translation.  <br/> |^(\\d{5})$  <br/> |$1  <br/> |34567 is translated to 34567  <br/> |

 **Redmond dial plan based on normalization rules shown in previous table.**
 
 The following table illustrates a sample dial plan for Redmond, Washington, United States, based on the normalization rules shown in the previous table.

| Redmond dial plan<br/> |
|:-----------------------|                                                                                                                      
| 5digitExtension <br/> |                                                                                                                                    
| 7digitcallingRedmond <br/> |
| RedmondSitePrefix <br/> |
| RedmondOperator <br/> |

> [!NOTE]
> The normalization rules names shown in the preceding table don't include spaces, but using spaces is a matter of choice. The first name in the table, for example, could be written "5 digit extension" or "5-digit Extension" and still be valid.

## Related topics

[Create and manage dial plans](create-and-manage-dial-plans.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
