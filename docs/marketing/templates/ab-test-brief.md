# Template — A/B Test Brief

Design an experiment BEFORE running it, so the result is interpretable. Fill this, run it, then record the outcome in `../experiments/ab-test-log.md`.

## Prompt (copy this into Claude)

```
Read context/metrics.md and context/customers.md.

Help me design an A/B test for Petio marketing.

INPUTS:
- Surface: <TikTok hook | App Store paywall | bio CTA | screenshot order | blog title | ...>
- What I want to improve: <views | CTR | Food Checker visits | install | free→paid conversion>
- My idea for the change: <describe variant B>

REQUIREMENTS:
- Force a SINGLE-variable test. If I'm changing more than one thing, tell me and split it.
- Output the brief in this exact shape:
  • Hypothesis: "We believe <B> will <outcome> because <reason>."
  • Variant A (control) / Variant B
  • Primary metric (one) + guardrail metric (don't-break)
  • Minimum sample or duration so the result isn't noise (be concrete given our small volume)
  • What result = ship B / keep A / inconclusive
- Flag if our traffic is too low to get a clean read, and suggest a cheaper proxy if so.
```

## Reminders for a small-volume startup
- Low traffic → small differences are noise. Prefer tests with **big expected effects** (hook format, paywall default) over tiny ones (button color).
- **One variable.** Always.
- Decide the stopping rule **before** you look at results (avoid peeking bias).
- Record every test — even losers. A "no difference" result is still learning.

## After running
- [ ] Result recorded in `experiments/ab-test-log.md`
- [ ] Winner fed back into the relevant calendar/template/plan
