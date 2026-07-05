# Lessons for the Physician in Solo Practice

Field-tested lessons from a board-certified family doctor running a solo
asynchronous practice. Copy everything here, then **discuss with Claude Code
to adapt it** — your clinic name, your credentials, even your signature.

## Lesson 1 — Use Spruce Health as your backbone

Secure patient messaging, phone, fax — one inbox, BAA available. Async
messaging is what makes solo practice survivable: patients write when they
want; you answer in batches on your schedule.

## Lesson 2 — Build reputation with a default end-of-consultation message

Send a rich closing message after EVERY first encounter — **systematically,
even when you don't feel like it. You'll be surprised by the outcomes.**
Ask patients to SHARE their experience (review link) — you want the patients
to share. The message also: sets follow-up expectations, states your scope,
promotes your free tools, and routes new patients.

Below is the actual production template (French, Truck Stop Santé). **You are
welcome to copy it and modify it to your practice** — paste it into Claude
Code and say: *"replace clinic name, review link, forms, credentials and
signature with mine."*

```
Votre prescription a été transmise à votre pharmacie. Je vous recommande de
vérifier auprès d'eux qu'elle est prête avant de vous y rendre.

Étant donné que vous recevez un traitement et que vous avez des symptômes,
veuillez garder un suivi avec moi ici dans 14 jours. Ne prenez pas de
rendez-vous, écrivez-moi simplement ici.

🛻💨 ➕ 🤧🤒😩 ➡️ 📲👨‍⚕️📝💊 ➡️ 😌💪🛣️🌟

Truck Stop Santé à votre service. 🫡🚚

Merci de partager votre expérience avec notre clinique : cela aide d'autres
personnes à comprendre nos services. Vous pouvez laisser votre avis ici :
https://g.page/r/CS7XOfBDzFhoEAI/review

J'ai créé @instanthpibot, un outil éducatif gratuit, disponible 24/7, dans
n'importe quelle langue.

C'est pour qui? Tout le monde. Camionneurs sur la route, familles sans
médecin de famille, immigrants qui ne parlent pas encore français ou anglais,
n'importe qui qui a des symptômes et ne sait pas par où commencer, personnes
sans accès aux médecins dans le tiers monde, etc.

Ça fait quoi? C'est un peu comme votre consultation ici, mais à titre
éducatif seulement et sans médecin derrière. 100% IA. Je pense en tant que
médecin que ce sera un des outils les plus précieux des personnes qui ont de
la difficulté à obtenir des soins à l'avenir. Ça fait 3 ans que j'y
travaille.

Vous décrivez vos symptômes, et l'assistant vous génère un bilan éducatif
complet : résumé de votre situation, exemples de documents médicaux
(ordonnance, référence, note SOAP, demande de labo/imagerie), raisonnement
clinique, chronologie, et questions fréquentes — tout ça en quelques minutes.

Ça aide comment? Quand vous arrivez chez un médecin avec un résumé clair de
vos symptômes, la consultation va plus vite et rien n'est oublié.

Combien ça coûte? Gratuit. Zéro. Rien. Ça me coûte 0.003$ par consultation,
donc avec 1000$usd, je peux financer 333 000 consultations...

👉 Essayez-le : t.me/instanthpibot — puis dites-moi ce que vous en pensez.
Je publie tout sur cette épopée sur www.instanthpi.com

Gardez-moi en tête pour vos urgences mineures ponctuelles, on est en mode
asynchrone. Pour référer des gens : http://www.m28.ca

Je ne prends pas de patients comme médecin de famille et je ne fais pas de
suivi longitudinal. J'offre des consultations médicales pour urgences
mineures ponctuelles chez les adultes seulement, en télémédecine asynchrone
[... scope: infections urinaires simples, sinusites, IVRS légères,
conjonctivites, peau, MSK léger, renouvellements ponctuels non contrôlés,
certificats courts, ajustements simples. PAS: enfants, grossesses, chronique
complexe, urgences graves, CNESST sans évaluation en personne.]
Pour un suivi global et continu, il est important d'avoir un médecin de famille.

À bientôt. 🫡

Vous êtes toujours bienvenue de remplir le formulaire en ligne et de m'envoyer
votre identifiant alphanumérique ici (clé-serrure) :
https://fs7.formsite.com/zUW21K/qrzblnvwq3/index
```

