# Handout obhajoba — detailní odpovědi na otázky z posudků

**Toto je interní příprava pro Stefana.** Neslouží jako handout pro komisi.
Slouží jako mentální taháky a kontrolní seznam, na co se v Q&A připravit.

---

## Otázka V1 (vedoucí): Jak přesně funguje registrace a přihlášení uživatele včetně uložení hesla do databáze?

### Krátká odpověď (30 s)

> Při registraci uživatel vyplní formulář (jméno, e-mail, heslo). PHP backend nikdy neukládá heslo v čisté podobě — použije funkci `password_hash($heslo, PASSWORD_DEFAULT)`, která interně použije algoritmus **bcrypt** se solí. Do databáze SQLite se uloží jen tento hash, nikdy původní heslo. Při přihlášení backend načte uložený hash a porovná zadané heslo přes `password_verify($zadane, $ulozeny_hash)`. Pokud odpovídá, vytvořím PHP session (`session_start()`) a uložím do ní `user_id`. Session cookie pak prohlížeč posílá při každém dalším požadavku, takže server ví, že je uživatel přihlášený.

### Detailní pochopení (na komisi v rozšiřujících otázkách)

#### 1. Hashování hesla — `password_hash()`
- `password_hash()` je PHP funkce, která hashuje heslo bezpečným algoritmem.
- Výchozí algoritmus = **bcrypt** (od PHP 5.5.0; PHP 7.4+ doporučuje Argon2id, ale my máme bcrypt).
- Automaticky generuje **náhodnou sůl (salt)** pro každé heslo.
- Výsledný hash je řetězec ~60 znaků, který obsahuje algoritmus, cost factor, sůl i hash samotný.
- **Cost factor** (výchozí 10) řídí, jak dlouho hashování trvá — vyšší = pomalejší = bezpečnější proti brute force.

**Příklad výstupu:**
```
$2y$10$N9qo8uLOickgx2ZMRZoMyeIjZAgcfl7p92ldGxad68LJZdL17lhWy
 │   │  │
 │   │  └── sůl + hash
 │   └───── cost factor (2^10 iterací)
 └───────── identifikátor algoritmu ($2y$ = bcrypt)
```

#### 2. Ověření při přihlášení — `password_verify()`
- Funkce vezme zadané heslo + uložený hash a porovná je.
- Vrátí `true` / `false`. Neporovnává hashe — porovnává heslo proti hashi.
- Je **konstantního času** (chrání proti timing útokům).

#### 3. Sessions v PHP
- `session_start()` — inicializuje session na začátku každého skriptu.
- Server vygeneruje **session ID** (např. `kj2h3jkh23j4h2k3j`) a pošle ho prohlížeči jako cookie (`PHPSESSID`).
- Při dalších požadavcích prohlížeč cookie pošle zpět, server podle ID načte data z `$_SESSION`.
- Při loginu uložím: `$_SESSION['user_id'] = $row['id']; $_SESSION['user_name'] = $row['name'];`

#### 4. Co Stefano NEMÁ (a posudek to kritizuje)
- ❌ **CSRF tokeny** — proti útokům, kdy podvržená stránka pošle požadavek mým jménem
- ❌ **`session_regenerate_id(true)`** po loginu — proti session fixation
- ❌ **Validace jedinečnosti e-mailu** — duplicitní registrace
- ❌ **Verifikace e-mailu** (potvrzovací e-mail)
- ❌ **Rate limiting** na login — proti brute force
- ❌ Možná chybí i validace formátu e-mailu (`filter_var($email, FILTER_VALIDATE_EMAIL)`)

### Možné rozšiřující otázky komise

| Otázka komise | Krátká odpověď |
|---------------|----------------|
| Co je **sůl (salt)** a proč? | Náhodný řetězec přidaný k heslu před hashováním. Brání rainbow table útokům — dvě stejná hesla mají různé hashe. |
| Proč ne MD5 nebo SHA-256? | MD5/SHA jsou rychlé, dají se hash crackovat miliardami pokusů za sekundu. Bcrypt je úmyslně pomalý (~100 ms na hash). |
| Co když útočník získá databázi? | Hesla jsou v hashích — nemůže je přečíst. Musel by brute-forcovat každé heslo zvlášť, což je při bcrypt drahé. |
| Co je **prepared statement**? | SQL šablona s placeholdery (`?` nebo `:name`), kam se hodnoty doplní bezpečně přes `bindValue()`/`execute()`. Chrání před SQL injection. |
| Co se stane, když uživatel zavře prohlížeč? | Session cookie je defaultně `session-only` (smaže se), ale data na serveru zůstávají, dokud nevyprší (defaultně 1440 s = 24 min nečinnosti) nebo dokud se nezavolá `session_destroy()`. |

