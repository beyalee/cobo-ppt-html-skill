# cobo-slides

> Cobo 品牌 HTML 演示技能，适用于 Claude Code。  
> 一行命令安装，输入主题，Claude 自动生成符合 Cobo 官网配色的产品演示幻灯片。

### 📖 [点这里看使用指南 →](https://beyalee.github.io/cobo-ppt-html-skill/guide.html)

不用 clone，点开就能看。里面有一份**可以直接翻页的示例 deck**，以及安装、用法、交付方式的完整说明。

---

## 安装

```bash
git clone https://github.com/beyalee/cobo-ppt-html-skill ~/.claude/skills/cobo-slides
```

安装后 Claude Code 会自动识别，无需重启。

> 仓库原名 `cobo-slides`，现已更名为 `cobo-ppt-html-skill`。旧地址靠 GitHub 重定向仍可 clone，建议直接用新地址。  
> **本地目录名仍用 `cobo-slides`** —— 技能名由目录名决定。

更新到最新版：

```bash
git -C ~/.claude/skills/cobo-slides pull
```

---

## 使用方式

**1. 直接描述主题**，Claude 自动生成：

```
帮我做一个 Cobo MPC 钱包的客户演示
```

**2. 给大纲或全文，只要排版：**

```
按这个大纲做一份 deck，面向合规团队：
1. 监管背景  2. 规则要求  3. 操作流程  4. 合规联动
```

**3. 上传 PDF / PPT，转换为 HTML：**

```
把这份 PPT 转成 HTML @产品介绍.pdf
```

Claude 会：
1. 询问演示主题、受众、章节结构
2. 给出大纲让你确认 —— **这一步值得认真看**，大纲的顶层章节会原样变成导航条的 Tab
3. 生成完整 Cobo 品牌风格的单文件 HTML
4. 在浏览器中打开预览

---

## 生成效果

-  **黑色背景** — `#0d0d0d`，与 cobo.com 官网一致
-  **紫色高亮** — `#7C7FE8`，与官网 "trusted" 强调色相同
-  **Plus Jakarta Sans** — 简洁现代的正文字体
-  **章节式顶部导航** — Logo + 4–6 个章节 Tab + 页码，随滚动高亮当前章节
-  **入场动画** — 每页内容依次淡入，章节切换流畅
-  **响应式** — 桌面 / 平板 / 手机均可演示
-  **零依赖** — 单个 `.html` 文件，离线可用

### 导航条给的是结构，不是页码索引

导航条**永远只有 4–6 个章节 Tab（硬上限 7 个）**，哪怕 deck 有 23 页 —— 每页一个 Tab 那不是导航，是页码列表。

```
·  封面      data-start="0"  data-end="0"
01 市场背景   data-start="1"  data-end="4"
02 产品能力   data-start="5"  data-end="11"
03 集成方案   data-start="12" data-end="17"
04 商务与支持 data-start="18" data-end="21"
·  结语      data-start="22" data-end="22"
```

每个 Tab 用 `data-start` / `data-end` 覆盖一段页码区间，区间须无缝隙、无重叠地铺满所有页。精确页码在右上角计数器与进度条里。

Tab 名字必须概括该章内容 —— `监管背景` `规则要求` 可以，`第一部分` `01` 不行。**名字是内容，编号只负责排序**：窄屏空间不够时藏编号，永远不藏名字。

---

## 放映操作

| 操作 | 作用 |
|------|------|
| ↓ / → / 空格 / PageDown | 下一页 |
| ↑ / ← / PageUp | 上一页 |
| Home / End | 首页 / 末页 |
| 滚轮、触屏上下滑 | 翻页 |
| 点顶部章节 Tab | 跳到该章第一页 |
| 点右侧圆点 | 跳到指定页 |
| 点左上 Logo | 回封面 |

---

## 导出分享

生成后 Claude 会询问是否需要：

**导出 PDF：**
```bash
bash scripts/export-pdf.sh my-deck.html
```

**部署到公网链接（Vercel）：**
```bash
bash scripts/deploy.sh my-deck.html
```

> 部署会把内容发布到公网。含客户名称、报价、未公开路线图的 deck，请先确认可以外发。

---

## 文件结构

```
cobo-slides/
├── SKILL.md              # 主流程：四个阶段 + 导航条规则（Claude 读取）
├── COBO_BRAND.md         # 完整品牌规范：CSS 变量 + 组件库 + 图标 + 产品词汇表
├── viewport-base.css     # 强制响应式基础样式
├── html-template.md      # JS 控制器完整实现 + 踩坑对照表
├── animation-patterns.md # 动画片段参考
├── guide.html            # 使用指南（浏览器打开）
└── scripts/
    ├── deploy.sh         # 部署到 Vercel
    └── export-pdf.sh     # 导出 PDF
```

---

## 依赖

- [Claude Code](https://claude.ai/code)（需登录 Anthropic 账户）
- 生成 HTML 无需任何本地依赖
- 导出 PDF 需要 Node.js（首次运行自动安装 Playwright）
- 部署需要 Vercel CLI（`npx vercel login`）

---

## 维护

更新品牌色或新增组件，编辑 `COBO_BRAND.md`；调整流程或规则，编辑 `SKILL.md`。  
Claude 每次生成前都会读取最新版本，改完立即生效。

`html-template.md` 里的 JS 控制器有几处反直觉的修复（滚动容器、`100vw`、导航同步、落位兜底），改动前先看该文件末尾的踩坑对照表。
