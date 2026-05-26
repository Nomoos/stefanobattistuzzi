# Otázka 18 — Webové aplikace a redakční systémy

Tento okruh pokrývá způsob, jakým fungují moderní webové aplikace — od rozdělení na frontend a backend, přes protokoly, kterými spolu klient a server komunikují (HTTP/HTTPS/FTP), princip request/response cyklu, architektonický vzor MVC až po redakční systémy (CMS) jako WordPress. Cílem je, aby student dokázal vysvětlit, co se stane od chvíle, kdy uživatel zadá adresu do prohlížeče, až po zobrazení stránky, a aby rozuměl tomu, jak velké weby (např. zpravodajské portály, e-shopy nebo klubové stránky TJ Slavoj Mýto) vznikají a fungují.

---

## 1. Frontend a backend

### Definice

- **Frontend** (česky *přední strana*, *klientská strana*, *client-side*) — část webové aplikace, kterou uživatel **vidí a se kterou přímo interaguje** ve svém prohlížeči. Běží na **klientovi** (v prohlížeči).
- **Backend** (česky *zadní strana*, *serverová strana*, *server-side*) — část aplikace, která běží na **serveru**, zpracovává logiku, pracuje s databází, autentizuje uživatele a posílá data frontendu. Uživatel ji nevidí.
- **Full-stack** — programátor, který umí obojí.

### Detailní výklad

#### Frontend
Frontend tvoří **uživatelské rozhraní (UI)**. Když si otevřete jakýkoliv web (např. seznam.cz nebo facebook.com), vše, co vidíte — texty, obrázky, tlačítka, formuláře, animace — to je výstup frontendu. Frontend je odpovědný za:

- **Strukturu stránky** — co je nadpis, odstavec, tabulka, formulář (řeší jazyk **HTML**)
- **Vzhled** — barvy, fonty, rozložení, responzivita pro mobil (řeší **CSS**)
- **Interaktivitu** — co se stane, když kliknu na tlačítko, validaci formulářů, animace, načítání obsahu bez znovuobnovení stránky (řeší **JavaScript**)

**Hlavní technologie frontendu:**

| Technologie | K čemu slouží |
|---|---|
| **HTML** (HyperText Markup Language) | Definuje strukturu a obsah stránky pomocí tagů (`<h1>`, `<p>`, `<form>`...) |
| **CSS** (Cascading Style Sheets) | Definuje vzhled — barvy, fonty, rozložení, responzivitu |
| **JavaScript** | Programovací jazyk, který běží v prohlížeči a umožňuje interaktivitu |
| **Bootstrap, Tailwind** | CSS frameworky — připravené komponenty a utility třídy pro rychlejší vývoj |
| **React, Vue, Angular** | JavaScriptové knihovny/frameworky pro tvorbu komplexních **SPA** (Single Page Applications) |
| **TypeScript** | Nadstavba JavaScriptu s typovou kontrolou — populární v moderních projektech |
| **Sass, Less** | Preprocesory CSS — umožňují proměnné, vnořování, mixiny |

#### Backend
Backend je **mozek aplikace**. Zatímco frontend rozhoduje *jak* se data zobrazí, backend rozhoduje *co* a *komu*. Backend:

