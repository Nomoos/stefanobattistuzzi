# Složka obhajoba/ — všechny materiály pro maturitní obhajobu

**Autor:** Stefano Battistuzzi · **Třída:** S4C · **Termín:** maturitní zkouška 2025/2026
**Projekt:** Webový portál CarzMeetz (carzmeetz.euweb.cz)
**Hodnocení posudků:** vedoucí 26/40 (65 %), oponent 17/30 (57 %) · **oba doporučují k obhajobě**
**Cíl obhajoby:** obhájit projekt s jistotou, věcně přijmout kritiku, ukázat porozumění

---

## Obsah složky

| Soubor | Použití | Komu |
|--------|---------|------|
| **`README.md`** | **ZAČNI TADY** — co je co ve složce | Stefano (orientace) |
| **`PREZENTACE-OBHAJOBA.md`** | **Master plán prezentace** — slide po slidu s mluveným textem, mapování 5 otázek z posudků | Stefano (příprava) |
| **`prezentace.md`** | Marp source — generování prezentace do PPTX/HTML | Stefano (export) |
| **`slides-copypaste.md`** | Slide-po-slide text pro manuální tvorbu/úpravu v PowerPoint/Google Slides | Stefano (sazba) |
| **`POSUDKY.md`** | Plný přepis obou posudků + analýza slabin + souhrn otázek | Stefano + lektor (reference) |
| **`HANDOUT-OBHAJOBA.md`** | Detailní odpovědi na všech 5 otázek z posudků + rozšiřující otázky | Stefano (interní příprava) — **NE komisi** |
| **`STRUCNY-PREHLED.md`** | 1 strana A4 — krátký handout pro komisi | **KOMISI** (volitelně k vytisknutí) |
| **`CUE-CARDS.md`** | Krátké taháky s klíčovými větami, do ruky | Stefano (vytisknout do ruky) |
| **`webove_aplikace_a_softwarove_inzenyrstvi.md`** | **Rozšířená příprava na okruhy 18 a 19** + sekce 20 aplikace teorie na CarzMeetz | Stefano (učení na ústní část) |
| **`../priprava-prezentace.md`** | Analýza stávajícího PPTX + návrhy úprav slidů | Stefano (úpravy prezentace) |
| **`../priprava-otazka-18-webove-aplikace.md`** | Obecná příprava na okruh 18 | Stefano (učení) |
| **`../priprava-otazka-19-sw-inzenyrstvi.md`** | Obecná příprava na okruh 19 | Stefano (učení) |

---

## Stav posudků a co z toho plyne

### Vedoucí (Slovák) — 26 / 40 (≈ chvalitebně/dobře)
- ✅ Pozitivně: `password_hash`, prepared statements, samostatná práce
- ⛔ Negativně: chybějící session management/validace/duplicity, popisná dokumentace, jazyk, citace
- **3 otázky** — viz `HANDOUT-OBHAJOBA.md` V1/V2/V3

### Oponent (Forman) — 17 / 30 (≈ dobře)
- ✅ Pozitivně: funkční výstup, splňuje minimum
- ⛔ Negativně: technické rezervy v kódu, hodně historie webu, málo backendu, slabší struktura
- **2 otázky** — viz `HANDOUT-OBHAJOBA.md` O1/O2

### Klíčový postoj k posudkům
**Oba posudky jsou věcné a obě připomínky jsou většinou oprávněné.** Strategie obhajoby je tedy:
1. **PŘIJÍMAT** drtivou většinu připomínek (pravopis, struktura, validace, dokumentace) — odpor by působil arogantně
2. **VYSVĚTLOVAT** designová rozhodnutí (žádný framework, SQLite, procedurální styl) — to je legitimní obrana
3. **NEOMLOUVAT SE DLOUHO** — uznat krátce a jít dál

---

## Plán obhajoby (cca 15 min)

```
┌─────────────────────────────────────────────────────────────┐
│  setup (předem)    10 min prezentace        ~5 min Q&A      │
│  ─────────────     ──────────────────       ─────────       │
│  - cache web       - 8 slidů                - 5 otázek      │
│  - cue cards       - ~1:15 min/slide        - rozšíření     │
│  - voda            - mluvit z hlavy         - live demo     │
└─────────────────────────────────────────────────────────────┘
```

---

