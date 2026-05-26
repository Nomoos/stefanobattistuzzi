# Prezentace k obhajobě maturitní práce — FINÁLNÍ PLÁN

**Autor:** Stefano Battistuzzi · **Třída:** S4C · **Obor:** Informační technologie 18-20-M/01
**Plný název práce:** Webový portál *(praktická realizace: webový portál CarzMeetz pro autosrazy)*
**Vedoucí:** Ing. Dalibor Slovák Ph.D., dipl. um. · **Oponent:** Ing. Jakub Josef Forman
**Škola:** ORBIS, MŠ/ZŠ/SŠ s.r.o., nám. T. G. Masaryka 1279, 760 01 Zlín
**Živý web:** carzmeetz.euweb.cz
**Délka:** **10 min prezentace** · **Celá obhajoba:** ~15 min (10 min prezentace + ~5 min Q&A)
**Hodnocení posudků:** 26/40 vedoucí (65 %), 17/30 oponent (57 %) · **oba doporučují k obhajobě**
**Cíl obhajoby:** obhájit s jistotou, věcně přijmout připomínky, ukázat porozumění tématu
**Termín obhajoby:** **od 29.5.2026** (veřejná)

---

## ⚠️ Závazná struktura podle školního vzoru `Orbis prezentace - final_vzor.pptx`

Škola ORBIS poskytla **závaznou 7slide šablonu**. Komise očekává tuto strukturu — moje předchozí 8slide návrh byl chybný. Stefanův stávající PPTX z této šablony vychází, ale obsahuje nevyplněné šablonové texty na slidech 6 a 7 — to je primární problém k opravě.

| # | Slide podle vzoru | Co se očekává | Mluvený čas |
|---|-------------------|---------------|-------------|
| 1 | **Titulní** | Název, autor, vedoucí, rok | 0:30 |
| 2 | **Úvod** | Proč téma? Cíl? Postup? | 1:30 |
| 3 | **Praktická část** | Charakteristika + analytické metody + proč tyto metody | 2:30 |
| 4 | **Projektové řešení** | Hlavní zásady, co přinese praxi, závěry | 2:30 |
| 5 | **Závěr** | Cíle dosaženy? Obohacení? Jak pokračovat? Osobní přínos | 1:30 |
| 6 | **Otázky** | Otázky komise + klíčová slova k odpovědím *(vzor přímo doporučuje!)* | 1:00 |
| 7 | **Děkuji za pozornost** | Poděkování + URL webu | 0:30 |
| Σ |  |  | **10:00** |

> **Důležité zjištění:** Slidy 6 a 7 v Stefanově stávajícím PPTX **obsahují nevyplněné navádějící otázky ze školní šablony** („Jaké jsou hlavní zásady?", „V čem spočívá Váš osobní přínos?"). To NEJSOU placeholdery v technickém smyslu — jsou to **otázky, na které má Stefano vlastními slovy odpovědět**. Stefano je zapomněl nahradit vlastními odpověďmi.

---

## Praktické info o průběhu obhajoby

| Položka | Detail |
|---------|--------|
| Setup time | **před vstupem do třídy** — otevřít PPTX + carzmeetz.euweb.cz v prohlížeči (cache warm-up) |
| Total | ~**15 min** |
| Prezentace | **10 min** · může obsahovat živé demo webu |
| Q&A | vedoucí + oponent pokládají otázky z posudků · mohou navázat další |
| Etiketa | **počkat na položení otázky**, neodpovídat předem |
| Místo | **kmenová třída** — pozor na kontrast text/pozadí |

### Důsledky pro design slidů a obsah

1. **Bílé pozadí + tmavý text.** Stávající Stefanův PPTX má tmavé pozadí — pro kmenovou třídu s denním světlem horší kontrast. Zvážit změnu.
2. **Akcent v auto-stylu** (červené proužky, ikony) jen jako barevné prvky.
3. **Mluvený text slidů 3 a 4 je hlavní nositel** odpovědí na otázky z posudků — natrénovat zvlášť, aby zněly plynule.
4. **Slide 6 (Otázky) je LEGITIMNÍ** — vzor přímo říká „doporučuje se na tento snímek umístit otázky oponenta (vedoucího)". Stefano má v stávajícím PPTX všech 5 otázek na slidu 9 — to bylo **správně**, jen je třeba k nim doplnit klíčová slova k odpovědím.
5. **Demo (živý web) proběhne v Q&A**, ne v prezentaci.

