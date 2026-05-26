# 18. Webové aplikace a redakční systémy

Technicky zpřesněné poznámky ke zkouškovému tématu — **rozšířená verze** s detaily nutnými pro úspěšnou maturitní obhajobu a propojením na projekt CarzMeetz.

---

## 1. Webová stránka vs. web vs. webová aplikace

### Webová stránka

**Webová stránka** je jeden konkrétní dokument nebo pohled dostupný přes URL.

Příklad:

```text
https://firma.cz/o-nas
```

Technicky může být stránka:

- **statický HTML soubor** — server pouze pošle hotový HTML soubor,
- **serverem vygenerovaná HTML stránka** — PHP/ASP.NET/Python/Node.js dynamicky sestaví HTML z databáze (klasický PHP web jako CarzMeetz),
- **stránka vykreslená JavaScriptem v prohlížeči** — Single Page Application (React/Vue/Angular), kde server pošle prázdné HTML + JS bundle, který se v prohlížeči „rozbalí" do uživatelského rozhraní.

### Web

**Web** je skupina souvisejících stránek propojených odkazy, obvykle pod jednou doménou.

Příklad:

```text
https://firma.cz/
https://firma.cz/o-nas
https://firma.cz/sluzby
https://firma.cz/kontakt
```

Typický firemní web hlavně **prezentuje informace**. Uživatel většinou čte obsah, prochází stránky a případně odešle kontaktní formulář.

### Webová aplikace

**Webová aplikace** je aplikace běžící přes prohlížeč, která má vlastní aplikační logiku, stav, uživatelské účty, oprávnění, práci s databází a často i napojení na další systémy.

Příklady:

- internetové bankovnictví,
- e-shop s účtem a objednávkami,
- CRM systém,
- rezervační systém,
- administrační rozhraní CMS,
- klientský portál pojišťovny,
- firemní intranetová aplikace,
- **CarzMeetz** — má registraci, přihlášení, databázi uživatelů a galerie.

### Srovnávací tabulka

| Kritérium | Běžný web | Webová aplikace |
|---|---|---|
| Hlavní účel | prezentace informací | vykonávání funkcí |
| Interakce | nízká | vysoká |
| Uživatelské účty | často ne | často ano |
| Databáze | někdy | téměř vždy |
| Business logika | jednoduchá | výrazná |
| Integrace | minimální | API, ERP, platby, e-mail, sklady |
| Bezpečnostní nároky | běžné | vyšší |
| Vývoj | často šablona/CMS | častěji vývoj na míru |

### Důležitá věta ke zkoušce

> Webová aplikace není jen „hezčí web". Je to **software poskytovaný přes webový prohlížeč**.

### Časté otázky komise

- *Je váš projekt CarzMeetz web, nebo webová aplikace?* → Hybrid — většina stránek je statický prezentační obsah, ale registrace, přihlášení a galerie z DB ho dělají webovou aplikací.
- *Kde je hranice mezi webem a aplikací?* → V přítomnosti uživatelských účtů, databáze a netriviální business logiky.

---

## 2. Frontend

**Frontend** je klientská část aplikace spuštěná v prohlížeči.

Zahrnuje:

- HTML strukturu,
- CSS vzhled,
- JavaScript logiku,
- formuláře,
- validace,
- komponenty,
- volání API,
- práci se stavem aplikace.

### Typický frontend stack

| Vrstva | Technologie |
|---|---|
| Struktura | HTML5 (semantic tags: `<header>`, `<nav>`, `<main>`, `<article>`, `<aside>`, `<footer>`) |
| Vzhled | CSS3, SCSS/SASS, Less, **Tailwind CSS** (utility-first) |
| Interaktivita | JavaScript (ES2015+) / **TypeScript** (staticky typovaný) |
| Frameworky/knihovny | React, Vue, Angular, Svelte, SolidJS |
| Build nástroje | Webpack, Vite, esbuild, Rollup, Parcel |
| Komunikace s backendem | `fetch`, Axios, GraphQL klient (Apollo, urql) |
| Stav aplikace | Redux/Redux Toolkit, Zustand, Pinia, NgRx, Jotai, Recoil |
| Testování | Jest, Vitest, Cypress, Playwright, Testing Library |
| Akcesibilita | ARIA atributy, semantic HTML, screen reader testing |

### Frontend frameworky — krátký rozhled

| Framework | Charakteristika |
|---|---|
| **React** (Meta) | nejpopulárnější, deklarativní, JSX, virtual DOM, komponenty + hooks |
| **Vue** (Evan You) | jednodušší křivka učení, single-file components |
| **Angular** (Google) | full-featured framework, TypeScript-first, RxJS, DI |
| **Svelte/SvelteKit** | compile-time framework, bez runtime — výsledný kód je menší |
| **Next.js** (Vercel) | React framework s SSR/SSG, routing, file-based pages |
| **Nuxt** | Vue ekvivalent Next.js |

Technicky frontend běží v **sandboxu prohlížeče**. Nemá přímý přístup k databázi ani k souborům na serveru. Data získává přes HTTP/HTTPS požadavky, typicky ve formátu JSON.

### Příklad volání API

```js
const response = await fetch("/api/orders/123");
const order = await response.json();
```

### Single Page Application (SPA) vs. Multi-Page Application (MPA)

| Vlastnost | SPA | MPA |
|---|---|---|
| Načítání | jeden HTML soubor + JS bundle | každá stránka má vlastní HTML |
| Navigace | beze refreshe (history API) | full reload |
| SEO | obtížnější (řeší SSR/prerendering) | přirozený, server vrací HTML |
| Rychlost první stránky | pomalejší (JS bundle) | rychlejší |
| Rychlost další navigace | bleskově (jen data) | klasické načítání |
| Příklady | Gmail, Trello, Notion | klasické weby, **CarzMeetz** |

### Server-Side Rendering vs. Client-Side Rendering

- **CSR** (Client-Side Rendering) — server pošle prázdné HTML + JS, JS si vyrenderuje obsah. Lépe pro interakce, hůře pro SEO/první načtení.
- **SSR** (Server-Side Rendering) — server vyrenderuje HTML a pošle hotové, JS pak doplní interaktivitu (hydration). Lépe pro SEO a první načtení.
- **SSG** (Static Site Generation) — HTML se vyrenderuje při buildu, server jen servíruje statiku. Nejrychlejší a nejlevnější.
- **ISR** (Incremental Static Regeneration) — kombinace SSG + průběžné regenerování (Next.js).

### Časté otázky komise

- *Co je responzivní web?* → Web, který se přizpůsobí velikosti obrazovky (mobile/tablet/desktop). Realizuje se přes CSS media queries a fluid layouty (flexbox/grid + `%`/`rem`/`vw` jednotky).
- *Co je mobile-first design?* → CSS se píše nejprve pro mobil, větší breakpointy se přidávají přes `@media (min-width: ...)`.
- *Co jsou breakpointy?* → Hraniční šířky obrazovek, kde se layout mění. Typicky: 576 (mobile L), 768 (tablet), 992 (desktop), 1200 (desktop L).

---

## 3. Backend

**Backend** je serverová část aplikace. Zpracovává požadavky, ověřuje uživatele, provádí business logiku a komunikuje s databází.

Backend řeší například:

- **autentizaci** — kdo to je? (login/heslo, OAuth, SSO)
- **autorizaci** — co smí dělat? (role, permissions, ACL)
- **validaci dat** — vstup z formulářů
- **práci s databází** — CRUD operace přes ORM nebo raw SQL
- **zpracování objednávek** — orchestrace více kroků (rezervace zásob, platba, e-mail)
- **výpočet cen** — daně, slevy, doprava
- **odesílání e-mailů** — transakční (SendGrid, AWS SES) i marketingové
- **napojení na platební brány** — Stripe, GoPay, ComGate
- **logování** — Monolog (PHP), Winston (Node), Serilog (.NET)
- **bezpečnost** — proti SQL injection, XSS, CSRF, brute force
- **API pro frontend** — REST, GraphQL, gRPC, WebSocket

### Typický backend stack

