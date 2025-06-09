---
title: Set up Live chat in Teams
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.topic: how-to
ms.service: msteams
audience: admin
ms.reviewer: lavenkat
ms.date: 01/17/2025
description: Learn how to set up and manage Live chat on your website and connect with customers in real time.
ms.localizationpriority: medium
search.appverid: MET150
ms.custom: teams-chat-and-channels
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# Set up and manage live chat

Live chat allows your website's visitors to chat easily with your business through a chat widget on your customer-facing website. Visitors submit queries to your website’s chat, connecting them directly to your support team in Teams.

This article teaches you how to set up and manage the live chat widget for Microsoft Teams.

Live chat is currently available in the US only with worldwide availability in Q2 of 2025. This post will be updated with the country and region availability list as the feature becomes available. 

## Requirements and limitations for live chat

- Live chat is available only to Microsoft 365 Business Basic, Microsoft 365 Business Standard, and Microsoft 365 Business Premium users.
- The Teams admin must be on a business license to set up live chat.
- The handoff support team should all have Business license.
- There's a limit of up to 25 users who can be added to the handoff support team.
- Any user in the tenant can be added to the Teams **Live chat requests** team. They can view visitor conversations but aren't tickets.

## Set up and manage live chat's settings

You must be a Global admin to set up live chat in the Teams **Admin** app.

1. Sign in to the Teams app using your Global admin credentials.
1. If you don’t already have the **Admin** app added to your Teams client, search the Teams **Apps** store for **Admin** and add it to Teams.
1. Open the **Admin** app in Teams.
1. Select **Live chat** in the left-rail **Admin** app menu.
1. Select **Get started** to start the set-up process.
1. Customize the chat widget by adding a business logo and name.
    1. This step also creates a default greeting for the bot to greet your website visitors.
1. Select **Next: Handoff** to continue to the next step.
1. When a customer on the website asks a question, Teams creates a request and automatically assigns it to the next available customer service member. In this step, add users to be assigned customer requests.
    1. Only users with a Microsoft 365 Business license can be added to the handoff team, with a maximum of 25 users.
    1. You and members listed in the hand-off team are added to the **Live chat requests** team, which is created automatically. All incoming requests are posted in the **General** channel in the **Live chat requests** team.
1. Select **Next: Set support hours** to continue to the final step.
1. Set which days and time your team is available to chat with customers.
    1. You can also customize what the bot should say when no one is available to chat with a customer or if customers reach you outside the service hours.
1. When you're finished managing Live chat’s settings, select the **Save changes** button.

## Add the live chat widget to your website

You must consent to adding the live chat bot to your organization.  

1. Sign in to the Teams app using your Global admin credentials.
1. Open the **Admin** app in Teams.
1. Select **Live chat** in the left-rail **Admin** app menu.
1. Select **Create** to start the live chat widget creation.
    1. The live chat widget is created in the background. Teams notifies you once the set-up process is complete.
1. Test the chat widget by sending a message via the chat widget right within the **Admin** app and see how it connects website visitors to someone on your team by selecting **Test** under **Next steps**.
1. To add the chat widget to your website, select the **Add to website** button.
1. Add your website’s full URL as a trusted website.
    1. The chat widget can only be embedded on this website.
1. Once you add the website, the code snippet is generated. Select **Copy code** to copy the JavaScript code snippet.
1. Paste the code snippet into your website’s code and publish your website.

The Live chat widget is now added to your website and ready for customers to use.

## Add an AI chatbot to your live chat experience

For tenants with a Microsoft Copilot Studio license, you can add an AI chatbot to your live chat widget to answer frequently asked customer questions before customers are connected to your support team. Learn more about Copilot Studio at [Microsoft Copilot Studio](https://www.microsoft.com/microsoft-copilot/microsoft-copilot-studio).

1. Go to **Teams Admin App** in Teams.
1. Select **Live chat** in the left rail **Admin** app menu.
1. Select **Set up** on the suggestion **Save time with AI-generated responses** to set up the chatbot. This suggestion is only available to the admin if they have a Microsoft Copilot Studio license. In this step, add users to be assigned customer requests.
1. Add your company's public website and select **Add AI agent**.

The AI chatbot is now added to your live chat widget on your website. The AI chatbot answers your customer's questions based on information available in your website. If no answer is found or if the website visitor wants to talk to a human agent, a Teams customer request is sent to your support team (same experience as live chat).

- When a customer on the website asks a question, Teams creates a request and automatically assigns it to the next available customer service member.

## What your customers and support people experience

Once a customer opens the **Live chat widget** on your website and submits a query, a request is made in the **Live chat requests** team. The admin and users in the Live chat team can view all tickets in the **General** channel under the **Requests** tab.

On your website, the customer initially talks to the **Live chat bot** until they're connected to a support agent in your business.

Live chat finds an available support person and connects the customer to the support person in your business. Live chat automatically assigns the ticket to someone in your support team and connects them to the customer in Teams **Chat** where the support person can chat with the customer in real time.

## Related articles

- [Set up Microsoft Teams in your small business](deploy-small-business.md).
- [Microsoft Teams for small and medium businesses](https://enablement.microsoft.com/microsoft-teams/smb/).
