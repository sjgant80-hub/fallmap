# FallMap

**Paste your workflow. See what a £20k consultant would build you, what it actually costs, and the sovereign version that does the same job for £0.**

One HTML file. Opens in any browser. No login. No subscription. No middleman.

**Live:** https://sjgant80-hub.github.io/fallmap/

---

## The premise

> *"We need to digitally transform your workflow."*
> *"Our discovery process is bespoke."*
> *"You'll need HubSpot + Zapier + Mailchimp + PandaDoc + Xero..."*
> *"That's £20,000 to map it · then £2,000/month retainer."*

Arrows shouldn't cost £20,000.

FallMap exposes the grift. You describe your workflow in plain English. It maps it. Shows you what a consultant would plug in. Shows you what it actually costs. Then shows you the sovereign alternative — same workflow, single HTML files, £0/month.

---

## How it works

1. **Paste your workflow** in plain English (or pick a preset)
2. **FallMap parses** it into discrete steps using built-in trade/business verbs
3. **The consultant column** maps each step to the SaaS a consultant would pick — with real UK pricing and the failure mode for each tool
4. **The sovereign column** maps the same steps to existing Fall* tools (FallForce, FallAccount Trades, FallGravity, etc.) — £0/month, on-device, your data
5. **The bill** shows year 1 vs year 2+ for both routes
6. **The savings** is the difference — usually £40,000-£100,000 in year 1 alone

---

## What's inside

### α workflow parser
- 16 step types (intake · qualify · schedule · quote · follow · close · onboard · deliver · invoice · pay_chase · support · marketing · inventory · logistics · feedback · renew)
- Verb-based classification from your plain English
- T3 LLM upgrade if you have any API key (Anthropic / OpenAI / Gemini / OpenRouter)

### β SaaS database (built-in)
30+ tools with real UK pricing. Each includes the **failure point** consultants don't mention:

| Category | Examples | Real cost |
|----------|----------|-----------|
| CRM | HubSpot, Salesforce, Pipedrive | £15-£800/mo |
| Email | Mailchimp, SendGrid, ConvertKit | £13-£350/mo |
| Quotes | PandaDoc, Proposify, DocuSign | £25-£65/mo |
| Accounting | Xero, QuickBooks, FreeAgent | £15-£36/mo |
| Automation | Zapier, Make, n8n | £9-£100/mo |
| Forms | Typeform, JotForm | £25-£99/mo |
| ... | ... | ... |

### γ cost calculator
- One-off (discovery + mapping + implementation + training)
- SaaS monthly × 12
- Retainer monthly × 12
- Year 1 total · Year 2+ ongoing
- 4 rate tiers: indie (£10k) · mid (£20k) · high (£34k) · luxury (£65k+)

### δ sovereign mapper
Each step routes to the **right Fall* tool** with the URL and the "why":

| Step type | Sovereign tool |
|-----------|---------------|
| intake / qualify / schedule | FallForce |
| invoice / pay_chase / logistics | FallAccount Trades |
| marketing | FallGravity |
| inventory / custom | Forge output |
| support / feedback / close | FallForce |

### Export & share
- **Download report** — plain text comparison ready to email
- **Share summary** — LinkedIn-ready post copied to clipboard with savings number

---

## Example output (mid-tier consultant)

```
Your workflow: 9 steps · consultancy sales funnel

CONSULTANT ROUTE (year 1):
  Discovery workshop:     £3,000
  Workflow mapping:       £4,000
  Implementation:        £10,000
  Training:               £3,000
  Consultant one-off:    £20,000

  HubSpot CRM Starter:   £540/yr
  HubSpot Pro:         £1,080/yr
  PandaDoc:              £420/yr
  Mailchimp Essentials:  £156/yr
  Xero Standard:         £432/yr
  Chaser:                £900/yr
  SaaS year 1:         £3,528

  Retainer £2k/mo:    £24,000/yr

  YEAR 1 TOTAL:        £47,528
  YEAR 2+:             £27,528/yr ongoing

SOVEREIGN ROUTE:
  2 tools: FallForce + FallAccount Trades
  Both already exist · MIT licenced · single HTML files
  Brand & config (optional, one-time): £997-£5,000
  Monthly: £0

  YEAR 1 MAX:          £5,000
  YEAR 2+:             £0

  ╔══════════════════════════════════════╗
  ║  YOU SAVE £42,528 IN YEAR ONE        ║
  ║  THEN £27,528/YEAR ONGOING           ║
  ╚══════════════════════════════════════╝
```

