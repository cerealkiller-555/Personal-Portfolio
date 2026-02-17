# CSS Cheatsheet

## Selectors
- `.class` – Class selector
- `#id` – ID selector
- `element` – Element selector
- `element.class` – Element with class
- `element, .class` – Multiple selectors
- `parent > child` – Direct child
- `parent descendant` – Any nested child
- `element:hover` – Pseudo-class (hover, focus, active)
- `element::before` – Pseudo-element (before, after)
- `[attr="value"]` – Attribute selector

## Box Model
```css
/* margin > border > padding > content */
margin: 10px;           /* Outside space */
border: 2px solid #ccc; /* Border width, style, color */
padding: 10px;          /* Inside space */
width: 100px;
height: 100px;
box-sizing: border-box; /* Include padding/border in width */
```

## Display & Layout
```css
display: block;        /* Full width, stacks vertically */
display: inline;       /* Width of content only */
display: inline-block;  /* Both inline + block properties */
display: flex;         /* Flexbox layout (1D) */
display: grid;         /* Grid layout (2D) */
display: none;         /* Hidden from page */

/* Flexbox */
flex-direction: row | column;
justify-content: space-between | space-around | center | flex-start | flex-end;
align-items: center | flex-start | flex-end | stretch;
gap: 1rem;
flex: 1; /* Grow equally */

/* Grid */
grid-template-columns: repeat(3, 1fr);
grid-template-columns: 200px 1fr 100px;
gap: 1rem;
```

## Typography
```css
font-family: Arial, sans-serif;
font-size: 16px;        /* px, em, rem, % */
font-weight: 400 | 700 | bold;
font-style: italic;
line-height: 1.5;       /* Relative to font-size */
letter-spacing: 0.05em;
text-align: left | center | right | justify;
text-decoration: none | underline | overline | line-through;
color: #111827;
```

## Colors & Backgrounds
```css
color: #fff;            /* Hex */
color: rgb(255, 0, 0);  /* RGB */
color: rgba(0, 0, 0, 0.5); /* RGB + Alpha (opacity) */
color: hsl(0, 100%, 50%); /* Hue, Saturation, Lightness */

background-color: #fff;
background-image: url('image.png');
background-size: cover | contain | 100px 200px;
background-position: center | top left | 50% 50%;
background-repeat: no-repeat | repeat-x | repeat-y;
background: url('img.png') no-repeat center / cover;
```

## Spacing & Size
```css
width: 100% | auto | 100px | calc(100% - 20px);
height: auto | 100px | 100%;
min-width: 300px;
max-width: 1200px;
padding: 10px;           /* All sides */
padding: 10px 20px;      /* Top/Bottom Left/Right */
padding: 10px 20px 30px 40px; /* Top Right Bottom Left */
margin: auto;            /* Center horizontally */
margin: 0 auto;          /* Vertical 0, horizontal center */
```

## Positioning
```css
position: static;   /* Default */
position: relative; /* Relative to normal flow */
position: absolute; /* Relative to positioned parent */
position: fixed;    /* Relative to viewport */
position: sticky;   /* Sticky on scroll */

top: 10px;
left: 20px;
z-index: 10;       /* Stack order (higher = on top) */
```

## Borders & Shadows
```css
border: 2px solid #ccc;
border-radius: 8px;
border-top: 1px solid #ddd;
box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.2);
text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
```

## Transforms & Transitions
```css
/* Transforms */
transform: translateX(10px) | translateY(20px);
transform: scale(1.5);
transform: rotate(45deg);
transform: skew(10deg);
transform-origin: center | top left;

/* Transitions */
transition: all 0.3s ease;
transition: background-color 0.3s ease-in-out;
transition-delay: 0.1s;
transition-duration: 0.5s;

/* Animations */
@keyframes slide {
  from { left: 0; }
  to { left: 100px; }
}
animation: slide 1s ease infinite;
```

## Opacity & Visibility
```css
opacity: 0.5;        /* 0 = transparent, 1 = opaque */
visibility: hidden;  /* Hidden but takes space */
visibility: visible;
overflow: hidden | visible | scroll | auto;
```

## CSS Variables
```css
:root {
  --primary-color: #2563eb;
  --spacing: 1rem;
  --border-radius: 8px;
}

/* Use variables */
color: var(--primary-color);
padding: var(--spacing);
border-radius: var(--border-radius);
```

## Media Queries (Responsive)
```css
/* Mobile-first: start small, add rules for larger screens */
@media (min-width: 640px) { /* tablet */ }
@media (min-width: 1024px) { /* desktop */ }

/* Landscape vs portrait */
@media (orientation: landscape) { }

/* Reduce motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  * { animation: none !important; transition: none !important; }
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
  body { background: #111; color: #fff; }
}
```

## Common Patterns

### Center content
```css
.container { max-width: 1200px; margin: 0 auto; padding: 0 1rem; }
```

### Center with Flexbox
```css
display: flex;
justify-content: center;
align-items: center;
height: 100vh;
```

### Responsive grid
```css
display: grid;
grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
gap: 1rem;
```

### Button styling
```css
.btn {
  display: inline-block;
  padding: 0.5rem 1rem;
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
  text-decoration: none;
  transition: background 0.3s ease;
}
.btn:hover { background: #1e40af; }
```

### Link styling
```css
a {
  color: #2563eb;
  text-decoration: none;
  position: relative;
}
a:hover { text-decoration: underline; }
a:visited { color: #7c3aed; }
a:focus { outline: 2px solid #2563eb; outline-offset: 2px; }
```

### Form inputs
```css
input, textarea, select {
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-family: inherit;
  font-size: 1rem;
}
input:focus, textarea:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
}
```

## Units
- `px` – Pixels (fixed)
- `em` – Relative to parent's font-size
- `rem` – Relative to root (html) font-size
- `%` – Percentage of parent
- `vw` / `vh` – Viewport width/height
- `vmin` / `vmax` – Smallest/largest viewport dimension

## Tips
1. **Reset CSS:** Use `*{box-sizing:border-box}` to include padding/border in width calculations.
2. **Mobile-first:** Write styles for mobile, then add larger breakpoints.
3. **Use rem:** Set `html{font-size:16px}` and use `rem` for scalability.
4. **CSS Vars:** Define colors/spacing in `:root` for easy theming.
5. **Flexbox > floats:** Use `display:flex` for layouts (easier and more reliable).
6. **BEM naming:** Use `.block__element--modifier` for clarity.
7. **Avoid `!important`:** Only use for utilities or accessibility fixes.
8. **Test responsiveness:** Use browser dev tools to emulate mobile devices.
9. **Contrast:** Ensure text/background colors have good contrast (WCAG AA ≥ 4.5:1).
10. **Performance:** Prefer `transform` + `opacity` for animations; avoid expensive properties like `width` changes.
