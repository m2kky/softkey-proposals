# Multilingual and visual contract

Use any BCP-47 `lang` code. Arabic/English chrome is built in. For other languages provide all `labels`: `proposal`, `preparedFor`, `preparedBy`, `print`, `contents`, `pricing`. When pricing is present translate every `pricing.labels` key: `title`, `item`, `qty`, `unit`, `total`, `pending`, `once`, `recurring`, `optional`, `sub`, `discount`, `tax`, `net`, `payment`, `note`, `commercial`. The agent translates content; the renderer does not translate automatically. Set `dir` when necessary. Use one brief/output pair per language so every edition is self-contained. Never change currency when translating. Verify target-script fonts.

Add optional visual objects to any section:

```json
{
  "title": "Delivery approach",
  "chart": {
    "title": "Agreed cost allocation (EGP)",
    "data": [{"label": "Design", "value": 1000}, {"label": "Development", "value": 2000}],
    "note": "Example syntax only; replace with actual agreed amounts."
  },
  "diagram": {
    "title": "Proposed workflow",
    "nodes": [{"id": "a", "label": "Client"}, {"id": "b", "label": "Booking service"}],
    "edges": [{"from": "a", "to": "b", "label": "Creates a booking"}],
    "note": "Proposed architecture, subject to scope approval."
  },
  "timeline": {
    "title": "Delivery phases",
    "phases": [{"title": "Discovery", "description": "Approved requirements", "when": "Phase 1"}],
    "note": "Dates await agreement."
  }
}
```

The diagram presents components and explicit relationships in a responsive layout. Edge direction is from `from` to `to`; IDs are unique and validated. Chart values must be finite nonnegative numbers, with values and unit available as text. Do not use a bar chart for negative values; adapt to an appropriate chart. All labels come from the brief. No CDN or network calls.

For proportional timelines supply numeric nonnegative `start` and positive `duration` on **every** phase, and translated `timeline.unit` (e.g. days). Also include readable `when` or duration text and assumptions. The bars share the same scale. Otherwise an ordered phase view appears without fabricated durations.

For more complex charts/diagrams render locally to SVG and embed with descriptive text. Match Soft Key colors, maintain accessible contrast, and verify static PDF output. Never replace explanatory diagrams with decorative icons.
