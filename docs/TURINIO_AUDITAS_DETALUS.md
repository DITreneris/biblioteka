# Detalus turinio auditas – eilutė po eilutės

**Data:** 2026-02-18  
**Tikslas:** Kiekviena problematiška eilutė, ką taisyti, kuris agentas atsakingas.

---

## KRITINĖS KLAIDOS (encoding / sugadintas tekstas)

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 1 | index.html:1524 | `Vieną idÄ—jÄ… paversk į 7 skirtingus formatus` | Sugadintos lietuviškos raidės (ė→Ä—, ą→Ä…) | `Vieną idėją paversk į 7 skirtingus formatus` | Content |
| 2 | index.html:1543 | `Vienos idÄ—jos daug formatÅ³:` | Sugadintos raidės (ė→Ä—, ų→Å³) | `Vienos idėjos daug formatų:` | Content |
| 3 | index.html:1544 | `Viena stipri idÄ—ja tampa 7 turinio vienetais` | Sugadintos raidės | `Viena stipri idėja tampa 7 turinio vienetais` | Content |

---

## GRAMATIKA / STILISTIKA

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 4 | index.html:1720 | `Iš klientų objection'ų sukurk turinį` | Žargonas "objection'ų" – pavadinime "Prieštaravimų", aprašyme lieka angl. | `Iš klientų prieštaravimų sukurk turinį` | Content |
| 5 | index.html:1735 | `neutralizuoja klientų abejonės ir prieštaravimus` | Gramatika: „abejonės“ – turėtų būti „abejonėms“ (dative) arba „abejones“ | `neutralizuoja klientų abejonėms ir prieštaravimus` | Content |
| 6 | index.html:1745 | `su nuoroda į atitinkamą prieštaravimą ir argumentu` | „argumentu“ – turėtų būti „argumentais“ (instrumental) | `su nuoroda į atitinkamą prieštaravimą ir argumentais` | Content |
| 7 | index.html:1832 | `(5) Pamokos (takeaways)` | Angl. „takeaways“ – žargonas | `(5) Pamokos (pagrindinės mintys)` arba pašalinti | Content |

---

## ŽARGONAS / NESUPRANTAMI DALYKAI

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 8 | index.html:1788 | `Lead'ai:` | Angl. lead'ai – info-box strong | `Potencialūs klientai:` | Content |
| 9 | index.html:1789 | `follower'io į kvalifikuotą lead'ą` | Angl. žargonas | `sekėjo į kvalifikuotą potencialų klientą` | Content |
| 10 | index.html:1779 | `lead generation specialistas` | Angl. – prompte gali palikti (techninis), bet info-box turi būti lt | - | Content |
| 11 | index.html:1928 | `case'ai` | Angl. „case'ai“ | `klientų istorijos` | Content |
| 12 | index.html:1935 | `repurpose` | Angl. žargonas | `performatavimas` arba „vienos idėjos daug formatų“ | Content |
| 13 | index.html:1640 | `scroll'inimą` | Mišrus lt/angl. | `slinkimo sustabdymą` arba „peržvalgymą“ | Content |
| 14 | index.html:1640 | `Short-form:` | Angl. | `Trumpas formatas:` | Content |
| 15 | index.html:1917 | `Performance` | Angl. – galima palikti kaip terminą | - | Content |
| 16 | index.html:1878 | `topical cluster`, `pillar`, `supporting` | SEO žargonas – prompte OK, bet galima paaiškinti | Pridėti į glosarė arba info-box | Content |
| 17 | index.html:1714 | `CTR`, `reach` | Sutrumpinimai be paaiškinimo | Pridėti į glosarė: CTR – paspaudimų santykis, reach – pasiekiamumas | Content |
| 18 | index.html:1680 | `B2B` | Angl. – ne visi žino | Pridėti: „(verslas su verslu)“ arba palikti | Content |

---

## README.md – nesuderinamumas su index.html

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 19 | README:3 | `lead'ai` | Žargonas | `potencialūs klientai` | Content |
| 20 | README:7 | `repurpose mašina, objection handling, lead magnet, case study, topical cluster` | Visi žargonai vienoje eilutėje | Pakeisti į lietuviškus atitikmenis arba paaiškinti | Content |
| 21 | README:19-28 | Promptų sąrašas | „One Insight“, „Objection Handling“, „Lead Magnet“, „Case Study“, „Topical Cluster“ – seni pavadinimai | Atnaujinti pagal index.html: Viena idėja, Prieštaravimų apdorojimas, Nemokamo vediklio postas, Kliento istorijos struktūra, Temų grupė | Content |
| 22 | README:19 | `Case` | „Case“ vietoj „Pavyzdys“ | `Pavyzdys` | Content |
| 23 | README:21 | `proof` | Žargonas | `įrodymai` | Content |
| 24 | README:35 | `DI įrankį` | DI nepaaiškintas | `DI (dirbtinės inteligencijos) įrankį` | Content |
| 25 | README:97 | `kurti lead'us` | Žargonas | `kurti potencialius klientus` | Content |

---

## PRIVATUMAS

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 26 | privatumas.html:31 | `localStorage` | Techninis terminas – vartotojui gali būti neaišku | Pridėti: „(naršyklės vietinė atmintinė)“ | Content |
| 27 | privatumas.html:34 | `panašiai` | Neaiškiai | `panašią formą` | Content |

