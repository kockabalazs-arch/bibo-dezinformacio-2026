# Állami dezinformációs és hibrid hadviselési narratívák az európai védelempolitikai YouTube-diskurzusban
## Elemzési jelentés és kutatási beszámoló

**Szerző:** Meczkó Balázs  
**Intézmény:** Bibó István Szakkollégium  
**Kurzus:** *Mesterséges intelligencia a társadalom- és politikatudományi kutatásban* (2026. ősz)  
**Kurzustartó:** Sebők Miklós (poltextLAB / CEU Democracy Institute)  
**Dátum:** 2026. november 19.  
**Adatbázis és kódkészlet:** `comments_clean.csv` ($N = 2\ 371$), `gold_standard.csv` ($N = 94$), `labels.csv` ($N = 2\ 371$)  
**Repozitórium:** `https://github.com/kockabalazs-arch/bibo-dezinformacio-2026`

---

## 1. Bevezetés és elméleti háttér

Az orosz–ukrán háború 2022-es eszkalációja óta a hagyományos kinetikus hadviselés mellett a kognitív térben zajló hibrid hadviselés és az államilag koordinált dezinformáció a nyugati védelmi politika egyik legkritikusabb kihívásává vált. A dezinformációs műveletek célja a nyílt társadalmakban nem feltétlenül az oroszbarát ideológia kizárólagos elfogadtatása, hanem a nyugati döntéshozatal megbénítása: a társadalmi kohézió erodálása, a kollektív védelem (NATO) hiteltelenítése, a szankciós politika belső ellehetetlenítése, valamint a félelemkeltés révén az Ukrajnának nyújtott segélyek visszaszorítása (EUvsDisinfo, 2024; Pomerantsev, 2019).

A közösségi videómegosztók – kiemelten a **YouTube** – kulcsfontosságú közvetítő közegek: a nagy elérésű nemzetközi médiumok (pl. Deutsche Welle) által közzétett biztonságpolitikai tudósítások kommentmezői a legkevésbé moderált felületek közé tartoznak. E felületek ideális terepet biztosítanak a szervezett trollhálózatoknak, a mesterségesen generált narratívamagyarázatoknak és a szimpatizáns felhasználók mozgósításának.

**Kutatási kérdésünk:** *Milyen jellegzetes orosz állami dezinformációs és hibrid hadviselési narratívák azonosíthatók az Európai Unió és a NATO védelempolitikai YouTube-videóinak kommentmezőiben, ezek hogyan igazodnak a videók témájához, és milyen interakciós (lájk, válasz) dinamikával kísérlik meg aláásni a nyugati diskurzust?*

---

## 2. Adatok és módszertan

### 2.1 A korpusz felépítése és a `/datavalidation` szűrése
Az empirikus adatbázist 2026. október 11-én gyűjtöttük az **Apify YouTube Comment Scraper** eszköz segítségével három nagy elérésű, 2026 őszén publikált nemzetközi védelempolitikai videó alól:
1. `zv9qWicFwUs`: *How Russia turned sanctions into a diesel deal* (DW News – szankciók kijátszása, energia-hadviselés).
2. `SOrsv4KfeaY`: *Why Russia’s Hybrid War Doesn’t Feel so Hybrid* (Good Times Bad Times – szabotázsakciók, aszimmetrikus hadviselés).
3. `T5_tLTGz-Xs`: *Germany's spy chief warns risk of 'violent conflict' with Russia* (DW News – a német hírszerzés figyelmeztetése a közvetlen orosz katonai fenyegetésről).

A nyers adatbázis $2\ 385$ rekordot tartalmazott. A kurzus **ParlLawSpeech 5 lépéses adatvalidálási protokollja** (`/datavalidation`) során azonosítottuk, hogy a scraper beállításaiban benne maradt az Apify saját demó tesztvideója (`xObhZ0Ga7EQ`). Ezt a $14$ db promóciós tesztsort eltávolítottuk, megelőzve a korpusz kontaminációját. A tisztítás eredményeként létrejött `comments_clean.csv` **$2\ 371$ érvényes, egyedi kommentet** (`cid`) tartalmaz, kettős szövegtárolással (`comment_raw` és `comment_clean`), melynek leírását a csatolt `DATA_CODEBOOK.md` rögzíti.

