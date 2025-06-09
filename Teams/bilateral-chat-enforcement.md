---
title: Set up a bilateral chat policy
author: DaniEASmith
ms.author: danismith
manager: jtremper
ms.reviewer: anpraka
ms.date: 05/09/2025
ms.topic: install-set-up-deploy
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
ms.custom:
  - admindeeplinkTEAMS
  - teams-chat-and-channels
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how to set up bilateral chat restrictions for your organization's users.
---

# Set up a bilateral chat policy

Some organizations may need to restrict who users are able to message in Teams. While organizations have always been able to limit users' chats to only other internal users, organizations can now limit users' chat ability to only chat other internal users and users in one other organization.

In this article, you'll learn to set up a bilateral chat policy and restrict external group chats to a maximum of two organizations for users who are assigned the policy.

Once your external access and bilateral policy is set up, users with the policy can only be in external group chats with a maximum of two organizations. Users under the policy are also removed from existing external group chats with more than two organizations.

This policy doesn't apply to meetings, meeting chats, or channels.

## Prerequisites

To set up a bilateral chat policy, you must first have external access set up and turned on. [Learn how to set up external access](/microsoftteams/trusted-organizations-external-meetings-chat?tabs=organization-settings).

## Set up a bilateral chat policy for your organization

To create a new bilateral chat policy, complete the following steps:

1. Sign in to the Teams admin center with your admin credentials.
2. In the left-side menu, expand **External access** and select **Policies**.
3. On the **Policies page**, select **Add**.
4. Turn on the setting for **Communication with Teams and Skype for Business users from trusted organizations in group chats is limited to two orgs max**.

## Assign a bilateral chat policy to users

To assign your newly created bilateral chat policy to users, complete the following steps:

1. On the External access Policies pages, select your newly created policy.
2. Select **Assign users**.
3. Select the users to assign the policy to.
4. Select the **Save** button.

## Create and assign a bilateral chat policy using PowerShell

You can also create and assign a bilateral chat policy using PowerShell. Use the following PowerShell commands to complete the process.
1. **Connect:** Connect-MicrosoftTeams
2. **Create the policy:** New-CsExternalAccessPolicy -Identity EnableBilateral -FederatedBilateralChats $True
3. **Assign the policy to a user / DL:** Grant-CsExternalAccessPolicy -PolicyName EnableBilateral -Identity [email address]
4. **Verify the policy was assigned:** Get-CsUserPolicyAssignment -Identity [email address]

> [!NOTE]
> Don't include the brackets around your chosen email addresses.
