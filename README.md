# AI Agent 製作簡報的選擇：完整選型研究

> **研究時間**：2026 年 4 月 29 日  
> **最後更新**：2026 年 4 月 30 日  
> **⚠️ 注意**：AI 工具生態變化極快，本文所列的專案版本、Stars 數、功能支援等資訊以研究當日為準，請自行查證最新狀態。

## 📊 簡報

👉 **[線上簡報（GitHub Pages）](https://nczz.github.io/ai-agent-slides/ai-agent-slides.html)**

本研究的結論簡報，用 Marp 從 Markdown 生成，本身就是研究成果的實證。

---

## 背景

當你想用 AI Agent（Kiro、Claude Code、Cursor、Windsurf…）來製作簡報時，面對的選擇比想像中多。這份研究從多個維度系統性地評估了現有方案，最終得出適合「個人教學用途」的推薦。

## 研究維度

### 一、源檔格式：開源 × 通用 × Agent 友善

*研究日期：2026-04-29*

Agent 需要能讀寫源檔，因此格式的選擇直接影響工作流效率。

| 格式 | Agent 可讀寫 | 版本控制 | 開放標準 | 學習成本 |
|------|:---:|:---:|:---:|:---:|
| **Markdown** | ✅ 最佳 | ✅ 純文字 | ✅ | 極低 |
| **HTML** | ✅ 佳 | ✅ 純文字 | ✅ | 中 |
| **ODP** | ⚠️ XML | ⚠️ 二進位 | ✅ | 高 |
| **PPTX** | ⚠️ XML | ❌ 二進位 | ⚠️ | 高 |
| **LaTeX** | ✅ 佳 | ✅ 純文字 | ✅ | 高 |

**結論**：Markdown 和 HTML 是 Agent 最容易生成和修改的格式。

### 二、輸出格式：觀眾怎麼看到簡報

*研究日期：2026-04-29*

| 場景 | 推薦格式 | 原因 |
|------|---------|------|
| 自己現場播放 | HTML | 瀏覽器即可，動畫最豐富 |
| 寄給對方自己看 | PDF | 萬用，不走版 |
| 對方需要編輯 | PPTX | 業界通用 |
| 教學講義 | PDF | 學員可列印、標註 |
| 線上分享 | HTML | 一個連結搞定 |

**教學場景最佳組合**：HTML 播放 + PDF 講義 + PPTX 備用。

### 三、設計品質：Markdown 工具的天花板

*研究日期：2026-04-29*

| 需求 | Marp | reveal.js |
|------|:---:|:---:|
| 圖片嵌入 | ✅ | ✅ |
| 背景圖 | ✅ | ✅ |
| 圖文混排 | ⚠️ 需 CSS hack | ✅ 原生 |
| 元素自由定位 | ❌ | ✅ |
| 轉場動畫 | ⚠️ 有限 | ✅ 豐富 |
| 匯出 PPTX | ✅ 原生 | ❌ 不支援 |
| 匯出 PDF | ✅ 原生 | ✅ 透過列印 |
| 單一 HTML 檔 | ✅ | ✅ |

**關鍵差異**：reveal.js 設計自由度高但不能原生匯出 PPTX。如果需要 PPTX 輸出，Marp 是唯一同時支援 HTML/PDF/PPTX 的 Markdown 工具。

### 四、Agent 整合方式

*研究日期：2026-04-29*

#### 方式 A：Skill / Prompt 驅動（開源、免費）

Agent 直接生成 HTML 或 Markdown 檔案，不需要外部服務。

| 專案 | Stars | 輸出 | 授權 | 特色 |
|------|------:|------|------|------|
| [Frontend Slides](https://github.com/zarazhangrui/frontend-slides) | ~16k | 單一 HTML | MIT | 12 種精選風格、反 AI 罐頭美學、視覺預覽選風格 |
| [revealjs-skill](https://github.com/ryanbbrown/revealjs-skill) | ~279 | reveal.js HTML | MIT | 自動溢出偵測、截圖逐頁審查、Chart.js 圖表 |
| [keynot](https://github.com/shawnzam/keynot) | ~11 | 單一 HTML | MIT | 極簡、品牌指南自動提取、支援 40+ agent |
| [cc-slidev](https://github.com/rhuss/cc-slidev) | — | Slidev (Vue) | — | 開發者導向技術簡報 |
| [Anthropic pptx skill](https://github.com/anthropics/skills/tree/main/document-skills/pptx) | — | PPTX | — | 官方 skill，用 python-pptx 生成 |

> 這些本質都是一個 `SKILL.md` 檔案 — 純 prompt engineering，不綁定特定 Agent 平台。

#### 方式 B：MCP / API 串接（付費服務）

Agent 透過 MCP（Model Context Protocol）或 REST API 操作外部簡報服務。

| 服務 | MCP | API | 設計品質 | 輸出 | 備註 |
|------|:---:|:---:|:---:|------|------|
| [Gamma](https://developers.gamma.app) | ✅ | ✅ | ⭐⭐⭐ | 網頁/PPTX/PDF | 設計品質業界最高，Pro 方案起有 API |
| [Canva](https://www.canva.dev/docs/mcp/) | ✅ | ✅ | ⭐⭐⭐ | 各種格式 | 整個設計平台都能操作 |
| [Beautiful.ai](https://support.beautiful.ai/hc/en-us/articles/44246954338829) | ✅ | — | ⭐⭐⭐ | PPTX/PDF | 自動排版引擎 |
| [Plus AI](https://plusai.com/features/mcp) | ✅ | — | ⭐⭐ | Google Slides | 直接在 Google Slides 裡操作 |
| [Alai](https://getalai.com/blog/mcp-server-for-presentations) | ✅ | — | ⭐⭐ | PPTX/PDF | 建立簡報、生成講者備註 |
| [SlideSpeak](https://slidespeak.co/blog/2025/04/02/introducing-slidespeak-mcp-for-presentations/) | ✅ | — | ⭐⭐ | PPTX | 從文件摘要生成簡報 |
| [MagicSlides](https://www.magicslides.app/mcps/magic-slides-mcp-server) | ✅ | — | ⭐⭐ | PPTX | 從文字/YouTube/JSON 生成 |

#### 方式 C：完整應用（開源、自架）

| 專案 | Stars | 輸出 | 授權 | 特色 |
|------|------:|------|------|------|
| [Presenton](https://github.com/presenton/presenton) | ~4.8k | PPTX/PDF | Apache 2.0 | 自架 Gamma 替代品，HTML+Tailwind 自訂模板，有桌面 App |
| [PPTAgent / DeepPresenter](https://github.com/icip-cas/PPTAgent) | ~4.2k | PPTX | MIT | 學術研究（EMNLP 2025 / ACL 2026），有專用微調 9B 模型 |

#### Google Slides MCP

*研究日期：2026-04-29*

Google 在 2026 年 4 月開放了 [managed MCP servers](https://cloud.google.com/blog/products/ai-machine-learning/google-managed-mcp-servers-are-available-for-everyone)，但 Google Slides 尚未在官方 managed MCP 清單中。社群有第三方實作：

- [matteoantoci/google-slides-mcp](https://github.com/matteoantoci/google-slides-mcp)
- [michaelpolansky/google-slides-mcp](https://lobehub.com/mcp/michaelpolansky-google-slides-mcp)

### 五、其他關鍵考量

*研究日期：2026-04-29*

| 維度 | 本地方案（Marp/reveal.js） | 雲端服務（Gamma/Canva） |
|------|---------|---------|
| **隱私** | ✅ 內容不離開電腦 | ⚠️ 上傳第三方伺服器 |
| **中文排版** | 需自訂字體 | 通常有支援 |
| **迭代修改** | ✅ 改單頁即可 | ⚠️ 可能整份重生 |
| **離線使用** | ✅ | ❌ |
| **長期可用** | ✅ 5 年後還能開 | ⚠️ 服務可能關閉 |
| **成本** | 免費 | 月費制 |
| **協作** | ❌ 純文字檔 | ✅ 多人即時 |
| **品牌一致性** | 自訂 CSS 主題 | 模板/主題系統 |
| **演講輔助** | Presenter View、講者備註 | 依平台而定 |

---

## 決策地圖

```
你的簡報需要 PPTX 輸出嗎？
├─ 是 → 需要精美設計嗎？
│       ├─ 是 → Gamma API（付費）或 Presenton（自架）
│       └─ 否 → Marp ✅
└─ 否 → 需要精美設計嗎？
        ├─ 是 → Frontend Slides / keynot（HTML）
        └─ 否 → Marp ✅
```

## 結論：Marp 是當前最務實的選擇

**場景定調**：個人對外教學使用，需要考量播放設備相容性，能滿足基本簡報播放效果 + 能輸出 PDF/PPTX。

**為什麼選 Marp**：

1. **一份源檔，三種輸出** — Markdown → HTML（播放）+ PDF（講義）+ PPTX（備用）
2. **Agent 天生擅長 Markdown** — 生成和修改都極其自然
3. **版本控制友善** — 純文字，可以 git diff
4. **自訂 CSS 主題** — 確保教學簡報風格一致
5. **零依賴** — `npm install -g @marp-team/marp-cli` 就搞定
6. **長期可維護** — Markdown 永遠能讀，不怕工具停更

**升級路徑**：

- 需要更好的設計 → 串接 Gamma API 或移植 Frontend Slides 的 prompt
- 需要更多動畫 → 改用 reveal.js（犧牲 PPTX 輸出）
- 需要完全控制 → 自架 Presenton

## 工作流

```
提供教學主題 / 大綱
        ↓
  AI Agent 生成 Markdown（含講者備註）
        ↓
  ┌─────┼─────┐
  ↓     ↓     ↓
 HTML  PDF   PPTX
 播放   講義   備用
```

```bash
# 安裝
npm install -g @marp-team/marp-cli

# 生成
marp --theme theme-teaching.css --html  slide.md -o slide.html
marp --theme theme-teaching.css --pdf   slide.md -o slide.pdf
marp --theme theme-teaching.css --pptx  slide.md -o slide.pptx
```

## 本 Repo 檔案說明

| 檔案 | 說明 |
|------|------|
| `ai-agent-slides.md` | 簡報 Markdown 源檔 |
| `theme-teaching.css` | 自訂教學主題 CSS |
| `ai-agent-slides.html` | HTML 簡報（可直接瀏覽器播放） |
| `ai-agent-slides.pdf` | PDF 版本 |
| `ai-agent-slides.pptx` | PPTX 版本 |
| `README.md` | 本文件 — 完整研究資料 |

## 授權

本研究資料以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 授權釋出。

---

*本研究由 AI Agent（Kiro）協助完成，包含資料搜尋、方案比較、簡報生成。*