| Vrstva | Příklad |
|---|---|
| Jazyk | PHP, C#, Java, Python, JavaScript/TypeScript, Go, Ruby, Rust |
| Framework | **Laravel** (PHP), **ASP.NET Core** (C#), Spring (Java), Django/FastAPI (Python), Express/NestJS (Node), Rails (Ruby), Gin (Go) |
| Databáze | PostgreSQL, MySQL/MariaDB, MS SQL Server, **SQLite**, MongoDB, Cassandra |
| Cache | Redis, Memcached |
| Fronta | RabbitMQ, Kafka, AWS SQS, Azure Queue Storage, Redis Streams |
| API | REST, GraphQL, gRPC, WebSocket |
| Auth | session cookie, JWT, OAuth2/OIDC, SAML |
| Kontejnerizace | Docker, Kubernetes (k8s) |
| CI/CD | GitHub Actions, GitLab CI, Jenkins, Azure DevOps |

Backend není jen „server". Server může znamenat fyzický nebo virtuální stroj, ale backend je **aplikační software**, který na serveru běží.

### Časté otázky komise

- *Co je business logika?* → Pravidla, podle kterých aplikace zpracovává data. Např. „kniha může být půjčena jen pokud je dostupná" je business logika.
- *Jaký backend máš v CarzMeetz?* → PHP s PDO + SQLite. Bez frameworku, procedurální styl.

---

## 4. Typická komunikace frontend ↔ backend

### Zjednodušený tok

```text
Uživatel
  ↓
Prohlížeč / frontend
  ↓ HTTPS request
Backend API
  ↓
Databáze / externí služby
  ↓
Backend API
  ↓ HTTPS response
Frontend
  ↓
Zobrazení výsledku
```

### Příklad: přihlášení v CarzMeetz

1. Uživatel zadá e-mail a heslo do formuláře v `register.php`.
2. JavaScript `fetch('login.php')` odešle data přes POST.
3. `login.php` načte uživatele přes PDO + prepared statement.
4. Backend ověří heslo přes `password_verify()`.
5. Při úspěchu se vytvoří PHP session, do ní se uloží `user_id`.
6. Odpověď se vrátí textově (success/error message).
7. JavaScript zobrazí výsledek v `<p id="loginMessage">`.

### Obecný princip: stateless HTTP

HTTP je **bezstavový protokol** — server po každém požadavku „zapomene", kdo byl klient. Aby si server pamatoval, kdo je přihlášený, používá se jedna z těchto technik:

| Technika | Princip | Použití |
|---|---|---|
| **Cookies + Session** | server vygeneruje session ID, pošle jako cookie, server si data drží v paměti | klasické weby (CarzMeetz) |
| **JWT** (JSON Web Token) | server podepíše token s claims, klient ho posílá v Authorization hlavičce | SPA + REST API, mobilní aplikace |
| **OAuth 2.0** | autorizace pomocí přístupových tokenů od poskytovatele identity | „Login with Google/Facebook" |

---

## 5. HTTP technicky

**HTTP** (HyperText Transfer Protocol) je aplikační protokol pro komunikaci mezi klientem a serverem. Funguje stylem **request-response**, tedy požadavek a odpověď. Pracuje na **TCP** portu **80** (HTTP) nebo **443** (HTTPS).

### Verze HTTP

| Verze | Rok | Klíčové vlastnosti |
|---|---|---|
| HTTP/1.0 | 1996 | jedno spojení = jeden request |
| HTTP/1.1 | 1997 | keep-alive (více requestů na jedno spojení), chunked transfer, hostname header |
| HTTP/2 | 2015 | binary protokol, multiplexing (více requestů paralelně), header compression, server push |
| HTTP/3 | 2022 | běží nad QUIC (ne TCP), nižší latence, vestavěné TLS |

### HTTP request

HTTP požadavek obsahuje:

```http
GET /produkty/15 HTTP/1.1
Host: example.com
Accept: text/html
Cookie: sessionId=abc123
User-Agent: Mozilla/5.0 ...
```

Části požadavku:

| Část | Význam |
|---|---|
| Metoda | co klient chce udělat |
| URL/path | s čím chce pracovat |
| Headers | metadata požadavku |
| Body | data požadavku, hlavně u `POST`, `PUT`, `PATCH` |

### HTTP response

HTTP odpověď může vypadat takto:

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 38
Set-Cookie: sessionId=abc123; HttpOnly; Secure

{
  "id": 15,
  "name": "Produkt"
}
```

Části odpovědi:

| Část | Význam |
|---|---|
| Status code | výsledek požadavku |
| Headers | metadata odpovědi |
| Body | HTML, JSON, obrázek, soubor apod. |

### Metody HTTP — detailněji

| Metoda | Technický význam | Idempotentní? | Cachovatelná? | Body? |
|---|---|---|---|---|
| `GET` | načtení dat | ✅ ano | ✅ ano | ne |
| `POST` | vytvoření / akce | ❌ ne | ne | ano |
| `PUT` | kompletní nahrazení zdroje | ✅ ano | ne | ano |
| `PATCH` | částečná změna | ❌ ne | ne | ano |
| `DELETE` | smazání zdroje | ✅ ano | ne | volitelně |
| `HEAD` | jen hlavičky bez body | ✅ ano | ✅ ano | ne |
| `OPTIONS` | dotaz na podporované metody | ✅ ano | ne | ne |

> **Idempotentní operace** = lze ji provést opakovaně se stejným výsledkem (např. nastavit `PUT /users/1 {name: "Ano"}` 10× je stejné jako 1×). `POST` typicky idempotentní není (vytváří nové záznamy).

### Stavové kódy — kompletní přehled

**1xx — Informational**
- `100 Continue` — pokračuj v posílání requestu

**2xx — Success**
- `200 OK` — požadavek proběhl úspěšně
- `201 Created` — nový zdroj byl vytvořen (`POST`/`PUT`)
- `204 No Content` — úspěch, ale není co vracet (typicky `DELETE`)

**3xx — Redirection**
- `301 Moved Permanently` — trvalé přesměrování (cachováno, SEO)
- `302 Found` — dočasné přesměrování
- `304 Not Modified` — klient má aktuální verzi v cache

**4xx — Client Error**
- `400 Bad Request` — špatný požadavek (chybný JSON, špatné parametry)
- `401 Unauthorized` — neověřený uživatel (chybí přihlášení)
- `403 Forbidden` — ověřený, ale nemá oprávnění
- `404 Not Found` — zdroj neexistuje
- `405 Method Not Allowed` — metoda není pro tento endpoint povolena (např. `DELETE` na `/users` listu)
- `409 Conflict` — konflikt stavu (např. duplikát e-mailu)
- `422 Unprocessable Entity` — validační chyba
- `429 Too Many Requests` — rate limit

**5xx — Server Error**
- `500 Internal Server Error` — neočekávaná chyba serveru
- `502 Bad Gateway` — proxy dostala chybu od upstream serveru
- `503 Service Unavailable` — server je dočasně nedostupný (údržba, přetížení)
- `504 Gateway Timeout` — proxy nedostala odpověď včas

### Hlavičky — nejdůležitější

**Request:**
- `Host` — doména
- `User-Agent` — identifikace prohlížeče
- `Accept` — jaký formát klient přijímá (`text/html`, `application/json`)
- `Authorization` — token nebo Basic auth
- `Cookie` — session ID a další
- `Content-Type` — formát body (`application/json`, `application/x-www-form-urlencoded`)

**Response:**
- `Content-Type` — formát body odpovědi
- `Content-Length` — velikost body
- `Set-Cookie` — nastav cookie
- `Cache-Control` — pravidla cachování (`no-store`, `max-age=3600`)
- `Location` — kam přesměrovat (s 3xx kódy)
- `X-Frame-Options`, `Content-Security-Policy` — bezpečnostní hlavičky

### Časté otázky komise

- *Rozdíl GET a POST?* → GET v URL (idempotentní, cachable, v historii), POST v body (změny stavu, není v URL).
- *Co je idempotence?* → Stejný request 10× = stejný výsledek jako 1×.
- *Jaký status kód při validační chybě?* → `400 Bad Request` nebo lépe `422 Unprocessable Entity`.
- *Co je `Cache-Control: no-store`?* → Cache to neukládá nikam (nutné pro citlivá data, autentizační tokeny).

---

## 6. HTTPS technicky

**HTTPS** (HTTP Secure) je HTTP zabezpečené pomocí **TLS** (Transport Layer Security, dříve SSL). TLS šifruje komunikaci mezi klientem a serverem a chrání ji před odposlechem a změnou po cestě.

### Co HTTPS zajišťuje

| Vlastnost | Význam |
|---|---|
| **Šifrování** | útočník nevidí obsah komunikace |
| **Integrita** | útočník nemůže nepozorovaně měnit data |
| **Autentizace serveru** | prohlížeč ověřuje certifikát domény (klient ví, že komunikuje s pravou doménou) |

### TLS handshake (zjednodušeně)

1. Klient: `ClientHello` — podporované šifrovací sady, náhodné číslo
2. Server: `ServerHello` — vybraná šifrovací sada, **certifikát**, náhodné číslo
3. Klient: ověří certifikát proti **Certificate Authority (CA)**
4. Klient + server si **vymění klíčový materiál** (asymetrické šifrování — RSA/ECDH)
5. Z klíčového materiálu se vygeneruje **symetrický klíč** pro session
6. Další komunikace už je šifrovaná symetricky (rychlejší než asymetrická)

### Typy TLS certifikátů

| Typ | Kdo si může objednat | Cena |
|---|---|---|
| **DV** (Domain Validation) | kdokoli s kontrolou nad doménou | zdarma (Let's Encrypt), nebo levné |
| **OV** (Organization Validation) | firmy, CA ověří identitu | placené |
| **EV** (Extended Validation) | firmy s extra kontrolou, zelený řádek v prohlížeči (dřív) | nejdražší |

> **Let's Encrypt** je nezisková CA, která poskytuje DV certifikáty zdarma a automaticky obnovované. Stalo se to standardem.

### Důležité zpřesnění

> HTTPS neznamená, že aplikace je automaticky bezpečná. Znamená pouze, že **transport** mezi klientem a serverem je šifrovaný.

Aplikace stále může mít chyby jako:

- SQL injection,
- XSS,
- slabá hesla,
- špatná oprávnění,
- únik dat,
- špatně nastavené cookies.

### Bezpečnostní HTTP hlavičky

| Hlavička | Účel |
|---|---|
| `Strict-Transport-Security` (HSTS) | klient musí pro tuto doménu vždy používat HTTPS |
| `Content-Security-Policy` (CSP) | omezí, odkud lze načítat skripty/styly/obrázky (proti XSS) |
| `X-Frame-Options` | brání vložení stránky do `<iframe>` (proti clickjacking) |
| `X-Content-Type-Options: nosniff` | brání MIME type sniffingu |
| `Referrer-Policy` | kontroluje, co se odesílá v Referer hlavičce |

### Časté otázky komise

- *Rozdíl SSL a TLS?* → SSL je starší protokol (SSL 2.0, 3.0 — dnes nepoužívané). TLS je modernější (TLS 1.0, 1.1, 1.2, 1.3 — dnes standard je 1.2 a 1.3). Lidé říkají „SSL", ale myslí TLS.
- *Co je Let's Encrypt?* → Nezisková CA poskytující TLS certifikáty zdarma + automatizovaný protokol ACME pro jejich obnovu.
- *Má CarzMeetz HTTPS?* → Pravděpodobně ano (euweb.cz typicky poskytuje Let's Encrypt). Stefano si ověří.

---

## 7. FTP, FTPS, SFTP

**FTP** (File Transfer Protocol) je protokol pro přenos souborů mezi klientem a serverem. Pracuje na **TCP** portech **20** (data) a **21** (řízení).

### Použití

- nahrání HTML/CSS/PHP souborů na webhosting,
- stažení záloh,
- správa souborů na serveru.

### Active vs. passive mode

| Mode | Komunikace |
|---|---|
| **Active** | klient otevře port pro server, server se k němu připojí — problémy za firewallem |
| **Passive** | klient se sám připojuje k serveru (oba kanály iniciuje klient) — funguje lépe |

### Varianty

| Protokol | Port | Šifrování | Popis |
|---|---|---|---|
| **FTP** | 20/21 | ❌ čistý text | starší přenos souborů, dnes nedoporučovaný |
| **FTPS** | 21 (explicit) / 990 (implicit) | ✅ TLS | FTP doplněné o TLS, podobný princip jako HTTPS |
| **SFTP** | 22 | ✅ SSH | přenos souborů přes SSH tunel, **technicky nejde o FTP** — je to subsystém SSH |
| **SCP** | 22 | ✅ SSH | nejjednodušší kopírování přes SSH |

> **SFTP ≠ FTPS!** SFTP je SSH File Transfer Protocol (jiný protokol pod SSH), FTPS je FTP over TLS.

### Klienti pro upload

- **FileZilla** — GUI, free, FTP/FTPS/SFTP
- **WinSCP** — Windows, GUI, SCP/SFTP/FTP
- **Cyberduck** — macOS/Windows, FTP/SFTP/S3/cloud storage
- **lftp** — CLI, skriptovatelné

### Moderní alternativy k FTP

Dnes se u profesionálních projektů často nepoužívá ruční FTP upload, ale spíše:

- **Git** + webhooky (Vercel, Netlify deploy on push)
- **CI/CD pipeline** (GitHub Actions, GitLab CI) — automatický build a deploy
- **Docker image** + push do registry
- **Rsync** přes SSH — efektivní synchronizace souborů
- **Cloud hosting** (AWS S3 + CloudFront, Vercel, Netlify)

### Časté otázky komise

- *Jak nahráváš změny na CarzMeetz?* → Pravděpodobně FTP přes FileZilla nebo PhpStorm vestavěný FTP klient (na euweb.cz).
- *Co je rozdíl FTPS a SFTP?* → FTPS = FTP přes TLS (port 21). SFTP = file transfer subsystém SSH (port 22). Oba šifrují, ale jiné protokoly.

---

## 8. MVC architektura

**MVC** znamená **Model–View–Controller**. Jde o **architektonický vzor**, který odděluje uživatelské rozhraní, data a aplikační logiku.

### Historie a kontext

MVC vymyslel **Trygve Reenskaug** v roce 1979 ve Smalltalk-80 pro desktop aplikace. Pro web ho zpopularizoval framework **Ruby on Rails** (2005) a od té doby je MVC dominantní vzor v server-side webových frameworcích (Laravel, Django, ASP.NET MVC, Spring MVC).

### Komponenty

| Část | Technická role |
|---|---|
| **Model** | data, doménové objekty, pravidla, práce s databází |
| **View** | zobrazení dat uživateli (HTML šablona) |
| **Controller** | přijme request, zavolá logiku, vybere response |

### Typický průběh v MVC

```text
HTTP request
  ↓
Router          (najde, který Controller a metoda má request zpracovat)
  ↓
Controller      (zpracuje request, validuje, volá Service/Model)
  ↓
Service / Model (business logika + DB)
  ↓
Database
  ↓
Controller      (převezme data)
  ↓
View / JSON     (vyrenderuje response)
  ↓
HTTP response
```

### Příklad v Laravelu

```php
// routes/web.php
Route::get('/products/{id}', [ProductController::class, 'show']);

// app/Http/Controllers/ProductController.php
class ProductController {
    public function show($id) {
        $product = Product::find($id);       // Model
        return view('products.show', [        // View
            'product' => $product
        ]);
    }
}

// app/Models/Product.php
class Product extends Model {
    protected $table = 'products';
}

// resources/views/products/show.blade.php
<h1>{{ $product->name }}</h1>
<p>{{ $product->description }}</p>
```

### Varianty MVC

- **MVP** (Model-View-Presenter) — Presenter má víc kontroly nad View; používá se v desktopu (WinForms) a Androidu.
- **MVVM** (Model-View-ViewModel) — ViewModel exponuje data jako observable property, View se na ně bindujе (data binding). Používá se v WPF, SwiftUI, Vue.js, Knockout.js.
- **Flux/Redux** — unidirectional data flow v React (action → reducer → store → view).

### Moderní hybridní architektura

U moderních aplikací se MVC často kombinuje s API přístupem:

```text
Frontend React/Vue/Angular
  ↓
REST API / GraphQL
  ↓
Backend services
  ↓
Database
```

Backend často nevrací HTML, ale **JSON**.

### Má CarzMeetz MVC?

**NE — CarzMeetz je psaný procedurálně, ne podle MVC.**

V projektu:
- Každá stránka (`index.php`, `srazy.php`, `galerie.php`, …) kombinuje HTML šablonu + PHP logiku v jednom souboru.
- `register.php` má `<form>` HTML i `INSERT INTO users …` v jednom souboru.
- Není router (URL = jméno PHP souboru).
- Není separátní Model vrstva (DB queries jsou rovnou v PHP skriptu).
- Není Controller (žádné explicitní oddělení request handlingu od view).

To **není chyba** — pro maturitní projekt to dává smysl. Ale je to **omezení**, na které by Stefano měl umět odpovědět.

### Časté otázky komise

- *Co znamená MVC?* → Model-View-Controller. Architektonický vzor pro oddělení datové vrstvy, prezentační vrstvy a řídicí logiky.
- *Má tvůj projekt MVC?* → Procedurální PHP, kombinuje view a controller v jednom souboru. Pro malou aplikaci to stačí, ale ve frameworku jako Laravel by se to rozdělilo.
- *Jaké výhody by mělo MVC pro CarzMeetz?* → Snazší testování (oddělitelná business logika), znovupoužitelnost (jeden Model může obsluhovat web i API), oddělení rolí v týmu (designer × backend dev).

---

## 9. REST API a další API styly

### REST — REpresentational State Transfer

**REST** je architektonický styl pro webové API, který používá HTTP metody pro práci se **zdroji** (resources). Definoval ho Roy Fielding v dizertační práci 2000.

### Principy REST

1. **Stateless** — server si nepamatuje předchozí requesty, každý je samostatný.
2. **Zdroje (resources)** mají URL — `/users/15`, `/users/15/orders`.
3. **HTTP metody** popisují operace:
   - `GET /users` — seznam
   - `GET /users/15` — detail
   - `POST /users` — vytvořit nového
   - `PUT /users/15` — kompletní update
   - `PATCH /users/15` — částečný update
   - `DELETE /users/15` — smazat
4. **JSON** jako primární formát dat.
5. **Status kódy** popisují výsledek.
6. **Hypermedia** (HATEOAS) — odpovědi mohou obsahovat odkazy na další akce.

### Příklad REST API

```http
GET /api/users/15
Accept: application/json
```

Odpověď:
```json
{
  "id": 15,
  "name": "Stefano",
  "email": "stefano@example.com",
  "_links": {
    "orders": "/api/users/15/orders"
  }
}
```

### Alternativy k REST

| Styl | Charakteristika |
|---|---|
| **GraphQL** (Meta) | jeden endpoint, klient si vyžádá přesně co potřebuje, řeší over/under-fetching |
| **gRPC** (Google) | binární protokol nad HTTP/2, schema definované v `.proto`, rychlý a typovaný — pro mikroservices |
| **SOAP** | starší, XML-based, formálně specifikovaný (WSDL) — dnes hlavně v enterprise/bankovnictví |
| **WebSocket** | obousměrná dlouhodobá komunikace (chat, live updates, notifikace) |
| **Server-Sent Events (SSE)** | jednosměrná streamovaná data od serveru klientu |

### CORS — Cross-Origin Resource Sharing

Když JavaScript na `example.com` volá API na `api.example.com`, prohlížeč to defaultně **blokuje** (Same-Origin Policy). Server musí poslat hlavičku:

```http
Access-Control-Allow-Origin: https://example.com
```

a u kontextu s cookies i:
```http
Access-Control-Allow-Credentials: true
```

### Časté otázky komise

- *Co je REST API?* → Architektonický styl pro web API, používá HTTP metody pro práci se zdroji.
- *Co je JSON?* → JavaScript Object Notation, textový formát pro výměnu dat. Lidsky čitelný, méně overhead než XML.
- *Co je idempotence v API?* → Stejný request → stejný výsledek (GET, PUT, DELETE jsou idempotentní; POST typicky ne).

---

## 10. Autentizace a autorizace

### Autentizace × autorizace

- **Autentizace** (authentication) = „kdo jsi?" — ověření identity (heslo, biometrika, token)
- **Autorizace** (authorization) = „co smíš?" — kontrola oprávnění (role, permissions)

### Mechanismy autentizace

#### 1. Session-based (cookies)

Klasika pro server-side weby:

```text
1. Klient: POST /login {username, password}
2. Server: ověří, vygeneruje session ID, uloží do paměti
3. Server: Set-Cookie: PHPSESSID=abc123
4. Klient: další requesty posílají PHPSESSID
5. Server: podle ID najde session v paměti
```

**Pro:** Snadné v PHP (`session_start()`), funguje out-of-the-box.
**Proti:** Server musí držet session v paměti, problém u horizontálního škálování (sticky sessions / Redis session store).

CarzMeetz používá tento přístup (PHP session v `login.php`).

#### 2. JWT (JSON Web Token)

Token-based, stateless:

```text
1. Klient: POST /login
2. Server: ověří, vytvoří JWT podepsaný svým klíčem
3. Server: vrátí token v body odpovědi
4. Klient: další requesty posílají Authorization: Bearer <token>
5. Server: ověří podpis tokenu, věří jeho obsahu (claims)
```

**JWT struktura:** `header.payload.signature` (base64 encoded JSON parts)

**Pro:** Stateless (server si nic nepamatuje), škálovatelné, vhodné pro mikroservices a SPA.
**Proti:** Není snadno revokovat, většinou nutná expirace + refresh token.

#### 3. OAuth 2.0 / OpenID Connect

Pro „login přes Google / Facebook / GitHub":

```text
1. Klient klikne „Login with Google"
2. Redirect na Google login
3. Google ověří uživatele
4. Google vrátí authorization code do callback URL
5. Server vymění code za access token
6. Server získá user info pomocí tokenu
7. Server vytvoří lokální session/JWT
```

**OAuth 2.0** = autorizace (přístup k zdrojům).
**OpenID Connect** (OIDC) = vrstva nad OAuth pro autentizaci (kdo to je).

#### 4. Multi-factor Authentication (MFA / 2FA)

Druhý faktor kromě hesla:
- SMS kód
- TOTP aplikace (Google Authenticator, Authy)
- Hardware token (YubiKey)
- Push notifikace (Microsoft Authenticator)

### Mechanismy autorizace

| Model | Princip |
|---|---|
| **Role-Based Access Control (RBAC)** | uživatel má roli, role má oprávnění (Admin, Editor, Viewer) |
| **Attribute-Based Access Control (ABAC)** | rozhodnutí na základě atributů uživatele + zdroje + kontextu |
| **Access Control List (ACL)** | každý zdroj má seznam uživatelů s povolenými operacemi |

### Časté otázky komise

- *Jaký rozdíl autentizace a autorizace?* → Autentizace = kdo jsi (heslo), autorizace = co smíš (role).
- *Co je JWT?* → Podepsaný token s claims, server ho ověřuje podpisem, ne uložením v DB.
- *Má CarzMeetz role / oprávnění?* → Ne, všichni přihlášení uživatelé mají stejná oprávnění.

---

## 11. Redakční systém — CMS

**CMS** (Content Management System) je systém pro správu obsahu. Umožňuje vytvářet, upravovat, organizovat a publikovat obsah **bez přímého programování**.

CMS je technicky většinou webová aplikace, která má:

- administraci (admin rozhraní),
- databázi obsahu,
- systém uživatelů a rolí,
- šablony vzhledu (themes),
- správu médií,
- pluginy/moduly,
- workflow publikace (draft → review → published).

### Typická architektura CMS

```text
Admin uživatel
  ↓
CMS administrace
  ↓
Databáze obsahu
  ↓
Šablonovací systém
  ↓
Veřejný web
```

### Důležité vlastnosti CMS

- **WYSIWYG editor** (What You See Is What You Get) — vizuální editor obsahu
- **Verze obsahu** — historie změn, možnost rollback
- **Plánování publikace** — článek se zveřejní v určitý čas
- **Custom Post Types / Content Types** — vlastní typy obsahu (např. produkty, akce, zaměstnanci)
- **Taxonomie / Kategorie / Tagy** — organizace obsahu
- **Multilanguage** — vícejazyčný obsah (i18n / l10n)
- **SEO funkce** — meta tagy, sitemap, friendly URLs
- **REST API** — moderní CMS exponují obsah přes API (headless)

---

## 12. Představitelé CMS

### Klasické (monolitické) CMS

| CMS | Technická charakteristika |
|---|---|
| **WordPress** | PHP CMS, šablony, pluginy, databáze MySQL/MariaDB. **~43 % všech webů světa.** Snadná instalace, obří ekosystém. |
| **Drupal** | PHP, robustní CMS s důrazem na strukturovaný obsah a oprávnění. Vhodný pro velké portály a vládní weby. |
| **Joomla** | PHP, univerzální CMS, historicky populární. Méně rozšířený než WordPress. |
| **Typo3** | PHP, populární v Německu pro enterprise weby. |
| **Ghost** | Node.js CMS, zaměřený na blogy a publikace, čistý UI. |
| **Wagtail** | Python/Django CMS, oblíbený pro vývojářsky orientované weby. |

### E-commerce platformy (specializované CMS)

| Platforma | Charakteristika |
|---|---|
| **Shopify** | SaaS, hosted e-shop, jednoduchá administrace |
| **WooCommerce** | WordPress plugin pro e-shop |
| **Magento (Adobe Commerce)** | enterprise e-commerce |
| **PrestaShop** | open-source e-commerce |

### No-code / WYSIWYG nástroje

| Nástroj | Charakteristika |
|---|---|
| **Webflow** | vizuální editor pro responzivní weby, generuje čistý HTML/CSS |
| **Wix** | drag-and-drop site builder |
| **Squarespace** | premium templates, jednodušší než WP |

### Headless CMS

| CMS | Charakteristika |
|---|---|
| **Strapi** | Node.js, open-source, sám si hostujete |
| **Contentful** | cloudový headless CMS, enterprise |
| **Sanity** | strukturovaná data, real-time API |
| **Storyblok** | visual editor + headless |
| **Directus** | open-source, automaticky generuje API ze SQL databáze |

### WordPress detailně (nejčastěji se ptají)

- **Jazyk:** PHP
- **Databáze:** MySQL / MariaDB
- **Šablony:** PHP soubory v `wp-content/themes/`
- **Pluginy:** PHP soubory v `wp-content/plugins/`
- **Klíčové APIs:** Hooks (`add_action`, `add_filter`), WP_Query, Custom Post Types, REST API
- **Admin:** `/wp-admin/`
- **Hlavní soubory:** `wp-config.php` (konfigurace), `index.php` (entry point), `functions.php` (theme logic)

### Časté otázky komise

- *Proč WordPress nejpopulárnější?* → Free, open source, obří komunita, tisíce témat a pluginů, jednoduchá instalace.
- *Mohl bys CarzMeetz udělat ve WordPressu?* → Ano, ale ztratil bych kontrolu nad architekturou. WP je vhodný pro obsahové weby, ne pro custom aplikace.

---

## 13. Klasické CMS vs. headless CMS

### Klasické CMS

Klasické CMS řeší **najednou**:

- administraci,
- ukládání obsahu,
- šablony,
- veřejné stránky.

Příklad:

```text
WordPress admin → databáze → PHP šablona → HTML stránka
```

**Výhody:**
- rychlé vytvoření webu,
- méně vývoje,
- dobré pro firemní weby, blogy a menší projekty,
- velký ekosystém pluginů.

**Nevýhody:**
- složitější oddělení frontend/backend části,
- rizika u pluginů (kvalita, bezpečnost, kompatibilita),
- někdy horší škálování a bezpečnost při špatné správě,
- obsah těžko reuse mimo web (mobil, IoT).

### Headless CMS

Headless CMS spravuje **pouze obsah** a poskytuje ho přes API.

```text
CMS admin
  ↓
API (REST/GraphQL)
  ↓
Frontend web / mobilní aplikace / smart TV / IoT
```

**Výhody:**
- **jeden obsah pro web, mobilní aplikaci i další kanály** (omnichannel),
- frontend může být v Reactu, Vue, Next.js apod.,
- větší flexibilita,
- nezávislost CMS na frontendu.

**Nevýhody:**
- složitější vývoj (musíte si frontend napsat),
- vyšší nároky na architekturu,
- často dražší řešení.

### Hybrid CMS

Kompromis — CMS umí servírovat HTML stránky **i** exponovat REST API. **WordPress** je díky `wp-json/` REST API de facto hybridní (lze ho použít headless).

### Časté otázky komise

- *Kdy bys volil headless?* → Když má obsah být v mobilní aplikaci, smart TV, IoT, nebo když mám oddělené frontend a backend týmy.
- *Kdy klasický CMS?* → Pro klasické weby, blogy, malé firmy, kde stačí jeden frontend.

---

## 14. Technicky přesná odpověď ke zkoušce

> **Webová aplikace** je softwarový systém dostupný přes webový prohlížeč. Na rozdíl od běžného informačního webu neprezentuje pouze statický obsah, ale umožňuje uživateli aktivně pracovat s daty, přihlašovat se, měnit nastavení, vytvářet objednávky nebo komunikovat s dalšími systémy. Typicky se skládá z **frontendu**, který běží v prohlížeči, a **backendu**, který běží na serveru, zpracovává požadavky, komunikuje s databází a vykonává aplikační logiku. Komunikace probíhá pomocí protokolu **HTTP**, v praxi zabezpečeně přes **HTTPS** s TLS. Pro přenos souborů na server se historicky používalo FTP, dnes bezpečněji **SFTP, FTPS** nebo automatizované nasazení přes CI/CD. Častou architekturou webových aplikací je **MVC**, které odděluje model, view a controller, případně novější API-based architektura, kde backend exponuje REST nebo GraphQL API a frontend je samostatná SPA. **Redakční systém** neboli **CMS** je speciální typ webové aplikace určený ke správě obsahu, například WordPress, Drupal nebo headless CMS jako Strapi či Contentful.

---

# 19. Softwarové inženýrství

Technicky zpřesněné poznámky ke zkouškovému tématu — **rozšířená verze** s detaily nutnými pro úspěšnou maturitní obhajobu.

---

## 1. Co řeší softwarové inženýrství

**Softwarové inženýrství** (Software Engineering, SE) není jen psaní kódu. Je to **řízený proces tvorby softwaru** — disciplína, která využívá inženýrské principy (analýza, návrh, ověření) na vývoj software.

Pojem zavedla konference NATO v Garmisch-Partenkirchen v roce 1968 jako reakci na **„softwarovou krizi"** — fakt, že tehdejší projekty často přesahovaly rozpočty, časy nebo vůbec selhaly.

### Typický životní cyklus

```text
požadavky → návrh → implementace → testování → nasazení → provoz → údržba
```

### Cílem je dodat software, který je

- **funkční** — dělá to, co má
- **bezpečný** — chrání data a uživatele
- **udržovatelný** — lze ho efektivně rozšiřovat a opravovat
- **testovatelný** — lze ověřit, že funguje
- **výkonný** — rychlý a efektivní
- **použitelný** — uživatelé se v něm vyznají
- **rozšiřitelný** — lze přidávat funkce bez kompletního přepisu
- **přenositelný** — funguje na různých platformách

---

## 2. Životní cyklus softwaru (SDLC)

Životní cyklus softwaru (**Software Development Life Cycle, SDLC**) popisuje fáze, kterými software prochází od nápadu až po vyřazení.

### Fáze SDLC

| Fáze | Co se děje |
|---|---|
| **Analýza požadavků** | zjištění, co systém má dělat — funkční + nefunkční požadavky |
| **Návrh řešení** | architektura, databáze, obrazovky, API, technologický stack |
| **Implementace** | programování aplikace |
| **Testování** | ověření funkčnosti a kvality (unit, integration, system, acceptance) |
| **Nasazení** | uvedení do provozu (deployment, deploy) |
| **Provoz** | monitoring, podpora uživatelů |
| **Údržba** | opravy chyb, drobná vylepšení, bezpečnostní záplaty |
| **Vyřazení** (decommissioning) | nahrazení nebo ukončení provozu |

### SDLC modely

#### Vodopád (Waterfall)

Sekvenční model — každá fáze se dokončí, než začne další.

```text
Analýza → Návrh → Implementace → Testování → Nasazení → Údržba
```

**Pro:** jasná struktura, dokumentace, vhodné pro projekty s pevnými požadavky (státní zakázky, embedded software, lékařské systémy).
**Proti:** nereaguje na změny, chyby v rané fázi se draze opravují později.

#### V-model

Rozšíření vodopádu — každá vývojová fáze má odpovídající testovací fázi.

```text
Požadavky         ↔  Akceptační testy
   ↓                       ↑
Analýza/Design    ↔  Systémové testy
   ↓                       ↑
Modul. design     ↔  Integrační testy
   ↓                       ↑
Implementace      → Unit testy
```

**Pro:** systematické testování, vhodné pro safety-critical systémy (letectví, medicína).
**Proti:** stejné nevýhody jako vodopád.

#### Iterativní

Vývoj v menších iteracích — postupně se zlepšuje produkt.

#### Inkrementální

Vývoj po částech — postupně se přidávají funkce, každá je sama o sobě funkční.

#### Spirálový (Boehm)

Kombinace iterativního přístupu s důrazem na **řízení rizik**. Každá spirála = další iterace s analýzou rizik.

#### Agile

Iterativní + inkrementální + flexibilní reakce na změny — detailně níže.

### Srovnávací tabulka

| Model | Pro | Proti |
|---|---|---|
| Vodopád | Pevné požadavky, dokumentace, audit | Nereaguje na změny, pozdní feedback |
| V-model | Důraz na testování, safety-critical | Stejně rigidní jako vodopád |
| Iterativní | Postupné zlepšování | Nutná průběžná validace |
| Spirálový | Řízení rizik, velké projekty | Komplexní, drahé |
| Agile/Scrum | Reakce na změny, rychlá dodávka | Vyžaduje disciplínu, hůře plánovat dlouhodobě |

### Časté otázky komise

- *Jakým modelem jsi vyvíjel CarzMeetz?* → Spíš vodopádem — postupné fáze (analýza, design, implementace, test, nasazení), jak je v slidu 3 prezentace.
- *Co je největší slabina vodopádu?* → Pozdní feedback — chyby zjištěné při testování stojí mnohem víc, než kdyby se odhalily při analýze.

---

## 3. Agilní vývoj

**Agilní vývoj** znamená, že se software nevytváří celý najednou podle pevného plánu, ale **postupně v menších iteracích** s důrazem na pravidelnou zpětnou vazbu.

### Agile Manifesto (2001)

V roce 2001 sepsalo 17 vývojářů v Snowbird, Utah, **Agile Manifesto**:

> **Hodnoty:**
> 1. **Jednotlivce a interakce** před procesy a nástroji
> 2. **Funkční software** před vyčerpávající dokumentací
> 3. **Spolupráci se zákazníkem** před vyjednáváním smluv
> 4. **Reakci na změnu** před následováním plánu

Plus **12 principů** (např. „Naší nejvyšší prioritou je uspokojit zákazníka rychlým a průběžným dodáváním hodnotného softwaru.").

### Typický rozdíl

| Tradiční přístup (vodopád) | Agilní přístup |
|---|---|
| vše se naplánuje dopředu | plán se průběžně upravuje |
| dodání až na konci | dodávání po částech |
| horší reakce na změny | lepší reakce na zpětnou vazbu |
| dlouhá analýza | kratší iterace |
| pevný scope, flexibilní čas | flexibilní scope, pevný čas |

### Hlavní principy agilního vývoje

- častá komunikace se zákazníkem,
- krátké vývojové cykly,
- rychlá zpětná vazba,
- možnost měnit požadavky,
- průběžné dodávání funkčního softwaru,
- self-organizing týmy,
- pravidelná retrospektiva a zlepšování.

### Agilní metodiky a frameworky

| Metodika | Charakteristika |
|---|---|
| **Scrum** | nejrozšířenější, sprinty 1–4 týdny, role + události |
| **Kanban** | vizualizace toku, WIP limity |
| **XP (Extreme Programming)** | pair programming, TDD, refactoring, continuous integration |
| **Lean Software Development** | inspirace z Toyota Production System (eliminace plýtvání) |
| **Feature-Driven Development (FDD)** | iterace okolo features |
| **Scaled Agile Framework (SAFe)** | škálování agile na úroveň firmy (release trains, ARTs) |
| **LeSS (Large Scale Scrum)** | škálovaný Scrum pro velké organizace |
| **DSDM** | Dynamic Systems Development Method |

---

## 4. Scrum

**Scrum** je jedna z nejznámějších agilních metodik. Pracuje v krátkých časových úsecích — **sprintech** — obvykle 1 až 4 týdny dlouhých.

Vznik: **Jeff Sutherland** a **Ken Schwaber**, 1995. Aktuální verze: **Scrum Guide 2020**.

### Role ve Scrumu

| Role | Úkol |
|---|---|
| **Product Owner (PO)** | spravuje priority produktu a backlog, je „hlas zákazníka" |
| **Scrum Master (SM)** | pomáhá týmu dodržovat proces, odstraňuje překážky (impediments), kouč týmu |
| **Developers** | sebeorganizující tým vytvářející produktový increment (3–9 členů) |

### Scrum artefakty

| Artefakt | Co je |
|---|---|
| **Product Backlog** | prioritizovaný seznam všeho, co má být uděláno (PBI — Product Backlog Items, často „user stories") |
| **Sprint Backlog** | podmnožina PB pro aktuální sprint + plán, jak to udělat |
| **Increment** | dokončená, použitelná funkce — musí být v **„Done"** stavu (splňovat Definition of Done) |

### Scrum události (ceremonies)

| Událost | Trvání (pro 1měsíční sprint) | Význam |
|---|---|---|
| **Sprint Planning** | max 8 h | plánování práce na sprint — co a jak |
| **Daily Scrum** (standup) | 15 min/den | krátká denní synchronizace — co jsem dělal včera / dělám dnes / blockers |
| **Sprint Review** | max 4 h | ukázka výsledku stakeholderům + získání feedbacku |
| **Sprint Retrospective** | max 3 h | reflexe týmu — co fungovalo, co změnit |

### Definition of Done (DoD)

Seznam kritérií, kdy je práce „hotová". Typicky:
- kód napsaný + code review
- unit testy projdou
- integration testy projdou
- code coverage > X %
- dokumentace aktualizována
- nasaditelné na produkci

### Story points

Místo odhadu v hodinách se používají **story points** — relativní velikost úkolu. Tým hraje **Planning Poker** (každý hodí kartu s odhadem, diskutuje, znovu hodí). Tipicky Fibonacciho posloupnost: 1, 2, 3, 5, 8, 13.

### Velocity

Průměrný počet story points dokončených za sprint. Pomáhá plánovat budoucí sprinty.

### Časté otázky komise

- *Jaká je role Scrum Mastera?* → Není manažer, je facilitátor a kouč. Pomáhá týmu odstraňovat překážky.
- *Co je sprint?* → Časově ohraničená iterace (1–4 týdny), po jejím konci je hotový increment.
- *Co je Daily Standup?* → 15min denní setkání týmu — synchronizace, blockers, plán dne.

---

## 5. Kanban

**Kanban** je agilní metoda založená na **vizualizaci práce** a **omezení rozpracovanosti** (Work-In-Progress limits). Vznikla z Toyota Production System (60. léta), pro software ji upravil **David J. Anderson** kolem 2010.

### Klíčové principy

1. **Vizualizuj práci** — Kanban board (fyzický nebo digitální)
2. **Omez WIP** — počet úkolů v každém sloupci je limitován (např. max 3 v In Progress)
3. **Řiď tok** — sleduj cycle time, throughput, blockers
4. **Explicitní pravidla** — co znamená každý sloupec, kdy úkol může přejít dál
5. **Feedback loops** — pravidelné review
6. **Postupné zlepšování** (kaizen)

### Typická tabule

| Backlog | To Do | In Progress (WIP ≤ 3) | Review (WIP ≤ 2) | Done |
|---|---|---|---|---|
| nové nápady | připraveno k práci | rozpracované úkoly | čeká na review | hotovo |

### Metriky Kanbanu

- **Cycle Time** — jak dlouho úkol jde od „In Progress" do „Done"
- **Lead Time** — jak dlouho jde od „Backlog" do „Done"
- **Throughput** — kolik úkolů dokončíme za týden/měsíc
- **WIP** — kolik je aktuálně rozpracováno

### Kanban vs. Scrum

| Vlastnost | Scrum | Kanban |
|---|---|---|
| Iterace | sprinty (1–4 týdny) | kontinuální tok |
| Role | PO, SM, Devs | nepředepisuje |
| Plánování | Sprint Planning | průběžně |
| Změny v iteraci | omezené | povoleno |
| Vhodné pro | produktový vývoj | provoz, podpora, údržba |

### Příklady použití Kanbanu

- technická podpora (incident management),
- údržba systému,
- opravy chyb,
- menší průběžné úpravy,
- hardwarový tým (kde sprinty nedávají smysl).

---

## 6. Extreme Programming (XP) a další praktiky

**Extreme Programming (XP)** je agilní metodika zaměřená na **inženýrské praktiky**. Autor: **Kent Beck**, 1996. Klíčové praktiky:

| Praktika | Co to je |
|---|---|
| **Pair Programming** | dva programátoři u jednoho počítače — jeden píše, druhý reviewuje |
| **Test-Driven Development (TDD)** | nejdřív test, pak kód (red-green-refactor) |
| **Continuous Integration** | každý commit se automaticky buildne a otestuje |
| **Refactoring** | průběžné zlepšování kódu bez změny funkčnosti |
| **Simple Design** | YAGNI — „You Aren't Gonna Need It", KISS — „Keep It Simple, Stupid" |
| **Small Releases** | časté nasazování malých změn |
| **Collective Ownership** | každý může editovat jakýkoli kód |
| **Coding Standards** | jednotný styl kódu |

---

## 7. Testování softwaru

Testování ověřuje, zda software splňuje požadavky a neobsahuje kritické chyby.

### Typy testů

| Typ testu | Co ověřuje |
|---|---|
| **Unit test** | jednu funkci, metodu nebo třídu — izolovaně, často s mocky |
| **Integration test** | spolupráci více částí systému (např. controller + DB) |
| **System test** / E2E | celý systém jako celek (Selenium, Cypress, Playwright) |
| **Acceptance test (UAT)** | zda systém splňuje požadavky zákazníka |
| **Regresní test** | zda nová změna nerozbila staré funkce |
| **Smoke test** | rychlý test, že nejzákladnější věci fungují (typicky po deployu) |
| **Performance / Load test** | rychlost a chování při zatížení (JMeter, k6, Gatling) |
| **Stress test** | jak se systém chová pod extrémním zatížením |
| **Security test** | zranitelnosti, oprávnění a ochranu dat (OWASP ZAP, Burp Suite) |
| **Usability test** | jak snadno se systém používá (s reálnými uživateli) |

### Testovací pyramida (Mike Cohn)

```text
        ▲
       /│\
      /E│E\         <- Málo, drahé, pomalé, ale realistické
     /─┴─\
    /Integr.\
   /─────────\
  /  Unit     \    <- Hodně, rychlé, levné, izolovaná logika
 /─────────────\
```

Doporučení: **70 % unit, 20 % integration, 10 % E2E**.

Opačný „cone shape" (málo unit, hodně E2E) je antipattern — testy jsou pomalé, křehké a drahé.

### Black-box vs. white-box

- **Black-box testing** — tester nezná vnitřní implementaci, testuje vstup → výstup. Vhodné pro acceptance testy.
- **White-box testing** — tester zná kód, testuje vnitřní cesty. Typické pro unit testy.

### Test-Driven Development (TDD)

Cyklus **Red-Green-Refactor**:

```text
1. RED      — napíšu test, který selže (kód ještě neexistuje)
2. GREEN    — napíšu minimální kód, aby test prošel
3. REFACTOR — vyčistím kód bez změny funkčnosti
```

### Behavior-Driven Development (BDD)

Rozšíření TDD — testy se píší jako **chování v přirozeném jazyce** (Gherkin):

```gherkin
Feature: Login
  Scenario: Successful login
    Given I am on the login page
    When I enter valid credentials
    Then I should see the dashboard
```

Nástroje: Cucumber (Java/Ruby), SpecFlow (.NET), Behat (PHP).

### Code Coverage

Procento řádků kódu pokrytých testy. Měření přes PHPUnit + Xdebug, Istanbul (JS), JaCoCo (Java). Pozor: **100 % coverage ≠ kvalitní testy** (mohou testovat triviálně).

### Testovací nástroje

| Jazyk | Unit/integration | E2E |
|---|---|---|
| PHP | PHPUnit, Pest | Codeception, Cypress |
| JavaScript/TS | Jest, Vitest, Mocha | Cypress, Playwright, Puppeteer |
| Java | JUnit, TestNG | Selenium |
| C# (.NET) | xUnit, NUnit, MSTest | Selenium, Playwright |
| Python | pytest, unittest | Selenium, Playwright |

### Příklad u e-shopu

- **Unit:** funkce `calculateDiscount(price, percent)` vrátí správnou hodnotu
- **Integration:** vložení produktu do košíku správně zapíše do DB
- **System (E2E):** uživatel projde celým checkout flow (košík → adresa → platba → potvrzení)
- **Performance:** při 1000 souběžných uživatelů odezva pod 500 ms
- **Security:** SQL injection v search formuláři není možný

### Časté otázky komise

- *Jak jsi testoval CarzMeetz?* → Manuálně — proklikal jsem všechny stránky, vyzkoušel registraci, login. Žádné automatizované testy.
- *Co je code coverage?* → Procento kódu pokrytého testy. Cíl ~70–80 %, ale kvalita testů je důležitější než procento.
- *Co je rozdíl mezi unit a integration testem?* → Unit testuje jednu funkci v izolaci (s mocky), integration testuje spolupráci více částí.

---

## 8. Issue tracking systémy

**Issue tracking systém** (bug tracker, task tracker) slouží k evidenci práce, chyb a požadavků.

### K čemu slouží

- sledovat, co je potřeba udělat,
- kdo na tom pracuje,
- v jakém je úkol stavu,
- jaká je priorita,
- jaké chyby byly nalezeny,
- jak spolu úkoly souvisí (parent/child, blocker, related),
- historie změn (audit log),
- komunikace v rámci úkolu (komentáře).

### Příklady systémů

| Systém | Popis |
|---|---|
| **Jira** (Atlassian) | nejrozšířenější v enterprise, podporuje Scrum, Kanban, custom workflows |
| **YouTrack** (JetBrains) | issue tracker s integrací do JetBrains IDE |
| **GitHub Issues** | úkoly přímo u GitHub repozitářů, integrované s pull requesty |
| **GitLab Issues** | úkoly propojené s GitLab projekty, integrace s CI/CD |
| **Azure DevOps Boards** | Microsoft, integrace s Azure |
| **Linear** | moderní, rychlý, populární u startupů |
| **Trello** | jednodušší Kanban styl |
| **Asana** | task management, project management |
| **Redmine** | open-source, populární u OSS projektů |
| **Bugzilla** | klasický bug tracker (Mozilla) |
| **ClickUp** | all-in-one |

### Typická pole issue

| Pole | Význam |
|---|---|
| **Summary** | krátký název („Login button doesn't work") |
| **Description** | detailní popis problému/požadavku, kroky k reprodukci |
| **Type** | Bug / Feature / Task / Story / Epic |
| **Assignee** | řešitel |
| **Reporter** | kdo issue vytvořil |
| **Priority** | Lowest / Low / Medium / **High** / Critical / Blocker |
| **Severity** | Trivial / Minor / Major / Critical / Blocker |
| **State** | Open / In Progress / Review / Done / Closed |
| **Labels/Tags** | štítky pro kategorizaci |
| **Sprint** | zařazení do iterace |
| **Story Points** | odhad velikosti |
| **Components** | která část systému je dotčena |
| **Affected Version** | ve které verzi se objevila |
| **Fix Version** | ve které verzi bude opravena |
| **Comments** | komunikace |
| **Attachments** | screenshoty, logy |
| **Links** | vazby na jiné issue (blocks, blocked by, relates to, duplicates) |

### Typické stavy issue

```text
Open → To Do → In Progress → Review → Testing → Done → Closed
                                ↓
                            Reopened (vrátí se zpět)
```

### Vazba Git ↔ Issue

V profesionálním vývoji se issue tracker propojuje s Git:

- **Commit message** zmiňuje issue: `git commit -m "Fix login button — closes #123"`
- **Pull Request** odkazuje na issue: PR description „Closes #123"
- Po mergi se issue automaticky uzavře.

### Časté otázky komise

- *Použil jsi nějaký issue tracker?* → Pravděpodobně Stefano ne (samostatný malý projekt). Mohl by říct, že znal princip a vedl si jen TODO seznam v texťáku.
- *Co je rozdíl bug × feature × task?* → Bug = oprava, Feature = nová funkce, Task = obecný úkol (technický, dokumentace).

---

## 9. Verzování kódu — Git

> Není přímo v zadání otázky 19, ale s issue trackingem a CI/CD souvisí — komise se může zeptat.

**Git** je distribuovaný systém pro verzování kódu (DVCS), vytvořil ho **Linus Torvalds** v 2005 pro vývoj Linuxového jádra. Dnes je standardem.

### Klíčové pojmy

| Pojem | Význam |
|---|---|
| **repository** (repo) | celý projekt + historie |
| **commit** | jedna změna v historii (snímek stavu) |
| **branch** | větev — paralelní linie vývoje |
| **merge** | spojení dvou větví |
| **rebase** | přepsání historie větve (sjednocení s jinou) |
| **pull** | stažení změn z remote |
| **push** | nahrání lokálních commitů na remote |
| **clone** | stažení celého repa z remote |
| **HEAD** | aktuální commit |
| **remote** | vzdálený repozitář (GitHub, GitLab, Bitbucket) |

### Git workflows

| Workflow | Princip |
|---|---|
| **GitHub Flow** | jedna `main` + krátkodobé feature branches, PR + merge |
| **Git Flow** (Vincent Driessen) | `main` + `develop` + `feature/*` + `release/*` + `hotfix/*` |
| **Trunk-Based Development** | každý pracuje přímo na `main`, krátké branches, feature flags |

### Hosting

- **GitHub** (Microsoft) — největší, OSS i privátní
- **GitLab** — self-hosted i cloud, integrované CI/CD
- **Bitbucket** (Atlassian) — integrace s Jirou

---

## 10. CI/CD — Continuous Integration & Continuous Delivery/Deployment

**CI/CD** je praktika automatizovaného buildu, testování a nasazování softwaru.

### Continuous Integration (CI)

Při každém commitu se automaticky:
1. Stáhne kód
2. Zkompiluje / nainstalují závislosti
3. Spustí unit + integration testy
4. Spustí statickou analýzu (linter, security scan)
5. Pokud cokoli selže → notifikace týmu

### Continuous Delivery (CD)

Po úspěšném CI je build **připraven k nasazení** — lze ho jedním kliknutím nasadit na produkci.

### Continuous Deployment

Po úspěšném CI se build **automaticky** nasadí na produkci — žádné lidské schválení.

### CI/CD nástroje

| Nástroj | Charakteristika |
|---|---|
| **GitHub Actions** | nativní v GitHubu, YAML workflows |
| **GitLab CI/CD** | nativní v GitLabu, `.gitlab-ci.yml` |
| **Jenkins** | klasický, on-premise, plugin ecosystem |
| **CircleCI** | cloud-based |
| **TeamCity** (JetBrains) | enterprise |
| **Azure DevOps Pipelines** | Microsoft |
| **Bitbucket Pipelines** | Atlassian |

### Příklad GitHub Actions workflow

```yaml
name: CI
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '20'
      - run: npm ci
      - run: npm test
      - run: npm run lint
```

### Časté otázky komise

- *Co je CI/CD?* → Automatizovaný build, test a nasazení. Cíl: rychlá zpětná vazba, žádné „funguje u mě".
- *Jaký rozdíl Continuous Delivery a Deployment?* → Delivery = připraveno k nasazení, ale nutné kliknout. Deployment = nasazuje se automaticky.

---

## 11. Kvalita softwaru

Kvalita softwaru se neposuzuje jen podle toho, zda program „funguje".

### ISO/IEC 25010 — model kvality softwaru

Mezinárodní norma (dříve ISO 9126) definuje **8 hlavních charakteristik kvality**:

| Charakteristika | Subcharakteristiky |
|---|---|
| **Funkční vhodnost** (Functional Suitability) | úplnost, správnost, vhodnost |
| **Výkonnostní efektivita** (Performance Efficiency) | doba odezvy, využití prostředků, kapacita |
| **Kompatibilita** | koexistence, interoperabilita |
| **Použitelnost** (Usability) | rozpoznatelnost vhodnosti, naučitelnost, ovladatelnost, ochrana před uživatelskými chybami, estetika, přístupnost |
| **Spolehlivost** (Reliability) | zralost, dostupnost, odolnost proti chybám, obnovitelnost |
| **Bezpečnost** (Security) | důvěrnost, integrita, neodmítnutelnost, odpovědnost, autenticita |
| **Udržovatelnost** (Maintainability) | modulárnost, znovupoužitelnost, analyzovatelnost, modifikovatelnost, testovatelnost |
| **Přenositelnost** (Portability) | adaptabilita, instalovatelnost, nahraditelnost |

### Technické aspekty kvality v praxi

| Aspekt | Význam | Příklad metriky |
|---|---|---|
| Funkčnost | software dělá to, co má | pokrytí požadavků (%) |
| Spolehlivost | stabilní provoz bez pádů | počet incidentů, uptime (% dostupnosti) |
| Výkon | rychlost a kapacita | odezva API (ms), requesty za sekundu |
| Bezpečnost | ochrana dat a přístupů | počet zranitelností (CVE) |
| Použitelnost | uživatel se v aplikaci vyzná | chybovost uživatelů, NPS, UX testy |
| Udržovatelnost | kód lze opravovat a rozšiřovat | cyklomatická složitost, code review feedback |
| Testovatelnost | systém lze dobře ověřit | pokrytí testy (%), počet testů |
| Škálovatelnost | zvládne více uživatelů nebo dat | výkon při zátěži |
| Přenositelnost | lze provozovat v různých prostředích | podpora OS/cloudů |

### Funkční vs. nefunkční požadavky

- **Funkční požadavky** — *co* systém dělá (uživatel se přihlásí, vytvoří objednávku)
- **Nefunkční požadavky** — *jak* systém funguje (rychlost odezvy < 200 ms, uptime > 99,9 %, dostupnost ve 3 jazycích)

### Technický dluh (Technical Debt)

Termín od **Warda Cunninghama** (1992). Analogicky k finančnímu dluhu — když píšeme „rychle a špinavě", půjčujeme si na budoucnost. **Úroky** platíme zpomalením vývoje, zvýšenou pravděpodobností chyb, obtížnější údržbou.

Strategie:
- **Dělat pravidelný refactoring** (~20 % času na úklid).
- **Code review** odhalí dluh včas.
- **Statická analýza** (SonarQube) měří kvalitu kódu.

### Code Review

Kontrola kódu jiným vývojářem před mergem do hlavní větve. Slouží k:
- odhalení chyb,
- sdílení znalostí v týmu,
- udržení coding standards,
- konzistenci architektury.

Typicky pomocí **Pull Request (PR)** / **Merge Request (MR)**.

### Statická analýza kódu

Nástroje, které analyzují kód bez spuštění:
- **SonarQube** — komplexní platforma pro kvalitu kódu, bezpečnost
- **ESLint** (JS), **Prettier** (formátování)
- **PHP_CodeSniffer**, **PHPStan**, **Psalm** (PHP)
- **Pylint**, **Black** (Python)
- **StyleCop**, **ReSharper** (C#)

### Refactoring

Zlepšování struktury kódu **bez změny funkčnosti**. Klasická kniha: Martin Fowler — *Refactoring: Improving the Design of Existing Code* (1999).

Příklady:
- Extract Method
- Rename Variable
- Move Function
- Replace Conditional with Polymorphism

### Příklad

> Aplikace může mít hezký vzhled, ale pokud často padá, je pomalá a není bezpečná, **není kvalitní**.

### Časté otázky komise

- *Co je ISO 25010?* → Norma pro kvalitu softwaru. 8 charakteristik: funkčnost, výkon, kompatibilita, použitelnost, spolehlivost, bezpečnost, udržovatelnost, přenositelnost.
- *Co je technický dluh?* → Nahromaděné technické problémy v kódu, které zpomalují další vývoj a zvyšují pravděpodobnost chyb.
- *Co je code review?* → Kontrola kódu jiným vývojářem před mergem, slouží k odhalení chyb a sdílení znalostí.

---

## 12. Jak se kvalita posuzuje v praxi

Kvalitu lze hodnotit například podle:

- **počtu chyb** (defects per KLOC — chyb na 1000 řádků kódu),
- **rychlosti odezvy** (response time, latency),
- **výsledků testů** (test pass rate, code coverage),
- **bezpečnostních auditů** (penetration testing, OWASP scan),
- **spokojenosti uživatelů** (NPS — Net Promoter Score, CSAT),
- **čitelnosti kódu** (code review feedback, static analysis score),
- **kvality dokumentace** (úplnost, aktuálnost),
- **dostupnosti systému** (uptime — 99.9 % = „three nines" = max 8.76 h výpadku/rok; 99.99 % = „four nines" = 52 min/rok),
- **snadnosti dalšího vývoje** (time to deploy new feature),
- **úspěšnosti nasazení** (deployment success rate, MTTR — Mean Time To Recover),
- **počtu incidentů v produkci** (P1, P2, P3 severity).

### SLA / SLO / SLI

- **SLI** (Service Level Indicator) — měřená metrika (např. response time)
- **SLO** (Service Level Objective) — interní cíl (např. response time < 200 ms v 99 % případů)
- **SLA** (Service Level Agreement) — smluvní závazek se zákazníkem (např. uptime 99.9 % s pokutou při porušení)

---

## 13. DevOps a SRE

> Pravděpodobně nebude v zadání, ale komise se může zeptat na trendy.

### DevOps

**DevOps** = kombinace **Dev**elopment + **Op**erations. Filozofie sblížení vývoje a provozu, automatizace deploymentu, monitoring, infrastructure as code (IaC).

Klíčové praktiky:
- **CI/CD**
- **Infrastructure as Code** (Terraform, Ansible, Pulumi)
- **Monitoring & observability** (Prometheus, Grafana, ELK stack, Datadog)
- **Containerization** (Docker, Kubernetes)
- **Microservices**

### SRE (Site Reliability Engineering)

Disciplína vyvinutá v Googlu. Aplikuje softwarové inženýrství na operations. Klíčové koncepty:
- **Error budgets** — kolik výpadku si můžeme dovolit
- **Toil reduction** — automatizace repetitivní práce
- **Postmortems** — analýza incidentů bez vinění

---

## 14. Technicky přesná odpověď ke zkoušce

> **Softwarové inženýrství** je systematický přístup k vývoji softwaru, který využívá inženýrské principy na celý životní cyklus produktu. Zahrnuje **analýzu požadavků** (funkční i nefunkční), **návrh architektury**, **implementaci**, **testování** (unit, integrační, systémové, akceptační), **nasazení** a **údržbu**. Moderní vývoj často využívá **agilní metodiky**, například **Scrum** nebo **Kanban**, které pracují s iteracemi, průběžnou zpětnou vazbou a prioritizací backlogu. **Testování** ověřuje funkčnost, integraci, výkon, bezpečnost a splnění požadavků, často podle testovací pyramidy (převažují unit testy). **Issue tracking systémy** jako Jira, YouTrack nebo GitHub Issues slouží ke správě úkolů, chyb a změn, přičemž se propojují s Git verzováním. **Kvalita softwaru** se hodnotí podle ISO 25010 — funkčnost, spolehlivost, výkon, bezpečnost, použitelnost, udržovatelnost, kompatibilita a přenositelnost. V praxi se kombinuje s **CI/CD automatizací**, **code review**, **statickou analýzou** a měřením metrik (test coverage, uptime, MTTR), aby tým dodával funkční, bezpečný a udržovatelný software.

---

# 20. Aplikace teorie na projekt CarzMeetz

Tato sekce propojuje teorii ze sekcí 18 a 19 s **konkrétním kódem projektu CarzMeetz** (Stefano Battistuzzi, maturita 2025/2026). Slouží jako mentální „lepidlo" mezi obecnou teorií a tím, co u zkoušky uvedu z vlastní práce.

## 20.1 Architektura CarzMeetz

```text
┌─────────────────────────────────────────────┐
│           Prohlížeč (klient)                │
│  - HTML + CSS (global.css + per-page.css)   │
│  - JS: hamburger menu, fetch() na login     │
└─────────────────────────────────────────────┘
                    ↓ HTTP(S)
┌─────────────────────────────────────────────┐
│          Webhosting euweb.cz                │
│  - PHP runtime (PHP 7.x/8.x)                │
│  - jednotlivé .php soubory:                 │
│    index.php, srazy.php, galerie.php,       │
│    about.php, kontakt.php,                  │
│    register.php, login.php, hamburger.php   │
└─────────────────────────────────────────────┘
                    ↓ PDO
┌─────────────────────────────────────────────┐
│         SQLite databáze (soubory)           │
│  - users.db       (uživatelé)               │
│  - gallery.sqlite (galerie obrázků)         │
│  - database.db    (nevyužitý?)              │
└─────────────────────────────────────────────┘
```

**Architektura je procedurální PHP, ne MVC.** Každá `.php` stránka kombinuje HTML view + business logiku v jednom souboru.

## 20.2 Co projekt skutečně implementuje

### Frontend (klientská část)
- ✅ HTML5 + semantic tagy (`<header>`, `<nav>`, `<section>`, `<footer>`)
- ✅ CSS3 — vlastní styly, mobile-first responzivní design
- ✅ Google Fonts (Orbitron, Inter) přes CDN
- ✅ Hamburger menu pro mobil — vanilla JavaScript (`hamburger.php`)
- ✅ Viewport meta tag pro responzivitu
- ⚠️ Inline `<style>` v `hamburger.php` — porušuje doporučení „no inline CSS"
- ⚠️ Inline `style="..."` atributy v `index.php` na několika místech

### Backend (serverová část)
- ✅ PHP procedurální (čisté PHP, žádný framework)
- ✅ PDO + SQLite — moderní a bezpečný DB přístup
- ✅ `password_hash($password, PASSWORD_DEFAULT)` — bcrypt s automatickou solí
- ✅ `password_verify()` — bezpečné porovnání hesel
- ✅ **Prepared statements** s `bindValue()` — ochrana před SQL injection
- ✅ `htmlspecialchars()` na výstupu — ochrana před XSS
- ✅ `session_start()` v `login.php` — vytváří PHP session po loginu
- ❌ **Žádný `logout.php`** — uživatel se nemůže odhlásit
- ❌ **Žádné `session_regenerate_id(true)`** po loginu — riziko session fixation
- ❌ **Žádný CSRF token** v žádném formuláři
- ❌ **Žádná validace duplicitního e-mailu/username** — spoléhá na UNIQUE constraint v DB (catch v PDOException)
- ❌ **Žádná verifikace e-mailu** při registraci
- ❌ **Žádný rate limiting** na login (proti brute-force)
- ❌ **Žádná stránka chráněna autentizací** — i přihlášený uživatel nemá nic „víc"
- ❌ **`db_users.php` je nepoužívaný legacy soubor** (41 bytů, používá `SQLite3` API místo PDO)

### Datová vrstva
- ✅ SQLite — embedded databáze v souboru
- ⚠️ **Tři DB soubory**: `users.db`, `gallery.sqlite`, `database.db` — proč ne jeden?
- ❌ Schema není v repozitáři (musí být v `.sql` migracích nebo CREATE TABLE statements někde)

### Co projekt nemá vůbec
- ❌ **Žádné dynamické srazy** — `srazy.php` je čistě statický HTML
- ❌ **Žádný upload obrázků do galerie** — galerie jen čte existující záznamy
- ❌ **Žádná správa profilu uživatele** — uživatel se přihlásí a... nic
- ❌ **Žádný kontaktní formulář** — `kontakt.php` má jen odkaz na Instagram
- ❌ Žádný framework, žádný build krok, žádné testy

## 20.3 Konkrétní ukázky kódu vs. teorie

### Ukázka 1: Bcrypt hashování (sekce HTTP/HTTPS/bezpečnost)

`register.php`:
```php
$passwordHash = password_hash($password, PASSWORD_DEFAULT);
$stmt = $db->prepare("INSERT INTO users (...) VALUES (..., :password)");
$stmt->bindValue(':password', $passwordHash, PDO::PARAM_STR);
$stmt->execute();
```

`login.php`:
```php
if (password_verify($password, $user['password_hash'])) {
    $_SESSION['user_id'] = $user['id'];
}
```

**Co o tom říct komisi:**
> „Hesla nikdy neukládám v plaintextu. Při registraci je hashuji funkcí `password_hash()`, která použije bcrypt s automaticky generovanou solí. Při loginu pak `password_verify()` v konstantním čase porovná zadané heslo s uloženým hashem."

### Ukázka 2: Prepared statements (sekce bezpečnost / SQL injection)

`login.php`:
```php
$stmt = $db->prepare("
    SELECT id, username, email, password_hash
    FROM users
    WHERE username = :ue OR email = :ue
");
$stmt->bindValue(':ue', $usernameOrEmail, PDO::PARAM_STR);
$stmt->execute();
```

**Co o tom říct komisi:**
> „Všechny SQL dotazy používají prepared statements s pojmenovanými parametry. To znamená, že uživatelský vstup se nikdy nelepí přímo do SQL stringu — místo toho se posílá jako parametr přes `bindValue()`. Tím se eliminuje riziko SQL injection."

### Ukázka 3: AJAX login přes fetch() (sekce frontend/backend komunikace)

`register.php`:
```html
<form id="loginForm">
    <input type="text" name="usernameOrEmail" ...>
    <input type="password" name="password" ...>
    <button type="submit">Přihlásit se</button>
</form>

<script>
document.getElementById('loginForm').addEventListener('submit', function (e) {
    e.preventDefault();
    const formData = new FormData(this);
    fetch('login.php', { method: 'POST', body: formData })
        .then(response => response.text())
        .then(data => {
            document.getElementById('loginMessage').innerText = data;
        });
});
</script>
```

**Co o tom říct komisi:**
> „Přihlašovací formulář používá `fetch` API — JavaScript zachytí submit, pošle data na `login.php` přes POST, a odpověď zobrazí bez celkového reloadu stránky. Je to drobná ukázka dynamičnosti, kterou bych ve full SPA frameworku rozšířil na celou aplikaci."

### Ukázka 4: Responzivní hamburger menu (sekce frontend / mobile-first)

`hamburger.php` (zkrácena):
```css
@media (max-width: 768px) {
    .mobile-menu-toggle { display: block; }
    nav { position: fixed; right: -280px; transition: right 0.3s ease; }
    nav.mobile-menu-open { right: 0; }
}
```

**Co o tom říct komisi:**
> „Mobilní menu se zobrazuje pod 768 pixelů šířky — to je breakpoint pro tablety. Menu sjíždí zprava pomocí CSS transition. Toggle button má `aria-label` pro screen reader accessibility."

### Ukázka 5: Galerie čte z DB (sekce databáze)

`galerie.php`:
```php
$pdo = new PDO("sqlite:" . $dbPath);
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
$stmt = $pdo->query("SELECT id, name, image_path FROM gallery ORDER BY id DESC");
$results = $stmt->fetchAll(PDO::FETCH_ASSOC);
```

**Co o tom říct komisi:**
> „Galerie je dynamická — místo natvrdo napsaných `<img>` tagů PHP přečte z SQLite tabulky `gallery` všechny záznamy a vyrenderuje je. Tím lze přidávat fotky bez úpravy kódu."

## 20.4 Známé slabiny a jak je obhájit

Tato tabulka shrnuje známé nedostatky (z posudků i z code review) a strategii, jak je u obhajoby odpovědět.

| Slabina | Strategie |
|---------|-----------|
| Žádný logout / odhlášení | **Přijmout** — „Implementoval jsem login, ale logout chybí. V další verzi bych přidal `logout.php` s `session_destroy()`." |
| Žádné `session_regenerate_id` | **Přijmout** — „Chybí mi obrana proti session fixation, doplnil bych po loginu." |
| Žádný CSRF token | **Přijmout** — „Formuláře nemají CSRF token. V produkční verzi bych přidal random token v session." |
| Žádná validace duplicit | **Vysvětlit** — „Spoléhám na UNIQUE constraint v DB. Při pokusu o duplikát odchytím PDOException." |
| `db_users.php` nepoužívaný | **Přijmout** — „To je pozůstatek z dřívější verze, kdy jsem zkoušel `SQLite3` API. Měl jsem ho smazat." |
| Header kopírovaný v každém souboru | **Vysvětlit/Přijmout** — „Mohl jsem extrahovat do `header.php` partial podobně jako `hamburger.php`. Kopírování je technický dluh." |
| Inline `<style>` v `hamburger.php` | **Přijmout** — „Mohlo být v samostatném CSS souboru. Pro jednoduchost partial jsem to spojil." |
| `srazy.php` čistě statická | **Vysvětlit** — „Pro maturitní rozsah jsem srazy nedělal dynamické. Komunita aktuálně řeší srazy přes Instagram." |
| Procedurální styl bez MVC | **Vysvětlit** — „Pro projekt této velikosti je procedurální PHP dostatečné. V Laravelu by se to rozdělilo do controllerů a views." |
| Žádný framework | **Vysvětlit + Obhájit** — „Chtěl jsem rozumět principům bez abstrakcí. Laravel pro 5stránkový web by byl overkill." |

## 20.5 Co bych v další verzi udělal

> **Tip pro obhajobu:** umět tento seznam zpaměti — komise miluje, když student vidí limity své práce.

### Bezpečnost
1. **CSRF tokeny** ve všech POST formulářích
2. **`session_regenerate_id(true)`** po loginu
3. **Verifikace e-mailu** při registraci
4. **Rate limiting** na login (počítadlo v session/Redis)
5. **HttpOnly + Secure + SameSite** flagy na session cookie
6. **Content Security Policy** hlavička
7. **HTTPS** (Let's Encrypt) — zkontrolovat, jestli má

### Funkcionalita
8. **Logout** — `logout.php` s `session_destroy()`
9. **Profile page** — uživatel může editovat údaje
10. **Dynamické srazy** — CRUD pro srazy, kalendář
11. **Upload do galerie** — chráněný admin endpoint
12. **Kontaktní formulář** — odeslání e-mailu přes PHP `mail()` nebo SMTP knihovnu

### Architektura
13. **Header/footer jako partial** — odstranit duplicitu
14. **CSS přesunout z `<style>` do souborů**
15. **Refactoring na MVC** — controller/model/view složky
16. **Composer + autoloading** — pro budoucí knihovny
17. **`.env` pro konfiguraci** (DB cesta, secrets)

### Kvalita
18. **Migrace** — schema v `.sql` souborech, ne natvrdo
19. **Logger** — Monolog nebo aspoň `error_log()`
20. **Unit testy** — PHPUnit, alespoň pro password handling

### Operace
21. **Verzování v Gitu** + commit po každé feature
22. **CI/CD** — GitHub Actions pro automatický deploy
23. **Backup skripty** — denní kopie SQLite na cloud
24. **Monitoring** — uptime checker (UptimeRobot)

---

# Stručné závěrečné shrnutí

## Webové aplikace

Webová aplikace běží přes prohlížeč. Má **frontend**, který uživatel vidí, a **backend**, který zpracovává logiku a data. Komunikace probíhá přes **HTTP** nebo bezpečněji přes **HTTPS** s TLS. FTP slouží k přenosu souborů, ale dnes se v profesionálním prostředí nahrazuje bezpečnějšími (SFTP/FTPS) nebo automatizovanými způsoby (CI/CD, Git deploy). Častou architekturou je **MVC** (Model-View-Controller), které odděluje datovou, prezentační a řídicí vrstvu. Moderní alternativou je **SPA + REST API** — frontend ve frameworku jako React/Vue komunikuje s backendem přes JSON API. **Redakční systém (CMS)** je speciální webová aplikace pro správu obsahu — WordPress, Drupal, nebo headless CMS jako Strapi či Contentful.

## Softwarové inženýrství

Softwarové inženýrství řeší **celý proces vývoje softwaru** od požadavků přes návrh, implementaci, testování a nasazení až po údržbu. **Agilní metodiky** (Scrum, Kanban, XP) umožňují vyvíjet software iterativně a reagovat na změny — Scrum pracuje se sprinty 1–4 týdny, definovanými rolemi (PO, SM, Devs) a událostmi (Planning, Daily, Review, Retro). **Testování** odhaluje chyby — testovací pyramida doporučuje 70 % unit testů, 20 % integration, 10 % E2E. **Issue tracking systémy** (Jira, YouTrack, GitHub Issues) organizují práci týmu a propojují se s Git verzováním. **Kvalita softwaru** se hodnotí podle **ISO 25010** — funkčnost, spolehlivost, výkon, bezpečnost, použitelnost, udržovatelnost, kompatibilita, přenositelnost. V praxi se kvalita zajišťuje kombinací **CI/CD**, **code review**, **statické analýzy** (SonarQube) a měření metrik (test coverage, uptime, MTTR).

---

# Použité a doporučené zdroje

## Pro otázku 18

- **MDN Web Docs: HTTP** — https://developer.mozilla.org/en-US/docs/Web/HTTP
- **MDN Web Docs: HTTPS** — https://developer.mozilla.org/en-US/docs/Glossary/HTTPS
- **MDN Web Docs: HTTP response status codes** — https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- **MDN Web Docs: Cross-Origin Resource Sharing (CORS)** — https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS
- **W3C TR/html52** — https://www.w3.org/TR/html52/
- **Microsoft: ASP.NET MVC** — https://dotnet.microsoft.com/en-us/apps/aspnet/mvc
- **Laravel docs** — https://laravel.com/docs
- **WordPress Codex** — https://wordpress.org/documentation/
- **Argo22: Webová aplikace vs. web** — https://argo22.com/blog/webova-aplikace-vs-web/
- **OWASP Top 10** — https://owasp.org/Top10/
- **OAuth 2.0 RFC 6749** — https://datatracker.ietf.org/doc/html/rfc6749
- **JWT.io** — https://jwt.io

## Pro otázku 19

- **Scrum Guide** — https://scrumguides.org/scrum-guide.html
- **Agile Manifesto** — https://agilemanifesto.org/
- **ISTQB Glossary** — https://istqb-glossary.page/
- **ISO/IEC 25010** — https://www.iso.org/standard/35733.html
- **Martin Fowler — Refactoring** (kniha)
- **Kent Beck — Test-Driven Development** (kniha)
- **GitHub Docs: GitHub Actions** — https://docs.github.com/en/actions
- **Atlassian: Jira Documentation** — https://www.atlassian.com/software/jira/guides
- **SonarQube** — https://www.sonarsource.com/products/sonarqube/

## Pro projekt CarzMeetz

- **PHP Manual: PDO** — https://www.php.net/manual/en/book.pdo.php
- **PHP Manual: password_hash** — https://www.php.net/manual/en/function.password-hash.php
- **PHP Manual: Sessions** — https://www.php.net/manual/en/book.session.php
- **SQLite documentation** — https://www.sqlite.org/docs.html
- **Let's Encrypt** — https://letsencrypt.org/
