# Állami dezinformációs és hibrid hadviselési narratívák az európai védelempolitikai YouTube-diskurzusban

**Kutató:** Meczkó Balázs  
**Kurzus:** *Mesterséges intelligencia a társadalom- és politikatudományi kutatásban* (2026. ősz)  
**Intézmény:** Bibó István Szakkollégium  
**Kurzustartó:** Sebők Miklós (poltextLAB / CEU Democracy Institute)  

---

## ⚡ 1 perces gyorsteszt az opponensnek és az oktatónak

A kutatás minden számítása, adatvalidálása, kódolói megbízhatósági auditja ($\kappa = 1{,}000$) és táblázata egyetlen paranccsal, külső csomagfüggőségek nélkül reprodukálható bármely gépen:

```bash
python reproduce.py
```

A szkript ellenőrzi az adatbázis integritását ($N = 2\ 371$ egyedi `cid`), kiszámítja a 94 elemű aranystandard kódolói egyezését, majd kiírja a kutatás 1. és 2. leíró táblázatát.

---

## 📁 A repozitórium tartalma (Adat, Kód, Kódkönyv)

| Kategória | Fájl | Leírás |
| :--- | :--- | :--- |
| **Adat** | [`comments_clean.csv`](comments_clean.csv) | $N = 2\ 371$ megtisztított YouTube komment három nemzetközi védelempolitikai videó alól, 100% egyedi `cid` kulccsal és kettős szövegtárolással (`comment_clean`, `comment_raw`). |
| **Kódkönyv (Adat)** | [`DATA_CODEBOOK.pdf`](DATA_CODEBOOK.pdf)<br>[`DATA_CODEBOOK.md`](DATA_CODEBOOK.md) | A ParlLawSpeech sablon szerinti 2 oldalas adatkódkönyv (adatforrás: Apify, tisztítási napló, változók leírása, 5 lépéses validáció). |
| **Kódkönyv (Narratívák)**| [`coding_rules.md`](coding_rules.md) | A 6 orosz dezinformációs narratíva + `OTHER` és `UNREADABLE` kategóriák definíciói, beválogatási/kizárási szabályai és valós példái. |
| **Aranystandard** | [`gold_standard.csv`](gold_standard.csv)<br>[`gold_standard_review.md`](gold_standard_review.md) | Rétegzett referencia-minta ($N = 94$), kiegyensúlyozott kategóriánkénti eloszlással az emberi auditáláshoz. |
| **Gépi kódolás** | [`labels.csv`](labels.csv)<br>[`prompt.md`](prompt.md), [`models.md`](models.md) | Mind a 2 371 komment gépi kódolása, döntési indoklással és idézett mondattal. |
| **Kód (Reprodukció)** | [`reproduce.py`](reproduce.py) | Teljes reprodukciós pipeline standard Python 3 könyvtárral. |

*Megjegyzés: A 3 oldalas szakmai elemzés (`szakmai_elemzes_meczko_balazs.pdf`) és az önálló MI-használati nyilatkozat (`MI_nyilatkozat_meczko_balazs.pdf`) közvetlenül PDF formátumban került benyújtásra.*

---

## 🤖 Mesterséges Intelligencia (MI) Nyilatkozat - Összefoglaló

A kutatás során felhasznált MI-eszközök: Google Antigravity ágens, Python 3.14 standard könyvtár, Apify YouTube Scraper, valamint a kurzus skillek (`vdiscover`, `vcodebook`, `vclassify`, `vcoder-agreement`, `datavalidation`).  
A kódkönyvi narratívák elméleti operacionalizálását a szerző végezte. A 94 elemű aranystandardot a szerző független felülvizsgálat alá vonta. A gépi kódolás megbízhatóságát a `/vcoder-agreement` skillel auditáltuk ($\kappa = 1{,}000$).
