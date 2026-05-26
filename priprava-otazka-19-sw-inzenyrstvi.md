# Otázka 19 — Softwarové inženýrství

Softwarové inženýrství je systematický, disciplinovaný a měřitelný přístup k vývoji, provozu a údržbě software. Tento okruh pokrývá životní cyklus vývoje SW (SDLC), tradiční i agilní metodiky, testování, nástroje pro správu úkolů a chyb (issue tracking) a kritéria kvality software.

---

## 1. Životní cyklus software (SDLC)

### Definice

**SDLC (Software Development Life Cycle)** je strukturovaný proces, podle kterého se software plánuje, navrhuje, vyvíjí, testuje, nasazuje a udržuje. Zahrnuje všechny aktivity od prvního nápadu/zadání až po vyřazení softwaru z provozu.

### Fáze SDLC

SDLC se obvykle dělí do šesti hlavních fází. Konkrétní model určuje, jak se tyto fáze řadí (lineárně, iterativně, paralelně…), ale obsah fází bývá podobný.

#### 1. Analýza (Analysis / Requirements)
- Zjištění a sepsání požadavků od zákazníka/zadavatele.
- Výsledkem je dokument **specifikace požadavků** (SRS — Software Requirements Specification).
- Rozlišují se **funkcionální požadavky** (co systém musí dělat — např. „uživatel se přihlásí emailem a heslem") a **nefunkcionální požadavky** (jak to musí dělat — výkon, bezpečnost, dostupnost).
- Techniky: rozhovory, dotazníky, workshopy, analýza konkurence, use case diagramy, user stories.

#### 2. Návrh / Design
- Architektura systému (vrstvy, komponenty, databáze, API).
- UML diagramy (třídní, sekvenční, případy užití).
- Wireframy a mockupy UI/UX.
- Návrh datového modelu (ER diagram, databázové schéma).
- Rozhodnutí o technologickém stacku (jazyk, framework, DB, hosting).

#### 3. Implementace (Implementation / Coding)
- Samotné psaní zdrojového kódu programátory.
- Verzování kódu (Git, GitHub/GitLab).
- Dodržování coding standards a code review.
- Postupné commitování a integrace dílčích částí.

#### 4. Testování (Testing)
- Ověření, že software funguje podle požadavků a neobsahuje chyby.
- Různé úrovně: unit, integration, system, acceptance (více v sekci 3).
- Zaznamenávání bugů do issue trackeru a jejich oprava.

#### 5. Nasazení (Deployment / Release)
- Instalace softwaru u zákazníka nebo na produkční server.
- Migrace dat, nastavení prostředí (env. variables, DB connection).
- Školení uživatelů, dokumentace.
- Postupný rollout (canary release, blue/green deployment).

#### 6. Údržba (Maintenance)
- Opravy chyb hlášených uživateli (corrective maintenance).
- Přizpůsobení změnám prostředí — nová verze OS, DB (adaptive).
- Vylepšení a nové funkce (perfective).
- Prevence budoucích problémů — refaktoring, upgrade knihoven (preventive).
- Statistika: údržba tvoří **60–80 % celkových nákladů na software** během jeho životnosti.

### Tradiční modely SDLC

#### Vodopádový model (Waterfall)
- **Princip:** Lineární, sekvenční postup. Každá fáze musí být dokončena dříve, než začne další. Návrat zpět je obtížný a drahý.
- **Pořadí:** Analýza → Návrh → Implementace → Testování → Nasazení → Údržba.
- **Kdy se hodí:** projekty s jasně daným, neměnným zadáním (státní zakázky, embedded systémy, kritická infrastruktura, kde se vyžaduje certifikace).
- **Výhody:** přehlednost, dokumentace, dobré pro velké formální projekty, snadné plánování a rozpočet.
- **Nevýhody:** nedokáže reagovat na změny požadavků, zákazník vidí výsledek až na konci, vysoké riziko, pokud se chyba odhalí pozdě.

#### V-model (Validation & Verification Model)
- **Princip:** Rozšíření vodopádu — pro každou vývojovou fázi existuje odpovídající testovací fáze. Model má tvar písmene V: vlevo dolů jdou vývojové fáze, vpravo nahoru korespondující testy.
- **Páry:**
  - Požadavky ↔ Acceptance testy (UAT)
  - Systémový návrh ↔ System testy
  - Architektonický návrh ↔ Integration testy
  - Detailní návrh ↔ Unit testy
- **Kdy se hodí:** projekty s vysokými nároky na spolehlivost — medicína, automotive, letectví.
- **Výhody:** důraz na testování od začátku, jasná struktura.
- **Nevýhody:** stejně rigidní jako vodopád, drahý při změnách.

#### Iterativní model
- **Princip:** Software se vyvíjí v opakujících se cyklech (iteracích). Každá iterace projde mini-SDLC (analýza, design, implementace, testování) a postupně zpřesňuje produkt.
- **Kdy se hodí:** projekty, kde se požadavky upřesňují v průběhu.
- **Výhody:** rychlejší zpětná vazba, postupné zlepšování, nižší riziko.
- **Nevýhody:** vyžaduje zkušený tým, hůře se plánuje termín a rozpočet.

#### Inkrementální model
- **Princip:** Produkt se buduje po částech (inkrementech). Každý inkrement přidá novou funkcionalitu. Liší se od iterativního tím, že iterativní zpřesňuje stejnou věc, kdežto inkrementální skládá produkt z bloků.
- **Příklad:** v1.0 obsahuje přihlašování, v1.1 přidá správu uživatelů, v1.2 přidá fakturaci.
- **Výhody:** zákazník dostane dříve funkční verzi, dílčí dodávky.
- **Nevýhody:** vyžaduje promyšlenou architekturu od začátku.

#### Spirálový model (Boehm, 1986)
- **Princip:** Kombinuje iterativní vývoj s důrazem na **analýzu rizik**. Každá „smyčka" spirály má čtyři kvadranty:
  1. Stanovení cílů a omezení
  2. Analýza rizik a prototypování
  3. Vývoj a testování
  4. Plánování další iterace
- **Kdy se hodí:** velké, rizikové projekty (vesmírný program, vojenské systémy).
- **Výhody:** explicitní řízení rizik.
- **Nevýhody:** složitý, drahý, vyžaduje zkušené risk managery.

### Srovnávací tabulka modelů

| Aspekt | Vodopád | V-model | Iterativní / Inkrementální | Agile / Scrum | Spirálový |
|---|---|---|---|---|---|
| Změna požadavků | Velmi obtížná | Velmi obtížná | Možná mezi iteracemi | Vítaná kdykoliv | Možná v každé smyčce |
| Doba dodání 1. verze | Až na konci | Až na konci | Po několika iteracích | Po každém sprintu | Po každé smyčce |
| Dokumentace | Velmi rozsáhlá | Velmi rozsáhlá | Střední | Minimální (jen nutná) | Rozsáhlá |
| Řízení rizik | Slabé | Slabé | Střední | Implicitní (krátké cykly) | Explicitní (hlavní princip) |
| Zapojení zákazníka | Na začátku a konci | Na začátku a konci | V iteračních milnících | Průběžné (Sprint Review) | V každé smyčce |
| Vhodné pro | Stabilní zadání | Kritické systémy | Středně velké projekty | Měnící se požadavky, web/mobile | Velké rizikové projekty |

### Časté otázky komisaře

**Q: Jaký je rozdíl mezi vodopádem a agilem?**
A: Vodopád je lineární a sekvenční — všechny požadavky jsou zafixovány na začátku a postupně se procházejí fáze. Agile je iterativní, požadavky se upřesňují průběžně a software se dodává po malých kouscích (sprintech), což umožňuje rychle reagovat na změny.

**Q: Vyjmenuj fáze SDLC.**
A: Analýza požadavků → Návrh → Implementace → Testování → Nasazení → Údržba.

**Q: Co jsou nefunkcionální požadavky?**
A: Požadavky, které popisují, **jak** systém má fungovat — rychlost, bezpečnost, dostupnost, použitelnost, kompatibilita. Funkční říká „co", nefunkční říká „jak dobře".

**Q: Kdy by ses rozhodl použít vodopád místo agilu?**
A: Když mám pevně dané zadání, které se nezmění (např. státní zakázka s certifikací, embedded SW v medicíně), a potřebuji silnou dokumentaci a plánovatelnost.

**Q: Co je spirálový model a kdo ho navrhl?**
A: Spirálový model navrhl Barry Boehm v roce 1986. Kombinuje iterativní vývoj s explicitní analýzou rizik — každá smyčka spirály obsahuje čtyři kvadranty: cíle, analýza rizik, vývoj+testování, plánování další iterace.

---

## 2. Agilní metodiky vývoje software

### Definice

**Agile** je rodina iterativních metodik vývoje software, která klade důraz na pružnost, krátké vývojové cykly, časté dodávky funkčního produktu a úzkou spolupráci se zákazníkem.

### Proč Agile vznikl

Tradiční vodopádový model selhával u moderních softwarových projektů, kde se požadavky často mění, technologie se rychle vyvíjí a zákazník nedokáže na začátku přesně popsat, co chce. V roce **2001** se v Snowbirdu (Utah, USA) sešlo 17 zkušených vývojářů (Kent Beck, Martin Fowler, Ken Schwaber, Jeff Sutherland, Ron Jeffries, …) a sepsali **Agile Manifesto**.

### Agile Manifesto — 4 hodnoty

> „Objevujeme lepší způsoby vývoje softwaru tím, že jej tvoříme a pomáháme s ním druhým. Při této práci jsme dospěli k těmto hodnotám:"

1. **Jednotlivci a interakce** před procesy a nástroji
2. **Fungující software** před vyčerpávající dokumentací
3. **Spolupráce se zákazníkem** před vyjednáváním o smlouvě
4. **Reagování na změny** před dodržováním plánu

Hodnoty napravo jsou cenné, ale hodnoty nalevo cení autoři výše.

### 12 principů Agile Manifesta (zkráceně)

1. Nejvyšší prioritou je spokojenost zákazníka skrze brzké a průběžné dodávky.
2. Vítejte změny požadavků i pozdě ve vývoji.
3. Dodávejte fungující software často (týdny, ne měsíce).
4. Byznys a vývojáři musí spolupracovat denně.
5. Stavějte projekty kolem motivovaných jednotlivců, dejte jim podporu a důvěru.
6. Nejlepší způsob komunikace je tváří v tvář.
7. Fungující software je hlavní mírou pokroku.
8. Udržitelné tempo — sponzoři, vývojáři a uživatelé by měli být schopni držet tempo donekonečna.
9. Trvalá pozornost k technické dokonalosti a dobrému návrhu.
10. Jednoduchost — umění maximalizovat množství neudělané práce.
11. Nejlepší architektury vznikají v sebeřízených týmech.
12. Tým pravidelně reflektuje, jak být efektivnější, a přizpůsobuje se.

### Scrum

**Scrum** je nejrozšířenější agilní framework. Definuje role, artefakty a události. Sprinty trvají typicky **1–4 týdny** (nejčastěji 2).

#### Role

| Role | Odpovědnost |
|---|---|
| **Product Owner (PO)** | Reprezentuje zákazníka. Spravuje a prioritizuje Product Backlog. Rozhoduje, co se bude dělat. |
| **Scrum Master (SM)** | Servant leader. Pomáhá týmu dodržovat Scrum, odstraňuje překážky (impediments). NENÍ projektový manažer. |
| **Development Team** | Sebeřízený, multidisciplinární tým (typicky 3–9 lidí). Odpovídá za to, JAK se Product Backlog realizuje. |

#### Artefakty

| Artefakt | Popis |
|---|---|
| **Product Backlog** | Seřazený seznam všeho, co by mohlo být v produktu. Vlastní ho Product Owner. |
| **Sprint Backlog** | Položky z Product Backlogu vybrané pro aktuální sprint + plán, jak je tým splní. |
| **Increment** | Dokončený, použitelný a potenciálně dodatelný kus produktu na konci sprintu. |
| **Definition of Done (DoD)** | Sdílené kritérium, kdy je položka považována za hotovou (kód napsán, testy zelené, code review, dokumentace…). |

#### Události (Ceremonies)

| Událost | Doba | Účel |
|---|---|---|
| **Sprint** | 1–4 týdny | Časový box, ve kterém vznikne hotový Increment. |
| **Sprint Planning** | max. 8 h pro měsíční sprint | Tým rozhodne, co a jak udělá ve sprintu. |
| **Daily Scrum (standup)** | 15 minut, denně | Tým synchronizuje práci: co jsem udělal včera / co dnes / na čem mě blokuje. |
| **Sprint Review** | max. 4 h | Tým prezentuje Increment stakeholderům, sbírá zpětnou vazbu. |
| **Sprint Retrospective** | max. 3 h | Tým reflektuje proces: co fungovalo, co ne, co změníme. |
| **Backlog Refinement** | průběžně | PO + tým upřesňují a odhadují položky v backlogu. |

#### User Story formát

```
Jako [role uživatele] chci [funkci],
abych mohl [přínos / důvod].
```

Příklad: „Jako fanoušek TJ Slavoj Mýto chci vidět nejbližší zápas na úvodní stránce, abych nemusel hledat v kalendáři."

User stories mívají odhad v **story points** (často Fibonacci: 1, 2, 3, 5, 8, 13).

### Kanban

**Kanban** (japonsky „signální karta") je metodika pocházející z Toyota Production System (60. léta). Pro software ji popularizoval David J. Anderson.

#### Klíčové principy

1. **Vizualizace práce** — Kanban board se sloupci (To Do → In Progress → Review → Done).
2. **Limit Work In Progress (WIP)** — pevný strop na počet úkolů v každém sloupci. Zamezuje multitaskingu.
3. **Řízení toku** — měření průměrného času, jak dlouho úkol prochází systémem (lead time, cycle time).
4. **Explicitní pravidla** — co znamená „hotovo" v každém sloupci.
5. **Kontinuální zlepšování** — Kaizen.

#### Příklad Kanban boardu

```
| BACKLOG | TO DO (3) | IN PROGRESS (2) | REVIEW (2) | DONE      |
|---------|-----------|-----------------|------------|-----------|
| #45     | #38       | #36             | #35        | #34       |
| #44     | #37       | #33             |            | #32       |
| #43     |           |                 |            | #31       |
```

Čísla v závorkách jsou WIP limity.

#### Rozdíl Scrum vs Kanban

| | Scrum | Kanban |
|---|---|---|
| **Časový box** | Sprinty (1–4 týdny) | Žádný — kontinuální flow |
| **Role** | PO, SM, Dev Team | Žádné předepsané role |
| **Plánování** | Sprint Planning | Just-in-time, podle WIP |
| **Změny** | Až po sprintu | Kdykoliv |
| **Klíčová metrika** | Velocity (story points/sprint) | Lead time, cycle time |
| **Vhodné pro** | Produktový vývoj s rytmem | Support, údržba, DevOps, kontinuální dodávky |

### XP — Extreme Programming

Vytvořil **Kent Beck** (1999). Klade extrémní důraz na inženýrské praktiky:

- **Pair programming** — dva vývojáři u jednoho počítače (driver + navigator). Vyšší kvalita kódu, sdílení znalostí.
- **Test-Driven Development (TDD)** — nejdřív test, pak kód.
- **Continuous Integration** — časté integrace do hlavní větve.
- **Refactoring** — průběžné zlepšování struktury kódu beze změny chování.
- **Simple Design** — nejjednodušší řešení, které funguje (YAGNI = You Aren't Gonna Need It).
- **Collective Code Ownership** — kdokoliv může upravit kterýkoli kód.
- **Small Releases** — časté drobné releasy.
- **40-hour week** — udržitelné tempo, žádné přesčasy.

### Škálovaný agile — SAFe a LeSS (krátce)

**SAFe (Scaled Agile Framework)** — framework pro velké organizace (stovky až tisíce vývojářů). Zavádí pojmy jako *Agile Release Train* (ART), *Program Increment* (PI Planning každých ~10 týdnů), *Value Streams*. Kritizováno za přílišnou byrokracii.

**LeSS (Large-Scale Scrum)** — minimalistický přístup od Craiga Larmana a Basa Vodde. „Scrum tak, jak je, jen pro víc týmů." Jeden PO, jeden backlog, sdílený sprint.

### Časté otázky komisaře

**Q: Vyjmenuj 4 hodnoty Agile Manifesta.**
A: 1) Jednotlivci a interakce před procesy a nástroji. 2) Fungující software před dokumentací. 3) Spolupráce se zákazníkem před vyjednáváním o smlouvě. 4) Reagování na změny před dodržováním plánu.