Why it works: the follow-up line fills your future schedule; the share ask
compounds your reputation; the scope paragraph prevents mismatched demands;
the alphanumeric identifier links forms to chats without exposing identity.

## Lesson 3 — Automate your PDFs under a BAA

The pipeline we run (all inside BAA-covered systems):
1. **Scan/fax arrives** → OCR + read with **Claude Sonnet 5 on AWS Bedrock**
   (BAA) — never a consumer endpoint for identifiable documents.
2. AI processes the document → **generates the patient message + a mini-SOAP
   text** → pushed **through the Spruce API** into the conversation and the
   internal message/note. You review and send.
3. **Outbound faxing:** SRFax (HIPAA-compliant fax API) — prescriptions,
   referrals, reports go out programmatically.
4. **Do ALL your PDFs with AI:** SOAP notes, prescriptions, referrals, lab
   requisitions, work notes — from locked templates (see the
   [PDF Filler maquette](https://github.com/carlosfalai/instanthpi-pdf-filler)).
   Deterministic templates beat chat drift; the AI fills, you sign.

## Lesson 4 — Everything is a template; Claude Code is the tailor

Take every artifact in this repo — messages, SOAP formats, document
templates, pipelines — paste into Claude Code and say what to change:
clinic name, credentials, review links, forms, **your signature**. The
system is the lesson; the personalization is an afternoon.

---
*Maquettes, not certified products. You review everything AI produces; your
license, your jurisdiction's privacy law, your responsibility. Questions:
cff@centremedicalfont.ca · https://instanthpi.ai/physicians/*

## Lesson 5 — Why asynchronous beats scheduled visits

For the patient: no appointment to hunt, no waiting room, no time off work —
they write when symptoms happen and get an answer the same day. For you: no
no-shows, no schedule tyranny, batch your responses when YOUR brain is fresh,
and one doctor can honestly serve far more patients. Scheduled visits force
both parties to guess when illness will be convenient; async lets care follow
reality. **Spruce makes this trivially affordable** (tens of dollars a month,
BAA included) — the whole practice runs on it.

## Lesson 6 — The patient warning system

Async is safe only with an explicit safety net, stated once per episode:
- Red-flag instructions live in the course-of-action paragraph ONLY — once,
  clearly ("if X happens, call emergency services"), not appended reflexively
  to every message (that dilutes it to noise).
- Timed follow-ups ("write me here in 14 days") create scheduled safety
  checkpoints without appointments.
- Scope statement in your closing template = patients know what NOT to bring
  to async care.
- Every result — normal or abnormal — owes the patient a message. Filed and
  silent is not an option.

## Lesson 7 — Boost it with AI: everything that can be automated

The full list of what we run or have validated — each one buildable:
1. Conversational AI intake before the visit (skips what the chart knows)
2. AI phone-call intake (see VOICE-INTAKE-CALLS.md)
3. HPI summary + follow-up questions, auto-generated per case
4. Multi-AI council reasoning with guideline citations (#7 reasoning)
5. Draft patient replies in the patient's language, your voice, your length
6. Mini-SOAP auto-generated into the internal note
7. Scan/fax OCR → classify → route → draft response (Sonnet 5 on Bedrock, BAA)
8. All PDFs by AI from locked templates: prescriptions, referrals, lab reqs,
   work notes, insurer forms (PDF Filler maquette)
9. Outbound HIPAA fax via SRFax API
10. Results routing: every result → patient message drafted (normal reassure /
    abnormal explain+plan)
11. Follow-up scheduler: the "14 days" line, tracked automatically
12. Reputation engine: closing template + share ask after every 1st encounter
13. Billing validation (decode + cross-check health-number before submitting)
14. Decision carousel: one gated card per waiting patient, swipe to decide,
    executor carries it out and logs it
15. Your own free educational bot as patient magnet (our bot kit, MIT)

## Lesson 8 — Create your own AI tools and platforms

Don't just consume platforms — build on their APIs: Spruce API (messages,
contacts, internal notes), SRFax API (fax in/out), Stripe (payments), AWS
Bedrock (BAA-covered models), Telegram Bot API (patient-facing bots). Every
tool in this ecosystem is a maquette you can hand to Claude Code: "adapt
this to my clinic" — name, credentials, signature, language. The doctor who
owns their tools owns their time.

## Lesson 9 — The invitation sequence (SMS + email + 3 AI calls)

Getting patients ONTO the secure channel is its own system. Ours, end to end:

**The flow per patient:**
1. **SMS + email invitation** — "log in to Spruce" (the secure channel), with
   the link. Sent the moment they're on today's list.
2. **Verify joined** — did they appear in Spruce? If yes, done.
3. **AI call #1, #2, #3** — a natural-voice AI phones them (we validated a
   Twilio⇄AI bridge that sounds genuinely human in French), explains, and
   walks them into logging in. Spaced across the day.
4. **All 3 calls fail →** generate the SOAP note anyway from what we have,
   and **email the patient** a summary of every step we took and how to
   reach us. Nothing silently dropped; the chart shows the whole trail.

**How you run it — a terminal, nothing fancier:** open PowerShell, run the
script, and **paste today's patient list (name, phone, email — one per
line).** The system does the rest and prints a status table: joined /
calling / exhausted→emailed+SOAP.

