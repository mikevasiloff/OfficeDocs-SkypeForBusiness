---
title: Teams Management Pro portal health reports
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.date: 2/28/2025
ms.reviewer: obahidika
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
description: This article helps you in monitoring the health of your devices in the Microsoft Teams Management Pro portal. 
---

# Health reports in the Teams Management Pro portal

There are reports for health and usage that are available in the **Reporting** node in the Teams Rooms Pro Management portal. The **Reporting** node contains data for the health and usage of your Microsoft Teams Rooms in the Pro Management portal. The **Overview** tab surfaces tenant-wide health trends of your rooms. The **Health** tab displays a list of rooms with their corresponding health data. Room usage based on calendar information and call quality data is visible under the **Usage** tab.

>[!Note]
> This feature is available with a Teams Rooms Pro or Teams Shared Device license.

## Export tickets

The ticket export feature lets you export all active and closed ticket history information within a select date range. Exporting tickets lets you easily access and analyze your ticket history data for better decision making.  

Under the **Overview** report, the **Export tickets** button provides ticket history details that include the following fields: creation date, device name, incident type, ticket state, ticket, last update, history, last resolved date, message/notes conversations, closure summary, closed by, and last closed date. 

The data is generated in a JSON file that you can download and import into Power BI. The download starts after you select **Export tickets**. If you leave the portal before the download starts, you have to request the file again. 

|Column |Description   |
|----------|-----------|
|Created |Date and time the ticket was created |
|Device |Device ID of the room mapped in room name (display name) and host name  |
|Incident Type  |Spread in incident type ID, incident type display name, which is a sub category in UI, the incident type category (for example, account, config) and the incident type severity (for example, critical, important)  |
|State |The state/status of the ticket, which can be new, investigating, resolved, or closed and watching |
|TicketID |The ticket ID in "7B7365-EPDOLF" format |
|LatsUpdate |Any updates made on the ticket with specific date and time  |
|History |Detailed history of the ticket status overtime |
|SnowIncident |SNOW incident number in "INC11684776" format |
|LastResolved |Date and time when the ticket was last resolved  |
|Closure Summary/Reason |The reason for ticket resolution (for example, self resolved) |
|Closure Summary/Closed By |Who is responsible for closing the ticket (for example, Managed Room Services |
|LastClosed |The date/time the ticket was closed |

## Navigating reports

<!--![A screenshot of active tickets bar graph](../media/health-and-usage-002new.png)-->

The overview section provides graphical representations of important aspects of meeting room management. The charts change depending on the time span selected or group selected. To change the time span, select the drop-down menu.

<!--!![A screenshot of a menu to choose a day](../media/health-and-usage-004.png)-->

To change the group, select the group selection drop-down menu in the banner.

<!--!![A screenshot of the banner menu auto-generated](../media/health-and-usage-005.png)-->
### Tickets by category

The donut displays the total tickets raised for the selected time span and group (default is seven days, all groups). Tickets are represented in their major categories: Audio, Display, Peripherals, Connectivity, Versioning, and Recorded issues.

<!--!![A screenshot of pie chart tickets by category](../media/health-and-usage-006.png)-->

A flyout for the detailed view for tickets of that category appears when selected.

<!--!![A screenshot of tickets and versioning side by side](../media/health-and-usage-007.png)-->

In the flyout, it's possible to filter the list of tickets by the subcategory by selecting the respective part of the donut. 

<!--!![A screenshot tickets by subcategory automatically generated](../media/health-and-usage-008.png)-->

To navigate back, either select on the donut or select on the breadcrumb at the top left.

To navigate to a specific ticket in this list view, select on the link under the **Support ticket column**.

<!--### Ticket history

The ticket history graph shows a comparison of incidents assigned to you or Microsoft over the specified time period.

> [!NOTE]
> If a ticket changes owner in a day, whoever owns the assignment for the majority of that day will have the ticket counted towards them. For example, if you assign the ticket to Microsoft early in the day, the ticket counts towards **Assigned to Microsoft** for the day.

<!--![A screen shot of Tickets history by different periods](../media/health-and-usage-009.png)-->

### Health history

This graph shows the average health (definition in Health section) for all the rooms in the tenant and the average health for all Microsoft Teams Rooms Pro customers on a day-to-day basis. You can view the average health for up to 90 days.

<!--!![A screenshot of rooms health and average health](../media/health-and-usage-010.png)-->

### Most reliable/least reliable rooms

Two tables show the most reliable and least reliable rooms based on health. For the full list view, select Health, then sort the list by the Health column.

### Rooms history

Provides a historical view of rooms enrolled in the service and provides a comparative view of rooms that were healthy or unmonitored in the same time period.

## Health

The  reporting node contains data for the health and usage of your Microsoft Teams Rooms in the Pro Management portal. The Overview tab surfaces tenant-wide health trends of your rooms. The Health tab displays a list of rooms with their corresponding health data.

To navigate to the Health report for all rooms, select Reports, then select  **Health**.

<!--!![A screenshot of a Reports health percentage](../media/health-and-usage-001.png)-->

A room can either be healthy or unhealthy for a given day. It's considered unhealthy if a ticket or many tickets with a severity of critical or important impacted the room for more than 20 total minutes during nonmaintenance hours (5AM -9PM machine local time). For example, if a ticket is opened at 5:00 AM but closed at 5:15 AM, the room is still considered healthy. But, if a second ticket occurred from 09:00AM to 9:10AM, the room would be considered unhealthy for the day. Similarly, if a ticket occurs from 5:00 AM to 5:21 AM, it's considered unhealthy for the day.

> [!NOTE]
> Health for the day is aggregated once a day at 12:00 AM UTC time. For customers near the international date line, health aggregation may occur near the middle of the workday.

> [!NOTE]
> Rooms that are onboarding are hidden for the list of rooms in the Health tab and don't count towards the average health of the tenant.

Clicking on a room listed in this view displays more details.

The bar graph displays the number of tickets on each day. Tickets opened on that respective day appear in blue. Tickets opened prior to the respective day appear in orange. Clicking on a day on the graph filters the pie chart and table to the relevant tickets. To reverse the filter, navigate with the breadcrumbs or select on the graph.

Categorization of tickets is represented in the donut chart. Interacting with this filters the timeline graph and table. To reverse the filter, navigate with the breadcrumbs or select on the graph.

<!--!![A screenshot of a Reports health bar graph](../media/health-and-usage-014.png)-->

The meeting impact view shows scheduled meetings during which a ticket with a severity of "Important" or "Critical" was open. The purpose of this view is to provide an approximation of meetings where participants could have experienced issues.

<!--![A screenshot of a Reports meeting impact](../media/health-and-usage-015.png)-->

The Settings tab displays the metadata of the room such as the hardware information, device settings, BIOS information, app settings, and location.

## Related articles

- [Usage report in Teams Rooms Management portal](/microsoftteams/rooms/usage-reports)
- [Device Health Status](/microsoftteams/alerts/device-health-status)