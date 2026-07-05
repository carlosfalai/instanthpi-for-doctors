# Setting up your automated clinic — step by step (no computer skills needed)

Read this like a recipe. You do the steps **one at a time**, and you can stop
after any step and continue another day. Nothing here needs coding knowledge.

**Two things to understand first, in plain words:**
- **The "terminal"** is just a plain window on your computer where you type or
  paste text. That's all it is.
- **"Claude Code"** is an AI helper that lives in that window. You **paste it
  instructions, and it does the work for you** — it writes the programs, sets up
  the accounts' technical parts, and connects everything. You don't write code;
  you paste and answer its questions.

Every step below has **two parts**:
- 👤 **What you need to know** — plain talk, for you the doctor.
- 💻 **Paste this into the terminal** — the instruction Claude Code follows. You
  just copy it in and press Enter.

---

## Step 0 — Get the helper (5 minutes, once)

👤 **What you need to know:** You install the AI helper once. If anything looks
confusing, that's normal — you'll paste a line and it handles itself.

💻 **Paste this into the terminal:**
```
npm install -g @anthropic-ai/claude-code
```
Then type `claude` and press Enter. The helper is now listening. (If `npm` isn't
found, paste: *"I'm on Windows/Mac with no dev tools. Give me the exact clicks to
install Node.js and Claude Code, one step at a time."*)

---

## Step 1 — Open your accounts and sign (only YOU can do this) 🖊️

👤 **What you need to know:** This is the one part a machine is **not allowed** to
do for you — because it's *signing your name*. Think of it like opening a bank
account: only you can sign. You'll:
1. Open an **AWS** account at aws.amazon.com (your card + ID, like any signup).
2. **Sign the privacy contract** (called a "BAA"). In AWS, go to the search bar,
   type **"Artifact"**, open it, find **"AWS Business Associate Addendum,"** and
   click **Accept**. That one click is what makes it legal to handle patient data.
3. Turn on the extra security code ("**MFA**") when it offers.
4. Do the same signing for the tools you'll use: **Spruce** (your secure
   messaging), **SRFax** (faxing). Each has a "sign the BAA" button.

💻 **Paste this into the terminal** (Claude walks you through the clicks):
```
I have no IT background. Walk me through, one click at a time with screenshots
described in words: creating an AWS account, finding AWS Artifact, accepting the
AWS BAA, and turning on MFA. Wait for me to say "done" after each click.
```

---

## Step 2 — Let Claude build the secure foundation

👤 **What you need to know:** Now the helper does the technical setup — the secure
storage and the AI engine — all inside the contract you just signed. You mostly
watch and press Enter.

💻 **Paste this into the terminal:**
```
I accepted the AWS BAA and turned on MFA. Set up my HIPAA-ready foundation for me:
a limited-access login (not the master one), encrypted storage for my documents,
and access to the Claude AI engine on AWS. Give me any button-clicks I must do
myself, one at a time, and do everything else. Never ask me for my master keys.
```

---

## Step 3 — Put in your passwords the safe way

👤 **What you need to know:** Your tools (messaging, fax, phone) each have a
"key" (a long password). The helper stores them safely so they're never exposed,
and checks they still work before every clinic day — because keys silently expire,
and a dead key is what makes a whole day quietly fail.

💻 **Paste this into the terminal:**
```
Make me a safe hidden file for my keys (Spruce, fax, phone/Twilio), and a check
that tests each key is alive before any patient run and stops loudly if one is
dead or missing. Never show my full keys or save them anywhere public. Tell me,
in plain words, where to click to get each key.
```

---

## Step 4 — Build your first tool: the patient caller

👤 **What you need to know:** This is the tool that invites patients onto your
secure channel — it texts and emails them, then makes up to **3 spaced AI phone
calls** through the day if they haven't logged in, and if none work, it writes the
note and emails them the whole trail. You run it by pasting today's patient list.

