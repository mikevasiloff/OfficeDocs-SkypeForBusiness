---
title: Use organization-wide teams in Microsoft Teams to help everyone collaborate
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.reviewer: shubhanshi.jain
ms.date: 11/12/2024
ms.topic: how-to
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to create and manage an organization-wide team in Teams to provide a way for everyone in a small to medium-sized organization to collaborate.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
  - EngageScoreOct2022
  - ContentEnagagementFY23
appliesto:
  - Microsoft Teams
ms.custom: 
  - seo-marvel-apr2020
  - chat-teams-channels-revamp
  - teams-chat-and-channels
---

# Use organization-wide teams in Microsoft Teams to help everyone collaborate

Global administrators can create organization-wide teams that provide a way for everyone in a small-to-medium-sized organization to be part of a single and collaborative team. Organization-wide teams automatically include every user in the organization and keep the membership up to date as users join and leave the organization.

If your organization is new to Teams and has no more than 5,000 users, an organization-wide team is created automatically. Organization-wide teams are limited to organizations with no more than 10,000 users. You can have up to five organization-wide teams.

## Create an organization-wide team

There are two ways to create an organization-wide team:

- Convert an existing team to an organization-wide team. Go to the team name, and select **More options** > **Edit team**.
- [Create a new team from scratch](https://support.microsoft.com/office/174adf5f-846b-4780-b765-de1a0a737e2b) and choose the **Org-wide** option.

## Types of users in an organization-wide team

When an organization-wide team is created, all Global administrators and Teams administrators are added as team owners, and all active users are added as team members. Team members can't leave an organization-wide team, but team owners can manually add or remove users if needed. When Teams automatically adds or removes someone, a notification is sent to the first created channel of the team, i.e. *General* channel, if not renamed by the team owner.

Unlicensed users are also added to the team. The first time an unlicensed user signs in to Teams, they're assigned a **Microsoft Teams Exploratory** license. To learn more about the Teams Exploratory license, check out [Manage the Microsoft Teams Exploratory license](teams-exploratory.md).

The following types of accounts aren't added to your organization-wide team:

- Accounts that are blocked from sign-in.
- Guests.
- Resource or service accounts (for example, accounts associated with auto attendants and call queues).
- Room or equipment accounts.
- Accounts backed by a shared mailbox.

> [!NOTE]
> Rooms that aren't a part of a room list, equipment, and resource accounts might be added or synced to the organization-wide team. Team owners can easily remove these accounts from the team.

> [!NOTE]
> If a user's account is disabled and then re-enabled, the user may need to be manually added to the organization-wide team again in Teams.

## Options to get the most out of an organization-wide team

To get the most out of your organization-wide team, we recommend that team owners do the following tasks:

### Allow only team owners to post to the first created channel of the team

Reduce channel noise by having only team owners post to the first created channel of the team.

1. Go to the team, select **... More options** > **Manage team**.
1. On the **Settings** tab, select **Permissions**, and then select **Only owners can post messages**.

### Turn off @team and @[team name] mentions

Reduce @mentions to keep them from overloading the entire organization.

1. Go to the team and select **... More options** > **Manage team**. 
1. On the **Channels** tab, locate the first created channel with the home icon.
1. Select **... More options** > **Manage channel**.
1. On the **Settings** tab, select **@mentions** and turn off **Show members the option to @team or @[team name]**.

### Recommend important channels

Mark important channels as "Recommend that people show this channel in their channel lists" to ensure everyone in your organization engages in specific conversations. To learn more, see [Recommend channels for the whole team](https://support.office.com/article/auto-favorite-channels-for-the-whole-team-a948272c-5aa5-429c-863c-4e1e1cd6b0f6).

### Set up channel moderation

Consider setting up channel moderation and giving moderator capabilities to certain team members. When moderation is set up, team owners are given moderator capabilities automatically.

Moderators can:

- Control who can start a new post in a channel.
- Add and remove moderators.
- Control whether team members can reply to existing channel messages.
- Control whether bots and connectors can submit channel messages.

For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

### Remove accounts that might not belong

Even though members can't leave an organization-wide team, as a team owner, you can manage the team roster by removing accounts that don't belong. Make sure you use Teams to remove users from your org-wide team.

If you use another way to remove a user, such as the Microsoft 365 admin center or from a group in Outlook, the user might be added back to the organization-wide team.
