# AI Phone Intake — the calling system (secure & non-secure builds)

**What it is:** an AI voice agent phones your patient before the visit (Twilio
line + AI voice), runs the full InstantHPI process by phone — the structured
intake questions → the HPI confirmation summary → the 10 follow-up questions —
and hands you the transcript. That transcript then feeds the reasoning
(what we call **#7**), the draft prescriptions, and the documents. **Before
you ever see the patient, ~95% of your work is pre-made.**

We have built and run this. It works — and it bit us. Below: the two ways to
build it, and every difficulty we hit so you don't rediscover them.

## The two builds

### 1. NON-SECURE build (prototyping ONLY — never real patients)
- **Stack:** ElevenLabs Conversational AI (agent + voice) + Twilio number
  for outbound calls.
- Fast to stand up (an afternoon), stunning voices, good for demos and for
  testing your question flow with fake patients.
- **Why it is non-secure:** ElevenLabs consumer/Creator tiers offer **NO BAA**
  — you cannot lawfully run identifiable patient calls through it (HIPAA, and
  in Quebec, Loi 25). Treat it strictly as a lab bench.

### 2. SECURE build (real patients) — Amazon AWS end to end
- **Voice AI:** **Amazon Nova Sonic** (speech-to-speech) on **AWS Bedrock**
  under your **BAA** — the conversation never leaves the covered environment.
- **Telephony:** Twilio (sign Twilio's BAA — they offer one) or Amazon
  Connect + Chime SDK to keep even the call leg inside AWS.
- **Pipeline:** Connect/Twilio call ⇄ Nova Sonic (runs the scripted intake:
  questions → HPI confirm → 10 Qs) → transcript stored in S3 (BAA,
  server-side encrypted) → your #7 reasoning + document drafting runs on
  Bedrock models over the transcript.
- **Regional caveat (learned the hard way):** Nova Sonic runs in **US
  regions only** — if your privacy law requires in-country processing (e.g.
  Quebec's Loi 25 preference for ca-central-1), either document the
  cross-border safeguards or fall back to the AWS build we validated in
  ca-central-1: **Transcribe ⇄ your Bedrock LLM ⇄ Polly** (slightly more
  robotic, fully in-region).

## The difficulties we actually hit (read before building)

1. **No BAA on the pretty voices.** ElevenLabs Creator tier = no BAA. Don't
   let voice quality seduce you into a compliance breach.
2. **The LLM skips your script.** Our agent kept skipping the Phase-3
   10-question stage; generic models "helpfully" shortcut multi-phase flows.
   Fix: enforce the phase machine in the prompt (numbered phases, explicit
   "do not advance until all questions asked"), and verify per-call.
3. **Voice model choice matters:** in ElevenLabs, the realtime-capable
   multilingual model sounded natural; the fast/turbo variant was robotic;
   the top-quality model wasn't realtime. Test the exact combination.
4. **Naturalness in French** took a custom Twilio⇄LLM bridge (we validated a
   Gemini-based bridge that sounded genuinely natural) — expect language-
   specific tuning.
5. **Keys and tiers rot:** stored API keys died between sessions; make fresh
   unrestricted keys part of your runbook.
6. **Patients answer phones unpredictably:** voicemail detection, callbacks,
   consent line at call start ("this is an AI assistant calling on behalf of
   Dr. X — may we proceed?") are not optional extras; they're the product.
7. **Never let the AI freelance:** the agent asks the scripted questions and
   confirms the summary. It does not give advice on the call. The doctor is
   the only audience of the reasoning output.

## Security rules for patient + clinic

- BAA on every link in the chain (voice AI, telephony, storage, LLM).
- De-identify before any non-BAA processing; identity stays in your EMR.
- Record consent at call start; store transcripts encrypted (S3 SSE) with
  access logging; retention per your jurisdiction.
- The call output is a DRAFT: the physician reviews everything (the work is
  AI; the verification is 100% yours).

Want it built for you instead? Use the intake form at
https://instanthpi.ai/physicians/ — this system is one of the automation
levels we install.