- **Zpracovává požadavky** od frontendu (např. „Přihlas uživatele", „Vrať seznam zápasů")
- **Pracuje s databází** — ukládá, čte, mazá, aktualizuje data
- **Implementuje business logiku** — pravidla aplikace (např. „Uživatel může editovat jen své příspěvky")
- **Zabezpečuje aplikaci** — autentizace, autorizace, šifrování, ochrana proti útokům
- **Generuje odpověď** (HTML, JSON, XML), kterou pošle zpět prohlížeči

**Hlavní technologie backendu:**

| Jazyk / Platforma | Typické frameworky | Příklady použití |
|---|---|---|
| **PHP** | Laravel, Symfony, WordPress (CMS) | Většina menších webů, WordPress |
| **Python** | Django, Flask, FastAPI | Data science, AI, weby (Instagram) |
| **JavaScript (Node.js)** | Express, NestJS, Next.js | Realtime aplikace (chat), API |
| **C#** | ASP.NET Core | Firemní aplikace, Microsoft ekosystém |
| **Java** | Spring, Spring Boot | Velké korporátní systémy, banky |
| **Ruby** | Ruby on Rails | GitHub, Shopify |
| **Go** | Gin, Echo | Mikroslužby, výkonná API |

**Databáze používané v backendu:**
- **Relační (SQL):** MySQL, MariaDB, PostgreSQL, SQL Server, Oracle
- **NoSQL:** MongoDB (dokumentová), Redis (key-value, cache), Elasticsearch (vyhledávací)

### Komunikace mezi frontendem a backendem

Frontend a backend spolu komunikují **přes síť**, typicky pomocí **HTTP/HTTPS** protokolu:

1. Frontend (prohlížeč) pošle **HTTP request** na URL backendu (např. `GET /api/zapasy`)
2. Backend požadavek zpracuje, sáhne do databáze a vrátí **HTTP response** (často ve formátu **JSON**)
3. Frontend obdržená data vykreslí v UI (např. seznam zápasů v tabulce)

Tomuto rozhraní se říká **API** (Application Programming Interface). Nejčastější styl je **REST API** (více v sekci 3).

```
[Prohlížeč / Frontend]  --- HTTP request --->  [Server / Backend]  --- SQL ---> [Databáze]
[Prohlížeč / Frontend]  <-- HTTP response ---  [Server / Backend]  <-- data --- [Databáze]
```

### Praktický příklad — TJ Slavoj Mýto

Klubový web TJ Slavoj Mýto:
- **Frontend:** HTML šablony PHP (`single-zapas.php`), CSS (Bootstrap 5 + vlastní), trochu vanilla JS (mobilní menu, filtry)
- **Backend:** WordPress (běží v PHP na serveru), databáze MySQL — ukládá custom post types `zapas`, `tym`, `hrac`
- **Komunikace:** prohlížeč pošle `GET /zapasy/`, WordPress (PHP) zpracuje, načte zápasy z MySQL, vygeneruje HTML, pošle zpět

### Časté otázky komisaře

**Q: Co je rozdíl mezi frontendem a backendem?**
A: Frontend běží v prohlížeči uživatele a stará se o zobrazení a interakci. Backend běží na serveru a stará se o logiku, databázi a zabezpečení.

**Q: Vyjmenujte technologie, které tvoří frontend.**
A: Základ je HTML (struktura), CSS (vzhled) a JavaScript (interaktivita). Z frameworků pak Bootstrap, React, Vue, Angular.

**Q: Co je full-stack vývojář?**
A: Programátor, který umí jak frontend, tak backend — tedy celý technologický „stack" aplikace.

**Q: Jak spolu frontend a backend komunikují?**
A: Přes síť pomocí HTTP/HTTPS protokolu. Frontend posílá requesty na backendové API, backend odpovídá daty (nejčastěji JSON).

**Q: Proč nemůže frontend přímo přistupovat k databázi?**
A: Z bezpečnostních důvodů — kód frontendu vidí každý uživatel ve svém prohlížeči. Kdyby tam byly přihlašovací údaje k databázi, kdokoliv by si je mohl přečíst a databázi zničit. Backend slouží jako kontrolovaná „brána" k datům.

---

## 2. HTTP, HTTPS, FTP — síťové protokoly

### Definice

- **Protokol** — soubor pravidel, jak spolu dvě zařízení v síti komunikují (co a v jakém pořadí si mají poslat).
- **HTTP** (HyperText Transfer Protocol) — protokol pro přenos webových stránek a dat na portu **80**.
- **HTTPS** (HTTP Secure) — šifrovaná verze HTTP pomocí TLS/SSL, port **443**.
- **FTP** (File Transfer Protocol) — protokol pro přenos souborů, port **21** (řídicí) a **20** (data).

### HTTP — detailní výklad

HTTP je základní protokol webu. Funguje na modelu **klient-server**:

1. Klient (prohlížeč) pošle **request** (požadavek)
2. Server pošle **response** (odpověď)
3. Spojení se ukončí (HTTP je **bezstavový** — stateless)

#### Struktura HTTP requestu

```
GET /zapasy/zapas-2 HTTP/1.1            ← startovací řádek (metoda, cesta, verze)
Host: tjslavojmyto.cz                   ← hlavičky (headers)
User-Agent: Mozilla/5.0 ...
Accept: text/html
Cookie: PHPSESSID=abc123

(prázdný řádek)
(tělo — u POST/PUT, u GET typicky prázdné)
```

#### Struktura HTTP response

```
HTTP/1.1 200 OK                         ← startovací řádek (verze, stavový kód, popis)
Content-Type: text/html; charset=UTF-8  ← hlavičky
Content-Length: 1234
Set-Cookie: session=xyz789

<!DOCTYPE html>                         ← tělo odpovědi (HTML, JSON, obrázek...)
<html>...</html>
```

#### HTTP metody (slovesa)

| Metoda | Účel | Příklad |
|---|---|---|
| **GET** | Získat data (neměla by měnit stav serveru) | `GET /zapasy` — vrať seznam zápasů |
| **POST** | Vytvořit nový záznam, odeslat formulář | `POST /zapasy` — přidej nový zápas |
| **PUT** | Aktualizovat (nahradit celý záznam) | `PUT /zapasy/5` — přepiš zápas č. 5 |
| **PATCH** | Částečná aktualizace | `PATCH /zapasy/5` — změň jen skóre |
| **DELETE** | Smazat záznam | `DELETE /zapasy/5` — smaž zápas č. 5 |
| **HEAD** | Jako GET, ale vrátí jen hlavičky bez těla | Testování dostupnosti |
| **OPTIONS** | Vrátí podporované metody (důležité pro CORS) | — |

#### HTTP stavové kódy

Jsou tříciferné a dělí se do 5 skupin:

| Skupina | Význam | Příklady |
|---|---|---|
| **1xx** | Informační | 100 Continue |
| **2xx** | Úspěch | **200 OK**, 201 Created, 204 No Content |
| **3xx** | Přesměrování | 301 Moved Permanently, 302 Found, **304 Not Modified** |
| **4xx** | Chyba klienta | **400 Bad Request**, **401 Unauthorized**, **403 Forbidden**, **404 Not Found**, 429 Too Many Requests |
| **5xx** | Chyba serveru | **500 Internal Server Error**, 502 Bad Gateway, **503 Service Unavailable**, 504 Gateway Timeout |

**Nejdůležitější kódy, které musí student znát:**
- **200 OK** — vše proběhlo v pořádku
- **301 / 302** — stránka přesměrována (301 trvalé, 302 dočasné)
- **400** — klient poslal nesmysl (špatný JSON, chybějící parametr)
- **401** — nepřihlášen / chybí ověření
- **403** — přihlášen, ale nemá oprávnění
- **404** — stránka neexistuje
- **500** — chyba na serveru (např. výjimka v PHP)

### HTTPS — detailní výklad

HTTPS je HTTP + **šifrovací vrstva** (TLS, dříve SSL).

#### Proč HTTPS?
HTTP posílá data **otevřeně**. Kdokoliv (na sdílené Wi-Fi v kavárně, na firemní síti, poskytovatel internetu) si může přečíst:
- Hesla
- Čísla platebních karet
- Cookies (a tím se přihlásit za vás)
- Obsah stránek

HTTPS data **zašifruje**, takže útočník vidí jen nesmyslné bajty.

#### Jak funguje TLS handshake (zjednodušeně)

1. Prohlížeč: „Chci se spojit, podporuju tyto šifrovací algoritmy."
2. Server: „OK, použijeme tento. Zde je můj **certifikát**." (podepsaný certifikační autoritou)
3. Prohlížeč ověří certifikát (vydaný důvěryhodnou autoritou — Let's Encrypt, DigiCert, Sectigo...)
4. Dohodne se **šifrovací klíč** (asymetrické šifrování pro výměnu klíče, pak symetrické pro vlastní komunikaci)
5. Veškerá další komunikace je šifrovaná

#### SSL certifikát
- Vystavuje ho **certifikační autorita (CA)** — např. Let's Encrypt (zdarma), DigiCert, GlobalSign
- Obsahuje veřejný klíč, doménu, platnost, podpis CA
- Druhy: **DV** (Domain Validation — ověřena jen doména), **OV** (Organization), **EV** (Extended Validation — zelený pruh, dříve)
- Prohlížeč zobrazí **zámeček** v adresním řádku, když je certifikát platný

#### Rozdíl HTTP vs HTTPS — shrnutí

| | HTTP | HTTPS |
|---|---|---|
| Port | 80 | 443 |
| Šifrování | NE | ANO (TLS/SSL) |
| Rychlost | Mírně rychlejší | Mírně pomalejší (handshake) |
| SEO | Penalizováno Googlem | Preferováno |
| Důvěryhodnost | Prohlížeč varuje „Není zabezpečeno" | Zámeček |
| Použití dnes | Jen interní/test | Standard pro produkci |

### FTP — detailní výklad

FTP slouží k **přenosu souborů** mezi klientem a serverem. Typicky se používá pro:
- Nahrávání webu na hosting
- Stahování záloh
- Údržbu vzdáleného souborového systému

#### Jak FTP funguje
- Používá **dvě spojení**: řídicí (port 21, příkazy) a datové (port 20, vlastní přenos souborů)
- Klient pošle příkaz (LIST, RETR, STOR, DELE...), server odpoví
- Funguje ve dvou režimech:
  - **Active** — server se sám připojuje zpět ke klientovi (problém s firewallem)
  - **Passive** — klient otevírá obě spojení (běžnější dnes)

#### Příkazy FTP
| Příkaz | Význam |
|---|---|
| `USER` | Přihlašovací jméno |
| `PASS` | Heslo |
| `LIST` | Vypiš obsah adresáře |
| `CWD` | Změň adresář (change working directory) |
| `RETR` | Stáhni soubor (retrieve) |
| `STOR` | Nahraj soubor (store) |
| `DELE` | Smaž soubor |
| `MKD` / `RMD` | Vytvoř / smaž adresář |
| `QUIT` | Ukonči spojení |

#### Problém FTP — bezpečnost
**FTP posílá heslo i data v plain textu** — stejně jako HTTP. Proto existují bezpečné varianty:

| Protokol | Port | Princip |
|---|---|---|
| **FTP** | 21 | Klasický, NEzabezpečený |
| **FTPS** (FTP Secure) | 990 (implicit) / 21 (explicit) | FTP nad TLS/SSL — přidá šifrování |
| **SFTP** (SSH File Transfer Protocol) | 22 | Úplně jiný protokol, běží přes SSH. **Nemá nic společného s FTP** kromě názvu! |

**Dnes se preferuje SFTP** (běží přes SSH, jedno spojení, lépe prochází firewally).

#### Klienti pro FTP
- **FileZilla** (zdarma, multiplatform) — nejpopulárnější
- **WinSCP** (Windows)
- **Cyberduck** (Mac)
- Plugin v IDE (např. VS Code FTP-Sync)

### Praktický příklad

Student dělá WordPress web pro TJ Slavoj Mýto na lokálním XAMPP. Až bude web hotový, nahraje ho:
- Buď přes **FTP/SFTP** (FileZilla → upload složky `wp-content/`)
- Nebo přes **cPanel** / **Plesk** (webové rozhraní hostingu)
- Web bude běžet přes **HTTPS** (hosting zajistí certifikát Let's Encrypt zdarma)

### Časté otázky komisaře

**Q: Jaký je rozdíl mezi HTTP a HTTPS?**
A: HTTPS je HTTP + šifrovací vrstva TLS/SSL. Komunikace je šifrovaná, takže útočník nemůže přečíst hesla nebo cookies. HTTP používá port 80, HTTPS port 443.

**Q: Vyjmenujte HTTP metody.**
A: GET (čtení), POST (vytvoření), PUT (úprava celého záznamu), PATCH (částečná úprava), DELETE (smazání), HEAD a OPTIONS.

**Q: Co znamená kód 404?**
A: „Not Found" — server stránku/zdroj nenašel. Klient požaduje něco, co neexistuje.

**Q: Co znamená kód 500?**
A: „Internal Server Error" — chyba na straně serveru (např. chyba v PHP kódu, nedostupná databáze).

**Q: Co je SSL certifikát a kdo ho vystavuje?**
A: Digitální certifikát potvrzující, že server, ke kterému se připojuji, je opravdu ten, za který se vydává. Vystavuje ho certifikační autorita (CA) — např. Let's Encrypt (zdarma), DigiCert.

**Q: Jaký je rozdíl mezi FTP a SFTP?**
A: FTP je nezabezpečený, posílá heslo i data otevřeně. SFTP běží přes SSH a je zcela šifrovaný. SFTP používá port 22, FTP port 21.

**Q: Co je stavový kód HTTP?**
A: Tříciferné číslo v odpovědi serveru, které říká, jak požadavek dopadl. 2xx úspěch, 3xx přesměrování, 4xx chyba klienta, 5xx chyba serveru.

---

## 3. Princip a fungování webové aplikace

### Definice

- **Webová aplikace** — aplikace, která běží přes internet, je přístupná z prohlížeče a používá model **klient-server**.
- **Klient-server model** — architektura, kde **klient** (typicky prohlížeč) posílá požadavky a **server** je zpracovává a odpovídá.
- **Request/response cyklus** — základní vzor komunikace na webu: klient se zeptá, server odpoví.

### Detailní výklad — co se stane, když napíšu URL do prohlížeče?

Tohle je **klasická maturitní otázka**. Krok za krokem:

```
[1] Uživatel zadá: https://www.tjslavojmyto.cz/zapasy
                          ↓
[2] DNS — překlad domény na IP adresu
    Prohlížeč se zeptá DNS serveru: "Jaká je IP adresa tjslavojmyto.cz?"
    DNS odpoví: "85.93.115.42"
                          ↓
[3] Navázání TCP spojení
    Prohlížeč se připojí na IP 85.93.115.42, port 443 (HTTPS)
    Three-way handshake: SYN → SYN-ACK → ACK
                          ↓
[4] TLS handshake (u HTTPS)
    Prohlížeč ověří certifikát serveru, dohodne se šifrovací klíč.
                          ↓
[5] HTTP request
    Prohlížeč pošle:
        GET /zapasy HTTP/1.1
        Host: tjslavojmyto.cz
        Cookie: PHPSESSID=...
                          ↓
[6] Server přijme request
    Webový server (Apache, Nginx) zjistí, kdo má požadavek zpracovat.
    Pro PHP soubor předá řízení PHP interpretu → WordPress.
                          ↓
[7] Backend zpracuje
    WordPress zjistí, že /zapasy je stránka, načte z MySQL data
    (custom post type zapas), vygeneruje HTML.
                          ↓
[8] HTTP response
    Server odpoví:
        HTTP/1.1 200 OK
        Content-Type: text/html
        Set-Cookie: ...

        <!DOCTYPE html><html>...
                          ↓
[9] Prohlížeč zpracuje HTML
    - Parsuje HTML → DOM strom
    - Najde <link rel="stylesheet"> → stáhne CSS (další HTTP requesty!)
    - Najde <script> → stáhne a vykoná JavaScript
    - Najde <img> → stáhne obrázky
                          ↓
[10] Render (vykreslení)
     Prohlížeč zkombinuje DOM + CSSOM → render tree → layout → paint → composite.
     Uživatel vidí stránku.
                          ↓
[11] Interakce
     Uživatel klikne na zápas → další HTTP request → ...
```

### Klient-server model

- **Klient** (prohlížeč, mobilní aplikace, IoT zařízení) — **iniciuje** komunikaci, ptá se serveru.
- **Server** — **čeká** na požadavky, reaguje na ně.
- Server může obsluhovat **mnoho klientů zároveň** (typicky tisíce).

### Bezstavovost HTTP (stateless)

HTTP je **bezstavový protokol** — každý request je samostatný, server si o předchozích requestech nepamatuje. To znamená:

- Server neví, jestli jste se přihlásili v minulém requestu
- Každý request musí nést všechny potřebné informace (URL, hlavičky, cookies)

To je **problém** pro aplikace, kde potřebujeme zachovat stav (kdo je přihlášený, co má v košíku). Řešením jsou **cookies** a **sessions**.

#### Cookies
- Malé soubory (max ~4 KB), které **server pošle klientovi** přes hlavičku `Set-Cookie`
- Klient (prohlížeč) je **automaticky posílá zpět** s každým dalším requestem na danou doménu (`Cookie: …`)
- Použití: zapamatování přihlášení, jazyk, preference, sledovací cookies (Google Analytics)
- Atributy: `HttpOnly` (nečitelná z JS), `Secure` (jen přes HTTPS), `SameSite` (ochrana proti CSRF), `Expires` / `Max-Age`

#### Sessions
- Stav uložený **na serveru** (v souboru, v databázi, v Redis)
- Klient drží jen **session ID** (krátký řetězec) v cookie (`PHPSESSID=xyz`)
- Server podle session ID dohledá data uživatele
- Výhoda: citlivá data (přihlášení, obsah košíku) jsou na serveru, ne v prohlížeči

```
[Klient: cookie PHPSESSID=abc123]
                    ↓
[Server: hledá session "abc123" v úložišti]
                    ↓
[Najde: {user_id: 5, username: 'lukas', cart: [...]}]
```

### REST principy

**REST** (REpresentational State Transfer) je **architektonický styl** pro tvorbu webových API. Hlavní principy:

1. **Klient-server** — oddělení frontendu a backendu
2. **Bezstavovost** (stateless) — každý request obsahuje vše potřebné, server si nepamatuje předchozí
3. **Cachovatelnost** — odpovědi mohou být cachovány (přes HTTP headers `Cache-Control`)
4. **Jednotné rozhraní** (uniform interface) — používáme HTTP metody a URL jako „zdroje"
5. **Vrstvená architektura** (layered system) — mezi klientem a serverem mohou být proxy, load balancery
6. **Code on demand** (volitelně) — server může poslat kód, který klient vykoná

#### REST v praxi — URL jako zdroje + HTTP metody jako akce

| URL | GET | POST | PUT | DELETE |
|---|---|---|---|---|
| `/zapasy` | seznam zápasů | vytvoř nový zápas | (nepoužívá se) | (nepoužívá se) |
| `/zapasy/5` | detail zápasu č. 5 | (nepoužívá se) | aktualizuj zápas č. 5 | smaž zápas č. 5 |
| `/zapasy/5/strelci` | střelci zápasu č. 5 | přidej střelce | — | — |

Data se typicky vyměňují ve formátu **JSON**:
```json
{
  "id": 5,
  "datum": "2025-10-12",
  "domaci": "TJ Slavoj Mýto",
  "hoste": "Sparta Praha",
  "skore": "2:1"
}
```

#### Alternativy REST
- **SOAP** — starší, XML-based, těžkopádné
- **GraphQL** — moderní, klient si říká přesně, jaká data chce
- **gRPC** — binární, vysoký výkon (interní mikroslužby)

### Časté otázky komisaře

**Q: Popište, co se stane, když do prohlížeče zadám URL a stisknu Enter.**
A: 1) DNS přeloží doménu na IP, 2) prohlížeč otevře TCP spojení (a TLS handshake u HTTPS), 3) pošle HTTP request, 4) server zpracuje a odpoví HTML, 5) prohlížeč HTML parsuje, dotahuje CSS, JS, obrázky, 6) vykreslí stránku.

