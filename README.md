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

## Disclaimer

This dataset is provided for **general informational purposes only**. The
intervals, schedules, and cost figures are **typical-case estimates** — many are
derived from generic, rule-based heuristics rather than manufacturer or expert
data, and some descriptions are produced with the help of automated (AI) tools.

It is **not** professional, medical, veterinary, or manufacturer advice. Always
verify against your veterinarian (this is not veterinary advice) before acting. The data is provided "as is", without
warranty of any kind, and you use it at your own risk. Team AM is not affiliated
with any manufacturer or brand referenced.

Full terms: https://teamam.org/terms
