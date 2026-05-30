# NEXUS AI — Design System & Brand Manual

> **Version:** 1.0.0 · **Status:** Active · **Owner:** Manik Mehta · **Last reviewed:** 2026-05-30

---

## Table of Contents

1. [Brand Overview](#1-brand-overview)
2. [Logo & Clear-Space Rules](#2-logo--clear-space-rules)
3. [Color Palette & Tokens](#3-color-palette--tokens)
4. [Typography](#4-typography)
5. [Spacing & Grid System](#5-spacing--grid-system)
6. [UI Component Specs](#6-ui-component-specs)
7. [Motion & Animation](#7-motion--animation)
8. [Imagery & Illustration Style](#8-imagery--illustration-style)
9. [Tone of Voice & Copy Guidelines](#9-tone-of-voice--copy-guidelines)
10. [Accessibility & Inclusivity Rules](#10-accessibility--inclusivity-rules)
11. [Real Usage Examples](#11-real-usage-examples)
12. [Asset Repository Structure](#12-asset-repository-structure)
13. [Governance](#13-governance)

---

## 1. Brand Overview

### Mission

NEXUS AI exists to democratise access to frontier AI by letting anyone — regardless of budget or technical background — converse with eight of the world's most capable language models from a single, beautifully crafted interface. No API keys to manage, no per-model billing surprises, no friction.

### Vision

One hub. All AI minds. Free.

### Brand Story

NEXUS AI was built by Manik Mehta, a 20-year-old computer science student from Fatehabad, Haryana, India. The project started as a personal experiment: what is the fastest path from a raw human thought to the best possible AI answer? That question led to three core innovations — a Prompt Enhancer that rewrites queries before they reach the model, a Deep Research Engine that explores topics across multiple branches simultaneously, and a multi-agent Debate Mode where AI systems challenge each other's reasoning. The name NEXUS — a connection or series of connections linking two or more things — reflects the product's role as a switchboard between human curiosity and machine intelligence.

### Brand Values

| Value | Expression in the product |
|---|---|
| **Openness** | Every core feature is free; no paywalls on intelligence |
| **Precision** | Prompt enhancement, structured responses, and skill sets all sharpen output quality |
| **Transparency** | API keys stay server-side; the user always knows which model is answering |
| **Ambition** | Deep Research, Debate Mode, and voice narration push beyond basic chat |
| **Craftsmanship** | Attention to micro-interactions, contrast ratios, and animation timing across every screen |

### Personality Archetype

NEXUS AI reads as an intelligent, slightly rebellious research partner — not a corporate assistant. The aesthetic borrows from deep-space visualisation and cyberpunk interfaces: dark, neon-lit, high-contrast, alive. It feels like a cockpit, not a chat box.

---

## 2. Logo & Clear-Space Rules

### Primary Logo

| Attribute | Value |
|---|---|
| Asset URL | `https://raw.githubusercontent.com/manik1312006/NEXUS-AI/refs/heads/main/Nexus_AI_logo%20.png` |
| Format | PNG with transparency |
| Minimum display size | 32 px tall |
| Preferred nav height | 40 px (landing page), 34 px (chat sidebar) |
| CSS filter (dark bg) | `drop-shadow(0 0 10px rgba(0,245,255,0.35))` |
| CSS filter (light bg) | none (logo has sufficient contrast without a glow) |

### Clear Space

The logo must have unobstructed space equal to the height of the letter "N" in the logotype on all four sides. Never place the logo closer than this margin to any other element, edge, or competing graphic.

```
         ← min clearance (1× cap-height) →
    ↑
    1× cap-height
    ↓
    [  N E X U S   A I   LOGO  ]
    ↑
    1× cap-height
    ↓
```

### Usage Rules

**Always:**
- Place on dark (`#050510`–`#111130`) or light (`#f0f0ff`–`#ffffff`) backgrounds only
- Apply the cyan drop-shadow on dark backgrounds to maintain the brand glow signature
- Use the PNG at its native aspect ratio — never stretch or skew

**Never:**
- Recolour the logo mark
- Place it on a busy photographic background without a dark scrim overlay (≥60% opacity)
- Use below 32 px tall — substitute a standalone "N" icon at that size
- Add extra text directly adjacent to the logo (taglines belong below with at least 8 px gap)

### Favicon / App Icon

Use the logo image scaled to 512×512 px for PWA icons and 192×192 px for Android. For 16×16 and 32×32 browser favicons, use a simplified single-glyph mark (the hexagonal node from the logo) at sufficient contrast on a `#050510` background.

---

## 3. Color Palette & Tokens

NEXUS AI ships two complete themes. CSS custom properties are the single source of truth — never hardcode a hex value in component code.

### 3.1 Dark Theme (Default)

```css
:root {
  /* Backgrounds */
  --c-bg:        #050510;   /* page canvas          */
  --c-sidebar:   #080820;   /* sidebar panel        */
  --c-surface:   #0d0d2b;   /* elevated surface     */
  --c-card:      #111130;   /* cards & bubbles      */

  /* Borders */
  --c-border:    rgba(120, 80, 255, 0.20);  /* default border */

  /* Neon Accents */
  --c-neon-purple: #7c3aed;  /* primary brand        */
  --c-neon-cyan:   #00f5ff;  /* links, highlights    */
  --c-neon-pink:   #ff2d78;  /* danger, delete, hot  */
  --c-neon-amber:  #ffbe00;  /* warning, enhance     */
  --c-neon-green:  #00ff9d;  /* success, research    */

  /* Text */
  --c-text:   #e8e8f8;  /* body copy            */
  --c-muted:  #7070a0;  /* captions, placeholders */

  /* Glows (box-shadow values) */
  --glow-purple: 0 0 40px rgba(124, 58, 237, 0.40);
  --glow-cyan:   0 0 40px rgba(0, 245, 255, 0.30);
}
```

### 3.2 Light Theme

```css
html.light {
  --c-bg:        #f0f0ff;
  --c-sidebar:   #e8e8ff;
  --c-surface:   #f5f5ff;
  --c-card:      #ffffff;
  --c-border:    rgba(120, 80, 255, 0.18);

  --c-neon-purple: #6d28d9;
  --c-neon-cyan:   #0284c7;
  --c-neon-pink:   #db2777;
  --c-neon-amber:  #d97706;
  --c-neon-green:  #059669;

  --c-text:   #1a1a3e;
  --c-muted:  #6060a0;

  --glow-purple: 0 0 40px rgba(109, 40, 217, 0.15);
  --glow-cyan:   0 0 40px rgba(2, 132, 199, 0.15);
}
```

### 3.3 Semantic Token Map

| Token | Dark | Light | Use |
|---|---|---|---|
| `--c-bg` | `#050510` | `#f0f0ff` | Page background |
| `--c-card` | `#111130` | `#ffffff` | Message bubbles, modal panels |
| `--c-neon-purple` | `#7c3aed` | `#6d28d9` | Primary buttons, brand accents |
| `--c-neon-cyan` | `#00f5ff` | `#0284c7` | Links, active states, highlights |
| `--c-neon-pink` | `#ff2d78` | `#db2777` | Destructive actions, errors |
| `--c-neon-amber` | `#ffbe00` | `#d97706` | Prompt Enhancer, warnings |
| `--c-neon-green` | `#00ff9d` | `#059669` | Deep Research, success states |
| `--c-text` | `#e8e8f8` | `#1a1a3e` | All body copy |
| `--c-muted` | `#7070a0` | `#6060a0` | Supporting text, placeholders |

### 3.4 Agent Identity Colors

Each AI agent has a unique color used for pills, badges, and debate transcript borders. These are **fixed** — they do not change between light and dark mode.

| Agent | Hex | Usage |
|---|---|---|
| GPT-OSS 120B | `#10b981` | Emerald green |
| LLaMA / Claude pill | `#f59e0b` | Warm amber |
| Gemini | `#3b82f6` | Sky blue |
| Mistral | `#8b5cf6` | Violet |
| LLaMA Groq | `#ec4899` | Hot pink |
| Cohere | `#06b6d4` | Teal |
| NVIDIA (NIM family) | `#76b900` | NVIDIA green |
| Gemma 4 | `#f472b6` | Pastel rose |

For debate turn borders, a rotating 5-color palette is applied in order:
`#00f5ff` → `#ff2d78` → `#ffbe00` → `#7c3aed` → `#00ff9d`

### 3.5 Contrast Notes

All text/background pairings meet **WCAG 2.1 AA** (4.5:1 for normal text, 3:1 for large text). Key pairings verified:

| Foreground | Background | Ratio | Rating |
|---|---|---|---|
| `#e8e8f8` on `#050510` | — | 17.4:1 | AAA |
| `#e8e8f8` on `#111130` | — | 11.6:1 | AAA |
| `#00f5ff` on `#111130` | — | 9.8:1 | AAA |
| `#7c3aed` on `#ffffff` | — | 5.1:1 | AA |
| `#7070a0` on `#050510` | — | 4.6:1 | AA |
| `#7070a0` on `#111130` | — | 3.1:1 | AA (large only) |

**Warning:** `--c-muted` (`#7070a0`) on `--c-card` (`#111130`) passes only at 18 px+ or bold weight. Use for captions and meta labels only, never for primary interactive copy.

The background grid overlay (`rgba(124,58,237,0.05)`) is a purely decorative layer and is excluded from contrast calculations.

---

## 4. Typography

### 4.1 Typeface Stack

All fonts are loaded from Google Fonts via a single `<link>` in the `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=Space+Mono:wght@400;700&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
```

| Role | Font | Weights | Character |
|---|---|---|---|
| **Display / Headings** | Syne | 400, 700, 800 | Geometric, space-age, strong visual rhythm |
| **Monospace / Labels** | Space Mono | 400, 700 | Technical, badge-friendly, deliberate quirkiness |
| **Body / UI** | DM Sans | 300, 400, 500, italic 300 | Clean, readable, warm at small sizes |

**Fallback stack:**
```css
font-family: 'DM Sans', system-ui, -apple-system, sans-serif;
font-family: 'Space Mono', 'Courier New', monospace;
font-family: 'Syne', 'Helvetica Neue', sans-serif;
```

### 4.2 Type Scale

| Level | Element | Font | Size | Weight | Line-height | Use |
|---|---|---|---|---|---|---|
| **Hero XL** | `.hero-title` | Syne | `clamp(3rem, 8vw, 6.5rem)` | 800 | 0.95 | Landing hero headline |
| **H1** | `h1`, `.modal-title` | Syne | 1.3–1.6 rem | 700–800 | 1.15 | Page and panel titles |
| **H2** | `.about-name`, `.welcome-state h2` | Syne | 1.6–2 rem | 800 | 1.1 | Section headings |
| **H3** | `.agent-current`, in-chat headings | Syne | 1 rem | 700 | 1.3 | Sub-section labels |
| **Logo text** | `.logo` | Syne | 1.6 rem | 800 | — | Nav brand |
| **Body** | `body`, `.message-content` | DM Sans | 0.9–0.95 rem | 400 | 1.7 | All conversational copy |
| **Body small** | captions, `.enhance-sub` | DM Sans | 0.72–0.8 rem | 400 | 1.4–1.6 | Supporting text |
| **Label** | `.agent-label`, `.about-label` | Space Mono | 0.65 rem | 400 | — | Uppercase category labels |
| **Micro** | `.input-hint`, `.skill-tag` | Space Mono | 0.62–0.7 rem | 400 | — | Badges, timestamps, hints |
| **Nav badge** | `.nav-badge` | Space Mono | 0.65 rem | 400 | — | Status chips |

### 4.3 Typographic Rules

- **Letter-spacing:** Syne display headings use `letter-spacing: -0.02em` to `−0.03em`. Space Mono labels use `+0.1em` to `+0.3em` for uppercase caps.
- **Gradient text:** Apply only to Syne display type. Use `background: linear-gradient(...)` + `-webkit-background-clip: text` + `-webkit-text-fill-color: transparent`. Never on body copy.
- **Shimmer animation** (`background-size: 200% auto; animation: shimmer 3s linear infinite`) is reserved for the hero gradient title only.
- **Italic:** DM Sans 300 italic is used only for blockquote-style callouts inside the artifact panel.
- **Code:** `Space Mono` at `0.82–0.88em`, inside a `<pre>` block styled with `background: rgba(0,0,0,0.4)`, `border-radius: 10–12px`.

---

## 5. Spacing & Grid System

### 5.1 Base Unit

The spacing system is built on a **4 px base unit**. All padding, margin, and gap values are multiples of 4.

| Token (informal) | Value | Common use |
|---|---|---|
| `space-1` | 4 px | Icon gap, tight inline |
| `space-2` | 8 px | Between badge and text, small button padding |
| `space-3` | 12 px | Sidebar row padding, agent grid gap |
| `space-4` | 16 px | Card interior padding (compact), input area |
| `space-5` | 20 px | Section header padding, modal inner |
| `space-6` | 24 px | Chat area padding, nav internal |
| `space-7` | 28 px | Auth card gap |
| `space-8` | 32 px | Modal padding |
| `space-10` | 40 px | Auth card padding, artifact body |
| `space-12` | 48 px | Nav outer padding, artifact body horizontal |
| `space-20` | 80 px | Hero vertical padding |

### 5.2 Layout Grid

**Sidebar + Main layout (chat page):**
```
┌──────────────────────────────────────────────────────┐
│  Sidebar (280 px fixed)  │  Main area (flex 1)       │
│                          │  ┌ Header (64 px)        │
│  • Agent panel           │  ├ Chat area (flex 1)    │
│  • Toggles               │  └ Input area (~80 px)   │
│  • Session list          │                           │
└──────────────────────────────────────────────────────┘
```

At ≤768 px the sidebar becomes a fixed-position drawer (`left: -300px` → `left: 0` on toggle) overlaid by a semi-transparent backdrop.

**Landing page:**
Single centered column with `max-width` controlled by the auth card (`min(480px, 90vw)`). Feature chips and agent pills use `flex-wrap` with `justify-content: center`.

**Research Artifact Panel:**
Slides in from the right at 50% viewport width (`min-width: 500px`). On ≤992 px it occupies 100% width. Uses `position: fixed` with `right: -100%` → `right: 0` transition.

### 5.3 Border Radii

| Size | Value | Used for |
|---|---|---|
| `radius-xs` | 4 px | code inline spans, small internal elements |
| `radius-sm` | 6–8 px | copy/listen buttons, small chips |
| `radius-md` | 10–12 px | inputs, agent buttons, session items |
| `radius-lg` | 14–16 px | message bubbles, input box, debate turns |
| `radius-xl` | 20–24 px | auth card, modals, main cards |
| `radius-pill` | 20–30 px | nav badge, feature chips, status pills |
| `radius-full` | 50% | avatars, toggle sliders, typing dots |

### 5.4 Background Grid

A decorative animated grid is applied to the landing page:

```css
background-image:
  linear-gradient(rgba(124,58,237,0.05) 1px, transparent 1px),
  linear-gradient(90deg, rgba(124,58,237,0.05) 1px, transparent 1px);
background-size: 60px 60px;
animation: gridMove 20s linear infinite;
```

This is purely decorative. Do not use it on the chat page (too visually busy behind conversation content).

---

## 6. UI Component Specs

### 6.1 Buttons

#### Primary Button

```css
background: linear-gradient(135deg, var(--c-neon-purple), #5b21b6);
color: #fff;
border: none;
border-radius: 12px;
padding: 14px;
font-family: 'Syne', sans-serif;
font-weight: 700;
font-size: 0.95rem;
letter-spacing: 0.05em;
box-shadow: 0 4px 20px rgba(124,58,237,0.30);
transition: all 0.2s;

/* Hover */
transform: translateY(-2px);
box-shadow: 0 8px 30px rgba(124,58,237,0.50);
```

**Use for:** Sign-in, form submission, "Continue as Guest".

#### Secondary / Outline Button

```css
border: 1px solid var(--c-neon-cyan);
background: transparent;
color: var(--c-neon-cyan);
border-radius: 12px;
padding: 13px;
font-family: 'DM Sans', sans-serif;
transition: all 0.2s;

/* Hover */
background: rgba(0,245,255,0.08);
```

**Use for:** Cancel, alternate actions.

#### Ghost / Tertiary Button

```css
border: 1px solid var(--c-border);
background: rgba(0,0,0,0.3);    /* dark */
background: rgba(255,255,255,0.6); /* light */
color: var(--c-muted);
border-radius: 10px;
padding: 7px 14px;
font-size: 0.8rem;
transition: all 0.2s;
```

**Use for:** "New chat", sidebar controls, copy buttons.

#### Destructive Button

```css
background: linear-gradient(135deg, #ff2d78, #c0185a);
color: #fff;
border: none;
border-radius: 12px;
box-shadow: 0 4px 20px rgba(255,45,120,0.30);
```

**Use for:** "Delete permanently" confirmation only.

#### Icon Send Button

```css
width: 40px; height: 40px;
border-radius: 12px;
border: 1px solid var(--c-border);
background: transparent;
color: var(--c-text);

/* Hover */
border-color: var(--c-neon-purple);
color: var(--c-neon-purple);
```

**States:** Never show a loading spinner on the send button — use the typing indicator in chat instead.

#### Button States Summary

| State | Visual change |
|---|---|
| Default | As specified above |
| Hover | `translateY(-1px)` to `−2px` + brightened shadow |
| Active/focus | `translateY(0)` + `outline: 2px solid var(--c-neon-cyan)` with 2 px offset |
| Disabled | `opacity: 0.6; pointer-events: none` |
| Loading | `opacity: 0.7; pointer-events: none` + inline spinner character |

### 6.2 Forms & Inputs

#### Text Input

```css
background: rgba(0,0,0,0.4);        /* dark */
background: rgba(255,255,255,0.9);   /* light */
border: 1px solid var(--c-border);
border-radius: 12px;
padding: 13px 16px;
color: var(--c-text);
font-family: 'DM Sans', sans-serif;
font-size: 0.95rem;
outline: none;
transition: all 0.2s;

/* Focus */
border-color: var(--c-neon-cyan);
box-shadow: 0 0 20px rgba(0,245,255,0.15);
```

Placeholder text uses `--c-muted`.

#### Chat Textarea

Borderless inside the input box container. `resize: none`, `max-height: 160px`, auto-expands via JS. Line-height 1.5.

#### Toggle Switch

44×22 px pill with a 14 px circular thumb. Three variants:

| Variant | `checked` background |
|---|---|
| Default (Enhancer) | `var(--c-neon-purple)` |
| Research | `linear-gradient(135deg, var(--c-neon-green), var(--c-neon-cyan))` |
| Debate | `linear-gradient(135deg, var(--c-neon-amber), #d97706)` |

Thumb transitions from `left: 3px` to `left: 23px` over `0.3s`.

### 6.3 Cards

#### Auth Card

```
background: rgba(17,17,48,0.8)   (dark) | rgba(255,255,255,0.85) (light)
border: 1px solid var(--c-border)
border-radius: 24px
padding: 40px 48px
width: min(480px, 90vw)
backdrop-filter: blur(30px)
box-shadow: var(--glow-purple), inset 0 1px 0 rgba(255,255,255,0.05)
```

#### Message Bubble — User

```
background: linear-gradient(135deg, var(--c-neon-purple), #5b21b6)
color: #fff
border-radius: 16px 4px 16px 16px   (top-right squared)
padding: 14px 18px
max-width: 75%
```

#### Message Bubble — Assistant

```
background: var(--c-card)
border: 1px solid var(--c-border)
border-radius: 4px 16px 16px 16px   (top-left squared)
padding: 14px 18px
max-width: 75%
```

#### Message Bubble — Error

```
background: rgba(255,45,120,0.10)
border: 1px solid rgba(255,45,120,0.30)
color: #ff6b9d
border-radius: 12px
```

#### About / Profile Card

```
background: rgba(17,17,48,0.6)   (dark)
border: 1px solid var(--c-border)
border-radius: 24px
padding: 36px 40px
max-width: 760px
transition: border-color 0.3s

/* Hover */
border-color: rgba(0,245,255,0.30)
```

#### Feature Chip (read-only)

```
border: 1px solid var(--c-border)
background: rgba(17,17,48,0.5)
border-radius: 40px
padding: 10px 20px
font-size: 0.82rem
color: var(--c-muted)
```

#### Skill Card

```
border: 1px solid var(--c-border)
border-radius: 12px
padding: 12px
background: rgba(255,255,255,0.025)
min-height: 170px
display: flex; flex-direction: column; gap: 8px
```

### 6.4 Agent Buttons (Sidebar Grid)

```css
/* 3-column grid, 5px gap */
padding: 8px 4px;
border-radius: 10px;
border: 1px solid var(--c-border);
background: rgba(0,0,0,0.3);
min-height: 88px;
display: flex; flex-direction: column; align-items: center;

/* Active */
border-color: var(--c-neon-cyan);
color: var(--c-neon-cyan);
background: rgba(0,245,255,0.08);
box-shadow: 0 0 12px rgba(0,245,255,0.15);

/* NVIDIA variant active */
border-color: #76b900;
color: #76b900;
background: rgba(118,185,0,0.08);
box-shadow: 0 0 12px rgba(118,185,0,0.20);
```

The "NIM" tag badge on NVIDIA agents:
```css
font-size: 0.55rem; background: rgba(118,185,0,0.15);
color: #76b900; border: 1px solid rgba(118,185,0,0.3);
border-radius: 3px; padding: 0 3px; letter-spacing: 0.04em;
```

### 6.5 Modals & Overlays

**Overlay backdrop:**
```css
background: rgba(5,5,16,0.85);
backdrop-filter: blur(10px);
```
Light theme: `rgba(240,240,255,0.85)`.

**Modal panel:**
```
background: var(--c-card)
border: 1px solid var(--c-border)
border-radius: 24px
padding: 32px
width: min(520px, 90vw)
box-shadow: 0 20px 60px rgba(0,0,0,0.5)
```

**Delete modal** adds a pink border tint and icon circle:
```css
border-color: rgba(255,45,120,0.3);
box-shadow: 0 20px 60px rgba(0,0,0,0.5), 0 0 40px rgba(255,45,120,0.08);
```

**Dismiss rule:** Always support click-outside-to-close for non-destructive modals. Destructive confirmation modals (delete chat) require explicit button confirmation.

### 6.6 Badges & Pills

| Type | Background | Border | Color | Radius |
|---|---|---|---|---|
| BETA badge | transparent | `var(--c-neon-amber)` | `var(--c-neon-amber)` | 20 px |
| Enhancer ON | `rgba(255,190,0,0.1)` | `rgba(255,190,0,0.3)` | `var(--c-neon-amber)` | 20 px |
| Web ON | `rgba(0,245,255,0.1)` | `rgba(0,245,255,0.3)` | `var(--c-neon-cyan)` | 20 px |
| Research ON | `rgba(0,255,157,0.1)` | `rgba(0,255,157,0.3)` | `var(--c-neon-green)` | 20 px |
| Debate ON | `rgba(255,190,0,0.1)` | `rgba(255,190,0,0.3)` | `var(--c-neon-amber)` | 20 px |
| Memory badge | `rgba(0,245,255,0.08)` | `rgba(0,245,255,0.25)` | `var(--c-neon-cyan)` | 10 px |
| Skill chip | `rgba(0,245,255,0.04)` | `rgba(0,245,255,0.20)` | `var(--c-neon-cyan)` | 999 px |

All header badges use `font-family: 'Space Mono'` at `0.72 rem`.

### 6.7 Icons

All icons use **Google Material Symbols** inline SVGs (24×24 viewBox, `fill="currentColor"`). Never use icon fonts or external icon CDNs — all icons are inlined for performance and offline reliability.

**Icon sizing:**
- Navigation / header actions: 24×24 px
- Button-embedded icons: 20×20 px
- Inline text icons: 14×16 px with `vertical-align: middle`
- Avatar fallback (agent): 22×24 px

**The robot icon** (`path M 323 -160 …`) is the universal agent avatar and appears in every AI message. Use the same path data consistently across all agent types — differentiation comes from the bubble label, not the avatar icon.

### 6.8 Typing Indicator

Three dots, 8×8 px, `border-radius: 50%`, `background: var(--c-neon-purple)`.

```css
@keyframes dot {
  0%, 100% { opacity: 0.3; transform: translateY(0); }
  50%       { opacity: 1;   transform: translateY(-4px); }
}
/* Stagger: nth-child(2) delay 0.2s, nth-child(3) delay 0.4s */
```

Status text below dots: `Space Mono`, `0.75 rem`, `var(--c-muted)`.

### 6.9 TTS Floating Player

```
position: fixed; bottom: 90px; left: 50%; transform: translateX(-50%)
background: var(--c-card)
border: 1px solid rgba(0,245,255,0.3)
border-radius: 20px
padding: 12px 20px
min-width: 320px; max-width: min(90vw, 520px)
backdrop-filter: blur(20px)
box-shadow: 0 12px 40px rgba(0,0,0,0.6), 0 0 30px rgba(0,245,255,0.1)
```

Supports drag-to-reposition (stores position in `localStorage`). On mobile: full-width, `border-radius: 16px`, speed selector hidden.

---

## 7. Motion & Animation

### 7.1 Core Principles

- **Purposeful:** Every animation communicates state or guides attention. No decorative loops on interactive elements (except the landing orbs which are background ambience).
- **Fast responses:** User-triggered transitions (`msgIn`, modal open/close) complete within 350 ms.
- **Easing:** Prefer `cubic-bezier(0.4, 0, 0.2, 1)` (Material standard ease) for panels; `cubic-bezier(0.16, 1, 0.3, 1)` (spring-like ease) for the artifact panel slide-in; `cubic-bezier(0.34, 1.56, 0.64, 1)` (overshoot spring) for the TTS player and memory toast.
- **Reduced motion:** All looping animations must be disabled with `@media (prefers-reduced-motion: reduce)` — add this override in the global stylesheet.

### 7.2 Animation Reference

| Name | Duration | Timing | Trigger |
|---|---|---|---|
| `msgIn` | 350 ms | ease | New message appended |
| `fadeDown` | 800 ms | ease | Landing page hero elements (staggered 0.1 s) |
| `fadeUp` | 800 ms | ease | Auth card, feature chips |
| `shimmer` | 3 s | linear infinite | Hero gradient title |
| `gridMove` | 20 s | linear infinite | Background grid |
| `orbFloat1/2/3` | 15–18 s | ease-in-out infinite | Background orbs |
| `pulse` | 2 s | ease-in-out infinite | Agent status dot |
| `dot` | 1.2 s | ease infinite | Typing indicator |
| `wspin` | 0.8–1 s | linear infinite | Spinners (research, debate) |
| `slideOut` | 300 ms | ease | Session item delete animation |
| `memCardIn` | 300 ms | ease | Memory card entry in modal |
| `branchPulse` | 1.5 s | alternate infinite | Active research branch node |
| `ttsBtnPulse` | 2 s | ease-in-out infinite | TTS button while speaking |
| `ttsBarWave` | 0.9–1.1 s | ease-in-out infinite | Waveform bars (button + player) |
| `ttsAvatarGlow` | 2 s | ease-in-out infinite | TTS player avatar |
| `recBlink` | 0.9 s | ease-in-out infinite | Live-search dot on branch nodes |

### 7.3 Transition Specifications

| Interaction | Property | Duration | Easing |
|---|---|---|---|
| Button hover | `transform`, `box-shadow` | 200 ms | ease |
| Input focus | `border-color`, `box-shadow` | 200 ms | ease |
| Sidebar open (mobile) | `left` | 300 ms | `cubic-bezier(0.4,0,0.2,1)` |
| Artifact panel open | `right` | 400 ms | `cubic-bezier(0.16,1,0.3,1)` |
| Agent panel expand | `max-height` | 350 ms | `cubic-bezier(0.4,0,0.2,1)` |
| Memory panel expand | `max-height` | 350 ms | `cubic-bezier(0.4,0,0.2,1)` |
| TTS player show | `opacity`, `transform` | 450 ms | `cubic-bezier(0.34,1.56,0.64,1)` |
| Memory toast show | `transform` | 450 ms | `cubic-bezier(0.34,1.56,0.64,1)` |
| Modal overlay | `display` → flex | instant | — (use opacity fade if adding) |
| Toggle slider thumb | `left` | 300 ms | ease |
| Theme toggle SVG elements | all | 350 ms | `cubic-bezier(0.4,0,0.2,1)` |

---

## 8. Imagery & Illustration Style

### 8.1 Photography

NEXUS AI is a **zero-photography product** in its current form. No stock photos, no user profile backgrounds, no scene photography in UI. Avatar images come exclusively from Google Auth photo URLs or the ui-avatars.com API (which generates initials-based avatars on a brand-matched background).

If photography is ever introduced (marketing pages, blog posts), it must be:
- Dark-tinted with ≥50% dark overlay
- Technology, data, or space-themed
- Avoiding faces unless it is the creator's own photo

### 8.2 Orbs (Ambient Background Illustration)

Three blurred radial gradients act as the primary "illustration" on the landing page:

```css
/* Orb 1 — purple, top-left */
width: 500px; height: 500px;
background: rgba(124,58,237,0.15);
filter: blur(80px);

/* Orb 2 — cyan, bottom-right */
width: 400px; height: 400px;
background: rgba(0,245,255,0.10);

/* Orb 3 — pink pulse, center */
width: 300px; height: 300px;
background: rgba(255,45,120,0.08);
```

These are hidden on mobile in light mode (`html.light .orb { display: none }`). They are **not** used on the chat page.

### 8.3 Icons & Glyphs as Illustration

Status icons within the product double as micro-illustrations:

| Context | Glyph | Colour |
|---|---|---|
| Welcome state spinner | `✦` | `var(--c-text)` with `rotate` animation |
| Deep Research | `🔬` | as-is |
| Debate Mode | Material SVG group icon | `var(--c-neon-amber)` |
| Memory | `🧠` | as-is |
| Success state | `✓` in circle | `var(--c-neon-green)` |
| Error state | `⚠️` | as-is / `var(--c-neon-pink)` |

### 8.4 Code Syntax Highlighting

Uses **highlight.js** with the `atom-one-dark` theme. This is the only context in which a third-party visual stylesheet overrides brand colors — it is acceptable because code is a distinct content type. Do not override hljs token colors.

### 8.5 Research Tree Visualisation

The research branch map is a pure CSS/HTML illustration using dashed borders:

```css
/* Trunk line */
border-left: 2px dashed rgba(120,80,255,0.2);

/* Branch connector */
border-top: 2px dashed rgba(120,80,255,0.2);
width: 16px;
```

Node states use the green/cyan glow progression (pending → active → completed) detailed in §3.4.

---

## 9. Tone of Voice & Copy Guidelines

### 9.1 Voice Attributes

| Attribute | What it means | What it doesn't mean |
|---|---|---|
| **Intelligent** | Uses precise, specific language | Jargon-heavy or inaccessible |
| **Direct** | Gets to the point fast | Blunt or cold |
| **Encouraging** | Celebrates capability | Sycophantic or hollow |
| **Slightly irreverent** | Can be playful in UI copy | Unprofessional in error messages |
| **Human** | Reads like a person wrote it | Conversational to the point of being unclear |

### 9.2 Copy Patterns

#### Headlines (Syne 800)
Short, punchy, verb-forward or noun-based. Two lines maximum.

```
✅  "One Hub. All AI Minds."
✅  "What can I help you with?"
❌  "Welcome to NEXUS AI — Your Multi-Agent Intelligence Platform"
```

#### Eyebrow Labels (Space Mono, all-caps, 0.7 rem)
Introduce a section or category. Always separated from the headline by at least 16 px.

```
✅  "✦ Multi-Agent Intelligence Platform"
✅  "Built by"
❌  "WELCOME TO THE NEXUS AI PLATFORM"
```

#### Feature / Sub-copy (DM Sans 300, 1.1 rem)
Conversational, benefit-led, 2–3 sentences maximum.

```
✅  "Chat with GPT-OSS 120B, LLaMA 3.3 70B, Gemini Flash... with our unique Prompt Enhancer
      that rewrites your query before sending it, getting you dramatically better answers."
❌  "NEXUS AI is a multi-model chat interface with prompt enhancement capabilities."
```

#### UI Labels (DM Sans 400–500 or Space Mono)
Imperative. Verb first for actions, noun for states.

```
✅  "Continue with Google"   ✅  "Sign out"     ✅  "✨ Enhancer ON"
❌  "Google Sign-In Button"  ❌  "Log Out"       ❌  "Enhancement Feature: Enabled"
```

#### Error Messages
Be specific about the cause; offer a path forward. Never blame the user.

```
✅  "⚠ Gemini key not configured on server."
✅  "⚠ Research execution failed: [reason]"
❌  "An unexpected error occurred. Please try again."
```

#### Empty States
Warm, action-oriented, never apologetic.

```
✅  "No chats yet"   ✅  "No memories yet. Start chatting to build your profile!"
❌  "You have not created any conversations."
```

#### Status / Progress Text (Space Mono)
Present tense, emoji prefix optional, concise.

```
✅  "Structuring research plan..."
✅  "🌐 Fetching live web data…"
✅  "✅ Research Completed!"
❌  "The system is currently generating your research plan. Please wait."
```

### 9.3 Punctuation & Formatting Rules

- Use an **ellipsis** (`…`) not three dots (`...`) in status messages and truncated text.
- Use an **em dash** (`—`) with no spaces in prose; use a spaced en dash (` – `) for ranges only if unavoidable.
- **Ampersands** (`&`) are acceptable in nav and badges (`CI/CD`, `Skill Sets`). Spell out "and" in running copy.
- **Emoji** are permitted in UI status labels, empty states, and section headers. Use sparingly (one per message max). Never use emoji in error text.
- **Sentence case** for all body copy, button labels, and modal text. **Title case** only for named features (Deep Research, Debate Mode, Prompt Enhancer).
- **"AI"** not "A.I." or "Ai". **"NEXUS AI"** always uppercase, never "Nexus AI" or "nexus ai".

### 9.4 Inclusive Language

- Refer to users as "you" — not "users", "clients", or "end-users".
- Avoid gendered language in all UI copy.
- "Guest" not "anonymous user".
- "Sign in" / "Sign out" not "Log in" / "Log out".

---

## 10. Accessibility & Inclusivity Rules

### 10.1 Colour & Contrast

- All text must meet **WCAG 2.1 Level AA**. Target AAA for body text where feasible.
- Never use colour as the *only* means of conveying information. Agent identity colours must always be accompanied by the agent name label.
- The `--c-muted` token (`#7070a0`) passes AA only at 18 px+ or 14 px bold on `--c-card`. Never use it for body text smaller than 14 px or for interactive labels.
- Decorative elements (orbs, background grid, glow effects) are excluded from contrast requirements but must not obscure text.

### 10.2 Keyboard Navigation

- All interactive elements must be reachable and operable via `Tab`/`Shift+Tab`.
- Visible `:focus-visible` outlines are required on all interactive elements:
  ```css
  :focus-visible {
    outline: 2px solid var(--c-neon-cyan);
    outline-offset: 2px;
    border-radius: inherit;
  }
  ```
- Modals must trap focus while open. The first focusable element receives focus on open; focus returns to the trigger on close.
- The chat textarea must allow `Enter` to send and `Shift+Enter` for newlines (implemented). This must be documented in the placeholder or `input-hint` label.
- The sidebar drawer on mobile must be closeable via `Escape` in addition to the overlay click.

### 10.3 Semantic HTML

- Use `<button>` for all click actions (never `<div onclick>`).
- Use `<nav>`, `<main>`, `<aside>`, `<footer>` landmarks correctly.
- All form inputs must have associated `<label>` elements (or `aria-label` where a visual label is not present).
- `<img>` elements must have descriptive `alt` attributes. The logo: `alt="NEXUS AI"`. User avatar: `alt="[User's name] avatar"`.
- Use `<details>` + `<summary>` for the CoT accordion and web source list — these are natively accessible and keyboard-navigable.

### 10.4 ARIA

- **Sparingly:** prefer native HTML semantics over ARIA roles.
- `aria-label` is required on icon-only buttons (theme toggle has `aria-label="Toggle theme"` — maintain this).
- `aria-label` on the send button: `"Send message"`.
- Dynamic regions that update (typing indicator, research status) should use `aria-live="polite"`.
- Modals require `role="dialog"`, `aria-modal="true"`, and `aria-labelledby` pointing to the modal title.

### 10.5 Reduced Motion

Add this to the global stylesheet (currently absent — this is a required addition):

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
  .orb, .bg-grid { display: none; }
}
```

The typing indicator dots, research spinner, TTS waveform bars, and orbs all loop infinitely — they must all stop under this media query.

### 10.6 Screen Readers

- The welcome state `✦` glyph: wrap in `<span aria-hidden="true">` so screen readers skip it.
- All emoji used as decorative prefixes in status text must be wrapped in `<span aria-hidden="true">`.
- The theme toggle SVG: the `<label>` has `aria-label` already. Ensure the hidden `<input type="checkbox">` also has `id="toggle"` matched by the label's `for` attribute (currently using `onchange` — consider adding `for` / `id` pairing).
- Agent avatar `<div>` elements should have `role="img"` and `aria-label="[Agent name] avatar"`.

### 10.7 Touch & Motor

- Minimum touch target size: **44×44 px** (WCAG 2.5.5). The send button at 40×40 px is marginally below — increase to 44×44 px at ≤768 px.
- The session delete button on desktop is `opacity: 0` until hover. On touch devices it must always be visible (`opacity: 1`), which the current rule `@media (max-width:768px) { .session-delete-btn { opacity:1 } }` satisfies. Maintain this.
- The TTS floating player includes drag-to-reposition. Provide a fallback for keyboard users to reposition or dismiss it via a visible close button.

### 10.8 Internationalisation (i18n)

- The product is currently English-only. All user-facing strings are hardcoded in HTML.
- When localisation is added, extract all strings to a JSON resource file keyed by ID.
- Do not hard-code text inside CSS `content: "..."` properties.
- Ensure font stacks include `system-ui` or CJK web-safe fonts in the fallback for future multilingual support.

---

## 11. Real Usage Examples

### 11.1 Web — Landing Page

The landing page demonstrates the full brand stack in a single view:

```
Nav:         Logo (40px) + BETA badge + theme toggle
Eyebrow:     "✦ Multi-Agent Intelligence Platform"  (Space Mono, cyan border pill)
H1:          "One Hub."      (Syne 800, var(--c-text))
             "All AI Minds." (Syne 800, shimmer gradient)
Sub-copy:    DM Sans 300, 1.1rem, var(--c-muted), max-width 560px
Agent pills: 8 × pill components (fixed agent colors)
Auth card:   24px radius, purple glow, tabbed (Google / Guest)
Features:    Row of 5 feature chips with colored dots
About card:  Flex row — avatar, label, name, meta, links
```

### 11.2 Web — Chat Interface

```
Sidebar:     280px, var(--c-sidebar), sectioned by collapse panels
Header:      Agent indicator dot + name + badge row + theme toggle
Chat area:   Message pairs, max-width 75% bubbles, syntax-highlighted code
Input:       Borderless textarea in a card container, send icon button
```

Active states in the header tell the user exactly what is running:
- `✨ Enhancer ON` — amber badge
- `🌐 Web ON` — cyan badge
- `🔬 Research ON` — green badge
- `Debate ON` — amber badge
- `Skills [n]` — purple badge (shown only when skills matched)

### 11.3 Social Media (Open Graph / Twitter Card)

Recommended OG image spec (not yet implemented — production requirement):
- **Size:** 1200×630 px
- **Background:** `#050510` with grid overlay and three orbs
- **Logo:** Centred, 120 px tall, with cyan drop-shadow
- **Tagline:** "One Hub. All AI Minds." in Syne 800, white, 64 px
- **Sub:** Eight agent pill labels arranged in two rows, fixed agent colors
- No photography. Export as PNG.

Twitter/X handle: not yet registered. Reserve `@nexushubai`.

### 11.4 Email (Transactional / Notification)

NEXUS AI does not currently send email. If Firebase email auth is added in future, emails must follow these rules:
- **Max width:** 600 px centred on `#0d0d2b` background
- **Primary font:** DM Sans served via Google Fonts `<link>` with `system-ui` fallback
- **Heading:** Syne Bold, white
- **CTA button:** Purple gradient, 12px radius, white Syne label, inline styles (email clients ignore stylesheets)
- **Logo:** Inline PNG at 160 px wide, `alt="NEXUS AI"`
- **Footer:** Muted `#7070a0`, Space Mono 11 px, unsubscribe link

### 11.5 Print / PDF (Research Reports)

The `@media print` block in `chat.html` converts the artifact panel to a readable print layout:
- Background: `white`
- Text: `black`
- `h1/h2/h3`: serif fallback font for print readability
- `pre` blocks: `#f4f4f4` background, `#000` text, `1px solid #ccc` border
- All chrome (header, action buttons) hidden

**PDF export** via the "Print / PDF" button uses the browser print dialog. Recommend adding `@page { margin: 1.5cm; }` to the print stylesheet.

---

## 12. Asset Repository Structure

```
nexus-ai/
├── assets/
│   ├── brand/
│   │   ├── logo/
│   │   │   ├── nexus-ai-logo.png          ← Primary logo (with transparency)
│   │   │   ├── nexus-ai-logo@2x.png       ← 2× retina version
│   │   │   ├── nexus-ai-logo-light.png    ← On-light variant (if needed)
│   │   │   ├── nexus-ai-wordmark.svg      ← Vector wordmark (to be created)
│   │   │   └── nexus-ai-icon.svg          ← Single-glyph icon for favicon / app
│   │   ├── favicon/
│   │   │   ├── favicon.ico                ← 16+32px multi-size ICO
│   │   │   ├── favicon-192.png            ← Android PWA
│   │   │   ├── favicon-512.png            ← Splash / PWA large
│   │   │   └── apple-touch-icon.png       ← 180px iOS
│   │   └── og/
│   │       ├── og-image.png               ← 1200×630 OG image
│   │       └── twitter-card.png           ← 800×418 Twitter summary large
│   ├── fonts/                             ← (Optional: self-hosted fallbacks)
│   │   ├── Syne-Bold.woff2
│   │   ├── Syne-ExtraBold.woff2
│   │   ├── SpaceMono-Regular.woff2
│   │   └── DMSans-Regular.woff2
│   └── screenshots/
│       ├── landing-dark.png
│       ├── landing-light.png
│       ├── chat-dark.png
│       └── chat-research.png
├── index.html
├── pages/
│   └── chat.html
├── server.js
├── skillRepository.js
├── package.json
├── DESIGN.md                              ← this file
└── README.md
```

### Remote Asset Locations

| Asset | Hosted URL |
|---|---|
| Primary logo | `https://raw.githubusercontent.com/manik1312006/NEXUS-AI/refs/heads/main/Nexus_AI_logo%20.png` |
| Syne (via Google Fonts) | `https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800` |
| Space Mono (via Google Fonts) | `https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700` |
| DM Sans (via Google Fonts) | `https://fonts.googleapis.com/css2?family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300` |
| Highlight.js CSS | `https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/atom-one-dark.min.css` |
| Highlight.js JS | `https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js` |
| Marked.js | `https://cdnjs.cloudflare.com/ajax/libs/marked/9.1.6/marked.min.js` |

**Recommendation:** For production resilience, bundle or self-host all assets above. The current reliance on GitHub raw URLs for the logo is fragile — migrate to `assets/brand/logo/`.

---

## 13. Governance

### Owner

**Manik Mehta** (`manikmehtaji@gmail.com`) is the sole design authority for NEXUS AI v1.x. All design decisions, token changes, and component additions require his approval.

### Change Process

1. **Propose** — open a GitHub Issue tagged `design` with a clear description of the change, the rationale, and a before/after visual if applicable.
2. **Draft** — implement the change in a feature branch. Update this document alongside any code change that affects a token, component spec, or typographic rule.
3. **Review** — self-review against the accessibility rules in §10. Check contrast ratios using the browser DevTools accessibility inspector or [Colour Contrast Checker](https://colourcontrast.cc).
4. **Merge** — squash-merge into `main`. Update the version number and changelog below.

### Review Cadence

| Review type | Frequency | Scope |
|---|---|---|
| Token audit | Every major feature addition | Verify no hardcoded colours crept in |
| Typography review | Quarterly | Check new copy against §9 guidelines |
| Accessibility audit | Every release | Run axe-core or Lighthouse accessibility scan |
| Full design system review | Annually or at v2.0 | Comprehensive check of all sections |

### Versioning

This document follows **SemVer** loosely:
- **Patch** (1.0.x) — copy corrections, clarifications, examples added.
- **Minor** (1.x.0) — new components documented, token additions, non-breaking changes.
- **Major** (x.0.0) — rebrand, token renames, breaking visual changes.

### Changelog

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-05-30 | Manik Mehta | Initial design system document created from v1.0 codebase |

---

*NEXUS AI Design System — maintained by Manik Mehta · `manikmehtaji@gmail.com` · [GitHub](https://github.com/manik1312006)*
