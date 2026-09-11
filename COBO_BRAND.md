# Cobo Brand Specification for HTML Slides

This file defines the complete visual identity for Cobo HTML presentations.
**Read this file in full before generating any slide.**

---

## Brand Identity

- **Company**: Cobo — "The trusted digital asset wallet platform"
- **Tagline**: Powering Your Crypto Ambitions
- **Website**: cobo.com
- **Tone**: Institutional, professional, Web3-native. Confident but not flashy.
- **Language**: Default Simplified Chinese. Match user's input language.

---

## Color Palette

```css
:root {
  /* === Core brand colors === */
  --bg:            #0d0d0d;   /* Near-black — primary slide background */
  --bg-card:       #161616;   /* Card background */
  --bg-card2:      #1c1c1c;   /* Card hover / secondary */
  --purple:        #7C7FE8;   /* PRIMARY ACCENT — matches cobo.com "trusted" */
  --purple-dim:    rgba(124,127,232,0.14);
  --purple-border: rgba(124,127,232,0.28);
  --blue-btn:      #3D50F5;   /* CTA button blue */
  --text:          #ffffff;
  --text-sec:      #888888;
  --text-muted:    #3a3a3a;
  --border:        rgba(255,255,255,0.07);
  --border-med:    rgba(255,255,255,0.11);

  /* === Layout === */
  --nav-h:      44px;   /* Fixed top nav height — ALL slides need padding-top: var(--nav-h) */

  /* === Typography scale (clamp = mobile → desktop) === */
  --title-size: clamp(1.6rem, 5vw, 4rem);
  --h2-size:    clamp(1.15rem, 2.8vw, 2.1rem);
  --h3-size:    clamp(0.9rem, 1.7vw, 1.28rem);
  --body-size:  clamp(0.7rem, 1.1vw, 0.92rem);
  --small-size: clamp(0.6rem, 0.88vw, 0.76rem);
  --label-size: clamp(0.53rem, 0.72vw, 0.66rem);

  /* === Spacing === */
  --pad:    clamp(1.4rem, 3.5vw, 4rem);
  --gap:    clamp(0.55rem, 1.3vw, 1.5rem);
  --gap-sm: clamp(0.28rem, 0.65vw, 0.75rem);

  /* === Animation === */
  --ease: cubic-bezier(0.16, 1, 0.3, 1);
  --dur:  0.6s;
}
```

---

## Typography

```
Logo font:  Varela Round 400       — circular rounded forms, approximates Cobo wordmark
Body font:  Plus Jakarta Sans      — 300 / 400 / 500 / 600 / 700 / 800
Source:     Google Fonts
```

**Google Fonts link (always include in `<head>`):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Varela+Round&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
```

**Type rules:**
- `h1` — 800 weight, letter-spacing -0.03em, line-height 1.07
- `h2` — 700 weight, letter-spacing -0.02em, line-height 1.15
- `h3` — 600 weight, line-height 1.3
- `p/li` — var(--body-size), color var(--text-sec), line-height 1.65
- Never use Inter, Roboto, Arial, or system fonts

---

## Cobo Logo

Use the inline SVG wordmark below. Do **not** use an `<img>` tag pointing to cobo.com — the CDN URL is blocked in many environments and breaks offline use.

```html
<svg width="69" height="21" viewBox="0 0 92 28" fill="none" xmlns="http://www.w3.org/2000/svg" style="display:block;">
  <path d="M63.054 17.2847C63.054 14.0335 60.4155 11.3966 57.1644 11.3981C53.9132 11.3981 51.2763 14.0365 51.2778 17.2877C51.2778 20.5389 53.9147 23.1743 57.1659 23.1743C60.4171 23.1743 63.054 20.5374 63.054 17.2862V17.2847ZM91.3344 17.2847C91.3299 23.1971 86.5316 27.9863 80.6191 27.9817C76.2218 27.9786 72.2725 25.2853 70.6644 21.1928L74.7402 17.117V17.2862C74.7478 20.5328 77.3863 23.1575 80.6329 23.1484C83.8795 23.1392 86.5042 20.5023 86.495 17.2557C86.4874 14.0091 83.849 11.3844 80.6024 11.3935C79.0492 11.3981 77.56 12.0154 76.4626 13.1144L64.7779 24.8052C60.635 29.0136 53.8644 29.0669 49.6545 24.9241C47.6075 22.9091 46.4582 20.1563 46.4628 17.2847V2.26495C46.5451 0.934302 47.6898 -0.0762592 49.0189 0.00452475C50.2352 0.0792118 51.2031 1.04862 51.2793 2.26495V8.27192C56.2178 5.02075 62.8573 6.38951 66.1085 11.328C66.8539 12.4605 67.3767 13.7241 67.651 15.0517L73.059 9.64525C77.2384 5.4643 84.0166 5.46278 88.1976 9.6422C90.2233 11.6679 91.3543 14.4207 91.3344 17.2847ZM44.8593 17.2847C44.87 23.191 40.0915 27.9893 34.1836 28C29.7695 28.0091 25.8034 25.3036 24.1999 21.1928L28.2757 17.117V17.2862C28.2833 20.5328 30.9218 23.1575 34.1684 23.1484C37.415 23.1407 40.0397 20.5023 40.0305 17.2557C40.0229 14.0091 37.3845 11.3844 34.1379 11.3935C32.5847 11.3981 31.0955 12.0154 29.9981 13.1144L18.2722 24.8509C14.0913 29.0303 7.31304 29.0288 3.13362 24.8479C-1.04581 20.6669 -1.04428 13.8887 3.13667 9.70927C7.31609 5.53137 14.0928 5.53137 18.2722 9.70927C19.2127 10.6543 19.2081 12.1846 18.2616 13.1235C17.3165 14.064 15.7862 14.0594 14.8473 13.1129C12.5442 10.8174 8.81593 10.8235 6.52045 13.1266C4.22496 15.4297 4.23106 19.1579 6.53416 21.4534C8.8327 23.7443 12.5503 23.7443 14.8473 21.4534L26.593 9.67726C30.7648 5.49631 37.5369 5.48869 41.7194 9.66049C43.7436 11.6801 44.8745 14.4267 44.8593 17.2877V17.2831V17.2847Z" fill="white"/>
