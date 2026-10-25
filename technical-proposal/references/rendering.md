# Rendering

`node <skill>/scripts/render.cjs <brief.json> <proposal.html> [proposal.pdf]`

Use Node 18+. For PDF, make `playwright` resolvable through installed dependencies or `NODE_PATH`. `CHROMIUM_EXECUTABLE_PATH` optionally selects an installed Chromium browser. Discover host dependencies. No machine path is hardcoded.

Input is UTF-8 JSON. Required: `client`, `title`, nonempty `sections`. Local logo paths resolve relative to JSON; PNG/JPG/WebP and inspected trusted SVG are supported. Text is escaped; do not supply HTML or Markdown. All assets/CSS/JS are embedded in the HTML. Omit unknown metadata instead of inventing it.

```json
{
  "lang": "en",
  "company": "Studio name",
  "client": "Client name",
  "title": "Project technical proposal",
  "subtitle": "The intended business outcome",
  "logo": "logo.png",
  "accent": "#006b5e",
  "status": "Draft for discussion",
  "date": "25 October 2026",
  "version": "1.0",
  "sections": [
    {"title": "Project understanding", "intro": "Client problem and desired result."},
    {"title": "Scope and deliverables", "items": [
      {"title": "D01 / Deliverable", "body": "Included scope.", "bullets": ["Acceptance: observable condition."]}
    ]},
    {"title": "Assumptions and exclusions", "bullets": ["Client supplies approved content."]},
    {"title": "Next steps", "intro": "Confirm open requirements before committing dates."}
  ]
}
```

`lang: ar` selects RTL and Arabic UI labels. Supplied content must also be Arabic. `dir: rtl` can override direction. An optional `labels` object can override `proposal`, `preparedFor`, `preparedBy`, `print`, `contents`. `pageBreak: true` on a section creates an intentional print break. Long individual deliverables can continue across pages. PDF export waits for fonts/images and disables motion. The renderer validates format, not technical/commercial completeness.

## Project-specific pricing

Supply `pricing` on every proposal. `items` accept `title`, `description`, `quantity`, `unitPrice` (number or null), `kind` (`once`, `recurring`, `optional`), and `period` for recurring items. Currency defaults to EGP, not to a conversion; set the actual agreed currency. No mixed currencies in one pricing object. Prices are exclusive of the separately supplied tax rate. `discount` is an absolute amount in the same currency, not a percentage. Minor-unit rounding is applied before summation; `decimals` defaults to 2 and can be 0–3 for the actual currency. A missing one-time price suppresses a misleading partial grand total. Unknown tax is explicitly labeled, and the displayed known total is before tax. Optional and recurring charges are separate from the one-time total.

```json
"pricing": {
  "currency": "EGP",
  "note": "Pricing awaits project-specific confirmation.",
  "items": [
    {"title": "D01 / UX design", "description": "Agreed screens and review rounds", "quantity": 1, "unitPrice": null, "kind": "once"},
    {"title": "Hosting", "quantity": 1, "unitPrice": null, "kind": "recurring", "period": "Monthly"}
  ],
  "discount": 0,
  "taxRate": null,
  "paymentTerms": ["Payment milestones to be agreed."]
}
```

Soft Key defaults, with a plain text wordmark, apply when company/logo are omitted. No image logo is inserted by default. Source identity: existing local Soft Key services catalogue, 22–25 October 2026. Colors are retained in the renderer and may be overridden by explicit `accent`; future brand updates must inspect canonical assets first.
