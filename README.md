# InstantHPI for Doctors — automate the grind, reclaim your life

**Audience: physicians.** This repository is the doctor-side of the Free
Universal Healthcare AI project: the architecture one board-certified family
doctor used to automate his own practice, published as sanitized patterns —
**no patient data, no secrets, no API keys, ever.**

Sibling repos, one per audience so nothing mixes:
[free-universal-healthcare-ai](https://github.com/carlosfalai/free-universal-healthcare-ai)
(patients — the free bot, MIT) ·
[instanthpi-web](https://github.com/carlosfalai/instanthpi-web)
(the public pages).

## The architecture (what actually runs)

```
INTAKE SOURCES                       THE PIPELINE
 secure messaging (Spruce) ────┐
 fax + document routing ───────┤   1. real-unread scan — who is truly
 email intake AI ──────────────┤      waiting (inbound-last law)
 booking rosters ──────────────┤   2. one actionable rule + one disposition
 pseudonym email channel ──────┘      store (no recycled, no double-shown)
                                   3. card builder — locked spec: identity,
                                      labs, options WITH a recommendation
                                   4. serve-time gate — live re-verify before
                                      showing; handled cases auto-evict
      doctor swipes ────────────▶  5. work-ledger — state machine
      (the carousel)                  CREATED→DECIDED→EXECUTING→DONE,
                                      append-only log, idempotent
                                   6. executor — approved decision → agent
                                      carries it out, source-faithful
```

Principles that make it safe:
- **The work is 100% AI; the physician does 100% of the verification.**
- Multiple AIs debate every case and must cite studies/guidelines; consensus
  only; disagreement surfaced, never hidden.
- Deterministic pipelines and locked templates beat chat drift — fail closed.
- De-identified content only in every API call (see
  [SECURITY.md](https://github.com/carlosfalai/free-universal-healthcare-ai/blob/master/SECURITY.md)).
- Real patient data → AWS Bedrock under BAA. Building → Claude Code + Sonnet 5.

## The Physician Guild — InstantHPI Physician Network

Physicians are verified as valid practitioners against their regional medical
boards and receive an ID — so they, and their approved AI works, carry proof
of work and verification. Doctors from all over the world, involved in the
care of patients all over the world, at record time.

Join ($100/month — keeps InstantHPI free for physicians and funds the
roadmap): https://buy.stripe.com/4gMcN61u6fehf4I3yfbMQ44

## Learn it end to end

Module 5 of the course ("Automating a Medical Practice", $35 — free for
everyone once 1,000 buy it): https://instanthpi.ai/courses

Contact: cff@centremedicalfont.ca · Support: https://instanthpi.ai/donations
