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
  h3 {
    color: #333333;
    font-size: 24px;
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
  blockquote {
    border-left: 4px solid #b30000;
    padding-left: 16px;
    color: #555;
    font-style: italic;
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

# Webový portál

## CarzMeetz — platforma pro organizaci autosrazů

<br>

**Autor:** Stefano Battistuzzi
**Třída:** S4C · **Obor:** Informační technologie 18-20-M/01 · **Rok:** 2025/2026

<br>

**Vedoucí práce:** Ing. Dalibor Slovák Ph.D., dipl. um.
**Škola:** ORBIS, MŠ/ZŠ/SŠ s.r.o., Zlín

<!-- Web nasazený na: carzmeetz.euweb.cz -->

---

# Úvod

### 🎯 Téma

Webový portál CarzMeetz pro komunitu **automobilových nadšenců** — osobní zájem o auta + reálná potřeba v komunitě.

### 📌 Cíl práce

> „Ukázat problematiku tvorby webových stránek a portálů a demonstrovat jejich funkčnost na praktickém příkladu." — *citace z úvodu MP*

Konkrétně: **funkční web s databází** pro zobrazování informací o srazech a registraci uživatelů.

### ⚙️ Postup zpracování

1. **Teoretická část** — HTML, CSS, JavaScript, SQLite, historie webu
2. **Praktická část** — návrh, implementace, nasazení webu CarzMeetz
3. **Iterativně:** HTML → CSS → JavaScript → PHP → SQLite → hosting

---

# Praktická část

### 📋 Charakteristika tématu

Webový portál CarzMeetz pro komunitu nadšenců v ČR. **6 hlavních stránek** — Domů, Srazy, Galerie, O nás, Kontakt, Účet. **2 SQLite databáze** — uživatelé + galerie. **Responzivní design** s mobilním hamburger menu.

### 🔍 Použité analytické metody

| Metoda | Popis |
|---|---|
| **Srovnávací analýza** | Studium konkurence: Srazy.info, FB skupiny |
| **Rešerše požadavků** | Neformální dotazování v komunitě |
| **Návrh struktury** | Definice MVP: registrace, galerie, info |
| **Iterativní vývoj** | Postupně od statického HTML k PHP + DB |
| **Manuální testování** | DevTools, W3C validátor, scénáře |

### ❓ Proč tyto metody

Vhodné pro **komunitní projekt menšího rozsahu** — kvalitativní přístup je dostatečný, akademický výzkum by byl overkill.

---

# Projektové řešení

### 🏗️ Hlavní zásady

| Zásada | Detail |
|---|---|
| **Procedurální PHP**, bez frameworku | Vlastní implementace — pochopení principů |
| **SQLite + PDO** | Embedded DB, jeden soubor, žádný server |
| **Bezpečné heslování** | `password_hash()` bcrypt + `password_verify()` |
| **Prepared statements** | `bindValue()` proti SQL injection |
| **Responzivní design** | Mobile-first, hamburger pod 768 px |

### 💡 Co řešení přináší praxi

Funkční MVP komunitního portálu nasazený na hostingu · **6 testovacích uživatelů + 6 fotek v galerii** · vlastní programátorský základ.

### 📌 Limity a budoucí kroky

<div class="tiny">

| Mezera | Plán pro produkční verzi |
|---|---|
| Bez frameworku → procedurální | **Laravel** pro produkci (CSRF, auth, ORM) |
| SQLite write-locking | **PostgreSQL + PostGIS** pro mapu autosrazů |
| Free euweb bez HTTPS | placený hosting + **Let's Encrypt** |
| Chybí CSRF, logout, regenerate session | doplnit pro reálný provoz |

</div>

---

# Závěr

### ✅ Dosažení cílů

> „Cíl se podařilo splnit — vytvořil jsem funkční web s databází, který umožňuje zobrazování informací o srazech a práci s nimi." — *citace ze závěru MP*

### 🎓 Jak mě práce obohatila

- Rozšíření znalostí **HTML, CSS, JavaScriptu a PHP**
- První zkušenost s databází **SQLite** + propojení s webem
- Reálný projekt **nasazený na hostingu**

### 🔮 Pokračování práce

Vytvoření web v podobném stylu a další rozvoj — kalendář srazů, mapa, profily uživatelů, UX testování.

### 🎯 Osobní přínos

**Vědomá volba vlastní implementace bez frameworku** → hluboké porozumění tomu, jak weby fungují. Tuto znalost využiji v dalším studiu i praxi.

---

# Otázky komise

### ❓ Otázky vedoucího práce (Ing. Slovák)

<div class="small">

1. **Jak funguje registrace a hashování hesla?** → bcrypt, prepared statements, PHP session *(viz slide 4)*
2. **Proč SQLite a jeho limity?** → embedded, zero-config, write-locking limit *(viz slide 4)*
3. **Bezpečnostní prvky pro reálný provoz?** → HTTPS, CSRF, rate limit, verifikace e-mailu, logout

</div>

### ❓ Otázky oponenta (Ing. Forman)

<div class="small">

4. **Výhody jiné databáze?** → MySQL pro konkurenci · **PostgreSQL + PostGIS pro mapu autosrazů**
5. **Proč žádný framework?** → vědomá volba pro pochopení principů · **Laravel pro produkci**

</div>

<br>

> *Klíčová slova k odpovědím — všechny otázky pokrývá slide 4 (Projektové řešení).*

---

<!-- _class: lead -->

# Děkuji za pozornost

<br>

## 🌐 carzmeetz.euweb.cz

<br>

**Web mám otevřený v prohlížeči pro případné dotazy.**

<br>

*Stefano Battistuzzi · S4C · 2025/2026*
