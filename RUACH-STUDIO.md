# Ruach Studio · branch ruach-studio/yue2-trainer

This branch is [Ruach Studio](https://github.com/igrbible/Ruach_Studio)'s derivative of [ostris/ai-toolkit](https://github.com/ostris/ai-toolkit). It starts at upstream commit `ecee894ed2b1` (27.09.2026), the AI-Toolkit our YuE2 trainer was ported from and checked against (`extensions_built_in/audio_models/yue2/src` is the same at `ecee894`, `f7a1fb9` and `b69b983`), and adds our changes as separate commits on top of it. Ruach Studio trains YuE2 LoRAs with a trainer of its own that needs nothing of AI-Toolkit at run time (HERESY 1086); AI-Toolkit stays its reference, and `PARITY.md` records the numbers each stage was accepted on against it.

We hide nothing and are not ashamed of it: our trainer stands on Ostris' work, and here it is, line by line, for anyone to read, compare and take back.

## What it changes

- `extensions_built_in/audio_models/yue2/src/model.py` (HERESY 1083): the network as it is, without AI-Toolkit's mixin and without quantized layers (our loader hands it plain bf16 weights).
- `extensions_built_in/audio_models/yue2/src/vae.py` (HERESY 1086): unchanged but for the mixin.
- `extensions_built_in/audio_models/yue2/ruach_trainer/`: our own trainer as it ships in the Studio: `load.py` and `lora.py` (HERESY 1083), `cache.py` (HERESY 1086, 1422), `train.py` (HERESY 1083, 1422), `tracks.py` (HERESY 1626), `PARITY.md`, and `LICENSE-AITK` (AI-Toolkit's MIT licence beside the files ported from it). In the Studio `model.py` and `vae.py` sit beside these files and are imported as siblings, so this directory is here to be read beside upstream's code, not imported from this tree.

The HERESY numbers are entries of our patch log, `heresy/docs/HERESY.md` in the Ruach Studio repository; further numbers are in the files' own comments.

## Licence

Upstream's code keeps its MIT licence and notice (Copyright (c) 2024 Ostris, LLC; `LICENSE` at the root, and `LICENSE-AITK` beside the trainer). What we wrote, the changes in these commits and our own trainer files, is licensed as Ruach Studio's release states for its own work: the GNU Affero General Public License, version 3 or any later version, with the additional terms of its section 7 (`LICENSE` and `LICENSE-ADDITIONAL-TERMS.md` in https://github.com/igrbible/Ruach_Studio).

Based on Ruach Studio by Viktor Zhuromskyy · https://github.com/igrbible/Ruach_Studio · GNU AGPL v3 or later