## Co opravit v PPTX před obhajobou

Hlavní body — detailní rozbor stávajícího PPTX viz `../priprava-prezentace.md`:

- 🔴 **Slide 6** — kompletně nahradit šablonový text vlastním obsahem (přejmenovat ze „Charakteristika tématu" na „Použité analytické metody")
- 🔴 **Slide 7** — kompletně nahradit šablonový text (architektura, klíčové funkce, bezpečnost)
- 🔴 **Slide 8** — smazat poslední větu „V čem přesně spočívá Váš osobní přínos…" (je to placeholder ze šablony)
- 🟡 **Slide 2** — doplnit jmenovitě technologie: PHP + SQLite (ne jen „PhpStorm")
- 🟡 **Slide 5** — doplnit konkrétní jména konkurenčních webů, nástroje testování
- 🟡 **Slide 9** — zvážit odebrání (otázky komise nepotřebují vidět) NEBO přejmenovat na „Limity projektu a možná rozšíření"

### Alternativa — vygenerovat novou prezentaci

Pokud Stefano chce **úplně novou prezentaci** podle připraveného plánu:

**Cesta A — Marp → PPTX (rychlejší, ~15 min):**
```bash
npm install -g @marp-team/marp-cli
cd obhajoba/
marp prezentace.md --pptx --output prezentace-nova.pptx
```
Pak nahrát do Google Slides nebo otevřít v PowerPointu a doplnit screenshoty.

**Cesta B — ručně v Google Slides / PowerPointu (~60 min):**
Podle `slides-copypaste.md` — pro každý slide paste TITULEK + OBSAH + SPEAKER NOTES.

---

## Co vytisknout na obhajobu

- [ ] **`STRUCNY-PREHLED.md`** — volitelně **4 výtisky** pro komisi (jen pokud škola vyžaduje)
- [ ] **`CUE-CARDS.md`** — **1 výtisk** pro Stefana do ruky (A4 oboustranně)
- [ ] PDF prezentace (záloha k PPTX) na flashce
- [ ] Dokumentace maturitní práce — **2 výtisky** pro vedoucího a oponenta (pokud žádají)

---

## Setup 5 minut před obhajobou

- [ ] Notebook nabitý / nabíječka po ruce
- [ ] PPTX otevřený, prezentační režim připravený
- [ ] **Otevřít carzmeetz.euweb.cz** v prohlížeči (proklikat všechny sekce kvůli cache warm-up)
- [ ] Backup PDF prezentace na flashce nebo mobilu
- [ ] Cue cards v ruce
- [ ] Voda po ruce
- [ ] Hotspot zapnutý jako záloha sítě
- [ ] Notifikace na laptopu vypnuté
- [ ] Mobil v tichém režimu

---

## Klíčové principy obhajoby

1. **Demo až v Q&A, ne během prezentace.** Web otevřený v prohlížeči, použít kontextově pokud se komise zeptá.
2. **3 kategorie reakcí na výtky:**
   - **PŘIJMOUT** (pravopis, citace, dokumentace, slabší struktura kódu) — „Máte pravdu, v produkci bych to vyřešil takto…"
   - **VYSVĚTLIT** (procedurální styl, SQLite) — „Toto byla vědomá volba s těmito kompromisy…"
   - **OBHÁJIT** (žádný framework pro malý projekt) — „Volba je vědomá z těchto důvodů…"
3. **NEŘÍKAT „Pan Slovák/Forman se ptá".** Odpovědi jsou autonomní argumentace. V Q&A se odkazujeme: „Jak jsem zmínil v prezentaci…"
4. **Krátké odpovědi.** 30–60 s na otázku. Pokud chtějí víc, doptají se.
5. **Když nevím:** přiznat, NEvymýšlet si.

---

## Reference k dalším souborům projektu

- `../battistuzzi_obhajoba.pptx` — finální prezentace (10 slidů, viz priprava-prezentace.md pro nutné úpravy)
- `../Battistuzzi_posudek.pdf` — originální posudky (vedoucího + oponenta) v jednom PDF
- `../otazky.png` + `../otazky.md` — maturitní okruhy 18 a 19
- `../zprava-studenta.md` — úvodní zpráva Stefana lektorovi
- carzmeetz.euweb.cz — živý web (otevřít před obhajobou pro cache warm-up)