---

## PROMPTŲ TEKSTAI – likę žargonai

| # | Promptas | Vieta | Tekstas | Problema | Ką taisyti | Agentas |
|---|----------|-------|---------|----------|------------|---------|
| 28 | prompt2 | OUTPUT | `Carousel outline` | Angl. | `Karuselės struktūra` arba palikti (LinkedIn terminas) | Content |
| 29 | prompt2 | OUTPUT | `Landing hero tekstas` | Angl. | `Titulinio ekrano tekstas` arba palikti | Content |
| 30 | prompt2 | OUTPUT | `hook variantai` | Žargonas – bet glosarėje nėra | Pridėti hook į glosarė: „pirmoji frazė, traukianti dėmesį“ | Content |
| 31 | prompt4 | INPUT | `hook 0–2 s` | Hook – žargonas | Galima palikti (kontekste aišku) arba „įžūgi 0–2 s“ | Content |
| 32 | prompt7 | META | `lead generation specialistas` | Angl. | `potencialių klientų pritraukimo specialistas` | Content |
| 33 | prompt7 | OUTPUT | `spamo` | Angl. „spam“ | `įkyraus rinkodaros` arba palikti | Content |
| 34 | prompt8 | OUTPUT | `takeaways` | Angl. | `pagrindinės mintys` | Content |
| 35 | prompt9 | META/INPUT/OUTPUT | `topical cluster`, `pillar`, `supporting` | SEO žargonas | Info-box jau paaiškina; prompte galima palikti | Content |
| 36 | prompt10 | META | `CMO lygio` | Angl. CMO – Chief Marketing Officer | `vyresniojo rinkodaros vadovo lygio` arba palikti | Content |

---

## UI / ARIA / PRIEINAMUMAS

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 37 | index.html:1412 | `Mini rinkodaros AI sistema, lead magnet versija` | aria-label – „lead magnet“ žargonas | `Mini rinkodaros AI sistema, nemokamo vediklio versija` | UI/UX |
| 38 | index.html:531 | `💡 Spausk čia ir nukopijuok` | code-block::before – emoji | Galima palikti; QA tikrinti a11y | - | QA |

---

## PAKARTOTINIAI TEKSTAI (10× prompt-footer)

| # | Vieta | Tekstas | Problema | Ką taisyti | Agentas |
|---|-------|---------|----------|------------|---------|
| 39 | prompt-cta (10×) | `Nukopijuok ir įklijuok į ChatGPT arba Claude – tai šio žingsnio tikslas.` | Kartojasi 10 kartų – monotoniška | Galima varijuoti: „Įklijuok į ChatGPT arba Claude ir pakeisk laukus.“ arba palikti vienodai | Content |

---

## KATEGORIJOS / NEXT-STEPS LINKS

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 40 | index.html:1964 | `4. 30s Video scenarijus` | Santrumpa – gali būti neaišku | `4. 30 sek. video scenarijus` | Content |
| 41 | index.html:1970 | `10. MASTER PROMPT` | Angl. MASTER | `10. Pagrindinis promptas (valdymo centras)` | Content |

---

## FOOTER / COMMUNITY

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 42 | index.html:1990 | `(Lead magnet versija)` | Žargonas | `(Nemokamo vediklio versija)` | Content |
| 43 | index.html:1993 | `CTA fokusas` | Žargonas – tag'e | `Veiksmų fokusas` arba palikti (glosarė paaiškino) | Content |
| 44 | index.html (community CTA) | `Atidaryti Promptų anatomija Telegram grupę` | aria-label – „Promptų anatomija“ gali būti neaišku naujiems | Galima palikti | UI/UX |

---

## OBJEKTŲ APRAŠYMAI (objectives)

| # | Vieta | Dabartinis tekstas | Problema | Ką taisyti | Agentas |
|---|-------|-------------------|----------|------------|---------|
| 45 | index.html:1430 | `lead'us` | Žargonas | `potencialius klientus` | Content |
| 46 | index.html:1431 | `Plan → Kurk → Distribuok → Matuok → Spręsk` | Veiksmažodžiai – gerai, bet rodyklė „→“ gali būti neaiški | Galima palikti | Content |

---

## AGENTŲ ATSAKOMYBĖS SANTRAUKA

| Agentas | Užduočių sk. | Prioritetas |
|---------|--------------|-------------|
| **Content** | 38 | KRITINIS – encoding, gramatika, žargonas, README |
| **UI/UX** | 2 | Žemas |
| **QA** | 1 | Žemas – a11y patikra |

---

## TAKTIKA

1. **PIRMA** – Content Agent: Taisyti encoding (1–3), gramatiką (4–7), kritinį žargoną (8–12).
2. **ANTRA** – Content Agent: README atnaujinimas (19–25).
3. **TREČIA** – Content Agent: Promptų tekstų žargonas (28–36), footer (42–43), objectives (45).
4. **KETVIRTA** – UI/UX Agent: aria-label (37).
5. **PENKTA** – QA Agent: Patikrinti `npm test`, rankinis turinio peržiūrėjimas.