**Build it yourself — paste this to Claude Code:**

> "Build me the patient invitation sequence as a PowerShell-launched Node
> script: I paste lines of `name, phone, email`. For each: (1) send SMS via
> Twilio API + email via my SMTP asking them to join my Spruce link; (2)
> poll the Spruce API to detect if they joined; (3) if not joined after N
> hours, place up to 3 AI voice calls via Twilio using [Gemini/Nova Sonic]
> with this exact script: [paste your call script]; (4) if all 3 fail,
> draft a SOAP note from the booking info and send the patient a summary
> email of all attempts. Log every step to a CSV. Use env vars for all
> keys. My clinic name/credentials/signature: [yours]."

**What it costs (realistic, per patient invited):**
- SMS: ~$0.01 · Email: ~$0 · AI voice calls: Twilio ~$0.014/min + the AI
  voice (Gemini-class ≈ pennies; Nova Sonic ≈ ~$0.06/min; ElevenLabs
  ~$0.10–0.30/min — prototype only, no BAA)
- **Typical: under $0.50/patient even with all 3 calls; ~$0.01 if they join
  on the SMS.** A 30-patient day ≈ a couple of dollars.
- Fixed: Spruce ~$25–50/user/mo · Twilio number ~$1.15/mo.

The lesson inside the lesson: the sequence is polite persistence with a
paper trail — and the paper trail (SOAP + summary email) is what protects
you when a patient never shows up on the channel.

### Lesson 9b — The AI call script + the full code

**When the AI schedules the calls:** the calls are spaced across the day (not
back-to-back) so the patient has time to act between them — e.g. call #1 at
T+2h after the SMS if not joined, call #2 at T+5h, call #3 at T+8h. Each call
asks the patient to **log into Spruce for their conversation** — the call
never gives medical advice, it only shepherds them onto the secure channel.

**The call script the AI speaks (adapt to your clinic):**
```
Bonjour, ici l'assistant de la clinique Truck Stop Santé qui appelle de la
part du Dr Font. Ceci est un message automatisé. Vous avez une consultation
en attente. Pour la compléter en toute confidentialité, veuillez vous
connecter à Spruce — le lien vous a été envoyé par texto et par courriel.
C'est là que se déroule votre conversation avec le médecin. Si vous avez
besoin d'aide pour vous connecter, répondez au texto. Merci, et à bientôt
sur Spruce.
```

