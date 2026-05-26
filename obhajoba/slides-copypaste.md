# Copy-paste sheet pro Google Slides / PowerPoint

> **Pro koho:** Stefano, při manuální tvorbě/opravě slidů.
> **Jak používat:** Otevři Google Slides → Blank prezentace (nebo stávající PPTX) → pro každý slide níže buď vytvoř nový slide, nebo přepiš existující obsah. Paste TITULEK + OBSAH + (volitelně) SPEAKER NOTES.
> **Speaker notes:** v Google Slides klikni dolů na panel „Click to add speaker notes" — paste tam mluvený text. V PowerPointu klikni na View → Notes Page nebo na panel pod slidem.

---

## SLIDE 1 — Titulní (0:30)

### TITULEK
Webový portál CarzMeetz
Platforma pro organizaci autosrazů

### OBSAH
Autor: Stefano Battistuzzi
Třída: S4C · Obor: Informační technologie 18-20-M/01
Rok: 2025/2026

Vedoucí: Ing. Dalibor Slovák Ph.D., dipl. um.
Oponent: Ing. Jakub Josef Forman

ORBIS Zlín
Web: carzmeetz.euweb.cz

### SPEAKER NOTES
Dobrý den, jmenuji se Stefano Battistuzzi a obhajuji maturitní práci na téma Webový portál CarzMeetz — platformu pro organizaci autosrazů. Vedoucím práce byl pan Slovák, oponentem pan Forman. Web je nasazený na adrese carzmeetz.euweb.cz. Pokud bude komise chtít, otevřu ho v rámci dotazů živě v prohlížeči.

---

## SLIDE 2 — Úvod, cíl a technologie (1:00)

### TITULEK
Úvod, cíl a technologie

### OBSAH
Cíl projektu:
Vytvořit moderní webový portál pro komunitu automobilových nadšenců — sdílení informací o autosrazech, registrace uživatelů, galerie.

Použité technologie:
| Vrstva | Použito |
|--------|---------|
| Backend | PHP (procedurální) |
| Databáze | SQLite přes PDO |
| Frontend | HTML5, CSS3 (mobile-first), vanilla JavaScript |
| IDE | PhpStorm |
| Hosting | euweb.cz · carzmeetz.euweb.cz |

Záměrně bez moderního frameworku (Laravel, Symfony) — vědomá volba pro pochopení principů.

### SPEAKER NOTES
Cílem projektu bylo vytvořit moderní webový portál pro komunitu automobilových nadšenců, který umožňuje sdílení informací o autosrazech, registraci uživatelů a správu galerie. Web je responzivní a běží na webhostingu.

Technologicky je projekt postaven na PHP s databází SQLite přes vrstvu PDO. Frontend je v čistém HTML5, CSS3 s mobile-first přístupem a vanilla JavaScriptu. Záměrně jsem nepoužil žádný moderní framework jako Laravel nebo Symfony — důvody rozeberu na příštím slidu. Vývojové prostředí bylo PhpStorm, web je nasazený na free hostingu euweb.cz.

---

## SLIDE 3 — Architektura a implementace (2:00)

### TITULEK
Architektura a implementace

### OBSAH
Struktura projektu:
Prohlížeč (HTML + CSS + JS)
        ↓ HTTP
Webhosting euweb.cz
  ├─ index.php · srazy.php · galerie.php · about.php · kontakt.php
  ├─ register.php · login.php · hamburger.php (mobile menu)
        ↓ PDO
SQLite databáze: users.db · gallery.sqlite

Proč žádný framework — tři důvody:
1. Porozumění principům — Laravel abstrahuje routing, autentizaci, ORM. Bez něj jsem si je musel napsat sám.
2. Velikost projektu — pro 6 prezentačních stránek by Laravel byl overkill.
3. Snadné nasazení — FTP upload PHP souborů + SQLite, žádné composer install ani migrace.

Pro produkci bych přešel na Laravel kvůli vyzrálé autentizaci, CSRF ochraně, validaci a ORM Eloquent.

### SPEAKER NOTES
Projekt má procedurální architekturu — žádný framework jako Laravel nebo Symfony. Každá stránka je samostatný PHP soubor, který kombinuje HTML šablonu s aplikační logikou. Databázová vrstva je řešena přes PDO s prepared statements.

Klíčové rozhodnutí — proč jsem nepoužil moderní framework. Volba čistého PHP byla úmyslná, ze tří důvodů.

Za prvé, chtěl jsem rozumět tomu, jak weby fungují „pod kapotou". Frameworky jako Laravel abstrahují routing, autentizaci, ORM, šablonování. Bez frameworku jsem si tyto věci musel napsat sám, takže přesně vím, co se kde děje. Pokud později budu pracovat ve frameworku, budu mít pevný základ.

