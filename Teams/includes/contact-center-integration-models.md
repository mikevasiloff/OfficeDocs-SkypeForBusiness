## Integration models for solution providers

<a name="steps"></a>

As a contact center solution provider, there are three integration models to choose from to integrate your connected contact center solution into Teams:

- If you want to use an SDK that enables solution providers to imbed native Teams experiences in their App, see the [Unify integration model](?tabs=unify#steps).

- If you want to use Azure bots and the Microsoft Graph Communication APIs to enable solution providers to create Teams apps, see the [Extend integration model](?tabs=extend#steps).

- If you want to use certified SBCs and Direct Routing to connect a contact center solution to Teams, see the [Connect integration model](?tabs=connect#steps).



### [**Unify integration model**](#tab/unify)

The Unify integration model enables solution providers to develop native Azure Communication Service-based CCaaS applications using Teams calling infrastructure.

This approach creates intelligent CCaaS solutions that enhance interactions between customers and contact center agents.

The Unify integration model extends Teams Phone system capabilities into CCaaS with the following resources:

- Azure Communication Services -- call automation
- Azure Communication Services -- calling software development kit
- OpenAI
- Other Microsoft tools

### [**Extend integration model**](#tab/extend)

The Extend integration model integrates with the Teams client using the [Teams client platform](/microsoftteams/platform/overview), [Teams Graph APIs](/graph/api/resources/teams-api-overview) and [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview). The Extend integration model also uses the Teams Phone system for all contact center calls and call control experiences, and the contact center solution provider acts as a telephony carrier alongside Microsoft 365.

Agents can use Teams for internal and external communication. They also benefit from dynamic, contextual notes correlating data from multiple systems before starting an engagement, avoiding costly context switching.

Organizations can design workflows and advanced routing configurations down to the individual and measure the quality of their system and interactions.

**Feature highlights:**

While these features aren't a comprehensive list of feature capabilities for this model of integration, the focus areas include:

- Teams Graph APIs and Cloud Communication APIs for integration with Teams

- Teams-based app for agent experiences

- Teams as the primary calling endpoint for the agents

- Teams client calling for all the call controls

- Agent experience app for both Teams web and mobile client

- Analytics, workflow management, role-based experiences for agents in the CCaaS app in Teams

- Chat and collaboration experiences integrated with Teams clients

- Preserve performance and quality of Teams client experiences in all apps

### [**Connect integration model**](#tab/connect)

The Connect integration model uses Microsoft certified SBCs and Direct Routing to connect contact center solutions to Teams Phone system infrastructure, enabling enhanced routing, configuration, and system insights.

Agents can set up automated virtual assistants and skill-based routing queues to gather information and connect customers with subject matter experts.

**Feature highlights:**

While these features aren't a comprehensive list of feature capabilities for this model of integration, the focus areas include:

- Office 365 authN for agents to connect to their Microsoft tenant from their integrated CCaaS client

- Availability reports of agents with Teams

- Transfers and group call support with Teams

- Teams Graph APIs and Cloud Communication APIs for integration with Teams

- Multitenant SIP trunking to support several customers on solution provider's SBC.

- Solution providers to use [<span class="underline">Microsoft certified session border controller (SBC)</span>](../direct-routing-border-controllers.md)

> [!NOTE]
> The agent used contact solution doesn't need a phone system license. The Teams user does need a phone system license and a phone number to agent's call transfer.
