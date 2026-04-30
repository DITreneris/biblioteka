# Gili kodo bazės analizė – DI Promptų Biblioteka

**Data:** 2026-02-18 (atnaujinta 2026-03-09)  
**Tikslas:** Klaidų, neatitikimų, trūkumų identifikavimas ir testų rinkinio pridėjimas, kad būtų garantuojamas sistemos veikimas.

---

## 1. Santrauka

| Kategorija        | Rasta | Kritiška | Pastabos |
|-------------------|-------|----------|----------|
| Klaidos / bug'ai  | 0     | 0        | Logika atitinka specifikaciją |
| Neatitikimai      | 2     | 0        | Dead CSS (pasirinktinai), inline JS nelintinamas |
| Trūkumai          | 0     | 0        | DEPLOYMENT.md, pa11y privatumas, console – išspręsta; BASE_PATH deploy – išspręsta (2026-03-09) |
| Rekomendacijos    | 4     | –        | Ilgalaikis priežiūra (dead CSS, privatumas atgal, lint) |

---

## 2. Rastos klaidos ir neatitikimai

### 2.1 Console naudojimas production kode — **IŠSPRĘSTA (2026-02-18)**

- **Buvusi problema:** `.cursorrules` ir MUST_TODO reikalavo nebenaudoti `console.error` / `console.warn` production kode.
- **Dabartinė būklė:** `index.html` inline skripte **nėra** `console.log` / `console.warn` / `console.error`. Testai (`tests/structure.test.js`) ir build skriptas (`scripts/build-locale-pages.js`) naudoja `console` tik Node aplinkoje – tai priimtina.

### 2.2 Nenaudojamas (dead) CSS – modal ir forma (likęs, neblokuoja deploy)

- **Vieta:** `index.html` – ~200 eilučių CSS (`.modal-overlay`, `.modal`, `.form-group`, `.form-input`, `.form-submit` ir kt.).
- **Problema:** Kontaktų forma ir modal šiuo metu išjungti (MUST_TODO) – atitinkamos HTML struktūros nėra. Šie stiliai niekada nėra taikomi.
- **Poveikis:** Didesnis failo dydis; neblokuoja release. Palikta kaip paruošimas būsimam etapui (kai bus įjungta forma).
- **Siūlomas sprendimas (pasirinktinai):** Perkelti į `form-modal.css` ir įtraukti tik įjungus formą, arba dokumentuoti ir palikti.

### 2.3 README vs faktinė struktūra — **IŠSPRĘSTA**

- **Buvusi problema:** `DEPLOYMENT.md` neegzistavo.
- **Dabartinė būklė:** `DEPLOYMENT.md` egzistuoja – GitHub Pages deploy instrukcijos, troubleshooting, post-deploy testavimas. README struktūra atitinka faktą.

### 2.4 CI – tik pagrindinis puslapis a11y — **IŠSPRĘSTA**

- **Buvusi problema:** `privatumas.html` nebuvo tikrinamas pa11y.
- **Dabartinė būklė:** `.github/workflows/ci.yml` jau turi antrą pa11y žingsnį: `npx pa11y http://127.0.0.1:3000/privatumas.html --standard WCAG2AA --ignore "warning"`.

### 2.5 JavaScript lint – tik atskiri .js failai

- **Vieta:** `package.json` – `"lint:js": "eslint . --ext .js"`.
- **Problema:** Pagrindinė aplikacijos logika yra `index.html` inline `<script>`. ESLint šio skripto nekontroliuoja.
- **Poveikis:** Inline kodo stilius ir klaidos nelintinami.
- **Siūlomas sprendimas:** Arba (A) ištraukti JS į atskirą `app.js` ir jį lintinti, arba (B) naudoti eslint-plugin-html / extract script į temp failą CI ir lintinti (sudėtingiau). Ilguoju laikotarpiu geriau (A).

---

## 3. Ko trūksta

### 3.1 Automatizuoti testai

- **Faktas:** Nėra nei vieno automatinio testų failo (unit / integration / E2E). MUST_TODO mini „Basic Testing“ kaip rankinį; unit testai nurodyti kaip P1.
- **Rizika:** Regresijos po pakeitimų neaptinkamos automatiškai.
- **Įgyvendinimas:** Pridėtas papildomas testų rinkinys – žr. skyrių „Pridėtas testų rinkinys“ ir `tests/` katalogą.

### 3.2 Test script package.json

- **Faktas:** `package.json` neturi `"test"` skripto. CI vykdo tik `lint:html` ir `lint:js`.
- **Įgyvendinimas:** Pridėtas `npm test`, kuris paleidžia struktūrinius testus + lint (arba atskirai `npm run test:structure`).

### 3.3 DEPLOYMENT.md — **IŠSPRĘSTA**

- `DEPLOYMENT.md` egzistuoja; GitHub Pages, lokalus tikrinimas, post-deploy testavimas, troubleshooting dokumentuoti.

### 3.4 Nuorodos / privatumas.html

- **Patikrinta:** Footer nuoroda `privatumas.html` ir failas `privatumas.html` egzistuoja; „Grįžti“ nuorodos veikia. Vienintelė smulkmena: privatumas.html turi dvi „Grįžti“ nuorodas (viršus ir apačioje) – tai priimtina (UX).