---

## Otázka V2 (vedoucí): Proč SQLite a jaké jsou výhody a limity?

### Krátká odpověď (30 s)

> SQLite jsem zvolil ze tří důvodů: **(1)** nepotřebuje žádný databázový server, celá DB je jeden soubor `.sqlite`, **(2)** nulová konfigurace — žádný user, port, cron, **(3)** PHP má vestavěnou podporu přes PDO bez nutnosti instalovat cokoli navíc. Pro maturitní projekt s malou komunitou je výkon zcela dostatečný.
>
> **Limity:** SQLite zamyká celý soubor při zápisu (write-locking na celou databázi), takže při paralelních zápisech od mnoha uživatelů by to bylo úzké hrdlo. Není určen pro vzdálený přístup — funguje jen lokálně na souborovém systému. A nemá pokročilou správu uživatelů a rolí, kterou má MySQL nebo PostgreSQL.

### Detailní pochopení

#### Výhody SQLite
- **Server-less** — žádný separátní proces, žádné démon
- **Zero-config** — `new PDO('sqlite:./carzmeetz.sqlite')` a funguje
- **Single-file** — celá databáze je jeden soubor, lze ho zazálohovat copy/paste
- **Cross-platform** — stejný soubor funguje na Windows/Linux/Mac
- **Public domain** — bez licence, lze používat kdekoli
- **Embedded** — knihovna se linkuje přímo do aplikace, nepotřebuje TCP/IP
- **Atomic transactions** — implementuje ACID
- Je to **nejrozšířenější databáze na světě** — používá ji Android, iOS, prohlížeče, Firefox, antivirové databáze

#### Nevýhody / limity
| Limit | Co to znamená |
|-------|---------------|
| **Write-locking na celý soubor** | Při zápisu je celá databáze uzamčena pro ostatní zápisy. Více souběžných uživatelů = úzké hrdlo. |
| **Nemá vzdálený přístup** | Funguje jen na souborovém systému, ne přes TCP/IP. Nemůžete mít aplikační server na jednom stroji a SQLite na druhém. |
| **Slabá správa uživatelů a rolí** | Nemá DB users / GRANT — autorizace musí být v aplikaci. |
| **Méně datových typů** | Používá **dynamické typování** (type affinity). Sloupec deklarovaný jako `INTEGER` přijme i text. To může vést k chybám. |
| **Limity na velikost dat** | Max DB size 281 TB, max BLOB 1 GB, max row 1 GB — v praxi neproblém, ale jiné limity (např. `ATTACH DATABASE` max 10) existují. |
| **Méně funkcí než velké RDBMS** | Žádné stored procedures, žádný `RIGHT JOIN` (jen `LEFT JOIN`), žádná replikace |

### Kdy SQLite použít a kdy ne

✅ **SQLite vyhrává:**
- Embedded aplikace (mobil, desktop)
- Cache/lokální data
- Malé weby (návštěvnost < tisíce/den)
- Prototypy a maturitní projekty 😉
- Testing (in-memory DB pomocí `:memory:`)

❌ **SQLite NE:**
- Velké webové aplikace s mnoha souběžnými zápisy
- Aplikace, kde DB běží na jiném serveru než app
- Aplikace, kde potřebujete fine-grained autorizaci na úrovni DB

### Možné rozšiřující otázky komise

| Otázka | Odpověď |
|--------|---------|
| Co je **PDO**? | PHP Data Objects — abstraktní vrstva pro práci s databázemi. Podporuje prepared statements, je DB-nezávislá (stejný kód funguje pro MySQL i SQLite — stačí změnit connection string). |
| Kolik uživatelů SQLite zvládne? | Pro **čtení** klidně desetitisíce souběžných. Pro **zápis** jen jeden naráz, ale zápisy jsou typicky velmi rychlé (ms), takže reálně zvládne desítky až stovky uživatelů. |
| Co je **WAL mode** v SQLite? | Write-Ahead Logging — alternativní zápisový režim, kde se zápisy nejprve píší do log souboru. Umožňuje **paralelní čtení a zápis** (čtenáři nečekají na zápis). Lze zapnout: `PRAGMA journal_mode=WAL;` |
| Co je **ACID**? | Atomicity (vše nebo nic), Consistency (data jsou validní), Isolation (transakce se neovlivňují), Durability (po commitu se data neztratí). SQLite je plně ACID. |

---

