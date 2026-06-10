# 03 - AI Products

Crowdsnare currently has seven main AI products.

## 1. Web Chat Agent

Website visitor chats with the dealer website widget. GHL receives the chat, n8n generates a response, and GHL sends the reply back through the web chat channel.

Typical responsibilities:

- Answer sales questions.
- Qualify the visitor.
- Recommend next action.
- Route to appointment booking or manual takeover.

## 2. Speed-To-Lead SMS Agent

New inbound leads receive fast SMS follow-up. The agent continues the conversation, qualifies the lead, and attempts to move the contact toward a booking or staff handoff.

Typical responsibilities:

- First response to new leads.
- Appointment intent detection.
- Stop/no-bump handling.
- Service/parts transfer when applicable.

## 3. Speed-To-Lead Email Agent

Email equivalent of speed-to-lead, commonly tied to ADF/XML or lead-provider email intake.

Typical responsibilities:

- Parse incoming lead context.
- Generate a relevant email reply.
- Track memory and qualification state.
- Avoid duplicate or stale replies.

## 4. Private Sale Agent

Outbound campaign agent for private-sale or trade-in style opportunities.

Typical responsibilities:

- Send campaign-driven outreach.
- Identify interest, not-interested, wrong-person, and already-purchased states.
- Move contacts through the correct pipeline states.
- Stop follow-up when the conversation reaches a terminal state.

## 5. Facebook Agent

Facebook Messenger lead response agent connected through GHL.

Typical responsibilities:

- Respond to Facebook lead messages.
- Qualify and route the customer.
- Apply the same manual takeover and stop-state discipline used by other text products.

## 6. DBR Agent

Database Reactivation agent for dormant leads and existing CRM contacts.

Typical responsibilities:

- Re-engage older leads.
- Handle stop states and already-purchased states safely.
- Book appointments.
- Prevent unwanted bumps after terminal outcomes.
- Maintain pipeline movement and campaign cleanup.

## 7. AI Voice Receptionist / Voice Agent

Phone or demo-call AI flow using voice infrastructure and n8n/GHL integration.

Typical responsibilities:

- Answer or place demo calls.
- Route language-specific demos when needed.
- Collect lead information.
- Trigger follow-up based on call outcome.

## Cross-Product Controls

Every product should support:

- Manual takeover.
- Stop/no-bump behavior.
- Booked appointment cleanup.
- Wrong-person and already-purchased handling.
- Product-specific tool workflows.
- Client-specific configuration lookup.
- Safe QA before production traffic.

## Current Documentation Status

The repo already has product-specific architecture docs for these seven products. This handoff package summarizes them in sanitized form. The deeper source docs should be reviewed before implementation work, but they should be scrubbed before being published publicly because some source docs contain internal IDs or operational paths.