</svg>
```

Scale by changing `width`/`height` proportionally (ratio is 92:28 ≈ 3.29:1). Never distort.

---

## Fixed Top Navigation Bar

**Required on every presentation. Two-row design: row 1 = logo + deck title + counter; row 2 = chapter tabs.**

Row 2 shows the deck's **chapters** — 4–6 of them, 7 absolute maximum — not its slides. See the rule under the HTML below.

```
--nav-h: 78px   (row1=36px + row2=42px)
```

### HTML structure

```html
<nav class="top-nav" id="topNav">

  <!-- Row 1: Logo · deck title · slide counter -->
  <div class="tn-row1">
    <div class="tn-logo" onclick="goToSlide(0)">
      <!-- Inline SVG logo — see "Cobo Logo" section above for full path data -->
      <svg width="69" height="21" viewBox="0 0 92 28" fill="none" xmlns="http://www.w3.org/2000/svg" style="display:block;"><path d="M63.054 17.2847C63.054 14.0335 60.4155 11.3966 57.1644 11.3981C53.9132 11.3981 51.2763 14.0365 51.2778 17.2877C51.2778 20.5389 53.9147 23.1743 57.1659 23.1743C60.4171 23.1743 63.054 20.5374 63.054 17.2862V17.2847ZM91.3344 17.2847C91.3299 23.1971 86.5316 27.9863 80.6191 27.9817C76.2218 27.9786 72.2725 25.2853 70.6644 21.1928L74.7402 17.117V17.2862C74.7478 20.5328 77.3863 23.1575 80.6329 23.1484C83.8795 23.1392 86.5042 20.5023 86.495 17.2557C86.4874 14.0091 83.849 11.3844 80.6024 11.3935C79.0492 11.3981 77.56 12.0154 76.4626 13.1144L64.7779 24.8052C60.635 29.0136 53.8644 29.0669 49.6545 24.9241C47.6075 22.9091 46.4582 20.1563 46.4628 17.2847V2.26495C46.5451 0.934302 47.6898 -0.0762592 49.0189 0.00452475C50.2352 0.0792118 51.2031 1.04862 51.2793 2.26495V8.27192C56.2178 5.02075 62.8573 6.38951 66.1085 11.328C66.8539 12.4605 67.3767 13.7241 67.651 15.0517L73.059 9.64525C77.2384 5.4643 84.0166 5.46278 88.1976 9.6422C90.2233 11.6679 91.3543 14.4207 91.3344 17.2847ZM44.8593 17.2847C44.87 23.191 40.0915 27.9893 34.1836 28C29.7695 28.0091 25.8034 25.3036 24.1999 21.1928L28.2757 17.117V17.2862C28.2833 20.5328 30.9218 23.1575 34.1684 23.1484C37.415 23.1407 40.0397 20.5023 40.0305 17.2557C40.0229 14.0091 37.3845 11.3844 34.1379 11.3935C32.5847 11.3981 31.0955 12.0154 29.9981 13.1144L18.2722 24.8509C14.0913 29.0303 7.31304 29.0288 3.13362 24.8479C-1.04581 20.6669 -1.04428 13.8887 3.13667 9.70927C7.31609 5.53137 14.0928 5.53137 18.2722 9.70927C19.2127 10.6543 19.2081 12.1846 18.2616 13.1235C17.3165 14.064 15.7862 14.0594 14.8473 13.1129C12.5442 10.8174 8.81593 10.8235 6.52045 13.1266C4.22496 15.4297 4.23106 19.1579 6.53416 21.4534C8.8327 23.7443 12.5503 23.7443 14.8473 21.4534L26.593 9.67726C30.7648 5.49631 37.5369 5.48869 41.7194 9.66049C43.7436 11.6801 44.8745 14.4267 44.8593 17.2877V17.2831V17.2847Z" fill="white"/></svg>
    </div>
    <div class="tn-divider"></div>
    <div class="tn-deck-title">[演示标题]</div>
    <div class="tn-counter" id="slideCounter">01 / N</div>
  </div>

  <!-- Row 2: one button per CHAPTER; data-start / data-end = that chapter's slide range -->
  <div class="tn-row2">
    <button class="tn-ch" data-start="0" data-end="0">
      <span class="tn-ch-num">·</span>
      <span class="tn-ch-name">封面</span>
    </button>
    <button class="tn-ch" data-start="1" data-end="5">
      <span class="tn-ch-num">01</span>
      <span class="tn-ch-name">章节名称</span>
    </button>
    <button class="tn-ch" data-start="6" data-end="12">
      <span class="tn-ch-num">02</span>
      <span class="tn-ch-name">章节名称</span>
    </button>
    <!-- 4–6 chapters total, plus 封面 / 结语 -->
  </div>

