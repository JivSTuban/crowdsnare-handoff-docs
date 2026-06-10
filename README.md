# Crowdsnare Handoff Documentation

This folder is a GitHub-ready, sanitized handoff package for Crowdsnare's AI automation work.

## Navigation

Start here, then follow the docs in order if you are learning the system from scratch.

| Order | Document | Use It For |
| --- | --- | --- |
| 1 | `01-request-summary.md` | What was requested, what this package covers, and what website work is still separate. |
| 2 | `02-platform-overview.md` | The big-picture system: GHL, n8n, Supabase, AI models, voice providers, and Vercel. |
| 3 | `03-ai-products.md` | The seven AI products and the common controls they should all support. |
| 4 | `04-client-onboarding-and-provisioning.md` | How a new dealership subaccount should be onboarded and provisioned. |
| 5 | `05-operations-and-internal-tools.md` | Internal tooling: bug-fix automation, comms memory, Signal Desk, and reconciliation. |
| 6 | `06-open-items-and-risks.md` | Known gaps, active risks, and recommended next steps. |
| 7 | `SOURCE_INDEX.md` | What internal source areas were reviewed to compile this package. |
| 8 | `SANITIZATION.md` | What was removed or avoided so this package can be shared publicly. |

## Question Map

| Question | Read |
| --- | --- |
| What is Crowdsnare? | `02-platform-overview.md` |
| What are the AI products? | `03-ai-products.md` |
| How do client subaccounts work? | `02-platform-overview.md`, then `04-client-onboarding-and-provisioning.md` |
| How are clients onboarded? | `04-client-onboarding-and-provisioning.md` |
| How would setup be automated? | `04-client-onboarding-and-provisioning.md` |
| What internal automation projects exist? | `05-operations-and-internal-tools.md` |
| What is Signal Desk? | `05-operations-and-internal-tools.md` |
| What still needs work? | `06-open-items-and-risks.md` |
| What was excluded for safety? | `SANITIZATION.md` and `SOURCE_INDEX.md` |

## Package Shape

It answers the current handoff questions:

- What is Crowdsnare?
- What AI products exist?
- How are clients onboarded?
- How should client subaccounts and AI products be provisioned?
- What internal automation projects were built around the work?
- What is still open or risky?

## Important Boundary

This package intentionally does not include:

- API keys, tokens, passwords, OAuth secrets, private access tokens, or service-role keys.
- Raw WhatsApp/Gmail transcripts.
- Personal identity details, private payment discussion, or private local machine paths.
- Customer lead exports, private screenshots, or raw support conversations.
- Dealer-specific credential files or `.env` files.

Use this as a clean external documentation set. Keep operational secrets in the existing controlled systems, not in GitHub docs.
