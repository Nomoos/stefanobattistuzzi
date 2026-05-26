# Copy-paste sheet pro PowerPoint / Google Slides

> **Pro koho:** Stefano, při manuální tvorbě/opravě slidů ve stávajícím PPTX nebo nové prezentaci.
> **Závazná struktura:** podle školního vzoru `Orbis prezentace - final_vzor.pptx` — **7 slidů**.
> **Jak používat:** Otevři PowerPoint → Stefanův stávající PPTX nebo nový z vzoru → pro každý slide níže buď přepiš obsah existujícího slidu, nebo vytvoř nový. Paste TITULEK + OBSAH + (volitelně) SPEAKER NOTES.
> **Speaker notes:** v PowerPointu klikni dolů na panel „Click to add notes". V Google Slides View → Show speaker notes.

---

## ⚠️ Důležité: zachování školní šablony

Vzor školy má 7 slidů. Stefanův stávající PPTX má 10 slidů (rozšíření). Doporučení: **přepsat na 7 slidů podle vzoru** — komise to ocení. Alternativně zachovat 10 slidů a opravit šablonové texty na slidech 6, 7, 8.

---

## SLIDE 1 — Titulní (0:30)

### TITULEK
Webový portál
CarzMeetz — platforma pro organizaci autosrazů

### OBSAH
Autor: Stefano Battistuzzi
Třída: S4C · Obor: Informační technologie 18-20-M/01
Rok: 2025/2026

Vedoucí práce: Ing. Dalibor Slovák Ph.D., dipl. um.
Škola: ORBIS, MŠ/ZŠ/SŠ s.r.o., Zlín

Web: carzmeetz.euweb.cz

### SPEAKER NOTES
Dobrý den, jmenuji se Stefano Battistuzzi a obhajuji maturitní práci na téma Webový portál. V praktické části jsem realizoval konkrétní portál pro organizaci autosrazů s názvem CarzMeetz, který je nasazený na adrese carzmeetz.euweb.cz. Vedoucím práce byl pan Slovák. Pokud bude komise chtít, otevřu web v rámci dotazů živě v prohlížeči.

---

## SLIDE 2 — Úvod (1:30)

### TITULEK
Úvod

### OBSAH
🎯 Téma
Webový portál CarzMeetz pro komunitu automobilových nadšenců — osobní zájem o auta + reálná potřeba v komunitě.

📌 Cíl práce
„Ukázat problematiku tvorby webových stránek a portálů a demonstrovat jejich funkčnost na praktickém příkladu." — citace z úvodu MP
Konkrétně: funkční web s databází pro zobrazování informací o srazech a registraci uživatelů.

⚙️ Postup zpracování
1. Teoretická část — HTML, CSS, JavaScript, SQLite, historie webu
2. Praktická část — návrh, implementace, nasazení webu CarzMeetz
3. Iterativně: HTML → CSS → JavaScript → PHP → SQLite → hosting

### SPEAKER NOTES
Téma webového portálu jsem si zvolil ze dvou důvodů. Subjektivně — jsem osobně součástí komunity automobilových nadšenců a chtěl jsem pro tuto komunitu vytvořit konkrétní nástroj. Objektivně — webová prezentace přesahuje jen psaní HTML, zahrnuje práci s databází, bezpečnost, responzivní design a nasazení na hosting. To znamenalo, že jsem se musel naučit více oblastí najednou.

Cílem práce bylo ukázat problematiku tvorby webových stránek a portálů a demonstrovat jejich funkčnost na praktickém příkladu — což cituji ze své práce. Konkrétně jsem si dal za úkol vytvořit funkční web s databází, který bude umožňovat zobrazování informací o autosrazech a registraci uživatelů.

Při zpracování jsem postupoval po fázích. V teoretické části jsem popsal historii webu, jednotlivé technologie HTML, CSS, JavaScript a databázový systém SQLite. V praktické části jsem nejprve navrhl strukturu webu, poté implementoval HTML kostru, doplnil CSS pro design, přidal JavaScript pro mobilní menu, PHP pro registraci a galerii, a nakonec vše propojil s SQLite databází. Web jsem nasadil na hosting webzdarma.cz pod doménou carzmeetz.euweb.cz.

---

## SLIDE 3 — Praktická část (2:30)

### TITULEK
Praktická část