</nav>
<div class="progress-bar" id="progressBar"></div>
```

> **Rule**: `.tn-row2` holds **chapters, not slides** — it is the deck's agenda, not a page index.
> Target 4–6 buttons, hard cap 7, regardless of deck length: a 23-slide deck gets ~5 buttons, never 23.
> `data-start` / `data-end` are the first and last 0-based slide indices of the chapter; clicking jumps to
> `data-start` and the button stays `.active` across the whole range. Ranges must tile every slide with
> no gaps or overlaps. `tn-ch-num` is the zero-padded chapter number, or `·` for 封面 / 结语.
> Exact page position lives in `tn-counter` (`07 / 23`) and the progress bar, so nothing is lost.

### CSS

```css
:root {
  --nav-h: 78px;  /* row1 36px + row2 42px */
}

/* ── Outer shell ── */
.top-nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 2000;
  height: var(--nav-h);
  background: rgba(13,13,13,0.92);
  backdrop-filter: blur(16px) saturate(120%);
  -webkit-backdrop-filter: blur(16px) saturate(120%);
  /* NEVER add border-bottom here — the progress-bar directly below acts as the bottom edge.
     Adding border-bottom creates two overlapping lines at the nav bottom. */
  display: flex; flex-direction: column;
}

/* ── Row 1: logo + title + counter ── */
.tn-row1 {
  display: flex; align-items: center;
  padding: 0 var(--pad); gap: clamp(0.8rem, 2vw, 2rem);
  height: 36px; flex-shrink: 0;
  border-bottom: 1px solid var(--border);
}
.tn-logo { display:flex; align-items:center; flex-shrink:0; cursor:pointer; }
.tn-divider { width:1px; height:16px; background:var(--border-med); flex-shrink:0; }
.tn-deck-title {
  flex: 1; font-size: clamp(0.6rem, 0.9vw, 0.76rem); font-weight: 500;
  color: var(--text-sec); letter-spacing: 0.03em;
  white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
}
.tn-counter {
  flex-shrink: 0; font-size: clamp(0.55rem, 0.78vw, 0.66rem); font-weight: 600;
  color: var(--text-sec); letter-spacing: 0.1em;
  background: rgba(255,255,255,0.04); border: 1px solid var(--border);
  padding: 2px 9px; border-radius: 20px; transition: color 0.3s;
}

/* ── Row 2: chapter tabs, one per slide ── */
.tn-row2 {
  display: flex; align-items: stretch;
  height: 42px; flex: 1;
}
.tn-ch {
  flex: 1; background: none; border: none;
  border-right: 1px solid var(--border);
  cursor: pointer; font-family: var(--font);
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  gap: 2px; padding: 0 clamp(4px, 0.8vw, 10px);
  position: relative; white-space: nowrap;
  transition: background 0.2s ease;
}
.tn-ch:last-child { border-right: none; }
.tn-ch-num {
  font-size: clamp(0.5rem, 0.65vw, 0.58rem); font-weight: 700;
  color: var(--text-muted); letter-spacing: 0.12em;
  transition: color 0.2s;
}
.tn-ch-name {
  font-size: clamp(0.58rem, 0.85vw, 0.72rem); font-weight: 500;
  color: var(--text-sec);
  transition: color 0.2s;
}
/* No ::after indicator line — active state uses background + text color only */
.tn-ch:hover { background: rgba(255,255,255,0.03); }
.tn-ch:hover .tn-ch-name { color: rgba(255,255,255,0.75); }
.tn-ch.active { background: rgba(124,127,232,0.08); }
.tn-ch.active .tn-ch-num { color: var(--purple); }
.tn-ch.active .tn-ch-name { color: var(--text); font-weight: 600; }

