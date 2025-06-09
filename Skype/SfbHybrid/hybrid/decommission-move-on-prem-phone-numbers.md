---
ms.date: 04/22/2025
title: Move phone numbers to the cloud
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: pavellatif
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: upgrade-and-migration-article
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Move phone numbers to Teams before decommissioning a Skype for Business on-premises environment."

---

# Upload Direct Routing numbers to your tenant and manage them online

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

This article describes how to move desired phone numbers from your Skype for Business on-premises deployment to Microsoft's cloud so that they can be managed using Microsoft's Teams admin center or Teams PowerShell.

Use the guidance in this article to move phone numbers online. 

This guidance can be performed at any time before [Clearing Skype for Business attributes for all on-premises users in Active Directory](cloud-consolidation-managing-attributes.md#model-2---clear-skype-for-business-attributes-for-all-on-premises-users-in-active-directory).

## Uploading numbers to online

> [!Note]
> Before beginning this process, ensure user has proper Teams Phone licensing.

Uploading your Direct Routing phone numbers to Microsoft's telephone number management inventory is optional. However, if you want to administer your phone numbers online, this is the preferred method to convert on-premises Direct Routing number to online Direct Routing number.

Once uploaded, Teams controls the service configuration of the numbers and the on-premises Active Directory configuration offered in every following Directory Sync is rejected.

Uploaded phone numbers can be viewed in the Teams admin center under **Phone Numbers** or by using the PowerShell cmdlets [Get-CsPhoneNumberAssignment](/powershell/module/teams/get-csphonenumberassignment) and [Export-CsAcquiredPhoneNumber](/powershell/module/teams/export-csacquiredphonenumber).

### Use Teams admin center

1. Go to **Voice** > **Phone numbers**.

2. Under the **Numbers** tab, select **Add**.

Adding phone numbers to your tenant and to Microsoft's telephone number management inventory is accomplished by creating an order request. By selecting **Add**, you're originating an order request that creates an order ID and launch the process of uploading your Direct Routing numbers. Follow the remaining steps to complete your order.

3. Give your order a **Name** and **Description**.

4. From the options, choose **From Direct Routing**.

5. Select your preferred method of uploading the numbers by selecting from the drop-down, one of the following options:

#### Add one to many phone numbers

If you select **Add one to many phone numbers**, type or paste the phone numbers you wish to upload in the text field.

If you're adding more than one phone number to this list, separate each number with a comma or a new line.

#### Add phone number range

If you select **Add phone number range**, type or paste the starting and ending numbers of your range in the respective text fields.

#### Upload CSV

If you select **Upload CSV**, select the **Upload CSV** icon and select your CSV file.

The CSV file format requirements are to have a single column, with the first row populated as **TelephoneNumber** and each subsequent row including one phone number.

Download a template by selecting **Download a sample CSV file with Direct Routing Numbers**.

6. Select **Next** and proceed to review the validated numbers to be reserved by Microsoft's telephone number management inventory.

7. Select **Confirm**, then select **Finish**

### PowerShell method

To upload Direct Routing telephone numbers to Microsoft's telephone number management inventory, use the [New-CsOnlineDirectRoutingTelephoneNumberUploadOrder](/powershell/module/teams/new-csonlinedirectroutingtelephonenumberuploadorder) cmdlet.

Uploading the numbers is an asynchronous operation.

### Order history

View the status of the numbers you uploaded in TAC by navigating in TAC to **Voice** > **Phone numbers** and selecting the **Order history** tab.

View the order status of numbers you uploaded with PowerShell by using the [Get-CsOnlineTelephoneNumberOrder](/powershell/module/teams/get-csonlinetelephonenumberorder) PowerShell cmdlet with **OrderType** set to `DirectRoutingNumberCreation`, as shown in the following example:

```PowerShell
 Get-CsOnlineTelephoneNumberOrder -OrderType DirectRoutingNumberCreation -OrderId <orderId>
```

## Considerations

Electing to administer number assignments online is optional. If you prefer, you can still manage number assignment with on-premises administrative tools. The option to use online tools to assign a number to a user automatically uploads the number to Microsoft's telephone number management inventory (if it's not already there) and automatically promotes Teams to control the service configuration of the number.

Once a phone number is migrated to online, you can't manage that phone number using on-premises tools any longer. If you need to manage the number on-premises, you can remove the telephone number from online, and add it back to your on-premises Active Directory.

After assigning the number online, the on-premises Active Directory configuration offered in every following Directory Sync is rejected. Once your numbers are migrated to online, stop Active Directory Sync for those numbers.

## See also

- [Move users to the cloud](decommission-move-on-prem-users.md)

- [Decommission your on-premises Skype for Business environment](decommission-on-prem-overview.md)

- [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md)

- [Move hybrid application endpoints from on-premises to online](decommission-move-on-prem-endpoints.md)

- [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md)