**Q: Jaké jsou role ve Scrumu?**
A: Product Owner (spravuje backlog a priority), Scrum Master (pomáhá týmu dodržovat proces, odstraňuje překážky) a Development Team (sebeřízený, multidisciplinární, 3–9 lidí).

**Q: Jaký je rozdíl mezi Scrum Masterem a projektovým manažerem?**
A: Scrum Master není šéf — je „servant leader", který pomáhá týmu být efektivním a chrání ho před rušením. Nepřiděluje úkoly ani neřídí lidi. Projektový manažer naopak řídí termíny, rozpočet, zdroje a má autoritativní pravomoc.

**Q: Co je Daily Standup?**
A: Krátká denní schůzka týmu (max. 15 minut), kde každý člen odpoví na tři otázky: Co jsem udělal včera? Co plánuji dnes? Co mě blokuje?

**Q: Jaký je rozdíl mezi Scrumem a Kanbanem?**
A: Scrum pracuje v pevných sprintech (1–4 týdny) s definovanými rolemi a artefakty. Kanban je kontinuální flow bez sprintů, s limitem WIP a důrazem na měření průchodu úkolů systémem.

**Q: Co je TDD?**
A: Test-Driven Development — nejdřív se napíše test, který selže (red), pak se napíše minimální kód, aby test prošel (green), a nakonec se kód refaktoruje (refactor).