/* ── Progress bar (below nav) ── */
.progress-bar {
  position: fixed; top: var(--nav-h); left: 0; height: 2px;
  background: linear-gradient(90deg, var(--purple), #a5a8ff);
  width: 0%; z-index: 1999; transition: width 0.35s ease;
}
```

### JS — `updateChapters` (in SlidePresentation class)

```javascript
updateChapters(slideIndex) {
  document.querySelectorAll('.tn-ch').forEach(ch => {
    const s = parseInt(ch.dataset.start);
    const e = parseInt(ch.dataset.end);
    ch.classList.toggle('active', slideIndex >= s && slideIndex <= e);
  });
}
```

---

## Slide Structure

**Every slide:**
```css
.slide {
  width: 100vw; height: 100vh; height: 100dvh;
  overflow: hidden; scroll-snap-align: start;
  display: flex; flex-direction: column;
  position: relative; background: var(--bg);
  padding-top: var(--nav-h); /* CRITICAL — reserve space for fixed nav */
}
.slide-content {
  flex: 1; display: flex; flex-direction: column;
  justify-content: center; max-height: 100%;
  overflow: hidden; padding: var(--pad); gap: var(--gap);
}
```

---

## Component Library

### Chip / Category Tag
```html
<div class="chip">LABEL TEXT</div>
```
```css
.chip { display:inline-flex; align-items:center; font-size:var(--label-size); font-weight:600; letter-spacing:0.09em; text-transform:uppercase; color:var(--purple); border:1px solid var(--purple-border); background:var(--purple-dim); padding:2px 10px; border-radius:20px; }
```
Use at top of each content slide to label the section.

---

### Section Divider Slide
```html
<section class="slide slide-section" id="slide-N">
  <div class="section-bg-num">I</div>  <!-- Ghost roman numeral -->
  <div class="section-inner">
    <div class="chip reveal d1">Chapter 1</div>
    <h1 class="reveal d2">Chapter<br><span class="hl">Title Here</span></h1>
  </div>
</section>
```
```css
.slide-section { justify-content:center; align-items:center; }
.section-inner { display:flex; flex-direction:column; align-items:center; text-align:center; padding:var(--pad); position:relative; z-index:1; gap:var(--gap-sm); }
.section-bg-num { position:absolute; inset:var(--nav-h) 0 0 0; display:flex; align-items:center; justify-content:center; font-size:clamp(7rem,20vw,17rem); font-weight:800; color:rgba(255,255,255,0.022); user-select:none; pointer-events:none; letter-spacing:-0.05em; }
```

---

### Stat Cards (company facts)
```html
<div class="g2x4">  <!-- 4-column grid, 2 rows -->
  <div class="stat"><div class="stat-num">500+</div><div class="stat-lbl">机构客户</div></div>
  <!-- ...repeat × 8 -->
</div>
```
```css
.g2x4 { display:grid; grid-template-columns:repeat(4,1fr); gap:var(--gap-sm); }
.stat { background:var(--bg-card); border:1px solid var(--border); border-radius:10px; padding:clamp(0.55rem,1.1vw,0.95rem); text-align:center; }
.stat-num { font-size:clamp(1.1rem,2.2vw,1.85rem); font-weight:800; line-height:1.2; letter-spacing:-0.02em; }
.stat-lbl { font-size:var(--label-size); color:var(--text-sec); margin-top:3px; }
```

---

### Tier Cards (1.0 / 2.0 / 3.0 progression)
```html
<div class="g3">
  <div class="tier">
    <div class="tier-label">1.0 通道</div>
    <div class="tier-name">基础收付通道</div>
    <ul><li>功能点一</li><li>功能点二</li></ul>
  </div>
  <!-- ×3 -->
</div>
```
```css
.g3 { display:grid; grid-template-columns:repeat(3,1fr); gap:var(--gap-sm); }
.tier { background:var(--bg-card); border:1px solid var(--border); border-radius:10px; padding:clamp(0.75rem,1.5vw,1.2rem); position:relative; overflow:hidden; }
.tier::after { content:''; position:absolute; top:0; left:0; right:0; height:2px; background:linear-gradient(90deg,var(--purple),#a5a8ff); }
.tier-label { font-size:var(--label-size); font-weight:700; color:var(--purple); letter-spacing:0.08em; text-transform:uppercase; margin-bottom:5px; }
.tier-name { font-size:var(--h3-size); font-weight:700; margin-bottom:var(--gap-sm); }
```

---

### Capability Cards (4-column)
```html
<div class="g4">
  <div class="cap">
    <div class="cap-icon">
      <!-- ALWAYS use inline SVG — never emoji. See Icon System below. -->
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M12 2v12m0 0l-4-4m4 4l4-4"/><rect x="3" y="17" width="18" height="4" rx="1"/>
      </svg>
    </div>
    <div class="cap-t">收款</div>
    <ul><li>功能点</li></ul>
  </div>
  <!-- ×4 -->
</div>
```
```css
.g4 { display:grid; grid-template-columns:repeat(4,1fr); gap:var(--gap-sm); }
.cap { background:var(--bg-card); border:1px solid var(--border); border-radius:10px; padding:clamp(0.65rem,1.3vw,1.05rem); }
.cap-icon { display:block; line-height:0; margin-bottom:8px; }
.cap-t { font-size:var(--h3-size); font-weight:700; margin-bottom:5px; }
```

---

### Flow Diagram (process arrows)
```html
<div class="flow">
  <div class="flow-box">
    <div class="flow-title">步骤名称</div>
    <div class="flow-desc">说明文字</div>
  </div>
  <div class="flow-arrow">→</div>
  <!-- repeat boxes + arrows -->
</div>
```
```css
.flow { display:flex; align-items:center; gap:clamp(0.25rem,0.7vw,0.55rem); }
.flow-box { flex:1; background:var(--bg-card); border:1px solid var(--border); border-radius:8px; padding:clamp(0.45rem,0.9vw,0.75rem); text-align:center; }
.flow-title { font-size:var(--label-size); font-weight:600; color:var(--purple); margin-bottom:2px; }
.flow-desc { font-size:clamp(0.53rem,0.75vw,0.66rem); color:var(--text-sec); }
.flow-arrow { color:var(--text-muted); font-size:clamp(0.75rem,1.1vw,0.95rem); flex-shrink:0; }
```
Use for: payment flows, process steps, data pipelines.

---

### Architecture Layer Stack
```html
<div class="layers">
  <div class="layer">
    <div class="layer-lbl">用户操作层</div>
    <div class="layer-tags">
      <span class="ltag">API 接入</span>
      <span class="ltag">Portal 接入</span>
    </div>
  </div>
  <!-- repeat for each layer; highlight bottom layer with border-color:var(--purple-border) -->
</div>
```
```css
.layers { display:flex; flex-direction:column; gap:var(--gap-sm); }
.layer { background:var(--bg-card); border:1px solid var(--border); border-radius:8px; display:flex; align-items:center; gap:var(--gap); padding:clamp(0.45rem,0.9vw,0.7rem) clamp(0.7rem,1.3vw,1.1rem); }
.layer-lbl { font-size:var(--small-size); font-weight:600; color:var(--purple); white-space:nowrap; min-width:clamp(65px,10vw,100px); }
.layer-tags { display:flex; flex-wrap:wrap; gap:5px; }
.ltag { background:rgba(124,127,232,0.1); border:1px solid var(--purple-border); border-radius:4px; padding:2px 7px; font-size:clamp(0.53rem,0.75vw,0.65rem); color:var(--text-sec); }
```

---

### Module Grid (6 features, 3×2)
```html
<div class="mods">
  <div class="mod">
    <div class="mod-n">① 功能名</div>
    <div class="mod-t">功能标题</div>
    <div class="mod-d">功能说明，控制在2行以内</div>
  </div>
  <!-- ×6 -->
</div>
```
```css
.mods { display:grid; grid-template-columns:repeat(3,1fr); gap:clamp(0.35rem,0.75vw,0.65rem); }
.mod { background:var(--bg-card); border:1px solid var(--border); border-radius:8px; padding:clamp(0.5rem,1vw,0.85rem); }
.mod-n { font-size:var(--label-size); font-weight:700; color:var(--purple); margin-bottom:3px; letter-spacing:0.05em; }
.mod-t { font-size:clamp(0.62rem,0.95vw,0.8rem); font-weight:700; margin-bottom:3px; }
.mod-d { font-size:clamp(0.56rem,0.78vw,0.68rem); color:var(--text-sec); line-height:1.5; }
```

---

### Highlight Box (key callout)
```html
<div class="hbox">
  Cobo 提供 <strong>MPC 自托管技术</strong>，助力满足 <strong style="color:var(--purple);">MiCA 合规</strong>要求。
</div>
```
```css
.hbox { background:rgba(124,127,232,0.07); border:1px solid var(--purple-border); border-radius:8px; padding:clamp(0.55rem,1.1vw,0.9rem); font-size:var(--body-size); color:var(--text-sec); }
.hbox strong { color:var(--text); font-weight:600; }
```

---

### Case Study / Scenario Layout
```html
<div class="scenario">
  <div class="scenario-tier">
    <!-- Tier label (1.0/2.0/3.0) + bullet list -->
  </div>
  <div>
    <div class="hbox">Case description...</div>
    <div class="flow"><!-- Flow diagram --></div>
  </div>
</div>
```
```css
.scenario { display:grid; grid-template-columns:1fr 2.2fr; gap:var(--gap); align-items:start; }
.scenario-tier { background:linear-gradient(135deg,rgba(124,127,232,0.11),rgba(124,127,232,0.04)); border:1px solid var(--purple-border); border-radius:10px; padding:clamp(0.75rem,1.4vw,1.15rem); }
```

---

### Partner Chips
```html
<div class="partners">
  <span class="ptag hi">Chainalysis</span>
  <span class="ptag">and more...</span>
</div>
```
```css
.partners { display:flex; flex-wrap:wrap; gap:var(--gap-sm); align-items:center; }
.ptag { background:var(--bg-card); border:1px solid var(--border); border-radius:6px; padding:3px 10px; font-size:var(--small-size); color:var(--text-sec); white-space:nowrap; }
.ptag.hi { border-color:var(--purple-border); color:var(--text); }
```

---

### Cover Slide
```html
<section class="slide slide-cover" id="slide-1">
  <div class="cover-body">
    <div class="chip reveal d1">Cobo · 2025</div>
    <h1 class="cover-title reveal d2">
      演示标题<br><span class="hl">关键词高亮</span>
    </h1>
    <div class="cover-meta reveal d3">
      <strong>姓名</strong><br>职位，Cobo<br>日期
    </div>
  </div>
  <div class="cover-orb"></div>  <!-- Animated purple glow orb -->
</section>
```
```css
.slide-cover { background:var(--bg); }
.cover-body { flex:1; display:flex; flex-direction:column; justify-content:center; padding:var(--pad); max-width:65%; gap:var(--gap); }
.cover-title { font-size:clamp(1.8rem,5.2vw,4.2rem); font-weight:800; line-height:1.06; letter-spacing:-0.03em; }
.cover-meta { font-size:var(--body-size); color:var(--text-sec); line-height:1.9; }
.cover-meta strong { color:var(--text); font-weight:600; }
.cover-orb { position:absolute; right:6%; top:50%; transform:translateY(-50%); width:clamp(140px,26vw,340px); height:clamp(140px,26vw,340px); border-radius:50%; background:radial-gradient(circle,rgba(124,127,232,0.2) 0%,rgba(124,127,232,0.05) 55%,transparent 70%); border:1px solid rgba(124,127,232,0.16); animation:orb 5s ease-in-out infinite; }
@keyframes orb { 0%,100%{transform:translateY(-50%) scale(1);opacity:.7} 50%{transform:translateY(-50%) scale(1.06);opacity:1} }
```

---

### Quote / Closing Slides
```css
.slide-quote,.slide-thanks { justify-content:center; align-items:center; }
.quote-txt { font-size:clamp(2rem,6vw,5.2rem); font-weight:800; letter-spacing:-0.04em; text-align:center; line-height:1.08; }
.hl2 { background:linear-gradient(135deg,var(--purple) 0%,#a5a8ff 100%); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; }
```

---

### Animations

```css
/* Standard entrance animations */
.reveal       { opacity:0; transform:translateY(20px); transition:opacity var(--dur) var(--ease),transform var(--dur) var(--ease); }
.reveal-left  { opacity:0; transform:translateX(-22px); transition:opacity var(--dur) var(--ease),transform var(--dur) var(--ease); }
.reveal-scale { opacity:0; transform:scale(0.93); transition:opacity var(--dur) var(--ease),transform var(--dur) var(--ease); }

/* Add .visible to slide on scroll (via IntersectionObserver) */
.slide.visible .reveal,
.slide.visible .reveal-left,
.slide.visible .reveal-scale { opacity:1; transform:none; }

/* Stagger delays via .d1 → .d8 classes */
.slide.visible .d1 { transition-delay:0.04s; }
.slide.visible .d2 { transition-delay:0.11s; }
.slide.visible .d3 { transition-delay:0.18s; }
.slide.visible .d4 { transition-delay:0.25s; }
.slide.visible .d5 { transition-delay:0.32s; }
.slide.visible .d6 { transition-delay:0.39s; }
.slide.visible .d7 { transition-delay:0.46s; }
.slide.visible .d8 { transition-delay:0.53s; }
```

---

### Right Nav Dots
```css
.nav-dots { position:fixed; right:clamp(0.5rem,1.2vw,1rem); top:50%; transform:translateY(-50%); display:flex; flex-direction:column; gap:5px; z-index:1999; }
.nav-dot { width:4px; height:4px; border-radius:50%; background:var(--text-muted); cursor:pointer; transition:all 0.25s ease; border:none; }
.nav-dot.active { background:var(--purple); box-shadow:0 0 5px var(--purple); transform:scale(1.6); }
```

---

## Responsive Breakpoints (copy into every presentation)

```css
@media (max-height: 700px) {
  :root { --pad:clamp(0.7rem,2.8vw,1.8rem); --gap:clamp(0.3rem,0.9vw,0.85rem); --title-size:clamp(1.2rem,4vw,2.3rem); --h2-size:clamp(1rem,2.5vw,1.55rem); }
}
@media (max-height: 600px) {
  :root { --pad:clamp(0.5rem,1.8vw,1.1rem); --gap:clamp(0.2rem,0.65vw,0.55rem); --body-size:clamp(0.6rem,0.92vw,0.78rem); }
  .nav-dots { display:none; }
}
/* Narrow screens: drop the chapter NUMBER, never the name.
   A nav reading "01 02 03 04" tells the reader nothing — the name is the
   content of the tab, the number is only decoration. */
@media (max-width: 760px) {
  .tn-ch-num { display:none; }
  .tn-ch { padding:0 3px; }
  .tn-ch-name {
    display:block; width:100%; text-align:center;
    font-size:clamp(0.5rem, 2.5vw, 0.68rem);
    overflow:hidden; text-overflow:ellipsis;
  }
}
@media (max-height: 500px) {
  :root { --pad:clamp(0.35rem,1.3vw,0.75rem); --title-size:clamp(0.95rem,3.2vw,1.4rem); --h2-size:clamp(0.88rem,2.1vw,1.15rem); }
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration:0.01ms !important; transition-duration:0.2s !important; }
  html { scroll-behavior:auto; }
}
```

---

## Common Utility Classes

```css
.hl  { color:var(--purple); }
.hl2 { background:linear-gradient(135deg,var(--purple),#a5a8ff); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; }
.g2  { display:grid; grid-template-columns:repeat(2,1fr); gap:var(--gap); }
.g3  { display:grid; grid-template-columns:repeat(3,1fr); gap:var(--gap-sm); }
.g4  { display:grid; grid-template-columns:repeat(4,1fr); gap:var(--gap-sm); }
.card { background:var(--bg-card); border:1px solid var(--border); border-radius:10px; padding:clamp(0.65rem,1.3vw,1.05rem); transition:border-color 0.22s,background 0.22s; }
.card:hover { border-color:var(--purple-border); background:var(--bg-card2); }
.card-title { font-size:var(--h3-size); font-weight:700; margin-bottom:var(--gap-sm); }
.glow-line { width:clamp(32px,5vw,54px); height:2px; background:linear-gradient(90deg,var(--purple),#a5a8ff); border-radius:2px; }
ul { list-style:none; }
ul li { padding-left:1.1em; position:relative; }
ul li::before { content:'·'; position:absolute; left:0; color:var(--purple); font-weight:700; }
```

---

## Cobo Products Reference

When generating product content, use these accurate terms:

| Product | Description |
|---------|-------------|
| Cobo Portal | All-in-one web dashboard for wallet operations |
| Custodial Wallets | Cobo-managed, institutional-grade custody |
| MPC Wallets | Multi-party computation — no single point of failure |
| Smart Contract Wallets | EVM contract-based, programmable policies |
| Exchange Wallets | API-based exchange account management |
| Cobo Guard | Mobile app for transaction approval (MFA) |
| Cobo Payment SDK | Stablecoin payment integration toolkit |
| Tokenization App | One-click stablecoin / RWA issuance |
| OTC App | In-platform fiat settlement with OTC partners |
| WaaS 2.0 | Wallet-as-a-Service API platform |

**Partners (use as examples):** Alchemy Pay, Bitget, HashKey, AntPool, Galaxy, Wintermute, Chainalysis, Elliptic

---

## Certifications to mention when relevant

- ISO 27001 certified
- SOC 2 Type 1 & 2 certified
- Singapore-licensed (MAS)
- 8+ years zero security incident

---

## Icon System

**Rule: NEVER use emoji as icons. Always use inline SVG.**

Emoji look unprofessional and render inconsistently across systems. Cobo.com uses minimalist line-drawn icons. Follow the same style:

- **Stroke-based** — `fill="none"`, `stroke="COLOR"`, `stroke-width="1.5"`, `stroke-linecap="round"`, `stroke-linejoin="round"`
- **Size** — `width="22" height="22" viewBox="0 0 24 24"` (scales with CSS if needed)
- **Color** — `stroke="#7C7FE8"` for accent icons (in cards, feature lists); `stroke="rgba(255,255,255,0.75)"` for neutral icons (cert badges, security)
- **Container** — `.cap-icon`, `.why-icon`, `.sec-icon` etc. must have `display:block; line-height:0; margin-bottom:8px`

**Starter icon library (copy-paste ready):**

```html
<!-- Layers / Flexible -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <path d="M2 9.5l10 5 10-5-10-5z"/><path d="M2 14l10 5 10-5"/><path d="M2 18.5l10 5 10-5"/>
</svg>

<!-- Network / Chain Support -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round">
  <circle cx="12" cy="12" r="3"/><circle cx="4" cy="6" r="2"/><circle cx="20" cy="6" r="2"/>
  <circle cx="4" cy="18" r="2"/><circle cx="20" cy="18" r="2"/>
  <line x1="5.8" y1="6.9" x2="9.5" y2="10.1"/><line x1="18.2" y1="6.9" x2="14.5" y2="10.1"/>
  <line x1="5.8" y1="17.1" x2="9.5" y2="13.9"/><line x1="18.2" y1="17.1" x2="14.5" y2="13.9"/>
</svg>

<!-- Zap / Automation -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <polyline points="13,2 6,13 12,13 11,22 18,11 12,11"/>
</svg>

<!-- Headset / Support -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round">
  <path d="M3 15V11a9 9 0 0 1 18 0v4"/>
  <rect x="1.5" y="13" width="4" height="6" rx="1.5"/>
  <rect x="18.5" y="13" width="4" height="6" rx="1.5"/>
  <path d="M22.5 19v1a3 3 0 0 1-3 3h-3"/>
</svg>

<!-- Shield + Check / Security -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="rgba(255,255,255,0.75)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <path d="M12 2L4 6v6c0 5.5 3.5 9.74 8 11 4.5-1.26 8-5.5 8-11V6z"/>
  <polyline points="9,12 11,14 15,10"/>
</svg>

<!-- Lock / Key Security -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="rgba(255,255,255,0.75)" stroke-width="1.5" stroke-linecap="round">
  <rect x="4" y="11" width="16" height="11" rx="2"/>
  <path d="M8 11V7a4 4 0 0 1 8 0v4"/>
  <circle cx="12" cy="16" r="1.5" fill="rgba(255,255,255,0.75)" stroke="none"/>
</svg>

<!-- Award / Certificate -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="rgba(255,255,255,0.75)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <circle cx="12" cy="9" r="5"/>
  <polyline points="9.5,14.5 8,22 12,19.5 16,22 14.5,14.5"/>
</svg>

<!-- Download / Receive -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <path d="M12 2v12m0 0l-4-4m4 4l4-4"/><rect x="3" y="17" width="18" height="4" rx="1"/>
</svg>

<!-- Upload / Send -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <path d="M12 22V10m0 0l4 4m-4-4l-4 4"/><rect x="3" y="3" width="18" height="4" rx="1"/>
</svg>

<!-- Globe / Global -->
<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#7C7FE8" stroke-width="1.5" stroke-linecap="round">
  <circle cx="12" cy="12" r="9"/>
  <path d="M2 12h20M12 3c-2.5 2.5-4 5-4 8s1.5 5.5 4 8M12 3c2.5 2.5 4 5 4 8s-1.5 5.5-4 8"/>
</svg>
```

---

## What NOT to do

- ❌ Use Inter, Roboto, or system fonts
- ❌ Use purple gradients on white backgrounds
- ❌ Use emoji as icons — always use inline SVG line-art (see Icon System above)
- ❌ Give every slide its own nav button — row 2 holds 4–6 **chapters**, never one tab per page
- ❌ Let the nav show bare numbers (`01 02 03 04`) — every tab must carry a name that summarises its chapter; when space is tight, hide `.tn-ch-num`, never `.tn-ch-name`
- ❌ Let slide content scroll
- ❌ Cram more than 6 bullet points per slide
- ❌ Show the style selection phase (always use Cobo Brand)
- ❌ Forget `padding-top: var(--nav-h)` on slides
- ❌ Negate CSS functions directly (`-clamp()` is invalid — use `calc(-1 * clamp(...))`)
- ❌ Add `border-bottom` to `.top-nav` — the progress bar sits flush below and serves as the bottom edge; a nav `border-bottom` creates two overlapping lines
