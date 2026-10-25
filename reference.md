# SevnJS API Reference (7-Step Curriculum)

> Author: Prateek Raj Gautam / prateekrajgautam  
> Source: https://sevnjs.mgeek.in

## Step 1: Element Generation — `gen`, `gens`, `genp`
**Signature**: `gen(elementtype, idin, htmlin, classin, src, event)`
- `htmlin`: string | HTMLElement | Array (mixed content supported).
- `src`: string (for `img`/`a`) or object (attributes).
- `event`: object of listeners, e.g. `{ click: () => ... }`.
- `gens(...)` → returns HTML string.
- `genp(...)` → returns escaped HTML string (for code display).

## Step 2: DOM Manipulation — `append`, `grab`
- `grab(selector)` → NodeList or element. Supports `grab('li[0]')`.
- `append(parentid, childhtml, position)`:
  - `position`: `'before'` | `'after'` (default) | `'over'` (replace inner) | `'replace'` (replace outer) | `'parent'` (wrap).
  - `childhtml` accepts arrays.

## Step 3: Asset Loading — `load`, `loadscss`
- `load(srcList, pos)` — auto-detects `.js`, `.css`, `.scss`; can load metadata objects (Open Graph).
- `loadscss(scssContent, styleid)` — custom SCSS-lite parser (nesting + variables only). `styleid` replaces existing `<style>` with same id.

## Step 4: File Fetching — `getfile`
- `getfile(URL, callback)` — fetches URL, passes content to callback. Useful for remote JSON/MD/CSS.

## Step 5: CSS Variables — `cssvar`
- `cssvar(name, value)` — get or set on `:root`. Auto-prefixes `--`.

## Step 6: Markdown — `parsemd`
- `parsemd(markdownText, callback)` — converts MD → HTML, passes to callback. **Slow for large inputs** — chunk it.

## Step 7: Visual Logging — `log`
- `log(data, pos)` — renders into persistent `#applog` container.
- `log('clear')` — clear/hide.
- Prefer over `console.log` for user-visible feedback.

## Error Handling
All core functions wrap logic in `try/catch` and log to console. Agents should still wrap user input in their own `try/catch`.