---

## Sovereignty

- All data on your device (localStorage)
- Saved workflows · settings · preferences — never leave your phone
- Export JSON anytime
- No telemetry · no signup · no subscription
- Works fully offline (T0 templates always available)
- Optional AI keys sharpen the parser — but T0 already handles 95% of common workflows

---

## How it's built

### Architecture
- **Single HTML file** — ~75 KB, no build step, no deps
- **Vanilla JS** · no framework
- **localStorage** for persistence
- **BroadcastChannel** `fall-signal` for mesh interop (prime 241)
- **Konomi licence shim** baked in (sovereign tier)
- **Cascade** — T0 templates → T3 (Claude / GPT / Gemini / OpenRouter) → T2 Ollama local

### 7-layer breakdown (v19)

| Ring | Role | Implementation |
|------|------|----------------|
| L1 FACE | Input → comparison → bill → CTA | scrolling single-page flow |
| L2 SWARM | Ω + 5 agents | α parser · β SaaS · γ cost · δ sovereign · ε render |
| L3 CASCADE | T0 always | regex parser + SaaS DB + sovereign DB · T3 enhances parsing |
| L4 BLOOM | routing | step type → SaaS pick → sovereign pick |
| L5 PERSIST | localStorage | saved maps · settings · custom pricing |
| L6 SKIN | dark + amber `#e8a012` | red consultant col · green sovereign col · big savings card |
| L7 ASS | empty state | 5 preset workflow chips · "Map it" CTA |

### Fork & rebrand

```bash
gh repo fork sjgant80-hub/fallmap --clone=true
cd fallmap
# Update SAAS_DB or CONSULTANT_RATES with your local pricing
# Update SOVEREIGN_DB to point at your own Fall* tool URLs
gh repo edit --enable-pages --pages-branch main
```

---

## postMessage API

Other Fall* tools can call FallMap programmatically:

```js
window.postMessage({
  target: 'fallmap',
  action: 'map',
  workflow: 'we get leads, qualify, quote, close, invoice, chase',
  rate: 'mid'
}, '*');
// → { steps, consultant: {...costs}, savings: 42528 }
```

---

## Roadmap

- ✅ 16 step types with verb classification
- ✅ SaaS database with real UK pricing + failure modes
- ✅ Sovereign mapping to existing Fall* tools
- ✅ 4-tier consultant rate calculator
- ✅ Side-by-side comparison + bill + savings card
- ✅ Export report · LinkedIn share copy
- ✅ T3 LLM parser enhancement (4 providers)
- ⬜ Custom SaaS pricing override (user can add their local rates)
- ⬜ Vertical-specific presets (law · medical · construction · agencies)
- ⬜ Animated bill counter on render
- ⬜ Sovereign install wizard (one click to fork all needed tools)

---

## Licence

MIT — see [LICENSE](LICENSE). Use it, fork it, customise SAAS_DB and SOVEREIGN_DB for your market.

---

## Credit

- **Architecture & build:** Simon Gant · [@sjgant80-hub](https://github.com/sjgant80-hub) · [LinkedIn](https://www.linkedin.com/in/simon-gant-295b56180/)

◊·κ=1 · paste your workflow · see the grift · six subscriptions vs one HTML file · the consulting bill vs the sovereign version · arrows shouldn't cost £20,000
