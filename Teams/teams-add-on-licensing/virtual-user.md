---
title: Microsoft Teams Phone Resource Account licenses
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.reviewer: roykuntz
ms.date: 04/03/2025
ms.topic: reference
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - tier1
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom: 
  - Licensing
  - LIL_Placement
  - admindeeplinkMAC
description: Learn how to assign Microsoft Teams Phone Resource Account licenses to resource accounts for auto attendants and call queues in your organization.
---

# Microsoft Teams Phone Resource Account licenses

> [!NOTE]
> There is no longer any cost associated with acquiring Teams Phone Resource Account licenses.

In Microsoft Teams, auto attendants and call queues that directly answer calls require an associated resource account. Each resource account must be assigned a **Microsoft Teams Phone Resource Account** license to ensure they're correctly identified by the system and properly function, *regardless of whether the resource account will be assigned a telephone number*.

A Microsoft calling plan isn't required unless you want to be able to dial out using that resource account. For more information, see [Plan for Teams auto attendant and call queues](../plan-auto-attendant-call-queue.md#prerequisites).

The **Teams Phone Resource Account** license should never be assigned to users that aren't resource accounts.

> [!NOTE]
> All resource accounts must be assigned a **Teams Phone Resource Account** license, regardless of whether they'll be assigned a phone number or not.
>
> If you're currently using resource accounts that aren't assigned any license, you should revisit them to ensure they're assigned a **Teams Phone Resource Account** license.
>
> Don't assign a **Teams Phone Standard** license to a resource account. If you currently have resource accounts configured with **Teams Phone Standard** licenses, you must [switch to a **Teams Phone Resource Account** license as described below](#change-an-existing-resource-account-to-use-a-microsoft-teams-phone-resource-account-license).

## How to obtain Microsoft Teams Phone Resource Account licenses

You obtain Teams Phone Resource Account licenses from the same purchasing channel you purchased the subscription containing Teams Phone. For example, if you purchased Resource Account licenses through an Enterprise Agreement (EA), you need to order through EA.

For Web Direct customers:

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).
1. Go to **Marketplace** > **All products**.
1. Search for *Resource* and select **Microsoft Teams Phone Resource Account**.
1. Scroll to find the **Microsoft Teams Phone Resource Account** license.
1. Select the **Details** button.
1. Choose the number of licenses you wish to purchase and your billing frequency.
1. Select the **Buy** button.
1. Fill in the purchasing details.
1. Select the **Place order** button.

   > [!NOTE]
   > You must still **Buy** the license even though it has a cost of zero.

## Change an existing resource account to use a Microsoft Teams Phone Resource Account license

If you have existing resource accounts using a **Teams Phone Standard** license, you must switch to using to a **Teams Phone Resource Account** license:

1. Purchase the new **Teams Phone Resource Account** license.
2. Follow the linked steps in the Microsoft 365 admin center to [Move users to a different subscription](/microsoft-365/admin/manage/assign-licenses-to-users#move-users-to-a-different-subscription).

> [!WARNING]
> Always remove a **Teams Phone Standard** license and assign the **Teams Phone Resource Account** license in the same license activity. If you remove the old license, save the account changes, add the new license, and save the account settings again, the resource account may no longer function as expected, like your organization's auto attendants and call queues not working anymore.
>
> If this happens, we recommend you create a new resource account using the **Teams Phone Resource Account** license and remove the broken resource account.

## Related articles

- [Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521)
- [Manage resource accounts in Microsoft Teams](../manage-resource-accounts.md)