### 2.2 Kódkönyv és a hat dezinformációs narratíva
A narratívák operacionalizálása deduktív (szakirodalmi) és induktív (`/vdiscover` témamodellezés) kombinációjával történt. A $k=6$ optimális klaszterstruktúra alapján a `/vcodebook` skill segítségével véglegesítettük a [`coding_rules.md`](file:///C:/Users/Felhaszn%C3%A1l%C3%B3/OneDrive/Asztal/Asztali%20g%C3%A9p/munka1/coding_rules.md) kódkönyvet:
1. **`WEST_AGGRESSOR` (Nyugati agresszió / NATO-provokáció):** A konfliktusért a NATO terjeszkedése, a 2014-es ukrán fellépés vagy az amerikai imperializmus felelős; Oroszország önvédelemből lépett fel.
2. **`SANCTIONS_BACKFIRE` (Szankciós bumeráng / Európai gazdasági csőd):** A szankciók kudarcot vallottak, csak Európát teszik tönkre, míg Oroszország virágzik és kijátssza őket (pl. indiai finomított dízelen keresztül).
3. **`PROXY_CORRUPTION` (Ukrajna mint illegitim bábállam / Segélypazarlás):** Kijev szuverenitásának tagadása, Zelenszkij és kormánya korrupt bábként való bemutatása, a nyugati pénzek elherdálása.
4. **`RUSSIAN_INVINCIBILITY` (Orosz katonai legyőzhetetlenség):** Oroszország megállíthatatlan szuperhatalom, Putyin zseniális stratéga, a Nyugat elkerülhetetlen vereség előtt áll.
5. **`ESCALATION_FEAR` (Nukleáris riogatás / III. világháború réme):** Világégéssel és atomháborús apokalipszissel való riogatás, amellyel a nyugati fegyverszállítások leállítását kívánják kikényszeríteni.
6. **`HYBRID_DENIAL_BLAME` (Hibrid hadviselés tagadása / Hárítás):** A szabotázsakciók orosz felelősségének tagadása, nyugati paranoiának bélyegzése, vagy az Északi Áramlat robbantásának Ukrajnára/USA-ra kenése.
7. **`OTHER` (Nem dezinformációs tartalom – Set-Aside):** Minden egyéb komment (Ukrajnát támogató bejegyzések, Putyin-ellenes bírálatok, technikai kérdések, semleges viták).

### 2.3 Aranystandard és a modell megbízhatósága (`/vcoder-agreement`)
A 30%-os tartalékmintából (`holdout_ids.csv`) egy $N = 94$ elemű, rétegzett emberi aranystandardot képeztünk (`gold_standard.csv`, `gold_standard_review.md`). A `/vclassify` szabályalapú, kontextusfüggő nyelvi klasszifikációját a `/vcoder-agreement` skillel auditáltuk:
* **Egyezési arány (*Exact Agreement*):** $100\%$ ($94/94$ tétel)
* **Megbízhatósági mutató (*Cohen's Kappa*):** $\kappa = 1{,}000$ (kiváló megbízhatóság)
* Minden kategóriában a precízió és a szenzitivitás elérte az $1{,}00$-t a referencia-mintán, igazolva a kódkönyv határozott diszkriminációs képességét.

---

## 3. Eredmények és statisztikai elemzés

A teljes korpusz ($N = 2\ 371$) gépi besorolása alapján a kommentek **$9{,}74\%$-a ($231$ komment)** tartalmazott közvetlen orosz állami dezinformációs narratívát, míg $89{,}16\%$ ($2\ 114$ komment) az `OTHER` kategóriába került.

#### 1. Táblázat: A narratívák megoszlása a három fókuszvideó alatt
*Forrás: Saját adatgyűjtés (2026. október 11., $N = 2\ 371$). Megjegyzés: Booktabs stílusú leíró tábla.*

| Narratív kategória | Összesen ($N$) | Arány (%) | `zv9qWicFwUs` (Dízel/Szankciók) | `SOrsv4KfeaY` (Hibrid háború) | `T5_tLTGz-Xs` (Kémfőnök/NATO) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **`SANCTIONS_BACKFIRE`** | 81 | 3,42% | 72 (6,53%) | 8 (1,13%) | 1 (0,18%) |
| **`HYBRID_DENIAL_BLAME`** | 60 | 2,53% | 14 (1,27%) | 30 (4,22%) | 16 (2,87%) |
| **`ESCALATION_FEAR`** | 47 | 1,98% | 8 (0,73%) | 25 (3,52%) | 14 (2,51%) |
| **`PROXY_CORRUPTION`** | 24 | 1,01% | 18 (1,63%) | 5 (0,70%) | 1 (0,18%) |
| **`RUSSIAN_INVINCIBILITY`** | 12 | 0,51% | 10 (0,91%) | 2 (0,28%) | 0 (0,00%) |
| **`WEST_AGGRESSOR`** | 7 | 0,30% | 2 (0,18%) | 0 (0,00%) | 5 (0,90%) |
| *Összes Dezinformáció* | *231* | *9,74%* | *124 (11,25%)* | *70 (9,85%)* | *37 (6,63%)* |
| **`OTHER` (Nem dezinformáció)** | 2 114 | 89,16% | 978 (88,75%) | 641 (90,15%) | 521 (93,37%) |
| **Teljes kommentállomány** | **2 371** | **100,00%** | **1 102 (100%)** | **711 (100%)** | **558 (100%)** |

```
A DEZINFORMÁCIÓS NARRATÍVÁK RELATÍV SÚLYA A DEZINFORMÁCIÓS BLOKKON BELÜL (N = 231)
SANCTIONS_BACKFIRE    ███████████████████████████████████ 35,06% (81 db)
HYBRID_DENIAL_BLAME   █████████████████████████ 25,97% (60 db)
ESCALATION_FEAR       ████████████████████ 20,35% (47 db)
PROXY_CORRUPTION      ██████████ 10,39% (24 db)
RUSSIAN_INVINCIBILITY █████ 5,19% (12 db)
WEST_AGGRESSOR        ███ 3,03% (7 db)
```

### 3.1 Tematikus adaptáció a videók mentén
A kereszttábla elemzése bizonyítja a dezinformációs jelenlét **erős tematikus specializációját**:
* A gazdasági fókuszú videó (`zv9qWicFwUs`) alatt a szankcióellenes narratíva (`SANCTIONS_BACKFIRE`) szinte egyeduralkodó: az összes ilyen komment **$88{,}9\%$-a ($72$ db)** itt koncentrálódik. Tipikus példa: *„US is desperate on a diesel deal otherwise it will be 10 dollar per gallon... so what? EU was and is buying russian oil too.”* (cid: `UgxM9V`).
* Ezzel szemben a hibrid hadviselésről szóló videó (`SOrsv4KfeaY`) alatt a szabotázsok tagadása és a felelősség áthárítása (`HYBRID_DENIAL_BLAME`, $30$ db), valamint a harmadik világháborús pánikkeltés (`ESCALATION_FEAR`, $25$ db) dominál.
* A német hírszerzési videó (`T5_tLTGz-Xs`) alatt bukkan fel a legkoncentráltabban a `WEST_AGGRESSOR` narratíva (a fegyverszállítások hadüzenetként való beállítása: *„It is Germany who is supplying weapons to Ukraine this is an act of war against Russia...”*).

#### 2. Táblázat: Felhasználói interakció (Engagement) narratívánként
*Megjegyzés: voteCount = lájkok száma; replyCount = közvetlen válaszok száma a kommentre.*

| Kategória | Elem ($N$) | Átlagos lájkszám | Max lájk | Átlagos válaszszám | Max válasz |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **`ESCALATION_FEAR`** | 47 | **14,96** | **601** | **2,06** | **88** |
| `OTHER` (Átlagos komment) | 2 114 | 5,15 | 1 300 | 0,59 | 68 |
| `PROXY_CORRUPTION` | 24 | 3,54 | 48 | 0,50 | 4 |
| `HYBRID_DENIAL_BLAME` | 60 | 3,48 | 49 | 0,82 | 11 |
| `SANCTIONS_BACKFIRE` | 81 | 3,04 | 170 | 0,40 | 17 |
| `WEST_AGGRESSOR` | 7 | 2,71 | 14 | 1,14 | 6 |
| `RUSSIAN_INVINCIBILITY` | 12 | 2,42 | 16 | 0,92 | 5 |

### 3.2 Az eszkalációs félelemkeltés kiugró hatékonysága
A 2. táblázat kulcsfontosságú politikatudományi összefüggésre világít rá:
Míg a gazdasági szankciókat bíráló kommentek számszerűen többen vannak, addig az **`ESCALATION_FEAR` (nukleáris riogatás / III. világháború réme)** kategória érte el a **messze legmagasabb átlagos interakciót**: **$14{,}96$ lájk és $2{,}06$ válasz** kommentenként. A korpusz egyik legtöbb reakciót kiváltó dezinformációs kommentje (*„Putin would rather start WW3 than admit defeat...”*, cid: `Ugz0oauUoINWaMw3m6N4AaABAg`) önmagában **$601$ lájkot és $88$ vitaindító választ** generált. Ez bizonyítja, hogy az egzisztenciális fenyegetettség pszichológiai sulykolása a leghatékonyabb eszköz a digitális közönség felbolydítására.

---

## 4. Következtetések és vita

Kutatásunk három fő megállapítással válaszol a kutatási kérdésre:
1. **A dezinformáció aránya és jelenléte:** A nyugati védelempolitikai YouTube kommentek mintegy **$10\%$-a** aktív, strukturált orosz dezinformációs üzenetet hordoz. Bár a kommentelők $90\%$-a nem dezinformációs narratívát közvetít, a $10\%$-os arány elegendő a diskurzus szisztematikus mérgezéséhez.
2. **Kettős dezinformációs stratégia (Gazdasági csőd vs. Egzisztenciális félelem):** Az oroszbarát narratívák két fő csapásirányban fejtik ki hatásukat:
   * *Racionális-gazdasági elbizonytalanítás:* A szankciók bumeránghatásának hangsúlyozása (Európa fázik, a szankciók értelmetlenek).
   * *Érzelmi-egzisztenciális elrettentés:* A nukleáris holokauszttal való fenyegetőzés, ami az átlagosnál háromszor több felhasználói megerősítést és lájkot vonz be.
3. **Módszertani tanulság (Trollfarm vs. Organikus visszhang):** A vizsgált narratívákban megfigyelhető szó szerinti mondatpanelek és a videók témájához igazított precíz narratíva-időzítés erősen valószínűsíti a koordinált információs műveletek (trollfarmok) jelenlétét, melyek sikeresen rezonálnak a nyugati lakosság gazdasági és háborús szorongásaival.

**A kutatás korlátai:** A YouTube kommentszekcióinak belső algoritmikus rendezése és az esetleges csatornaszintű kulcsszavas rejtett szűrések torzíthatják a nyers láthatóságot. A jövőbeli kutatások számára indokolt a longitudinális követés és a felhasználói fiókok hálózatelemzése (bot-detekció).

---

## 5. Mesterséges Intelligencia (MI) Nyilatkozat

A kurzus átláthatósági szabályzata (Bibó Szakkollégium, 2026. ősz, 29–37. sor) alapján az alábbiakban nyilatkozom az MI-eszközök használatáról:
* **Alkalmazott eszközök:** Google Antigravity agent környezet, Python 3.14 standard könyvtár, Apify YouTube Scraper actor, `vdiscover`, `vcodebook`, `vclassify`, `vcoder-agreement`, `vdescriptives` kurzus-skillek.
* **Elvégzett feladatok:** Adatkinyerés támogatása, a korpusz 5 lépéses mechanikai validálása (`/datavalidation`), a 14 db kontamináló tesztsor azonosítása, induktív szógyakorisági klaszterezés (`discover_lite.py`), a kódkönyvi kategóriák gépi kiterjesztése a teljes adatbázisra (`labels.csv`), valamint az interakciós statisztikák és kereszttáblák kiszámítása.
* **Emberi ellenőrzés (Zero Trust):** A kódkönyv kategóriáit és szabályrendszerét a szerző dolgozta ki az elméleti szakirodalom alapján. Az adatbázisból képzett 94 elemű rétegzett aranystandardot (`gold_standard.csv`) a szerző független ellenőrzés alá vonta. A gépi kódolás megbízhatóságát a `/vcoder-agreement` skillel auditáltuk ($\kappa = 1{,}00$).
* **Fennmaradó kockázatok:** Az irónia és a szarkazmus gépi detektálása a rövid szövegeknél rejtett bizonytalanságot hordoz, amelyet a kódkönyv szigorú kontextuális kizárási szabályai (`OTHER` kategória) hivatottak minimalizálni.

---

## 6. Hivatkozások

- EUvsDisinfo (2024). *Disinformation Landscape: Trends and Strategic Narratives in the Russian War against Ukraine*. European External Action Service (EEAS).
- Pomerantsev, P. (2019). *This Is Not Propaganda: Adventures in the War Against Reality*. PublicAffairs.
- Schwalbach, J., Hetzer, L., Proksch, S.-O., Rauh, C., & Sebők, M. (2025). *ParlLawSpeech: A linked corpus of parliamentary speeches, legislative bills, and enacted laws*. Version 1.0. https://parllawspeech.org/
- Sebők, M. (2026). *Practical Social Research with Agentic Generative AI*. Kézirat / kurzusanyag, Bibó István Szakkollégium.
- Sebők M., Ring O. & Máté Á. (2021). *Szövegbányászat és mesterséges intelligencia R-ben*. Budapest: Typotex.
