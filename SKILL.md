---
name: sevnjs-frontend-design-skill
description: Use when building frontend UIs with SevnJS (gen, append, grab, loadscss, cssvar, load, getfile, parsemd, log). Trigger when a user asks to create web interfaces using SevnJS utilities without a build step, or references sevnjs.mgeek.in.
version: 1.0.0
author: Prateek Raj Gautam / prateekrajgautam
license: MIT
tags: [frontend, dom-manipulation, vanilla-js, sevnjs, no-build]
---

# SevnJS Frontend Design Skill

## When to Use
Load this skill when the user wants to build a web UI using **SevnJS** — a lightweight, utility-driven vanilla JS library. Triggers include:
- Requests mentioning `gen`, `append`, `grab`, `loadscss`, `cssvar`, `load`, `getfile`, `parsemd`, or `log`.
- Requests for "no build step" frontends or dynamic DOM manipulation without React/Vue.
- References to `sevnjs.mgeek.in` or `sevnjs.github.io`.

## Basic Setup
The entry `index.html` must include:
```html
<script src="https://sevnjs.github.io/cdn/latest/sevn.min.js"></script>
```
After load, SevnJS auto-imports `./script.js` from the current directory — all app logic goes there.

## Core Paradigm
- **Imperative & Direct**: create, grab, modify elements directly (no virtual DOM).
- **Global API**: functions live on `self` (`window`).
- **No Build Step**: plain HTML/JS runnable in any browser.

## Quick Reference
| Goal | Function | Example |
| :--- | :--- | :--- |
| Create element | `gen('div', 'id', 'Hello', 'cls')` | `gen('input', 'user', 'John', 'field')` |
| Get element | `grab('#id')` | `grab('.items')[0]` |
| Insert | `append('#parent', child, 'after')` | `append('#list', [a, b], 'over')` |
| Set CSS Var | `cssvar('color', 'red')` | `cssvar('--main', 'blue')` |
| Load assets | `load('app.js')` | `load(['a.css', 'b.js'], 'body')` |
| Fetch file | `getfile(url, cb)` | `getfile('data.json', r => log(r))` |
| Parse Markdown | `parsemd(md, cb)` | `parsemd('# Hi', h => append('body', h))` |
| Log to UI | `log('Message')` | `log('clear')` |

## Essential Patterns

### Component Factory
```javascript
function createButton(label, onClick) {
    return gen('button', null, label, 'btn-primary', null, { click: onClick });
}
append('body', createButton('Submit', () => log('Submitted!')));
```

### Batch Injection
```javascript
const navItems = ['Home', 'About', 'Contact'].map(t => gen('li', null, t));
append('#nav', navItems, 'over');
```

## Critical Constraints
- **No Virtual DOM**: `'over'` and `'replace'` positions destroy existing event listeners.
- **Global namespace**: avoid collisions with `self` functions.
- **SCSS**: `loadscss` is a *lite* parser — stick to nesting and variables, no mixins/functions.
- **`parsemd` is slow**: split large markdown into chunks to avoid freezing.

## Full Reference
See [reference.md](./reference.md) for the 7-step API curriculum, and [examples.md](./examples.md) for extended patterns (theming, SCSS injection, markdown rendering).
```


