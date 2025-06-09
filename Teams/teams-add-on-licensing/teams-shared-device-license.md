---
title: Microsoft Teams Shared Devices licensing
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms. reviewer: chester, sirigudur
ms.date: 11/11/2024
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - tier1
audience: Admin
appliesto:
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - Licensing
  - admindeeplinkMAC
description: Learn about the Microsoft Teams Shared Devices licensing for common area phones, Teams displays, and Teams panels.
---

# Microsoft Teams Shared Devices licensing

Microsoft Teams supports hybrid work scenarios and enables users to work in flexible spaces. The **Microsoft Teams Shared Devices** license was first introduced to designate certain devices including Teams Phone devices deployed in common areas, Teams displays <sup>1</sup>, Teams panels, and Android mobile phones as shared devices and license the extra software running on them with a shared use model.

The Teams Shared Devices license includes [bring your own device (BYOD) rooms](/microsoftteams/rooms/bring-your-own-device), such as focus or huddle rooms. Associating a Teams Shared Devices license to these room accounts enables valuable usage analytics, reports, and insights in Teams Rooms Pro Management portal. These usage reports can help IT teams optimize BYOD rooms throughout the organization and gain valuable intelligence for planning and budgeting.

The license can still be applied per device as originally introduced. In addition, it can now also be applied to a BYOD room. The Teams Shared Devices license provides usage analytics, reports, and insights for one BYOD room. Customers who already use a Teams Shared Devices licensed device in a BYOD room are granted access to the inventory function and usage analytics and reports for that space through the Teams Rooms Pro Management portal<sup>2</sup> without an extra add-on license.

For information about other Teams add-on licenses, see [Microsoft Teams add-on licenses](/microsoftteams/teams-add-on-licensing/microsoft-teams-add-on-licensing).

<sup>1 End of certification for Teams display devices is September 3, 2025. Microsoft will make commercially reasonable best efforts to maintain compatibility with the most recent version of the Teams apps provided to manufacturers for a period of two (2) years from this date. See the [Microsoft Product and Services lifecycle](/lifecycle/products/) for details.</sup>

<sup>2 For BYOD rooms, the Teams Shared Device license enables inventory, analytics, and reports but doesn't entitle access to the full set of Teams Rooms Pro Management capabilities that come with a Teams Rooms Pro-licensed meeting room.</sup>

The **Microsoft Teams Shared Devices** license includes the following service plans:

- Microsoft Teams
- Microsoft Teams Phone (Previously known as *Phone System*)
- Microsoft Intune (Microsoft Intune Plan 1 and Plan 2)
- Microsoft Entra ID P1
- Exchange Online Plan 2 (Cloud-based voicemail capabilities only.)

> [!NOTE]
> The **Exchange Online (Plan 2)** license is only to support cloud voicemail. Email and calendar aren't supported. If you don't want your Teams enabled shared device to have voicemail, you can deselect the Exchange Online (Plan 2) license or disable the user account's voicemail using the following Teams PowerShell command:
> ```
> `Set-CsOnlineVoicemailUserSettings -Identity`` user1@contoso.com`` -VoicemailEnabled`` ``$false`
> ```

## Teams Shared Devices license availability

The **Teams Shared Devices** license is available to purchase worldwide to commercial, public sector, GCC, GCC High, and DoD tenants.

To purchase the **Teams Shared Devices** license, you can choose your preferred purchasing channel: EA, EAS, EES, CSP, Web Direct, MCA - Customer led, and MCA - Partner led.

## Acquire Teams Shared Devices licenses

Purchase the **Teams Shared Devices** license in the [Microsoft admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Purchase services**.
1. Find the **Purchase from Microsoft** section, and select **View products**.
1. Select the **Collaboration and communication** filter.
1. In the product list, find **Microsoft Teams Shared Devices**, and select **Details**.
1. Enter the number of licenses you need and the billing frequency.
1. Select **Buy**.

## Related articles

The following articles help you set up the various devices that use the **Teams Shared Devices** license.

- [Introducing the Microsoft Teams Shared Device License](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-the-microsoft-teams-shared-device-license/ba-p/3677138)
- [Set up common area phones](/microsoftteams/set-up-common-area-phones)
- [Microsoft Teams panels](/microsoftteams/devices/teams-panels)
- [Microsoft Teams displays](/microsoftteams/devices/teams-displays)
- [Set up an Android mobile phone as a common area phone](../devices/common-area-mobile-phones.md)
- [Set up BYOD rooms](/microsoftteams/rooms/bring-your-own-device)