### Setup checklist (před prezentací)

- [ ] Spustit PPTX v prezentačním režimu (F5)
- [ ] Otevřít carzmeetz.euweb.cz v prohlížeči → **proklikat** všechny stránky kvůli cache warm-up
- [ ] Backup PDF prezentace na flashce / mobilu
- [ ] Cue cards (`CUE-CARDS.md`) v ruce vytištěné
- [ ] Voda po ruce
- [ ] Vypnuté notifikace na laptopu
- [ ] Mobil v tichém režimu, hotspot jako záloha

---

## Slide 1 — Titulní (0:30)

**Co očekává vzor:** Vedoucí práce, název, autor.

**Vizuál:**
- Logo CarzMeetz (z `images/carzmeetz_logo1.png` v ZIPu projektu)
- **Plný název práce:** „Webový portál" *(jak je v zadání)*
- Podtitul: „Webový portál CarzMeetz pro organizaci autosrazů"
- Autor: **Stefano Battistuzzi, S4C**
- Vedoucí: Ing. Dalibor Slovák Ph.D., dipl. um.
- Škola: ORBIS Zlín · 2025/2026
- Volitelně: URL `carzmeetz.euweb.cz`

**Mluvený text:**

> „Dobrý den, jmenuji se Stefano Battistuzzi a obhajuji maturitní práci na téma **Webový portál**. V praktické části jsem realizoval konkrétní portál pro organizaci autosrazů s názvem **CarzMeetz**, který je nasazený na adrese `carzmeetz.euweb.cz`. Vedoucím práce byl pan Slovák. Pokud bude komise chtít, otevřu web v rámci dotazů živě v prohlížeči."

---

## Slide 2 — Úvod (1:30)

**Co očekává vzor:**
- Proč jste si zvolil/a dané téma?
- Co bylo cílem práce a čeho jste chtěl/a dosáhnout (objektivní i subjektivní důvody)?
- Jak jste při zpracování postupoval/a?

**Vizuál (3 bloky):**

**🎯 Téma**
Autosrazy CarzMeetz — vlastní zájem o auta + osobní angažmá v komunitě.

**📌 Cíl práce**
„Ukázat problematiku tvorby webových stránek a portálů a demonstrovat jejich funkčnost na praktickém příkladu." *(citace z úvodu MP)*

**⚙️ Postup zpracování**
- Teoretická část: HTML, CSS, JavaScript, SQLite, historie webu
- Praktická část: návrh a implementace webu CarzMeetz
- Postupně: HTML → CSS → JavaScript → PHP → SQLite → nasazení na hosting

**Mluvený text:**

> „**Téma webového portálu** jsem si zvolil ze dvou důvodů. **Subjektivně** — jsem osobně součástí komunity automobilových nadšenců a chtěl jsem pro tuto komunitu vytvořit konkrétní nástroj. **Objektivně** — webová prezentace přesahuje jen psaní HTML, zahrnuje práci s databází, bezpečnost, responzivní design a nasazení na hosting. To znamenalo, že jsem se musel naučit více oblastí najednou.
>
> **Cílem práce** bylo ukázat problematiku tvorby webových stránek a portálů a demonstrovat jejich funkčnost na praktickém příkladu — což cituji ze své práce. Konkrétně jsem si dal za úkol vytvořit funkční web s databází, který bude umožňovat zobrazování informací o autosrazech a registraci uživatelů.
>
> **Při zpracování jsem postupoval po fázích.** V teoretické části jsem popsal historii webu, jednotlivé technologie HTML, CSS, JavaScript a databázový systém SQLite. V praktické části jsem nejprve navrhl strukturu webu, poté implementoval HTML kostru, doplnil CSS pro design, přidal JavaScript pro mobilní menu, PHP pro registraci a galerii, a nakonec vše propojil s SQLite databází. Web jsem nasadil na hosting webzdarma.cz pod doménou `carzmeetz.euweb.cz`."

---

## Slide 3 — Praktická část (2:30)

