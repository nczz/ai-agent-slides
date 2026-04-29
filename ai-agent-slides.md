---
marp: true
theme: teaching
paginate: true
---

<!-- _class: lead -->
<!-- _paginate: false -->

# AI Agent 製作簡報的選擇

從格式、工具到工作流的完整評估

2026.04

---

# 今天要回答的問題

當你想用 AI Agent（Kiro、Claude Code、Cursor…）來製作簡報時：

1. **源檔格式**該選什麼？
2. **輸出格式**怎麼決定？
3. 有哪些**開源工具**可以用？
4. 有哪些**付費服務**可以串接？
5. 怎麼選最適合自己的方案？

---

<!-- _class: section-divider -->

# 📐 維度一：源檔格式

開源 × 通用 × Agent 友善

---

# 源檔格式比較

| 格式 | Agent 可讀寫 | 版本控制 | 開放標準 | 學習成本 |
|------|:---:|:---:|:---:|:---:|
| **Markdown** | ✅ 最佳 | ✅ 純文字 | ✅ | 極低 |
| **HTML** | ✅ 佳 | ✅ 純文字 | ✅ | 中 |
| **ODP** | ⚠️ XML | ⚠️ 二進位 | ✅ | 高 |
| **PPTX** | ⚠️ XML | ❌ 二進位 | ⚠️ | 高 |
| **LaTeX** | ✅ 佳 | ✅ 純文字 | ✅ | 高 |

> **結論**：Markdown 和 HTML 是 Agent 最容易生成和修改的格式

---

<!-- _class: section-divider -->

# 🖥️ 維度二：輸出格式

你的觀眾怎麼看到這份簡報？

---

# 輸出格式的選擇邏輯

| 場景 | 推薦格式 | 原因 |
|------|---------|------|
| 自己現場播放 | **HTML** | 瀏覽器即可，動畫最豐富 |
| 寄給對方自己看 | **PDF** | 萬用，不走版 |
| 對方需要編輯 | **PPTX** | 業界通用 |
| 教學講義 | **PDF** | 學員可列印、標註 |
| 線上分享 | **HTML** | 一個連結搞定 |

> **教學場景最佳組合**：HTML 播放 + PDF 講義 + PPTX 備用

---

<!-- _class: section-divider -->

# 🎨 維度三：設計品質

色塊文字 vs 有設計感的簡報

---

# 設計能力光譜

```
簡潔文字 ◄──────────────────────────────► 精美設計

  Marp          reveal.js        Gamma / Canva
  純 Markdown    HTML + CSS       AI 自動排版
  乾淨但樸素     自由但要寫 CSS    精美但依賴雲端
```

**教學簡報的真相**：
- 內容清晰 > 視覺炫技
- 字夠大、結構分明 > 精美插圖
- 一致的風格 > 每頁不同設計

---

# Marp vs reveal.js 設計能力

| 需求 | Marp | reveal.js |
|------|:---:|:---:|
| 圖片嵌入 | ✅ | ✅ |
| 背景圖 | ✅ | ✅ |
| 圖文混排 | ⚠️ CSS hack | ✅ 原生 |
| 元素自由定位 | ❌ | ✅ |
| 轉場動畫 | ⚠️ 有限 | ✅ 豐富 |
| 匯出 PPTX | ✅ 原生 | ❌ |
| 匯出 PDF | ✅ 原生 | ✅ 列印 |
| 單一 HTML | ✅ | ✅ |

> reveal.js 設計自由度高，但**不能原生匯出 PPTX**

---

<!-- _class: section-divider -->

# 🤖 維度四：Agent 整合方式

Skill/Prompt vs MCP vs API

---

# 三種整合模式

**① Skill / Prompt 驅動**
Agent 直接生成 HTML/Markdown 檔案，不需要外部服務

**② MCP（Model Context Protocol）**
Agent 透過標準協議操作外部簡報服務

**③ REST API**
Agent 呼叫 HTTP API 生成簡報

---

# 開源 Skill/Prompt 專案

| 專案 | ⭐ Stars | 輸出 | 特色 |
|------|---------|------|------|
| **Frontend Slides** | 16k | 單一 HTML | 12 種風格、反 AI 罐頭美學 |
| **revealjs-skill** | 279 | reveal.js | 溢出偵測、Chart.js 圖表 |
| **keynot** | 11 | 單一 HTML | 極簡、品牌指南自動提取 |
| **cc-slidev** | — | Slidev | 開發者技術簡報 |

