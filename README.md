# Sanada Kojiroh Ver.1.09

> **Sanada Kojiroh** (真田小次郎) — M.U.G.E.N character from *The Last Blade 2* (幕末浪漫 月華の剣士 第二幕)

---

## Introduction

**Sanada Kojiroh** is a M.U.G.E.N character port based on the original character from **Bakumatsu Roman Dai Ni Maku - Gekka no Kenshi ~Tsuki ni Saku Hana, Chiri Yuku Hana~** (The Last Blade 2 - Samurai Spirits), a 2D fighting game by SNK.

### Character & Original Creator

| Field | Value |
|-------|-------|
| **Character Name** | Sanada Kojiroh (真田小次郎) |
| **M.U.G.E.N Author** | HAL |
| **Original Game** | The Last Blade 2 (月華の剣士 第二幕) |
| **Version** | 1.09 |
| **Website** | http://slowstep-mugen.versus.jp/index.html |

### Character Storyline

In the original game's lore, **Sanada Kojiroh** is the younger sister of **Sanada** (真田), a swordsman from the Bakumatsu period. She wields the **Mumeiken** (Darkness Sword) and fights with three sword styles: **Power** (力), **Technique** (技), and **Extreme** (極). Her rival is **Washizuka** (鷲塚), and her story intertwines with the supernatural elements of the series. HAL chose her as the fourth installment of his original character creation series, wanting to make a female character from the Gekka roster. Ogaki-san has also remade Kojiroh's older brother — both Kojirohs can be tried together.

---

## Documentation Index

| Document | Description |
|----------|-------------|
| [README.md](README.md) | This file — character overview and specifications |
| [docs/TRANSLATION.md](docs/TRANSLATION.md) | Japanese-to-English translation reference for CNS, CMD, DEF comments |
| [docs/log.md](docs/log.md) | Update history and creator feature journals |
| [CHARACTER_REACTIONS.md](CHARACTER_REACTIONS.md) | Opponent reactions, effects, counterparty triggers |
| `Command_Table.txt` | Full move list and command input reference |

---

## System Architecture

### Fight Mode File Structure

The character uses a modular CNS layout via the DEF file (`kojiroh_hal.def`):

| Slot | File | Role |
|------|------|------|
| `cns` | Kojiroh_01_N.cns | Main states — data, movement, match flow, victory/defeat |
| `st` | Kojiroh_01_N.cns | State controller (same as main) |
| `st0` | Kojiroh_02_S.cns | **Special moves** (Shikku-satsu, Koku-satsu, Shobi-sen, Mumeiken, Shunshin, Tenchi, Sange, Mozu Renzan) |
| `st1` | Kojiroh_03_H.cns | **Super / hidden / combo specials** (Mumeiken-Nie, Rouga-Rei, Kassatsu-Midare Setsugekka) |
| `st2` | Kojiroh_04_P.cns | **Helpers & projectiles** (Shikku-satsu projectiles, gauges, effects, Mumeiken-Nie helpers) |
| `st3` | Kojiroh_-2-3.cns | **Statedef -2/-3** — opponent compatibility patches, global effects |
| `st4` | Kojiroh_Config.cns | Config states (5900, 25000) |
| `stcommon` | Kojiroh_Common.cns | Shared states — stand, walk, jump, dash, hit, guard, get-up |

**State flow:** `Kojiroh_Common.cns` defines base states (0–155, 5000–5070). `Kojiroh_01_N.cns` handles match phases (170–195, 180–189, 5151). Special moves branch from common states via `ChangeState` triggered by commands in `Kojiroh.cmd`.

### Skills → States → Animations

| Skill | State(s) | Anim(s) | Notes |
|-------|----------|----------|-------|
| **Shikku-satsu A** (疾空殺) | 1000 | 1000, 51000 | Projectile helper 1050 |
| **Shikku-satsu B** (疾空殺) | 1010 | 1010, 51000, 51010 | Projectile helpers 1060, 1061 |
| **Koku-satsu A** (虚空殺) | 1100 | 1100, 51100 | |
| **Koku-satsu B** (虚空殺) | 1110 | 1110, 51110 | |
| **Shobi-sen** (翔飛閃) | 1200, 1202, 1205, 1206 | 15110, 15120, 15130 | Multi-phase |
| **Mumeiken** (無明剣) | 1210, 1220, 1230, 1231 | 1210, 1220, 1230, 1231, 15420 | 3-hit, super-cancelable |
| **Shunshin** (瞬身) | 1300 | 1300 | Movement, Tenchi cancel |
| **Tenchi** (天地) | — | — | During Shunshin |
| **Sange** (散華) | — | — | Technique/Extreme |
| **Mumeiken-Nie** (無明剣・贄) | 2000–2008 | 2000, 261, 1210, 5950 | Super cancel from Mumeiken |
| **Rouga-Rei** (狼牙・零) | 3000, 3050–3052, 3091–3099 | 130, 3002 | Guard-crush KO special |
| **Mozu Renzan** (百舌連斬) | 3500–3573, 3900–3905 | 15100–15130, 15420 | Combo special, timing routes |

