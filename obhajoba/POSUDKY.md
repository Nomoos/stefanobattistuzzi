# Posudky maturitní práce

**Autor:** Stefano Battistuzzi
**Název:** Webový portál (CarzMeetz — portál pro organizaci autosrazů)
**Škola:** ORBIS, Mateřská škola, Základní škola a Střední škola, s.r.o., nám. T. G. Masaryka 1279, 760 01 Zlín
**Obor:** Informační technologie 18-20-M/01 · Třída: S4C
**Vedoucí:** Ing. Dalibor Slovák Ph.D., dipl. um.
**Oponent:** Ing. Jakub Josef Forman
**Živý web:** carzmeetz.euweb.cz

---

## 1. Posudek vedoucího — Ing. Dalibor Slovák Ph.D., dipl. um.

### Bodové hodnocení: **26 b. / 40 b.** (65 %)

#### Odborná úroveň práce (12 / 18 b.)
| Kritérium | Body |
|-----------|------|
| Míra naplnění všech bodů zadání (max 4) | **3** |
| Obtížnost odevzdaného projektu (max 4) | **2** |
| Vhodnost zvolených metod provedení (max 2) | **2** |
| Kreativita (max 2) | **1** |
| Celková úroveň teoretické části (max 3) | **2** |
| Celková úroveň praktické části (max 3) | **2** |

#### Formální úroveň práce (6 / 12 b.)
| Kritérium | Body |
|-----------|------|
| Formální zpracování a celkový dojem (max 4) | **2** |
| Úroveň jazykového zpracování (max 4) | **2** |
| Práce s literaturou a citace (max 4) | **2** |

#### Přístup žáka ke zpracování (8 / 10 b.)
| Kritérium | Body |
|-----------|------|
| Žák pracoval aktivně, samostatně (max 5) | **5** |
| Žák dodržoval dohodnuté termíny konzultací (max 5) | **3** |

### Připomínky vedoucího — citace

> Žák vytvořil vlastní webový portál CarzMeetz pro srazy automobilových nadšenců. Projekt obsahuje několik stránek, responzivní navigaci, galerii, registraci a přihlášení uživatelů, práci s PHP, PDO a databází SQLite.
>
> **Praktická část je v dokumentaci popsána spíše uživatelsky a obecně, nikoli jako technická dokumentace aplikace.**
>
> U přihlášení a registrace je pozitivní použití `password_hash`/`password_verify` a připravených SQL dotazů. **Práce ale nijak neřeší správu session, odhlášení, ošetření duplicit a validaci.**
>
> Teoretická část je rozsáhlá, ale převážně popisná. Obsahuje obecný výklad historie webu, HTML, CSS, JavaScriptu a SQLite. **Část textu je použitelná, ale často nepřechází do hlubšího odborného vysvětlení a jen částečně navazuje na konkrétní praktický projekt.**
>
> Formální a jazyková úroveň je průměrná až slabší. V textu se opakují **pravopisné, gramatické a stylistické nedostatky**: např. „taky" místo spisovnějšího „také", „scriptovací" místo „skriptovací", „technologii" místo „technologií", „byla využit databázový systém" místo „byl využit databázový systém", „všechny data" místo „všechna data", „kategorii" místo „kategorií", „Instagramu, která" místo „Instagramu, který", „datum vytvoření" vhodněji „datum vytvoření záznamu".
>
> **Práce se zdroji je problematická.** Některé zdroje jsou kvalitní a relevantní, zejména CERN, W3C, MDN a SQLite. **Zásadní chybou je ale číslování citací:** v textu se například kapitola HTML opakovaně odkazuje na zdroj (7), ale sedmá položka seznamu literatury je článek Britannica o JavaScriptu, nikoli zdroj k HTML. Kapitola CSS opakovaně používá zdroj (8), ale osmá položka je W3C Wiki o historii webu, nikoli použitý zdroj světWP o CSS. Podobně tvrzení o moderních webových technologiích je odkázáno na (13), což je v seznamu zdrojů k HTML.

### Celkové hodnocení vedoucího

