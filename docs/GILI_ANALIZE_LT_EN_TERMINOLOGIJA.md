# Gili kodo bazės analizė – LT/EN, terminologija, UI/UX, klaidos

**Data:** 2026-03-09  
**Tikslas:** Neatitikimų, klaidų, terminologijos (LT: DI, EN: AI), UI/UX ir kalbos/stiliaus patikra.

---

## 1. Terminologijos taisyklė (AI vs DI)

| Kalba | Naudoti | Nenaudoti | Priežastis |
|-------|---------|-----------|------------|
| **LT** | **DI** (dirbtinis intelektas) | AI | Lietuviškas terminas; „AI“ – anglų kalbos santrumpa |
| **EN** | **AI** (Artificial Intelligence) | DI | Tarptautinė anglų santrumpa; „DI“ – lietuviška |

**Rezultatas:** LT versijoje visur naudojamas **DI**, EN versijoje – **AI** (pavadinimuose, CTA, instrukcijose, community tekste, aria-label).

---

## 2. Atlikti pataisymai (2026-03-09)

### 2.1 LT: AI → DI

| Vieta | Buvo | Pataisyta |
|-------|------|-----------|
| `index.html` – badge `aria-label` | „Mini rinkodaros **AI** sistema, Lead generator versija“ | „Mini rinkodaros **DI** sistema, Lead generator versija“ |
| `scripts/build-locale-pages.js` | EN replacement ieškojo „Mini rinkodaros AI sistema“ | Dabar ieško „Mini rinkodaros DI sistema“ (kad EN pakeitimas veiktų po LT pataisos) |

Kitos LT vietos jau buvo teisingos: pavadinimas „Turinio DI sistema“, instrukcijos „DI (dirbtinio intelekto) įrankį“, CTA „į DI įrankį“, community „promptus ir DI“.

### 2.2 EN: DI → AI

| Vieta | Buvo | Pataisyta |
|-------|------|-----------|
| `scripts/build-locale-pages.js` – EN title | „Content **DI** System – for Marketing Leads“ | „Content **AI** System – for Marketing Leads“ |
| `scripts/build-locale-pages.js` – EN h1 | „Content **DI** System&lt;br&gt;for Marketing Leads“ | „Content **AI** System&lt;br&gt;for Marketing Leads“ |
| `index.html` – inline JS `applyStaticLocaleText()` | `h1.innerHTML = 'Content DI System<br>...'` | `h1.innerHTML = 'Content AI System<br>...'` |

EN badge jau buvo teisingas: „Mini marketing **AI** system“. Instrukcijos, CTA ir community EN tekste – „AI tool“, „prompts and **AI**“.

### 2.3 Rašyba: Linkedin → LinkedIn

| Vieta | Buvo | Pataisyta |
|-------|------|-----------|
| `index.html` – prompt 3 pavadinimas ir nuoroda | „**Linkedin** Autoriteto Kūrimas“ | „**LinkedIn** Autoriteto Kūrimas“ |
| `scripts/build-locale-pages.js` – EN replacement | Ieškomas „Linkedin“ | Ieškomas „LinkedIn“ |

EN versijoje visada buvo „LinkedIn authority building“ – tik LT turėjo klaidingą „Linkedin“.

---

## 3. Patikrintos vietos – be pakeitimų

- **README.md** – LT, naudoja DI; atitinka taisyklę.
- **Instrukcijos (LT):** „Įklijuok į ChatGPT, Claude ar kitą DI (dirbtinio intelekto) įrankį“ – teisingai.
- **Instrukcijos (EN):** „Paste into ChatGPT, Claude or another AI tool“ – teisingai.
- **Prompt 4 CTA (LT):** „Nukopijuok, įklijuok į DI įrankį…“ – teisingai.
- **Prompt 4 CTA (EN):** „Copy, paste into AI tool…“ – teisingai.
- **Community (LT):** „…apie promptus ir DI“ – teisingai.
- **Community (EN):** „…about prompts and AI“ – teisingai.
- **Kalbos perjungiklis:** LT mygtukas – „Perjungti į lietuvių kalbą“, EN – „Switch to English“; root puslapyje EN mygtukas „Switch to English“ – priimtina (dažna praktika rodyti tikslą kalbos mygtuke).

---

## 4. UI/UX ir lokalizacija

- **Struktūra:** DOM (id, class, data-*) identiškas LT ir EN – atitinka [LT_EN_UI_UX_REPORT.md](../LT_EN_UI_UX_REPORT.md).
- **Build:** `npm run build` generuoja `lt/index.html` ir `en/index.html` iš root `index.html`; EN tekstai keičiami per `EN_REPLACEMENTS`.
- **Runtime:** `applyStaticLocaleText()` atnaujina dinaminį turinį, kai `locale === 'en'` (root su `?lang=en` arba `/en/`).
- **A11y:** aria-label visur lokalizuoti (skip link, mygtukai, progresas, info-box, toast).

---

## 5. Kitos pastabos (be kritinių klaidų)

### 5.1 Gramatika / stilius (iš docs)

- **TURINIO_AUDITAS_DETALUS.md** mini: „neutralizuoja klientų **abejonės**“ – siūloma „abejonėms“ (datyvas). Dabartiniame `index.html` / `lt/index.html` prompt 6 aprašyme yra „sukurk turinį, kuris juos **neutralizuoja**“ – gramatiškai teisinga; jei kur nors liko „abejonės“, verta pataisyti į „abejonėms“.

### 5.2 EN rašyba

- „neutralises“ (britiškas variantas) – naudojama EN tekste; jei tikslinė rinka US English, galima „neutralizes“. Projektas naudoja en-GB (pvz. `toLocaleString('en-GB')` kituose projektuose) – palikta „neutralises“.

### 5.3 Canonical / hreflang

- `en/index.html` ir `lt/index.html` turi `canonical` ir `hreflang` su santykiniais keliais (`en/`, `lt/`). GitHub Pages su `BASE_PATH` – build skriptas įterpia base; be BASE_PATH canonical yra santykinis. SEO poveikis priklauso nuo to, kaip hostas nustato bazinį URL.

---

## 6. Santrauka

| Kategorija | Rezultatas |
|------------|-------------|
| **Terminologija LT (DI)** | Pataisyta: badge aria-label „AI“ → „DI“ |
| **Terminologija EN (AI)** | Pataisyta: title ir h1 „Content DI System“ → „Content AI System“; inline JS atnaujintas |
| **Rašyba** | Pataisyta: „Linkedin“ → „LinkedIn“ LT |
| **UI/UX / a11y** | Atitinka LT_EN_UI_UX_REPORT; DOM ir aria-label sutampa |
| **Build** | `npm run build` paleistas po pakeitimų – `lt/` ir `en/` sugeneruoti iš naujo |

**Rekomendacija:** Tolimesniam turiniui laikytis taisyklės: **LT = DI**, **EN = AI** (pavadinimuose, CTA, instrukcijose, aria-label ir community tekste).