💻 **Paste this into the terminal:**
```
Build the patient invitation tool from BUILD-PROMPTS.json in the
instanthpi-for-doctors repo (the "invitation" one). I'll paste a list of patients
(name, phone, email) and it sends text + email, then up to 3 AI calls spaced
hours apart, and emails a summary if all fail. Use my keys from Step 3. My clinic
name, credentials and signature are: [tell it here].
```

---

## Step 5 — Add the rest, one at a time (only when you want)

👤 **What you need to know:** Each of your other tools has a ready‑made
instruction in **`BUILD-PROMPTS.json`** in this repo — the PDF filler, the
fax‑reader, the AI phone intake, the reasoning "council," the patient carousel,
the free education bot. Do them **little by little**; there's no rush.

💻 **Paste this into the terminal** (swap the name for the tool you want):
```
Open BUILD-PROMPTS.json in the instanthpi-for-doctors repo, use the "pdf-filler"
prompt, and build it for me step by step. Ask me for my clinic details when you
need them.
```

---

## Good habits for working with the AI helper (learned the hard way)

- **You keep the crown jewels:** your accounts, the signed contracts, and the
  master password stay with **you**. The helper builds; it never signs and never
  holds the master key.
- **Nothing goes to a patient without you seeing it and approving it.** The helper
  writes the message; **you** press send.
- **A check runs before every clinic day** to make sure the keys still work —
  this alone prevents the silent "nothing happened all day" failure.
- **Patient data goes only through the signed (AWS/BAA) engine**; anything less
  secure only ever sees de‑identified text.
- **Don't let it rebuild something that already works** — point it at the working
  file and say "fix this in place," not "build a new one."

---

## What you'll see — the terminal tells you what it built

You never have to wonder if it worked. The helper **reports back in plain words**
after every step. Here's what to expect.

**After it builds a tool:**
```
✓ Patient caller built.
✓ Keys checked: Spruce OK · Phone OK · Fax OK.
Ready. Paste today's patients when you want to run it.
```

**After you run the patient caller** (you pasted your list; it shows progress and
a final table):
```
→ Marie Tremblay    text sent ✓   email sent ✓
→ Jean Dupont       text sent ✓   email sent ✓
... 2 hours later, not logged in → calling ...
→ Jean Dupont       call 1 of 3 placed ✓
STATUS:  8 logged in · 2 still being called · 1 emailed after 3 tries
```

**When it creates a document** (say, a prescription), it tells you the file is
ready and opens it for you:
```
✓ Prescription created:  Rx_Tremblay_2026-07-04.pdf   (112 KB) — opened for your review
```

**And the PDF itself looks like a real, signed clinic document** — not a rough
draft. Example of what appears on your screen:
```
──────────────────────────────────────────────
   TRUCK STOP SANTÉ   ·   Dr Carlos Faviel Font
   Médecine familiale · CMQ 16812
──────────────────────────────────────────────
   ORDONNANCE / PRESCRIPTION

   Patient : Marie Tremblay          NAM : TREM 8012 3456
   Date : 4 juillet 2026

   1.  Amoxicilline 500 mg
       1 comprimé, 3 fois par jour, pendant 7 jours

   ─────────────
   Signature :  [ votre signature ]
   Imprimé le 2026-07-04 · Produit par InstantHPI
──────────────────────────────────────────────
```
*(The patient above is fictional — an example only.)*

You read it on screen. If it's right, you sign and send. If something's off, you
just tell the helper in plain words — *"change the dose to 250 mg"* or *"add a
second medication"* — and it **regenerates the PDF instantly**. You are always the
one who decides and signs; the helper only prepares.

---

## Last step — you sign

The helper did the building and wrote the drafts. **You review and sign.** The
work is done by AI; the checking, the license, and the signature are **100%
yours.** Questions any time: cff@centremedicalfont.ca · instanthpi.ai/physicians/
