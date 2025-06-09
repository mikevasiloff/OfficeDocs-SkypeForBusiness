---
title:  Set up calendar syncing between Google Workspace and Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.topic: article
ms.date: 03/03/2025
ms.service: msteams
audience: admin
ms.collection: 
ms.reviewer: 
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn how to enable bidirectional calendar syncing between Google Workspace and Microsoft Teams.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---

# Set up calendar syncing between Google Workspace and Microsoft Teams for your business

> [!NOTE]
> If your primary email service provider is Microsoft or another service provider other than Google Workspace, you can connect your business domain and email to Teams to manage Teams meetings. Follow the process in [Integrating your business email with Microsoft Teams](/MicrosoftTeams/integrating-business-email?branch=main).

If your business relies on Google Workspace for email and calendaring, you can enable bidirectional syncing with Microsoft Teams. Enabling sync reduces missed meetings and simplifies meeting management by ensuring events and meeting responses created in either platform are seamlessly reflected in both.

> [!NOTE]
> Currently, this set up is only available to small and medium business administrators with a Teams Essentials license and using Google Workspace with a custom domain for email and calendaring.

## Prerequisites

- Be assigned [Microsoft Global Admin role](/microsoft-365/admin/add-users/about-admin-roles) with a Teams Essentials license.
- Be sure all of your users added in the Microsoft directory for whom you want to enable calendar sync for have Teams licenses assigned.
- Have the login credentials for your Google Workspace admin account ([admin.google.com](https://accounts.google.com)).
- Have the login credentials for your custom business domain host website (for example, GoDaddy).

## Choose the appropriate Setup Wizard

1. Sign into [Teams](https://teams.microsoft.com) using your Global Admin account.
1. Go to the [Admin app in Teams](https://teams.microsoft.com/l/app/b47c7387-2807-440c-9fc2-7c8f46147a20?source=share-app-dialog).
1. If your custom business domain isn't already connected with Microsoft 365, select the **Use your existing email and custom domain with Teams** option on the Admin app home page and proceed to "[Use your existing email and custom domain with Teams](#use-your-existing-email-and-custom-domain-with-teams)."
1. If your domain is already connected, select the **Set up calendar synchronization** option on the Admin app home page and proceed to "[Set up calendar synchronization](#set-up-calendar-synchronization)."

## Use your existing email and custom domain with Teams

1. Choose **Google Workspace** on the email selection screen.
1. Review the overview page and select **Continue**.  
1. Enter your business domain and select **Verify**.

   Teams attempts to detect your domain host provider and prompts you to sign into your account. This authorization is solely for verifying domain ownership and doesn't involve any Domain Name System (DNS) changes.

   There are two methods to verify ownership:

    **Method 1: If your domain is hosted at a common registrar, such as GoDaddy, WordPress, or 1&1 IONOS, you have the option to sign in to that registrar and give Microsoft permission to set up your domain for you.**

    - Select **Verify**.
    - Sign in to your registrar if prompted, and then select **Authorize Microsoft to conduct verification**.
    - Return to Microsoft Teams and the custom domain setup task.

    **Method 2: To manually verify ownership and configure DNS records, follow the instructions in Add DNS records to connect your domain.**

1. Sign out of Teams and sign back in with your updated email.

    Your work remains intact and your Microsoft 365 password stays the same. If you encounter issues, allow time for the process to complete and try again.

1. After you sign back into Teams using your business email, return to the Admin app in Teams, and to the custom domain setup task. Now you can update email addresses for other users.
1. Next, move to the calendar synchronization process. Follow the steps outlined in "[Set up calendar synchronization](#set-up-calendar-synchronization)."

## Set up calendar synchronization

1. Review the Calendar sync **Overview** page and select **Get Started**.
1. Before moving forward in the Setup Wizard in Microsoft Teams, you must install an application in Google Marketplace. This application authorizes Microsoft to access your Google user directory and manage their calendars. To do this installation, select the **Go to Google Workspace Marketplace** button to go to the Google Workspace Marketplace, choose **Install**, and follow the steps to authorize access. These permissions are used solely for calendar synchronization.
1. After the installation, return to the Setup Wizard in Teams. Select the **I have installed the Microsoft 365 Mail Migration and Calendar Sync app** checkbox in Google Workspace and select **Next**.
1. When prompted, sign in to your Google Workspace administrator account. Select the **Sign in to Google Workspace** button, enter your credentials in the pop-up dialog box, and follow the instructions to sign in and provide consent.

    Once you're successfully signed in, you may get a loading screen as the system imports the Google user-account details and performs matching with the corresponding Microsoft user accounts.  

1. Next, you see two tables. The first table shows you all the Google user accounts that could be automatched with existing Microsoft user accounts based on user’s first name, family name, and email address. The second table contains a list of Google user accounts that couldn't be automatched. For unmatched users, select the existing Microsoft user account you would like to sync the Google account with from the provided drop-down menu.
1. Once you're satisfied with all user account matching, be sure you selected the checkboxes for the users for whom you want you to enable bi-directional calendar synchronization, and select **Next**.
1. Review all Google user accounts matched with their corresponding Microsoft user accounts. Carefully check each match.
   > [!CAUTION]
   > An incorrect pairing might result in users gaining access to each other's calendar events. Also, mismatches can lead to data privacy issues and unintended calendar access.
1. Once the matches are thoroughly reviewed and confirmed, select **Start Sync** to start calendar synchronization. The calendar-synchronization process might take up to 30 minutes to begin.
1. After reviewing the information on the final page, select **Finish & View Users page**. From the **Users** page, you can monitor and manage the sync status for each user.

## Maintaining calendar synchronization

- To rematch users between Google and Microsoft, disable sync for the current Microsoft users using the **More Actions** menu on the **Users** page in the Admin app.
- When new users are added to Google Workspace or Microsoft 365, you must set up their syncing from the Admin app home page by using the Setup Calendar Synchronization Wizard.
- Be sure newly added users have a Teams license assigned to them.  
- To turn off calendar syncing for a specific user, go into the overflow menu in the **Users** view of the Admin app for that user and select **Turn off Google sync**.

## Frequently asked questions

**How do I schedule Teams meetings from my Google Calendar?**

- You can create Teams meetings directly from the Google Calendar by using the [Teams Meeting add-on in Google Marketplace](https://workspace.google.com/marketplace/app/microsoft_teams_meeting/961264221134).

**What does the "User edits detected" Google Calendar sync status mean?**

- This means critical user-identifiable information, such as a first name, was modified in either the Microsoft or Google Workspace Directory, which results in termination of the calendar sync.
- You can resume the calendar sync for this user by either selecting the **Manage Google Calendar sync** link on the **Users** page or by using the Set Up Calendar Synchronization Wizard on the Admin app home page.

**Can I sync my Google Calendar for personal use with Teams?**

- No, it’s currently not possible to sync your Gmail or Google Calendar for personal use with Teams. However, you can import your Google Calendar into Microsoft Outlook.
- You can also use the [Teams Meeting add-on in Google Marketplace](https://workspace.google.com/marketplace/app/microsoft_teams_meeting/961264221134) to schedule Teams meetings directly from your Google Calendar for personal use.

**I previously set up calendar forwarding using this wizard. Can I switch to the sync experience?**

- If calendar forwarding using this wizard was set up in the past, you can't set up bidirectional syncing at this time. We're working to improve this experience. For updates, check your Microsoft Admin Center Message Center posts or this article.

**How can I share feedback about this experience?**

- You can provide feedback within the Admin app in Teams by using the **Give Feedback** button. You can also provide feedback in our [online portal](https://aka.ms/CalendarSyncFeedback).

**How can I get additional support for this setup process?**

- For support for small to medium businesses, see [Help and learning for small business](https://support.microsoft.com/smallbusiness). You can also get support by using the support page in the [Admin app in Teams](https://teams.microsoft.com/l/app/b47c7387-2807-440c-9fc2-7c8f46147a20?source=share-app-dialog).
- For more help with connecting your domain, see [Add a custom domain name](https://support.microsoft.com/office/add-a-custom-domain-name-071780ac-46bb-4758-b30d-39ad0aeccf42).