**Co očekává vzor:**
- Stručná charakteristika tématu
- Vlastní analýzy — jaké konkrétní analytické či výzkumné metody jste využil/a?
- Proč jste zvolil/a právě tyto metody?

**Vizuál:**

**📋 Charakteristika tématu**
Webový portál CarzMeetz pro komunitu automobilových nadšenců — registrace uživatelů, galerie z autosrazů, informace o nadcházejících akcích.

**🔍 Použité analytické metody**
| Metoda | Popis |
|---|---|
| **Srovnávací analýza** | Studium konkurenčních platforem (Srazy.info, FB skupiny) |
| **Rešerše komunitních požadavků** | Neformální dotazování v komunitě nadšenců |
| **Návrh struktury** | Definice MVP funkcí: registrace, galerie, informace |
| **Iterativní implementace** | Postupné rozšiřování od statického HTML k dynamickému PHP |
| **Manuální testování** | Průchod scénáři + validace HTML (W3C) + responzivita (DevTools) |

**❓ Proč tyto metody**
Vhodné pro komunitní projekt malého rozsahu — žádné automatizované testy ani externí výzkum nepotřeba.

**Mluvený text:**

> „**Charakteristika tématu.** Webový portál CarzMeetz je platforma pro komunitu automobilových nadšenců v České republice. Slouží ke sdílení informací o autosrazech, registraci uživatelů a archivaci fotek z proběhlých akcí. Portál obsahuje šest hlavních stránek, dvě SQLite databáze a responzivní design pro mobilní zařízení.
>
> **Použité analytické metody.** První metoda byla **srovnávací analýza konkurenčních platforem**. Studoval jsem zejména server Srazy.info a několik komunitních skupin na Facebooku — chtěl jsem ověřit, které funkce už existují a které uživatelům chybí. Druhá metoda byla **rešerše komunitních požadavků** — neformální dotazování v komunitě, ve které sám fungujem. Z toho vzešel seznam MVP funkcí: registrace, galerie, informace o srazech. Třetí metoda byla **iterativní implementace** — postupně jsem stavěl od statického HTML přes CSS až po dynamický PHP s databází. Čtvrtá metoda bylo **manuální testování** — procházel jsem všechny stránky, zkoušel registraci s různými hesly, ověřoval validitu HTML v W3C validátoru a responzivitu v Chrome DevTools v módech mobile, tablet i desktop.
>
> **Proč jsem zvolil tyto metody.** Pro projekt menšího rozsahu jsou tyto kvalitativní metody dostatečné. Automatizované testy by byly overkill, marketingový výzkum konkurence by byl příliš formální. Cílem nebylo udělat akademickou studii, ale dodat fungující produkt pro reálnou komunitu."

---

## Slide 4 — Projektové řešení (2:30)

**Co očekává vzor:**
- Jaké jsou hlavní zásady/principy navrhovaného řešení?
- Co konkrétně implementace přinese praxi?
- Nejdůležitější závěry

> **Toto je centrální slide pro odpovědi na 4 z 5 otázek z posudků** (V1 hashování, V2 SQLite, V3 bezpečnost, O2 framework). Komise dostane odpovědi „v autonomní argumentaci", aniž by Stefano čekal na otázku.

**Vizuál:**

**🏗️ Hlavní zásady řešení**

| Zásada | Detail |
|---|---|
| **Procedurální PHP, bez frameworku** | Vlastní implementace všeho — pochopení principů |
| **SQLite + PDO** | Embedded databáze, jeden soubor, žádný server |
| **Bezpečné heslování** | `password_hash()` bcrypt + `password_verify()` |
| **Prepared statements** | `bindValue()` proti SQL injection |
| **Responzivní design** | Mobile-first, hamburger menu pod 768 px |

**💡 Co řešení přináší praxi**
- Funkční MVP komunitního portálu nasazený na hostingu
- Reálné použití: 6 testovacích uživatelů + 6 fotek v galerii
- Vlastní programátorský základ k pochopení jak weby fungují

