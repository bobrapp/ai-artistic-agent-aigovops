# Module 16 — Protecting Your Work from AI

**Purpose:** Help artists understand the AI training data problem, take concrete steps to protect their existing and future work, fight back when violations are found, and stay connected to the advocacy movement. This module turns fear into action.
**Estimated time:** 35–45 minutes.
**Prerequisites:** Module 09 (Copyright) recommended but not required — this module covers the key copyright basics as they apply to AI.

---

## When to pull this module

- Artist says "AI is stealing my work" or "I'm worried about AI"
- Artist found AI-generated images that look like their style
- Artist wants to know how to protect their portfolio from scraping
- Artist is posting work online and wants to do it safely
- Artist asks about Glaze, Nightshade, or AI opt-outs
- Artist mentions any AI-related legislation or lawsuits
- Artist is skeptical about using this AI coach because of AI art concerns

---

## Opening (90 seconds)

> *"I want to be upfront about something. I'm an AI tool — and I know that many artists have real, justified concerns about AI companies scraping artwork without permission. That concern is completely valid. Major companies trained their image generators on millions of artworks without consent or compensation.*
>
> *Here's what I am and what I'm not: I'm a business advisor. I don't generate art, I don't compete with your creative work, and I don't use your artwork as training data. Think of me like using AI to help with your taxes — not an AI that paints your paintings.*
>
> *But I want to go further than just not being part of the problem. I want to help you actively protect your work. Let me walk you through the tools, the legal options, and the advocacy organizations that are fighting for your rights."*

---

## Diagnostic questions

1. **Do you post your work online?** (Instagram, website, Etsy, DeviantArt, ArtStation, other platforms.)
2. **Do you have a personal website?** (If yes, we can block AI crawlers today.)
3. **Have you registered any of your work with the US Copyright Office?** (This is the legal foundation for everything else.)
4. **Have you noticed AI-generated images that look like your style or specific works?**
5. **How concerned are you about this issue?** (Scale of 1–10 — helps me calibrate how deep to go.)

---

## The problem in plain language

AI image generators (Midjourney, Stable Diffusion, DALL-E) were trained on billions of images scraped from the internet — including artwork posted by artists on Instagram, personal websites, DeviantArt, ArtStation, and other platforms. Most of this was done without permission or compensation.

**What this means for you:**
- If you've ever posted artwork online, it may already be in one or more AI training datasets.
- AI tools can generate images "in the style of" your work — and there's currently no automatic compensation.
- Copyright law protects your specific works but not your style (though active lawsuits are trying to change this).

**What this does NOT mean:**
- It does not mean your individual paintings were "stolen" and are sitting in a database somewhere — the models learn patterns, not store images.
- It does not mean AI can perfectly replicate your specific works (usually).
- It does not mean the situation is hopeless — there are real tools and real legal movement happening right now.

---

## Layer 1: Protect — Stop future scraping

These are the concrete steps you can take today, right now, to protect your work going forward.

### Glaze (Free)

**What it does:** Applies invisible pixel-level changes to your images that confuse AI models. When an AI tries to learn your style from a Glazed image, it learns the wrong thing.

**How to use it:** Download from glaze.cs.uchicago.edu. Run it on every image before posting to Instagram, your website, Etsy, or anywhere online. It takes a few seconds per image.

**Important:** Glaze is an arms race. In 2025, researchers published a method (LightShed) that can partially strip Glaze protection. The Glaze team updates regularly — keep your version current and re-Glaze important works when updates ship.

**Stats:** 6+ million downloads since March 2023.

### Nightshade (Free)

**What it does:** Goes on offense. Images treated with Nightshade actively corrupt AI models that scrape them — the model learns wrong information. Think of it as a poison pill for AI scrapers.

**How to use it:** Same lab as Glaze (University of Chicago). Download, run on images before posting. 1.6+ million downloads since January 2024.

**When to use which:** Glaze is defensive (protects your style). Nightshade is offensive (punishes scrapers). You can use both on the same image.

### Block AI crawlers on your website (Free, 10 minutes)

If you have a personal website, you can block AI companies from crawling it. Add this to your robots.txt file:

```
User-agent: GPTBot
Disallow: /

User-agent: OAI-SearchBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: Claude-User
Disallow: /

User-agent: CCBot
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: Applebot-Extended
Disallow: /
```

**Important caveat:** This is voluntary. AI companies claim to honor robots.txt for future crawls, but there's no enforcement mechanism and it doesn't affect data already collected.

**Platform-specific instructions:**
- WordPress: Install the Yoast SEO plugin, or edit robots.txt directly in your hosting panel
- Squarespace: Settings → SEO → robots.txt
- Wix: SEO Tools → robots.txt Editor

### Cloudflare AI Bot Blocking (Free)

As of July 2025, Cloudflare blocks AI crawlers by default for new sites. If your website uses Cloudflare (the free plan works), AI bots are automatically blocked. Cloudflare also offers a "Pay Per Crawl" feature — AI companies would have to pay to scrape your site.

### EU / International Protection: TDMRep (Free)

