---
title: "Setting up Bookable Desks in Microsoft Teams "  
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: eviegrimshaw
ms.date: 01/17/2025  
ms.topic: article
audience: Admin
appliesto: 
  - Microsoft Teams
ms.service: msteams  
ms.subservice: itpro-rooms
ms.localizationpriority: medium
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Rooms
  - Tier1
ms.custom: QuickDraft 
search.appverid: MET150  
f1.keywords:
  - NOCSH  
description: Helps admins set up Bookable Desks for their Microsoft Teams organization.
---

# Setting up Bookable Desks in Microsoft Teams

Unlock the full potential of your desks with Microsoft Teams. Bookable desks in Microsoft Teams are designed to enhance the efficiency of your organization by enabling users to seamlessly reserve desks upon plug-in to peripherals while providing you with the tools to understand and manage those spaces.

## Overview of steps  

To set up and use Bookable Desks in your organization, you must perform these tasks:

- Step 1: Review the prerequisites.

- Step 2: Create resource accounts.

- Step 3: Collect information on peripheral devices on each desk such as a monitor.

- Step 4: Enable additional features for users. 

- Step 5: Verify the user experience. 

- Step 6: Review data in usage reports. 

## Step 1 - Review the prerequisites 

- Confirm that you have access to the Microsoft Teams Pro Management portal.

- Ensure that your users have access to the new version of Microsoft Teams desktop app on Windows or Mac.

- If you're planning to use individual desks, verify that your users have a Teams Premium license. Individual desk booking is a Teams Premium feature.

## Step 2 - Create Desk Pool or Individual Desk Accounts

Desk pool accounts, known as **'workspaces'** in Exchange, are slightly different from room accounts. The capacity of a desk pool represents the number of seats in that pool and is set by the admin. The pool can be reserved by multiple users at the same time until all seats (the capacity) are taken. For example, the capacity on a desk pool is set to 2. User A and User B are both able to reserve it from 8am to 5pm, and the remaining capacity will be 0. This means that a third user won't be able to reserve it between 8am and 5pm.

On the other hand, individual desks, known as **'desk'** in Exchange, represents a specific seat in the office. If a user reserves the individual desk, that specific seat is theirs. 