**The full working scripts** (also shipped as files in this repo:
`invite/invite.js`, `invite/run.ps1`, `invite/.env.example`). Copy, set your
keys, run in PowerShell, paste today's list.

`run.ps1` — what you launch:
```powershell
# run.ps1 — paste today's patients, one per line: Name, phone, email
Write-Host "Paste patients (Name, +1phone, email). Blank line to finish:" -ForegroundColor Cyan
$lines = @(); while ($true) { $l = Read-Host; if ([string]::IsNullOrWhiteSpace($l)) { break }; $lines += $l }
$lines | Set-Content -Encoding utf8 "$PSScriptRoot\today.csv"
node "$PSScriptRoot\invite.js" "$PSScriptRoot\today.csv"
```

`invite.js` — the sequence engine (Node; Twilio SMS+voice, SMTP email,
Spruce poll, fail→SOAP+email). Keys via env. This is a maquette — review,
then hand to Claude Code to finish/adapt:
```js
// invite.js  — usage: node invite.js today.csv
// env: TWILIO_SID, TWILIO_TOKEN, TWILIO_FROM, SMTP_URL, FROM_EMAIL,
//      SPRUCE_API_KEY, SPRUCE_BASE, TTS_URL (your AI-voice TwiML endpoint)
const fs = require('fs');
const rows = fs.readFileSync(process.argv[2],'utf8').trim().split(/\r?\n/)
  .map(l => l.split(',').map(s=>s.trim())).map(([name,phone,email])=>({name,phone,email}));

const SPRUCE_LINK = process.env.SPRUCE_LINK || 'https://your.spruce.care/xxxx';
const CALL_OFFSETS_H = [2,5,8];                 // when the 3 calls fire if not joined
const CALL_SCRIPT = `Bonjour, ici l'assistant de la clinique de la part du Dr Font. `+
  `Ceci est un message automatise. Vous avez une consultation en attente. `+
  `Veuillez vous connecter a Spruce, le lien vous a ete envoye par texto et courriel. `+
  `C'est la que se deroule votre conversation avec le medecin. Merci.`;

async function twilio(path, params){
  const url = `https://api.twilio.com/2010-04-01/Accounts/${process.env.TWILIO_SID}/${path}`;
  const body = new URLSearchParams(params);
  const r = await fetch(url,{method:'POST',
    headers:{Authorization:'Basic '+Buffer.from(process.env.TWILIO_SID+':'+process.env.TWILIO_TOKEN).toString('base64'),
             'Content-Type':'application/x-www-form-urlencoded'}, body});
  return r.json();
}
const sms  = (to,msg)=>twilio('Messages.json',{To:to,From:process.env.TWILIO_FROM,Body:msg});
// TwiML that speaks CALL_SCRIPT — host a tiny endpoint returning:
//   <Response><Say language="fr-CA">...CALL_SCRIPT...</Say></Response>
// or use <Play> with an AI-generated (Nova Sonic/Gemini) audio URL.
const call = (to)=>twilio('Calls.json',{To:to,From:process.env.TWILIO_FROM,Url:process.env.TTS_URL});

async function email(to,subject,text){
  const nodemailer = require('nodemailer');
  const t = nodemailer.createTransport(process.env.SMTP_URL);
  return t.sendMail({from:process.env.FROM_EMAIL,to,subject,text});
}
async function joined(email){                    // poll Spruce: has this contact joined?
  const r = await fetch(`${process.env.SPRUCE_BASE}/v1/contacts?email=${encodeURIComponent(email)}`,
    {headers:{Authorization:'Bearer '+process.env.SPRUCE_API_KEY}});
  const d = await r.json().catch(()=>({}));
  return !!(d.contacts && d.contacts.some(c=>c.status==='active'));
}
async function draftSOAP(p){                      // fail-safe SOAP from booking info (swap in Bedrock BAA)
  return `SOAP (auto-draft, review required)\nPatient: ${p.name}\nS: pending — patient not reachable on channel\n`+
         `O: n/a\nA: consultation not completed; 3 call attempts + SMS + email failed\nP: emailed patient all steps; awaiting login`;
}
const sleep = h => new Promise(r=>setTimeout(r, h*3600*1000));