Za druhé, pro projekt tohoto rozsahu by byl Laravel overkill. Web má pět prezentačních stránek, registraci a galerii — pět minimálně. Instalovat kvůli tomu Composer balíček s několika sty závislostmi nemělo smysl.

Za třetí, jednodušší nasazení. Stačí nahrát PHP soubory a SQLite databázi přes FTP na hosting, žádné composer install, žádné databázové migrace, žádné kompilace assetů.

Kdy bych framework použil. Pokud by projekt měl jít do produkce pro tisíce uživatelů, určitě bych přešel na Laravel — kvůli vyzrálé autentizaci s CSRF ochranou, validaci formulářů přes Request třídy, ORM Eloquent, migracemi databáze, queue pro odesílání e-mailů, a hlavně lepší bezpečnosti out-of-the-box. Pro maturitní práci ale byla volba čistého PHP správnější.

---

## SLIDE 4 — Bezpečnost a databáze (2:00)

### TITULEK
Bezpečnost a databáze

### OBSAH (tabulka)
| ✅ Implementováno | ⚠️ Chybí pro produkci |
|-------------------|----------------------|
| password_hash() + bcrypt | HTTPS / TLS |
| password_verify() | CSRF tokeny ve formulářích |
| Prepared statements (PDO bindValue) | session_regenerate_id() po loginu |
| htmlspecialchars() na výstupu (XSS) | Rate limiting na login |
| session_start() v login | Verifikace e-mailu |
|  | logout.php (odhlášení) |

Ukázka kódu:
// register.php — hash, ne plaintext
$hash = password_hash($password, PASSWORD_DEFAULT);
$stmt->bindValue(':password', $hash, PDO::PARAM_STR);

// login.php — konstantní čas porovnání
if (password_verify($password, $user['password_hash'])) {
    $_SESSION['user_id'] = $user['id'];
}

SQLite — bez serveru, jeden soubor, vhodný pro maturitu. Limit: write-locking, žádný vzdálený přístup.

### SPEAKER NOTES
Bezpečnost a práce s databází je oblast, kde můj projekt udělal základní kroky správně, ale několik produkčních prvků zatím nemá.

Co je v projektu hotové. Hesla se v databázi nikdy neukládají v plaintextu. Při registraci je hashuji funkcí password_hash() s výchozím algoritmem bcrypt, který automaticky generuje náhodnou sůl. Při loginu pak password_verify() v konstantním čase porovná zadané heslo s uloženým hashem. Všechny SQL dotazy používají prepared statements s pojmenovanými parametry přes bindValue() — uživatelský vstup se nikdy nelepí přímo do SQL stringu, takže riziko SQL injection je eliminováno. Při výpisu uživatelských dat používám htmlspecialchars() proti XSS. Po úspěšném loginu vytvořím PHP session a uložím do ní user_id.

Databáze. Zvolil jsem SQLite ze tří důvodů: nepotřebuje samostatný databázový server, je to jeden soubor, PHP má vestavěnou podporu přes PDO. Pro malou komunitu nadšenců je výkon dostatečný. Hlavní limit SQLite je, že zamyká celý soubor při zápisu, takže pro vysoký objem souběžných zápisů by bylo nutné přejít na MySQL nebo PostgreSQL. Pro produkční verzi s mapou autosrazů by se hodil zejména PostgreSQL s rozšířením PostGIS pro geografická data.

Co projektu chybí pro reálný provoz. Chybí mi HTTPS — free euweb HTTPS nepodporuje, na placeném hostingu by se přidalo přes Let's Encrypt. Chybí CSRF tokeny ve formulářích, rate limiting na login proti brute-force, verifikace e-mailu při registraci, regenerování session ID po loginu proti session fixation, a chybí odhlášení. Tyto věci uznávám jako mezery a v produkční verzi bych je doplnil.

---

## SLIDE 5 — Vizuální ukázky webu (0:50)

### TITULEK
Vizuální ukázky webu

### OBSAH
• Homepage — hero sekce + sekce o klubu + statistiky
• Registrace + Login — formuláře, login přes fetch() (AJAX)
• Galerie — fotky dynamicky načítané z gallery.sqlite
• Mobilní zobrazení — hamburger menu pod 768 px, CSS transition

URL hostingu: carzmeetz.euweb.cz
Web mám otevřený v prohlížeči — v rámci dotazů ho ukážu živě.

