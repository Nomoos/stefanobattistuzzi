---
marp: true
theme: default
size: 16:9
paginate: true
backgroundColor: '#ffffff'
color: '#1a1a1a'
style: |
  section {
    font-family: 'Segoe UI', 'Helvetica', sans-serif;
    font-size: 26px;
    padding: 50px 70px;
  }
  h1 {
    color: #b30000;
    font-size: 42px;
    border-bottom: 3px solid #b30000;
    padding-bottom: 10px;
    margin-bottom: 25px;
  }
  h2 {
    color: #b30000;
    font-size: 32px;
  }
  table {
    font-size: 22px;
    border-collapse: collapse;
    margin: 10px 0;
  }
  th {
    background-color: #b30000;
    color: #ffffff;
    padding: 8px 14px;
    text-align: left;
  }
  td {
    padding: 6px 14px;
    border-bottom: 1px solid #cccccc;
  }
  code {
    background-color: #f4f4f4;
    padding: 2px 6px;
    border-radius: 3px;
    font-size: 22px;
  }
  pre {
    background-color: #1e1e1e;
    color: #d4d4d4;
    padding: 16px 20px;
    border-radius: 6px;
    font-size: 18px;
    line-height: 1.4;
  }
  pre code {
    background: transparent;
    color: inherit;
    padding: 0;
  }
  .small { font-size: 20px; }
  .tiny { font-size: 16px; }
  .center { text-align: center; }
  .lead h1 { font-size: 50px; border: none; }
  .lead { text-align: center; }
  .ok { color: #006400; font-weight: 600; }
  .warn { color: #cc6600; font-weight: 600; }
  .err { color: #b30000; font-weight: 600; }
  footer { color: #888; font-size: 14px; }
---

<!-- _class: lead -->

# Webový portál CarzMeetz

## Platforma pro organizaci autosrazů

<br>

**Autor:** Stefano Battistuzzi
**Třída:** S4C · **Obor:** Informační technologie 18-20-M/01 · **Rok:** 2025/2026

<br>

**Vedoucí:** Ing. Dalibor Slovák Ph.D., dipl. um. · **Oponent:** Ing. Jakub Josef Forman
**Škola:** ORBIS Zlín

<!-- Web nasazený na: carzmeetz.euweb.cz -->

---

# Úvod, cíl a technologie

**Cíl projektu:** Vytvořit moderní webový portál pro komunitu automobilových nadšenců — sdílení informací o autosrazech, registrace uživatelů, galerie.

<br>

| Vrstva | Použito |
|---|---|
| Backend | **PHP** (procedurální) |
| Databáze | **SQLite** přes PDO |
| Frontend | HTML5, CSS3 (mobile-first), vanilla JavaScript |
| Vývojové IDE | PhpStorm |
| Hosting | euweb.cz · web: **carzmeetz.euweb.cz** |

<br>

> **Záměrně bez moderního frameworku** (Laravel, Symfony) — vědomá volba pro pochopení principů.

---

# Architektura a implementace

<div class="small">

```text
Prohlížeč (HTML + CSS + JS)
        ↓ HTTP
Webhosting euweb.cz
  ├─ index.php · srazy.php · galerie.php · about.php · kontakt.php
  ├─ register.php  · login.php  · hamburger.php (mobile menu)
        ↓ PDO
SQLite databáze: users.db · gallery.sqlite
```

</div>

**Proč žádný framework — tři důvody:**

1. **Porozumění principům** — Laravel abstrahuje routing, autentizaci, ORM. Bez něj jsem si je musel napsat sám.
2. **Velikost projektu** — pro 6 prezentačních stránek by Composer + Laravel byl overkill.
3. **Snadné nasazení** — FTP upload PHP souborů + SQLite, žádné `composer install`, žádné migrace.

> **Pro produkci** bych přešel na **Laravel** kvůli vyzrálé autentizaci, CSRF ochraně, validaci a ORM Eloquent.

---

# Bezpečnost a databáze

<div class="small">

| <span class="ok">✅ Implementováno</span> | <span class="warn">⚠️ Chybí pro produkci</span> |
|---|---|
| `password_hash()` + **bcrypt** | HTTPS / TLS |
| `password_verify()` | CSRF tokeny ve formulářích |
| **Prepared statements** (PDO `bindValue`) | `session_regenerate_id()` po loginu |
| `htmlspecialchars()` na výstupu (XSS) | Rate limiting na login |
| `session_start()` v login | Verifikace e-mailu při registraci |
|  | `logout.php` (odhlášení) |

</div>

```php
// register.php — hash, ne plaintext
$hash = password_hash($password, PASSWORD_DEFAULT);
$stmt->bindValue(':password', $hash, PDO::PARAM_STR);

// login.php — konstantní čas porovnání
if (password_verify($password, $user['password_hash'])) {
    $_SESSION['user_id'] = $user['id'];
}
```

> **SQLite** — bez serveru, jeden soubor, vhodný pro maturitu. **Limit:** write-locking, žádný vzdálený přístup.

---

# Vizuální ukázky webu

<div class="small">

- **Homepage** — hero sekce + sekce o klubu + statistiky
- **Registrace + Login** — formuláře s validací, login přes `fetch()` (AJAX)
- **Galerie** — fotky dynamicky načítané z `gallery.sqlite`
- **Mobilní zobrazení** — hamburger menu pod 768 px, CSS transition

</div>

<br>

> **URL hostingu:** [carzmeetz.euweb.cz](http://carzmeetz.euweb.cz)
> *Web mám otevřený v prohlížeči — v rámci dotazů ho ukážu živě.*

<!-- Doplnit screenshoty: 4 obrázky v gridu 2×2: homepage, registrace, galerie, mobilní pohled -->

---

# Analýza, metody a testování

<div class="small">

**🔍 Analýza konkurence**

- Srazy.info (fórum pro autosrazy)
- AutoMotoSrazy (Facebook skupiny)
- Auto-srazy.eu (informační portál)

**📋 Metody návrhu**

- Rešerše požadavků komunity (neformální dotazování)
- Definice MVP funkcí: registrace, galerie, info o srazech
- Iterativní implementace HTML/CSS přímo v PhpStormu

**🧪 Testování**

- Manuální průchod všemi stránkami
- Responzivita: Chrome DevTools (mobile / tablet / desktop)
- HTML validita: **W3C validátor**

</div>

---

# Slabá místa a rozšíření

<div class="tiny">

| Mezera | Stav | Plán pro produkční verzi |
|---|---|---|
| **HTTPS** chybí (free euweb HTTPS nemá) | nedostatek hostingu | placený hosting + **Let's Encrypt** |
| **CSRF tokeny** ve formulářích | chybí | random token v session, ověření před submitem |
| **Logout** + `session_regenerate_id` | chybí | `logout.php` + regenerování po loginu |
| **Verifikace e-mailu** + rate limit | chybí | confirmation link, počítadlo neúspěšných pokusů |
| **Dokumentace** popisná, ne technická | uznáno z posudku | doplnit architekturu + ER diagram |
| **Pravopis / čísla citací** | uznáno z posudku | reference manager **Zotero** + korektura |
| **Žádný framework** | vědomá volba | **Laravel** pro produkci |
| **SQLite** | dostatečné pro maturitu | **PostgreSQL + PostGIS** pro mapu autosrazů |

</div>

---

<!-- _class: lead -->

# Děkuji za pozornost

<br>

<div class="small">

| ✅ Hotovo | 🔄 Rozšiřitelné | 🎯 Výsledek |
|----------|----------------|-------------|
| 6 stránek, registrace, galerie | HTTPS + CSRF + logout | funkční portál |
| bcrypt + prepared statements | Laravel + MySQL pro produkci | vlastní programátorský základ |
| responzivní design | technická dokumentace | nasazený na **carzmeetz.euweb.cz** |

</div>

<br>

**Web mám otevřený v prohlížeči pro případné dotazy.**