> 本質都是一個 `SKILL.md` — 純 prompt engineering，不綁定特定 Agent

---

# 付費 MCP / API 服務

| 服務 | MCP | API | 設計品質 | 輸出 |
|------|:---:|:---:|---------|------|
| **Gamma** | ✅ | ✅ | ⭐⭐⭐ 最高 | 網頁/PPTX/PDF |
| **Canva** | ✅ | ✅ | ⭐⭐⭐ | 各種格式 |
| **Beautiful.ai** | ✅ | — | ⭐⭐⭐ | PPTX/PDF |
| **Plus AI** | ✅ | — | ⭐⭐ | Google Slides |
| **SlideSpeak** | ✅ | — | ⭐⭐ | PPTX |

> Gamma 的 API 最簡單：丟文字進去 → 非同步拿回精美簡報

---

<!-- _class: section-divider -->

# 🔒 維度五：其他關鍵考量

隱私、中文、迭代、長期性

---

# 容易忽略的評估維度

| 維度 | 本地方案 | 雲端服務 |
|------|---------|---------|
| **隱私** | ✅ 內容不離開電腦 | ⚠️ 上傳第三方 |
| **中文排版** | 需自訂字體 | 通常有支援 |
| **迭代修改** | ✅ 改單頁即可 | ⚠️ 可能整份重生 |
| **離線使用** | ✅ | ❌ |
| **長期可用** | ✅ 5 年後還能開 | ⚠️ 服務可能關閉 |
| **成本** | 免費 | 月費制 |
| **協作** | ❌ 純文字檔 | ✅ 多人即時 |

---

<!-- _class: section-divider -->

# 🗺️ 決策地圖

根據你的場景選方案

---

# 怎麼選？

```
你的簡報需要 PPTX 輸出嗎？
├─ 是 → 需要精美設計嗎？
│       ├─ 是 → Gamma API（付費）或 Presenton（自架）
│       └─ 否 → Marp ✅
└─ 否 → 需要精美設計嗎？
        ├─ 是 → Frontend Slides / keynot（HTML）
        └─ 否 → Marp ✅
```

**教學場景推薦**：**Marp**
- 一份 Markdown → HTML + PDF + PPTX 三種輸出
- Agent 天生擅長生成 Markdown
- 自訂 CSS 主題確保風格一致

---

# Marp 工作流示範

```
你提供教學主題 / 大綱
        ↓
  Kiro 生成 Markdown
   （含講者備註）
        ↓
  ┌─────┼─────┐
  ↓     ↓     ↓
 HTML  PDF   PPTX
 播放   講義   備用
```

```bash
marp --html  slide.md    # 瀏覽器播放
marp --pdf   slide.md    # 學員講義
marp --pptx  slide.md    # PPT 備用
```

---

# 這份簡報本身就是用 Marp 做的

源檔：一個 `.md` 檔 + 一個 `.css` 主題

```markdown
---
marp: true
theme: teaching
paginate: true
---

# 標題

內容用標準 Markdown 語法
```

> 你現在看到的每一頁，都是 Kiro 生成的 Markdown

---

<!-- _class: section-divider -->

# 📋 總結

---

# 方案總覽

| 方案 | 適合場景 | 設計 | 成本 | PPTX |
|------|---------|:---:|:---:|:---:|
| **Marp** | 教學、技術分享 | ⭐⭐ | 免費 | ✅ |
| **reveal.js** | 需要動畫的演講 | ⭐⭐⭐ | 免費 | ❌ |
| **Frontend Slides** | 精美 HTML 簡報 | ⭐⭐⭐ | 免費 | ❌ |
| **Gamma** | 商業提案、客戶簡報 | ⭐⭐⭐ | 付費 | ✅ |
| **Presenton** | 自架、完全控制 | ⭐⭐⭐ | 免費 | ✅ |

**個人教學推薦**：從 Marp 開始，不夠再升級

---

<!-- _class: end -->
<!-- _paginate: false -->

# 謝謝

用 AI Agent + Marp 製作
源檔是 Markdown，你也可以