---

## 4. Atitikimo patikrinimas

### 4.1 Funkcionalumas

- **10 promptų:** Visi 10 promptų egzistuoja su teisingais `id="prompt1"` … `id="prompt10"` ir `id="block1"` … `id="block10"`.
- **Kopijavimas:** Naudojamas `navigator.clipboard.writeText` + `fallbackCopy` (execCommand) – atitinka README ir .cursorrules.
- **Progresas:** „Pažymėjau kaip atlikau“ saugoma `localStorage` su raktais `di_prompt_done_1` … `di_prompt_done_10` – atitinka privatumas.html aprašymą.
- **Klaviatūra:** Code-block turi `tabindex="0"`, `role="button"`, `onkeydown` (Enter/Space) – atitinka a11y reikalavimus.
- **Skip link:** `href="#main-content"`, `<main id="main-content">` – teisingai.

### 4.2 Dokumentacija

- README aprašymas atitinka realią minimalią aplikaciją (be formos, be duomenų rinkimo).
- MUST_TODO aiškiai nurodo, kad Google Script ir GDPR užduotys – vėlesniems etapams; dabartinis fokusas – promptų biblioteka.

### 4.3 Saugumas

- Nėra hardcoded `GOOGLE_SCRIPT_URL` (forma išjungta).
- Jautrų duomenų rinkimo nėra; privatumas.html tai aiškiai nurodo.

---

## 5. Pridėtas testų rinkinys

Pridėta siekiant **garantuoti, kad sistema veikia** po pakeitimų:

| Testas              | Failas / komanda        | Ką tikrina |
|---------------------|-------------------------|------------|
| Struktūra (HTML)    | `tests/structure.test.js` | 10 promptų ID, 10 code-block, skip link, main, progress, toast, footer nuoroda į privatumas.html |
| Lint HTML           | `npm run lint:html`     | W3C HTML validacija |
| Lint JS             | `npm run lint:js`       | ESLint .js failams |
| A11y (CI)           | pa11y                   | WCAG2AA index.html (ir rekomenduojama privatumas.html) |

**Kaip paleisti:**

```bash
npm test
```

arba atskirai:

```bash
npm run test:structure
npm run lint:html
npm run lint:js
```

CI workflow rekomenduojama papildyti `npm test` (kad būtų vykdomi ir struktūriniai testai).

---

## 6. Rekomendacijos (prioritetas)

1. ~~**Dabar:** Pridėti `npm test` į CI~~ — **atlikta:** CI vykdo `npm test`.
2. ~~**Dabar:** Console production~~ — **atlikta:** index.html neturi console.
3. ~~**Trumpuoju laikotarpiu:** DEPLOYMENT.md~~ — **atlikta:** DEPLOYMENT.md egzistuoja.
4. ~~**Deploy:** BASE_PATH GitHub Pages~~ — **atlikta (2026-03-09):** deploy workflow build žingsnyje nustatytas `BASE_PATH=/marketingas`, canonical ir hreflang teisingi.
5. **Pasirinktinai:** Pašalinti arba išskirti nenaudojamą modal/form CSS; privatumas.html „atgal“ nuoroda – išsaugoti locale (žr. planą).
6. **Viduriuoju laikotarpiu:** JavaScript iš `index.html` ištraukti į `app.js` ir lintinti per ESLint (arba palikti kaip yra).

---

## 7. Checklist – „sistema veikia“

Po šios analizės ir pridėtų testų:

- [x] Struktūriniai testai – 10 promptų, semantika, nuorodos.
- [x] Lint (HTML + JS) – įtraukti į `npm test`.
- [x] CI – `npm test` + pa11y (index.html + privatumas.html).
- [x] Production console – pašalinti `console.error` / `console.warn` iš index.html (2026-02-18).
- [x] Dead CSS – dokumentuota komentaru (modal/forma rezervuota būsimai).
- [x] HTML validacija – pataisytos ARIA klaidos (span/p + aria-label → pridėtas role="status").
- [ ] Rankinis QA – MUST_TODO Basic Testing (naršyklės, mobilus, kopijavimas, klaviatūra) – rekomenduojama kartoti prieš release.

---

## 8. Legacy Golden Standard

Dabartinis kodas įrašytas kaip **legacy golden standard**. Toliau keičiame **tik turinį** (promptų tekstus, antraštes, aprašymus, info boksus), laikydamiesi fiksuotos struktūros, ID, CSS klasių ir JavaScript API.

- **Dokumentas:** [docs/LEGACY_GOLDEN_STANDARD.md](docs/LEGACY_GOLDEN_STANDARD.md) – kas fiksuota, ką leidžiama keisti, struktūros schema, checklist prieš commit.
- **Taisyklė:** Content Agent redaguoja tik turinį; pakeitimai struktūrai arba JS reikalauja QA patvirtinimo ir (jei reikia) šio standarto dokumento atnaujinimo.

---

**Paskutinis atnaujinimas:** 2026-03-09 (deploy ruoštis: BASE_PATH, CHANGELOG 1.1.0, išspręstų punktų pažymėjimas)