### SPEAKER NOTES
Web obsahuje šest hlavních stránek: domovskou, srazy, galerii, o nás, kontakt a registraci. Galerie je dynamická — fotky se načítají z SQLite databáze přes PDO query, takže administrátor může přidávat snímky bez úpravy kódu. Design je mobile-first, navigace na mobilu používá hamburger menu pod hranicí 768 pixelů, které se vysune zprava pomocí CSS transition. Web je nasazený na hostingu euweb.cz, v rámci dotazů ho otevřu živě, pokud bude komise chtít cokoliv vidět.

---

## SLIDE 6 — Analýza, metody a testování (1:20)

### TITULEK
Analýza, metody a testování

### OBSAH
🔍 Analýza konkurence
• Srazy.info (fórum pro autosrazy)
• AutoMotoSrazy (Facebook skupiny)
• Auto-srazy.eu (informační portál)

📋 Metody návrhu
• Rešerše požadavků komunity (neformální dotazování)
• Definice MVP funkcí: registrace, galerie, info o srazech
• Iterativní implementace HTML/CSS přímo v PhpStormu

🧪 Testování
• Manuální průchod všemi stránkami
• Responzivita: Chrome DevTools (mobile / tablet / desktop)
• HTML validita: W3C validátor

### SPEAKER NOTES
Analytická část projektu vycházela ze srovnávací analýzy existujících platforem pro autosrazy. Studoval jsem zejména Srazy.info a několik komunitních skupin na Facebooku — chtěl jsem ověřit, které funkce už existují a které uživatelům chybí. Z toho vznikl seznam MVP funkcí: registrace, galerie, informace o srazech.

Návrh jsem vedl iterativně. Nejprve jsem si rozkreslil základní layout pro hlavní stránky, pak jsem postupně implementoval HTML a CSS přímo v PhpStormu — bez Figmy nebo jiného grafického nástroje, protože pro projekt této velikosti to nebylo potřeba. Funkčnost backendu jsem řešil postupně: nejdřív statická HTML, pak databáze, pak registrace, pak galerie načítaná z DB.

Testování bylo manuální — automatizované testy v projektu nejsou. Procházel jsem všechny stránky, zkoušel registraci s různými hesly, ověřoval responzivitu v Chrome DevTools v módech mobile, tablet i desktop. Pro validitu HTML jsem použil W3C validátor. V produkční verzi bych přidal PHPUnit unit testy alespoň pro password handling, ale pro maturitní rozsah jsem to nepovažoval za nutné.

---

## SLIDE 7 — Slabá místa a rozšíření (1:50)

### TITULEK
Slabá místa a rozšíření

### OBSAH (tabulka)
| Mezera | Stav | Plán pro produkční verzi |
|--------|------|--------------------------|
| HTTPS chybí (free euweb HTTPS nemá) | nedostatek hostingu | placený hosting + Let's Encrypt |
| CSRF tokeny ve formulářích | chybí | random token v session, ověření před submitem |
| Logout + session_regenerate_id | chybí | logout.php + regenerování po loginu |
| Verifikace e-mailu + rate limit | chybí | confirmation link, počítadlo neúspěšných pokusů |
| Dokumentace popisná, ne technická | uznáno z posudku | doplnit architekturu + ER diagram |
| Pravopis / čísla citací | uznáno z posudku | reference manager Zotero + korektura |
| Žádný framework | vědomá volba | Laravel pro produkci |
| Pouze SQLite | dostatečné pro maturitu | PostgreSQL + PostGIS pro mapu autosrazů |

### SPEAKER NOTES
Závěrem chci sám zmínit body, které v práci považuji za slabší nebo mezery, na které mi posudky upozornily.

HTTPS — toto je důležitá mezera. Free euweb hosting HTTPS neposkytuje, takže hesla a session cookies se aktuálně přenášejí v plaintextu. V produkční verzi bych přešel na placený hosting s Let's Encrypt certifikátem, který je zdarma a automaticky obnovovaný.

CSRF tokeny a regenerování session ID — toto jsou oprávněné připomínky vedoucího v posudku. Můj projekt nemá obranu proti CSRF útokům ani proti session fixation. Doplnil bych random token uložený v session, který by se ověřoval při každém POST submitu, a po úspěšném loginu bych volal session_regenerate_id(true).

Logout a verifikace e-mailu — také uznané mezery. Implementoval bych klasický logout.php se session_destroy() a confirmation link při registraci s tokenem v URL.

Použití jiné databáze než SQLite — pokud bych projekt rozšiřoval do produkce, MySQL nebo MariaDB by přinesly podporu plně konkurentních zápisů, vzdálený přístup po síti a lepší správu uživatelů. Pro mou doménu — mapování autosrazů na území Česka — by se ale ideálně hodil PostgreSQL s rozšířením PostGIS pro geografická data a indexování souřadnic.