**Q: Co je klient-server model?**
A: Architektura, kde klient (prohlížeč) iniciuje požadavky a server (počítač s aplikací) na ně odpovídá. Jeden server obsluhuje mnoho klientů.

**Q: Co znamená, že HTTP je bezstavový?**
A: Server si nepamatuje předchozí requesty. Každý request je samostatný. Stav (např. přihlášení) se řeší pomocí cookies a sessions.

**Q: Jaký je rozdíl mezi cookie a session?**
A: Cookie je uložená u klienta (v prohlížeči), session je uložená na serveru. Klient drží jen session ID v cookie, podle kterého server data dohledá.

**Q: Co je REST?**
A: Architektonický styl pro tvorbu webových API. Používá HTTP metody (GET, POST, PUT, DELETE) na zdroje identifikované URL. Je stateless, jednotný a cachovatelný.

**Q: K čemu slouží DNS?**
A: Domain Name System — překládá doménová jména (např. seznam.cz) na IP adresy (např. 77.75.79.222), které potřebuje síťová vrstva pro spojení.

---

## 4. Architektura MVC

### Definice

**MVC** (Model-View-Controller) je **architektonický návrhový vzor** (design pattern) pro tvorbu uživatelských rozhraní, který odděluje aplikaci do tří vzájemně propojených komponent. Cílem je **oddělit interní reprezentaci dat od způsobu, jakým jsou prezentována uživateli**.