## Otázka V3 (vedoucí): Jaké bezpečnostní prvky doplnit pro reálný provoz?

### Krátká odpověď (30 s)

> Pro reálný provoz bych doplnil sedm hlavních prvků: **HTTPS/TLS** (šifrovaná komunikace), **CSRF tokeny** ve všech POST formulářích, **rate limiting** nebo captcha na login proti brute-force, **verifikaci e-mailu** při registraci, **HttpOnly + Secure + SameSite flagy** na session cookie, **Content Security Policy hlavičku** proti XSS, a **pravidelné zálohy databáze**. K tomu GDPR opatření — souhlas se zpracováním osobních údajů, možnost smazání účtu.

### Detailní pochopení

#### 1. HTTPS / TLS
- Bez šifrované komunikace lze přečíst hesla a session cookies po síti (Wi-Fi packet sniffing).
- **Let's Encrypt** poskytuje TLS certifikáty zdarma.
- Většina hostingů (i euweb.cz) HTTPS umožňuje — Stefano si to ověří.

#### 2. CSRF tokeny
- **C**ross-**S**ite **R**equest **F**orgery — útok, kdy podvržená stránka pošle požadavek mým jménem (např. odhlášení nebo změnu e-mailu).
- Obrana: ke každému formuláři vygenerovat náhodný token, uložit do session, ověřit při submitu.
```php
// Při generování formuláře
$_SESSION['csrf_token'] = bin2hex(random_bytes(32));
// V HTML
echo '<input type="hidden" name="csrf" value="' . $_SESSION['csrf_token'] . '">';
// Při zpracování
if (!hash_equals($_SESSION['csrf_token'], $_POST['csrf'])) die('Invalid token');
```

#### 3. Rate limiting / captcha
- Bez ochrany může útočník zkoušet milion hesel za hodinu.
- Možnosti: **počítadlo neúspěšných pokusů** (po 5 → 1 minuta pauza, po 10 → 1 hodina), **reCAPTCHA** od Googlu, **fail2ban** na úrovni serveru.

#### 4. Verifikace e-mailu
- Při registraci poslat token na e-mail, uživatel musí kliknout pro aktivaci účtu.
- Brání spamu falešnými účty a zaručuje, že e-mail je opravdu uživatelův.

#### 5. Cookie flagy
```php
session_set_cookie_params([
    'httponly' => true,    // JavaScript nemá k cookie přístup (proti XSS)
    'secure' => true,      // posílá se jen přes HTTPS
    'samesite' => 'Lax',   // nepošle se z cross-site požadavků (proti CSRF)
]);
```

#### 6. Content Security Policy (CSP)
- HTTP hlavička, která říká prohlížeči, odkud smí načítat skripty/styly/obrázky.
- Brání injekci cizích skriptů (XSS).
```
Content-Security-Policy: default-src 'self'; script-src 'self' https://www.google.com;
```

#### 7. Zálohy
- SQLite je jen jeden soubor — kopírujte ho denně cronem.
- Nestačí nechat ho na produkci, musí být i mimo (offsite backup).

### Bonus: XSS a SQL injection

| Útok | Co to je | Obrana |
|------|----------|--------|
| **XSS** (Cross-site scripting) | Útočník vloží JS kód do obsahu, který se zobrazí dalším uživatelům (např. v komentáři) | `htmlspecialchars($vstup, ENT_QUOTES, 'UTF-8')` při výpisu |
| **SQL Injection** | Útočník pošle SQL kód v inputu, který se nelepený dostane do query | **Prepared statements** s `bindValue()`/`execute()` — Stefano má, **dobře!** |
| **Path traversal** | Útočník zkusí `../../../etc/passwd` v URL | Whitelisting přípustných cest, `realpath()` kontrola |

### Možné rozšiřující otázky komise

- Co je **OWASP Top 10**? *(Open Web Application Security Project — seznam 10 nejčastějších web zranitelností. Injection, broken auth, sensitive data exposure, XSS, CSRF, …)*
- Co je **2FA / MFA**? *(Two-factor / Multi-factor authentication — kromě hesla i druhý faktor: SMS kód, Google Authenticator, hardware token)*

---

## Otázka O1 (oponent): Jakou výhodu by mělo použití jiné databáze?

### Krátká odpověď (30 s)

> **MySQL/MariaDB** by přinesly podporu plně konkurentních zápisů od mnoha uživatelů zároveň, vzdálený přístup po síti, lepší správu uživatelů a rolí, replikaci a clustering pro vysokou dostupnost a profesionální správní nástroje jako phpMyAdmin. **PostgreSQL** navíc nabízí pokročilé datové typy — třeba JSONB pro nestrukturovaná data a PostGIS pro geografická data, což by se u portálu pro autosrazy přímo nabízelo k uchovávání souřadnic míst srazů.