To create a desk pool or an individual desk account, you need to set up the resource account in Exchange. We recommend following the steps outlined in [Configure desk booking](/microsoft-365/places/configure-desk-booking?branch=main#configure-desk-pools).

After you create the account, allow 24 to 48 hours for the account to appear in Outlook, Teams, and Teams Rooms Pro Management Portal.

## Step 3 - Collect information on peripheral devices

Next, to ensure a seamless user experience, peripherals such as the monitors on the physical desks need to be associated or linked to the desk pool or individual desk account you created earlier. To do this, you need to identify the peripherals based on their unique information such as product ID, vendor ID, and serial number.

You can use a free PowerShell script to fetch the details of a peripheral and ensure they're mapped to the corresponding desk pool or individual desk accounts in the Teams Rooms Pro Management portal. The PowerShell script is located [here ](https://www.microsoft.com/download/details.aspx?id=106063)to download, and for detailed step-by-step instructions, see [Add peripherals to inventory](/microsoftteams/rooms/get-peripheral-information).

## Step 4 - Enable additional features for users

You have the option to [enable the automatic work location update policy](/powershell/module/teams/new-csteamsworklocationdetectionpolicy) for your organization or for a group of users. Automatic work location updates are designed to enhance the end user experience by making it easier to keep their work location up-to-date and connect with others when they are in the office. With the policy enabled, users have the option to enable automatic work location updates. They can do so in Teams desktop client under **Settings** > **Privacy** > **Manage my work location**. After users have opted-in, their work location will automatically update to **In the office** when they connect to a bookable desk, provided their work location was previously set to unknown or remote. If the desk pool or individual desk is parented to a building, their work location can also change to a specific building when they connect to a bookable desk, provided their work location was previously set to unknown, remote, or In the office. The detected location lasts until the end of their working hours. If they plug in after work hours, the location will be set until 11:59pm that day. This feature allows for a seamless transition between remote and in-office work, which enhances collaboration and communication within your team and other users. 

## Step 5 - Test the end user experience

Wait 24 hours after associating to test this experience. After that point, ensure that you're signed into Teams on a Windows or Mac laptop. Upon plugging the laptop into a peripheral you associated to a desk pool or individual desk account and assuming there's availability to book, you should receive an activity feed notification that 'The [space or desk] is reserved and ready for you' along with a booking in your calendar. You can also reserve the desk for a future time slot. To learn more on the end user experience, see [First things to know about bookable desks in Microsoft Teams](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-in-microsoft-teams-5d10c217-1205-48a1-a883-ff4533f4ae71?preview=true).

## Step 6 - Review data in usage reports 

Once the end-user experience is working, you can start to review reports to learn more on how your desk pools or individual desks are being used. Desk usage reports are located in the Teams Rooms Pro Management portal > Reports > Desks usage.   

The top metrics listed are described in the following table: 

|Metrics| Definition|
| -------- | -------- |
|Total associated desks|The total number of device groups associated to all desk pools or individual desks.|
|Total unused desk pools|The total number of desk pools that have 0% utilization.|
|Total unused desks|The total number of individual desks that have 0% utilization.|
|Unplanned reservations|The percentage of reservations across all desk pools and individual desks that weren't planned in advance and were autobooked. |

Below the top metrics, there's a table that provides a granular breakdown of each desk pool and individual desk, accompanied by specific metrics that highlight the usage of each. You can adjust the time filter to view usage over different time periods or the type filter to view metrics for a specific type of desk. 

| Column| Description|
| -------- | -------- |
|Display name|The name of the desk pool or individual desk. |
|Utilization   | The percentage of time users were plugged into associated desks during business hours in the given time period.|
|Associated desks|The number of device groups associated to this desk pool or individual desk, out of the total capacity.|
|Reservations|The number of reservations across bookable desks in the selected time period.|
|Unplanned reservations|The percentage of reservations that weren't planned in advance and were autobooked.|
|Reservation occupancy|The percentage of time users spent plugged into bookable desks during reservations. Lower values indicate more reservations were spent with less time plugged in.|

## Settings

### Turning off automatic discovery and usage data collection in the Teams client 

Bookable desks in Microsoft Teams use peripheral data crowdsourced from the Teams desktop client running on the users' laptops to discover peripherals as well as understand when those desk pools or individual desks they're associated to are used. No personally identifiable data is collected, but should you feel this data collection is inappropriate for your tenant or a group of users in your tenant, you may use the following PowerShell cmdlets to configure the policy appropriately. Please note that for government clouds, this policy is off by default. 

First, ensure that your Microsoft Teams module is on version 6.5.0 or higher. To confirm the version, please run the following:


```powershell
Import-Module MicrosoftTeams
Get-Module -Name MicrosoftTeams
```

If you don't have the Microsoft Teams module installed, please run the following and then re-run the above command to check the version:


```powershell
Install-Module -Name MicrosoftTeams -Force -AllowClobber
Import-Module MicrosoftTeams
```

If your version is lower than 6.5.0, please follow [these instructions](/microsoftteams/teams-powershell-install) to update it. 

Use the following commands to create, set, grant, or remove a configuration in the TeamsBYODAndDesks policy: 


```powershell
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
Get-CSTeamsBYODAndDesksPolicy
Set-CSTeamsBYODAndDesksPolicy -Identity Test -DeviceDataCollection Enabled
Grant-CSTeamsBYODAndDesksPolicy -PolicyName Test -Identity testuser@test.onmicrosoft.com
Grant-CSTeamsBYODAndDesksPolicy -Group 
Grant-CSTeamsBYODAndDesksPolicy -Global -PolicyName Test
Remove-CSTeamsBYODAndDesksPolicy -Identity Test
```

### Configuring cloud data

**Delete device data**

This setting enables admins to delete all device management data for a specific user. 

**Inventory management permission**

The inventory management permission in Teams Rooms Pro Management portal allows others to view and manage the inventory. You can create roles under **Settings** > **Roles** in Teams Room Pro Management portal and grant permissions to access inventory and associate peripherals to desks. 

## Frequently asked questions

**Question: What are Desk Pools?**  

**Answer:** Desk pools are a group of seats in the office that are close to one other and in the same area. When an employee books a desk in the desk pool, they're reserving a seat in the desk pool.

**Question: What is the difference between individual desks** **and desk pools?**

**Answer**: Individual desks are a new type of resource account in Exchange which will allow a user to book a specific seat instead of booking one of the seats in a desk pool. Support for individual desks for Bookable desks in Teams released in April 2025.

**Question:** **Is the bookable desks feature available on Classic (old Teams) and new Teams?**

**Answer**: No, the bookable desk experience is only available on the new Teams client. To download and switch to the latest Teams client see, [New Microsoft Teams](https://adoption.microsoft.com/new-microsoft-teams/).

**Question: Is the bookable desks feature available in VDI?**

**Answer:** Yes, this feature set is supported in the [New VDI solution for Teams](/MicrosoftTeams/vdi-2).  

**Question: Does Bookable** **desks work with Microsoft Places?**

**Answer**: Yes, it does! If a user is automatically reserved in a desk pool or at an individual desk, the booking will also appear as the user's desk booking for the day in Places. If a user books a seat in a desk pool or individual desk in advance through Places, upon plug-in to a bookable desk, the user sees a confirmation message that they're all set for their reservation.

**Question: How can I be sure that it will work with my devices? Do I need** **to buy new hardware?**

**Answer**: That is one of the beauties of Bookable desks! No new hardware is required. We have designed our solution with the goal of working with all models and manufacturers, which is dependent on the device having unique properties. We currently support monitor and devices with both audio and video capabilities. Support for docking stations and webcams are coming soon. 

**Question: Is there another way I can associate my devices other than the PowerShell script?**

**Answer**: Yes, there is! You can also associate the device manually through Pro Management portal. Navigate to **Planning > Inventory > Devices >** select on an unassociated device (one with a 'Needs action' tag) > select on 'Add device to a room or desk' > search for the desired desk pool you'd like to assign the device to. To make it easier to discover devices, they're automatically discovered using your users' Teams app. Once five unique users have plugged into a device on a desk, it will automatically surface in the **Devices** tab for association.

**Question: What do I need to access usage reports?**

**Answer:** These reports are currently in preview and don't require a license to access. 

## Related links

- [First things to know about bookable desks for end users](https://support.microsoft.com/office/first-things-to-know-about-bookable-desks-5d10c217-1205-48a1-a883-ff4533f4ae71)

