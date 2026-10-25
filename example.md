# SevnJS Extended Examples

Author:  Prateek Raj Gautam / prateekrajgautam

## Pattern C: Dynamic Theming
```javascript
function toggleTheme() {
    const current = cssvar('bg-color') || 'white';
    cssvar('bg-color', current === 'white' ? 'black' : 'white');
    append('body', gen('style', null, 'body { background: var(--bg-color); }'), 'before');
}
```

## Pattern D: Scoped SCSS Injection
```javascript
const scss = `
.card {
    border: 1px solid #ccc;
    padding: 10px;
    .title { font-weight: bold; }
}
`;
loadscss(scss, 'card-style');
append('body', gen('div', null, gen('span', null, 'Hello', 'title'), 'card'));
```

## Pattern E: Markdown Content App
```javascript
getfile('content.md', md => {
    parsemd(md, html => append('#content', html, 'over'));
});
```

## Pattern F: Metadata for SEO
```javascript
load({
    title: 'My App',
    description: 'Built with SevnJS',
    type: 'website',
    image: '/og.png'
});
```
