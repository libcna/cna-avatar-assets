# CNA avatar assets

The avatar catalog of [CNA](https://github.com/libcna/cna): the bodies, wardrobe items and
accessories, textures, face-feature atlas and the 31 animations behind CNA's XNA 4.0 avatar API
(`AvatarDescription`, `AvatarAnimation`, `AvatarRenderer` and the Guide's avatar editor).

CNA checks this repository out as the Git submodule `modules/gamer-services/assets/avatars` and
compiles the catalogs into its gamer-services library, so avatars draw offline. Everything else --
the runtime, the catalog reader, the tests and the generator -- lives in CNA.

## Contents

`v3/` is avatar catalog version 3, **revision 5** (`catalog.json`: `"catalogVersion": 3`,
`"revision": 5`, `"reader": 2`): 359 files, 45,960,930 bytes. `catalog.json` lists every other file
with its size and SHA-256. A catalog directory holds only generator output: CNA embeds every file in
it, and CNA's `generate_avatar_catalog.py --check` refuses any file it did not write.

## Provenance and licence

All of it is original CNA work, generated deterministically by CNA's
`tools/avatar_builder/generate_avatar_catalog.py`; nothing is downloaded, third-party or Xbox
content. It is licensed under the Microsoft Public License (Ms-PL), CNA's own licence (`LICENSE`).

The files were moved here unchanged from CNA commit `bdaeaff01`; their earlier history, including
the unsupported development catalogs v1 and v2, is CNA's Git history of
`modules/gamer-services/assets/avatars/`.

## Changing the catalog

Never edit these files by hand; change the generator in CNA and regenerate:

1. In a CNA checkout, change `tools/avatar_builder/`, run `generate_avatar_catalog.py` (it writes
   into this submodule) and validate it (CNA's `tools/avatar_builder/README.md`).
2. Commit the regenerated catalog here and push it.
3. In CNA, stage the new submodule commit (`git add modules/gamer-services/assets/avatars`).
4. Run CNA's acceptance (`tools/avatar_builder/avatar_acceptance.py`).
5. Commit the pointer in CNA with the generator change that produced it.

Push this repository before the CNA commit that points into it: a CNA commit naming an unpublished
asset commit cannot be cloned.
