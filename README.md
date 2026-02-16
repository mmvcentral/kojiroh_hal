# Sanada Kojiroh Ver.1.09

Hello everyone, this is HAL from 幕末浪漫 月華の剣士 2

Sorry for the delay, but this is the fourth installment of my original character creation.
From **Bakumatsu Roman Dai Ni Maku - Gekka no Kenshi ~Tsuki ni Saku Hana, Chiri Yuku Hana~** (The Last Blade 2 - Samurai Spirits), I present Sanada Kojiroh!

I wanted to make a female character... and so I decided on this younger sister.
The other candidate was Yukihime (Snow Princess), but... well, you know how that goes (when I felt like it...
...hey, the Zantetsu remake is still left to do, right?
Then Yukihime was made by Ogaki-san... w

There were more troublesome processes than expected, but I think I managed to get it close to the original specifications.
Ogaki-san has also remade Kojiroh's older brother, so please try out both Kojirohs!

## Documentation Index

| Document | Description |
|----------|-------------|
| [README.md](README.md) | This file — character overview and specifications |
| [CHARACTER_REACTIONS.md](CHARACTER_REACTIONS.md) | List of opponents with special intros, victory demos, and effects |
| [TRANSLATION_TABLE.md](TRANSLATION_TABLE.md) | Japanese-to-English translation reference for CNS comments |
| `Command_Table.txt` | Full move list and command input reference |

## Character Specifications

I've aimed to reproduce the original as much as possible, but due to various circumstances, there are some parts that cannot be (or have not been) reproduced.
Below, I've listed the differences between the original and MUGEN.

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

## A.I.

Default A.I. is not included.

- Oie-san created one: [MUGEN Nanka (Provisional)](http://mugezon.web.fc2.com/)

## Update History

| Date | Version |
|------|---------|
| 2015/04/05 | Ver1.00 Complete |
| 2015/05/03 | Various fixes for differences from original |
| 2015/05/08 | Various fixes for differences from original |
| 2015/12/05 | Minor bug fixes |
| 2016/08/18 | Minor bug fixes |
| 2016/10/02 | Minor bug fixes |
| 2016/12/30 | Minor bug fixes |
| 2017/08/06 | Minor bug fixes |
| 2024/05/04 | Fixes for differences from original, minor bug fixes |
| 2024/08/09 | Fixes for differences from original, minor bug fixes |

See `Command_Table.txt` for the full move list, or the [Documentation Index](#documentation-index) above for all related files.

## Special Thanks

- **Ogaki-san** — Advice on creation, Gekka character descriptions and assets
- **Oie-san** — A.I. creation
- **GameApple-san** — Differences from original and bug reports

---

**Creator:** HAL  
**Site:** http://slowstep-mugen.versus.jp/index.html