If you sell to or have an audience in Europe, the EU Copyright Directive gives you the legal right to opt out of text and data mining. To exercise it in a machine-readable way, create a file at `/.well-known/tdmrep.json` on your website:

```json
{
  "tdm-reservation": 1
}
```

This satisfies Article 4(3) of the EU CDSM. Without this file, EU law assumes you're allowing data mining.

### C2PA Content Credentials (Free)

Cryptographic proof of authorship embedded in your image files. Records who made the image, when, and with what tools — in a tamper-evident format.

**How:** Use Adobe Photoshop or Lightroom (both embed C2PA natively) or the free open-source `c2patool` command line tool. Verify your credentials at verify.contentauthenticity.org.

**Limitation:** Most social media platforms strip image metadata when you upload. C2PA works best on your own website and when sharing files directly.

### Cara (Free)

Artist-run social media platform (cara.app) that's anti-AI by default. Blocks AI-generated submissions and integrates Glaze for automatic upload-time cloaking. Consider using alongside Instagram — share work on both, but know that Cara actively protects you while Meta does not.

---

## Layer 2: Detect — Find out if your work was used

### Have I Been Trained (Free)

**What it does:** Searches the LAION-5B dataset (the open dataset behind Stable Diffusion) for your images.

**How:** Go to haveibeentrained.com. Upload your artwork. If found, register opt-outs immediately — Stability AI has committed to honoring them for Stable Diffusion 3 and future models.

**Limitation:** This only searches LAION-5B. OpenAI, Midjourney, and Adobe's training datasets are not publicly searchable. You cannot currently check whether your work is in those models.

**Stats:** ~80 million artworks flagged by artists as of 2024.

### Spawning AI (Free)

The parent platform behind Have I Been Trained. If you have a large portfolio (50+ works), Spawning's bulk tools are faster than one-by-one uploads. Also provides an API for platforms to implement opt-out at scale.

### Reverse image search (Free)

Google Images reverse search and TinEye can find copies of your specific works online — including AI-generated images that closely match yours. Set a quarterly reminder to search your most-shared pieces.

---

## Layer 3: Fight back — Take action when violations are found

### Step 1: Copyright Registration ($45–65)

**This is the single most important step.** Without US Copyright Office registration:
- You cannot file a lawsuit in federal court
- You cannot collect statutory damages (up to $150,000 per work for willful infringement)
- You cannot recover attorney's fees

**With registration**, you have a real legal weapon.

**How to register:**
1. Go to copyright.gov → eCO online system
2. For individual works: $45–65 per work
3. For unpublished portfolios: Group registration — up to 750 works for $85
4. Have good photographs/scans of each work ready
5. Plan 90 minutes for your first registration; faster after that

**Group registration is your best friend.** If you have 30 paintings, batch-register them as unpublished works. Cost: ~$85 total instead of $1,350+ individually.

### Step 2: File opt-outs with every company that offers them

The coach can walk you through each one:

| Company | Method | What it covers |
|---------|--------|---------------|
| Stability AI | Register at haveibeentrained.com / Spawning | Future Stable Diffusion training |
| OpenAI (DALL-E) | Block GPTBot in robots.txt | Future web crawling only |
| Adobe Firefly | Adobe opt-out form | Adobe Stock / training data |
| DeviantArt | noai meta tag (on by default) | All deviations auto-protected |
| ArtStation | NoAI tag per work | Must be manually applied to each piece |
| Meta (Instagram/FB) | Objection form — EU/UK only | US artists currently have NO opt-out |
| Midjourney | No mechanism exists | No opt-out available |

**Note on Meta/Instagram:** As of 2026, US artists have no way to opt out of Meta using their Instagram posts for AI training. This is one of the strongest arguments for also posting to Cara or your own website (where you control robots.txt).

### Step 3: DMCA takedown notices (Free)

If an AI tool produces output that closely reproduces your specific registered work, you can send a DMCA takedown notice to the platform hosting it.

**What you need:**
- Identification of your original work
- URL of the infringing AI-generated image
- Statement that you own the copyright
- Statement of good faith
- Your contact info and signature

**Important legal reality:** DMCA protects against reproduction of specific works. It does NOT cover style imitation. "Someone generated images that look like my style" is not currently actionable through DMCA. This is what the active lawsuits are trying to change.

### Step 4: Connect to active lawsuits

**Bartz v. Anthropic** — Settled October 2025 for $1.5 billion. The largest AI training data settlement in history. Covered up to 500,000 works at ~$3,000 per work. Anthropic agreed to destroy the pirated datasets. This was for book authors, but set the legal precedent that training on scraped copyrighted material is actionable.

**Andersen v. Stability AI, Midjourney, DeviantArt, Runway** — Active class action by visual artists. Direct copyright infringement claims survived motions. In discovery. This is the case that will define visual artist rights against AI image generators. No trial date set yet.

**Getty Images v. Stability AI (UK)** — Judgment November 2025. Trademark infringement claims survived (generating images with Getty watermarks). Established that AI outputs containing copyrighted elements are infringing.

