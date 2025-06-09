---
title: Enable and manage SMS in Microsoft Teams
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: nijait, julienp
ms.date: 02/24/2025
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection:
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
  - CSH
description: Enable and manage SMS in Microsoft Teams
---

# Enable and manage SMS in Microsoft Teams

This article is for IT administrators and IT professionals who are administering the Short Message Service (SMS) usage in Microsoft Teams. You can manage SMS for Teams through the Teams admin center.

> [!NOTE]
> SMS in Teams is only available on Calling Plan phone numbers in the United States (including Puerto Rico) and Canada.

## Prerequisites

### Brand and Campaign

To ensure successful enablement of SMS for a Teams Calling Plan phone number, confirm service enablement is configured, as described in the articles [Step 1: Create brand](sms-setup-brand.md) and [Step 2: Create campaign](sms-setup-campaign.md).

### Licensing

To enable Teams users with SMS capabilities, you must assign the following licenses to your users:

- Teams
- Teams Phone
- Microsoft Teams Calling Plan

For more information, see [SMS Licensing](sms-overview.md#licensing).
  
### Billing mechanism

A tenant **billing mechanism** *should* be in place for SMS consumption overages and *must* be in place for Pay-as-you-go Calling Plans.

Funding for usage overages is supported either with prepaid Communication Credits using a Microsoft Online Subscription Agreement (MOSA) or with postpaid invoicing using a Microsoft Customer Agreement (MCA). For more information, see [SMS overview of usage and billing](sms-overview.md#usage-and-billing).

#### Permissions

As an administrator, you must be assigned one of the following Role-Based Access Control (RBAC) roles:

- Teams Administrator
- Teams Communications Administrator
- Teams Telephony Administrator

For more information about Teams administrator roles, see [Use Microsoft Teams administrator roles to manage Teams](using-admin-roles.md).

## Manage SMS in Teams for Users

### SMS status for phone numbers

Not all phone numbers support SMS in Teams. In the Teams admin center, under **Voice** > **Phone numbers** > **Numbers**, the **SMS status** shows whether a number can use SMS in Teams and displays the phone number's current SMS in Teams status. The following table lists the **SMS status** values and their descriptions.

|SMS status |Description|
| -------- | -------- |
|Not available| SMS in Teams isn't available on the phone number. SMS might not be available due to the current phone number's configuration&mdash;for example, the phone number is assigned to a Resource Account, or the phone number itself doesn't support SMS.|
|Not Activated| SMS in Teams is available on the phone number, but you haven't activated it yet. You can select **Enable SMS** to activate SMS in Teams for this phone number.|
|In Progress|SMS in Teams activation is in progress and might take up to two hours.|
|Activated|SMS in Teams is activated on the phone number. You can select **Disable SMS** to turn off SMS in Teams for this phone number.|

#### Turn on SMS for a user

To enable SMS in Teams for a user, you must turn on SMS for a user's phone number.

1. In Teams admin center, navigate to the left side rail, select **Voice** > **Phone numbers** > **Numbers**.
1. Find and select the number for the user.
1. In the contextual menu just above the list of phone numbers, select **Enable SMS**.

If the number isn't already assigned to a user, you can assign that number to a user. For more information on number management, see [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).

#### Turn off SMS for a user

To turn off SMS for a user, do the following steps:

1. In the Teams admin center, navigate to the left side rail, select **Voice** > **Phone numbers** > **Numbers**.
1. Find and select the number for the user.
1. In the contextual menu just above the list of phone numbers, select **Disable SMS**.

## SMS usage report

To view itemized SMS reporting, do the following steps:

1. In Teams admin center, navigate to the left side rail, select **Reports & analytics** > **Usage reports** > **PSTN and SMS Usage**.
1. Choose a date range.
1. Select **Run report**.

For more information, see [Microsoft Teams PSTN Usage report](.\teams-analytics-and-reports\pstn-usage-report.md).

## Related topics

- [SMS overview](sms-overview.md)

- [Step 1: Create brand](sms-setup-brand.md)

- [Step 2: Create campaign](sms-setup-campaign.md)
