# Mesterséges Intelligencia (MI) Használati Nyilatkozat
## Kutatási jelentés és záródolgozat melléklet

**Szerző:** Meczkó Balázs  
**Intézmény:** Bibó István Szakkollégium  
**Kurzus:** *Mesterséges intelligencia a társadalom- és politikatudományi kutatásban* (2026. ősz)  
**Kurzustartó:** Sebők Miklós (poltextLAB / CEU Democracy Institute)  
**Dátum:** 2026. november 19.  
**Kutatási téma:** *Állami dezinformációs és hibrid hadviselési narratívák az európai védelempolitikai YouTube-diskurzusban*  
**Kapcsolódó elemzés:** `szakmai_elemzes_meczko_balazs.pdf`  
**Adatbázis és kódkészlet:** `comments_clean.csv` ($N = 2\ 371$), `labels.csv`, `gold_standard.csv`  
**GitHub repozitórium:** `https://github.com/kockabalazs-arch/bibo-dezinformacio-2026`  

---

A kurzus átláthatósági és etikai szabályzatának megfelelően az alábbiakban részletesen és tételesen nyilatkozom a kutatás során alkalmazott mesterséges intelligencia (MI) eszközökről, azok szerepéről, az emberi felülvizsgálat mértékéről és a felismert korlátokról.

### 1. Alkalmazott MI-eszközök és szoftverkörnyezet
* **Ágens és nyelvi modellek:** Google Antigravity autonóm kódoló ágens környezet (DeepMind), Python 3.14 futtatókörnyezet.
* **Adatgyűjtő modul:** Apify YouTube Comment Scraper felhőalapú actor.
* **Kurzus-specifikus módszertani skillek:** A kurzus során átadott és auditált skillek:
  * `/datavalidation` (ParlLawSpeech 5 lépéses adatvalidálási protokoll),
  * `/vdiscover` (induktív szógyakorisági témamodellezés és klaszterkeresés),
  * `/vcodebook` (narratíva-operacionalizálás és formai szabályrendszer),
  * `/vclassify` (szabályalapú és kontextusfüggő gépi klasszifikáció),
  * `/vcoder-agreement` (kódolói megbízhatósági audit, Cohen-féle kappa számítás).

### 2. Az MI által támogatott munkafolyamatok
* **Adatbázis-tisztítás és hibaszűrés:** A nyers YouTube-adatbázis ($N = 2\ 385$) mechanikai ellenőrzése; az Apify beágyazott demó tesztvideójából származó 14 db kontamináló adatsor azonosítása és eltávolítása (`comments_clean.csv`, $N = 2\ 371$).
* **Feltáró témaklaszterezés:** A 70%-os feltáró részminta szókincs-eloszlásának és kulcsszavainak kigyűjtése (`discover_lite.py`), ami támpontot nyújtott az empirikus témák körvonalazásához.
* **Gépi kódolás skálázása:** A szerző által definiált kódkönyvi szabályok végrehajtása a teljes korpuszon ($N = 2\ 371$), minden kommenthez egyértelmű indoklást és a döntést megalapozó mondatidézetet társítva (`labels.csv`).
* **Leíró statisztikai táblázatok kiszámítása:** A kereszttáblák (Videó $\times$ Narratíva) és a felhasználói interakciós mutatók (átlagos és maximális lájkok, válaszok) mechanikai aggregálása.

### 3. Emberi szerzői ellenőrzés (Zero Trust elv)
* **Elméleti keret és kódkönyv megalkotása:** A 6 dezinformációs narratívát és a beválogatási/kizárási szabályokat a szerző dolgozta ki az orosz hibrid hadviselés szakirodalma (EUvsDisinfo, Pomerantsev) alapján.
* **Független emberi aranystandard:** A 30%-os tartalékmintából képzett, rétegzett $N = 94$ elemű ellenőrző mintát (`gold_standard.csv`) a szerző függetlenül átvizsgálta és validálta.
* **Kódolói megbízhatóság igazolása:** A gépi kódolás pontosságát a `/vcoder-agreement` skillel auditáltuk az emberi aranystandardhoz viszonyítva. Az egyezési arány 100%-os ($94/94$), a Cohen-féle kappa mutató $\kappa = 1{,}000$ lett, ami a kódkönyv diszkriminációs élességét igazolja.
* **Kvalitatív értelmezés és szövegezés:** Az eredmények szintézisét, a politikatudományi következtetéseket, a táblázatok értelmezését és a zárótanulmány szövegét a szerző fogalmazta meg.

### 4. Fennmaradó korlátok és etikai megfontolások
* **Nyelvi árnyalatok:** A rövid online kommentekben rejlő irónia és szarkazmus gépi detektálása kockázatot hordoz; e bizonytalanságot a kódkönyv szigorú, konzervatív kizárási szabályai (`OTHER` kategória preferálása kétség esetén) minimalizálták.
* **Platform-torzítás:** A YouTube kommentszekcióinak belső algoritmikus sorrendje és a csatornatulajdonosok moderációs beállításai befolyásolhatják a láthatóságot, amit a kutatás korlátként kezel.

---

**Nyilatkozat:**  
Alulírott Meczkó Balázs kijelentem, hogy a benyújtott szakmai elemzésben a mesterséges intelligencia eszközöket kizárólag kutatás-asszisztensi és számítási funkciókra használtam a fenti leírás szerint. A kutatás szellemi irányítása, az elméleti hipotézisek, az aranystandard validálása és a levont következtetések a saját, önálló szellemi termékemet képezik.

Budapest, 2026. november 19.

\
__________________________________  
**Meczkó Balázs**  
hallgató, Bibó István Szakkollégium
