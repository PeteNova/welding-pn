# Welding-PN Website

Single-file landing page for Nowakowski TIG Welding. Based on the GD Autocentre template — three theme variants (industrial / editorial / cyber), light/dark, Web3Forms enquiry form, WhatsApp float, fully responsive.

## Files

- `index.html` — entire site (HTML + CSS + JS in one file)
- `welding-pn-logo.jpg` — TODO: add logo (referenced in OG meta, favicon, og:image)

## Deploy

Use `/welding-pn-deploy` from anywhere.

Manual:
```bash
git add -A && git commit -m "Update" && git push
npx vercel --yes --prod
```

## Local preview

```bash
python -m http.server 8000
# open http://localhost:8000
```

## Customize

**Theme variant**: open the floating Tweaks panel (bottom-right gear icon) → pick industrial / editorial / cyber.

**Light/dark**: same Tweaks panel.

**Content edits**: edit `index.html` directly. Search for `TBA` to find every placeholder needing real data.

## Web3Forms

Default form uses a placeholder access key. Sign up at https://web3forms.com (free), copy your access key, find the form `<input name="access_key">` in `index.html`, and replace.

Form submissions go to: `piotrrekas@gmail.com`
