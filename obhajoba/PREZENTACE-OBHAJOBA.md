# Prezentace k obhajobě maturitní práce — FINÁLNÍ PLÁN

**Autor:** Stefano Battistuzzi · **Třída:** S4C · **Obor:** Informační technologie 18-20-M/01
**Téma:** Webový portál CarzMeetz — platforma pro organizaci autosrazů
**Vedoucí:** Ing. Dalibor Slovák Ph.D., dipl. um. · **Oponent:** Ing. Jakub Josef Forman
**Škola:** ORBIS, MŠ/ZŠ/SŠ s.r.o., nám. T. G. Masaryka 1279, 760 01 Zlín
**Živý web:** carzmeetz.euweb.cz
**Délka:** **10 min prezentace** · **Celá obhajoba:** ~15 min (10 min prezentace + ~5 min Q&A)
**Hodnocení posudků:** 26/40 vedoucí (65 %), 17/30 oponent (57 %) · **oba doporučují k obhajobě**
**Cíl obhajoby:** obhájit s jistotou, věcně přijmout připomínky, ukázat porozumění tématu — posunout hodnocení výše tím, že u zkoušky doplním to, co v písemné práci chybí

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

1. **Bílé pozadí + tmavý text.** Žádné světle šedé pastely, žádný tmavý text na tmavém pozadí. Aktuální Stefanův PPTX má tmavé pozadí — zvážit, jestli ho neudělat bělejším pro kmenovou třídu.
2. **Akcent v auto-stylu** (červená/oranžová proužky, ikony) jen jako barevné prvky, ne podklad.
3. **Mluvený text slidů 3, 4 a 7 přerámován** — odpovědi na otázky z posudků jsou v autonomní argumentaci, **NE jako reaktivní „Pan Slovák se ptá, jak funguje hashování…"**. Komise může otázku položit znovu v Q&A — Stefano se pak odkáže „jak jsem zmínil v prezentaci…".
4. **Demo (živý web) proběhne v Q&A**, ne v hlavní prezentaci — viz sekce na konci.
5. **Otázky ze stávajícího slidu 9 v pptx VYPUSTIT** — komise je má v posudcích, není potřeba je v prezentaci ukazovat. Nahradit slidem o limitech projektu (slide 7).

### Setup 3 min checklist (před prezentací)

- [ ] Spustit PPTX v prezentačním režimu (full screen, F5)
- [ ] Otevřít carzmeetz.euweb.cz v prohlížeči → **proklikat** všechny stránky kvůli cache warm-up
- [ ] Backup PDF prezentace na flashce / mobilu (pro případ selhání PowerPointu)
- [ ] Cue cards (`CUE-CARDS.md`) v ruce vytištěné
- [ ] Voda po ruce
- [ ] Vypnuté notifikace na laptopu
- [ ] Mobil v tichém režimu, hotspot zapnutý jako záloha sítě

---

> **Strukturální princip:** Prezentace volně sleduje strukturu posudků (Splnění zadání → Technické řešení → Bezpečnost → Dokumentace → Slabá místa). **Odpovědi na všech 5 otázek z posudků jsou vepsány přímo do mluveného textu příslušných slidů jako autonomní argumentace**, aby komise viděla, že tématu rozumíš, ale bez explicitního „Pan Slovák se ptá…".

---

## Návrh osnovy (8 slidů, sekce posudků jako kostra)

> **Pozn.:** Stávající Stefanův PPTX má 10 slidů, ale slidy 6 a 7 obsahují nevyplněný šablonový text a slide 9 (Otázky) je nadbytečný. Doporučený nový rozsah je **8 slidů**, kompaktnější a obsahovější. Pokud Stefano chce zachovat 10slide PPTX, lze stávající strukturu přemapovat — viz sekce „Mapování na stávající PPTX" níže.

