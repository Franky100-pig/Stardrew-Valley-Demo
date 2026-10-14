# Stardrew-Valley-Demo

A tiny browser farming sim ("Rootlet Farm") inspired by *Stardew Valley*, built from
reverse-engineering the game's mechanics (see the `stardew_re` work). It is **original
code** — no game assets or decompiled source are included.

## What it models (grounded in the RE)

- **Calendar** — 4 seasons × 28 days (matches `WorldDate`: `GetDaysPlayed = (year-1)*4 + season)*28 + day-1`).
- **Seasonal visuals** — grass palette + mood tint shift per season; snow instead of rain in Winter.
- **Crops as data** — a small catalog (Parsnip, Potato, Blueberry, Tomato, Pumpkin, Wheat) with approximate
  factual grow-days, sell price, seed price, and which seasons they may be planted in.
- **Watering-gated growth** — a crop only advances a day if its tile was watered (or it rained), exactly like
  the `Crop.phaseDays` / `dayOfCurrentPhase` model.
- **Regrowable crops** — e.g. Tomato / Blueberry keep producing after harvest (`regrowDays`).
- **Withering** — crops not valid in the new season die at the season change (`Crop.dead`).
- **Seed economy** — buy seeds at the shipping bin, sell harvest there.
- **Bigger world + camera** — the farm is now 48×36 tiles (was 26×18) with a player-following
  camera viewport and a minimap (bottom-right) so you can explore without losing your way.
- **Forest & groves** — a deterministic tree border plus a couple of interior groves frame the
  farmland; trees are solid obstacles, the home/farm yard stays clear.

## Controls

| Key | Action |
|-----|--------|
| `WASD` / arrows | Move |
| `1` `2` `3` `4` | Hoe / Seeds / Water / Hand |
| `C` | Cycle selected seed |
| `Space` / Click | Use tool on facing tile |
| `E` | Sell harvest at bin / sleep at door |
| `B` | Buy 1 seed at bin |

## Run it

Open `index.html` in any browser. Till soil, plant a season-appropriate seed, water it every day,
sleep at the house door (`E`) to advance the day, and harvest when mature.

## Notes

- Pure client-side, single file, no build step.
- Mechanics are simplified for a demo; they mirror the *structure* observed in the decompiled `Crop` /
  `WorldDate` classes, not the game's exact numbers or code.
