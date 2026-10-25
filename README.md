# Soft Key Proposals

Reusable Codex skill for client-facing technical and commercial proposals, with Soft Key colors and a simple text wordmark. No image logo is inserted by default.

## الاستخدام

انسخ مجلد `technical-proposal` إلى مجلد skills الخاص بـCodex، ثم افتح محادثة جديدة واكتب:

> استخدم $technical-proposal لعمل عرض للعميل [الاسم]، بنطاق [التفاصيل]، باللغة [اللغة أو اللغات]، بصيغة PDF وHTML. أسعار المشروع هي [تفاصيل البنود].

- الهوية: خلفية داكنة، أزرق وبنفسجي ووردي، ونسخة PDF فاتحة للطباعة.
- التسعير لكل مشروع على حدة؛ لا يتم سحب أسعار كتالوج الخدمات تلقائيًا.
- تفاصيل البنود والكميات وسعر الوحدة والخصم والضريبة والدفعات، مع فصل التكاليف المتكررة والإضافات الاختيارية.
- Timeline للمراحل، وGantt عند توفير مدد فعلية، وdiagrams للعلاقات، وcharts مبنية على بيانات حقيقية أو افتراضات معلنة.
- اللغات حسب الحاجة؛ نصوص وواجهات عربي/إنجليزي جاهزة، وأي لغة إضافية مع labels مترجمة بالكامل. نسخ مستقلة لكل لغة، بنفس النطاق والأرقام.
- HTML مستقل بلا CDN، متجاوب ويدعم reduced motion؛ PDF نصي قابل للتحديد.

الـskill تصيغ المحتوى وتترجمه. الـrenderer يعرض البيانات المنظمة ولا يترجم تلقائيًا أو يقدّر الأسعار. البيانات غير المكتملة تظهر بوضوح، ولا تُستبدل بصفر أو أرقام مخترعة.

## Run the renderer

Node 18+ is required. HTML needs no dependencies:

```sh
node technical-proposal/scripts/render.cjs examples/brief-ar.json proposal.html
```

For automated PDF output:

```sh
npm install
npx playwright install chromium
npm run demo:ar
npm run demo:en
npm test
```

Use `CHROMIUM_EXECUTABLE_PATH` to select an existing compatible Chromium browser. If Playwright/browser is unavailable, HTML still works and offers browser printing; the PDF is only delivered when actually generated and verified.

See [content and pricing contract](technical-proposal/references/rendering.md) and [languages and visuals](technical-proposal/references/visuals.md).

## Examples and verification

`examples/` includes Arabic/English briefs and rendered HTML/PDF examples. They are clearly marked illustrations; prices and delivery dates await agreement. Charts show counts from the brief, not invented business results.

Verified locally: pricing arithmetic and unknown inputs, visual-data validation, RTL/LTR and translated-label handling, desktop/mobile overflow, embedded assets, navigation, reduced motion and static PDF output. Examples were visually reviewed. Complex architecture, additional scripts/fonts and real client briefs require review for each proposal.

This repository does not publish a website, submit a quote, send messages or collect payments. No real client data or credentials are included.