| # | Slide | Sekce posudku | Čas | Kam patří otázky z posudků |
|---|-------|---------------|-----|----------------------------|
| 1 | Titulní | — | 0:30 | — |
| 2 | **Úvod + Cíl + Technologie** | I. | 1:00 | — (kontext) |
| 3 | **Architektura a implementace** | II. praktická | 2:00 | O2 (proč žádný framework) |
| 4 | **Bezpečnost a databáze** | II. praktická | 2:00 | V1 (registrace/heslo), V2 (SQLite), V3 (bezpečnost) |
| 5 | **Vizuální ukázky webu** | I./II. | 0:50 | — (vizuální důkaz) |
| 6 | **Analýza, metody a testování** | II. teoretická | 1:20 | — |
| 7 | **Slabá místa a rozšíření** | III. dokumentace + IV. jazyk + sebereflexe | 1:50 | O1 (jiná DB) + sebereflexe k posudkům |
| 8 | Závěr | — | 0:30 | — |
| Σ | | | **10:00** | |
| **→ po závěru: Dotazy komise + DEMO webu** | | ~5 min mimo prezentaci | Demo carzmeetz.euweb.cz použité kontextově podle dotazů |

> **Buffer:** 10:00 mluveného textu s přirozeným tempem (~115 slov/min). Komise očekává **10 min prezentaci + ~5 min Q&A**. **Live demo bylo přesunuto z hlavního času do Q&A sekce po závěru** — komise dostane demo kontextově, podle toho na co se ptá. Web bude otevřený v prohlížeči, připravený k otevření kdykoliv během dotazů.
>
> **Důležité:** Slidy 3, 4 a 7 jsou nejdelší — obsahují odpovědi na 4 z 5 otázek z posudků. Stefano by je měl **přečíst a natrénovat zvlášť**, aby zněly plynule, ne čtené.

---

## Slide 1 — Titulní

**Čas:** 0:30

**Vizuál:**
- Logo **CarzMeetz** (z `images/carzmeetz_logo1.png`) — vlevo nebo na střed
- Hlavní název: „**Webový portál CarzMeetz**"
- Podtitul: „Platforma pro organizaci autosrazů"
- Autor: **Stefano Battistuzzi**, S4C, 2025/2026
- Vedoucí: Ing. Dalibor Slovák Ph.D., dipl. um.
- Oponent: Ing. Jakub Josef Forman
- Škola: ORBIS Zlín
- Vpravo dole: malý mockup hero sekce webu nebo URL `carzmeetz.euweb.cz`

**Mluvený text:**
> „Dobrý den, jmenuji se Stefano Battistuzzi a obhajuji maturitní práci na téma **Webový portál CarzMeetz** — platformu pro organizaci autosrazů. Vedoucím práce byl pan Slovák, oponentem pan Forman. Web je nasazený na adrese `carzmeetz.euweb.cz`. Pokud bude komise chtít, otevřu ho v rámci dotazů živě v prohlížeči."

---

## Slide 2 — Úvod, Cíl projektu a Technologie

**Čas:** 1:00

**Hlavní sdělení:** Co CarzMeetz dělá a jaké technologie tam jsou. **Klíčové: jmenovitě uvést PHP + SQLite + bez frameworku** — to v aktuálním pptx chybí a komise to potřebuje vědět.

**Vizuál:**
- Vlevo: krátký odstavec **Cíl projektu**
- Vpravo: tabulka **Technologie**

| Vrstva | Použito |
|---|---|
| Backend | **PHP** (procedurální) |
| Databáze | **SQLite** přes PDO |
| Frontend | HTML5, CSS3 (mobile-first) |
| Interaktivita | vanilla JavaScript |
| Vývojové IDE | PhpStorm |
| Hosting | euweb.cz |

**Mluvený text:**
> „Cílem projektu bylo vytvořit moderní webový portál pro komunitu automobilových nadšenců, který umožňuje **sdílení informací o autosrazech**, **registraci uživatelů** a **správu galerie**. Web je responzivní a běží na webhostingu.
>
> **Technologicky** je projekt postaven na **PHP s databází SQLite** přes vrstvu PDO. Frontend je v čistém HTML5, CSS3 s mobile-first přístupem a vanilla JavaScriptu. **Záměrně jsem nepoužil žádný moderní framework jako Laravel nebo Symfony** — důvody rozeberu na příštím slidu. Vývojové prostředí bylo PhpStorm, web je nasazený na free hostingu euweb.cz."

