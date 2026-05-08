# Dota 2 Custom Game Starter Repository

Starter structure for a Dota 2 custom game repository using the standard `content/` and `game/` addon layout.

## This repository structure

```text
my-dota2-custom-game/
├─ content/
│  └─ dota_addons/
│     └─ dota2-extra-start-bonus/
│        └─ panorama/
│           ├─ layout/
│           ├─ scripts/
│           └─ styles/
├─ game/
│  └─ dota_addons/
│     └─ dota2-extra-start-bonus/
│        └─ scripts/
│           ├─ vscripts/
│           └─ custom_events.txt
├─ .gitignore
└─ README.md
```

Then you should copy `content` and `game` folders to:

```
C:/Program Files (x86)/Steam/steamapps/common/dota 2 beta/
├─ content/
│  └─ dota_addons/
│     └─ dota2-extra-start-bonus/
│        └─ etc
└─ game/
   └─ dota_addons/
      └─ dota2-extra-start-bonus/
         └─ etc
```

## Feature currently planned for this custom map

This repository is also intended to host a custom Dota 2 map feature with the following gameplay rule:

At the start of the match, the 5 participating heroes are randomly assigned one unique bonus package each, without repetition:

1. **12,000 gold + one Tier 1 neutral item**
2. **10,000 gold + one Tier 2 neutral item**
3. **8,000 gold + one Tier 3 neutral item**
4. **6,000 gold + one Tier 4 neutral item**
5. **4,000 gold + one Tier 5 neutral item**

### Design goals

- The bonus applies to **all 5 heroes**, including human players and standard bots.
- **Normal neutral progression remains enabled** during the match.
- Human players should be able to **choose one item from all neutral items available in the assigned tier**.
- Standard bots may either:
  - choose via a custom heuristic if implemented later, or
  - receive a random item from the assigned tier as a fallback.
- The initial bonus is a one-time advantage and does **not** disable future neutral progression by time.

### Example of intended progression behavior

- A hero that starts with a **Tier 2** neutral item still continues through the normal match progression.
- That hero only gains access to a higher normal tier when the game reaches the proper unlock time for the next tier.
- In other words, the bonus accelerates that hero's starting point, but does not replace the rest of the neutral progression system.

## Suggested next files to add

As the project grows, consider adding:

- `game/dota_addons/<addon_name>/scripts/vscripts/addon_game_mode.lua`
- `game/dota_addons/<addon_name>/scripts/vscripts/neutral_bonus.lua`
- `game/dota_addons/<addon_name>/scripts/custom_events.txt`
- `content/dota_addons/<addon_name>/panorama/layout/custom_game/neutral_choice.xml`
- `content/dota_addons/<addon_name>/panorama/scripts/custom_game/neutral_choice.js`
- `content/dota_addons/<addon_name>/panorama/styles/custom_game/neutral_choice.css`

## GitHub setup suggestion

A clean approach is to keep only the addon files in the repository, not the entire game installation.

You can clone the repository wherever you prefer and then sync or copy the addon folders into your Dota 2 Workshop Tools environment while developing.