> Celkově práci hodnotím jako **dobrou, nikoli výbornou**. Praktický projekt je funkční a má vlastní programátorský základ, ale dokumentace, práce se zdroji, jazyková úroveň a odborná hloubka neodpovídají vyššímu hodnocení.
>
> **Tuto práci doporučuji k obhajobě.**

### Otázky vedoucího (3)

1. **Popište, jak přesně funguje registrace a přihlášení uživatele včetně uložení hesla do databáze.**
2. **Vysvětlete, proč jste zvolil SQLite a jaké jsou výhody a limity této databáze pro webový portál s více uživateli.**
3. **Jaké bezpečnostní prvky byste do aplikace doplnil, aby byla vhodnější pro reálný provoz?**

---

## 2. Posudek oponenta — Ing. Jakub Josef Forman

### Bodové hodnocení: **17 b.** (celkový počet bodů za zpracování práce)

> **Pozn.:** Posudek oponenta nehodnotí samostatně přístup žáka — jen odbornou a formální úroveň. Maximum z těchto dvou kategorií je 30 b., Stefano dostal 17 b. (≈ 57 %).

#### Odborná úroveň práce (11 / 18 b.)
| Kritérium | Body |
|-----------|------|
| Míra naplnění všech bodů zadání (max 4) | **3** |
| Obtížnost odevzdaného projektu (max 4) | **2** |
| Vhodnost zvolených metod provedení (max 2) | **2** |
| Kreativita (max 2) | **1** |
| Celková úroveň teoretické části (max 3) | **2** |
| Celková úroveň praktické části (max 3) | **1** |

#### Formální úroveň práce (6 / 12 b.)
| Kritérium | Body |
|-----------|------|
| Formální zpracování a celkový dojem (max 4) | **2** |
| Úroveň jazykového zpracování (max 4) | **2** |
| Práce s literaturou a citace (max 4) | **2** |

### Připomínky oponenta — citace

> V teoretické části se autor zaměřuje na historii webových stránek. **Rozsah této kapitoly je však neúměrně detailní vzhledem k jejímu významu pro zbytek práce**, a to bohužel na úkor jiných podstatných teoretických celků. Zatímco popis frontendových technologií je zpracován v dostatečné míře, v práci **citelně chybí podrobnější analýza backendových technologií**. Z hlediska formálního zpracování se v textu objevují **strukturální chyby, jako jsou nadpisy bez následného obsahu**, a občasné gramatické nedostatky, které mírně snižují celkový dojem.
>
> Praktickým výstupem je funkční webová stránka, která splňuje stanovené minimální požadavky na projekt tohoto typu. Autor prokázal schopnost vytvořit funkční celek, **nicméně po technické stránce má práce značné rezervy. Struktura projektu a čistota kódu by si zasloužily systematičtější přístup.** Pro zvýšení úrovně práce by bylo vhodné využít pokročilejší technologie nebo moderní frameworky, které by projektu dodaly větší profesionalitu.
>
> Práce i přes své koncepční a gramatické nedostatky v teoretické části a spíše základní technické řešení v části praktické naplňuje zadání maturitní práce. **Autor prokázal základní kompetence pro tvorbu webového řešení.**
>
> S ohledem na výše uvedené připomínky **doporučuji práci k obhajobě**.

### Otázky oponenta (2)

1. **Jakou by mělo výhodu, pokud by byla použita jiná databáze?**
2. **Proč není použita žádná moderní knihovna/framework v projektu?**

---

## Souhrn k obhajobě

| Kategorie | Vedoucí (Slovák) | Oponent (Forman) |
|-----------|------------------|------------------|
| Odborná úroveň | 12 / 18 | 11 / 18 |
| Formální úroveň | 6 / 12 | 6 / 12 |
| Přístup žáka | 8 / 10 | — |
| **Celkem** | **26 / 40 = 65 %** | **17 / 30 = 57 %** |
| Doporučení k obhajobě | ✅ ANO | ✅ ANO |

### Slabá místa — připravené reakce

> **Pozn.:** Scope je zafixován na obhajobu — kód se před obhajobou neupravuje (ani opravdu nemůže, posudky jsou dány). Tato místa Stefano v Q&A buď přijme jako oprávněnou připomínku, nebo věcně vysvětlí designové rozhodnutí.

