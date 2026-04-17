# ameen-intake-form

Client-facing marketing strategy intake form for Ameen Shkur. Built with pure HTML, CSS, and vanilla JS — no frameworks, no build tools.

---

## Deploying to GitHub Pages

1. Go to **Settings → Pages** in this repo
2. Under **Source**, select **Deploy from a branch**
3. Choose `main` branch, `/ (root)` folder
4. Click **Save**

The site will be live at `https://ameenshkur.github.io/ameen-intake-form/` within a minute or two.

---

## Sending links to clients

Always pass the `plan` parameter so submissions are tagged correctly:

| Plan | Link |
|------|------|
| Basic | `https://ameenshkur.github.io/ameen-intake-form/?plan=basic` |
| Standard | `https://ameenshkur.github.io/ameen-intake-form/?plan=standard` |
| Premium | `https://ameenshkur.github.io/ameen-intake-form/?plan=premium` |
| Strategy | `https://ameenshkur.github.io/ameen-intake-form/?plan=strategy` |

The `plan` value appears in every Formspree submission. If no `?plan=` is in the URL, it defaults to `unknown`.

---

## Languages

The form auto-detects the visitor's browser language and defaults to English if no match. The visitor can also switch manually using the flag dropdown (top right). The choice is remembered in `localStorage`.

**Currently supported:**
- `en` — English
- `ar` — Arabic (RTL layout activates automatically)
- `zh` — Simplified Chinese

---

## Adding a new language

1. Create `assets/lang/ku.json` (or whatever code you need), following the same key structure as `en.json`
2. Open `index.html` and find the `LANGS` config object near the top of the `<script>` block:

```js
const LANGS = {
  en: { code: 'en', flag: 'us', short: 'EN' },
  ar: { code: 'ar', flag: 'ae', short: 'AR' },
  zh: { code: 'zh', flag: 'cn', short: '中文' }
  // ku: { code: 'ku', flag: 'iq', short: 'KU' }   ← uncomment this line
};
```

3. Uncomment (or add) the entry for the new language. That's it — the dropdown, RTL switching, and font-family are all driven by this config + the JSON file.

For the flag image, use a 2-letter ISO country code from [flagcdn.com](https://flagcdn.com). Kurdish doesn't have its own flag on flagcdn, so `iq` (Iraq) or a custom image in `assets/flags/` works as a placeholder.

---

## Where submissions land

All submissions go to Formspree: **https://formspree.io/f/mbdqodoj**

Log in at [formspree.io](https://formspree.io) to view, export, or set up email notifications for new submissions.

Each submission includes:
- All 22 questions
- Hidden field: `plan` (from the URL parameter)
- Hidden field: `submission_date` (ISO date, e.g. `2026-04-17`)
- Hidden field: `language` (the language the form was submitted in: `en`, `ar`, or `zh`)
