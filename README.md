# KAIROS Assessment — plugin for Grok Bot, Cursor, and MCP hosts

**What it does.** Runs the KAIROS business readiness assessment inside
your agent chat. Five short questions — team size, repetitive load,
biggest bottleneck, the business in one sentence, readiness — return a
plain-language recommendation: which AI department setup fits, and
why. Already have a discovery-call transcript or intake notes? Your
agent can submit the answers it finds there in a single call instead —
no re-answering.

The assessment is free, needs no account, and quotes no prices in
chat. It ends with a next-step link; anything beyond the assessment
happens only if you open it and sign up yourself.

**Tools**

| Tool | Label | What it does |
|---|---|---|
| `kairos_assessment_start` | Write | Opens a session, returns question 1 |
| `kairos_assessment_answer` | Write | Records one answer, returns the next question or the recommendation |
| `kairos_assessment_submit` | Write | Completes the assessment in one call from existing answers (e.g. a transcript) |
| `kairos_assessment_cta` | Read | Returns the next-step link for a completed session |

**Configure variables.** None. The assessment endpoint is public and
rate-limited; no key, no sign-in, no credentials of yours are ever
requested or stored.

**Privacy.** The assessment server stores nothing. Your answers
travel between calls inside a signed token your own agent carries,
and are used only to produce the recommendation. Nothing is sent
anywhere on your behalf.

## Test locally

The package points at the hosted endpoint in `mcp.json`. To exercise
the tools from any MCP client, add the server from `mcp.json` and ask
your agent to "run the KAIROS assessment".

Cursor IDE local load:

```bash
ln -s /path/to/kairos-assessment ~/.cursor/plugins/local/kairos-assessment
```

Then reload the window and confirm the `kairos-assessment` skill and
MCP server load.

## Submit

- Grok Bot / Cursor marketplace: https://x.ai/bot/marketplace/submit-a-plugin
- License: MIT (see LICENSE) — the plugin package is open; the
  assessment service itself is hosted by KAIROS AI Systems.

Built by KAIROS AI Systems — https://kairosasi.com