| Slabé místo | Kategorie reakce | Co říct |
|-------------|------------------|---------|
| **Chybí správa session, odhlášení, validace, ošetření duplicit** (vedoucí) | **PŘIJMOUT** | „To je oprávněná připomínka. Implementoval jsem `session_start()` a uložení user_id, ale neměl jsem CSRF tokeny, regenerování session ID po loginu, ani validaci jedinečnosti e-mailu. V příští verzi bych to doplnil." |
| **Dokumentace je uživatelská, ne technická** (vedoucí) | **PŘIJMOUT** | „Souhlasím — psal jsem dokumentaci spíš pro budoucího uživatele, ne pro vývojáře. V příští verzi bych přidal sekci s architekturou aplikace, schématem databáze a popisem hlavních funkcí v kódu." |
| **Pravopisné/gramatické/stylistické chyby** (vedoucí) | **PŘIJMOUT** | „Přijímám tuto kritiku, text jsem před odevzdáním neměl řádně zkontrolován." (KRÁTCE — neomlouvat se dlouho) |
| **Špatné číslování citací** (vedoucí) | **PŘIJMOUT** | „To byla chyba při finálním sestavování seznamu zdrojů — některé citace v textu odkazují na nesprávná čísla v bibliografii. Při příštím psaní bych použil reference manager (např. Zotero), který tomu předchází." |
| **Teorie je popisná, nepřechází do hloubky** (vedoucí + oponent) | **VYSVĚTLIT** | „Snažil jsem se v teorii ukázat základní porozumění tématu. Souhlasím, že některé pasáže by si zasloužily hlubší rozbor — zejména backend a databáze. Při dalším projektu bych si lépe hlídal poměr mezi obecnou teorií a tím, co je relevantní pro vlastní řešení." |
| **Historie webu je neúměrně detailní** (oponent) | **PŘIJMOUT** | „Souhlasím, historie web technologií dostala v práci nepřiměřeně mnoho prostoru. Místo toho měla být dána větší pozornost backendu a SQLite, na kterých projekt skutečně stojí." |
| **Chybí analýza backendových technologií** (oponent) | **PŘIJMOUT** | „Toto vidím nyní jako jednu z hlavních slabin práce — k PHP, PDO a SQLite jsem mohl napsat významně víc. Mohu o nich vyprávět nyní, pokud chcete." (NABÍDKA k diskusi) |
| **Nadpisy bez následného obsahu** (oponent) | **PŘIJMOUT** (jen pokud se zeptají) | „To byl důsledek toho, že jsem v některých sekcích plánoval doplnit obsah a před odevzdáním na to zapomněl." |
| **Struktura projektu a čistota kódu** (oponent) | **VYSVĚTLIT** | „Kód jsem psal procedurálně, soubor po souboru, bez striktní MVC struktury. To je vědomé rozhodnutí — viz otázka o frameworku — ale uznávám, že by si projekt zasloužil systematičtější rozdělení (např. složky `controllers/`, `models/`, `views/`)." |
| **Doporučení použít moderní framework** (oponent) | **VYSVĚTLIT + OBHÁJIT** | viz otázka 5 v `HANDOUT-OBHAJOBA.md` |
| **Kreativita pouze 1 b. u obou** | (jen pokud se zeptají) | „Téma autosrazů mě baví osobně, ale projekt vychází z konvenční šablony 'CMS pro komunitu'. Pro maturitní práci jsem chtěl zvolit téma, které dokončím, ne nutně něco unikátního." |

### Otázky pro obhajobu — sumář (5 otázek celkem)

**Od vedoucího (technické detaily implementace):**
- V1: Jak funguje registrace a přihlášení uživatele včetně uložení hesla?
- V2: Proč SQLite a jaké jsou výhody a limity?
- V3: Jaké bezpečnostní prvky doplnit pro reálný provoz?

**Od oponenta (architektonická rozhodnutí):**
- O1: Jakou výhodu by mělo použití jiné databáze?
- O2: Proč není použita žádná moderní knihovna/framework v projektu?

> **Plné odpovědi** na všech 5 otázek jsou v `HANDOUT-OBHAJOBA.md`.
