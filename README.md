# kittystory-data

Public dataset for **Kitty Story** (Team AM): cat-care task templates with
intervals and typical cost ranges, served via GitHub Pages so shipped apps can
fetch updates without an App Store release.

- `data/kitty-tasks.json` — the dataset (schema 1). Systems: dental, grooming, parasite, vaccines, vet. Applicability
  by life stage: adult / kitten / senior.
- `data/manifest.json` — version + sha256, rebuilt by CI (`scripts/build-manifest.mjs`)
  on every data change.

## How updates reach users

The app ships this data **bundled** (v1). At runtime it reads
`data/manifest.json`; when the remote `version` is higher than the bundled one
and the `schema` is supported, it downloads `kitty-tasks.json` and verifies the
`sha256`. Edit the dataset → push → CI bumps the manifest → users fetch the
latest on next check. No app release required.

## Honesty contract

Intervals are **standard feline-care recommendations, not veterinary advice**. The app presents them as such. Your veterinarian and your cat's individual needs take precedence; corrections are welcome via issues.

## Consumers

- The Kitty Story iOS app (v1 ships this data bundled; over-the-air updates read
  `data/manifest.json`).

Sibling repo: [homestory-data](https://github.com/support-teamam/homestory-data).
