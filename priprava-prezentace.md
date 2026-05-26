# Příprava prezentace k obhajobě — „CarzMeetz"

Podklad pro lektora na konzultaci se Stefanem Battistuzzim.

**Projekt:** Webový portál CarzMeetz pro organizaci autosrazů
**Vedoucí práce:** Ing. Dalibor Slovák Ph.D., dipl. um.
**Stack (odvozeno z otázek na slidu 9):** čisté PHP + SQLite, bez moderního frameworku, vývoj v PhpStorm
**Existující soubor:** `battistuzzi_obhajoba.pptx` (10 slidů)

---

## 1. Shrnutí stavu prezentace

Prezentace má rozumnou kostru (titulní → úvod → tvorba → charakteristika → analýza → projektové řešení → závěr → otázky → poděkování), ale **trpí třemi vážnými problémy, které musí Stefano před obhajobou opravit**:

### 🔴 Kritické problémy

| # | Problém | Slide | Řešení |
|---|---------|-------|--------|
| 1 | **Nevyplněný šablonový text z osnovy** | 6, 7 | Smazat instrukce, doplnit vlastní obsah |
| 2 | **Duplicitní nadpis** „Charakteristika tématu" | 4 i 6 | Slide 6 přejmenovat (např. „Použité metody analýzy") |
| 3 | **Slide 8 obsahuje placeholder otázku** | 8 | Smazat větu „V čem přesně spočívá Váš osobní přínos…" |

### 🟡 Sekundární problémy

- Nikde v prezentaci nejsou **jmenovitě uvedeny použité technologie** (PHP, SQLite, HTML/CSS/JS). Komise to bude potřebovat vědět.
- Slide 5 „Analýza a metody" je velmi obecný (3 bullety bez detailu) — působí slabě.
- Chybí konkrétní **výstupy/snímky obrazovky** projektu (přitom je 12 obrázků v médiích — možná tam jsou, ale extrakcí textu to nezjistím).
- V celé prezentaci je opakující se zápatí „Stefano Battistuzzi" — to je OK, ale ujistit se, že je opravdu na všech slidech jednotně.

---

## 2. Slide-by-slide analýza a doporučení

### Slide 1 — Titulní ✅
> Vedoucí práce: Ing. Dalibor Slovák Ph.D., dipl. um.
> Webový portál
> Stefano Battistuzzi

**Stav:** OK. Možná doplnit: název školy, rok, plný název práce („Webový portál CarzMeetz pro organizaci autosrazů" namísto jen „Webový portál").

---

### Slide 2 — Úvod ✅
**Stav:** OK. Sdělení cíle je jasné.

**Drobné zlepšení:** „Vytvořeno v aplikaci PhpStorm" je trochu nešťastné — PhpStorm je jen IDE, ne použitá technologie. Lepší formulace:

> Vyvinuto v jazyce **PHP** s databází **SQLite**, IDE PhpStorm.

To zároveň elegantně vyřeší absenci jmenování technologií jinde v prezentaci.

---

### Slide 3 — Tvorba ✅
> Vizualizace layoutu a designu → Tvorba základní struktury → Implementace designu → Tvorba databází a responzivity → Testování funkčnosti

**Stav:** Dobrý postup, ale je to **vodopád**, což je v pořádku — Stefano může u otázky 19 (SDLC) na tento slide odkázat: „Pracoval jsem víceméně vodopádovým modelem, postupně po fázích."

**Drobné zlepšení:** „Tvorba databází" (množné číslo) → „Návrh databáze" (1× SQLite).

---

### Slide 4 — Charakteristika tématu ✅
**Stav:** OK. Konkrétní, srozumitelný.

**POZOR:** Stejný nadpis se opakuje na slidu 6 — viz níže.

---

### Slide 5 — Analýza a metody ⚠️
> Analýza konkurenčních webů a sociálních sítí
> Testování funkčnosti webu
> Kontrola responzivity

**Stav:** Příliš obecné, působí slabě. Komise se bude ptát „co konkrétně jste analyzoval/měřil/srovnával?".

**Návrh doplnit:**
- *Které konkurenční weby jsem analyzoval?* (např. 2–3 jmenovitě: Srazy.info, MeetingFun, FB skupiny…)
- *Jaké funkce jsem na nich identifikoval a kterou jsem převzal/zamítl?*
- *Jaký nástroj jsem použil na kontrolu responzivity?* (Chrome DevTools, BrowserStack, vlastní zařízení…)
- *Jak jsem testoval funkčnost — manuálně? Nějaký scénář? Beta-uživatelé?*

---

### Slide 6 — 🔴 NEVYPLNĚNÝ
> Charakteristika tématu *(duplicitní s.4!)*
> Vlastní analýzy - jaké konkrétní analytické či výzkumné metody jste využil/a (např. srovnávací analýza, textová analýza, rešerše médií, marketingový průzkum zákazníků či konkurence apod.)?
> Proč jste zvolil/a právě tyto metody?