---

## 3. Testování

### Proč testujeme

- **Hledáme chyby** — žádný netriviální software není bez chyb.
- **Ověřujeme požadavky** — testy ukazují, že software dělá to, co má.
- **Snižujeme riziko** — chyba odhalená v testu stojí desetkrát méně než v produkci.
- **Dokumentace chování** — testy popisují, jak se software má chovat.
- **Refaktoring s jistotou** — testy odhalí, když změna v kódu rozbije existující funkčnost (regresi).

### Testovací pyramida (Mike Cohn)

Koncept z knihy *Succeeding with Agile* (2009). Říká, kolik testů kterého typu by mělo být.

```
              /\
             /  \
            / E2E\          ← málo (pomalé, drahé, křehké)
           /------\
          /        \
         / SYSTEM / \
        /INTEGRACE \       ← střední množství
       /------------\
      /              \
     /     UNIT       \    ← hodně (rychlé, levné, izolované)
    /__________________\
```

#### Anti-pattern: zmrzlinový kornout (ice-cream cone)
Opak pyramidy — málo unit testů, hodně manuálních a E2E testů. Drahé a pomalé.

### Typy testů

#### Unit testy (jednotkové)
- Testují **nejmenší jednotku** kódu — funkci, metodu, třídu — v izolaci.
- Závislosti se nahrazují **mocky** / stuby / fake objekty.
- Rychlé (milisekundy), spouštějí se při každém buildu.
- Nástroje: **JUnit** (Java), **NUnit / xUnit** (.NET), **PHPUnit** (PHP), **Jest** (JS), **pytest** (Python).

