# Stručný přehled k obhajobě maturitní práce

**Autor:** Stefano Battistuzzi · **Obor:** Informační technologie 18-20-M/01 · **Třída:** S4C
**Téma:** Webový portál CarzMeetz — platforma pro organizaci autosrazů
**Vedoucí:** Ing. Dalibor Slovák Ph.D., dipl. um. · **Oponent:** Ing. Jakub Josef Forman
**Živý web:** carzmeetz.euweb.cz

---

## Cíl práce

Vytvořit moderní webový portál pro komunitu automobilových nadšenců, který umožňuje sdílení informací o autosrazech, registraci uživatelů a správu uživatelského obsahu. Web má být responzivní a nasaditelný na běžný webhosting.

## Výsledný produkt

- **Funkční webový portál** CarzMeetz nasazený na hostingu (carzmeetz.euweb.cz)
- Vlastní implementace v PHP bez frameworku — kompletní kontrola nad architekturou
- Registrace a přihlášení uživatelů (`password_hash` / `password_verify`, prepared SQL dotazy)
- Galerie a stránky s informacemi o srazech
- Responzivní design (mobile-first)
- Databáze SQLite — bezserverové řešení vhodné pro malou komunitu

## Vlastní přínos

Projekt je psaný v čistém PHP bez použití moderního frameworku. To znamená, že **veškerá funkcionalita — routing, autentizace, práce s databází, šablonování — je implementována vlastním kódem**. Cílem bylo prokázat porozumění tomu, jak weby fungují „pod kapotou", a nezávislost na vysokoúrovňových abstrakcích. Pro produkci by bylo vhodné doplnit pokročilejší bezpečnostní vrstvy a zvážit přechod na Laravel/Symfony.

## Použité technologie

PHP · PDO · SQLite · HTML5 · CSS3 (mobile-first responzivní design) · JavaScript · vývojové prostředí PhpStorm · hosting endora/euweb.cz

## Hlavní reakce na posudky

| Připomínka | Reakce |
|------------|--------|
| **Chybí správa session, validace, odhlášení** | **PŘIJÍMÁM** — implementoval jsem základ (password_hash, prepared statements), ale chybí CSRF, regenerování session ID, validace duplicit. V produkční verzi bych doplnil. |
| **Dokumentace popisná, ne technická** | **PŘIJÍMÁM** — psal jsem ji spíš pro uživatele než pro vývojáře. Pro další verzi přidám sekci s architekturou a schématem DB. |
| **Pravopisné a stylistické chyby v textu** | **PŘIJÍMÁM** — text jsem před odevzdáním neměl řádně zkontrolován. |
| **Chybná čísla citací v bibliografii** | **PŘIJÍMÁM** — výsledek manuálního číslování zdrojů. Při příští práci bych použil reference manager (Zotero). |
| **Historie webu zabírá nepřiměřeně mnoho prostoru** | **PŘIJÍMÁM** — měl jsem víc prostoru věnovat backendu a SQLite. |
| **Chybí podrobnější analýza backendových technologií** | **PŘIJÍMÁM** — viditelná slabina práce; mohu o backendu mluvit nyní. |
| **Nepoužitý framework, doporučení moderní knihovny** | **VYSVĚTLUJI** — záměrná volba pro pochopení principů. Pro produkci bych zvolil Laravel. |
| **Struktura projektu / čistota kódu má rezervy** | **PŘIJÍMÁM/VYSVĚTLUJI** — psal jsem procedurálně, soubor po souboru. Frameworkové MVC rozdělení by projekt vylepšilo. |

## Možná rozšíření

- Migrace na **MySQL/PostgreSQL** pro konkurentní zápisy
- **Laravel** nebo **Symfony** pro lepší autentizaci, validaci, migrace DB
- **CSRF tokeny**, **rate limiting** na login, **verifikace e-mailu**
- **HTTPS** (Let's Encrypt) + Content Security Policy hlavička
- **PostgreSQL + PostGIS** pro geografická data (mapa autosrazů)
- **Cache vrstva** (Redis) pro session storage a rate limiting
- **GDPR opatření** — souhlas se zpracováním osobních údajů, mazání účtu

---

## Hodnocení posudků

| Posuzovatel | Body | Doporučení |
|-------------|------|------------|
| Vedoucí (Slovák) | **26 / 40** (65 %) | ✅ k obhajobě |
| Oponent (Forman) | **17 / 30** (57 %) | ✅ k obhajobě |
