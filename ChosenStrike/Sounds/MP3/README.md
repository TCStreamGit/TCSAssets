# ChosenStrike Sound Assets
## Path Rules
- Never use `/home/nike/Streaming/Github` or `Z:\home\nike\Streaming\Github` (backup only).
- Use runtime paths under `/home/nike/Streaming` or `Z:\home\nike\Streaming`.
- See `MAP.md` at the repo root for the full runtime mapping and missing file checklist.


This folder contains MP3 sound effects used by the case-opening overlay. The default file names are referenced by `lumia-overlays/case-opening/configs.json`.


## Sync Rules
- After updating repo files that are mapped to runtime, run `python tools\sync_using_map.py --apply`.
- Use `python tools\sync_using_map.py` for a dry-run preview.
- Never sync to or from `.../Streaming/Github/...`; Github is backup only.

## Required files

| File | Used by config key | Purpose | Recommended length |
| --- | --- | --- | --- |
| `tick.mp3` | `sfxTick` | Tick sound as items pass the marker | ~50-100ms |
| `reveal.mp3` | `sfxReveal` | Normal item reveal | ~1-2s |
| `rare.mp3` | `sfxRare` | Pink/red rarity reveal | ~2-3s |
| `gold-reveal.mp3` | `sfxGold` | Gold rarity reveal | ~3-5s |

Other sounds are referenced outside this folder:
- `Assets/Sounds/ChosenStrike_Sound_Assets/menu_accept.mp3` (`sfxAccept`)
- `Assets/Sounds/MP3/csgo_ui_crate_open.mp3` (`sfxOpen`)

## File format guidance

- Format: MP3
- Sample rate: 44.1 kHz
- Bitrate: 128-192 kbps
- Channels: Stereo or Mono

## Usage notes

- Tick sounds fire rapidly and should be short with minimal tail.
- Volume is controlled by `sfxVolume` and `sfxTickVolume` in `configs.json`.
- If you change file names, update the config paths to match.
- Keep file sizes small for fast overlay loading.

## Quick verification

To verify the overlay can load sounds:
1. Open the overlay and run an `!open` command.
2. Confirm tick sounds during spin and reveal sounds at the end.
3. If no sound plays, check that the file paths in `configs.json` are valid relative to the repo root.
