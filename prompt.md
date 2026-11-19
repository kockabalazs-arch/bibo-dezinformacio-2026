# Classification Prompt — Russian Disinformation Narratives · v1.0
**Date:** 2026. november 17.  
**Instrument:** `coding_rules.md` (v1)

## Instructions
Classify the given YouTube comment into exactly ONE of the following mutually exclusive categories defined in the codebook:
1. `WEST_AGGRESSOR`: Blaming NATO expansion, the US or Ukraine for starting or provoking the war.
2. `SANCTIONS_BACKFIRE`: Asserting that Western economic sanctions failed and only destroy Europe while Russia thrives.
3. `PROXY_CORRUPTION`: Depicting Ukraine as an illegitimate Western vassal or corrupt regime siphoning funds.
4. `RUSSIAN_INVINCIBILITY`: Asserting Russian military or geopolitical invincibility and inevitable Western defeat.
5. `ESCALATION_FEAR`: Evoking nuclear war, WW3 apocalypse or direct retaliation to deter Western defense aid.
6. `HYBRID_DENIAL_BLAME`: Denying Russian hybrid sabotage, dismissing warnings as hysteria, or blaming the West/Ukraine.
7. `OTHER`: Any comment that does not express one of the six defined Russian state disinformation narratives.
8. `UNREADABLE`: Empty, non-English gibberish or pure symbols.

## Response Format
For each unit, produce:
- `code`: The exact category name.
- `reason`: A concise explanation of at most 20 words referencing the codebook rule.
- `sentence`: One verbatim sentence copied directly from the comment text that justifies the code.
