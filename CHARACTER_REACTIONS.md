# Character Reactions

This document lists all characters that **Sanada Kojiroh** (by HAL) has special reactions to, extracted from the CNS files.

---

## 1. Kojiroh_01_N.cns — Intros, Victory Demos & Screen Behavior

### HAL Roster Characters

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

**Reaction type:** Special `ScreenBound` handling during victory/defeat states (Statedef 170, 5151).

### Other Characters (by Name)

| Character Name | Alternate Names / Notes |
|----------------|-------------------------|
| **washizuka** | Washizuka (Kojiroh's rival from Gekka no Kenshi / The Last Blade) |
| **sanada_ani** | Sanada (older brother) — Ogaki-san's remake |
| **Mukuro** | Also checked by name alone for victory demo (State 185) |
| **Kojiroh Sanada** | Mirror match — accepts: `Kojiroh Sanada`, `Kojiroh_Sanada`, `Sanada Kojiroh`, `Sanada_Kojiroh`, `真田 小次郎` |

**Reaction types:**
- **washizuka** — Special victory demo (State 184) — Rouga・Rei style performance
- **sanada_ani** — Special victory demo (State 184) — Brother matchup
- **Mukuro** — Special victory demo (State 185)
- **Kojiroh Sanada** — Special Explod effect (anim 9185) when facing mirror match

---

## 2. Kojiroh_03_H.cns — Super Move Compatibility

### Kojiroh Sanada (HAL) — Mirror Match

When facing **Kojiroh Sanada** by **HAL**:

- **Mumeiken-Nie (無明剣・贄):** Special `StateTypeSet` handling — opponent transitions to air/stand state at specific anim elements (State 2007)
- **Rouga-Rei / Kassatsu-Midare Setsugekka:** Special `LifeSet` trigger when opponent Kojiroh is in Anim 3002 with AnimElemTime(36) > 0 (States 3050, 3052)

---

## 3. Kojiroh_-2-3.cns — Opponent Mechanics Compatibility

Statedef -2 contains compatibility patches so Kojiroh correctly receives damage/effects from opponent-specific mechanics. When facing these characters, Kojiroh will be affected by their special systems.

### Melty Blood / Tsukihime

| Character | Author | Effect |
|-----------|--------|--------|
| **Akiha** | tukemon&HAL | Burn the Beast (Kuro Akiha) — Life/Power drain |
| **Akiha_Vermilion** | ⑨ | Plunder/Burn/Corner the Beast — Life/Power drain |
| **Len** | ⑨ | Powder Snow — Life drain |
| **Hisui** | ⑨ | Watering can, Ganbarimashita EX — Life/Power drain |
| **Warachia** | ⑨ | Black Crack — Life/Power drain |
| **Kohaku** | ⑨ | Victim of modern medicine — Life drain |

### Touhou Project

| Character | Author | Effect |
|-----------|--------|--------|
| **Yuyuko Saigyouji** | Souki | Spirit talisman, lifespan drain |
| **Reisen Udongein Inaba** | Shiroto | Poison smoke screen |
| **Reisen Udongein Inaba** | mikage_th / mikage_th105 | Gas Fabric Orb — poison damage |
| **Komachi Onoduka** | mikage_th / mikage_th105 | Datsukon no Gi — position/movement control |
| **Suwako Moriya** | mikage_th | Native god curse, Mishaguji-sama curse |

### Other

| Character | Author | Effect |
|-----------|--------|--------|
| **Misuzu Kamio** | 586 | Curse effect — Life drain, PalFX |
| **JUDA** | SAIKEI | Ichikoro poison — Life drain, PalFX |
| **Drowin arcana** | (AuthorName only) | Poison effect — Power/Life drain, PalFX |
| **AIHARA NATSUMI** | YU-TOHARU | Taunt — Power drain |
| **AL AZIF** | YU-TOHARU | Taunt — Power drain |
| **MAMIYA** | YU-TOHARU | Taunt — Power gain |

### Partner-Only (Team Mode)

| Character | Author | Effect |
|-----------|--------|--------|
| **Agrias_Oaks** | ouchi | Moogle blessing — PalFX, Life gain |

---

## Reaction Types & Possible Effects

### Reaction Types

| Type | Description | Where Used |
|------|-------------|------------|
| **ScreenBound** | Different screen boundary behavior during victory/defeat | HAL roster (Statedef 170, 5151) |
| **Victory Demo** | Special win pose/sequence | washizuka, sanada_ani, Mukuro |
| **Mirror Match Effect** | Extra visual effect when facing another Kojiroh | Kojiroh Sanada (Explod anim 9185) |
| **StateTypeSet** | Forces opponent into air/stand state at specific anim times | Kojiroh vs Kojiroh in Mumeiken-Nie |
| **LifeSet** | Instant KO when a specific condition is met | Rouga-Rei / Kassatsu-Midare vs Kojiroh |
| **Compatibility Patch** | Kojiroh receives damage/effects from opponent mechanics | Kojiroh_-2-3.cns (Statedef -2) |

### Possible Effects (CNS Controllers)

| Effect | CNS Type | Description |
|--------|----------|-------------|
| **Life drain/gain** | LifeAdd | Adds or subtracts life (negative = damage) |
| **Power drain/gain** | PowerAdd | Adds or subtracts power gauge |
| **Instant KO** | LifeSet | Sets life to fixed value (e.g. 0) |
| **Visual effect** | Explod | Extra visual effect (e.g. mirror match) |
| **Color/tint** | PalFX | Screen/character color change (poison, curse, blessing) |
| **Position change** | PosAdd / PosSet | Moves character or sets position |
| **State change** | ChangeState | Switches to another state (e.g. knockdown) |
| **Physics change** | StateTypeSet | Changes physics type (Stand/Air/Crouch) |
| **Special flag** | AssertSpecial | Sets flags like `NoAutoTurn` |

### Compatibility Patch Effects (Kojiroh_-2-3.cns)

When facing certain opponents, Kojiroh can receive:

- **Life drain** — Periodic or conditional damage (poison, curse, burn, etc.)
- **Power drain** — Power gauge loss
- **Power gain** — Power gauge gain (e.g. Mamiya taunt)
- **PalFX** — Screen/character color change (poison, curse, blessing)
- **Position control** — Forced movement (e.g. Komachi Datsukon no Gi)
- **State changes** — Forced knockdown or state change

### Summary by Source

| Source | Reaction Types | Main Effects |
|--------|----------------|--------------|
| `Kojiroh_01_N.cns` | ScreenBound, Victory Demo, Mirror Match Effect | Screen behavior, win demos, Explod |
| `Kojiroh_03_H.cns` | StateTypeSet, LifeSet | Mirror match super handling |
| `Kojiroh_-2-3.cns` | Compatibility Patch | LifeAdd, PowerAdd, PalFX, PosAdd, ChangeState |

---

## Summary Table (Kojiroh_01_N.cns — Core Reactions)

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

## Source Files

| File | Contents |
|------|----------|
| `Kojiroh_01_N.cns` | Intros, victory demos, ScreenBound, mirror match effects |
| `Kojiroh_03_H.cns` | Mumeiken-Nie, Rouga-Rei mirror match handling |
| `Kojiroh_-2-3.cns` | Opponent mechanics compatibility (damage/effects from enemy systems) |
| `Kojiroh_02_S.cns` | No character-specific reactions |
| `Kojiroh_04_P.cns` | No character-specific reactions |

---

## Related Documentation

| Document | Description |
|----------|-------------|
| [README.md](README.md) | Character overview |
| [docs/TRANSLATION.md](docs/TRANSLATION.md) | Japanese-to-English translation reference |
| [docs/log.md](docs/log.md) | Update history |