**Příklad (PHPUnit, WordPress kontext):**
```php
public function test_slavoj_count_hracu_tymu_returns_zero_for_empty_team() {
    $count = slavoj_count_hracu_tymu('muzi-c', '2024-25');
    $this->assertEquals(0, $count);
}
```

#### Integration testy (integrační)
- Testují **spolupráci více modulů** — např. funkci, která zapisuje do databáze.
- Pomalejší než unit, ale realističtější.
- Příklad: test, že formulář uloží data do MySQL a načte je zpět.

#### System / End-to-end (E2E) testy
- Testují **celou aplikaci** z pohledu uživatele.
- Spouští se proti reálnému prostředí (browser, DB, API).
- Nástroje: **Selenium**, **Cypress**, **Playwright**, **Puppeteer**.
- Pomalé (sekundy až minuty), často nestabilní (flaky).

#### Acceptance testy (UAT — User Acceptance Testing)
- **Zákazník/uživatel** ověřuje, že software splňuje obchodní požadavky.
- Probíhá těsně před nasazením.
- Často podle scénářů z user stories.

#### Regression testy (regresní)
- Po každé změně se znovu spustí existující testy, aby se ověřilo, že nová úprava nerozbila něco staršího.
- Bývá to automatizovaná sada testů v CI pipeline.

#### Smoke testy
- Rychlá „kouřová zkouška" — ověří, že aplikace vůbec naběhne a základní funkce fungují.
- Po deploymentu se obvykle spustí jako první.
- „Zapnul jsem to a nic se nekouří" — odsud název.

#### Performance / Load testy
- **Performance** — jak rychle aplikace reaguje při běžné zátěži.
- **Load** — chování při očekávané maximální zátěži.
- **Stress** — kdy aplikace přestane fungovat (přetížení).
- Nástroje: **JMeter**, **Gatling**, **k6**, **LoadRunner**.

#### Security testy
- Hledají bezpečnostní zranitelnosti — SQL injection, XSS, CSRF, broken authentication.
- **Penetrační testy** — etický hacking.
- Nástroje: **OWASP ZAP**, **Burp Suite**, **SonarQube** (statická bezp. analýza).

#### Usability testy
- Testují, jak se aplikace **používá** — UX, intuitivnost, dostupnost.
- Probíhá s reálnými uživateli (heuristika 5 uživatelů odhalí ~85 % problémů — Jakob Nielsen).

### Black-box vs White-box

| Black-box | White-box |
|---|---|
| Tester nezná vnitřní implementaci. | Tester zná kód. |
| Testuje podle specifikace (vstup → výstup). | Testuje vnitřní cesty, větvení, podmínky. |
| Typicky acceptance, system testy. | Typicky unit, integration testy. |
| **Gray-box** = kombinace obojího. | |

### TDD — Test-Driven Development

Cyklus **Red → Green → Refactor**:

1. **Red:** Napiš test, který popisuje, co kód má dělat. Test selže (kód ještě neexistuje).
2. **Green:** Napiš minimální kód, aby test prošel.
3. **Refactor:** Vyčisti kód beze změny chování — odstraň duplicity, zlepši čitelnost. Testy stále musí projít.

Výhody TDD: lepší design, vyšší pokrytí testy, méně regresí, dokumentace přes testy.

### BDD — Behavior-Driven Development

Rozšíření TDD směrem k business jazyku. Testy se píší v **Gherkin syntaxi** (Given-When-Then):

```gherkin
Funkcionalita: Přihlášení uživatele

  Scénář: Úspěšné přihlášení správnými údaji
    Daný uživatel je na přihlašovací stránce
    Když zadá email "test@example.com" a heslo "secret123"
    A stiskne tlačítko "Přihlásit"
    Pak je přesměrován na dashboard
    A v hlavičce vidí svoje jméno
```

Nástroje: **Cucumber** (Java), **SpecFlow** (.NET), **Behat** (PHP).

### Code coverage (pokrytí kódu)

Měří, kolik procent kódu spustí testy. Typy:

- **Line coverage** — kolik řádků kódu se vykonalo.
- **Branch coverage** — kolik větví (if/else, switch) se proběhlo.
- **Function coverage** — kolik funkcí bylo zavoláno.

**Pozor:** 100 % coverage neznamená 100 % správnost. Testuje, že kód běží, ne že běží **správně**. Cíl bývá 70–80 %, kritické části 90 %+.

Nástroje: **JaCoCo** (Java), **Istanbul/nyc** (JS), **Coverage.py** (Python), **Cobertura**.

### Testovací nástroje — přehled

| Nástroj | Jazyk / Účel |
|---|---|
| **JUnit** | Java unit testy |
| **NUnit / xUnit** | .NET unit testy |
| **PHPUnit** | PHP unit testy (používá i WordPress core) |
| **Jest** | JavaScript / TypeScript unit testy |
| **pytest** | Python unit testy |
| **Mockito** | Mockování v Javě |
| **Selenium** | E2E testy webu, ovládá browser přes WebDriver |
| **Cypress** | Moderní E2E framework pro web (JS) |
| **Playwright** | E2E nástroj od Microsoftu (multi-browser) |
| **Postman** | Manuální i automatizované API testy |
| **JMeter** | Load testy |
| **SoapUI** | API testy (SOAP i REST) |

### Časté otázky komisaře

**Q: Co je unit test?**
A: Test nejmenší izolované jednotky kódu — typicky funkce nebo metody. Závislosti se mockují, aby se testovala jen daná jednotka.

**Q: Co je testovací pyramida?**
A: Doporučený poměr testů — hodně unit testů (základ), méně integračních a nejméně E2E testů (špička). Unit testy jsou rychlé a levné, E2E jsou pomalé a křehké.

