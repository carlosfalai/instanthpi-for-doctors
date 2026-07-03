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
