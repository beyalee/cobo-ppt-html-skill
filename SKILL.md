# Cobo Slides

Generate zero-dependency, Cobo-branded HTML presentations that run entirely in the browser.

**Brand**: Black background · Purple `#7C7FE8` accent · Plus Jakarta Sans · Fixed top nav  
**Output**: Single `.html` file, no build tools, no npm, works offline.

---

## Core Rules (Non-negotiable)

1. **Always use Cobo Brand style** — Never ask the user to pick a style. Brand spec is in [COBO_BRAND.md](COBO_BRAND.md).
2. **Viewport fitting** — Every slide MUST fit exactly within 100vh. No scrolling within slides. Content overflows? Split into multiple slides. Read [viewport-base.css](viewport-base.css) and embed it fully.
3. **Fixed top nav** — Every presentation includes the fixed top nav bar: Cobo logo left · chapter tabs center · slide counter right. See brand spec.
4. **Chinese-first** — Default language is Simplified Chinese unless user provides content in another language.
5. **Zero dependencies** — Single HTML file with all CSS/JS inline. Google Fonts loaded via CDN only.

---

## Phase 1: Understand the request

Determine what the user needs. Ask all questions in **one single `AskUserQuestion` call**:

**Question 1 — Topic** (header: "演示主题"):  
这次演示的主题/产品是什么？(例如：MPC钱包、稳定币支付、Cobo Portal)

**Question 2 — Audience** (header: "目标受众"):  
面向谁？Options: 客户/潜在客户 / 内部团队 / 合作伙伴 / 大会演讲

**Question 3 — Content** (header: "内容准备"):  
你有现成内容吗？Options: 有完整内容 / 有大纲/草稿 / 只有主题（我来帮你生成）/ 有PDF/PPT需要转换

**Question 4 — Length** (header: "幻灯片数量"):  
Options: 短 5-10页 / 中 10-20页 / 长 20+页

**Question 5 — Chapters** (header: "章节结构"):  
你希望有哪些章节？可以简单列出，或选择：让我根据主题推荐

If the user has content, ask them to share it after they answer the questions.

---

## Phase 2: Plan the slide structure

Based on the user's input, output a slide outline:

```
封面 (1)
关于 Cobo (1-2)
[Chapter 1 name] (N slides)
[Chapter 2 name] (N slides)
...
结语 (1-2)
```

Keep the outline to **4–6 chapters** between 封面 and 结语 — these become the top nav's chapter tabs verbatim (Phase 3), so an outline with 12 sections produces an unusable nav. Slide count per chapter is free; chapter count is not.

Show the outline and ask: "这个结构看起来合适吗？直接开始生成，还是需要调整？"

Wait for confirmation before generating.

---

## Phase 3: Generate the HTML

**Before generating, read these files in full:**

- [COBO_BRAND.md](COBO_BRAND.md) — Complete brand spec, CSS variables, component library
- [viewport-base.css](viewport-base.css) — Mandatory responsive CSS (embed fully in `<style>`)
- [html-template.md](html-template.md) — JS controller architecture
- [animation-patterns.md](animation-patterns.md) — Animation reference

### Generation requirements

**Font loading:**
```html
<link href="https://fonts.googleapis.com/css2?family=Varela+Round&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
```

**Fixed top nav — two-row design** (`--nav-h: 78px`). See COBO_BRAND.md for full CSS:
```html
<nav class="top-nav" id="topNav">
  <!-- Row 1: logo · deck title · slide counter -->
  <div class="tn-row1">
    <div class="tn-logo" onclick="goToSlide(0)"><!-- Cobo SVG wordmark --></div>
    <div class="tn-divider"></div>
    <div class="tn-deck-title">[演示标题]</div>
    <div class="tn-counter" id="slideCounter">01 / N</div>
  </div>
  <!-- Row 2: one button per CHAPTER (not per slide) -->
  <div class="tn-row2">
    <button class="tn-ch" data-start="0" data-end="0">
      <span class="tn-ch-num">·</span><span class="tn-ch-name">封面</span>
    </button>
    <button class="tn-ch" data-start="1" data-end="5">
      <span class="tn-ch-num">01</span><span class="tn-ch-name">章节名</span>
    </button>
    <button class="tn-ch" data-start="6" data-end="12">
      <span class="tn-ch-num">02</span><span class="tn-ch-name">章节名</span>
    </button>
    <!-- … 4–6 chapters total, then: -->
    <button class="tn-ch" data-start="22" data-end="22">
      <span class="tn-ch-num">·</span><span class="tn-ch-name">结语</span>
    </button>
  </div>
</nav>
<div class="progress-bar" id="progressBar"></div>
```

**Row 2 rule — chapters, never slides.**

The nav bar exists to show the **structure of the talk**, the way a deck's agenda slide does. It is not a page index.

