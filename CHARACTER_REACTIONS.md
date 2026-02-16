# Character Reactions

This document lists all characters that **Sanada Kojiroh** (by HAL) has special reactions to, as defined in `Kojiroh_01_N.cns`.

## HAL Roster Characters

These characters require both matching **Name** and **AuthorName = "HAL"** to trigger reactions:

| # | Character Name | Notes |
|---|----------------|-------|
| 1 | Genbu no Okina | |
| 2 | Inaba Tewi | |
| 3 | Shinnosuke Kagami | |
| 4 | Mukuro | |
| 5 | Moriya Minakata | |
| 6 | Kojiroh Sanada | Mirror match (self) |
| 7 | Juzo Kanzaki | |

**Reaction type:** Special `ScreenBound` handling during victory/defeat states (Statedef 170, 5151). These HAL characters use different screen boundary behavior compared to other opponents.

---

## Other Characters (by Name)

These characters are matched by **Name** only (no author check):

| Character Name | Alternate Names / Notes |
|----------------|-------------------------|
| **washizuka** | Washizuka (Kojiroh's rival from Gekka no Kenshi / The Last Blade) |
| **sanada_ani** | Sanada (older brother) — Ogaki-san's remake |
| **Mukuro** | Also checked by name alone for victory demo (State 185) |
| **Kojiroh Sanada** | Mirror match — accepts multiple name variants: `Kojiroh Sanada`, `Kojiroh_Sanada`, `Sanada Kojiroh`, `Sanada_Kojiroh`, `真田 小次郎` |

**Reaction types:**
- **washizuka** — Special victory demo (State 184) — Rouga・Rei style performance
- **sanada_ani** — Special victory demo (State 184) — Brother matchup
- **Mukuro** — Special victory demo (State 185)
- **Kojiroh Sanada** — Special Explod effect (anim 9185) when facing mirror match

---

## Summary Table

| Character | Author Filter | Reaction |
|-----------|---------------|----------|
| Genbu no Okina | HAL | ScreenBound |
| Inaba Tewi | HAL | ScreenBound |
| Shinnosuke Kagami | HAL | ScreenBound |
| Mukuro | HAL / Name | ScreenBound, Victory Demo |
| Moriya Minakata | HAL | ScreenBound |
| Kojiroh Sanada | HAL / Name | ScreenBound, Mirror Match Effect |
| Juzo Kanzaki | HAL | ScreenBound |
| washizuka | — | Victory Demo (Rival) |
| sanada_ani | — | Victory Demo (Brother) |

---

*Source: `Kojiroh_01_N.cns` — extracted from Enemy trigger conditions*