### Detailní pochopení

#### MySQL / MariaDB
- **Pro:** server-based, plně konkurentní zápisy, vyzrálé replikační schopnosti, plná správa uživatelů, široká hostingová podpora
- **Proti:** musí běžet jako separátní proces, nutná konfigurace, hostingy mohou účtovat zvlášť za MySQL

#### PostgreSQL
- **Pro:** striktnější dodržování SQL standardu, lepší transakce, JSONB (nestrukturovaná data v relační DB!), PostGIS (geografická data — perfektní pro mapu autosrazů), generické typy, lepší konkurence
- **Proti:** méně rozšířený mezi sdílenými hostingy než MySQL

#### NoSQL — MongoDB / Redis
- **MongoDB** (document store) — vhodné pro nestrukturovaná data, posty na sociálních sítích, komentáře. Ne náhrada relační DB pro projekt CarzMeetz, ale doplněk.
- **Redis** (key-value, in-memory) — vhodné pro cache, session storage, rate limiting counters. Velmi rychlé čtení/zápis.

### Srovnávací tabulka

| Vlastnost | SQLite | MySQL | PostgreSQL | MongoDB |
|-----------|--------|-------|------------|---------|
| Typ | Embedded | Server | Server | Server |
| Schéma | Relační | Relační | Relační | Dokumentové |
| Konkurentní zápisy | ❌ jeden naráz | ✅ ano | ✅ ano | ✅ ano |
| Vzdálený přístup | ❌ | ✅ | ✅ | ✅ |
| JSON podpora | částečná | ano | **JSONB (indexovaná)** | nativní |
| Geografická data | ne | spatial extension | **PostGIS** | GeoJSON |
| Hodí se pro CarzMeetz? | ✅ maturita | ✅ produkce | ✅✅ produkce (mapy!) | ne primárně |

### Možné rozšiřující otázky

- Rozdíl mezi **SQL a NoSQL**? *(SQL = relační, tabulky s pevným schématem, SQL jazyk; NoSQL = flexibilní schéma, různé modely — dokument/key-value/graf, vlastní API místo SQL)*
- Co je **migrace databáze**? *(Postupné změny schématu pomocí verzovaných skriptů — např. v Laravel přes `php artisan migrate`)*
- Co je **transakce**? *(Posloupnost SQL operací jako jeden atomický celek — ACID)*

---

## Otázka O2 (oponent): Proč není použita žádná moderní knihovna/framework v projektu?

### ⚠️ Toto je nejdůležitější otázka — připravit JISTOU odpověď

### Krátká odpověď (45 s)

> Volba čistého PHP byla úmyslná, ze tří důvodů. **Za prvé:** chtěl jsem rozumět tomu, jak weby fungují „pod kapotou". Frameworky jako Laravel abstrahují routing, ORM, autentizaci a session management — bez nich jsem si to musel naprogramovat sám, takže přesně vím, co se kde děje. **Za druhé:** velikost projektu Laravel ani nevyžadovala. Pro web s pěti stránkami a registrací by Laravel byl overkill — nainstaloval bych si stovky závislostí přes Composer kvůli funkcím, které nevyužiji. **Za třetí:** snazší nasazení — stačí nahrát PHP soubory + SQLite na hosting, žádné `composer install` nebo migrace.
>
> Pokud bych projekt rozšiřoval do produkce, určitě bych přešel na **Laravel** nebo **Symfony** — kvůli jejich vyzrálé autentizaci, validaci formulářů, databázovým migracím a lepší bezpečnosti out-of-the-box. Pro učení a maturitní práci ale bylo čisté PHP správnější volba.

### ⚠️ Pasti, do kterých nespadnout

1. **NEŘÍKAT „Frameworky jsou složité":** zní to jako vyhýbání se. Místo toho říct „pro malý projekt to byl overkill" — to je obhajitelná designová volba.
2. **NEŘÍKAT „Neumím Laravel":** i kdyby to byla pravda, nepřiznávat. Místo toho ukázat, že **vím, co Laravel je a co poskytuje** — to dokazuje rozhled.
3. **NEPLÉST framework × knihovna:**
   - **Knihovna** = řeší jeden problém, vy ji voláte (jQuery, axios)
   - **Framework** = řeší celý projekt, on volá vás (Inversion of Control — Laravel, Symfony, Spring)

### Co Stefano musí vědět o PHP frameworcích