### Animations & Counterparties

Animations that change based on opponent (see [CHARACTER_REACTIONS.md](CHARACTER_REACTIONS.md)):

| Anim | Context | Counterparty Trigger |
|------|---------|----------------------|
| **181–185, 189** | Victory poses | 181/182/183 = default; 184 = washizuka, sanada_ani; 185 = Mukuro |
| **9185** | Mirror match Explod | Kojiroh Sanada (any name variant) |
| **5950** | Mumeiken-Nie center performance | Single/Team vs Kojiroh Sanada (HAL) — StateTypeSet |
| **3002** | Rouga-Rei / Kassatsu-Midare | Opponent Kojiroh in 3002 → LifeSet trigger |

**Victory demo flow (State 180):** `MatchOver` + `Time=20` → branch by `Enemy,Name` to State 184 (washizuka/sanada_ani), 185 (Mukuro), 182 (Power), or 183 (Technique/Extreme).

### Opponent Compatibility (Kojiroh_-2-3.cns)

Statedef -2 contains compatibility patches so Kojiroh correctly receives damage/effects from opponent-specific mechanics. Supported opponents include Melty Blood/Tsukihime characters (Akiha, Len, Hisui, etc.), Touhou characters (Yuyuko, Reisen, Komachi, Suwako), and others. See [CHARACTER_REACTIONS.md](CHARACTER_REACTIONS.md) for the full list.

---

## Character Specifications

HAL aimed to reproduce the original as much as possible. Below are the differences between the original and MUGEN.

### Sword Style Selection

- Default sword styles: **1P/4P** = Power style, **2P/5P** = Technique style, **3P/6P** = Extreme style
- You can change to your preferred style during the intro using the left/right direction keys
- Extreme style is a hidden command: **Up 6× (Technique) → Down 3× (Power) → Up 4× (Technique)** = Extreme style (no further changes allowed)

### Command Input

In the original, command reception is reset once after Mumeiken (Darkness Sword) or Shunshin (Instant Dust), but in MUGEN there is no such reset. Therefore, it's easier to perform Mumeiken → Mumeiken・Nie (Sacrifice). Shunshin has a simulated command reset to reduce accidental activations.

### Rouga・Rei (Wolf Fang・Zero)

When K.O.'ing by guard crush, transitions to a special performance (similar to Act 1 Washizuka).

### Rensatsuzan ABC

A dedicated attack performed with Rensatsuzan A→B→C. Arranged as a mid attack. Fast startup, functions as a shake-up.

---

## Configuration

In `Kojiroh_Config.cns`, you can configure various settings. Open the file with a text editor and change items under **[Character-Related Settings]**.

**Changeable items:**
- Limit damage on/off
- Invincibility during auto-recovery state
- Forward jump guard setting
- Extreme style defense setting
- Extreme style gauge recovery rate
- Guard stun reduction
- Victory demo on/off
- Mumeiken・Nie performance setting
- Tenchi (Heaven and Earth) attack attribute

---

## A.I.

Default A.I. is not included.

- Oie-san created one: [MUGEN Nanka (Provisional)](http://mugezon.web.fc2.com/)

---

## Special Thanks

- **Ogaki-san** — Advice on creation, Gekka character descriptions and assets
- **Oie-san** — A.I. creation
- **GameApple-san** — Differences from original and bug reports

---

## License

### Creative Circle License

This character is an **edition from the original author** (HAL) and is released under the **Creative Circle License**.

This MUGEN character is a fan-made adaptation of Sanada Kojiroh from *The Last Blade 2* (月華の剣士 第二幕). All original character designs, names, and related intellectual property belong to **SNK Corporation**.

- **Free to use** in MUGEN and MUGEN-based projects
- **Attribution** — Credit the original creator (HAL) when sharing or modifying
- **Non-commercial** — For fan use only; do not use for commercial purposes without permission

---

**Creator:** HAL  
**Site:** http://slowstep-mugen.versus.jp/index.html
