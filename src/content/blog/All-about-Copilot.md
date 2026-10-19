---
title: "All about Microsoft Copilot"
description: "What Copilot Chat, Copilot and Copilot Studio include, how they're billed, and where to control PAYG spend."
pubDate: 2026-10-19
tags: ["Copilot", "Copilot Studio", "Microsoft 365", "Licensing"]
draft: false
---

Microsoft now has three Copilot products for business, each licensed and billed differently. Worse, the pay-as-you-go spend controls live in three different admin centers. This post untangles what each one does, what it costs, and where you control the spend.

*Last verified: 19 October 2026.*

## What is Copilot?

Copilot is Microsoft's family of AI assistants.
For Business & Enterprise environments it currently includes:

- Microsoft Copilot Chat
- Microsoft Copilot
- Microsoft Copilot Studio

When using these in your M365 tenant, signed in with your work (Entra) account, they are covered by Microsoft's [Enterprise Data Protection](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection) terms.

There is also GitHub Copilot and Security Copilot, but we'll leave those out for the moment.

### At a glance

| Product | License | Included | Billed extra | Control spend in |
|---|---|---|---|---|
| Copilot Chat (Basic) | With M365 | Web chat, web agents | Work-data agents | M365 admin → Billing |
| Copilot (Premium) | Add-on or Copilot Business | Work-data chat, Office apps, work-data agents | Cowork & Code | n/a |
| Cowork & Code | Needs Premium | Nothing | All usage | M365 admin → Copilot → Cost Management |
| Copilot Studio | Capacity packs and/or PAYG | Pack credits | Usage beyond packs | Power Platform admin + Azure budget |

Next we'll look at what each one does, then the billing.


## Microsoft Copilot Chat (Basic)

Securely interact with Copilot Chat using web data only.
Limited use of organizational content, it needs to be explicitly provided with your prompt. For example uploading a docx file into your chat, or using Copilot Chat in Outlook or Teams with the email or chat you have open.

Users with an eligible Microsoft 365 license but no Copilot license also get standard (non-priority) access to Copilot inside Word, Excel, PowerPoint and OneNote. Microsoft calls this Microsoft 365 Copilot (Basic).

##### License 

Included with eligible Microsoft 365 licenses at no extra cost.

Agents grounded in instructions and public websites are included. To access agents grounded with tenant data, PAYG billing is required.


## Microsoft Copilot (Premium)

Securely interact with Copilot using web data and work data (through Microsoft Graph and Work IQ).

Full integrated experience in Word, Excel, PowerPoint, with priority access.

[Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/) & [Code (Frontier)](https://blogs.microsoft.com/blog/2026/09/25/introducing-the-new-copilot-with-home-code-and-autopilot/) are also available.

##### License 

Premium license required. It's an add-on for most Microsoft 365 plans, and included in Microsoft 365 E7.
For Business SKU tenants with 300 or fewer users, a Copilot Business license is available at a cheaper cost but with the same functionality. 

See the [full list of Copilot features in Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview?tabs=microsoft-365-copilot-premium%2Cmicrosoft-copilot-chat-basic-training#copilot-features-in-microsoft-365-apps).

**Important to note:** although Cowork & Code require the Premium license, they are not covered by it. They are billed on usage (Copilot Credits) via an Azure subscription.


## Microsoft Copilot Studio

This is Microsoft's no/low code option for building agents.

Currently there are 3 things you can build in Studio:

- Agents
    - [Standard](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview#standard-harness) harness agents
    - [GitHub Copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview#github-copilot-harness) harness agents
    - [Copilot chat](https://learn.microsoft.com/en-us/microsoft-copilot-studio/harnesses-overview#copilot-chat-harness) harness agents, to extend Microsoft Copilot Chat

- Workflows
    - [Standard](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview) Agent Flows
    - [GitHub Copilot](https://learn.microsoft.com/en-us/microsoft-copilot-studio/workflows-experience/flows-overview) Agent flows

- [Apps](https://learn.microsoft.com/en-us/microsoft-copilot-studio/apps-experience/apps-overview) (Preview)

Agents built in Copilot Studio live and are managed in Power Platform.

##### License

There are two ways to pay, and they can be used in combination:

- Copilot Studio prepaid capacity packs, each giving your tenant 25 000 Copilot Credits per month (unused credits don't roll over)
- PAYG via an Azure subscription

If you run out of prepaid credits, any further billing will then go to your Azure subscription.

All of the tools in Studio are consumption based, so mileage may vary depending on the models used, tools called etc.
Watch out for the GitHub Copilot harness (which also powers Apps): it starts consuming credits from the moment you start building and testing, not only after you publish.


## PAYG Management

This is where things get tricky.
Many features require PAYG, but how and where do we control the spend?

Firstly, there are two ways to build agents: Agent Builder and Copilot Studio. 
To decide which one you need, see Microsoft's [Agent Builder vs Copilot Studio comparison](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/copilot-studio-experience).

#### Agent Builder

- Web grounded agents 
    - Included for both Basic and Premium users
- Work data agents 
    - Premium users - Included
    - Basic users - PAYG

To allow Basic users to access work data agents, and to monitor what they spend, you need a billing policy.

From the M365 admin center → Billing → Pay-as-you-go, add a billing policy and link it to a Resource Group in your Azure subscription.
There you can set up budgets and alerts to keep an eye on your spending. Note the budget only sends alerts, it doesn't stop usage.
Then connect the policy to the service in M365 admin center → Copilot → Cost Management → classic Billing & usage → Pay-as-you-go services → Microsoft Copilot Chat.

#### Copilot Studio

Agents built here consume Copilot Credits. These either come from prepaid capacity packs or are billed via an Azure subscription.

To enable PAYG, create a billing plan in the Power Platform admin center → Licensing → Billing Plans.

You cannot set a budget or alerts for PAYG from here, which is a bit of an oversight to be honest.
There is an overage notification, but it only applies to your prepaid credits.

You can set a monthly limit per agent (Licensing → Copilot Studio → Manage Agents), with notifications and an optional hard stop. If you are deploying and managing dozens of agents, that isn't a scalable way to manage costs, but it does show you who your high cost agents are.

My recommendation is to set up an Azure budget and notification scoped to the Resource Group linked to the billing plan. Keep in mind Azure budgets only alert, they don't stop usage.

#### Copilot Cowork and Code

This is managed in the M365 admin center → Copilot → Cost Management.
Again, link it to your Azure subscription and set up your spending limits & alerts. Unlike the other two, these limits actually cap spend, and you can set a per-user monthly limit too.


## Summary

In true Microsoft style they have managed to create a convoluted system to manage your Copilot environment.
PAYG sounds like it should make things simpler, but you have to set it up in 3 different places:

1. **Copilot Chat agents (Basic users):** M365 admin center → Billing → Pay-as-you-go, then connect the policy under Copilot → Billing & usage
2. **Copilot Studio:** Power Platform admin center → Licensing → Billing Plans, plus an Azure budget on the linked Resource Group
3. **Cowork & Code:** M365 admin center → Copilot → Cost Management

No doubt this article will be out of date in a month as they continue to shift things around, but I hope it has helped you to understand the Copilot ecosystem a little better.
