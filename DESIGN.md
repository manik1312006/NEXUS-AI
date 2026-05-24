# NEXUS AI — Design System

> This document is the single source of truth for the visual language of NEXUS AI.  
> Every component, page, and element must conform to these specifications.  
> Deviation without documented justification is not permitted.

---

## Philosophy

The current interface suffers from three compounding problems: competing accent colors that cancel each other out, emoji-heavy chrome that reads as noise rather than signal, and animation overload that fatigues rather than delights. The result is a UI that tries to feel premium by being loud.

The new direction is the opposite. **Restraint is the luxury.** One accent color. Two typefaces. Deliberate whitespace. Motion that reveals rather than decorates. The interface should feel like a precision tool — confident, quiet, and extraordinarily capable.

No emoji anywhere in the interface except where the user has typed them. No decorative icons except the main logo. Iconography, when needed, uses thin SVG line icons at 1px–1.5px stroke weight (Lucide or equivalent).

---

## Color System

The palette is built around a single chromatic accent — Iris — used sparingly against neutral foundations. Both modes share the same accent; only the foundation flips.

### Token Names

| Token | Role |
|---|---|
| `--color-bg` | Page and app background |
| `--color-surface` | Cards, sidebar, modals, input areas |
| `--color-accent` | Interactive elements, highlights, focus rings, active states |
| `--color-text` | Primary body and heading text |
| `--color-muted` | Secondary text, placeholders, disabled states, borders |

### Dark Mode (default)

| Token | Hex | Name | Usage |
|---|---|---|---|
| `--color-bg` | `#08080E` | Void | Page background, deepest layer |
| `--color-surface` | `#111118` | Onyx | Sidebar, cards, input boxes, modals |
| `--color-accent` | `#6D4AFF` | Iris | Buttons, active nav, links, focus rings, progress bars |
| `--color-text` | `#EDECEA` | Pearl | All readable text |
| `--color-muted` | `#4A4A62` | Slate | Borders, placeholder text, secondary labels, dividers |

### Light Mode

| Token | Hex | Name | Usage |
|---|---|---|---|
| `--color-bg` | `#F5F4F1` | Linen | Page background |
| `--color-surface` | `#FFFFFF` | White | Sidebar, cards, input boxes, modals |
| `--color-accent` | `#6D4AFF` | Iris | Same accent, unchanged |
| `--color-text` | `#0D0C14` | Ink | All readable text |
| `--color-muted` | `#A8A8BC` | Ash | Borders, placeholder text, secondary labels, dividers |

### Derived Values (not additional colors — computed from the five tokens)

These are tints and transparencies of the five tokens above, not new colors.

```css
/* Accent tints — used for backgrounds on hover states and badges */
--color-accent-10: rgba(109, 74, 255, 0.10);
--color-accent-20: rgba(109, 74, 255, 0.20);
--color-accent-border: rgba(109, 74, 255, 0.35);

/* Muted tints — used for hairline borders */
--color-border: rgba(from var(--color-muted) r g b / 0.25);

/* Text on accent (button labels) */
--color-on-accent: #FFFFFF;

/* Destructive — a single red, used only for delete confirmations */
--color-danger: #E03E3E;
--color-danger-10: rgba(224, 62, 62, 0.10);
```

### Rules

- Iris (`#6D4AFF`) is the only chromatic color in the interface. No cyan. No pink. No amber. No green status colors.
- Status meaning (online, error, success) is communicated through text labels and icon shapes, not color.
- Gradients are permitted only on the primary CTA button: a linear gradient from `#6D4AFF` to `#4F33CC` (a darker violet), applied at 135deg. No other element uses a gradient.
- Dark glows and neon box-shadows are removed entirely.

---

## Typography

Two typefaces. No others.

### Display — Syne