### OBSAH
📋 Charakteristika tématu
Webový portál CarzMeetz pro komunitu nadšenců v ČR. 6 hlavních stránek — Domů, Srazy, Galerie, O nás, Kontakt, Účet. 2 SQLite databáze — uživatelé + galerie. Responzivní design s mobilním hamburger menu.

🔍 Použité analytické metody
| Metoda | Popis |
|--------|-------|
| Srovnávací analýza | Konkurence: Srazy.info, FB skupiny |
| Rešerše požadavků | Neformální dotazování v komunitě |
| Návrh struktury | Definice MVP: registrace, galerie, info |
| Iterativní vývoj | Postupně od statického HTML k PHP + DB |
| Manuální testování | DevTools, W3C validátor, scénáře |

❓ Proč tyto metody
Vhodné pro komunitní projekt menšího rozsahu — kvalitativní přístup je dostatečný, akademický výzkum by byl overkill.

### SPEAKER NOTES
Charakteristika tématu. Webový portál CarzMeetz je platforma pro komunitu automobilových nadšenců v České republice. Slouží ke sdílení informací o autosrazech, registraci uživatelů a archivaci fotek z proběhlých akcí. Portál obsahuje šest hlavních stránek, dvě SQLite databáze a responzivní design pro mobilní zařízení.

Použité analytické metody. První metoda byla srovnávací analýza konkurenčních platforem. Studoval jsem zejména server Srazy.info a několik komunitních skupin na Facebooku — chtěl jsem ověřit, které funkce už existují a které uživatelům chybí. Druhá metoda byla rešerše komunitních požadavků — neformální dotazování v komunitě, ve které sám fungujem. Z toho vzešel seznam MVP funkcí: registrace, galerie, informace o srazech. Třetí metoda byla iterativní implementace — postupně jsem stavěl od statického HTML přes CSS až po dynamický PHP s databází. Čtvrtá metoda bylo manuální testování — procházel jsem všechny stránky, zkoušel registraci s různými hesly, ověřoval validitu HTML v W3C validátoru a responzivitu v Chrome DevTools v módech mobile, tablet i desktop.

Proč jsem zvolil tyto metody. Pro projekt menšího rozsahu jsou tyto kvalitativní metody dostatečné. Automatizované testy by byly overkill, marketingový výzkum konkurence by byl příliš formální. Cílem nebylo udělat akademickou studii, ale dodat fungující produkt pro reálnou komunitu.

---

## SLIDE 4 — Projektové řešení (2:30)

### TITULEK
Projektové řešení

### OBSAH
🏗️ Hlavní zásady řešení
| Zásada | Detail |
|--------|--------|
| Procedurální PHP, bez frameworku | Vlastní implementace — pochopení principů |
| SQLite + PDO | Embedded DB, jeden soubor, žádný server |
| Bezpečné heslování | password_hash() bcrypt + password_verify() |
| Prepared statements | bindValue() proti SQL injection |
| Responzivní design | Mobile-first, hamburger pod 768 px |

💡 Co řešení přináší praxi
- Funkční MVP komunitního portálu nasazený na hostingu
- 6 testovacích uživatelů + 6 fotek v galerii (živě ověřeno)
- Vlastní programátorský základ k pochopení jak weby fungují

📌 Limity a budoucí kroky
| Mezera | Plán pro produkční verzi |
|--------|--------------------------|
| Bez frameworku | Laravel (CSRF, auth, ORM) |
| SQLite write-locking | PostgreSQL + PostGIS pro mapu autosrazů |
| Free euweb bez HTTPS | placený hosting + Let's Encrypt |
| Chybí CSRF, logout | doplnit pro reálný provoz |

### SPEAKER NOTES
Hlavní zásady navrhovaného řešení vycházejí ze tří klíčových rozhodnutí.

První rozhodnutí — procedurální PHP, bez frameworku. Cíleně jsem se rozhodl nepoužít Laravel ani Symfony. Důvod je pedagogický — pro maturitní projekt jsem chtěl rozumět tomu, jak weby fungují „pod kapotou". Frameworky abstrahují routing, autentizaci, ORM. Bez nich jsem si tyto věci musel napsat sám, takže přesně vím, co se kde děje. Pro produkční verzi pro tisíce uživatelů bych Laravel zvolil — kvůli vyzrálé autentizaci a CSRF ochraně.