---

## Slide 3 — Architektura a implementace

**Čas:** 2:00

**Hlavní sdělení:** Procedurální PHP architektura, vědomá volba bez frameworku. **Toto je odpověď na otázku O2 od oponenta.**

**Vizuál:** Schéma struktury projektu + tabulka „kde co je":

```text
┌─────────────────────────────────────────────┐
│  Prohlížeč (klient)                         │
│  HTML + CSS + JS                            │
└─────────────────────────────────────────────┘
                    ↓ HTTP
┌─────────────────────────────────────────────┐
│  Webhosting euweb.cz                        │
│  index.php · srazy.php · galerie.php        │
│  about.php  · kontakt.php · register.php    │
│  login.php  · hamburger.php                 │
└─────────────────────────────────────────────┘
                    ↓ PDO
┌─────────────────────────────────────────────┐
│  SQLite databáze                            │
│  users.db (uživatelé)                       │
│  gallery.sqlite (galerie)                   │
└─────────────────────────────────────────────┘
```

| Stránka | Funkce |
|---|---|
| `index.php` | Domovská stránka — hero + sekce o klubu |
| `srazy.php` | Informace o autosrazech |
| `galerie.php` | Galerie (čte fotky z SQLite) |
| `about.php` | O nás + tým |
| `kontakt.php` | Kontaktní info |
| `register.php` | Registrace + login formulář |
| `login.php` | Backend pro ověření (volaný přes `fetch()`) |
| `hamburger.php` | Mobilní hamburger menu (partial) |

**Mluvený text:**

> „Projekt má **procedurální architekturu** — žádný framework jako Laravel nebo Symfony. Každá stránka je samostatný PHP soubor, který kombinuje HTML šablonu s aplikační logikou. Databázová vrstva je řešena přes **PDO s prepared statements**.
>
> **Klíčové rozhodnutí — proč jsem nepoužil moderní framework.** Volba čistého PHP byla úmyslná, ze tří důvodů.
>
> **Za prvé,** chtěl jsem **rozumět tomu, jak weby fungují „pod kapotou"**. Frameworky jako Laravel abstrahují routing, autentizaci, ORM, šablonování. Bez frameworku jsem si tyto věci musel napsat sám, takže přesně vím, co se kde děje. Pokud později budu pracovat ve frameworku, budu mít pevný základ.
>
> **Za druhé,** pro projekt **tohoto rozsahu by byl Laravel overkill**. Web má pět prezentačních stránek, registraci a galerii — pět minimálně. Instalovat kvůli tomu Composer balíček s několika sty závislostmi nemělo smysl.
>
> **Za třetí, jednodušší nasazení**. Stačí nahrát PHP soubory a SQLite databázi přes FTP na hosting, žádné `composer install`, žádné databázové migrace, žádné kompilace assetů.
>
> **Kdy bych framework použil.** Pokud by projekt měl jít do produkce pro tisíce uživatelů, určitě bych přešel na **Laravel** — kvůli vyzrálé autentizaci s CSRF ochranou, validaci formulářů přes Request třídy, ORM Eloquent, migracemi databáze, queue pro odesílání e-mailů, a hlavně lepší bezpečnosti out-of-the-box. Pro maturitní práci ale byla volba čistého PHP správnější."

---

## Slide 4 — Bezpečnost a databáze

**Čas:** 2:00

**Hlavní sdělení:** **Toto je centrální slide — pokrývá tři otázky z posudků: V1, V2, V3.** Ukazuje, co je v projektu hotové (bcrypt, prepared statements, htmlspecialchars) a co by se mělo doplnit pro produkci.

**Vizuál:** Dvě sloupce — **✅ Co je hotové** vs. **⚠️ Co chybí pro produkci**

