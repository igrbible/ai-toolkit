# Ruach Studio · branch ruach-studio/h3rt

This branch is [Ruach Studio](https://github.com/igrbible/Ruach_Studio)'s derivative of [ostris/ai-toolkit](https://github.com/ostris/ai-toolkit). It starts at upstream commit `b69b98314557` (27.10.2026), the commit Ruach Studio vendored MiniMax H3 from, and adds our changes as separate commits on top of it. In the Studio the Videographer runs MiniMax H3 on a runtime of its own, without AI-Toolkit installed (HERESY 1870); this branch shows every line of AI-Toolkit's code we changed to do that.

We hide nothing and are not ashamed of it: our work stands on Ostris' work, and here it is, line by line, for anyone to read, compare and take back.

## What it changes

- `extensions_built_in/diffusion_models/minimax_h3/src/pipeline.py` and `packing.py` (HERESY 1879, 1879b, 2361): a long shot sampled in pieces without a seam. The chunk before's last latent frames come in as context at their own times (`context_latents`, `context_offsets`), the picture can stand at its own time beside them (`ctrl_time`), the latents can come back undecoded (`decode=False`) so the whole shot is decoded once, and a last-frame keyframe can be pinned (`last_img`).
- `toolkit/util/ostris_quant.py` (HERESY 1870): the orbit, orbit_vq and uintx backends dropped from the quantizer lookup, since the Studio ships only the backends its files use (int8 ConvRot, nvfp4, float8).
- `extensions_built_in/diffusion_models/minimax_h3/ruach_h3rt/` (HERESY 1870): the runtime glue as it ships in the Studio (`runtime.py`, `files.py`, `util.py`, the cut-down loading mixin `mixin.py`, and `SOURCES.txt`, which maps each vendored file to its path here). Its imports point at the Studio's package `h3rt`, so it is here to be read beside upstream's code, not imported from this tree.

The HERESY numbers are entries of our patch log, `heresy/docs/HERESY.md` in the Ruach Studio repository.

## Licence

Upstream's code keeps its MIT licence and notice (Copyright (c) 2024 Ostris, LLC; `LICENSE` at the root). What we wrote, the changes in these commits and our own files under `ruach_h3rt/`, is licensed as Ruach Studio's release states for its own work: the GNU Affero General Public License, version 3 or any later version, with the additional terms of its section 7 (`LICENSE` and `LICENSE-ADDITIONAL-TERMS.md` in https://github.com/igrbible/Ruach_Studio).

Based on Ruach Studio by Viktor Zhuromskyy · https://github.com/igrbible/Ruach_Studio · GNU AGPL v3 or later