| Framework | Charakteristika | Příklady použití |
|-----------|-----------------|------------------|
| **Laravel** | Nejpopulárnější moderní PHP framework. Elegant syntax. Eloquent ORM, Blade templates, Artisan CLI, Tinker REPL. | Slack, Twitch (částečně), startupy, e-commerce |
| **Symfony** | Robustnější, komponenta-based. Používaný i jako základ pro Laravel (Symfony Components). | Spotify (backend), Trivago, drupal.org |
| **CodeIgniter** | Lehký, jednoduchý, vhodný pro učení. | Menší projekty |
| **Slim** | Mikrorámec pro REST API. | Mikroservices |

### Co je **MVC** a má ho CarzMeetz?

- **Model** = data + business logika (DB queries)
- **View** = prezentace (HTML šablony)
- **Controller** = řídí flow (přijme request, zavolá model, vybere view)

**Stefanův projekt:** Pravděpodobně NEMÁ čisté MVC. PHP skripty často kombinují controller + view (`registrace.php` má jak `<form>` HTML, tak i `if ($_POST) { ... INSERT INTO ... }`). To je **procedurální PHP** (klasický styl "PHP4 web").

Pokud se komise zeptá „máš MVC?", **čestně přiznat:** „Strukturoval jsem to procedurálně — každá stránka je vlastní PHP soubor s HTML i logikou. Pro takový projekt to dává smysl, ale ve frameworku by se to rozdělilo do controllerů a views." To zní mnohem lépe než tvrdit MVC, které tam není.

### Co je **Composer** a **packagist.org**?

- **Composer** = package manager pro PHP, jako `npm` pro JavaScript nebo `pip` pro Python.
- **packagist.org** = veřejný repozitář PHP knihoven.
- `composer require firma/balicek` stáhne balíček a všechny jeho závislosti.

### Možné rozšiřující otázky

- Co znamená **MVC**? *(viz výše)*
- Co je **ORM**? *(Object-Relational Mapping — vrstva, která mapuje DB tabulky na třídy/objekty. Příklad: Eloquent v Laravel, Doctrine v Symfony.)*
- Jaký framework znáš pro JavaScript? *(React, Vue, Angular — frontend; Express, NestJS — backend. Stefano by měl jmenovat alespoň React nebo Vue.)*
- Proč by Laravel byl lepší pro CarzMeetz v produkci? *(Hotová autentizace s `php artisan make:auth`, hotové CSRF tokeny ve formulářích, migrace DB, validace formulářů přes Request třídy, autorizace přes Gate/Policy, queue pro odesílání e-mailů, …)*

---

## Tipy pro Q&A obecně

1. **Pause před odpovědí je OK** — 2–3 sekundy ticha = přemýšlení, ne mlčení.
2. **Když nevím:** „V tomto jsem narazil na limit projektu — neimplementoval jsem to." Nikdy si nevymýšlet.
3. **Krátké odpovědi.** Komise se nudí dlouhými monology. 30–60 s na otázku stačí. Pokud chtějí víc, doptají se.
4. **Když mě komise opraví:** přijmout („Děkuji za upřesnění, máte pravdu") — nepouštět se do hádky.
5. **Když si nejsem jistý termínem:** „Neznám přesný termín, ale princip je takový, že…" — popsat funkci místo slova.

---

## Self-test — Stefano si projde sám před obhajobou

Stefano musí umět odpovědět na tyto kontrolní otázky alespoň jednou větou:

- [ ] Co je bcrypt a proč není MD5?
- [ ] Co je sůl (salt) a k čemu slouží?
- [ ] Co je session a jak funguje session cookie?
- [ ] Co je CSRF token?
- [ ] Co je SQL injection a jak se před ním chráním?
- [ ] Co je XSS a jak se před ním chráním?
- [ ] Co je PDO?
- [ ] Co je prepared statement?
- [ ] Co je HTTPS (TLS) a proč je nutné?
- [ ] Jaký je rozdíl mezi GET a POST?
- [ ] Co je HTTP stavový kód 200, 301, 404, 500?
- [ ] Co je MVC architektura?
- [ ] Co je framework × knihovna?
- [ ] Co je Composer?
- [ ] Co je ORM?
- [ ] Co je ACID v databázích?
- [ ] Co je transakce?
- [ ] Co je relační vs. NoSQL databáze?
- [ ] Co je responzivní web a co znamená mobile-first?
- [ ] Co jsou breakpointy v CSS?

Pokud si na něco z tohoto seznamu **nejsem 100 % jistý**, projít to nahlas s lektorem!