(async ()=>{
  for (const p of rows) {
    console.log('→', p.name);
    await sms(p.phone, `Bonjour ${p.name}, connectez-vous a Spruce pour votre consultation: ${SPRUCE_LINK}`);
    await email(p.email, 'Votre consultation — connectez-vous a Spruce',
      `Bonjour ${p.name},\n\nConnectez-vous a Spruce pour votre consultation: ${SPRUCE_LINK}\n\nMerci.`);
  }
  for (let i=0;i<CALL_OFFSETS_H.length;i++){
    await sleep(i===0 ? CALL_OFFSETS_H[0] : CALL_OFFSETS_H[i]-CALL_OFFSETS_H[i-1]);
    for (const p of rows){
      if (p.done) continue;
      if (await joined(p.email)) { p.done=true; console.log('✓ joined', p.name); continue; }
      console.log(`call #${i+1} →`, p.name); await call(p.phone);
    }
  }
  for (const p of rows){
    if (p.done) continue;
    console.log('✗ exhausted →', p.name, '→ SOAP + summary email');
    await email(p.email,'Votre consultation — nos tentatives',
      `Bonjour ${p.name},\n\nNous avons tente de vous joindre (texto, courriel, 3 appels) sans succes. `+
      `Connectez-vous a Spruce quand vous le pouvez: ${SPRUCE_LINK}\n\nMerci.`);
    fs.appendFileSync('soap-drafts.txt', await draftSOAP(p) + '\n\n---\n\n');
  }
  console.log('done. review soap-drafts.txt');
})();
```

`.env.example`:
```
TWILIO_SID=       TWILIO_TOKEN=      TWILIO_FROM=+1...
SMTP_URL=smtps://user:pass@smtp.host:465   FROM_EMAIL=you@clinic
SPRUCE_API_KEY=   SPRUCE_BASE=https://api.sprucehealth...   SPRUCE_LINK=
TTS_URL=https://your-twiml-endpoint   # returns <Say fr-CA> or <Play> AI audio
```

Costs are in Lesson 9 above. **Hand this whole file to Claude Code** to wire
your real Spruce endpoints, your AI-voice TwiML, and your clinic details.

## Lesson 2b — Brief message, English version, and why it works

**Why this matters more than anything (real result):** Google reviews are a
repository of the angry few who try to attack or destroy a doctor's
reputation — the satisfied majority stay silent. Doing this **systematically**
gives a far less opinionated, more representative picture: lots of people
thank you, but **if you don't capture it, nobody knows.** This exact system
took my clinic from about **2/5 stars** to a true reflection of the care
given. See the proof — the verbatim, anonymized thank-yous at
**instanthpi.ai/thankyou** (mirror: instanthpi.netlify.app/thankyou).

**Brief version of the closing message:**
```
Votre prescription a été transmise à votre pharmacie. Vérifiez auprès d'eux
qu'elle est prête avant de vous y rendre.

Comme vous recevez un traitement et avez des symptômes, gardez un suivi avec
moi ici dans 14 jours. Ne prenez pas de rendez-vous, écrivez-moi simplement ici.

🛻💨 ➕ 🤧🤒😩 ➡️ 📲👨‍⚕️📝💊 ➡️ 😌💪🛣️🌟

Truck Stop Santé à votre service. 🫡🚚

Merci de partager votre expérience avec notre clinique : cela aide d'autres
personnes à comprendre nos services.
Vous pouvez laisser votre avis ici : https://g.page/r/CS7XOfBDzFhoEAI/review
```

**The share ask in English (adapt clinic name + link):**
```
[Your Clinic] at your service. 🫡

