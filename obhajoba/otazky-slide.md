# Slide „Otázky komise" — dotazy z posudků

**Soubor pro tisk / rychlou referenci** během obhajoby. Obsah slidu 6 (v 7slide struktuře) / slidu 9 (v 10slide stávajícím PPTX).

---

## ❓ Otázky vedoucího práce — Ing. Dalibor Slovák Ph.D., dipl. um.

### 1. Jak přesně funguje registrace a přihlášení uživatele včetně uložení hesla do databáze?

**Klíčová slova:** `bcrypt` + prepared statements + PHP session

> Heslo se hashuje přes `password_hash($pwd, PASSWORD_DEFAULT)` — bcrypt s automatickou solí. Do DB jde jen hash. Při loginu `password_verify()` v konstantním čase porovná. Po úspěchu `session_start()` + `$_SESSION['user_id']`.
>
> ⚠️ Přiznat: **nemám CSRF, regenerování session ID, validaci duplicit**.

---

### 2. Proč byl zvolen SQLite a jaké jsou výhody a limity této databáze pro webový portál s více uživateli?

**Klíčová slova:** embedded, zero-config, write-locking limit

> **Pro:** server-less, jeden soubor, PHP má vestavěnou podporu přes PDO. Pro maturitu ideální.
>
> **Limit:** zamyká celý soubor při zápisu → pro paralelní zápisy by bylo nutné MySQL. Žádný vzdálený přístup, slabší správa uživatelů.

---

### 3. Jaké bezpečnostní prvky bych do aplikace doplnil, aby byla vhodnější pro reálný provoz?

**Klíčová slova:** HTTPS, CSRF, rate limit, verifikace e-mailu, logout

> 1. **HTTPS** (Let's Encrypt) — aktuálně free euweb HTTPS nemá
> 2. **CSRF tokeny** ve všech POST formulářích
> 3. **`session_regenerate_id(true)`** po loginu (proti session fixation)
> 4. **Rate limiting** na login (proti brute-force)
> 5. **Verifikace e-mailu** při registraci
> 6. **HttpOnly + Secure + SameSite** flagy na session cookie
> 7. **Content Security Policy** hlavička (proti XSS)
> 8. **`logout.php`** se `session_destroy()`

---

## ❓ Otázky oponenta — Ing. Jakub Josef Forman

### 4. Jakou by mělo výhodu, pokud by byla použita jiná databáze?

**Klíčová slova:** MySQL pro konkurenci · **PostgreSQL + PostGIS pro mapu autosrazů**

> **MySQL/MariaDB:** plně konkurentní zápisy, vzdálený přístup, lepší správa uživatelů, replikace.
>
> **PostgreSQL:** navíc **PostGIS** pro geografická data → **mapa autosrazů** s indexovanými souřadnicemi. JSONB pro nestrukturovaná data.
>
> **NoSQL (Redis):** cache, session storage, rate limiting counters.

---

### 5. Proč nebyla použita žádná moderní knihovna/framework v projektu?

**Klíčová slova:** vědomá volba pro pochopení principů · Laravel pro produkci

> Vědomá volba ze tří důvodů:
>
> 1. **Porozumění principům** — Laravel abstrahuje routing, autentizaci, ORM. Bez něj jsem si je musel napsat sám, takže rozumím každému řádku.
> 2. **Velikost projektu** — pro 6 stránek je Laravel + Composer s tisíci závislostmi overkill.
> 3. **Snadné nasazení** — FTP upload PHP souborů + SQLite, žádné `composer install` ani migrace.
>
> ⚠️ Nikdy neříkat „Laravel neumím" — říct „pro tento rozsah by byl overkill". Pro produkci bych Laravel zvolil kvůli vyzrálé autentizaci, CSRF ochraně, validaci a ORM Eloquent.

---

## 📋 Rychlá tabulka — kterým slidem v prezentaci to pokrývám

| Otázka | Slide v prezentaci | Co tam říkám |
|--------|--------------------|--------------|
| 1 — hashování | **Slide 4** (Projektové řešení) | „Bezpečné heslování: `password_hash()` bcrypt + `password_verify()`" |
| 2 — SQLite | **Slide 4** (Projektové řešení) | „SQLite + PDO — embedded DB, jeden soubor; limit write-locking" |
| 3 — bezpečnost produkce | **Slide 4** (Limity) | „Pro produkci doplnit HTTPS, CSRF, regenerování session ID, logout" |
| 4 — jiná DB | **Slide 4** (Limity) | „PostgreSQL + PostGIS pro mapu autosrazů" |
| 5 — žádný framework | **Slide 4** (Zásady) | „Procedurální PHP bez frameworku — vědomá volba pro pochopení principů" |

> **Tip:** v Q&A se odkazuj na slide 4: „Jak jsem zmínil v prezentaci, hlavní důvod je X — a rád to rozvedu detailněji o Y a Z."

---

## ⚠️ Tři věci, které NESMÍŠ říct

1. ❌ „Frameworky neumím." → ✅ „Pro tento rozsah by Laravel byl overkill."
2. ❌ „To jsem nestihl." → ✅ „V produkci bych to doplnil — viz limity projektu."
3. ❌ „To je špatně v posudku." → ✅ „Souhlasím, mohlo to být lepší."

---

## ✅ Když komise opraví / nevím odpověď

- **Opraví:** „Děkuji za upřesnění." (krátce, **nehádat se**, pokračovat dál)
- **Nevím:** „V tomto jsem narazil na limit projektu — neimplementoval jsem to." NEBO „Tento konkrétní termín neznám, ale princip je…"
- **Překvapí mě otázka:** 2–3 sekundy ticha = OK. Pak: „Tak nad tím jsem nepřemýšlel během psaní, ale myslím, že…"

⚠️ NIKDY si nevymýšlet!