Druhé rozhodnutí — SQLite jako databáze. SQLite jsem zvolil proto, že nepotřebuje samostatný server, je to jeden soubor a PHP má vestavěnou podporu přes PDO. Pro komunitu desítek uživatelů je výkon dostatečný. Hlavní limit SQLite je, že zamyká celý soubor při zápisu, takže pro vysoký objem souběžných zápisů by bylo nutné přejít na MySQL. Pro produkční verzi s mapou autosrazů by se hodil zejména PostgreSQL s rozšířením PostGIS pro geografická data.

Třetí rozhodnutí — bezpečné heslování od začátku. Hesla se v databázi nikdy neukládají v plaintextu. Při registraci je hashuji funkcí password_hash() s algoritmem bcrypt, který automaticky generuje náhodnou sůl. Při loginu pak password_verify() v konstantním čase porovná zadané heslo s uloženým hashem. Všechny SQL dotazy používají prepared statements proti SQL injection. Při výpisu uživatelských dat používám htmlspecialchars() proti XSS.

Co řešení přináší. Funkční MVP komunitního portálu nasazený na hostingu, šest registrovaných testovacích uživatelů a šest fotek v galerii — to znamená, že každá implementovaná funkce je živě ověřená.

Limity a budoucí kroky. Uznávám, že pro reálný provoz by web potřeboval HTTPS, CSRF tokeny, regenerování session ID po loginu a logout — tyto mezery v posudku vedoucího uznávám a v produkční verzi bych je doplnil. Free euweb HTTPS aktuálně neumožňuje, ale na placeném hostingu by se přidalo přes Let's Encrypt zdarma.

---

## SLIDE 5 — Závěr (1:30)

### TITULEK
Závěr

### OBSAH
✅ Dosažení cílů
„Cíl se podařilo splnit — vytvořil jsem funkční web s databází, který umožňuje zobrazování informací o srazech a práci s nimi." — citace ze závěru MP

🎓 Jak mě práce obohatila
- Rozšíření znalostí HTML, CSS, JavaScriptu a PHP
- První zkušenost s databází SQLite + propojení s webem
- Reálný projekt nasazený na hostingu

🔮 Pokračování práce
Vytvoření webu v podobném stylu a další rozvoj — kalendář srazů, mapa, profily uživatelů, UX testování.

🎯 Osobní přínos
Vědomá volba vlastní implementace bez frameworku → hluboké porozumění tomu, jak weby fungují. Tuto znalost využiji v dalším studiu i praxi.

### SPEAKER NOTES
Dosáhl jsem cílů, které jsem si stanovil? Ano. Cílem bylo vytvořit webovou aplikaci zaměřenou na autosrazy CarzMeetz a tento cíl se mi podařilo splnit — povedlo se mi vytvořit funkční web s databází, který umožňuje zobrazování informací o srazech a práci s nimi.

Jak mě práce obohatila. Během tvorby jsem si rozšířil znalosti v oblasti webových technologií, především HTML, CSS, JavaScriptu a PHP. Vyzkoušel jsem si práci s databází SQLite a její propojení s webovým portálem, což pro mě byla zcela nová zkušenost. Zároveň jsem si vyzkoušel nasazení vlastní aplikace na hosting, což je krok, který v běžné výuce často chybí.

Jak pokračovat. Do budoucna bych chtěl vytvořit web v podobném stylu a dále jej rozvíjet — přidat dynamickou správu srazů s kalendářem, mapu autosrazů s geografickými souřadnicemi, profily uživatelů a komentáře k fotkám. Z bezpečnostního pohledu by bylo nutné doplnit HTTPS, CSRF tokeny a verifikaci e-mailu.

Můj osobní přínos. Vědomá volba implementovat celý web vlastním kódem bez frameworku mi umožnila pochopit, jak weby fungují od HTML šablony až po databázi. Tuto zkušenost — že rozumím každému řádku kódu ve svém projektu — mohu využít v dalším studiu i v praxi. To je největší přínos, který mi maturitní práce dala.

---

## SLIDE 6 — Otázky komise (1:00)

### TITULEK
Otázky komise

### OBSAH
❓ Otázky vedoucího práce (Ing. Slovák)
1. Jak funguje registrace a hashování hesla?
   → bcrypt, prepared statements, PHP session (viz slide 4)
2. Proč SQLite a jeho limity?
   → embedded, zero-config, write-locking limit (viz slide 4)
3. Bezpečnostní prvky pro reálný provoz?
   → HTTPS, CSRF, rate limit, verifikace e-mailu, logout