Dokumentace a citace — pan vedoucí v posudku připomíná, že dokumentace praktické části je popsaná spíše uživatelsky a čísla citací v bibliografii jsou nesprávná. Obojí přijímám — pro další práci bych použil reference manager Zotero, který sleduje propojení odkazů, a dokumentaci bych rozšířil o technickou sekci s architekturou a schématem databáze.

---

## SLIDE 8 — Závěr (0:30)

### TITULEK
Děkuji za pozornost

### OBSAH
✅ 6 stránek, registrace, galerie
✅ bcrypt + prepared statements
✅ responzivní design
🔄 HTTPS + CSRF + logout (plán)
🔄 Laravel + MySQL pro produkci
🎯 Funkční portál nasazený na carzmeetz.euweb.cz
🎯 Vlastní programátorský základ bez frameworku

Web mám otevřený v prohlížeči pro případné dotazy.

### SPEAKER NOTES
Projekt splňuje stanovené cíle — vytvořil jsem funkční webový portál s registrací, galerií a informacemi o autosrazech, nasazený na hostingu. Hlavním přínosem je vlastní programátorský základ bez závislosti na frameworku, díky kterému jsem získal hluboké porozumění tomu, jak weby fungují. Pro produkční nasazení by bylo nutné doplnit HTTPS, CSRF ochranu, logout a zvážit přechod na Laravel s databází vhodnou pro geografická data. Děkuji za pozornost. Web mám otevřený v prohlížeči, takže pokud bude komise chtít cokoliv vidět živě, mohu se kdykoli přepnout. Jsem připraven na otázky.

---

## DOPLNĚNÍ OBRÁZKŮ

Slidy 1, 3, 5 mohou mít obrázky:

| Slide | Doporučený obrázek |
|-------|---------------------|
| 1 | Logo CarzMeetz (z `images/carzmeetz_logo1.png` v ZIPu projektu) vpravo dole |
| 3 | Diagram struktury projektu (ASCII v OBSAH se dá nahradit pěkným box-and-arrow obrázkem) |
| 5 | 4 thumbnaily v gridu 2×2: homepage, registrace, galerie, mobilní pohled s hamburgerem |
| 7 | (nepotřeba — tabulka mluví sama) |

Zdroje pro screenshoty:
- Web: otevři carzmeetz.euweb.cz → příslušnou stránku → Print Screen (Win+Shift+S)
- Mobilní pohled: Chrome DevTools → F12 → Toggle device toolbar (Ctrl+Shift+M) → vybrat iPhone/Pixel
- Logo: z `untitled/images/carzmeetz_logo1.png` v rozbaleném ZIPu

---

## DESIGN SETTINGS pro Google Slides / PowerPoint

- **Téma:** Simple Light nebo Basic (bílé pozadí — DOPORUČENO pro kmenovou třídu kvůli kontrastu)
  - Alternativa: tmavé pozadí jak má stávající Stefanův PPTX — funguje, ale v třídě s denním světlem se hůř čte
- **Fonty:**
  - Title — **Orbitron** (sportovní/auto vibe) nebo Roboto, 36–42 pt
  - Body — Inter / Roboto / Open Sans, 22–26 pt
- **Barvy** (auto-styl):
  - Pozadí: bílá (#FFFFFF) nebo světle šedá (#F5F5F5)
  - Text: tmavě šedá (#1A1A1A) — NE čistá černá kvůli kontrastu
  - Akcent (nadpisy, proužky): **CarzMeetz červená/oranžová** (#B30000 nebo #FF4500)
  - Sekundární akcent: tmavě šedá (#333333)
- **Tabulky:** hlavička barevná (akcent), řádky střídavě jemně podbarvené
- **Page numbers:** zapnout (Slide → Layout → with footer)

---

## TIP: Generování přes Marp (rychlejší než ruční tvorba)

Pokud Stefano nainstaloval Node.js / npm:

```bash
# Instalace Marp CLI (jednou)
npm install -g @marp-team/marp-cli

# Export do PPTX (ze složky obhajoba/)
marp prezentace.md --pptx --output prezentace-vygenerovana.pptx

# Nebo náhled v HTML
marp prezentace.md --html --output prezentace-vygenerovana.html
```

Pak nahraj `prezentace-vygenerovana.pptx` do Google Slides nebo otevři v PowerPointu. **Marp vygeneruje formát, který je už hotový — stačí doplnit screenshoty.**

Alternativa bez instalace: nahrát `prezentace.md` do online Marp editoru: https://web.marp.app
