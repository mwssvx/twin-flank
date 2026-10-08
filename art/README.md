# Art

- `source/sprites/`: the painted art from the Unity project (`~/Merge towers/Assets/_Project/Resources/Art/Sprites`), copied 9 Oct 2026 without Unity `.meta` files. 512×512 transparent PNGs for heroes (`hero_NN_t1..t5`, `hero_NN_portrait`), enemies (`enemy_NN`, boss phases `_p2/_p3`), 38 effects, UI icons, frames, pads, castle states, one map plate (1080×1920).
- `source/audio/`: 7 placeholder sound effects and one music loop. To be replaced per ROADMAP Appendix C.
- `reference/style_ref.png`: the style reference every new image is generated against.
- `reference/battle-screen-concept.png`: the target look for the battle screen.

Source files are never edited by hand. The import script (ROADMAP 0.2) produces game-ready assets from them.
Hero, enemy, map and pet specs (names, roles, looks): `../docs/artspecs/`.
