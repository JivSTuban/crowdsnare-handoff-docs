# 04 - Client Onboarding And Provisioning

## Target Outcome

Onboarding should take a new dealership from "subaccount exists" to "selected AI products are live, tested, monitored, and documented."

## Required Inputs

For each client, collect:

- Dealership name and approved display name.
- GHL subaccount/location.
- Website URL.
- Primary sales phone.
- Timezone and business hours.
- Sales/service/parts routing contacts.
- Calendar IDs and booking rules.
- Product list to deploy.
- Inventory source, if inventory-aware products are included.
- Brand/persona requirements for the agent.
- Escalation/manual takeover rules.

Do not store credentials in this documentation folder.

## Provisioning Flow

1. Confirm the GHL subaccount exists.
2. Create or confirm the GHL private integration token with required scopes.
3. Load the correct GHL snapshot for the product suite.
4. Verify custom fields, custom values, pipelines, tags, calendars, and workflows.
5. Clone or create the matching n8n parent workflows and tool subworkflows.
6. Replace copied webhook URLs so the new account points to the new client workflows.
7. Add or update Supabase client configuration.
8. Configure inventory tables and match functions if needed.
9. Verify all tool workflow IDs point to the correct client-specific workflows.
10. Run safe synthetic QA for every enabled product.
11. Confirm GHL sends through the intended channel and number.
12. Disable duplicates after traffic is confirmed on the intended runtime.
13. Log the final state in the operating KB and Signal Desk.

## Automation Strategy

The long-term goal is to reduce onboarding to a deterministic script-driven workflow:

- Discover GHL subaccount metadata.
- Generate or validate client slug.
- Verify required GHL permissions.
- Apply snapshot.
- Read generated GHL asset IDs.
- Insert or update a Supabase `client_config` row.
- Clone n8n parent/tool workflows from templates.
- Rewrite webhook paths, credential refs, tool IDs, and product config.
- Run readiness audits.
- Produce a client deployment report.

## Current Automation State

Existing docs and scripts already cover parts of this:

- New dealer deployment guide.
- Client configuration architecture.
- Snapshot/master-copy audit.
- Production self-hosted migration checklist.
- Product QA reports and migration audits.
- Manual takeover audit and patching scripts.
- Calendar booking cleanup audit scripts.

The gap is a single polished "one command" provisioning tool that ties all of those pieces together.

## Golden Source Rules

Do not blindly use a snapshot just because it has the right name. A source account/snapshot is only safe when it passes:

- Pipeline/stage completeness.
- Deterministic hard-stop handling.
- Post-agent stop handling.
- Calendar cleanup before booking.
- GHL bump/reminder audit.
- Product-level live or safe synthetic QA.
- Duplicate workflow shutdown plan.

## QA Gates

Before a client is considered live:

- Webhook custom values point to the correct runtime.
- AI response fields are populated by n8n.
- GHL sends the response through the expected channel.
- Stop, DND, wrong-person, already-purchased, and booked states work.
- Manual takeover prevents AI from replying while staff is handling the thread.
- Calendar tools clean up prior automations before booking.
- Runtime duplicate risk is resolved or explicitly documented.
