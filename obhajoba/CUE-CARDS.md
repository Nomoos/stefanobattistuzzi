# Cue cards pro obhajobu — k tisku do ruky

**Pro Stefana — krátké taháky.** Vytisknout A4 oboustranně, mít v ruce při obhajobě.

---

## ÚVOD (30 sekund) — nauč se nazpaměť

> „Dobrý den, jmenuji se Stefano Battistuzzi a obhajuji maturitní práci „Webový portál CarzMeetz" — platformu pro organizaci autosrazů. Web je nasazený na carzmeetz.euweb.cz a je celý napsaný v PHP s databází SQLite, bez použití frameworku. Cílem bylo vytvořit funkční komunitní platformu a zároveň prokázat porozumění tomu, jak weby fungují bez vysokoúrovňových abstrakcí."

---

## 5 OTÁZEK Z POSUDKŮ — 1 věta klíčové sdělení

### V1: Jak funguje registrace a přihlášení?
> **Heslo se hashuje přes `password_hash()` bcryptem, do DB jde jen hash. Při loginu `password_verify()` porovná, pak `session_start()` + uložení user_id do session.**

⚠️ Nezapomenout: **NEMÁM CSRF, regenerování session ID ani validaci duplicit** — přiznat upřímně.

### V2: Proč SQLite?
> **Bez serveru, jeden soubor, žádná konfigurace. Pro maturitní projekt ideální. Limit: zamyká celý soubor při zápisu — pro velký provoz by bylo nutné MySQL/PostgreSQL.**

### V3: Bezpečnost pro reálný provoz?
> **HTTPS, CSRF tokeny, rate limiting na login, verifikace e-mailu, HttpOnly+Secure+SameSite cookies, CSP hlavička, zálohy, GDPR.**

### O1: Výhody jiné databáze?
> **MySQL = konkurentní zápisy + vzdálený přístup. PostgreSQL navíc JSONB a PostGIS — geodata se hodí pro mapu autosrazů.**

### O2: Proč žádný framework?
> **Záměrně — chtěl jsem rozumět principům „pod kapotou". Laravel pro malý projekt byl overkill. Pro produkci bych Laravel zvolil.**

⚠️ NEŘÍKAT „neumím Laravel" — říct „Laravel je nejpopulárnější PHP framework, znám princip, pro tento rozsah jsem ho nepotřeboval."

---

## SLABINY POSUDKŮ — KRÁTKÉ REAKCE

| Připomínka | Co říct |
|------------|---------|
| Chybí správa session/odhlášení/validace | „Máte pravdu, implementoval jsem jen základ. V produkci bych doplnil." |
| Dokumentace je uživatelská, ne technická | „Přijímám — psal jsem pro uživatele, ne pro vývojáře." |
| Pravopisné chyby | „Souhlasím, text jsem neměl řádně zkontrolován." (KRÁTCE!) |
| Špatná čísla citací | „Chyba manuálního číslování, použil bych Zotero." |
| Hodně historie webu | „Souhlasím, mělo to být kratší a víc backendu." |
| Chybí backendová analýza v teorii | „Souhlasím — mohu o backendu mluvit nyní, pokud chcete." |
| Struktura kódu má rezervy | „Procedurální styl — MVC by to systematizovalo." |

**KAŽDÝ POSUDEK MÁ ALESPOŇ JEDEN PŘIJATELNÝ DŮVOD KRITIKY. NEHÁDAT SE.**

---

## KLÍČOVÉ POJMY — když zapomenu

- **bcrypt** — pomalý hashovací algoritmus s vestavěnou solí
- **sůl / salt** — náhodný řetězec, aby dvě stejná hesla měla různé hashe
- **prepared statement** — SQL šablona s placeholdery, chrání před SQL injection
- **session** — server si pamatuje uživatele přes ID v cookie
- **CSRF** — útok cizí stránkou, obrana = token ve formuláři
- **XSS** — útočník vloží JS do obsahu, obrana = `htmlspecialchars()`
- **SQL injection** — útok přes input, obrana = prepared statements (mám!)
- **PDO** — PHP knihovna pro práci s DB, abstrakce nad MySQL/SQLite
- **MVC** — Model/View/Controller architektura
- **ORM** — Object-Relational Mapping (Eloquent v Laravel)
- **Composer** — package manager pro PHP
- **ACID** — Atomicity/Consistency/Isolation/Durability
- **HTTPS = HTTP + TLS** — šifrovaná komunikace + certifikát
- **GET vs POST** — GET je v URL (cachable, idempotentní), POST v body (změny stavu)
- **status kódy:** 200 OK, 301 Moved Permanently, 404 Not Found, 500 Internal Server Error

---

## CO DĚLAT, KDYŽ…

### Komise mě opraví
> „Děkuji za upřesnění." (krátce, **nehádat se**, pokračovat dál)

### Nevím odpověď
> „V tomto jsem narazil na limit projektu — neimplementoval jsem to." NEBO „Tento konkrétní termín neznám, ale princip je…"

⚠️ NIKDY si nevymýšlet!

### Otázka mě překvapí
> 2–3 sekundy ticha = OK. Pak: „Tak nad tím jsem nepřemýšlel během psaní, ale myslím, že…"

### Komise se mě zeptá na něco mimo můj projekt
> Klidně odpovědět zájmem: „Mimo můj projekt jsem to neřešil, ale znám princip — …"

---

## PŘED OBHAJOBOU — checklist

- [ ] **Otevři carzmeetz.euweb.cz** v prohlížeči (cache warm-up)
- [ ] Záložní PDF prezentace na flashce / mobilu
- [ ] Cue cards (tento dokument) vytisknuté
- [ ] Voda u sebe
- [ ] Mobil v tichém režimu, mimo dosah
- [ ] **Demo:** vědět kde najít přihlášení / registraci na webu (kdyby chtěli ukázat)
- [ ] Notebook nabitý / nabíječka u sebe
- [ ] Hotspot zapnutý jako záloha

---

## DURING — během prezentace

- **Mluvit z hlavy**, slide je jen opora — komise nemá rád čtení.
- **Oční kontakt s komisí** (nezírat do slidu)
- **Tempo 30–60 s na slide** — 10 slidů = 5–10 min celkem
- **Před každým slidem 1 dech** — nehoň se
- **Když se zaseknu**: „… moment, formuluji to lépe…" — chvíle ticha je OK

---

## TOP 3 VĚCI, KTERÉ MUSÍŠ ŘÍCT BĚHEM PREZENTACE

1. **Co projekt dělá** (organizace autosrazů, registrace, galerie)
2. **Technologie** (PHP + SQLite, bez frameworku — vědomá volba)
3. **Co jsem se naučil** (registrace, hashe hesel, PDO, responzivita, hosting)

---

## TOP 3 VĚCI, KTERÉ NESMÍŠ ŘÍCT

1. ❌ „Frameworky neumím."  → ✅ „Pro tento rozsah by Laravel byl overkill."
2. ❌ „To jsem nestihl."  → ✅ „V produkci bych to doplnil — viz limity projektu."
3. ❌ „To je špatně v posudku."  → ✅ „Souhlasím, mohlo to být lepší."

---

## ZAKONČENÍ

> „Děkuji za pozornost a jsem připraven na vaše otázky."

**Pauza. Úsměv. Komise si rozmyslí, kdo se zeptá první.**