### Historie

- **MVC** poprvé popsal **Trygve Reenskaug** v roce **1978/1979** v rámci práce na jazyku **Smalltalk-76/80** v Xerox PARC.
- Původně sloužil pro desktopové GUI, později se rozšířil do webových aplikací.
- Dnes je MVC základem většiny webových frameworků (Laravel, Django, Ruby on Rails, ASP.NET MVC, Spring MVC).

### Tři komponenty MVC

#### Model
- **Co to je:** reprezentuje **data a business logiku** aplikace.
- **Co dělá:** komunikuje s databází, validuje data, obsahuje pravidla aplikace (např. „cena nesmí být záporná").
- **Příklad:** třída `Zapas` s metodami `nactiZapasy()`, `ulozZapas()`, `vypoctiSkore()`.
- **Nezná:** jak budou data zobrazena (nezná View).

#### View (Pohled)
- **Co to je:** **prezentační vrstva** — to, co vidí uživatel.
- **Co dělá:** vykresluje data z Modelu do HTML, JSON, PDF...
- **Příklad:** šablona `zapasy.blade.php` (Laravel), `zapasy.html` (Django), `single-zapas.php` (WordPress).
- **Nezná:** business logiku, je „hloupá".

#### Controller (Řadič)
- **Co to je:** **prostředník** mezi Modelem a View. Zpracovává vstup od uživatele.
- **Co dělá:**
  1. Přijme HTTP request
  2. Zavolá Model (např. „dej mi všechny zápasy")
  3. Předá data View
  4. Vrátí response uživateli
- **Příklad:** `ZapasController` s metodou `index()`, `show($id)`, `store($data)`.

### Diagram interakce

```
        +-------------+
        |   Uživatel  |
        +------+------+
               |
               | 1. HTTP request
               ▼
        +-------------+
        | Controller  |  ← přijme request
        +------+------+
               |
               | 2. zavolá
               ▼
        +-------------+         +-------------+
        |    Model    | ←-→     |  Databáze   |
        +------+------+         +-------------+
               |
               | 3. vrátí data
               ▼
        +-------------+
        | Controller  |
        +------+------+
               |
               | 4. předá data
               ▼
        +-------------+
        |    View     |  ← vygeneruje HTML
        +------+------+
               |
               | 5. HTTP response (HTML)
               ▼
        +-------------+
        |   Uživatel  |
        +-------------+
```

### Konkrétní příklad — výpis zápasů v Laravelu

**Route** (cesta):
```php
Route::get('/zapasy', [ZapasController::class, 'index']);
```

**Controller:**
```php
class ZapasController {
    public function index() {
        $zapasy = Zapas::all();              // 1. zavolá Model
        return view('zapasy.index', [        // 2. předá data View
            'zapasy' => $zapasy
        ]);
    }
}
```

**Model:**
```php
class Zapas extends Model {
    protected $table = 'zapasy';
    // metody Eloquent: ::all(), ::find(), ::where()
}
```

**View** (`zapasy/index.blade.php`):
```php
<h1>Seznam zápasů</h1>
<ul>
@foreach ($zapasy as $zapas)
    <li>{{ $zapas->datum }} — {{ $zapas->domaci }} vs {{ $zapas->hoste }}</li>
@endforeach
</ul>
```

### Výhody MVC

1. **Oddělení odpovědností** (Separation of Concerns) — každá vrstva má jasnou roli
2. **Testovatelnost** — Model lze testovat bez UI, Controller s mockovaným Modelem
3. **Znovupoužitelnost** — stejný Model lze použít s různými View (HTML, JSON, PDF)
4. **Týmová spolupráce** — frontendista pracuje na View, backendista na Modelu/Controlleru
5. **Údržba** — změna v jedné vrstvě nerozbije ostatní

### Nevýhody MVC

1. Vyšší komplexita pro malé projekty
2. Více souborů a tříd
3. Učení křivka pro začátečníky

### Současné varianty MVC

#### MVP (Model-View-Presenter)
- Místo Controlleru je **Presenter**
- Presenter **přímo aktualizuje View** (View je „pasivní")
- Lepší pro desktopové aplikace, Android (klasické MVP)

#### MVVM (Model-View-ViewModel)
- ViewModel obsahuje stav a logiku View
- **Data binding** — View se automaticky aktualizuje, když se změní ViewModel
- Používá se v: WPF, Xamarin, Angular, Vue.js
- Příklad: napíšu do inputu → ViewModel se aktualizuje → automaticky se přepočítá zobrazení

| | Model | View | Controller / Presenter / ViewModel |
|---|---|---|---|
| **MVC** | Data + logika | UI | Zpracovává vstup, předává data View |
| **MVP** | Data + logika | Pasivní UI | Aktualizuje View přímo |
| **MVVM** | Data + logika | UI s data bindingem | Stav View, automaticky synchronizován |

### MVC a WordPress?

**Důležité:** WordPress **NENÍ** čistý MVC framework — má vlastní architekturu založenou na **template hierarchy** a **hooks** (filters/actions). Ale **lze v něm uvažovat v duchu MVC**:
- **Model:** WP_Query, custom post types, meta fields, databáze MySQL
- **View:** soubory šablon (`single-zapas.php`, `archive-zapas.php`)
- **Controller:** `functions.php`, hooks (např. `pre_get_posts`), pluginy

### Časté otázky komisaře

**Q: Co znamená zkratka MVC a co označuje?**
A: Model-View-Controller. Architektonický návrhový vzor, který odděluje aplikaci do tří vrstev: Model (data), View (zobrazení), Controller (řízení).

**Q: Kdo vymyslel MVC a kdy?**
A: Norský programátor Trygve Reenskaug, v roce 1978/79, v rámci jazyka Smalltalk v Xerox PARC.

**Q: Co dělá Controller?**
A: Přijímá vstup (HTTP request), volá Model pro získání/změnu dat, předává data View, vrací response uživateli. Je „dirigent" mezi Modelem a View.

**Q: Jaké jsou výhody MVC?**
A: Oddělení odpovědností, lepší testovatelnost, znovupoužitelnost, snadnější týmová práce, lepší údržba kódu.

**Q: Vyjmenujte frameworky používající MVC.**
A: Laravel (PHP), Django (Python, ale spíše MTV), Ruby on Rails (Ruby), ASP.NET MVC (C#), Spring MVC (Java).

**Q: Jaký je rozdíl mezi MVC a MVVM?**
A: MVC má Controller, který explicitně předává data do View. MVVM má ViewModel a data binding — View se aktualizuje automaticky, když se změní ViewModel. MVVM se používá v Angular, Vue, WPF.

---

## 5. Redakční systémy (CMS)

### Definice

**CMS** (Content Management System, česky **redakční systém** nebo **systém pro správu obsahu**) je software, který umožňuje **uživatelům bez programátorských znalostí vytvářet, upravovat a publikovat obsah** na webu pomocí grafického administračního rozhraní.

### K čemu CMS slouží

- **Redaktor / autor článků** píše obsah přes WYSIWYG editor (jako Word) místo psaní HTML.
- **Šablony** (themes) řeší vzhled — redaktor se o ně nestará.
- **Pluginy / moduly** přidávají funkce (e-shop, formuláře, SEO, galerie).
- **Více uživatelů** s různými právy (administrátor, editor, autor, návštěvník).
- Změny obsahu jsou **okamžité** — žádné nahrávání souborů FTP.

### Klíčové funkce CMS

| Funkce | Popis |
|---|---|
| **Správa obsahu** | Vytváření, editace, mazání článků, stránek, médií. Verzování (revize). |
| **WYSIWYG editor** | Co vidíš v editoru, to vidíš na webu (Gutenberg, TinyMCE, CKEditor). |
| **Uživatelé a role** | Admin / Editor / Autor / Přispěvatel / Předplatitel. Granularní oprávnění. |
| **Šablony (themes)** | Vzhled webu — lze měnit bez ztráty obsahu. |
| **Pluginy / moduly / rozšíření** | Přidávají funkce — e-shop, formuláře, kalendář, SEO. |
| **Multilanguage** | Více jazykových verzí webu. |
| **SEO nástroje** | Meta tagy, sitemap.xml, structured data. |
| **Média manager** | Knihovna obrázků, videí, dokumentů. |
| **Komentáře, recenze** | Interakce s návštěvníky. |
| **Aktualizace** | Auto-update jádra, šablon, pluginů. |

### Výhody CMS

1. **Rychlost vývoje** — web stojí za pár dní, ne měsíců
2. **Nízká cena** — open-source CMS jsou zdarma
3. **Bez programátora** — redaktor zvládne obsah sám
4. **Velká komunita** — tisíce témat, pluginů, návodů
5. **Updaty a bezpečnost** — komunita opravuje chyby
6. **Standardizace** — strukturovaný kód, SEO friendly

### Nevýhody CMS

1. **Bezpečnost** — populární CMS jsou cíl útoků (zejména WordPress). Nutné pravidelně aktualizovat.
2. **Výkon** — zbytečně tlustý kód pro jednoduché weby (WordPress načítá ~100 souborů PHP na request).
3. **Vendor lock-in** — přechod z jednoho CMS na druhý je drahý.
4. **Pluginy ne vždy spolupracují** — konflikty, pomalý web.
5. **Omezení** — nestandardní funkce vyžadují programátora.
6. **Pravidelná údržba** — pluginy se musí aktualizovat, jinak hrozí napadení.

### Princip fungování CMS

```
+---------------------+
| Administrační UI    |  ← redaktor píše článek
| /wp-admin/          |
+----------+----------+
           ↓ (uloží)
+---------------------+
|     Databáze        |  ← uloží článek (texty, kategorie, autoři)
|  (typicky MySQL)    |
+----------+----------+
           ↓
+---------------------+
|  Šablony (themes)   |  ← načte data, zobrazí ve vzhledu šablony
|     + pluginy       |
+----------+----------+
           ↓
+---------------------+
|   HTML stránka      |  ← prohlížeč návštěvníka
+---------------------+
```

Konkrétně u WordPressu:
1. Návštěvník otevře `tjslavojmyto.cz/zapasy`
2. Apache pošle request do PHP → WordPress (`index.php`)
3. WordPress parsuje URL → najde, že má vykreslit archiv CPT `zapas`
4. Načte data z MySQL (tabulky `wp_posts`, `wp_postmeta`, `wp_terms`)
5. Najde šablonu podle hierarchie (`archive-zapas.php` → `archive.php` → `index.php`)
6. Spustí všechny aktivní pluginy přes hooks (filtry, akce)
7. Vygeneruje HTML a pošle zpět

### Hlavní představitelé CMS

#### WordPress (PHP + MySQL)
- **Nejpopulárnější CMS na světě** — ~43 % všech webů (2025).
- **Vznik:** 2003, vyvinul **Matt Mullenweg** jako fork b2/cafelog.
- **Open-source**, zdarma, GPL licence.
- **Použití:** blogy, firemní weby, e-shopy (WooCommerce), zpravodajské weby.
- **Výhody:** obrovský ekosystém (>60 000 pluginů), snadné použití, velká komunita.
- **Nevýhody:** terč útoků, výkon, závislost na pluginech.
- **Příklad:** TJ Slavoj Mýto (klubový web s vlastním tématem `tj-slavoj-myto` a pluginem `slavoj-custom-fields`).

#### Joomla (PHP + MySQL)
- **Vznik:** 2005, fork Mambo.
- Mezi WordPressem a Drupalem — silnější než WP, jednodušší než Drupal.
- **Použití:** firemní weby, portály, komunity.
- **Výhody:** silný systém oprávnění, vícejazyčnost out-of-the-box.
- **Nevýhody:** menší komunita než WordPress, učení křivka.

#### Drupal (PHP + MySQL/PostgreSQL)
- **Vznik:** 2001, vyvinul **Dries Buytaert**.
- **Nejvýkonnější** z trojice WP/Joomla/Drupal, ale nejsložitější.
- **Použití:** velké firemní weby, vládní portály, univerzity (např. weby Bílého domu, MIT, Tesla v minulosti).
- **Výhody:** vysoká bezpečnost, škálovatelnost, flexibilita.
- **Nevýhody:** strmá křivka učení, vyžaduje programátora.

#### Typo3 (PHP + MySQL)
- **Vznik:** 1998, vyvinul **Kasper Skårhøj**.
- Silný v **Německu a Evropě** (mimo USA méně).
- **Použití:** velké firemní weby, korporátní intranety.
- **Výhody:** robustní, vícejazyčnost, enterprise funkce.
- **Nevýhody:** složitý, drahý vývoj.

#### Ghost (Node.js + MySQL/SQLite)
- **Vznik:** 2013, založeno bývalým zaměstnancem WordPress (John O'Nolan).
- **Zaměření na blogy a publishing** (newslettery, členství).
- **Výhody:** moderní stack (Node.js), rychlý, krásný editor, vestavěné předplatné.
- **Nevýhody:** méně pluginů, méně univerzální.

#### Další zmiňované CMS

| CMS | Jazyk | Specifika |
|---|---|---|
| **Wix, Squarespace** | (cloud) | SaaS — drag-and-drop, bez instalace, ale uzamčené do platformy |
| **Shopify** | (cloud) | Specializovaný e-shop CMS |
| **Magento / Adobe Commerce** | PHP | E-shopy, robustní, drahý |
| **PrestaShop** | PHP | E-shopy, open-source |
| **OctoberCMS** | PHP (Laravel) | Programátorsky orientovaný CMS |
| **Webnode** | (cloud) | České SaaS řešení |

### Headless CMS — moderní trend

**Headless CMS** je CMS bez „hlavy" — tj. **bez prezentační vrstvy (View)**. Poskytuje jen **API** (REST nebo GraphQL), které vrací obsah ve formátu JSON. Frontend si pak postaví vývojář, jak chce (React, Vue, mobilní aplikace, IoT...).

#### Tradiční CMS vs Headless CMS

```
TRADIČNÍ (monolithic) CMS:
[Admin UI] → [Databáze] → [Šablony / Theme] → [HTML]
                            (CMS určuje vzhled)

HEADLESS CMS:
[Admin UI] → [Databáze] → [REST/GraphQL API] → [Libovolný frontend]
                            (vývojář si volí stack)
```

#### Výhody headless
- **Stejný obsah → více kanálů** (web, mobilní app, smart TV, IoT)
- **Moderní frontend stack** (Next.js, Nuxt, React Native)
- **Lepší výkon** (statické stránky generované buildem — JAMstack)
- **Lepší bezpečnost** (admin běží na jiné doméně než web)

#### Představitelé headless CMS
- **Strapi** (Node.js, open-source) — nejpopulárnější self-hosted headless CMS
- **Contentful** (SaaS) — enterprise, drahý
- **Sanity** (SaaS) — moderní, hybridní
- **Directus** (Node.js, open-source)
- **Ghost** umí oba režimy (klasický i headless)
- **WordPress jako headless** — od verze 4.7 má REST API, lze ho použít headless

### CMS vs vlastní řešení — kdy co?

| Situace | Doporučení |
|---|---|
| Blog, firemní web, klubový web (TJ Slavoj!) | **WordPress** — rychlé, levné |
| E-shop | WooCommerce (WordPress), Shopify, PrestaShop |
| Velký portál (zpravodajský, vládní) | **Drupal** nebo vlastní řešení v Laravel/Django |
| Mobilní app + web sdílí obsah | **Headless** (Strapi, Contentful) |
| Specifická aplikace (rezervace, CRM, ERP) | **Vlastní vývoj** (Laravel, Django, .NET) — CMS by byl omezující |

### Časté otázky komisaře

**Q: Co je CMS a k čemu slouží?**
A: Content Management System — software pro správu obsahu webu. Umožňuje redaktorům vytvářet a upravovat obsah bez znalosti HTML/CSS přes administrační rozhraní.

**Q: Vyjmenujte alespoň tři redakční systémy.**
A: WordPress, Joomla, Drupal. Dále Typo3, Ghost, Magento.

**Q: Jaké jsou výhody a nevýhody CMS?**
A: + Rychlý vývoj, nízká cena, redaktor zvládne obsah sám, velká komunita.
   − Bezpečnostní rizika (terč útoků), výkon, závislost na pluginech, omezené přizpůsobení.

**Q: Jak funguje WordPress?**
A: Běží v PHP, používá databázi MySQL. Obsah ukládá do tabulek (wp_posts, wp_postmeta). Vzhled řeší přes témata (themes), funkce přes pluginy. Když přijde request, WordPress podle URL najde správnou šablonu, načte data z DB a vrátí HTML.

**Q: Co je headless CMS a k čemu se používá?**
A: CMS bez prezentační vrstvy — poskytuje pouze API. Frontend si pak postaví vývojář v libovolné technologii (React, Vue, mobilní app). Používá se, když chceme stejný obsah ve více kanálech (web + mobil + smart TV).

**Q: Z čeho se skládá WordPress?**
A: Z jádra (core PHP soubory), databáze MySQL, témat (themes — vzhled) a pluginů (rozšíření funkcí). Admin rozhraní je v `/wp-admin/`.

**Q: Co jsou pluginy a šablony?**
A: Šablona (theme) určuje vzhled webu — barvy, layout, fonty. Plugin přidává funkce — kontaktní formulář, e-shop, SEO. Šablona = jak web vypadá, plugin = co web umí.

**Q: Jaký je rozdíl mezi WordPress.com a WordPress.org?**
A: WordPress.org je open-source software, který si stáhnete a nainstalujete na vlastní hosting. WordPress.com je hostovaná verze (SaaS) — neinstalujete nic, ale máte omezení (např. ne všechny pluginy jdou ve freemium verzi).

---

## Souhrn klíčových pojmů

Student musí umět vysvětlit:

1. **Frontend** — klientská strana, HTML/CSS/JS, prohlížeč
2. **Backend** — serverová strana, PHP/Python/Node, databáze
3. **Full-stack** — programátor obojího
4. **HTTP** — protokol webu, port 80, stateless, request/response
5. **HTTPS** — HTTP + TLS/SSL šifrování, port 443
6. **TLS/SSL** — kryptografický protokol pro zabezpečení
7. **SSL certifikát** — digitální certifikát vystavený CA
8. **FTP / FTPS / SFTP** — protokoly pro přenos souborů, rozdíly
9. **HTTP metody** — GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS
10. **HTTP stavové kódy** — 200, 301, 401, 403, 404, 500
11. **DNS** — překlad domén na IP
12. **Klient-server model** — kdo iniciuje, kdo odpovídá
13. **Request/response cyklus** — průběh od URL po vykreslení
14. **Stateless** — bezstavovost HTTP
15. **Cookies** — uložení dat u klienta
16. **Sessions** — uložení dat na serveru, drženy přes session ID v cookie
17. **REST / RESTful API** — architektonický styl, URL jako zdroje
18. **JSON** — formát pro výměnu dat
19. **MVC** — Model-View-Controller, Trygve Reenskaug, Smalltalk
20. **Model / View / Controller** — role každé vrstvy
21. **MVP / MVVM** — varianty MVC
22. **CMS** — Content Management System
23. **WordPress** — nejpopulárnější CMS, PHP + MySQL
24. **Theme (šablona)** vs **Plugin** — co je co
25. **Headless CMS** — CMS poskytující jen API (Strapi, Contentful)

---

## Možné praktické úkoly u zkoušky

Komisař může chtít, aby student:

1. **Načrtnul diagram MVC** — tři komponenty se šipkami, kdo s kým komunikuje, kde je databáze, kde je uživatel.

2. **Načrtnul průběh request/response** — od zadání URL v prohlížeči přes DNS, TCP, TLS, HTTP request, server, databázi, response, render.

3. **Vysvětlil rozdíl HTTP vs HTTPS** na konkrétním příkladu — co se stane, když uživatel na nezabezpečené Wi-Fi v kavárně zadá heslo do nešifrovaného webu.

4. **Vyjmenoval a popsal HTTP metody** s příkladem každé — `GET /clanky` (čtení), `POST /clanky` (vytvoření).

5. **Vysvětlil stavové kódy** — co znamená 404, 500, 301, 200, 401, 403, a kdy je server vrací.

6. **Popsal, jak funguje cookie a session** — k čemu jsou, jak prohlížeč drží přihlášení.

7. **Načrtnul strukturu webu na WordPressu** — kde je jádro, kde téma, kde plugin, kde admin, kde databáze.

8. **Vysvětlil REST API** — co je „zdroj", jak se mapují HTTP metody na operace (CRUD: Create=POST, Read=GET, Update=PUT/PATCH, Delete=DELETE).

9. **Popsal rozdíl mezi klasickým a headless CMS** — kde končí CMS, kde začíná frontend.

10. **Vysvětlil bezpečnostní rizika webových aplikací** — proč FTP není dobrý nápad, proč potřebujeme HTTPS, proč se musí aktualizovat pluginy.

11. **Vyjmenoval reprezentanty různých CMS** a řekl, pro jaký typ webu by co zvolil (osobní blog → WordPress; korporátní portál → Drupal; e-shop → WooCommerce/Shopify; mobilní app + web → headless Strapi).

12. **Načrtl jednoduchou architekturu klient-server** — prohlížeč → internet → webový server → aplikační server → databáze.

---

## Tipy pro lektora

- Stefano si může praktickou ukázku osahat přímo ve **WordPressu** (TJ Slavoj Mýto) — kde je admin, kde téma, kde plugin, jak vzniká custom post type, jak se data ukládají do MySQL.
- Při výkladu MVC použijte **konkrétní příklad z TJ Slavoj** — Model = `WP_Query` pro CPT `zapas`, View = `single-zapas.php`, Controller = `functions.php` + hooks.
- HTTP/HTTPS lze demonstrovat v prohlížeči přes **DevTools → Network tab** — ukázat reálné requesty, hlavičky, stavové kódy, cookies.
- REST se dá vyzkoušet i na WordPressu (`https://web.cz/wp-json/wp/v2/posts` vrací JSON).
- Pro FTP/SFTP stáhněte **FileZilla** a propojte se přes SFTP s jakýmkoliv hostingem nebo lokálním SSH serverem — student uvidí přenos v praxi.
- Doporučte studentovi mít **schéma průběhu request/response nakreslené na papíře** — komisaři často chtějí, aby student kreslil u zkoušky.