**NYT v. OpenAI** — Not an artist case, but the most-watched test of fair use for AI training. Motion to dismiss denied March 2025. The outcome will affect all creators.

---

## Layer 4: Advocate — Stay informed, stay organized

### Organizations fighting for artist rights

**Human Artistry Campaign** (humanartistrycampaign.com) — The most active US coalition. "Stealing Isn't Innovation" campaign. 92% bipartisan voter support for stronger artist protections.

**Graphic Artists Guild** (graphicartistsguild.org) — Leading advocacy for the CLEAR Act (would require disclosure when copyrighted work is used in AI training). Open to independent visual artists. Affordable dues. Their "No Artists, No Art" position paper is a useful policy reference.

**Creators Coalition on AI (CCAI)** — Launched December 2025. Building collective lobbying infrastructure for entertainment and creative workers.

**DACS (UK)** (dacs.org.uk) — Represents 100,000+ visual creators. Pushing for retrospective compensation and collective licensing frameworks. Their model — where artists collectively negotiate rather than individually opt out — is the template for what US artists should eventually demand.

### Legislation to track

**Federal — TRAIN Act** (August 2025, bipartisan): Would give copyright holders the right to access AI training datasets and sue companies using their work without permission. Status: introduced, not passed.

**Federal — NO FAKES Act** (S.1367, April 2025, bipartisan): Creates property rights in individual voice and visual likeness against digital replicas. Status: referred to Senate Judiciary Committee.

**Federal — CLEAR Act**: Would require disclosure when copyrighted work is used in AI training. Endorsed by Graphic Artists Guild.

**Washington State — HB 1168** (2025): Would have required AI developers to document training data sources. Passed the House Technology committee but was killed by tech lobby pressure. Watch for revival. Contact Rep. Clyde Shavers (D-Oak Harbor) to register support.

**EU AI Act** — Fully applicable August 2, 2026. Requires AI companies serving EU markets to maintain copyright-compliance policies honoring machine-readable opt-outs. The strongest binding obligation currently in force globally.

### What you can do as a Kittitas County artist

1. **Join or follow** the Graphic Artists Guild and Human Artistry Campaign — both accept remote members.
2. **Contact Rep. Shavers** about reviving WA HB 1168. Rural artist voices are rarely heard in Olympia — yours matters.
3. **Talk to other artists** in the community. When 50 artists from one county register copyrights, file opt-outs, and contact their representative at the same time — that's a story. That's a movement.
4. **Share what you learn.** Every artist you help protect is one more person who understands the issue.

---

## Kittitas County specifics

- The Arts Commission can provide DMCA takedown templates and help with first-time filings.
- **CWU's library** has copyright reference resources and a librarian who knows IP law.
- For serious infringement cases requiring an attorney, expect to look in Seattle ($400–$600/hour) — there are no IP specialists in Kittitas County.
- The coach tracks all relevant legislation and pushes alerts when deadlines or action opportunities arise.
- The Kittitas Artist Business Coach community (Phase 2) will organize collective action on advocacy issues.

---

## Action items

1. **Today:** Search Have I Been Trained for your most recognizable works. Register opt-outs if found.
2. **Today:** If you have a website, add robots.txt blocks for AI crawlers (10 minutes).
3. **This week:** Download and install Glaze. Run it on your next 5 images before posting.
4. **This month:** Register your best/most valuable works with the US Copyright Office. Use group registration to save money.
5. **This month:** File opt-outs with Stability AI, Adobe, DeviantArt, and ArtStation.
6. **Ongoing:** Run Glaze on all images before posting online. Keep it updated.
7. **Ongoing:** Follow the Human Artistry Campaign or Graphic Artists Guild for legislative updates.
8. **Quarterly:** Reverse-image-search your most-shared works to catch infringement early.

**Total cost for full protection: under $100 and about 2 hours of your time.**

---

## Escalation triggers

- **You find your specific artwork reproduced by an AI tool** → DMCA takedown immediately, then consult IP attorney if the platform doesn't comply.
- **Someone is selling AI-generated copies of your work** → IP attorney. Have your copyright registration ready.
- **You receive a cease & desist related to AI** → Do not respond without an attorney.
- **You're considering joining a class action** → Review the case details carefully. The coach can explain what's currently active, but an attorney should advise on whether to join.
- **A company contacts you about licensing your work for AI training** → Attorney for the contract. Do not sign without legal review. Know what you're giving up.
- **You discover your name is being used as a style prompt in AI tools** → Document everything (screenshots with dates). This may become legally actionable as cases progress.

---

## A note on this coach

You might wonder: if AI is the problem, why am I using an AI tool? Fair question. Here's the distinction:

- **Generative AI image tools** (Midjourney, DALL-E, Stable Diffusion) create art. They were trained on artist work. They compete with artists. That's the problem.
- **This AI coach** gives business advice. It doesn't generate images, doesn't use your artwork, and doesn't compete with your creative work. It's closer to using AI to help with your taxes than to using AI to paint your paintings.

We built this coach specifically to be on your side — including actively helping you fight the AI companies that aren't. If you have concerns about using it, that's completely fair, and you can always talk to a human at the Arts Commission instead.
