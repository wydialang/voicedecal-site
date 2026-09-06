# Images

Sidebar logo, one per theme set:

- `voicedecallogo.png` — theme set 1 (default). Also the `logo:` in `_config.yml`.
- `sealion.png` — theme set 2 ("Blue & Pink").
- `voicedecallogo_withmiku.png` — theme set 3 ("Miku").

The swap is wired in each scheme file (`$logo-name` in
`_sass/color_schemes/light2.scss`, `light3.scss`, and their `dark*` twins) and
applied in `_sass/custom/custom.scss`.

Other:

- `larynxmodel.png` — the favicon (same for every theme; set in
  `_includes/head_custom.html`).
- `voicedecallogo_withsidetext.png` — home-page image (with the "the art and
  science of the human voice" text). Used in `index.md` with `{: .home-hero }`;
  `custom.scss` floats it next to the intro text.
- `staff-placeholder.svg` — stand-in headshot on `staff.md`.

To swap a logo: drop a PNG here with the same name (or change `$logo-name` /
`logo:` to point at the new file).