**📌 Limity a budoucí kroky**
- Bez frameworku → procedurální styl (pro produkci → Laravel)
- SQLite → write-locking (pro produkci → PostgreSQL + PostGIS pro mapu autosrazů)
- Free euweb → bez HTTPS (pro produkci → Let's Encrypt)
- Chybí CSRF, logout, `session_regenerate_id` (uznané mezery z posudku)

**Mluvený text:**

> „**Hlavní zásady navrhovaného řešení** vycházejí ze tří klíčových rozhodnutí.
>
> **První rozhodnutí — procedurální PHP, bez frameworku.** Cíleně jsem se rozhodl nepoužít Laravel ani Symfony. Důvod je pedagogický — pro maturitní projekt jsem chtěl rozumět tomu, jak weby fungují „pod kapotou". Frameworky abstrahují routing, autentizaci, ORM. Bez nich jsem si tyto věci musel napsat sám, takže přesně vím, co se kde děje. Pro produkční verzi pro tisíce uživatelů bych Laravel zvolil — kvůli vyzrálé autentizaci a CSRF ochraně.
>
> **Druhé rozhodnutí — SQLite jako databáze.** SQLite jsem zvolil proto, že nepotřebuje samostatný server, je to jeden soubor a PHP má vestavěnou podporu přes PDO. Pro komunitu desítek uživatelů je výkon dostatečný. Hlavní limit SQLite je, že zamyká celý soubor při zápisu, takže pro vysoký objem souběžných zápisů by bylo nutné přejít na MySQL. Pro produkční verzi s mapou autosrazů by se hodil zejména PostgreSQL s rozšířením PostGIS pro geografická data.
>
> **Třetí rozhodnutí — bezpečné heslování od začátku.** Hesla se v databázi nikdy neukládají v plaintextu. Při registraci je hashuji funkcí `password_hash()` s algoritmem **bcrypt**, který automaticky generuje náhodnou sůl. Při loginu pak `password_verify()` v konstantním čase porovná zadané heslo s uloženým hashem. Všechny SQL dotazy používají prepared statements proti SQL injection. Při výpisu uživatelských dat používám `htmlspecialchars()` proti XSS.
>
> **Co řešení přináší.** Funkční MVP komunitního portálu nasazený na hostingu, šest registrovaných testovacích uživatelů a šest fotek v galerii — to znamená, že každá implementovaná funkce je živě ověřená.
>
> **Limity a budoucí kroky.** Uznávám, že pro reálný provoz by web potřeboval **HTTPS**, **CSRF tokeny**, **regenerování session ID po loginu** a **logout** — tyto mezery v posudku vedoucího uznávám a v produkční verzi bych je doplnil. Free euweb HTTPS aktuálně neumožňuje, ale na placeném hostingu by se přidalo přes Let's Encrypt zdarma."

---

## Slide 5 — Závěr (1:30)

**Co očekává vzor:**
- Dosáhl/a jste cílů, které jste si stanovil/a?
- Jak Vás osobně práce na daném tématu obohatila?
- Jakým způsobem by bylo možno (nebo nutno) na zkoumání daného problému pokračovat?
- V čem přesně spočívá Váš osobní přínos k řešení problematiky?

**Vizuál (4 bloky):**

**✅ Dosažení cílů**
„Cíl se podařilo splnit — funkční web s databází, který umožňuje zobrazování informací o srazech a práci s nimi." *(citace ze závěru MP)*

**🎓 Jak mě práce obohatila**
- Rozšíření znalostí HTML, CSS, JavaScriptu a PHP
- První zkušenost s databází SQLite a její propojení s webovým portálem
- Reálný projekt nasazený na hostingu

**🔮 Pokračování práce**
- Vytvořit web v podobném stylu a dále jej rozvíjet
- Přidání dalších funkcí: kalendář srazů, mapa, profily uživatelů
- Vylepšení uživatelského prostředí + UX testování

**🎯 Osobní přínos**
Vlastní implementace celého stacku od HTML přes PHP po SQLite **bez použití frameworku** — hluboké porozumění tomu, jak weby fungují pod kapotou. Tuto znalost mohu využít v dalším studiu nebo praxi.

**Mluvený text:**

> „**Dosáhl jsem cílů, které jsem si stanovil?** Ano. Cílem bylo vytvořit webovou aplikaci zaměřenou na autosrazy CarzMeetz a tento cíl se mi podařilo splnit — povedlo se mi vytvořit funkční web s databází, který umožňuje zobrazování informací o srazech a práci s nimi.
>
> **Jak mě práce obohatila.** Během tvorby jsem si rozšířil znalosti v oblasti webových technologií, především HTML, CSS, JavaScriptu a PHP. Vyzkoušel jsem si práci s databází SQLite a její propojení s webovým portálem, což pro mě byla zcela nová zkušenost. Zároveň jsem si vyzkoušel nasazení vlastní aplikace na hosting, což je krok, který v běžné výuce často chybí.
>
> **Jak pokračovat.** Do budoucna bych chtěl vytvořit web v podobném stylu a dále jej rozvíjet — přidat dynamickou správu srazů s kalendářem, mapu autosrazů s geografickými souřadnicemi, profily uživatelů a komentáře k fotkám. Z bezpečnostního pohledu by bylo nutné doplnit HTTPS, CSRF tokeny a verifikaci e-mailu.
>
> **Můj osobní přínos.** Vědomá volba implementovat celý web vlastním kódem bez frameworku mi umožnila pochopit, jak weby fungují od HTML šablony až po databázi. Tuto zkušenost — že rozumím každému řádku kódu ve svém projektu — mohu využít v dalším studiu i v praxi. To je největší přínos, který mi maturitní práce dala."

---

## Slide 6 — Otázky komise (1:00)

**Co očekává vzor:**
> „Vaše prezentace skončila předchozím snímkem. Po něm následuje vyjádření vedoucího práce a oponenta. Doporučuje se na tento snímek umístit otázky oponenta (vedoucího), případně podstatné informace k Vašim odpovědím, na něž se dostane po přečtení posudků."

**Vizuál (kompaktní seznam 5 otázek + klíčová slova k odpovědi):**

**❓ Otázky vedoucího práce (Ing. Slovák)**

1. **Jak přesně funguje registrace a přihlášení včetně uložení hesla?**
   → bcrypt, prepared statements, PHP session — *viz slide 4*

2. **Proč SQLite a jaké jsou výhody a limity?**
   → embedded, zero-config, write-locking limit — *viz slide 4*

3. **Jaké bezpečnostní prvky pro reálný provoz?**
   → HTTPS, CSRF, rate limit, verifikace e-mailu, logout

**❓ Otázky oponenta (Ing. Forman)**

4. **Výhoda jiné databáze?**
   → MySQL pro konkurenci, PostgreSQL + PostGIS pro mapu autosrazů

5. **Proč žádný moderní framework?**
   → vědomá volba pro pochopení principů, Laravel pro produkci — *viz slide 4*

**Mluvený text:**

> „Tímto má prezentace končí. Komise nyní dostane prostor pro vyjádření vedoucího práce a oponenta. Na tomto snímku mám připravený přehled pěti otázek, které mi byly položeny v posudcích, společně s klíčovými body, na které ve své odpovědi navážu. Na všechny tyto otázky jsem v prezentaci alespoň zčásti odpověděl — především v rámci slidu 4 o projektovém řešení. V Q&A rád jakoukoli odpověď rozvedu detailněji."

> **Pozn.:** Tento mluvený text je krátký záměrně — komise teď přijme slovo, takže Stefano jen plynule předá štafetu. Klíčová slova na slidu fungují jako vizuální opora pro Q&A, ne pro mluvený monolog.

---

## Slide 7 — Děkuji za pozornost (0:30)

**Vizuál:**
- Velký nadpis: **„Děkuji za pozornost"**
- Pod tím: **carzmeetz.euweb.cz**
- Logo CarzMeetz (volitelně)
- Stefano Battistuzzi, S4C

**Mluvený text:**

> „Děkuji za pozornost a za příležitost představit svou maturitní práci. Web mám otevřený v prohlížeči, takže pokud bude komise chtít cokoliv vidět živě, mohu se kdykoli přepnout. Jsem připraven na otázky."

---

## Po závěru: Dotazy komise + LIVE DEMO (mimo 10 min)

**Princip:** demo není časovaný blok, ale **kontextový nástroj během Q&A**.

**Co mít připraveno PŘED Q&A:**
- Prohlížeč s otevřenými 5 záložkami: Homepage, /srazy, /galerie, /register, /about
- Cache warm-up — všechny stránky načtené 30 min předem
- Záložní PDF prezentace na flashce / mobilu

**Mapování dotazů → demo akcí:**

| Pokud se komise zeptá na… | Otevři tab… | Co krátce komentovat |
|---------------------------|-------------|----------------------|
| **Registrace, hashování** | `/register.php` | „Vyplním testovací účet — heslo se uloží jako bcrypt hash, ne plaintext. V `register.php` je vidět volání `password_hash()`." |
| **Login, session** | `/register.php` (login form vpravo) | „Login se odesílá přes JavaScript fetch na `login.php`. Po úspěchu se vytvoří PHP session." |
| **SQL prepared statements** | otevřít kód v PhpStormu | „V `login.php` je prepared statement s `:ue` parametrem a `bindValue()` — žádný uživatelský vstup se nelepí do SQL." |
| **Galerie / SQLite** | `/galerie.php` | „Galerie čte z `gallery.sqlite` tabulky `gallery` — sloupce `id, name, image_path`." |
| **Mobilní zobrazení** | DevTools (F12) → responsive | „V mobilním režimu se navigace skryje a objeví hamburger button." |
| **Architektura projektu** | strukturu v PhpStormu | „V root projektu vidíte všech 9 PHP souborů — procedurální styl, žádné MVC složky." |
| **Něco, co nefunguje** | Backup PDF | „Hosting reaguje pomalu — ukážu na záložních screenshotech." |
| **HTTPS** | — | „Free euweb HTTPS nemá — uvidíte error 403. V produkci bych řešil přes Let's Encrypt." |

**Záchranné fráze v demu:**

| Situace | Co říct |
|---------|---------|
| Web se načítá > 3 s | „Free hosting reaguje pomalu — v produkci s placeným hostingem by to bylo bleskové." |
| Komise se ptá na funkci, kterou web nemá | „V aktuální verzi to není, ale dalo by se to řešit takto: [krok]. Patří to mezi rozšíření, která jsem zmínil." |
| Stefano zabloudí v navigaci | „Vrátím se na úvodní stránku a otevřu to z hlavního menu." |
| Web vrátí chybu (500/404) | „Vidíme chybu — proto by se v produkci hodil staging server. Pokračuji slovně nebo otevřu screenshoty." |
| Otázka mimo můj projekt | „Mimo můj projekt jsem to neřešil, ale princip je…" |

> **Klíčový princip:** demo není performance pro komisi, je to **odpověď na konkrétní dotaz**. Stefano mluví o webu, ne web sám.

---

## Mapování 5 otázek z posudků → slidů

| Otázka | Slide | Jak je implicitně pokryta |
|--------|-------|---------------------------|
| **V1 (Slovák) — Registrace a hashování hesla** | 4 | „Hesla se nikdy neukládají v plaintextu… `password_hash()` s bcrypt… `password_verify()`…" |
| **V2 (Slovák) — Proč SQLite a jeho limity** | 4 | „SQLite jsem zvolil proto, že nepotřebuje samostatný server… hlavní limit je write-locking…" |
| **V3 (Slovák) — Bezpečnostní prvky pro reálný provoz** | 4 | „Uznávám, že pro reálný provoz by web potřeboval HTTPS, CSRF, regenerování session ID, logout…" |
| **O1 (Forman) — Výhody jiné databáze** | 4 | „Pro produkci by se hodil PostgreSQL s PostGIS pro geografická data — mapa autosrazů…" |
| **O2 (Forman) — Proč žádný framework** | 4 | „Procedurální PHP bez frameworku — důvod pedagogický, chtěl jsem rozumět principům…" |

> **Důsledek:** Stefano odpovědi vysvětluje **jako vlastní rozhodnutí na slidu 4**. V Q&A se odkazuje: „Jak jsem zmínil v prezentaci, hlavní důvod je X — a rád to rozvedu detailněji o Y a Z." Tím dodržuje etiketu „počkat na položení otázky" a zároveň ukazuje, že měl odpověď připravenou.

---

## Mapování na stávající 10slide PPTX

Stefanův stávající PPTX má 10 slidů (rozšíření vzoru o postup tvorby + statickou „Charakteristiku tématu"). Pokud chce stávající strukturu zachovat, doporučuji následující úpravy:

| Stávající slide | Stav | Akce |
|---|---|---|
| 1. Titulní | ✅ OK | Doplnit ORBIS + rok + plný název práce „Webový portál" |
| 2. Úvod | ⚠️ slabě | Přepsat podle nového slidu 2 — proč téma, cíl, postup |
| 3. Tvorba | ✅ OK | Drobně: „Tvorba databází" → „Návrh databáze" (singulár) |
| 4. Charakteristika tématu | ⚠️ slabě | Sjednotit se slidem 3 nového plánu — charakteristika webu CarzMeetz |
| 5. Analýza a metody | ⚠️ slabě | Doplnit konkrétně podle nového slidu 3 (Srazy.info, DevTools, W3C) |
| **6. Charakteristika tématu (duplicitní)** | 🔴 nevyplněno | **Nahradit textem nového slidu 3 (Vlastní analýzy, proč tyto metody)** |
| **7. Projektové řešení** | 🔴 nevyplněno | **Nahradit textem nového slidu 4 (Zásady, přínos, závěry)** |
| 8. Závěr | ⚠️ částečně | **Smazat placeholder „V čem přesně spočívá Váš osobní přínos…"** a nahradit textem nového slidu 5 |
| **9. Otázky** | ✅ OK | **Ponechat 5 otázek** + přidat klíčová slova k odpovědím podle nového slidu 6 |
| 10. Děkuji za pozornost | ✅ OK | Doplnit URL `carzmeetz.euweb.cz` |

> **Doporučení:** Pokud má Stefano čas, je lepší **vygenerovat zcela novou prezentaci ze souboru `prezentace.md`** (Marp) — bude přesně podle školního vzoru a komise to ocení. Pokud čas chybí, opravit stávající podle této tabulky.

---

## Časová kontrola (před obhajobou)

- [ ] **Přečíst slidy nahlas se stopkami**, cíl 9:30–10:00
- [ ] **Slide 3 a 4** natrénovat zvlášť — obsahují odpovědi na 4 z 5 otázek z posudků a musí znít plynule
- [ ] **Slide 4** je nejnáročnější (2:30) — natrénovat všechny 3 zásady plynule, bez čtení
- [ ] **Slide 5** — natrénovat citace z mé práce nahlas (cíl, obohacení, pokračování, přínos)
- [ ] **Slide 6** — natrénovat krátké předání slova komisi po prezentaci
- [ ] **Otevřít `carzmeetz.euweb.cz` 30 min před obhajobou** (cache warm-up)
- [ ] **Zkontrolovat HTTPS** — pokud nefunguje, mít připravenou odpověď „free hosting…"
- [ ] **Backup PDF prezentace** na flashce/mobilu (proti selhání PowerPointu)
- [ ] **Cue cards** (`CUE-CARDS.md`) v ruce vytištěné A4 oboustranně

---

## Reference

- Závazný školní vzor: `../Orbis prezentace - final_vzor.pptx`
- Plná maturitní práce: `../2025-26_S4C_MP_IT_Stefano_Battistuzzi.pdf` (38 stran)
- Zdroják projektu: `../battistuzzi_prace.zip`
- **Opravený PPTX (Cesta B, 10 slidů):** `../battistuzzi_obhajoba_OPRAVENO.pptx`
- Posudky: [`POSUDKY.md`](./POSUDKY.md)
- Detailní odpovědi na 5 otázek: [`HANDOUT-OBHAJOBA.md`](./HANDOUT-OBHAJOBA.md)
- **Standalone slide s 5 otázkami (k tisku):** [`otazky-slide.md`](./otazky-slide.md)
- Cue cards k tisku: [`CUE-CARDS.md`](./CUE-CARDS.md)
- Stručný handout pro komisi: [`STRUCNY-PREHLED.md`](./STRUCNY-PREHLED.md)
- Marp source pro generování PPTX (Cesta A, 7 slidů): [`prezentace.md`](./prezentace.md)
- Copy-paste pro PowerPoint: [`slides-copypaste.md`](./slides-copypaste.md)
- Maturitní okruhy 18 a 19 (rozšířená příprava): [`webove_aplikace_a_softwarove_inzenyrstvi.md`](./webove_aplikace_a_softwarove_inzenyrstvi.md)