**Stav:** ⛔ **Toto je text osnovy/šablony**, Stefano ho zapomněl nahradit vlastním obsahem. Komise to okamžitě uvidí.

**Co s tím:**
- Přejmenovat nadpis (např. **„Použité analytické metody"**)
- Odpovědět na ty dvě otázky vlastními slovy. Návrh:

> **Použité analytické metody**
> - **Srovnávací analýza konkurenčních platforem** — Srazy.info, automotorevue, FB skupiny
> - **Rešerše uživatelských požadavků** — neformální dotazování v komunitě autosrazů
> **Proč:** chtěl jsem ověřit, které funkce už existují, abych nestavěl něco nadbytečného, a které funkce uživatelům chybí.

---

### Slide 7 — 🔴 NEVYPLNĚNÝ
> Projektové řešení
> Týká se pouze maturitní práce, pokud obsahuje projekt, jinak lze nazvat tento snímek „Návrhy a doporučení" apod., nebo úplně vynechat.
> Jaké jsou hlavní zásady/principy navrhovaného řešení?
> Co konkrétně implementace vámi navrhovaného řešení přinese praxi?
> Neprezentujte v plné šíři konkrétní výstupy (grafy, tabulky apod.), ale pokuste se shrnout, jaké nejdůležitější závěry jste učinil/a. …

**Stav:** ⛔ **Opět text osnovy, nevyplněný!** Tohle je nejvážnější problém prezentace.

**Co s tím:** Vyhodit šablonový text a doplnit obsah typu:

> **Projektové řešení**
> - **Architektura:** klient (HTML/CSS/JS) ↔ PHP backend ↔ SQLite databáze
> - **Klíčové funkce:** registrace/přihlášení, vytvoření srazu, přihlášení na sraz, profil uživatele
> - **Princip bezpečnosti:** hesla uložena jako `password_hash()` (bcrypt), prepared statements proti SQL injection
> - **Responzivita:** mobile-first, breakpointy 576/768/992/1200 px
> - **Hosting:** [doplnit kde — webhosting, vlastní VPS, …]
>
> **Co projekt přináší:** Funkční MVP platformu pro malou komunitu autosrazů, kterou lze provozovat zdarma na základním hostingu.

Sem se hodí 1–2 screenshoty — homepage + detail srazu.

---

### Slide 8 — Závěr ⚠️
> Stanovil jsem si cíle, které jsem byl schopen dokončit.
> Naučil jsem se pracovat samostatně na větším projektu …
> Pro budoucí použití stránky je nutno zapracovat na bezpečnosti, soukromí a vylepšení databáze.
> **V čem přesně spočívá Váš osobní přínos k řešení problematiky?** ⛔

**Stav:** Tři první body OK, ale poslední věta je **opět placeholder ze šablony** — smazat!

**Doporučená náhrada poslední věty:**
> Osobním přínosem práce je kompletně vlastní implementace webu od návrhu databáze po hosting bez použití frameworku, díky čemuž jsem získal hluboké porozumění tomu, jak weby fungují „pod kapotou".

---

### Slide 9 — Otázky 🎯
**Stav:** Tento slide obsahuje 5 otázek. Není zcela jasné, zda jsou to:
- (a) otázky, které **Stefano očekává od komise**, nebo
- (b) otázky, které **chce sám prezentovat a zodpovědět**.

Doporučuji v prezentaci **otázky vůbec neuvádět** (komise si je položí sama). Místo toho použít slide na **technické detaily / ukázku kódu** (např. snippet `password_hash()` + prepared statement). **Otázky si Stefano musí umět odpovědět tak jako tak** — viz sekce 3 níže.

---

### Slide 10 — Poděkování ✅
**Stav:** OK.

---

## 3. Příprava odpovědí na otázky ze slidu 9

Toto jsou pravděpodobně otázky, které Stefano očekává. Lektor si je pročte a na konzultaci s ním projde každou — co odpovědět, kde má slabiny, co dotyčný umí říct sám a kde mu pomoct.

---

### Otázka 1 — Jak funguje registrace a přihlášení včetně uložení hesla?

**Vzorová odpověď (cca 30 s):**

> Při registraci uživatel vyplní formulář (jméno, e-mail, heslo). Backend v PHP heslo nikdy neukládá v čistém tvaru — použije funkci `password_hash($heslo, PASSWORD_DEFAULT)`, která interně použije algoritmus **bcrypt** se solí. Do databáze SQLite se uloží jen tento hash, ne původní heslo.
>
> Při přihlášení backend načte uložený hash a porovná zadané heslo přes `password_verify($zadane, $ulozeny_hash)`. Pokud sedí, vytvořím PHP session (`session_start()`) a uložím do ní user_id. Session cookie pak browser posílá při každém dalším requestu, takže si server pamatuje, že je uživatel přihlášený.

**Kontrolní otázky pro Stefana během konzultace:**
- Co je to **sůl (salt)** v hashování? *(náhodný řetězec, který se přidá k heslu před hashováním, aby dvě stejná hesla měla různé hashe — zabraňuje rainbow table útokům)*
- Proč ne MD5 nebo SHA-256? *(jsou rychlé → snadný brute force; bcrypt je úmyslně pomalý)*
- Co se stane, když mu uživatel pošle e-mail s tečkou navíc? *(pokud nepoužívá email_validate, projde — měl by říct, že validuje přes `filter_var($email, FILTER_VALIDATE_EMAIL)`)*

**Slabiny v odpovědi — na co se připravit:**
- Komise se může zeptat, **zda používá CSRF token** ve formuláři. Pokud ne, čestně přiznat a vědět co to je.
- **Brute-force ochrana** (rate limiting / captcha) — pravděpodobně nemá. To uvést v limitacích.

---

### Otázka 2 — Proč SQLite a jaké jsou jeho limity?

**Vzorová odpověď:**

> SQLite jsem zvolil, protože:
> - **Nepotřebuje žádný databázový server** — celá DB je jeden soubor `.sqlite`. Pro maturitní projekt to znamená triviální deployment.
> - **Nulová konfigurace** — žádné user/password/port, žádný cron.
> - PHP má **vestavěnou podporu** přes PDO (`PDO('sqlite:...')`), takže nemusím nic instalovat navíc.
> - Pro malou komunitu (desítky až stovky uživatelů) je výkon naprosto dostatečný.
>
> **Limity:**
> - **Souběžné zápisy** — SQLite zamyká celý soubor při zápisu (write-locking na celou databázi). Pro hodně paralelních uživatelů by to bylo úzké hrdlo.
> - **Není určen pro velké provozy** — pro tisíce souběžných uživatelů by bylo nutné přejít na MySQL/PostgreSQL.
> - **Není uzpůsoben pro vzdálený přístup** — funguje jen lokálně na souborovém systému, nelze ho používat z více serverů.
> - **Slabší správa práv** — neexistují DB uživatelé/role tak, jak je má MySQL.

**Kontrolní otázky:**
- Co je **PDO**? *(PHP Data Objects — vrstva pro práci s databázemi, podporuje prepared statements, je DB-nezávislá)*
- Co jsou **prepared statements** a proč jsou důležité? *(předem připravený SQL šablon s parametry — chrání před SQL injection a jsou rychlejší při opakovaném použití)*

---

### Otázka 3 — Jaké bezpečnostní prvky bys doplnil pro reálný provoz?

**Vzorová odpověď (komise miluje sebereflexi):**

> Pro reálný provoz by web potřeboval:
>
> 1. **HTTPS/TLS** — bez šifrované komunikace by hesla a session cookies šly přečíst po síti.
> 2. **CSRF tokeny** ve všech POST formulářích — proti útokům, kdy podvržená stránka pošle požadavek mým jménem.
> 3. **Rate limiting / captcha na login** — proti brute-force hádání hesel.
> 4. **Verifikace e-mailu** při registraci — uživatel musí potvrdit, že e-mail je jeho.
> 5. **HttpOnly + Secure + SameSite flagy na session cookie** — proti XSS a CSRF.
> 6. **Content Security Policy (CSP) hlavička** — proti injekci cizích skriptů.
> 7. **Pravidelné zálohy databáze.**
> 8. **GDPR opatření** — souhlas se zpracováním osobních údajů, možnost smazání účtu, šifrování citlivých údajů v DB.

**Kontrolní otázky:**
- Co je **XSS** a jak se proti němu chráníš? *(Cross-site scripting — útočník vloží JS do obsahu, který se zobrazí dalším uživatelům. Obrana: `htmlspecialchars()` při výpisu uživatelského vstupu.)*
- Co je **SQL Injection**? *(útok, kdy uživatel pošle SQL kód v poli formuláře. Obrana: prepared statements, NIKDY nelepit vstup do SQL stringu.)*

---

### Otázka 4 — Jakou výhodu by mělo použití jiné databáze?

**Vzorová odpověď:**

> **MySQL/MariaDB** by přinesly:
> - Plnou podporu **konkurentních zápisů** od mnoha uživatelů zároveň.
> - **Vzdálený přístup** — databáze může běžet na jiném serveru než aplikace.
> - **Lepší správu uživatelů a práv** (DB role, granularita).
> - **Replikaci a clustering** pro vysokou dostupnost.
> - **Profesionální nástroje** pro správu (phpMyAdmin, MySQL Workbench).
>
> **PostgreSQL** navíc nabízí:
> - Pokročilé datové typy (JSONB, geografická data PostGIS — což by se hodilo pro mapu autosrazů!).
> - Striktnější dodržování SQL standardu.
> - Lepší transakce a integritu dat.
>
> **NoSQL (MongoDB, Redis)** by se hodilo pro:
> - Cache uživatelských session (Redis).
> - Nestrukturovaná data — např. fotky/komentáře k srazům, kde se struktura mění (MongoDB).

**Kontrolní otázky:**
- Rozdíl mezi **SQL a NoSQL**? *(SQL = relační, tabulky se vztahy, SQL jazyk; NoSQL = dokumenty/key-value, flexibilní schéma)*
- Co je **transakce** v databázi? *(ACID — Atomicity/Consistency/Isolation/Durability — operace buď celá projde, nebo se vrátí zpět)*

---

### Otázka 5 — Proč jsi nepoužil moderní framework?

**Vzorová odpověď (toto je trochu obranná otázka — připravit dobrou):**

> Volba čistého PHP byla úmyslná, z pedagogických důvodů:
>
> 1. **Chtěl jsem rozumět tomu, jak weby fungují „pod kapotou".** Frameworky jako Laravel abstrahují routing, ORM, autentizaci, session management. Bez frameworku jsem si toto musel naprogramovat sám a vědět, co se kde děje.
>
> 2. **Velikost projektu to nevyžadovala.** Laravel by pro projekt s 5 stránkami a registrací byl overkill — nainstaloval bych si stovky závislostí přes Composer kvůli funkcím, které nevyužiji.
>
> 3. **Lepší kontrola nad výstupem.** Žádné magické chování, žádné konvence — všechno je explicitní.
>
> 4. **Snadnější nasazení.** Stačí FTP soubory + SQLite, bez nutnosti instalovat Composer/migrace/atd.
>
> **Pokud bych projekt rozšiřoval do produkce, určitě bych přešel na Laravel nebo Symfony** kvůli jejich vyzrálé správě uživatelů, validaci formulářů, migracemi DB a lepší bezpečnosti out-of-the-box.

**Pozor — možné dotazy komise:**
- Konkrétní jméno PHP frameworku? *(Laravel, Symfony, CodeIgniter, Slim)*
- Co je **MVC** a má ho tvůj projekt? *(viz otázka 18 v prep souboru — student by měl vědět; pokud ne, čestně přiznat, že struktura je spíš procedurální / "skripty na stránky")*
- Co je **Composer**? *(package manager pro PHP, instaluje knihovny ze packagist.org)*

---

## 4. Doporučený postup pro konzultaci

**Pokud máme málo času (30–45 min):**
1. Projít kritické problémy (slide 6, 7, 8) — společně přeformulovat texty (15 min)
2. Projít 5 otázek ze slidu 9 — diskuse ke každé, ověřit, že Stefano umí odpovědět (20 min)
3. Pokud zbude čas: slide 5 (Analýza a metody) — doplnit konkrétní detaily

**Pokud máme více času (60–90 min):**
4. + Probrat související maturitní otázku 18 (webové aplikace, HTTP/HTTPS, MVC) — viz `priprava-otazka-18-*.md`
5. + Letmý průchod otázkou 19 (SW inženýrství) — viz `priprava-otazka-19-*.md`

---

## 5. Konkrétní akce pro Stefana po konzultaci

- [ ] Opravit slide 6 — vyhodit šablonový text, doplnit obsah, přejmenovat
- [ ] Opravit slide 7 — totéž, doplnit technickou architekturu projektu
- [ ] Smazat ze slidu 8 placeholder otázku, nahradit textem o osobním přínosu
- [ ] Doplnit do slidu 2 nebo 4 explicitní zmínku o technologiích (PHP, SQLite)
- [ ] Doplnit do slidu 5 konkrétní jména konkurenčních webů, nástroje
- [ ] Zvážit přidání slidu se screenshotem aplikace
- [ ] Zvážit odebrání slidu 9 (otázky) nebo přeformulovat na „Limity projektu a možná rozšíření"
- [ ] Trénovat ústní odpovědi na 5 otázek (nahlas, alespoň 2×)

---

## 6. Poznámky k vystupování (krátké připomenutí)

- **Tempo:** 1 slide ≈ 30–60 s. Při 10 slidech = 5–10 minut celkem — sedí.
- **Oční kontakt s komisí**, ne čtení ze slidu.
- **Mluvit z hlavy**, slide je jen opora.
- **Když nevím:** přiznat a řekněte „v tomto jsem narazil na limit projektu" — lepší než lhát.
- **Otázky komise — vyslechnout celou otázku**, krátce přemýšlet (2–3 s ticha je OK), pak odpovědět.
