# YL Vault — Custom Icon Packs

A curated collection of SVG icon **packs** for [YL Vault](https://github.com/sawyelin1011/ylvault-webapp). Each pack is a themed folder you import straight from the app's collection picker.

> **One leaf folder = one importable pack.** Every pack has its own `manifest.json` for friendly names + search keywords.

---

## Structure Tree

```
ylvault-icons/
├── README.md
└── icons/                     # parent category folders (each = a separate pack)
    ├── folders/               #  → pack "Folders"
    │   ├── manifest.json
    │   └── folder.svg
    ├── favorites/             #  → pack "Favorites"
    │   ├── manifest.json
    │   └── star.svg
    └── goals/                 #  → pack "Goals"
        ├── manifest.json
        └── target.svg
```

## How to import a pack in the app

1. Create a collection, or right-click an existing one → **Color / Icon**.
2. Click **Import from GitHub**.
3. Fill in:
   - **Repo URL** — `https://github.com/sawyelin1011/ylvault-icons`
   - **Path (folder)** — the pack you want, e.g. `icons/goals`
   - **Branch** — `main`
   - **Pack name** — anything, e.g. `Goals`
4. **Fetch icons** → cached locally, then pick from the "Custom icons / packs" section (shares the built-in search box).

Import a pack once per collection modal as needed — each category folder is independent.

---

## Adding a new category pack

1. Create a folder: `icons/<new-category>/`.
2. Drop your `.svg` files into it.
3. (Optional) Add a `manifest.json` for a nicer label + search keywords.

```
icons/
└── rockets/
    ├── manifest.json
    ├── rocket.svg
    └── shuttle.svg
```

`manifest.json`:

```json
{
  "name": "Rockets",
  "description": "Launch and space icons.",
  "icons": {
    "rocket":  { "name": "Rocket",  "keywords": ["launch", "ship", "startup"] },
    "shuttle": { "name": "Shuttle", "keywords": ["space", "orbit"] }
  }
}
```

Keys must match SVG filenames without `.svg`. Everything is optional — icons work with no manifest.

---

## Adding an icon to an existing pack

Just drop a `.svg` into that pack's folder and optionally add a `manifest.json` entry. Then **re-import** the pack in the app to refresh it.

---

## Icon authoring rules (important)

Prefer SVGs that use `currentColor` so they tint to the collection's color:

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
     fill="none" stroke="currentColor"
     stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <path d="..."/>
</svg>
```

- `stroke="currentColor"` / `fill="currentColor"` → tints to the collection color.
- Explicit hex colors (`fill="#000"`) are rewritten to `currentColor` on import, so they tint too.
- Multi-color logos render as a single tint (expected for folder icons).

### Stripped on import (for security) — do NOT include
- `<script>`, any `on*` attribute
- `href="javascript:..."` or `data:` URLs
- `<foreignObject>`, external `<use href="...">`, `<style>` blocks, CDATA

---

## License

Keep attribution / license files from the original icon set. Example SVGs here are simple common shapes for illustration.