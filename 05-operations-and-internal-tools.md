# 05 - Operations And Internal Tools

## Claude Code Style Bug-Fixing Automation

Crowdsnare had internal automation around repeated support and bug-fix loops. The intent was:

- Monitor communication channels for dealer issues.
- Convert issues into internal work items.
- Diagnose likely GHL/n8n/Supabase causes.
- Patch safe issues directly when possible.
- Preserve draft replies for human approval.
- Record fixes and reusable lessons.

Important rule: external replies should not be auto-sent without explicit approval.

## WhatsApp/Gmail Communications Memory

The communications memory stores normalized summaries of:

- WhatsApp thread observations.
- Gmail thread observations.
- Work items.
- Draft replies.
- Media references.
- Scan runs.

The goal is continuity: agents should know what is active, blocked, done, waiting, and drafted without rereading every raw private conversation.

For GitHub, publish only summaries and schemas. Do not publish raw WhatsApp/Gmail text.

## Crowdsnare Signal Desk

Signal Desk is the shared dashboard/work queue built around the communications memory.

It reads:

- Work items.
- Bugs.
- Draft replies.
- Threads.
- Media references.
- Scan-run status.
- Cross-machine state events.

It exists so multiple AI sessions/machines can coordinate without losing state.

Key behavior:

- It is a dashboard and queue, not the durable source of truth.
- It must not expose secrets.
- It must not send WhatsApp or Gmail replies on its own.
- Supabase mirrors the data for hosted access.

## Cross-Machine Reconciliation

A deterministic reconciler checks whether work was completed elsewhere before another agent continues stale tasks.

Expected behavior:

- Read local KB/comms state.
- Read hosted Signal Desk/Supabase state.
- Compare active items and terminal states.
- Append safe superseding state events when the remote terminal state is proven.
- Leave ambiguous conflicts for review.

## Operational Guardrails

- Keep secrets in managed credential stores, not Markdown.
- Do not paste credentials into chat, Signal Desk, or GitHub.
- Keep raw customer conversations out of public docs.
- Record decisions and failed paths so future agents do not repeat them.
- Prefer deterministic checks and scripts over prompt-only process.

## Internal Tooling Worth Preserving

The following categories should be preserved during handoff:

- n8n workflow audit scripts.
- GHL webhook/custom-value audits.
- Manual takeover coverage audits.
- Calendar booking cleanup audits.
- Self-hosted migration matrix scripts.
- Signal Desk sync/reconcile scripts.
- WhatsApp/Gmail summary ingestion scripts.
- Test/demo page verification scripts.
