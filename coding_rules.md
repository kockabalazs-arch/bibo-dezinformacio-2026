# Codebook — Russian Disinformation Narratives in EU/NATO Defense YouTube Comments · v1 · 2026. november 17.

Unit of observation: one YouTube comment (`cid`).  
Set-aside code: `OTHER` (no Russian disinformation narrative applies) · `UNREADABLE` (cannot be coded / gibberish).

---

## 1. Research Context & Purpose
This classification instrument measures the presence and distribution of characteristic state-sponsored disinformation and hybrid warfare narratives in the comment sections of prominent European defense and geopolitical YouTube videos. The coding scheme is designed to distinguish Russian information operations and weaponized anti-Western rhetoric from legitimate democratic debate, standard government critique, and neutral commentary.

---

## 2. Codes

### 1 WEST_AGGRESSOR (Nyugati agresszió és NATO-provokáció)
- **Definition:** The comment claims that NATO, the United States, or Western European powers are the true aggressors or warmongers responsible for the war in Ukraine or impending conflict with Russia, portraying Russia as acting purely in self-defense or reacting to Western encirclement.
- **Include when:** The text explicitly blames NATO expansion, Western "regime change" efforts, the 2014 Maidan events, or US geopolitical machinations for initiating or forcing the military conflict; or frames Western defense initiatives as offensive imperialism targeting Russia.
- **Example:** `"Ukraine started this war in 2014 by attacking and trying overwhelm Russian speaking people and Ukraine government were given 8 years to implement the Minsk Agreements but refused."` (cid: `UgzAtfjNJ-IOns7XAKh4AaABAg`)
- **Near miss:** `"NATO European allies need to increase defense spending to reach 2% of GDP."` — *Not WEST_AGGRESSOR because it discusses standard alliance defense capabilities without accusing NATO of causing the conflict.*

### 2 SANCTIONS_BACKFIRE (Szankciós bumeráng és európai gazdasági csőd)
- **Definition:** The comment asserts that Western economic sanctions against Russia have completely failed, only hurt and impoverish Europe/the West, and that Russia is thriving economically while Western leaders are desperate and hypocritical.
- **Include when:** The text highlights European economic decline, deindustrialization, inflation, or fuel shortages as direct self-inflicted wounds of anti-Russian sanctions; mocks Western trade restrictions; or points out sanction circumvention as proof of Western futility and hypocrisy (e.g., buying refined Russian diesel via third countries).
- **Example:** `"US is desperate on a diesel deal otherwise it will be 10 dollar per gallon by next month... so what? EU was and is buying russian oil too."` (cid: `UgxM9V-P3T_sample`)
- **Near miss:** `"Energy prices have increased across Germany over the past winter."` — *Not SANCTIONS_BACKFIRE because it states an empirical economic observation without asserting sanction failure or Russian economic victory.*

### 3 PROXY_CORRUPTION (Ukrajna mint illegitim bábállam és a támogatások elherdálása)
- **Definition:** The comment denies Ukrainian agency or state sovereignty, framing Ukraine as a corrupt Western proxy or puppet regime ("vassal") whose leadership artificially prolongs the bloodshed to siphon Western taxpayer funds.
- **Include when:** The text refers to Ukraine or its government as an illegitimate puppet of Washington/Brussels; attacks Ukrainian leadership as personal grifters/dictators; or claims financial and military aid is stolen, futile, or directly impoverishing Western citizens for a lost cause.
- **Example:** `"Is the money from Europe not prolonging the war? Foolish Zelensky"` (cid: `UgzAtfjNJ-IOns7XAKh4AaABAg`)
- **Near miss:** `"Transparency mechanisms must ensure all military equipment sent to frontline units is properly audited."` — *Not PROXY_CORRUPTION because constructive oversight demands do not deny the legitimacy of Ukraine's defense.*

### 4 RUSSIAN_INVINCIBILITY (Orosz katonai legyőzhetetlenség és geopolitikai diadal)
- **Definition:** The comment glorifies Russian military prowess, resilience, or strategic superiority, asserting that Russia cannot be defeated and that the collective West or Ukraine faces inevitable, crushing defeat.
- **Include when:** The text exalts Vladimir Putin or the Russian military as unstoppable geniuses ("playing 4D chess"); celebrates the BRICS / multipolar alignment as having already crushed Western hegemony; or taunts Western military inability to alter the battlefield outcome.
- **Example:** `"Putin The goat, can't stop, won't stop... US, CHN, Russia are squishing EU on the floor"` (cid: `UgxQ7_sample`)
- **Near miss:** `"Russia has significant artillery reserves and can sustain high attrition rates for years."` — *Not RUSSIAN_INVINCIBILITY because military analysis of material reserves is not ideological cheerleading of Russian invincibility.*

### 5 ESCALATION_FEAR (Nukleáris riogatás és a III. világháború réme)
- **Definition:** The comment uses the threat of direct global conflict, nuclear war, or the total annihilation of Europe to argue that the West must halt all military assistance to Ukraine and capitulate to Russian demands.
- **Include when:** The text explicitly evokes nuclear weapon deployment, World War III apocalypse, or apocalyptic retaliatory strikes specifically linked to Western weapons supplies, intelligence cooperation, or NATO defensive operations.
- **Example:** `"If NATO continues to send these long-range weapons to strike inside Russia, it will guarantee World War 3 and nuclear annihilation of Europe."`
- **Near miss:** `"Tensions between major nuclear powers require careful diplomatic management."` — *Not ESCALATION_FEAR because generic diplomatic realism does not weaponize nuclear threats to deter defensive aid.*

