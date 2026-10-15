---
name: kairos-assessment
description: Run the KAIROS business readiness assessment for the user. Use when they ask what an AI department or agent team could do for their business, which automation setup fits them, or when they share a discovery-call transcript or intake notes and want a recommendation.
---

# KAIROS business readiness assessment

The assessment is five short questions. It ends with a plain-language
recommendation — which setup fits their business and why — and a
next-step link. It is free and needs no account.

## Two ways to run it

**Guided (default).** Call `kairos_assessment_start`, then ask the
user ONE question at a time. Pass each reply to
`kairos_assessment_answer` together with the `state` value from the
previous tool result (it carries the assessment progress — pass it
back unchanged) and the question index. Never batch questions, never
paraphrase a question's options, and never answer on the user's
behalf. After the fifth answer the tool returns the recommendation.

**One-shot (from a transcript).** When the user shares a discovery-call
transcript, intake notes, or answers in any form, extract the five
answers and call `kairos_assessment_submit` once:
- `team`: "Just me", "2–10", "11–50", or "51+"
- `repetitiveWork`: 1–5, how much of their week is repetitive work
- `bottleneck`: "Finding and closing customers", "Delivering /
  fulfilling work", "Finance, invoicing and admin", or "Customer
  support and follow-up"
- `businessDescription`: their business in one sentence
- `readiness`: 1–5, how ready they are to start this quarter
If the material doesn't cover a field, ask the user for just that one
— never guess a value the material doesn't support.

## Presenting the result

Relay the recommendation and its reason in plain language, and name
the other tiers briefly so the user sees the full ladder. Then call
`kairos_assessment_cta` with the `state` from the completed result and
your surface as `channel` (for example "grok-bot" or "cursor") and
present the link as the way to continue.

## Hard rules

- **Never state a price.** Pricing lives behind the next-step link.
  If the user asks what it costs, say the link shows current pricing
  and the assessment itself is free.
- **Never invent results.** Only report the tier and reason the tool
  returned.
- **The link is the handoff.** The user opens it and completes any
  signup themselves. You never submit forms, payments, or signups on
  their behalf, and you never send messages to KAIROS or anyone else
  as part of this flow.
- If a tool call errors (expired session, invalid answer), say so
  plainly and offer to restart — don't paper over it.
