---
name: technical-proposal
description: Create branded client technical proposals from a company logo, client name, and project scope, delivered as polished PDF or animated HTML. Supports Arabic and English proposals and statements of work.
---

# Technical Proposal

Turn a brief into a credible client offer with an editorial layout and reviewable implementation scope. Deliver actual files.

## Intake and content

Reuse supplied attachments and context. Collect the company logo, client name, and scope together if missing. Ask for logo attachments in ordinary chat. Clarify whether the logo belongs to the proposer or client if ambiguous. Optional inputs: proposer name, title, language, format, brand guide, design reference, confirmed timeline, budget, terms, contacts. Match the brief language. Default to animated HTML plus a matching PDF when export is available. Optional fields must not block progress: omit them or explicitly flag unresolved commitments. If asked to proceed without a logo, use a company wordmark and disclose draft branding.

Preserve every requirement and ID. Map scope items to deliverables and observable acceptance criteria. Distinguish confirmed scope, proposed implementation and assumptions; never silently reduce scope to an MVP. Ask only when ambiguity changes the offer materially.

Lead with the client's problem and intended outcome. Follow with solution, scope/deliverables, approach, phases, acceptance, dependencies, exclusions and next steps. Include security, integrations, handover and support when relevant. Write useful project-specific text, not filler. Keep all proposal text in the chosen language except familiar technical terms; handle Arabic RTL deliberately.

Never invent prices, delivery dates, credentials, case studies, certifications, guarantees, signatures or compliance claims. Suggested durations must be labeled estimates with dependencies. Include commercials only when provided/requested. Keep internal costs and margin out of client files.

## Soft Key identity and pricing

Default proposer is SOFT KEY. Use a plain SOFT KEY text wordmark. The user explicitly removed the image logo; do not reinsert it unless requested. Brand palette: background #06070a, surface #101117, blue #569bff, purple #b47ef2, pink #f049bf. HTML uses the dark identity; PDF uses a light print treatment with the same brand accents and text wordmark. A different explicit client brief can override these defaults. Client logos stay separate from the proposer identity.

Pricing is project-specific: ask for each line item's scope, quantity, unit price, currency, optional extras, recurring costs, discount, tax treatment and payment milestones together. Do not reuse service-catalogue prices automatically. A proposal needs a dedicated pricing section. If pricing is not supplied, show descriptive rows with null prices and clearly pending totals; never invent example amounts in a client offer. Missing tax treatment is unknown, not zero tax. Distinguish one-time totals from recurring charges and exclude optional extras from the base total. Show recurring billing periods, third-party cost ownership, and supplied payment/validity terms. Preserve supplied commercial detail. Validate all arithmetic, including milestone amounts, before delivery; do not invent a percentage split.

## Visual system

Inspect any explicitly supplied logo and design reference; the default Soft Key proposal uses text branding only. Preserve logo proportions, colors and clear space; do not redraw it. Use brand colors as restrained accents with readable contrast and suitable backing for the logo. Use the Soft Key defaults above, a spacious editorial cover, numbered sections and calm scope rows. Avoid generic dashboards, excessive cards, invented metrics and decorative architecture. Adapt to the supplied reference rather than forcing the starter layout.

Read [rendering.md](references/rendering.md) for the JSON contract. The bundled renderer is a starting layout. Complex tables, architecture diagrams or exact references may warrant adapting it in the task workspace. Allow long content to flow; do not shrink text to an arbitrary page count.

HTML must work locally without network dependencies, with responsive layout, keyboard access, visible content if JavaScript fails, discreet motion and reduced-motion support. No trackers, forms or submission behavior. Publishing/sending requires user authorization.

PDF must be a separate static, selectable A4 export with intentional page breaks, footer page numbers and no controls. Use the available PDF skill for authoring and verification. A print button alone is not a delivered PDF.

## Build and verify

1. Write structured content using the reference contract; keep original inputs separate. Run `node scripts/render.cjs brief.json proposal.html [proposal.pdf]`. HTML needs only Node; PDF also needs Playwright and Chromium. Discover available runtimes rather than assuming paths. If PDF export is unavailable, deliver HTML and state the limitation.
2. Inspect desktop/mobile HTML and every rendered PDF page. Verify scope coverage, logo, missing assets, clipping, contrast, pagination, Arabic shaping/bidi, links and reduced motion. Test RTL and long content when changing the renderer. Script success alone does not prove visual quality.
3. Deliver requested files and flag material unresolved commitments. Never claim user acceptance or unperformed PDF verification.

## Languages and explanatory visuals

Support any requested language; do not limit proposals to Arabic/English. Ask which languages only if context does not establish them. Default to the conversation language. For multiple languages produce separate, consistently named HTML/PDF editions with matching scope, prices, currency and version. Translate all body text, labels, pricing, chart legends, diagram nodes, timeline units and metadata. Preserve requirement IDs and amounts exactly. Arabic, Persian, Urdu and Hebrew need RTL; other language scripts require suitable installed fonts and visual verification. Do not claim a translation is verified merely because the renderer accepts its language code.

Include a timeline view with phase outputs, dependencies and review gates. Without agreed durations/dates use an ordered phase timeline and explicitly say dates await agreement; do not invent a schedule. With confirmed durations use the proportional Gantt treatment in the visual contract.

Use diagrams when they clarify the proposed solution, system boundaries, integrations or delivery workflow. Clearly distinguish proposed from existing architecture. The bundled diagram renders labeled component nodes and explicit directional relationships; complex graphs may use locally rendered SVG. Keep all visuals embedded and printable, with meaningful labels rather than screenshots of text.

Use charts only for relevant supplied or transparently derived data, such as agreed cost allocation, delivery effort estimates labeled as estimates, or scope coverage. Never invent performance improvements, ROI, market numbers or completion percentages for decoration. If cost data is pending, omit the cost chart until known. Provide the values in accessible text and preserve readable static visuals in PDF. See `references/visuals.md` for rendering and translation contracts.