Source: [Google Fonts — Syne](https://fonts.google.com/specimen/Syne)  
Weights loaded: `700`, `800`  
Usage: Logo wordmark, page headings (H1, H2), hero titles, modal titles, the agent name label in the header.

Syne is already loaded in the project. It is geometric and distinctive without being novelty. It provides the personality of the brand at large sizes while remaining legible.

### Body — DM Sans

Source: [Google Fonts — DM Sans](https://fonts.google.com/specimen/DM+Sans)  
Weights loaded: `300`, `400`, `500`  
Usage: All body text, UI labels, buttons, inputs, sidebar items, chat messages.

DM Sans is already loaded in the project. It is warm, optically even at small sizes, and neutral enough to let the content dominate.

### Monospace — Space Mono

Source: [Google Fonts — Space Mono](https://fonts.google.com/specimen/Space+Mono)  
Weights loaded: `400`, `700`  
Usage: Code blocks, inline code, keyboard shortcut labels, timestamp labels, agent model badges, the monospace hint text in the input footer.

Space Mono is already loaded in the project. Its slightly quirky letterforms give code blocks personality without competing with the UI text.

### Type Scale

```css
/* --- Headings (Syne) --- */
--text-hero:    clamp(2.5rem, 7vw, 5.5rem); /* Landing hero */
--text-h1:      1.75rem;   /* Page-level headings, modal titles */
--text-h2:      1.35rem;   /* Section headings */
--text-h3:      1.1rem;    /* Sub-section headings */

/* --- Body (DM Sans) --- */
--text-lg:      1.0rem;    /* Lead paragraphs, welcome message */
--text-base:    0.925rem;  /* Chat bubbles, sidebar items, modal body */
--text-sm:      0.8rem;    /* Secondary labels, timestamps, captions */
--text-xs:      0.7rem;    /* Badges, keyboard hints, meta info */

/* --- Mono (Space Mono) --- */
--text-code:    0.875rem;  /* Code block content */
--text-label:   0.65rem;   /* Agent type badges, section headers */
```

### Line Heights

```css
--leading-tight:  1.15;   /* Headings */
--leading-normal: 1.6;    /* Body text */
--leading-code:   1.7;    /* Code blocks */
--leading-loose:  1.85;   /* Chat messages (for readability at conversation pace) */
```

### Letter Spacing

```css
--tracking-tight:  -0.025em;  /* Hero headings (Syne 800) */
--tracking-normal:  0;        /* Body text */
--tracking-wide:    0.08em;   /* Uppercase labels, badges (Space Mono) */
--tracking-widest:  0.15em;   /* Section divider labels */
```

---

## Spacing System

Based on a 4px base unit. All spacing values are multiples of 4.

```
4px   — xs    (tight label gaps, icon-to-text spacing)
8px   — sm    (intra-component padding, badge padding)
12px  — md    (list item vertical padding)
16px  — lg    (card inner padding, input padding)
20px  — xl    (section gaps within a panel)
24px  — 2xl   (card padding, header padding)
32px  — 3xl   (section margins)
48px  — 4xl   (page section gaps)
64px  — 5xl   (hero section padding)
```

---

## Component Specifications

### Buttons

**Primary (CTA)**  
Background: linear-gradient(135deg, `#6D4AFF`, `#4F33CC`)  
Text: `--color-on-accent`, Syne 700, `--text-sm`, `--tracking-wide`  
Padding: `10px 24px`  
Border radius: `10px`  
Border: none  
Hover: `transform: translateY(-1px)`, increase shadow slightly  
Shadow: `0 4px 18px rgba(109, 74, 255, 0.30)`  
Active: `transform: translateY(0)`, shadow removed  
Transition: `all 180ms ease`

**Secondary (outlined)**  
Background: transparent  
Border: `1px solid var(--color-accent-border)`  
Text: `--color-accent`, DM Sans 500, `--text-sm`  
Hover: `background: var(--color-accent-10)`  
Same padding, radius, transition as primary.

**Ghost (tertiary)**  
Background: transparent  
Border: `1px solid var(--color-muted)` at 40% opacity  
Text: `--color-muted`, DM Sans 400, `--text-sm`  
Hover: `border-color: var(--color-text)`, `color: var(--color-text)`

**Danger**  
Background: transparent  
Border: `1px solid rgba(224, 62, 62, 0.40)`  
Text: `--color-danger`, DM Sans 500, `--text-sm`  
Hover: `background: var(--color-danger-10)`

### Input Fields

Background: `--color-surface`  
Border: `1px solid` at `--color-muted` opacity 40%  
Border radius: `12px`  
Padding: `12px 16px`  
Font: DM Sans 400, `--text-base`, `--color-text`  
Placeholder: `--color-muted`  
Focus border: `1px solid var(--color-accent-border)`  
Focus shadow: `0 0 0 3px var(--color-accent-10)`  
Transition: `border-color 150ms ease, box-shadow 150ms ease`

### Cards / Surfaces

Background: `--color-surface`  
Border: `1px solid` color-muted at 25% opacity  
Border radius: `16px`  
No box-shadow in dark mode (depth is created by the bg–surface contrast).  
Light mode only: `box-shadow: 0 1px 4px rgba(0,0,0,0.06)`

### Chat Bubbles

**User**  
Background: `--color-accent`  
Text: `--color-on-accent`, DM Sans 400, `--text-base`, `--leading-loose`  
Border radius: `16px 4px 16px 16px`  
Padding: `12px 18px`

**Assistant**  
Background: `--color-surface`  
Border: `1px solid` color-muted at 25% opacity  
Text: `--color-text`, DM Sans 400, `--text-base`, `--leading-loose`  
Border radius: `4px 16px 16px 16px`  
Padding: `12px 18px`

**Error**  
Background: `var(--color-danger-10)`  
Border: `1px solid rgba(224, 62, 62, 0.30)`  
Text: `--color-danger`

### Toggle Switch

Track off: border `1px solid` color-muted, background transparent  
Track on: background `--color-accent`, border-color `--color-accent`  
Knob: white circle  
No glow or shadow on the track.

### Badges / Pills

Background: `--color-accent-10`  
Border: `1px solid var(--color-accent-border)`  
Text: `--color-accent`, Space Mono 400, `--text-label`, `--tracking-wide`, uppercase  
Padding: `3px 10px`  
Border radius: `20px`

Only one badge style. Color is not used to differentiate badge types — text content differentiates them.

### Sidebar

Width: `272px`  
Background: `--color-surface` in dark, one step lighter than bg  
Right border: `1px solid` color-muted at 25%  
No shadow on the sidebar itself.  
Active session item: left border `2px solid --color-accent`, background `--color-accent-10`

---

## Motion

### Principles

- Motion should be **functional first** — it communicates state changes, not aesthetic flair.
- Duration is short. Most transitions: 150ms–250ms. No transition exceeds 400ms except page-level panel slides.
- Easing: `cubic-bezier(0.16, 1, 0.3, 1)` for elements entering the screen (snappy deceleration). `ease` for color/opacity changes.
- No continuous ambient animations (no pulsing orbs, no grid drift, no rotating elements at rest).
- No neon glow animations. No `box-shadow` keyframe loops.

### Permitted Animations

| Animation | Duration | Easing | Trigger |
|---|---|---|---|
| Message enter (translateY 10px → 0, opacity 0 → 1) | 280ms | cubic-bezier(0.16,1,0.3,1) | New message appended |
| Panel slide (sidebar, artifact panel) | 360ms | cubic-bezier(0.16,1,0.3,1) | Toggle open/close |
| Modal overlay (opacity 0 → 1) | 180ms | ease | Open |
| Modal card (translateY 12px → 0, opacity 0 → 1) | 240ms | cubic-bezier(0.16,1,0.3,1) | Open |
| Typing dots | 1.2s loop | ease-in-out | While AI is generating |
| Button hover (translateY -1px) | 180ms | ease | :hover |
| Focus ring (box-shadow expand) | 150ms | ease | :focus-visible |
| Toast slide (translateX 100% → 0) | 380ms | cubic-bezier(0.34,1.56,0.64,1) | New toast |
| Accordion expand (max-height) | 300ms | cubic-bezier(0.4,0,0.2,1) | Toggle |

### Removed

- Ambient orb floating animations
- Grid background drift animation
- Neon glow pulse keyframes on agent dot
- `wspin` welcome icon rotation
- `shimmer` gradient animation on hero text
- `branchPulse` box-shadow loop on research nodes

---

## Layout

### Page Structure

The chat interface is a two-column layout: fixed sidebar (272px) + fluid main area. On screens narrower than 768px the sidebar becomes a drawer (fixed, off-canvas, z-index 150).

### Spacing Grid

All major layout regions use multiples of the 4px base:

- Page top padding: `24px`
- Header height: `60px`
- Input area bottom padding: `20px` (plus `env(safe-area-inset-bottom)` on mobile)
- Chat messages horizontal padding: `24px` (desktop), `16px` (mobile)
- Chat messages vertical gap between messages: `16px`
- Sidebar inner padding: `16px`

### Max Width for Message Bubbles

- Desktop: `72%` of the chat column
- Tablet (768px–1024px): `80%`
- Mobile: `88%`

---

## Removed UI Patterns

The following patterns from the current codebase must be removed during implementation:

- All animated background orbs (`div.orb`, `div.bg-grid`)
- All neon color variables (`--c-neon-cyan`, `--c-neon-pink`, `--c-neon-amber`, `--c-neon-green`)
- All `box-shadow` values that reference cyan, pink, amber, or green
- Emoji used as functional UI elements (replace with SVG line icons or plain text labels)
- Animated `text-shadow` and `filter: drop-shadow` on body text
- `@keyframes shimmer` gradient animation on headings
- `@keyframes orbFloat` and `@keyframes gridMove` animations
- `@keyframes wspin` on the welcome icon
- The `sparkleIn` / `blurOut` prompt enhancement animation (replace with a simple `opacity` fade)
- The `enhanced-pill` emoji decoration (replace with a plain text badge)
- The `nvidia-tag` green micro-badge (use text label instead)

---

## CSS Variable Reference

Full declaration block for both modes:

```css
:root {
  /* --- Five core tokens (dark mode defaults) --- */
  --color-bg:       #08080E;
  --color-surface:  #111118;
  --color-accent:   #6D4AFF;
  --color-text:     #EDECEA;
  --color-muted:    #4A4A62;

  /* --- Derived (computed, not new colors) --- */
  --color-accent-10:     rgba(109, 74, 255, 0.10);
  --color-accent-20:     rgba(109, 74, 255, 0.20);
  --color-accent-border: rgba(109, 74, 255, 0.35);
  --color-border:        rgba(74, 74, 98, 0.30);
  --color-on-accent:     #FFFFFF;
  --color-danger:        #E03E3E;
  --color-danger-10:     rgba(224, 62, 62, 0.10);

  /* --- Typography --- */
  --font-display: 'Syne', sans-serif;
  --font-body:    'DM Sans', sans-serif;
  --font-mono:    'Space Mono', monospace;

  /* --- Type scale --- */
  --text-hero:  clamp(2.5rem, 7vw, 5.5rem);
  --text-h1:    1.75rem;
  --text-h2:    1.35rem;
  --text-h3:    1.1rem;
  --text-lg:    1.0rem;
  --text-base:  0.925rem;
  --text-sm:    0.8rem;
  --text-xs:    0.7rem;
  --text-code:  0.875rem;
  --text-label: 0.65rem;

  /* --- Leading --- */
  --leading-tight:  1.15;
  --leading-normal: 1.6;
  --leading-code:   1.7;
  --leading-loose:  1.85;

  /* --- Tracking --- */
  --tracking-tight:   -0.025em;
  --tracking-normal:   0em;
  --tracking-wide:     0.08em;
  --tracking-widest:   0.15em;

  /* --- Spacing --- */
  --space-xs:  4px;
  --space-sm:  8px;
  --space-md:  12px;
  --space-lg:  16px;
  --space-xl:  20px;
  --space-2xl: 24px;
  --space-3xl: 32px;
  --space-4xl: 48px;
  --space-5xl: 64px;

  /* --- Radii --- */
  --radius-sm:   6px;
  --radius-md:   10px;
  --radius-lg:   14px;
  --radius-xl:   20px;
  --radius-full: 9999px;

  /* --- Transitions --- */
  --transition-fast:   150ms ease;
  --transition-base:   180ms ease;
  --transition-enter:  280ms cubic-bezier(0.16, 1, 0.3, 1);
  --transition-panel:  360ms cubic-bezier(0.16, 1, 0.3, 1);
  --transition-spring: 380ms cubic-bezier(0.34, 1.56, 0.64, 1);
}

html.light {
  --color-bg:      #F5F4F1;
  --color-surface: #FFFFFF;
  --color-accent:  #6D4AFF;  /* unchanged */
  --color-text:    #0D0C14;
  --color-muted:   #A8A8BC;
  --color-border:  rgba(168, 168, 188, 0.35);
}
```

---

## Accessibility

- Minimum contrast ratio for body text against its background: **4.5:1** (WCAG AA).
- Minimum contrast ratio for large text (Syne headings above 24px): **3:1**.
- All interactive elements must have a visible `:focus-visible` ring: `0 0 0 3px var(--color-accent-10)` with `outline: 2px solid var(--color-accent)`.
- Do not use color alone to communicate state — pair color changes with label or icon changes.
- The typing indicator dots must have an `aria-label="Thinking"` on the parent element.
- Theme toggle button must have `aria-label="Switch to light mode"` / `aria-label="Switch to dark mode"` updated dynamically.

---

## What This System Does Not Include

- Illustration or decorative imagery of any kind
- Gradient meshes or noise texture overlays
- Particle systems or canvas-based effects
- Any icon set beyond the main logo and Lucide SVG line icons
- Custom cursor styles
- Scroll-triggered entrance animations
- Parallax effects

This list is intentional. Every item removed is a decision, not an omission.

---

*Version 1.0 — NEXUS AI Design System*