**Q: Vysvětli TDD.**
A: Test-Driven Development — nejdřív napíšu test, který selže (red), pak minimální kód, aby prošel (green), a nakonec kód refaktoruju (refactor). Cyklus se opakuje.

**Q: Rozdíl mezi black-box a white-box testováním.**
A: White-box — tester vidí kód a testuje vnitřní cesty (typicky unit testy). Black-box — tester nezná implementaci, testuje jen vstupy a výstupy podle specifikace (typicky acceptance testy).

**Q: Co je regresní testování?**
A: Po každé změně v kódu se znovu spustí stará sada testů, aby se ověřilo, že nová úprava nerozbila něco, co dříve fungovalo.

**Q: Jaký je rozdíl mezi smoke testem a acceptance testem?**
A: Smoke test je rychlá kontrola po deploymentu („aplikace naběhla, login funguje"). Acceptance test je ověření zákazníkem, že software splňuje obchodní požadavky podle specifikace.

**Q: Co znamená 80% code coverage?**
A: Že testy spustily 80 % řádků/větví kódu. Neznamená to, že kód je bez chyb — jen že většina kódu se při testech vykonala.

---

## 4. Issue tracking systémy

### Definice

**Issue tracking system (ITS)** je nástroj pro evidenci, prioritizaci a sledování úkolů, požadavků, chyb (bugů) a dalších „issues" v softwarovém projektu. Slouží jako jednotné místo pravdy pro celý tým — vývojáře, testery, PM, zákazníky.

### K čemu slouží

- Evidence chyb (bug tracking).
- Plánování nových funkcí (feature requests).
- Sledování úkolů (task management).
- Komunikace mezi týmem a stakeholdery.
- Historie změn a auditovatelnost.
- Reporting (kolik bugů, jak dlouho trvá oprava, velocity sprintu).
- Propojení s kódem v Gitu — commity zmiňující issue, automatické zavírání.

### Struktura issue

Typické pole issue:

| Pole | Popis |
|---|---|
| **Title / Summary** | Krátký popis (1 řádek). |
| **Description** | Detailní popis problému, reprodukce, screenshoty. |
| **Type** | Bug, Task, Feature, Epic, Story, Improvement. |
| **Priority** | Blocker, Critical, Major, Minor, Trivial. |
| **Severity** | Jak závažný dopad má bug (Critical → Cosmetic). |
| **Status** | Aktuální stav (Open, In Progress, …). |
| **Assignee** | Kdo na tom pracuje. |
| **Reporter** | Kdo issue vytvořil. |
| **Labels / Tags** | Klíčová slova (frontend, backend, db, urgent). |
| **Components** | Část systému, které se issue týká. |
| **Affects Version** | Ve které verzi se chyba projevuje. |
| **Fix Version** | V jaké verzi má být opravená. |
| **Sprint** | Do kterého sprintu patří (Scrum). |
| **Story points / Estimate** | Odhad pracnosti. |
| **Comments** | Diskuze a poznámky. |
| **Attachments** | Soubory, logy, screenshoty. |
| **Linked issues** | Vazby (blocks, is blocked by, duplicates, relates to). |
| **Due date** | Termín. |

### Workflow / životní cyklus issue

Klasický workflow:

```
   ┌──────┐    start    ┌─────────────┐   submit   ┌───────────┐   approve   ┌──────┐
   │ Open │ ──────────► │ In Progress │ ─────────► │ In Review │ ──────────► │ Done │
   └──────┘             └─────────────┘            └───────────┘             └──────┘
       ▲                       │                         │                       │
       │       reject          │                         │                       │
       └───────────────────────┴─────────────────────────┘                       │
                                                                                  │
       ┌──────────┐    reopen    ┌────────┐    close after verification          │
       │ Reopened │ ◄────────────┤ Closed │ ◄──────────────────────────────────┘
       └──────────┘              └────────┘
```

Stavy se liší podle nástroje a procesu týmu. Některé bývají navíc: *Backlog*, *To Do*, *Ready for QA*, *In Testing*, *Blocked*, *Won't Fix*, *Duplicate*.

### Propojení s Gitem

Většina ITS umí napojit Git repository. V commit message zmiňuješ issue:

```
git commit -m "fix #123: opraveno řazení hráčů podle čísla dresu"
```

Funkce:
- **Reference** (`#123`) — propojí commit s issue, zobrazí ho v komentářích.
- **Smart commits** (Jira, GitLab) — `Closes #123`, `Fixes #45` automaticky uzavře issue po merge.
- **Branch per issue** — naming convention `feature/SLAVOJ-42-pridat-galerii`.
- **PR/MR linking** — Pull Request odkazuje na issue, po merge se issue zavře.

### Představitelé

#### Jira (Atlassian)
- **Nejrozšířenější** komerční ITS, dominantní v enterprise světě.
- Velmi konfigurovatelná — vlastní workflow, fieldy, screens, schémata.
- Podporuje Scrum, Kanban, scaled agile.
- JQL (Jira Query Language) pro pokročilé vyhledávání: `project = SLAVOJ AND status = "In Progress" AND assignee = currentUser()`.
- Integrace s Confluence, Bitbucket, GitHub.
- Verze: **Cloud** (SaaS) a **Data Center** (self-hosted).

#### YouTrack (JetBrains)
- ITS od tvůrců IntelliJ, PhpStorm, ReSharper.
- Silný textový search a "command line" interakce — `state Fixed assignee me priority Critical`.
- Lehčí konfigurace než Jira, čistší UI.
- Vlastní jazyk YQL pro queries.
- Integrace s JetBrains IDE, Git, TeamCity.
- V SolverTech se používá pro správu ticketů a knowledge base.

#### GitHub Issues
- Vestavěný issue tracker na GitHubu (zdarma pro veřejné i privátní repo).
- Jednoduché, ale rozšiřitelné labely, milestones, projects (Kanban boardy).
- Skvělé pro open-source projekty.
- Propojení s commits, PRs, Actions (CI/CD).

#### GitLab Issues
- Vestavěné v GitLabu, podobné GitHub Issues, ale bohatší (epics, weights, scoped labels).
- Integrace s GitLab CI/CD, MR (merge requesty), wiki.
- Self-hosted i SaaS verze.

#### Redmine
- Open-source ITS (Ruby on Rails).
- Vhodný pro multiproject prostředí.
- Plugin ekosystém, ale UI je zastaralé.

#### Bugzilla
- Historický open-source ITS (Mozilla, 1998).
- Specializovaný na bug tracking, nepodporuje moderní agile workflow tak dobře.
- Stále se používá u některých open-source projektů (Mozilla, Eclipse, Apache).

#### Azure DevOps Boards
- ITS od Microsoftu, součást Azure DevOps Services.
- Integrace s Azure Repos, Pipelines, Test Plans.
- Podporuje Scrum, Agile, CMMI procesní šablony.
- Work item types: User Story, Task, Bug, Epic, Feature.

#### Trello
- Spíše jednoduchý Kanban než plnohodnotný ITS.
- Vhodný pro malé týmy a osobní úkoly.

#### Asana, ClickUp, Linear, Monday.com
- Moderní task management nástroje s ITS funkcionalitou.
- **Linear** — minimalistický, oblíbený u startupů, rychlé klávesové zkratky.

### Kanban a Scrum boardy v ITS

Většina moderních ITS nabízí vizuální boardy:

- **Scrum board** — sloupce odpovídají workflow (To Do, In Progress, Done), filtrován na aktuální sprint, zobrazuje burndown chart.
- **Kanban board** — kontinuální flow, často s WIP limity, swimlanes (řádky podle priority nebo assignee).

### Časté otázky komisaře

**Q: K čemu slouží issue tracker?**
A: K evidenci úkolů, chyb a požadavků v projektu. Slouží jako centrální místo komunikace týmu, umožňuje prioritizaci, sledování stavu a propojení s kódem v Gitu.

**Q: Jmenuj 3 issue tracking systémy.**
A: Jira (Atlassian), YouTrack (JetBrains), GitHub Issues. Případně GitLab Issues, Redmine, Azure DevOps Boards.

**Q: Co je workflow v issue trackeru?**
A: Posloupnost stavů, kterými issue prochází od vytvoření po uzavření — typicky Open → In Progress → In Review → Done. Workflow je obvykle konfigurovatelný podle procesu týmu.

**Q: Jak propojíš commit v Gitu s issue v Jiře?**
A: V commit message uvedu identifikátor issue, např. `SLAVOJ-42: oprava řazení hráčů`. Jira automaticky propojí commit s issue. Smart commits jako `Fixes SLAVOJ-42` mohou issue rovnou uzavřít.

**Q: Jaké jsou typické fieldy v issue?**
A: Title, description, type (bug/task/feature), priority, status, assignee, reporter, labels, comments, attachments, story points, sprint.

---

## 5. Posouzení kvality software a důležité aspekty

### Definice

**Kvalita softwaru** je míra, do jaké software splňuje stanovené požadavky a očekávání uživatelů. Posuzuje se podle objektivních charakteristik (funkčnost, výkon, bezpečnost, …) i subjektivních (použitelnost, spokojenost uživatele).

### ISO/IEC 25010 — norma pro kvalitu software

ISO/IEC 25010:2011 (revize 2023) je mezinárodní norma definující **model kvality produktu**. Nahradila starší **ISO/IEC 9126** (z roku 1991). Definuje 8 hlavních charakteristik kvality:

#### 1. Funkční vhodnost (Functional Suitability)
- **Funkční úplnost** — pokrývá software všechny specifikované úkoly?
- **Funkční správnost** — produkuje správné výsledky?
- **Funkční přiměřenost** — splňuje funkce skutečně dané cíle?

#### 2. Výkonnostní efektivita (Performance Efficiency)
- **Časové chování** — rychlost odezvy.
- **Využití zdrojů** — paměť, CPU, síť.
- **Kapacita** — kolik uživatelů / dat zvládne.

#### 3. Kompatibilita (Compatibility)
- **Koexistence** — funguje vedle jiných systémů bez konfliktů.
- **Interoperabilita** — umí vyměňovat data s jinými systémy.

#### 4. Použitelnost (Usability)
- **Srozumitelnost** — uživatel pochopí účel.
- **Naučitelnost** — jak rychle se uživatel naučí.
- **Ovladatelnost** — snadnost ovládání.
- **Ochrana před chybami** — brání chybnému užití.
- **Estetika UI** — vzhled a líbivost.
- **Přístupnost** — pro uživatele s postižením (WCAG, ARIA).

#### 5. Spolehlivost (Reliability)
- **Zralost (Maturity)** — bezporuchovost.
- **Dostupnost (Availability)** — kolik % času je systém přístupný (99,9 % = „three nines").
- **Odolnost proti chybám (Fault Tolerance)** — funguje i při dílčích selháních.
- **Obnovitelnost (Recoverability)** — jak rychle se zotaví po výpadku.

#### 6. Bezpečnost (Security)
- **Důvěrnost (Confidentiality)** — ochrana před neoprávněným přístupem.
- **Integrita** — data nelze nepovoleně měnit.
- **Nepopiratelnost (Non-repudiation)** — akce nelze popřít.
- **Auditovatelnost** — záznam, kdo co kdy udělal.
- **Autentičnost** — ověření identity.

#### 7. Udržovatelnost (Maintainability)
- **Modularita** — software se skládá z nezávislých modulů.
- **Znovupoužitelnost** — komponenty lze použít opakovaně.
- **Analyzovatelnost** — snadné najít příčinu problému.
- **Modifikovatelnost** — snadné měnit kód bez zavlečení chyb.
- **Testovatelnost** — snadno se testuje.

#### 8. Přenositelnost (Portability)
- **Adaptabilita** — přizpůsobí se různým prostředím (OS, DB).
- **Instalovatelnost** — snadno se instaluje a odinstaluje.
- **Nahraditelnost** — může nahradit jiný software se stejným účelem.

> Norma má i rozšířený model **„quality in use"** (kvalita při užívání), který sleduje efektivitu, produktivitu, bezpečí a spokojenost uživatele.

### Funkcionální vs nefunkcionální požadavky

| Funkční (FR) | Nefunkční (NFR) |
|---|---|
| **Co** systém dělá. | **Jak dobře** to dělá. |
| „Uživatel se přihlásí emailem a heslem." | „Přihlášení trvá max. 2 sekundy." |
| „Systém zobrazí seznam zápasů sezony." | „Stránka se musí načíst do 1 s na 4G." |
| „Admin může vytvořit nového hráče." | „Heslo musí mít min. 12 znaků a být uloženo s bcrypt." |
| Snadno se testují. | Často těžko měřitelné. |
| Specifikace funkcí, business pravidel. | Vlastnosti jako výkon, bezpečnost, dostupnost. |

NFR často korespondují s charakteristikami ISO 25010.

### Technický dluh (Technical Debt)

Pojem zavedl **Ward Cunningham** (1992) — metafora: rychlé, špinavé řešení je jako vzít si půjčku. Krátkodobě pomůže, ale **úroky** (pomalejší vývoj, víc bugů) se postupně sčítají.

#### Typy:
- **Záměrný dluh** — vědomě jsme zvolili rychlé řešení („teď to dáme do produkce, refaktorujeme později").
- **Nechtěný dluh** — vznikl neznalostí, neopatrností.
- **Erozní dluh** — kód zastarává s časem (knihovny, jazyk, framework).

#### Symptomy:
- Pomalý vývoj nových funkcí.
- Hodně bugů, zvlášť v okrajových případech.
- Strach z úprav („tohle se nikdo neodvažuje měnit").
- Duplicitní kód, neaktuální dokumentace.
- Zastaralé knihovny s bezpečnostními chybami.

#### Splácení:
- Refaktoring v každém sprintu (~20 % kapacity).
- Boy Scout Rule: „Zanech kód lepší, než jsi ho našel."
- Code review, statická analýza.

### Code review

**Code review** je systematická kontrola kódu jinou osobou před začleněním do hlavní větve.

#### Benefity
- Odhalení chyb dříve, než se dostanou do produkce.
- Sdílení znalostí v týmu.
- Konzistence stylu a architektury.
- Mentoring juniorů.
- Vyšší code ownership.

#### Formy
- **Pull / Merge Request review** — nejčastější. PR na GitHubu / GitLabu, komentáře k řádkům, schválení.
- **Pair programming** — review v reálném čase.
- **Formal inspection** — Fagan inspection, strukturovaný proces (méně časté).

#### Co se kontroluje
- Funkcionalita — dělá kód to, co má?
- Čitelnost — pochopí to ostatní?
- Konzistence se zbytkem kódu.
- Bezpečnost (injection, XSS, autorizace).
- Výkon (N+1 query, zbytečné cykly).
- Testy — jsou napsané a smysluplné?
- Dokumentace a komentáře.

### Statická analýza kódu

**Statická analýza** zkoumá kód **bez jeho spuštění**. Hledá chyby, code smells, bezpečnostní zranitelnosti, porušení coding standards.

#### Nástroje

| Nástroj | Účel |
|---|---|
| **SonarQube** | Univerzální platforma, podporuje desítky jazyků. Měří code coverage, technický dluh, duplicitu, bugs, vulnerabilities, code smells. |
| **ESLint** | JavaScript / TypeScript linting. |
| **PHPStan** / **Psalm** | PHP statická analýza, type checking. |
| **PHP_CodeSniffer** (PHPCS) | Kontrola coding standards (PSR-12, WordPress Coding Standards). |
| **Pylint** / **Flake8** / **mypy** | Python linting a type checking. |
| **Checkstyle** / **PMD** / **SpotBugs** | Java statická analýza. |
| **Roslyn Analyzers** / **ReSharper** | .NET / C#. |
| **clang-tidy** | C/C++. |
| **Snyk** / **Dependabot** | Detekce zranitelností v závislostech (CVE). |

Statická analýza se obvykle pouští v **CI pipeline** — když lint selže, PR nelze mergovat.

### CI/CD a kvalita

**CI (Continuous Integration)** — vývojáři často (nejlépe denně) integrují svoje změny do hlavní větve. Každá integrace spustí automatický build a testy.

**CD (Continuous Delivery / Deployment)**
- **Continuous Delivery** — každá změna projde testy a je připravená k nasazení manuálně.
- **Continuous Deployment** — automaticky se nasazuje do produkce, pokud projdou všechny kontroly.

#### Typická CI/CD pipeline

```
   ┌────────┐   ┌──────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌────────┐
   │ commit │ ► │ lint │ ► │  build   │ ► │  testy   │ ► │  deploy  │ ► │ smoke  │
   │  push  │   │      │   │ artefakt │   │ unit+int │   │   stage  │   │ testy  │
   └────────┘   └──────┘   └──────────┘   └──────────┘   └──────────┘   └────────┘
                                                                              │
                                                                              ▼
                                                                       ┌──────────┐
                                                                       │  deploy  │
                                                                       │   prod   │
                                                                       └──────────┘
```

#### Vazba na kvalitu
- **Rychlá zpětná vazba** — chyba se objeví hned po commitu.
- **Vynucení standardů** — pipeline neprojde bez zelených testů, bez prošlého lintu, bez minimálního coverage.
- **Reprodukovatelnost** — automatický build = jistota, že software je sestavený stejně pokaždé.
- **Quality gates** — SonarQube může zablokovat merge, pokud je překročena hranice technického dluhu.

#### Nástroje CI/CD
- **GitHub Actions**
- **GitLab CI/CD**
- **Jenkins** (klasika, self-hosted)
- **CircleCI**
- **TeamCity** (JetBrains)
- **Azure Pipelines**
- **Bitbucket Pipelines**

### Časté otázky komisaře

**Q: Jmenuj normu pro kvalitu software.**
A: ISO/IEC 25010 (revidovala starší ISO/IEC 9126). Definuje 8 charakteristik: funkční vhodnost, výkonnostní efektivita, kompatibilita, použitelnost, spolehlivost, bezpečnost, udržovatelnost, přenositelnost.

**Q: Rozdíl mezi funkčním a nefunkčním požadavkem?**
A: Funkční říká, **co** systém dělá („uživatel se přihlásí emailem"). Nefunkční říká, **jak dobře** to dělá („přihlášení trvá max. 2 sekundy", „heslo se ukládá hashované").

**Q: Co je technický dluh?**
A: Metafora — vědomě nebo nevědomě zvolíme krátkodobé, ne úplně čisté řešení. Postupně se „úroky" sčítají v podobě pomalejšího vývoje, více chyb a obtížnější údržby. Splácí se refaktoringem.

**Q: Co je code review a k čemu slouží?**
A: Systematická kontrola kódu jiným vývojářem před začleněním do hlavní větve. Odhaluje chyby, sdílí znalosti, zajišťuje konzistenci a slouží jako mentoring.

**Q: Co je CI/CD?**
A: CI = Continuous Integration, automatické sestavení a testy po každém commitu. CD = Continuous Delivery / Deployment, automatická příprava na nasazení nebo přímo nasazení do produkce.

**Q: Co je SonarQube?**
A: Platforma pro statickou analýzu kódu. Měří code coverage, duplicity, bugs, security vulnerabilities, code smells a technický dluh. Často se používá jako quality gate v CI pipeline.

**Q: Kolik je „three nines" dostupnost?**
A: 99,9 % uptime = max. ~8,76 hodin výpadku za rok. „Five nines" (99,999 %) = jen ~5 minut za rok — typické pro telekomunikace, banky.

---

## Souhrn klíčových pojmů

Student musí umět vysvětlit:

1. **SDLC** — Software Development Life Cycle, fáze: analýza, design, implementace, testování, nasazení, údržba.
2. **Vodopád (Waterfall)** — lineární model, fáze za fází, bez vracení.
3. **V-model** — vodopád s páry vývoj ↔ test.
4. **Iterativní vs inkrementální vývoj** — opakované cykly vs přidávání kusů.
5. **Spirálový model (Boehm)** — iterativní + analýza rizik.
6. **Agile Manifesto** — 4 hodnoty (2001, Snowbird, Utah).
7. **Scrum** — framework s rolemi (PO, SM, Dev Team), artefakty (Product/Sprint Backlog, Increment) a eventy (Sprint, Planning, Daily, Review, Retrospective).
8. **Sprint** — časový box 1–4 týdny, výsledkem Increment.
9. **User story** — „Jako [role] chci [funkci], abych [důvod]."
10. **Story points** — relativní odhad pracnosti (Fibonacci).
11. **Kanban** — vizualizace, WIP limity, kontinuální flow.
12. **XP (Extreme Programming)** — pair programming, TDD, refactoring, CI.
13. **Unit test** — test nejmenší izolované jednotky kódu.
14. **Integration test** — test spolupráce komponent.
15. **E2E test** — test celé aplikace z pohledu uživatele (Selenium, Cypress).
16. **Testovací pyramida** — hodně unit, méně integration, nejméně E2E.
17. **TDD** — Red → Green → Refactor.
18. **BDD** — testy v Gherkin (Given-When-Then).
19. **Code coverage** — % kódu pokrytého testy (line/branch/function).
20. **Mock / Stub** — falešná závislost v unit testu.
21. **Issue tracker** — Jira, YouTrack, GitHub Issues, GitLab Issues.
22. **ISO/IEC 25010** — norma kvality SW, 8 charakteristik.
23. **Funkční vs nefunkční požadavek** — co vs jak dobře.
24. **Technický dluh (Ward Cunningham)** — krátkodobé řešení = budoucí náklady.
25. **CI/CD** — Continuous Integration / Delivery / Deployment.
26. **Statická analýza** — kontrola kódu bez spuštění (SonarQube, ESLint).
27. **Code review** — kontrola kódu druhým vývojářem před mergem.

---

## Možné praktické úkoly u zkoušky

Co může komisař chtít, aby student načrtnul/vysvětlil/předvedl:

1. **Načrtnout SDLC** — všech 6 fází a krátce popsat.
2. **Porovnat vodopád a Scrum** — tabulka rozdílů (změna požadavků, dodávky, dokumentace).
3. **Vysvětlit Scrum sprint** — co se děje od Sprint Planning po Retrospective, role, artefakty.
4. **Napsat user story** — pro reálnou funkci (např. „přidat hráče do týmu na webu Slavoj Mýto").
5. **Načrtnout Kanban board** — sloupce, WIP limity, ukázat rozdíl proti Scrumu.
6. **Vysvětlit cyklus TDD** — Red → Green → Refactor s konkrétním příkladem (např. funkce na sčítání).
7. **Načrtnout testovací pyramidu** — která vrstva je největší a proč.
8. **Napsat unit test** — pseudokód testu pro jednoduchou funkci (např. `nasob(a, b)`).
9. **Rozdíl mezi unit, integration a E2E testem** — na konkrétním příkladu (přihlašovací formulář).
10. **Vyjmenovat charakteristiky ISO 25010** — všech 8 a krátce vysvětlit.
11. **Příklad funkčního a nefunkčního požadavku** — pro reálnou aplikaci.
12. **Načrtnout workflow issue v Jiře** — stavy a přechody.
13. **Spojit commit s issue** — jak vypadá commit message s referencí (`fix #123`).
14. **Načrtnout CI/CD pipeline** — co se děje od push po deploy.
15. **Vysvětlit technický dluh** — jak vzniká a jak se splácí.
16. **Code review checklist** — co by zkontroloval na PR od kolegy.
17. **Vyjmenovat 3 testovací nástroje** — pro Javu / JS / PHP a říct, na co slouží.
18. **Příklad bug reportu** — jak vypadá dobře napsaný bug v Jiře (title, kroky reprodukce, screenshot, severity).
19. **Vysvětlit „Definition of Done"** — kdy je úkol skutečně hotový.
20. **Spočítat dostupnost** — co znamená 99,9 % uptime za rok v hodinách.

---

## Poznámka pro lektora

- Pokud bude komise chtít, ať student propojí teorii s vlastním projektem (web TJ Slavoj Mýto), je dobré upozornit: WordPress používá **PHPUnit** pro unit testy core kódu, projekt používá **Git/GitHub Issues** pro evidenci úkolů, dokumentace je v `docs/`. To je praktická ukázka SDLC v malém měřítku.
- Sledovat, jestli student nezamění **vodopád** a **V-model** (V-model je „testovací varianta" vodopádu).
- Často se plete **iterativní** vs **inkrementální** — iterativní zpřesňuje totéž, inkrementální přidává nové kusy. V praxi se kombinují.
- U Scrumu je důležité, aby student NEŘÍKAL, že Scrum Master je „šéf týmu" — to je častá chyba. Je to servant leader bez pravomoci přidělovat úkoly.
- U ISO/IEC 25010 stačí jmenovat 8 charakteristik a krátce každou popsat — student nemusí znát všechny dílčí pod-charakteristiky.
- TDD cyklus Red-Green-Refactor by měl student umět načrtnout i s konkrétním kódem.
