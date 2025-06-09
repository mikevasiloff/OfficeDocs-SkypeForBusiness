---
title: What's the status of your port orders?
ms.author: scottfrancis
author: sfrancis206
manager: pamgreen
ms.reviewer: mikedav, roykuntz, jastark, leiaglezer
ms.date: 01/22/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Calling Plans
description: Learn how to get the status of your telephone number port orders for Microsoft Teams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
---

# What's the status of your port orders?

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Microsoft Calling Plans

To see the status of your port order, in the left navigation of the Microsoft Teams admin center, go to  > **Voice** > **Phone numbers**, and then select **Order history**. Each port order status is listed in the **Status** column.

If the **Status** column isn't listed, select the gear-shaped setting icon in the **Order history** table, and enable the **Status** column.

You can view orders that are saved but not submitted, and orders that are submitted and in progress by selecting the order name.

|Status |Description | Supported Action | Considerations and Rules |
|:-----|:-----|:-----|:-----|
|Draft |You started your order, but it isn't yet validated. |You can edit, delete, or validate your order. |Only available in the new port wizard (for example, US & CA currently). </br>Your LOA isn't yet generated. |
|Not submitted |Your order is validated and ready to be signed and submitted. |You can edit or delete your order. |In this status, you need to sign and submit your LOA in one of two ways in the port wizard: </br>1. Upload a signed LOA (available in all supported markets), </br>2. Request an E-signature submission (US & CA only currently). |
|Manual review |Your order is in review with Microsoft support. |You can edit the order name, extra contacts, and number usage. |Microsoft support corrects and resubmits the order and contacts you if other information is required. |
|Pending operator approval |Your order is submitted to the losing provider and awaiting their response. |You can edit the order name, extra contacts, and number usage. |Planned port date is available in the order details in Teams admin center. |
|Exception |The carrier that currently owns your porting phone numbers rejects your order. |You can edit the order name, extra contacts, and number usage. |Exceptions are due to incorrect info in the LOA (for example, PIN, ZIP code). </br></br>Microsoft support corrects and resubmits the order and contacts user if additional information is required. |
|Approved (FOCAccepted) |Your order is approved to port to Microsoft. |You can edit the order name, extra contacts, and number usage. |**Direct Routing and Operator Connect preassignment in the US or CA**: preassignment isn't allowed. But we can maintain your existing number assignment. Ensure you have a Calling Plan license and emergency calling location assigned for each number before port completion. </br></br>**Direct Routing and Operator Connect preassignment outside US or CA**: preassignment isn't allowed, and numbers transfer as unassigned into Calling Plans. </br></br>**New number preassignment**: If you're porting numbers from an external carrier into Calling Plans, preassignment is allowed. The rules are as follows: </br></br>1. A phone system license must be enabled for the user. </br>2. A phone resource account license must be enabled for the resource account. </br>3. A Calling Plan license must be enabled for the intended users or resource account: </br></br>  a. The intended user's usage location must match the telephone number's country for primary and private phone. </br>  b. The intended resource account's usage location must match the telephone number's country for assignment. </br></br>4. For Toll Free numbers, the tenant must have a positive balance of [Communication Credits](../what-are-communications-credits.md).
|Completed |Porting complete and numbers are active in Microsoft’s system. |No fields are editable. | |
|Cancellation requested |Customer requests cancellation. |No fields are editable. | |
|Canceled |Port order is canceled and closed. |No fields are editable. |The numbers aren't ported, and no further actions are allowed. If you must start a new port order, no prior validations or documents are reused. |

Keep in mind the lead times for order processing, as described in [Port planning](port-order-overview.md).

If you need to inquire about an existing order, use the [Phone Number Service Center Portal](https://pstnsd.powerappsportals.com/) to contact the [Telephone Number Services (TNS) Service Desk](../manage-phone-numbers-for-your-organization/contact-tns-service-desk.md).

When making an inquiry about an existing port request, find the related case for your order in the Phone Number Service Center Portal and provide your inquiry in the case comments, rather than opening a new case.

## Related articles

- [What's a port order?](port-order-overview.md)
- [Transfer phone numbers to Teams](transfer-phone-numbers-to-teams.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
