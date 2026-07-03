# Real prices (verified from official vendor pages, 2026-07-03)

No estimates — these are the published numbers, with sources. Re-check before
budgeting; prices move.

## Spruce Health — sprucehealth.com/plans
- **Basic: $24/user/month** — includes signed **BAA**, medical phone/text/video/fax,
  shared inbox, auto-replies, AI voicemail transcription. No per-minute charges.
- **Communicator: $49/user/month** — adds IVR call flows, after-hours triage,
  **API access** (needed for our automations), VoIP, AI call summaries.
- One-time $19.50 SMS registration. 14-day free trial, month-to-month.
- **Bottom line: the whole secure backbone of a solo practice is $24–49/mo.**

## Twilio — twilio.com/pricing
- US SMS: **$0.0083/message** · US outbound voice: **$0.014/min** (inbound $0.0085)
- Phone number ≈ $1.15/mo (support-article figure; confirm in console)
- **BAA: contact-sales only** (Security/Enterprise Edition). For BAA-covered
  calling without sales calls, use **Amazon Connect: $0.038/min** (HIPAA-eligible
  under the standard AWS BAA).

## SRFax (fax) — srfax.com healthcare plans (CAD, BAA included in ALL tiers)
- Lite **$12.60/mo / 200 pages** · Basic **$16.05 / 500p** · Standard **$41.35 / 1,500p**
- Professional **$137.90 / 5,000p** … up to 20,000p tiers. Overage **$0.05/page**.

## AWS (all HIPAA-eligible under your BAA)
- **Textract OCR: $0.0015/page** (first 1M pages/mo) — a 500-page chart = $0.75
- **Amazon Connect voice: $0.038/min**
- **Nova Sonic** (speech-to-speech): ≈ $0.0034/1k speech-in + $0.0136/1k
  speech-out tokens (≈ cents/minute; re-verify at aws.amazon.com/nova/pricing)
- Claude on Bedrock: Haiku $1/$5 · Sonnet $3/$15 · Opus $5/$25 per 1M tokens

## DeepSeek — api-docs.deepseek.com (no BAA — de-identified text only)
- **deepseek-v4-flash: $0.14/1M in (cache miss; $0.0028 cache hit!) · $0.28/1M out**
- deepseek-v4-pro: $0.435/1M in · $0.87/1M out
- A full consult ≈ **well under 1 cent**. This is the $0.003/consult claim, verified.

## ElevenLabs (voice) — elevenlabs.io/pricing
- Creator $22/mo (275 agent-min) · Pro $99/mo (1,238 min) · overage **$0.08/min**
- **BAA: Enterprise tier ONLY (contact sales).** Anything below = prototyping
  only, never real patients.

## What a day actually costs (30-patient solo async day)
- Spruce: ~$1.60/day ($49/mo) · AI drafting (DeepSeek de-identified): ~$0.10
- Bedrock de-id + council on 30 cases (Haiku+Sonnet): ~$1–3
- 20 fax pages: $1 · Invitation sequence w/ calls: ~$2–5
- **Total: roughly $5–10/day in tooling to run a practice that used to need a
  secretary.** The economics are not the barrier.