Thank you for sharing your experience with our clinic — it helps other people
understand our services.
You can leave your review of this experience here: [your review link]
```

## Lesson 4b — Keep the tailor kosher (HIPAA): which Claude Code, and how to set up AWS

Claude Code is the tailor — but **which** Claude Code matters once patient data
is involved.

- **Non-PHI building** (templates, sites, tools, anything with no patient data):
  the standard Claude Code (Anthropic API) is fine and fastest.
- **PHI-touching work** (debugging against a live chart, drafting from real
  patient data): route Claude through **AWS Bedrock — Claude Sonnet under your
  BAA** (a "claude-phi" setup), so no identifiable data ever touches a
  non-covered endpoint. Rule of thumb: **non-PHI dev → normal Claude Code;
  PHI work → Bedrock/BAA.** Same tailor, compliant thread.

**Say it accurately (this is what keeps it honest, not false advertising):**
Bedrock-under-BAA covers the **AI-processing link**. It does NOT by itself make
you "HIPAA compliant" — compliance is a property of the **whole system** (signed
BAA, HIPAA-eligible services only, encryption at rest/in transit, least-privilege
access, audit logging, minimum-necessary data). Claim **"BAA-covered AI
processing,"** never "this makes you HIPAA compliant."

### What Claude Code CAN and CANNOT do for your AWS setup

**Allowed / good practice:** Claude writes your infrastructure-as-code
(Terraform/CloudFormation), least-privilege IAM policies, and setup scripts; runs
AWS CLI with credentials **you** provisioned; enables Bedrock models; guides you
through the console steps.

**Against AWS practice — do NOT let an AI do these:**
- **Accept the AWS Customer Agreement or sign the BAA** — a human authorized
  representative must; an AI "accepting" it is void.
- **Sign up accounts autonomously** (bypassing identity / payment / MFA
  verification) — against AWS Terms of Service.
- **Generate or hold root or long-lived keys, or "manage logins / turn keys"
  unsupervised** — against AWS security best practice (no root keys; use MFA +
  IAM roles + temporary STS credentials; a human stays accountable).
- **"Approve / disapprove" security decisions on its own** — breaks AWS's
  shared-responsibility model; **you** keep the legal accountability.

**The compliant model:** **you** create the account, accept the BAA (free via
AWS Artifact), enable MFA, and create one least-privilege IAM role. **Claude**
then automates the entire buildout with those scoped credentials + IaC, and
**you approve**. "Claude sets it all up" — but the legal and credential acts stay
human.

### Copy-paste setup prompts for Claude Code

**A — guided AWS + BAA + Bedrock setup:**
> "Walk me through a HIPAA-ready AWS setup for a solo clinic. First list the
> human-only steps in order (create the account, accept the AWS BAA in AWS
> Artifact, enable MFA on root, then stop using root). Then generate Terraform
> for: a least-privilege IAM role for Bedrock + S3, an encrypted S3 bucket
> (SSE-KMS) with access logging, and Bedrock model access for Claude Sonnet.
> Explain each resource. I'll run `terraform apply` myself and paste back
> errors. Never ask for root keys."

**B — PHI-safe routing:**
> "Configure this project so PHI work routes Claude through AWS Bedrock (Sonnet,
> my BAA region) via a scoped IAM role using temporary STS credentials, and
> non-PHI work uses the normal endpoint. Add a check that fails loudly if a PHI
> path would hit a non-BAA endpoint."

**C — keys the right way:**
> "Put my API keys (Twilio, Spruce, SRFax) in a gitignored `.env`, add a
> preflight that validates each key is live before any patient run, never commit
> or print full keys, and show me how to rotate them."

The lesson inside the lesson: an AI can build almost everything for you, but it
cannot **be you** for the legal acts (the BAA, account ownership) or hold your
root credentials. Keep those human; automate the rest.
