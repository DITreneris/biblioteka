# Changelog

Visi reikšmingi projekto pakeitimai dokumentuojami šiame faile.

Formatas pagal [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), versijavimas – [Semantic Versioning](https://semver.org/).

## [Nereleisuota]

### Prideta

- Bullet-proof promptų standartas: docs/BULLET_PROOF_PROMPTS.md (META/INPUT/OUTPUT struktūra, reikalavimai, „Naudok kai“ taksonomija). Dokumentų inventoriuje – docs/DOCUMENTATION.md.
- Kiekviename prompte: META/INPUT/OUTPUT blokai, „Pakeisk prieš naudodamas:“, „Rezultatas:“, „Naudok kai:“. Pirmame prompte – „Tai nėra klausimynas. Nukopijuok šį tekstą ir įklijuok į ChatGPT arba Claude.“
- Kortelėse: „Naudok kai“ eilutė po kiekvieno prompto aprašymo (CSS .prompt-when). Gyvo testavimo checklist: „Turinio / bullet-proof“ skyrius docs/TESTAVIMAS.md.
- QA ir dokumentų valdymo procesas: CHANGELOG.md, docs/DOCUMENTATION.md, integracija su AGENTS.md ir .cursorrules.
- Deploy: GitHub Pages workflow (.github/workflows/deploy.yml), DEPLOYMENT.md.
- QA standartas: docs/QA_STANDARTAS.md su nuoroda į [DITreneris/spinoff01](https://github.com/DITreneris/spinoff01).
- Gyvo testavimo dokumentacija: docs/TESTAVIMAS.md (scenarijai ir žurnalas).
- Ryšys su pagrindiniu produktu: badge „Promptų anatomija“ → https://ditreneris.github.io/anatomija/, nuorodos footer ir community skyriuje.
- Favicon: favicon.svg (SVG, „P“ ant teal fono), nuorodos index.html ir privatumas.html.

### Pakeista

- Instrukcijos „Kaip naudoti“ ir footer: aiškinama, kad [ĮMONĖ]/[MANO ROLĖ] keičiami savo duomenimis; DI rolė (pvz. „kritiškas analitikas“) jau nurodyta prompte – jos keisti nereikia. README.md „Kaip naudoti“ atnaujintas atitinkamai.
- Visi 8 promptai perrašyti į META/INPUT/OUTPUT struktūrą; „Rolė – X“ pakeista į „Tu esi X“ (META). DI rolė atskirta nuo vartotojo rolės [MANO ROLĖ].
- Copyable promptas: į mainų atmintinę kopijuojamas tik META+INPUT+OUTPUT. Instrukcijos (Naudok kai, Pakeisk prieš naudodamas, Ką daryti) perkeltos į atskirą bloką „Prieš naudojant“ tarp code-block ir „Kodėl tai svarbu“; „Naudok kai“ pašalintas iš prompt-header.
- Community sekcija: hierarchija ir UX – vienas pagrindinis CTA (brand green #0E7A33, be glow, subtilus shadow), antrinis outline („Promptų anatomija“). Trumpesnė antraštė dviem eilutėm, vertikalūs tarpai (16px / 24px / 16px), kortelė 1px border ir 16px radius. Emoji pašalintas iš CTA. STYLEGUIDE 4.7 atnaujintas.

### Taisyta

- Badge „Promptų anatomija“: paspaudimo zona (min-height/min-width 44px), z-index ir cursor, kad nuoroda būtų aiškiai paspaudžiama.
- A11y WCAG2AA: community skyriaus nuorodos „Promptų anatomija“ kontrastas (teksto spalva #040404).

### Pašalinta

- (tuščia)

### Deprecated

- (tuščia)

### Saugumas

- (tuščia)

---

## [1.0.0] - 2026-02-18

### Prideta

- Pradinė DI Promptų Biblioteka: 8 promptai, interaktyvus dizainas, kopijavimo funkcija.
- Dokumentacija: README.md, INTEGRACIJA.md, AGENTS.md, .cursorrules, feedback-schema.md.
- CI: lint, testai, a11y (pa11y) per .github/workflows/ci.yml.
- PR šablonas ir agentų commit prefiksai.

### Pakeista

- (pirmas release – nėra ankstesnių pakeitimų)

### Taisyta

- (nėra)
