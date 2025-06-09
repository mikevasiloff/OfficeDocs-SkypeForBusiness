---
title: Teams Management Pro portal usage reports
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
description: This article helps you in monitoring the usage of your devices in the Microsoft Teams Management Pro portal. 
---

# Usage reports in the Teams Management Pro portal

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

## Usage

The reporting node contains data for the health and usage of your Microsoft Teams Rooms in the Pro Management portal. The Usage tab contains Room usage based on calendar information and call quality data.

To view the Usage report for all rooms, select **Reports->Usage**.

<!--!![A screenshot of all rooms' usage by health](../media/health-and-usage-011.png)-->

The headlines provide a few insights:

- Total rooms in your tenant
- How many don't have any booked meetings, either offline or online
- Percentage of utilization of rooms across the tenant
- Total number of booked meetings through exchange
- Percentage of booked meetings that included a Skype or Teams link
- Total calls with room participation
- Aggregate call performance score from all calls classified with "Good" quality to all calls. 

Below the headline **Metrics** is a table of rooms with corresponding metrics. Select a room to view more usage details. The metrics in the table are described in the following table.

|Column|Description|
|---|---|
|Utilization|Percentage of time the room was booked during business hours (Max of 8hours/ per day) in the selected period.  Utilization= (total hours)/ (number of selected days set in the report * 8).   Ex: Time period set to seven days in the report. The room was booked for five days during that period and the total hours= (8 * *5) =* 40 hours*. **In this case, utilization = (8 **** **5)/ (7 * 8) = 40/56= 71%**      |
|Booked online|Of the booked meetings, the percentage of which were enabled with Teams. Ex. 10 meetings were booked. Of that, 8 had a Teams link. Booked Online = 80%|
|Scheduled meetings|Absolute number of meetings scheduled in the room.|
|Total calls|Absolute number of calls with the room as a participant.|
|Call performance|Percentage of calls with a "Good" rating. Each call is evaluated and receives a Good, Poor, Unknown rating. This metric is calculated from Good calls/Total calls.|
|Video Utilization|Percentage of time the video was on during the meeting. |
|Capacity|Maximum number of seats that the room can accommodate. |
|Average people count.|Average number of individuals present in the room during the meeting.  This data is coming from OEM camera witch support people count such as:  Poly Studio E70 Video, Jabra PanaCast 50, Polycom Studio Video, AVer VC520 Pro2, AVer CAM550, Yealink UVC84 Camera, Poly Studio P15 Video, Poly Studio R30 Video, Yealink UVC86 Camera, Jabra PanaCast 50 Composite, Bose Videobar VB1, Poly Studio V52 Video, AVer VB342 Pro|

Usage is calculated at the end of each day at midnight (00:00) local time of the meeting room device. Utilization is calculated based on the total booked meeting time for that day divided by 8 hours.

> [!NOTE]
> The metrics for Panels that aren't sharing an account with Microsoft Teams Rooms aren't showing yet in the usage report.  

## Usage details of a room

Clicking on a room in the list view prompts a flyout with more in-depth information. Under the Utilization tab of the flyout is a graph showing hours of usage of the last five business days. For each day there are two bars: blue represents booked meeting time; purple represents scheduled time of Teams/Skype enabled meetings. At the bottom, the average meeting bookings and duration for the past five business days are calculated.

<!--![A screenshot of utilization by hours per day](../media/health-and-usage-012.png)-->

The **Calls** table shows meetings in which the room participated in a Teams call. The Room Audio Quality is evaluated for only the room, not all participants. To view call quality for all participants of a specific call, select a call by selecting the Start Time.

<!--!![A screenshot of room audio quality](../media/health-and-usage-016.png)-->

To view stream details for the room, select the Session Start Time.

## Insight report

The Insight report is located under the Report section of the pro-management portal. It provides a detailed overview of all the activities completed by our services during a specific time range, including the types of actions performed, such as detection, remediation, and updates. This report highlights the value we provide through actions to resolve rooms issues and how much time and money we help you save by doing that. 

To view the Insight report for all rooms, select **Report** > **Insight Report (Preview)**.

## Actions

 The Actions section of the report shows a timeline view and aggregate count of all actions completed each day by the service. Action types include detection, remediation, and updates. Details on the actions can be viewed by selecting **See details**. Once you have selected **See details**, a new panel appears with two sections; Tickets and Updates. The Tickets section shows a list of tickets with corresponding hours saved. Select the Tickets section to show an expanded view of each action taken on the respective ticket and the hours saved. The Updates section shows a list of each update applied and the corresponding tally of devices that successfully completed the update.  
 
## Detection, investigation, and remediation

The Detection, investigation, and remediation section displays two counts respective of the specified time range: Meeting issues prevented and Incidents remediated.

## Updates
 
The Updates section provides a count of total updates either scheduled, in progress, or completed across the devices enrolled in the service.

## Estimated savings
 
The estimated hours saved from the actions completed are converted to a monetary amount based on a default rate of $50 USD/hour for IT professionals. To customize the rate, select _See details_ in this section.
The Detail pane allows you to input a custom hourly rate and corresponding currency to get a better monetary estimate.  

## User experience

This section provides the average call rating by end-users on a scale of 1 to 5 (5 being the best).

## Related articles

- [Health report in Teams Rooms Management portal](/microsoftteams/rooms/health-reports)
- [Device Health Status](/microsoftteams/alerts/device-health-status)