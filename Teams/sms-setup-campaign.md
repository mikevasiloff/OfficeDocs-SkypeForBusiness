---
title: Set up a Campaign for SMS in Microsoft Teams
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: nijait, julienp
ms.date: 02/24/2025
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
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
description: Learn how to set up a Campaign to enable SMS in Microsoft Teams.
---

# Create a Campaign for SMS in Microsoft Teams

> [!NOTE]
> Service update: If you receive a Brand or Campaign rejection, our Telephone Number Services team is aware and managing a case with you through the [Phone Number Service Center](https://pstnsd.powerappsportals.com) portal. Due to a high volume of requests for SMS in Teams, processing times to facilitate approvals of rejected Brand and Campaign applications for SMS in Teams may take 4 to 6 weeks. We appreciate your patience as we work diligently to address all requests.

This article is for IT administrators and IT professionals who are enabling Short Message Service (SMS) in Teams and need to register their company's campaign.

Before reading this article, make sure you've read [Plan for SMS in Teams](sms-overview.md) and [Step 1: Create a brand](sms-setup-brand.md).

> [!NOTE]
> SMS in Teams is only available on Calling Plan phone numbers in the United States (including Puerto Rico) and Canada.
> Customers must have an approved Brand and Campaign before enabling SMS on Teams Calling Plan numbers.

## Prerequisites

Ensure fundamental understanding of the *purpose* for a Campaign, as described in [Learn about SMS Texting in Teams](sms-overview.md).

Administrators must have one of the following role-based access control (RBAC) roles assigned:

- Teams Administrator
- Teams Communications Administrator
- Teams Telephony Administrator

## Campaign registration details for SMS in Teams

After you verify your brand and your brand's status shows as **Approved** in the Teams admin center, proceed with the campaign registration.

The 10DLC (10-digit long code) registration process involves validating your **Campaign**, or organization's objective, for accessing SMS service on 10DLC phone numbers. To get your campaign approved, you must submit details via the Teams admin center. This section provides details required to register your campaign.

> [!IMPORTANT]
> To increase the likelihood of your campaign being approved and to ensure 10DLC program compliance, please review the following information.

### Campaign Use Case

The use case specifies how the SMS service is used for the given campaign. For SMS in Teams, the use case is Unified Communications as a Service (UCaaS), Low Volume. Microsoft defines the use case and you can't change the use case.

### Campaign Description

The description provides a comprehensive explanation of the SMS service utilization, type of messages sent, and your target audience.  

### SMS Privacy Policy

When you register a campaign, you must provide a link to your brand's Privacy Policy related to SMS messaging. The Privacy Policy link can be a webpage or an online file that's publicly accessible.

The Privacy Policy must clearly describe the following information:

- How consumer data is used and shared (if applicable)
- How consumers can contact the message sender
- A statement that says "mobile opt-in information won't be shared with third parties for marketing purposes"

If your company doesn't have a privacy statement related to SMS messaging, you can use a Microsoft-provided template, completed with your company's information. For the template, see [SMS privacy statement and terms and conditions template](/microsoftteams/sms-privacy-terms-template).

### SMS Terms and Conditions

When registering a campaign, you must provide a link to your brand's Terms & Conditions related to SMS. The Terms & Conditions URL can be a webpage or an online file that is publicly accessible.

If your company doesn't have a privacy statement related to SMS messaging, you can use a Microsoft-provided template, completed with your company's information. For the template, see [SMS privacy statement and terms and conditions template](/microsoftteams/sms-privacy-terms-template).

The Terms and Conditions must have an SMS disclosure that includes the types of messages consumers can expect to receive, texting cadence, message and data rate notices, privacy policy links, HELP information, and opt-out instructions.

The Terms & Conditions must include the following information:

- Brand name

- Types of messages the consumer can expect to receive

- Message frequency disclosure (for example, "Msg frequency varies")

- Message and data rates disclosure (for example, "Msg & data rates may apply")

- Support contact information (for example, "send HELP for support," "contact help@contoso.com for support")

- Opt-out information (for example, "Send STOP to unsubscribe")

### Call to Action

The Call to Action clearly and transparently describes how a recipient opts-in to receive messages from you. The Call to Action must be explicit, must ensure that users understand what they are consenting to, and must be collected in a direct and verifiable way. Call To Action should be specific to SMS messaging services and not bundled with other services or be hidden within terms & conditions or other agreements.

The Call-to-Action disclosure refers to the language provided to the recipient informing them that they are opting in and must include the following information:

- Brand name

- Types of messages the consumer can expect to receive

- Message frequency disclosure (for example, "Msg frequency varies")

- Message and data rates disclosure (for example, "Msg & data rates may apply")

- Opt-in information (see the following table for examples)

- Help information (for example, "send HELP for help")

- Opt-out information (for example, "send STOP to unsubscribe")

- Privacy Policy link

- Terms and Conditions link

The table below shows examples of how users might opt in:

|Method|Description|Requirement|Examples|
| -------- | -------- | -------- | -------- |
|Web Sign-Up|Users enter their phone number on a website and check a box agreeing to receive messages.  |Provide a direct link to the submission form or the webpage.  |"By submitting this form, you consent to receive [type of text messages] from [Brand Name] at the number provided. Msg & data rates may apply. Msg frequency varies. Unsubscribe by replying STOP or clicking the unsubscribe link. Reply HELP for help. Phone numbers aren't shared with third parties. Privacy Policy [link] & Terms [link]."|
|Text Message Keyword|Users opt-in by texting a keyword (for example, "START") to a specific number.|Explain how users learn about the keyword, such as via a webpage link or screenshot.|"By texting START to [phone number], you consent to receive text messages from [Brand Name]. Msg & data rates may apply. Msg frequency varies. Unsubscribe by replying STOP. Reply HELP for help. Phone numbers won't be shared with third parties. Privacy Policy [link] & Terms [link]."|
|Verbally|Users opt-in verbally at a physical location or over the phone.|Provide a copy of the script used to inform users about the opt-in.|"[Brand name] collects opt-in verbally at their locations or over the phone. Customers provide their number and are informed that 'Message and data rates may apply', 'Message frequency varies', and they can 'text HELP for support or STOP to unsubscribe.' Phone numbers won't be shared with third parties. Privacy Policy [link] & Terms [link]."|

> [!NOTE]
> The provided examples are for illustrative purposes and don't guarantee the approval of your campaign. It's important to be as detailed and accurate as possible in your Call to Action.

### Sample Messages

These sample messages are examples of messages that you send. Sample Messages must align with the campaign use case.

The Sample Messages must include the following information:

- Brand name
- Opt-out language in at least one sample message
- An embedded link in at least one sample message if "Yes" is selected for **Embedded Link** under Content Attributes

### Campaign and Content Attributes

The following information should be included in your campaign:

#### Opt-In Message

When a Teams user sends the first message in an SMS conversation or when recipient replies START, the **Opt-In Message** is automatically sent to the recipient.

The Opt-In Message must include the following information:

- Brand name
- Message frequency disclosure (for example, "Msg frequency varies")
- Message and data rates disclosure (for example, "Msg & data rates may apply")
- Help information (for example, "send HELP for help")
- Opt-out information (for example, "send STOP to unsubscribe")

An example might look like this:
>Thank you for opting in to receive [type of messages] from [Brand Name]. Msg frequency varies. Msg & data rates may apply. Reply HELP for help. Reply STOP to opt out from receiving messages from this number.*" automated message is sent to the recipient send START to resume a conversation.

> [!IMPORTANT]
> Only the keywords START, HELP, and STOP, QUIT, END, REVOKE, OPT OUT, CANCEL, UNSUBSCRIBE are monitored and enforced in SMS in Teams.

##### Opt-Out Message

When recipient replies STOP, the Opt-Out Message is automatically sent to the recipient.

The Opt-Out Message must include the following information:

- Brand name
- Confirmation that the recipient will receive no further messages.

An example might look like this:
>You have successfully opted out of messages from this [Brand Name] number. You'll receive no further messages. Reply START to resume. Msg & data rates may apply.

> [!IMPORTANT]
> Only the keywords START, HELP, and STOP, QUIT, END, REVOKE, OPT OUT, CANCEL, UNSUBSCRIBE are monitored and enforced in Teams SMS.

##### Help Message

When recipient replies HELP, the Help Message is automatically sent to the recipient.

The Help Message must include the following information:

- Brand name
- Support contact information (for example, an email address, phone number, or website)

 An example might look like this:
>Thank you for contacting [Brand Name] support. Please email us at [email address] for support. Reply STOP to opt-out from receiving messages from this number. Msg & data rates may apply.

> [!IMPORTANT]
> Only the keywords START, HELP, and STOP, QUIT, END, REVOKE, OPT OUT, CANCEL, UNSUBSCRIBE are monitored and enforced for SMS in Teams.

##### Content

The following table provides a detailed description of the content attributes of a campaign:

|Content|Description|
| -------- | -------- |
|**Direct Lending or Loan Arrangement**| Indicates if the brand engages in lending, even if the campaign isn't related to lending or loan arrangement.|
|**Embedded Link**|Indicates if embedded links are sent in messages. Public URL shorteners (bitly, tinyurl) aren't accepted. If selected, at least one sample message must include an embedded link.|
|**Embedded Phone Number**|Indicates if embedded phone numbers are sent in messages, excluding HELP contact. If selected, at least one sample message must include an embedded phone number.|
|**Age-Gated Content**|Indicates if the content includes age-gated materials.|

## Create an SMS in Teams Campaign in Teams admin center

The Teams admin center allows you to provide the minimum details about your company's Campaign.

To initiate Campaign approval application, do the following steps:

1. In the Teams admin center, navigate to **Voice** > **Service configuration** > **SMS** > **Step 2: Create campaign**.
1. Select **Create Campaign / Update Campaign / View details** to open a right-side configuration slide-out and populate the fields with your company's campaign information. Your Brand must be approved before you can apply for Campaign approval.

Populate your campaign application to TCR according to the following steps associated with the Campaign field sections:

- [Step 1: Campaign details](#step-1-check-campaign-details)
- [Step 2: Accept Terms and Conditions](#step-2-accept-terms-and-conditions)
- [Step 3: Submit your Campaign and view Campaign status](#step-3-submit-your-campaign-and-view-status)

### Step 1: Check Campaign details

In the campaign form, provide details of your company's plan for SMS operations, if any.

- **Campaign details**

  - *Description*: A description for the campaign, explaining its purpose and target audience.
  - *Call-to-Action/Message Flow*: A description of how recipients are opt-in to receive messages from you (such as opt-in process, expected interactions).
  - *Sample Message*: A sample message that aligns with the campaign's use case. Multiple sample messages are acceptable. If embedded phone number or link is selected, please include an embedded phone number or link in your sample messages.
  - *Privacy Policy*: A link to your privacy policy related to SMS services. It can be a webpage or an online file that is publicly accessible.
  - *Terms and Conditions*: A link to your terms and conditions related to SMS services. It can be a webpage or an online file that is publicly accessible.

- **Campaign attributes**

  - *Opt-in Message*: the content of the automated message sent to the recipient when Teams users sends the first message in an SMS conversation or when recipient sends START.
  - *Opt-out* *Message*: the content of the automated message sent to the recipient when they send STOP.
  - *Help* *Message*: the content of the automated message sent to the recipient when they send HELP.

- **Content attributes**

  - *Direct Lending or Loan Arrangement*: Indicates if the campaign involves any lending or loan arrangements.
  - *Embedded Link*: Indicates if the campaign includes an embedded link.
  - *Embedded Phone Number*: Indicates if a phone number is embedded within the campaign content.
  - *Age-gated Content*: Indicates if the content is age-restricted.

### Step 2: Accept Terms and Conditions

Select the box to accept the terms and conditions.

The terms as follows relate to Microsoft sharing your brand and campaign information with a 10DLC operator.

>Teams SMS services involve an integration between Microsoft and the underlying carrier, aggregator, or operator ("Operator"). Microsoft must share application details and/or brand information with the Operator to ensure that the program meets regulatory guidelines and standards set by operators. The Operator is the final reviewer and approver of your service application. If the details you provide on your application change, it's your responsibility to resubmit your application with up-to-date information. By submitting an application, you agree that Microsoft may share the application details as necessary for provisioning the Teams messaging service.

### Step 3: Submit your Campaign and view status

After reviewing your Campaign's details and accepting Microsoft's terms and conditions, select **Submit**.

After submission, the Campaign status shows as **Submitted** and the campaign information can't be modified.

- If your campaign is approved, your campaign status updates to **Approved** and you can move on to [Step 3: Enable SMS](sms-management.md).

- If your campaign isn't approved, the status changes to **Microsoft Support Engaged**, and our support team may contact the support representative of your brand for further assistance.

> [!NOTE]
> If your campaign isn't approved, a Microsoft case is automatically opened on your behalf with Microsoft's Telephone Number Services (TNS) - Service Desk. You can view your case by navigating to the [Phone Number Service Center](https://pstnsd.powerappsportals.com), and then selecting the tab for **My Company Cases**. Open the case, and you can interact with the Telephone Number Services - Service Desk team about the details and status of the case.

## Considerations

### Building a campaign with more than 49 SMS-enabled numbers

If you require more than 49 SMS-enabled numbers, you must work with [Microsoft's Telephone Number Services - Service Desk](contact-tns-service-desk.md) so that they can work with you on an exception to the default maximum campaign quantity.
Provide the TNS Service Desk with the number of SMS-enabled numbers and the expected volume of messages sent and received per month, so that they can support the required provisioning.
> [!NOTE]
>Enabling over 49 phone numbers is only allowed on an Approved campaign and may take 20 business days. These timelines are approximate and subject to change.

### Campaign approval process timeline

The review and approval process may take 20 business days. These timelines are for informational purposes only and may vary. 

If you submit incorrect campaign information, or if you have questions related to the process, [contact Microsoft's Telephone Number Services (TNS) - Service Desk](contact-tns-service-desk.md).

## Related topics

- [Microsoft Calling Plan Overview](calling-plan-overview.md)

- [Getting numbers with Microsoft Calling Plan](manage-phone-numbers-landing-page.md)

- [Learn about SMS texting in Teams](sms-overview.md)

- [SMS privacy statement and terms and conditions template](sms-privacy-terms-template.md)

- [Step 3: Enable SMS](sms-management.md)

- [Plan for SMS in Microsoft Teams](sms-overview.md)

- [Microsoft's SMS in Teams messaging policy](sms-microsoft-teams-policy.md)