❓ Otázky oponenta (Ing. Forman)
4. Výhody jiné databáze?
   → MySQL pro konkurenci, PostgreSQL + PostGIS pro mapu autosrazů
5. Proč žádný framework?
   → vědomá volba pro pochopení principů, Laravel pro produkci (viz slide 4)

Klíčová slova k odpovědím — všechny otázky pokrývá slide 4 (Projektové řešení).

### SPEAKER NOTES
Tímto má prezentace končí. Komise nyní dostane prostor pro vyjádření vedoucího práce a oponenta. Na tomto snímku mám připravený přehled pěti otázek, které mi byly položeny v posudcích, společně s klíčovými body, na které ve své odpovědi navážu. Na všechny tyto otázky jsem v prezentaci alespoň zčásti odpověděl — především v rámci slidu 4 o projektovém řešení. V Q&A rád jakoukoli odpověď rozvedu detailněji.

(Tento mluvený text je krátký záměrně — komise teď přijme slovo. Klíčová slova na slidu fungují jako vizuální opora pro Q&A, ne pro mluvený monolog.)

---

## SLIDE 7 — Děkuji za pozornost (0:30)

### TITULEK
Děkuji za pozornost

### OBSAH
🌐 carzmeetz.euweb.cz

Web mám otevřený v prohlížeči pro případné dotazy.

Stefano Battistuzzi · S4C · 2025/2026

### SPEAKER NOTES
Děkuji za pozornost a za příležitost představit svou maturitní práci. Web mám otevřený v prohlížeči, takže pokud bude komise chtít cokoliv vidět živě, mohu se kdykoli přepnout. Jsem připraven na otázky.

---

## DOPLNĚNÍ OBRÁZKŮ

Slidy 1, 3, 5 mohou mít obrázky:

| Slide | Doporučený obrázek |
|-------|---------------------|
| 1 | Logo CarzMeetz (z untitled/images/carzmeetz_logo1.png v ZIPu) vpravo dole |
| 3 | Screenshoty 4 hlavních stránek webu — homepage, srazy, galerie, mobil |
| 4 | Diagram architektury projektu (frontend → PHP → SQLite) NEBO ER diagram tabulek users + gallery |
| 5 | (volitelně) Screenshot závěru práce — odkud cituji |

Zdroje pro screenshoty:
- Web: otevři carzmeetz.euweb.cz → příslušnou stránku → Print Screen (Win+Shift+S)
- Mobilní pohled: Chrome DevTools → F12 → Toggle device toolbar (Ctrl+Shift+M)
- Logo: z untitled/images/carzmeetz_logo1.png v rozbaleném ZIPu battistuzzi_prace.zip

---

## DESIGN SETTINGS pro PowerPoint / Google Slides

- **Téma:** Simple Light nebo Basic (bílé pozadí — DOPORUČENO pro kmenovou třídu kvůli kontrastu)
  - Stávající Stefanův PPTX má tmavé pozadí — pro denní světlo v třídě horší. Zvážit změnu.
- **Fonty:**
  - Title — **Orbitron** (sportovní/auto vibe — stejný font jako web CarzMeetz) nebo Roboto, 36–42 pt
  - Body — Inter / Roboto / Open Sans, 22–26 pt
- **Barvy** (CarzMeetz styl):
  - Pozadí: bílá (#FFFFFF) nebo světle šedá (#F5F5F5)
  - Text: tmavě šedá (#1A1A1A)
  - Akcent (nadpisy, proužky): **CarzMeetz červená** (#B30000)
  - Sekundární akcent: tmavě šedá (#333333)
- **Tabulky:** hlavička červená (akcent), řádky střídavě jemně podbarvené
- **Page numbers:** zapnout

---

## TIP: Generování přes Marp (rychlejší než ruční tvorba)

Pokud Stefano má Node.js / npm:

```bash
# Instalace Marp CLI (jednou)
npm install -g @marp-team/marp-cli

# Export do PPTX (ze složky obhajoba/)
marp prezentace.md --pptx --output prezentace-vygenerovana.pptx

# Nebo náhled v HTML
marp prezentace.md --html --output prezentace-vygenerovana.html
```

Pak nahraj `prezentace-vygenerovana.pptx` do PowerPointu / Google Slides. **Marp vygeneruje formát, který je už hotový** — stačí doplnit screenshoty.

Alternativa bez instalace: nahrát `prezentace.md` do online Marp editoru: **https://web.marp.app**