| ✅ Implementováno | ⚠️ Chybí pro produkci |
|---|---|
| `password_hash()` + bcrypt | HTTPS / TLS |
| `password_verify()` | CSRF tokeny |
| Prepared statements (PDO `bindValue()`) | `session_regenerate_id()` po loginu |
| `htmlspecialchars()` na výstupu | Rate limiting na login |
| `session_start()` v `login.php` | Verifikace e-mailu |
| | `logout.php` (odhlášení) |
| | HttpOnly + Secure + SameSite cookies |

Pod tím malá ukázka kódu:

```php
// register.php — hashování hesla
$hash = password_hash($password, PASSWORD_DEFAULT);
$stmt->bindValue(':password', $hash, PDO::PARAM_STR);

// login.php — ověření
if (password_verify($password, $user['password_hash'])) {
    $_SESSION['user_id'] = $user['id'];
}
```

**Mluvený text:**

> „**Bezpečnost a práce s databází** je oblast, kde můj projekt udělal dva základní kroky správně, ale několik produkčních prvků zatím nemá.
>
> **Co je v projektu hotové.** Hesla se v databázi nikdy neukládají v plaintextu. Při registraci je hashuji funkcí `password_hash()` s výchozím algoritmem **bcrypt**, který automaticky generuje náhodnou sůl. Při loginu pak `password_verify()` v konstantním čase porovná zadané heslo s uloženým hashem. Všechny SQL dotazy používají **prepared statements** s pojmenovanými parametry přes `bindValue()` — uživatelský vstup se nikdy nelepí přímo do SQL stringu, takže riziko SQL injection je eliminováno. Při výpisu uživatelských dat používám `htmlspecialchars()` proti XSS. Po úspěšném loginu vytvořím PHP session a uložím do ní `user_id`.
>
> **Databáze.** Zvolil jsem **SQLite** ze tří důvodů: nepotřebuje samostatný databázový server, je to jeden soubor, PHP má vestavěnou podporu přes PDO. Pro malou komunitu nadšenců je výkon dostatečný. Hlavní **limit** SQLite je, že zamyká celý soubor při zápisu, takže pro vysoký objem souběžných zápisů by bylo nutné přejít na MySQL nebo PostgreSQL. Pro produkční verzi s mapou autosrazů by se hodil zejména **PostgreSQL s rozšířením PostGIS** pro geografická data.
>
> **Co projektu chybí pro reálný provoz.** Chybí mi **HTTPS** (free euweb HTTPS nepodporuje, na placeném hostingu by se přidalo přes Let's Encrypt). Chybí **CSRF tokeny** ve formulářích, **rate limiting** na login proti brute-force, **verifikace e-mailu** při registraci, **regenerování session ID** po loginu proti session fixation, a chybí **odhlášení**. Tyto věci uznávám jako mezery a v produkční verzi bych je doplnil."

---

## Slide 5 — Vizuální ukázky webu

**Čas:** 0:50

**Hlavní sdělení:** Vizuální důkaz, že web vypadá moderně a obsahuje očekávané stránky. **Statické screenshoty, žádné živé demo** — to si komise nechá na Q&A.

**Vizuál:** Slide jako mřížka 2×2 se screenshoty z živého webu:
- Homepage (hero + sekce „CarzMeetz srazy")
- Registrace + Login formulář
- Galerie (z `gallery.sqlite`)
- Mobilní zobrazení s otevřeným hamburger menu

Pod tím malý popisek:
> „URL hostingu: **carzmeetz.euweb.cz**"

**Mluvený text:**
> „Web obsahuje **šest hlavních stránek**: domovskou, srazy, galerii, o nás, kontakt a registraci. Galerie je dynamická — fotky se načítají z SQLite databáze přes `PDO->query`, takže administrátor může přidávat snímky bez úpravy kódu. Design je **mobile-first**, navigace na mobilu používá hamburger menu pod hranicí 768 pixelů, které se vysune zprava pomocí CSS transition. Web je nasazený na hostingu **euweb.cz**, v rámci dotazů ho otevřu živě, pokud bude komise chtít cokoliv vidět."

> *Pozn.: Tento slide je nejkratší. Pokud sklouznu s časem, dá se zkrátit nebo úplně vynechat — vizuál mluví sám za sebe.*

---

## Slide 6 — Analýza, metody a testování

**Čas:** 1:20

**Hlavní sdělení:** Co konkrétně jsem analyzoval, jak jsem testoval. **Vyplňuje šablonový text ze stávajícího slidu 6 v pptx**, který je dnes prázdný/šablonový.

**Vizuál:** Tři sloupce nebo bullet list:

**🔍 Analýza konkurence**
- Srazy.info — fórum pro autosrazy
- AutoMotoSrazy (FB skupina)
- Auto-srazy.eu — informační portál

**📋 Metody návrhu**
- Rešerše komunitních požadavků (neformální dotazování v komunitě)
- Definice MVP funkcí — registrace, galerie, info o srazech
- Návrh UI v PhpStormu (HTML/CSS přímo)

**🧪 Testování**
- Manuální průchod všemi stránkami
- Test responzivity v Chrome DevTools (mobile/tablet/desktop)
- Test registrace a loginu s různými hesly
- Validace HTML přes W3C validátor

**Mluvený text:**
> „**Analytická část projektu** vycházela ze srovnávací analýzy existujících platforem pro autosrazy. Studoval jsem zejména Srazy.info a několik komunitních skupin na Facebooku — chtěl jsem ověřit, které funkce už existují a které uživatelům chybí. Z toho vznikl seznam MVP funkcí: registrace, galerie, informace o srazech.
>
> **Návrh** jsem vedl iterativně. Nejprve jsem si rozkreslil základní layout pro hlavní stránky, pak jsem postupně implementoval HTML a CSS přímo v PhpStormu — bez Figmy nebo jiného grafického nástroje, protože pro projekt této velikosti to nebylo potřeba. Funkčnost backendu jsem řešil postupně: nejdřív statická HTML, pak databáze, pak registrace, pak galerie načítaná z DB.
>
> **Testování** bylo **manuální** — automatizované testy v projektu nejsou. Procházel jsem všechny stránky, zkoušel registraci s různými hesly, ověřoval responzivitu v Chrome DevTools v módech mobile, tablet i desktop. Pro validitu HTML jsem použil **W3C validátor**. V produkční verzi bych přidal **PHPUnit** unit testy alespoň pro password handling, ale pro maturitní rozsah jsem to nepovažoval za nutné."

---

## Slide 7 — Slabá místa a rozšíření

**Čas:** 1:50

**Hlavní sdělení:** **Sebereflexe** — vědomé přiznání zbývajících výtek z posudků + konkrétní plán doplnění. **Signalizuje jistotu a porozumění — komise miluje, když student vidí slabiny své práce.**

**Vizuál:** Tabulka 3 sloupce, 6 řádků:

| Výtka / Mezera | Stav | Plán pro produkční verzi |
|---|---|---|
| **HTTPS** chybí (free euweb) | nedostatek hostingu | placený hosting + Let's Encrypt certifikát |
| **CSRF tokeny** ve formulářích | chybí | random token v session, ověření před submitem |
| **Logout** a `session_regenerate_id` | chybí | `logout.php` se `session_destroy()` + regenerování po loginu |
| **Verifikace e-mailu** + rate limit | chybí | confirmation link, počítadlo neúspěšných pokusů |
| **Dokumentace** popisná, ne technická | uznáno z posudku | doplnit sekci s architekturou + ER diagram |
| **Pravopisné/citační chyby** | uznáno z posudku | reference manager (Zotero), pečlivá korektura |
| **Žádný framework / žádné MVC** | vědomá volba | Laravel pro produkci — autentizace, ORM, validace |
| **Pouze SQLite** | dostatečné pro maturitu | MySQL/PostgreSQL pro produkci · **PostGIS pro mapu autosrazů** |

**Mluvený text:**

> „Závěrem chci sám zmínit body, které v práci považuji za slabší nebo mezery, na které mi posudky upozornily.
>
> **HTTPS — toto je důležitá mezera.** Free euweb hosting HTTPS neposkytuje, takže hesla a session cookies se aktuálně přenášejí v plaintextu. V produkční verzi bych přešel na placený hosting s Let's Encrypt certifikátem, který je zdarma a automaticky obnovovaný.
>
> **CSRF tokeny a regenerování session ID — toto jsou oprávněné připomínky vedoucího v posudku.** Můj projekt nemá obranu proti CSRF útokům ani proti session fixation. Doplnil bych random token uložený v session, který by se ověřoval při každém POST submitu, a po úspěšném loginu bych volal `session_regenerate_id(true)`.
>
> **Logout a verifikace e-mailu** — také uznané mezery. Implementoval bych klasický `logout.php` se `session_destroy()` a confirmation link při registraci s tokenem v URL.
>
> **Použití jiné databáze než SQLite** — pokud bych projekt rozšiřoval do produkce, **MySQL nebo MariaDB** by přinesly podporu plně konkurentních zápisů, vzdálený přístup po síti a lepší správu uživatelů. Pro mou doménu — mapování autosrazů na území Česka — by se ale ideálně hodil **PostgreSQL s rozšířením PostGIS** pro geografická data a indexování souřadnic.
>
> **Dokumentace a citace** — pan vedoucí v posudku připomíná, že dokumentace praktické části je popsaná spíše uživatelsky a čísla citací v bibliografii jsou nesprávná. Obojí přijímám — pro další práci bych použil reference manager Zotero, který sleduje propojení odkazů, a dokumentaci bych rozšířil o technickou sekci s architekturou a schématem databáze."

---

## Slide 8 — Závěr

**Čas:** 0:30

**Vizuál:** Tři kompaktní bloky + závěrečná věta:

| ✅ Hotovo | 🔄 Rozšiřitelné | 🎯 Výsledek |
|----------|----------------|-------------|
| 6 stránek, registrace, galerie | HTTPS + CSRF + logout | funkční portál |
| bcrypt + prepared statements | Laravel + MySQL pro produkci | vlastní programátorský základ |
| responzivní design | technická dokumentace | nasazený web carzmeetz.euweb.cz |

Velký nadpis: **„Děkuji za pozornost. Web mám otevřený pro případné dotazy."**

**Mluvený text:**

> „Projekt splňuje stanovené cíle — vytvořil jsem **funkční webový portál s registrací, galerií a informacemi o autosrazech**, nasazený na hostingu. Hlavním přínosem je **vlastní programátorský základ** bez závislosti na frameworku, díky kterému jsem získal hluboké porozumění tomu, jak weby fungují. Pro produkční nasazení by bylo nutné doplnit HTTPS, CSRF ochranu, logout a zvážit přechod na Laravel s databází vhodnou pro geografická data. Děkuji za pozornost. Web mám otevřený v prohlížeči, takže pokud bude komise chtít cokoliv vidět živě, mohu se kdykoli přepnout. Jsem připraven na otázky."

---

## Po závěru: Dotazy komise + LIVE DEMO (mimo 8 min)

**Princip:** demo není časovaný blok, ale **kontextový nástroj během Q&A**. Komise se zeptá → Stefano podle relevance buď odpoví slovně, nebo přepne na browser a ukáže to na webu.

**Co mít připraveno PŘED Q&A:**
- Prohlížeč s otevřenými **5 záložkami**: Homepage, /srazy, /galerie, /register, /about
- Cache warm-up — všechny stránky načtené 30 min předem
- Záložní PDF prezentace na flashce / mobilu

**Mapování dotazů → demo akcí:**

| Pokud se komise zeptá na… | Otevři tab… | Co krátce komentovat |
|---------------------------|-------------|----------------------|
| **Registrace, hashování hesla** | `/register.php` | „Vyplním testovací účet — vidíte, že po submitu je heslo uložené jako bcrypt hash, ne v plaintextu. Tady v PhpStormu otevřu `register.php`, kde je vidět volání `password_hash()`." |
| **Login, session** | `/register.php` (login form vpravo) | „Zde se login odesílá přes JavaScript fetch na `login.php`. Po úspěchu se vytvoří PHP session — to bych v dev tools mohl ukázat v cookies." |
| **SQL prepared statements** | otevřít kód v PhpStormu | „V `login.php` je vidět prepared statement s `:ue` parametrem a `bindValue()` — žádný uživatelský vstup se nelepí do SQL stringu." |
| **Galerie / SQLite** | `/galerie.php` | „Tady je vidět dynamická galerie — fotky se načítají z `gallery.sqlite` tabulky `gallery`, sloupce `id, name, image_path`. PHP cyklus přes výsledek query renderuje `<img>` tagy." |
| **Mobilní zobrazení / hamburger** | DevTools (F12) → responsive mode | „V mobilním režimu se navigace skryje a objeví se hamburger button vpravo nahoře. Po kliknutí menu sjíždí zprava CSS transition v `hamburger.php`." |
| **Architektura projektu** | otevřít strukturu v PhpStormu | „V root projektu vidíte všech 9 PHP souborů — žádné podsložky pro controllers/models/views, procedurální styl." |
| **Něco, co nefunguje / hosting nereaguje** | Backup PDF | „Hosting reaguje pomalu — ukážu na záložních screenshotech v PDF." |
| **Otázka mimo můj projekt** | (zůstat u prezentace) | „Mimo můj projekt jsem to neřešil, ale princip je …" |

**Záchranné fráze v demu:**

| Situace | Co říct |
|---------|---------|
| Web se načítá > 3 s | „Free hosting reaguje pomalu — v produkci s placeným hostingem a cache pluginem by to bylo bleskové." |
| Komise se ptá na funkci, kterou web nemá | „Toto v aktuální verzi není, ale dalo by se to řešit takto: [konkrétní krok]. Patří to mezi rozšíření, která jsem zmínil na slidu 7." |
| Stefano zabloudí v navigaci | „Vrátím se na úvodní stránku a otevřu to z hlavního menu." |
| Web vrátí chybu (500/404) | „Vidíme chybu — to je dobrá ukázka, proč by se v produkci hodil staging server pro testování. Pokračuji slovně nebo otevřu screenshoty." |
| Komise se zeptá na HTTPS | „Free euweb HTTPS nemá — viděli byste error 403 'HTTPS není dostupné'. V produkci bych řešil přes Let's Encrypt." |

> **Klíčový princip:** demo není performance pro komisi, je to **odpověď na konkrétní dotaz**. Stefano mluví o webu, ne web sám.

---

## Mapování 5 otázek z posudků → slidů (autonomní rámování)

| Otázka | Slide | Jak je implicitně pokryta v mluveném textu |
|--------|-------|--------------------------------------------|
| **V1 (Slovák) — Registrace a hashování hesla** | 4 | „Při registraci hashuji funkcí `password_hash()` s bcrypt… při loginu `password_verify()` v konstantním čase…" |
| **V2 (Slovák) — Proč SQLite a jeho limity** | 4 | „SQLite jsem zvolil ze tří důvodů… hlavní limit je write-locking…" |
| **V3 (Slovák) — Bezpečnostní prvky pro reálný provoz** | 4 + 7 | „Chybí mi HTTPS… CSRF tokeny… rate limiting…" + slide 7 jako rozšíření |
| **O1 (Forman) — Výhody jiné databáze** | 7 | „Pro produkci by se hodil PostgreSQL s PostGIS pro geografická data — mapování autosrazů…" |
| **O2 (Forman) — Proč žádný framework** | 3 | „Klíčové rozhodnutí — proč jsem nepoužil framework. Tři důvody: porozumění, rozsah, nasazení…" |

> **Důsledek:** Stefano odpovědi vysvětluje **jako vlastní rozhodnutí, ne jako reakci na komisi**. V Q&A když komise otázku položí, Stefano se odkáže: „Jak jsem zmínil v prezentaci, hlavní důvod je X — a rád to rozvedu detailněji o Y a Z." Tím dodržuje etiketu „počkat na položení otázky" a zároveň ukazuje, že měl odpověď připravenou.

---

## Mapování na stávající PPTX (pokud Stefano nechce generovat nové)

Pokud Stefano chce zachovat **stávající 10slide PPTX** místo nového 8slide, doporučuji následující úpravy:

| Stávající slide | Stav | Akce |
|---|---|---|
| 1. Titulní | ✅ OK | Doplnit ORBIS + rok + úplný název práce |
| 2. Úvod | ✅ OK | Změnit „Vytvořeno v aplikaci PhpStorm" → „Vyvinuto v PHP s databází SQLite, IDE PhpStorm" |
| 3. Tvorba | ✅ OK | „Tvorba databází" → „Návrh databáze" (singulár) |
| 4. Charakteristika tématu | ✅ OK | Beze změny |
| 5. Analýza a metody | ⚠️ slabé | Doplnit jmenovitě konkurenty + nástroje (Chrome DevTools, W3C validátor) |
| **6. Charakteristika tématu (duplicitní)** | 🔴 nevyplněno | **Přejmenovat na „Použité analytické metody"**, nahradit text — viz slide 6 v této osnově |
| **7. Projektové řešení** | 🔴 nevyplněno | **Nahradit celý šablonový text** vlastním obsahem — viz slidy 3 a 4 v této osnově |
| 8. Závěr | ⚠️ částečně | **Smazat poslední větu „V čem přesně spočívá Váš osobní přínos…"** (je to placeholder ze šablony), nahradit konkrétním textem o přínosu |
| **9. Otázky** | 🔴 nadbytečné | **Smazat nebo přepsat na „Slabá místa a rozšíření"** — viz slide 7 v této osnově. Komise otázky z posudků zná, není potřeba je v prezentaci ukazovat. |
| 10. Děkuji za pozornost | ✅ OK | Beze změny, případně doplnit URL `carzmeetz.euweb.cz` |

> **Doporučení:** Pokud má Stefano čas, **udělat novou prezentaci ze souboru `prezentace.md`** (Marp). Pokud ne, opravit stávající podle této tabulky.

---

## Časová kontrola (před obhajobou)

- [ ] **Přečíst slidy nahlas se stopkami**, cíl 7:00–8:00
- [ ] Slide 5 (vizuální ukázky) natrénovat krátké uvedení, **bez čtení**
- [ ] Slide 7 (slabá místa) — pokud > 1:30, zkrátit poslední odstavec o dokumentaci
- [ ] Slide 3 a 4 — natrénovat zvlášť, obsahují odpovědi na 4 z 5 otázek a musí znít plynule
- [ ] **Otevřít `carzmeetz.euweb.cz` 30 min před obhajobou** (cache warm-up)
- [ ] **Zkontrolovat HTTPS** — pokud nefunguje, mít připravenou odpověď „free hosting…"
- [ ] **Backup PDF prezentace na flashce/mobilu** (proti selhání PowerPointu)
- [ ] **Cue cards** (`CUE-CARDS.md`) v ruce vytištěné A4 oboustranně

---

## Reference

- Posudky v plném znění: [`POSUDKY.md`](./POSUDKY.md)
- Detailní odpovědi na 5 otázek z posudků: [`HANDOUT-OBHAJOBA.md`](./HANDOUT-OBHAJOBA.md)
- Cue cards k tisku: [`CUE-CARDS.md`](./CUE-CARDS.md)
- Stručný handout pro komisi: [`STRUCNY-PREHLED.md`](./STRUCNY-PREHLED.md)
- Marp source pro generování PPTX: [`prezentace.md`](./prezentace.md)
- Maturitní okruhy 18 a 19 (rozšířená příprava): [`webove_aplikace_a_softwarove_inzenyrstvi.md`](./webove_aplikace_a_softwarove_inzenyrstvi.md)
