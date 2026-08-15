# Hair Master Heiloo

Statische website voor Hair Master Heiloo (Nijverheidsweg 25, Heiloo).
Gebouwd om te hosten op Cloudflare Pages.

## Structuur

```
index.html            de complete pagina (HTML + CSS inline, geen build)
assets/decore.svg     decoratieve lijn achter de hero
assets/favicon.svg    favicon
_headers              cache- en securityheaders voor Cloudflare Pages
```

Er is geen build-stap en geen dependency. Lokaal bekijken kan door `index.html`
in de browser te openen, of met bijvoorbeeld `npx serve .`.

## Deployen op Cloudflare Pages

Koppel de repo in het Cloudflare-dashboard onder **Workers & Pages → Create → Pages
→ Connect to Git** en kies:

| Instelling            | Waarde     |
| --------------------- | ---------- |
| Framework preset      | None       |
| Build command         | *(leeg)*   |
| Build output directory| `/`        |
| Production branch     | `main`     |

Daarna deployt elke push naar `main` automatisch.

## Herkomst

De pagina komt uit het Claude Design-project *Hair Master Heiloo*
(`Hair Master Heiloo v2.dc.html`). Dat bronbestand gebruikt de DC-preview-runtime
(`support.js`, React) met `{{ }}`-placeholders, `sc-for`, `sc-if` en `style-hover`.
Voor deze repo is dat gecompileerd naar platte HTML:

- placeholders ingevuld, kleuren als CSS-variabelen (`--accent`, `--amber`, ...)
- `sc-for`-lussen (diensten, USP's, reviews, openingstijden) uitgeschreven
- `sc-if` voor de mobiele sticky CTA is altijd aan
- `style-hover` vertaald naar echte `:hover`-regels met transitions
- de datumafhankelijke teksten (dag markeren, "vandaag geopend", jaartal) draaien
  in een klein script onderaan `index.html`, met dezelfde logica als `renderVals()`

Pas je iets aan in Design, dan moet die vertaling opnieuw gebeuren. Bewerk anders
gewoon `index.html` direct.

## Aandachtspunten

- **Foto's staan nog op `static.wixstatic.com`** (hero, galerij, over-ons). Die
  hotlinks werken zolang de oude Wix-site online staat. Zet ze bij voorkeur in
  `assets/` en pas de `src`-attributen aan.
- **De galerijfoto's zijn voorbeeldfoto's** en herhalen zich; vervang ze door echt
  werk uit de zaak.
- **Reviews zijn illustratief** en staan hard in `index.html`. Vervang ze door echte
  Google-reviews voordat de site live gaat.
- **Canonical en Open Graph** wijzen naar `https://hairmasterheiloo.nl/`. Pas dit aan
  als het domein anders wordt.
- Boekingen lopen via Fresha, telefoon `06 86 48 99 86`.