- **Hard cap: 7 buttons.** Target 4–6. A 23-slide deck still gets ~5 buttons — never 23.
- Each button covers a **range**: `data-start` / `data-end` = the first and last 0-based slide index of that chapter. Clicking it jumps to `data-start`; the button stays `.active` for every slide in the range.
- `tn-ch-num` = the chapter number, zero-padded (`01`, `02`, …). For the cover and the closing slide use `·` instead of a number — they are not chapters.
- `tn-ch-name` = chapter name, ≤5 Chinese chars or ≤10 English chars.
- Every slide index from `0` to `N-1` must fall inside exactly one range — no gaps, no overlaps.

**Deriving the chapters**: reuse the outline you confirmed in Phase 2. Its top-level sections *are* the chapters. If that outline has more than 6 sections, group the neighbouring ones; if it has fewer than 3, split the longest.

Per-slide position is not lost — the `tn-counter` in row 1 shows the exact `07 / 23`, and the progress bar tracks it continuously.

**Example — a 23-slide deck:**
```
·  封面      data-start="0"  data-end="0"
01 市场背景   data-start="1"  data-end="4"
02 产品能力   data-start="5"  data-end="11"
03 集成方案   data-start="12" data-end="17"
04 商务与支持 data-start="18" data-end="21"
·  结语      data-start="22" data-end="22"
```

**Each slide must have** `padding-top: var(--nav-h)` to not hide under the nav.

**JS controller must:**
- Track current slide via IntersectionObserver
- Update chapter tab `.active` state based on `data-start`/`data-end`
- Update slide counter `"01 / N"` format
- Support keyboard (arrows, space, home/end), mousewheel, touch swipe
- Right-side nav dots

**Slide density limits** (strictly enforced):

| Type | Max content |
|------|-------------|
| Cover | Title + subtitle + speaker name |
| Section divider | Large chapter title + ghost number background |
| Content slide | H2 + 4-6 bullets OR H2 + 2-3 cards |
| Feature grid | H2 + 6 cards max (2×3 or 3×2) |
| Flow diagram | H2 + 4-5 boxes with arrows |
| Architecture | H2 + layer stack (4 rows max) |
| Quote/closing | 1 large quote OR thank-you |

**Content exceeds limits? Split into multiple slides automatically. Never cram, never scroll.**

### Cobo-specific slide templates to use

Use these battle-tested patterns from the brand spec:

- **Stats grid** — 2×4 grid of `.stat` cards for company facts
- **Tier cards** — 3-column `.tier` cards for product tiers (1.0/2.0/3.0)
- **Cap cards** — 4-column `.cap` cards for capabilities
- **Flow diagram** — Horizontal `.flow-box → .flow-box` for process flows
- **Layer stack** — Vertical `.layer` rows for architecture diagrams
- **Module grid** — 3×2 `.mod` grid for 6 feature modules
- **Scenario** — 1fr + 2fr split for case studies
- **Highlight box** — `.hbox` for key callouts

---

## Phase 4: Deliver

1. Save the file as `[topic-slug]-slides.html` in the current directory
2. Open it: `open [filename].html`
3. Tell the user:
   - File path and slide count
   - Navigation: arrow keys / space / scroll / nav dots
   - Chapter tabs in top nav jump to sections
4. Ask: "需要导出 PDF 或部署到公网链接吗？"

### Export PDF (if requested)
```bash
bash scripts/export-pdf.sh <path-to-html> [output.pdf]
```

### Deploy to URL (if requested)
```bash
bash scripts/deploy.sh <path-to-html>
```
Requires Vercel CLI. Guide user to `npx vercel login` if not authenticated.

---

## Converting existing PPT/PDF

If the user has a PPT or PDF to convert:

**PDF:**
```bash
# Install poppler if needed
brew install poppler
# Convert to images
mkdir -p /tmp/slides-pages
pdftoppm -r 150 -png "input.pdf" /tmp/slides-pages/page
```
Then read each page image with the Read tool (Claude is multimodal), extract text and structure, then generate HTML.

**PPTX:**
```bash
pip install python-pptx
python3 -c "
from pptx import Presentation
prs = Presentation('input.pptx')
for i, slide in enumerate(prs.slides):
    print(f'--- Slide {i+1} ---')
    for shape in slide.shapes:
        if hasattr(shape, 'text') and shape.text.strip():
            print(shape.text)
"
```
Extract content, then generate HTML preserving the structure.

---

## Supporting Files

| File | Purpose | When to read |
|------|---------|--------------|
| [COBO_BRAND.md](COBO_BRAND.md) | Full brand CSS + component reference | Always, before generating |
| [viewport-base.css](viewport-base.css) | Mandatory responsive CSS | Always, embed fully |
| [html-template.md](html-template.md) | JS architecture | Phase 3 |
| [animation-patterns.md](animation-patterns.md) | Animation snippets | Phase 3 |
| [scripts/export-pdf.sh](scripts/export-pdf.sh) | PDF export | Phase 4 if requested |
| [scripts/deploy.sh](scripts/deploy.sh) | Vercel deploy | Phase 4 if requested |