### 6 HYBRID_DENIAL_BLAME (Hibrid hadviselés tagadása és a szabotázsok áthárítása)
- **Definition:** The comment denies Russian responsibility for sub-threshold hybrid operations (pipeline sabotage, cyberattacks, undersea cable severing, GPS jamming, disinformation), dismissing them as Western fabrications ("false flags") or actively blaming Ukraine, the US, or European governments.
- **Include when:** The text dismisses Western intelligence warnings about Russian sabotage as paranoid propaganda designed to steal taxpayer money; or claims that incidents like the Nord Stream pipeline explosion were executed by Western/Ukrainian agencies while scapegoating Russia.
- **Example:** `"Germany's spy chief is just creating fake hysteria to justify defense budgets. Federal prosecutors in Germany have formally charged Ukrainians with sabotage of the Nordstream, not Russia."` (cid: `Ugz8mK_sample`)
- **Near miss:** `"We should wait for official technical investigations before drawing final conclusions about maritime infrastructure damage."` — *Not HYBRID_DENIAL_BLAME because exercising evidentiary caution is distinct from spreading state blame-shifting narratives.*

### 7 OTHER (Nem orosz dezinformációs narratíva — Set-Aside Code)
- **Definition:** The comment does not contain any of the six defined Russian state disinformation or hybrid warfare narratives.
- **Include when:** The text expresses support for Ukraine or NATO; criticizes Vladimir Putin, the Kremlin, or Russian aggression; engages in domestic political debate unrelated to Russian narratives; asks a technical question about the video; or represents off-topic banter, humor, or emojis.
- **Example:** `"Slava Ukraini! Democracy must defend itself against imperialist aggression."` / `"Great journalism from DW News as always."`

---

## 3. Decision Rules for Competing and Boundary Cases

1. **Hierarchy Rule (Primary Narrative Dominance):**
   - If a comment articulates multiple Russian disinformation narratives in a single sentence or paragraph, assign the **primary / dominant narrative** that carries the core rhetorical claim:
     - If nuclear/World War 3 annihilation is threatened, **`ESCALATION_FEAR`** takes precedence over other themes, as existential deterrence is the pinnacle of Russian coercive rhetoric.
     - If both sanction failure and Ukrainian corruption are mentioned, assign the code that forms the subject of the main clause.
2. **The "Disinformation Intent" Threshold:**
   - Sharp criticism of Western politicians (e.g. Olaf Scholz, Joe Biden, Donald Trump) is standard democratic discourse. A comment only qualifies for codes 1–6 if the criticism is explicitly anchored in Kremlin talking points (e.g., Western warmongering, sanction futility, proxy war tropes). Otherwise, code as **`OTHER`**.
3. **Sarcasm and Irony:**
   - Comments mocking Russian propaganda claims (e.g., *"Sure, Russia's 3-day special military operation is going totally according to plan..."*) express anti-Kremlin sentiment and MUST be coded as **`OTHER`**.
4. **Short / Ambiguous Texts:**
   - Single-word insults, emojis, or ambiguous phrases (e.g. *"Typical DW"*) without a clear narrative claim MUST be coded as **`OTHER`**.
   - If the text is completely incomprehensible, non-English, or broken characters, code as **`UNREADABLE`**.

---

## 4. Hard Cases and Calibration Benchmarks

| Candidate Comment | Ground Truth Code | Methodological Rationale |
| :--- | :---: | :--- |
| *"More like the US outplayed Europe on this oil ban while making record profits."* | `SANCTIONS_BACKFIRE` | Focuses squarely on the economic exploitation and backfire of sanctions against Europe. |
| *"If NATO triggers Article 5 and declares war as a result of these spy claims, Russia will turn Berlin to glass."* | `ESCALATION_FEAR` | Explicit nuclear/annihilation threat used to intimidate against collective defense enforcement. |
| *"Who blew up the Nord Stream pipelines? Definitely wasn't Russia."* | `HYBRID_DENIAL_BLAME` | Direct denial and deflection of hybrid sabotage away from the Kremlin. |
| *"Both sides are lying, war is always about money for the rich politicians."* | `OTHER` | Generic cynical pacifism; does not advance a specific Russian state narrative justifying the invasion. |
| *"Putin has completely isolated his country from the civilized world."* | `OTHER` | Anti-Kremlin critique directly opposing Russian narrative goals. |

---

## 5. Hand-Coding and Validation Plan (Gold Standard)

1. **Sample Selection:**
   - A score-stratified and topic-informed sample of **$N = 105$ comments** (approximately $15$ units per code across all 7 categories) will be drawn from the 30% hold-out set (`holdout_ids.csv`).
2. **Blind Human Annotation:**
   - The human researcher codes these 105 comments strictly applying the rules in this codebook into `gold_standard.csv` (containing `cid`, `gold_label`, `sentence_evidence`).
   - The human coding is conducted **blind** to any machine predictions.
3. **Reliability Metrics:**
   - Machine predictions (`vclassify`) will be evaluated against `gold_standard.csv` using the `/vcoder-agreement` skill, measuring:
     - Exact percentage agreement ($> 80\%$ target).
     - Cohen's Kappa ($\kappa > 0.70$ required for acceptable reliability).
     - Per-class Precision, Recall, and Confusion Matrix.
4. **Calibration:**
   - Any residual systematic machine over- or under-prediction will be adjusted using design-weighted Rogan-Gladen correction via `/vcalibrate`.
