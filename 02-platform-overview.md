# 02 - Platform Overview

## What Crowdsnare Is

Crowdsnare is an AI automation system for car dealerships. It connects CRM events, inbound messages, outbound campaigns, inventory data, booking workflows, and AI agents so dealerships can qualify leads, respond quickly, book appointments, and reactivate dormant opportunities.

## Core Stack

| Layer | Role |
| --- | --- |
| GoHighLevel | CRM, subaccounts, contacts, tags, pipelines, calendars, conversations, workflow automations, SMS/email/channel delivery. |
| n8n | AI orchestration, webhook handlers, tool workflows, API calls, data routing, and product logic. |
| OpenAI / LLM providers | Chat, classification, extraction, lead response generation, and some internal automation support. |
| Supabase | Client configuration, inventory tables, embeddings/vector search, comms mirror, and dashboard data. |
| Voice providers | Voice-agent infrastructure for phone and demo flows. |
| Vercel | Hosted dashboards and demo/test pages. |

## Standard Message Loop

Most text-based AI products follow the same loop:

1. A customer message or lead event enters GoHighLevel.
2. A GHL workflow updates memory/context fields and calls an n8n webhook.
3. n8n loads client configuration, product rules, inventory/context, and tool workflow references.
4. The AI agent decides whether to respond, stop, book, transfer, tag, or escalate.
5. n8n writes the output back to GHL fields and/or performs tool actions.
6. GHL sends the customer-facing SMS/email/chat/Facebook response.
7. Follow-up automations continue or stop based on tags, pipeline stages, and AI/tool state.

## Client Isolation Model

Each dealership normally maps to a GHL subaccount/location with its own:

- Private integration token.
- Custom fields and custom values.
- Pipelines and stages.
- Calendars and phone numbers.
- GHL workflows.
- n8n parent workflows and tool subworkflows.
- Supabase client configuration and inventory references.

## Source Of Truth Model

Operationally, the system uses:

- Markdown KB as durable working memory.
- Signal Desk as a shared queue/dashboard for agents across machines.
- Supabase as a mirror/index and hosted dashboard data source.

For GitHub-facing docs, this package summarizes that model without including private local memory files or raw communication logs.
