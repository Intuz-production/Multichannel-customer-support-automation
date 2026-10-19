*Intuz — Your automation partner, one workflow at a time.*

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

[Intuz](https://www.intuz.com) helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [Enterprise AI Development](https://www.intuz.com/ai/) · [AI Consulting Company](https://www.intuz.com/company/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

# Route multichannel support tickets with OpenAI, HubSpot, Jira, and Slack

## Quick overview

Analyze incoming support requests, classify intent and priority with AI, create Jira tickets, assign the correct team, send Slack notifications, and track SLA deadlines. Supports Gmail, WhatsApp, forms, HubSpot CRM, OpenAI, Jira, and Slack integrations.

## How it works

1. Triggers when a new Gmail email arrives, a WhatsApp message is received via a WAHA webhook, or a user submits the n8n contact form.

2. Normalizes each inbound request into a consistent ticket payload and captures any attachments (including downloading WhatsApp media when present).

3. Searches HubSpot CRM for a matching contact by email and/or phone and merges any found customer context into the ticket.

4. Sends the ticket text to OpenAI to classify category, intent, priority, sentiment, and generate a summary and suggested reply.

5. Calculates the SLA due time and maps the ticket category to the appropriate Jira assignee/component configuration.

6. Checks Jira Cloud for an existing issue labeled with the computed dedupe key and either posts a duplicate notice to Slack or creates a new Jira issue.

7. Stamps SLA and AI metadata onto the Jira issue, uploads any attachments, posts a new-ticket notification to Slack, and returns a completion message for form submissions.

8. Every 10 minutes, searches Jira for unresolved tickets past their SLA due time, posts breach alerts to Slack (and optionally a manager DM), escalates Jira priority when configured, and marks tickets as notified.

## Setup

- Connect credentials for Gmail, Slack, OpenAI, Jira Cloud (HTTP Basic/API token), HubSpot (private app token via header auth), and WAHA (X-Api-Key header auth) and select them on the relevant nodes.
- Configure the WAHA inbound webhook URL in your WAHA instance and publish the n8n form (or embed it) for web submissions.
- Update the hardcoded configuration in the workflow (Jira base URL and project key, assignee account IDs, Slack channel names, manager Slack user ID, and Jira custom field IDs for SLA/AI/dedupe/channel).
- Ensure your Jira project has the referenced custom fields and that your priority names match the workflow mapping (`Highest`, `High`, `Medium`, `Low`).
- Verify Slack channels like `#support-triage`, `#support-sla`, and `#support-ops-errors` exist and adjust them in the config if needed.

## Requirements

- Gmail
- HubSpot or any CRM platform
- Jira Cloud
- Slack
- OpenAI
- WAHA or WhatsApp API

## Customization

- Add additional support channels
- Connect a different CRM
- Customize ticket categories
- Modify SLA policies
- Add customer tier-based prioritization
- Integrate with internal knowledge bases
- Add automated customer responses
- Add approval workflows before escalation

## FAQ

**Is this template free to use?**
Yes. It's an open-source n8n workflow published by Intuz — copy the workflow JSON from this repo and import it into your own n8n instance at no cost.

**Do I need a paid n8n plan to run this?**
No. It runs on n8n's free self-hosted Community Edition or on n8n Cloud. You'll need your own credentials for the services this workflow connects to, not a specific n8n pricing tier.

**What determines how a ticket gets routed?**
OpenAI classifies each request (category, intent, priority, sentiment). The workflow maps that classification to Jira assignee/component settings, creates or dedupes the issue, and notifies the configured Slack channels.

## Related n8n templates from Intuz

- [AI-Powered Support Ticket Triage and Routing](https://github.com/Intuz-production/AI-Support-Ticket-Triage-Routing-Automation)
- [Route Gmail Emails to Slack Channels Using AI](https://github.com/Intuz-production/AI-Powered-Gmail-to-Slack-Email-Routing)
- [Route and categorize Gmail emails to Slack with Llama 3 via OpenRouter](https://github.com/Intuz-production/Gmail-email-routing-automation)

[See all of Intuz's free n8n templates](https://www.intuz.com/n8n-workflow-automation-templates/)

## Connect with us

Intuz is a USA-based AI & workflow automation company with 16+ years of experience building custom AI-enabled workflow automations for SMBs and Enterprises, specializing in agentic AI, LLM integrations, and CRM/ERP sync across Healthcare, FinTech, eCommerce, Manufacturing, and Real Estate.

* **Website:** [https://www.intuz.com](https://www.intuz.com)
* **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
* **LinkedIn:** https://www.linkedin.com/company/intuz/
* **Get Started:** https://n8n.partnerlinks.io/intuz

## For Custom Workflow Automation

[Click here - Get Started](https://www.intuz.com/get-started/)
