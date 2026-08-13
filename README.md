# Custom Icon Pack — Template

A ready-to-use icon pack for **[YL Vault](https://github.com/sawyelin1011/ylvault-webapp)**. Upload this whole folder to a GitHub repository, then import it straight from the app's collection create/edit picker.

> One **folder** = one pack. Each **`.svg` file** = one icon. `manifest.json` is optional and only adds friendly names + search keywords.

---

## Structure Tree

```
icon-pack-template/
├── manifest.json          # optional: pack name/description + per-icon labels & keywords
└── icons/                 # the "path (folder)" you enter in the app's import form
    ├── folder.svg         # each .svg becomes one pickable icon
    ├── star.svg
    └── target.svg
```

## How to import it in the app

1. Create a new collection, or right-click an existing one → **Color / Icon**.
2. Click **Import from GitHub**.
3. Fill in:
   - **Repo URL** — e.g. `https://github.com/you/my-icons`
   - **Path (folder)** — `icons` (or leave the specific subfolder, e.g. `icons/social`)
   - **Branch** — `main`
   - **Pack name** — what to call it, e.g. `My Icons`
4. **Fetch icons** → the pack is cached locally, then choose any icon from the "Custom icons / packs" section (uses the same search box as the built-in ones).

The collection saves a reference (`iconCustom`) and renders the icon tinted to its color. It works offline after the first import.

---

## Adding / extending icons

To add a new icon, just drop an `.svg` file into the `icons/` folder — no manifest changes required.

```
icons/
└── rocket.svg      ← new icon, name auto-becomes "Rocket"
```

If you want a friendlier label or search keywords, also add it to `manifest.json`:

```json
{
  "icons": {
    "rocket": {
      "name": "Rocket",
      "keywords": ["launch", "project", "ship", "startup"]
    }
  }
}
```

---

## Icon authoring rules (important)

To render **correctly tinted** with a collection's color, prefer SVGs that use `currentColor`:

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
     fill="none" stroke="currentColor"
     stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <path d="..."/>
</svg>
```

- `stroke="currentColor"` / `fill="currentColor"` → tints to the collection color.
- Explicit hex colors (e.g. `fill="#000"`) are rewritten to `currentColor` on import, so they tint too.
- Multi-color brand logos will render as a **single tint** — that's expected for folder icons.

### Do NOT include (stripped on import for security)
- `<script>`, `onclick`/`onerror`/any `on*` attributes
- `href="javascript:..."` or `data:` URLs
- `<foreignObject>`, external `<use href="...">`, `<style>` blocks, CDATA

---

## `manifest.json` reference

```json
{
  "name": "Pack name shown in the picker",
  "description": "Optional, shown as context",
  "icons": {
    "<file-without-.svg>": {
      "name": "Display name",
      "keywords": ["search", "terms", "here"]
    }
  }
}
```

- Keys must match SVG filenames **without** the `.svg` extension.
- `name` — shown in the picker tooltip.
- `keywords` — extra search words (searched alongside `name` and filename).
- Everything is optional; icons work even with no manifest.

---

## License

Keep attribution / license files that came with the original icon set. This template's example SVGs are derived from common open-source icon shapes (see your set's license terms).