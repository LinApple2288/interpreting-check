---
ctime: 2026-11-25 22:26
mtime: 2026-11-25 22:51
---

> 🌐 **语言 / Language**：[简体中文](#chinese) | [English](#english)

<h1 id="chinese">🎧 口译练习打卡 · 便利贴版</h1>

![项目形象：口译练习督促员](./banner-cutout.png)

一个为口译学习者设计的**网页练习打卡工具**。上传录音即可自动统计时长、生成日历热力图、管理每日目标与待办，并可为每段录音关联 AI 生成的复盘文档。整体采用温暖的黄色便利贴视觉风格，纯前端实现，无需服务器、无需联网、无需注册。

> 🔗 **在线体验**：<https://linapple2288.github.io/interpreting-check/>
>
> 📦 **GitHub 仓库**：<https://github.com/LinApple2288/interpreting-check>

---

## 🎯 目标用户

| 用户群体 | 典型场景 |
|---------|---------|
| 口译专业本科生 / MTI 研究生 | 备考 CATTI、考研复试，需要长期量化练习量 |
| 口译自学者 | 脱离课堂，缺少监督，需要可视化进度维持动力 |
| 口译教师 / 助教（轻量使用） | 查看学生阶段性练习趋势，辅助个性化指导 |

核心画像：**有持续练习意愿，但缺乏追踪与反馈机制的口译学习者**。

---

## 😣 实际问题

1. **练了多少说不清**——录音散落在电脑各处，时长靠手动累加，进度全凭感觉。
2. **坚持不下去**——没有即时反馈和视觉激励，目标遥不可及，容易半途而废。
3. **练习质量无法回溯**——分不清哪段是英译中、哪段是中译英，更记不住当时的表现问题。
4. **复盘文档与录音脱节**——用 AI 工具生成了复盘报告，却无法与对应录音关联，翻阅困难。
5. **现有打卡工具太重**——需要注册、联网、付费，对个人学习者不友好。

---

## ✨ 功能一览

```mermaid
flowchart LR
    A[上传录音] --> B[自动读取时长]
    B --> C[进度概览 / 周计划]
    B --> D[日历热力图]
    B --> E[录音条目管理]
    E --> F[方向 / 标签 / 日期筛选]
    E --> G[关联 docx 复盘]
    G --> H[弹窗预览 · 可放大]
    C --> I[Banner 动态督促语]
    J[侧栏] --> K[每日目标]
    J --> L[待办清单]
```

| 模块 | 说明 |
|-----|------|
| 🏠 Banner 督促区 | 卡通督促员形象 + 根据录音进度动态切换的标语 |
| ① 目标设置 | 设定总小时数、起止日期，支持个性化周期 |
| ② 进度概览 | 已录 / 剩余时长、剩余周数、每周需完成量、进度条 |
| ③ 上传录音 | 点击或拖拽上传，自动解析音频时长（精确到秒） |
| ④ 打卡热力图 | 月历视图，颜色深浅反映当日练习强度 |
| ⑤ 录音记录 | 编辑日期、翻译方向、表现标签，关联复盘文档 |
| 🎙️ 录音管理（侧栏） | 按语言类型 / 标签 / 日期范围筛选，查看总时长 |
| 📅 目标·待办（侧栏） | 本周每日目标追踪 + 待办清单（localStorage 持久化） |
| 📄 复盘预览 | 关联 WorkBuddy 生成的 .docx 文件，本地转换后弹窗预览 |

---

## 🚀 使用方法

### 1. 打开网页

访问 GitHub Pages 页面：<https://linapple2288.github.io/interpreting-check/>

无需安装任何环境，打开即用。数据保存在当前浏览器中。

### 2. 日常使用流程

1. 在「① 目标设置」填写总目标小时数与起止日期；
2. 把练习录音拖进「③ 上传录音」区域，系统自动识别时长；
3. 在录音条目中选择翻译方向（英译中 / 中译英）、填写表现标签；
4. 打开右侧栏「📅 目标 · 待办」查看本周每日目标，添加待办事项；
5. 在「🎙️ 录音管理」中按条件筛选，回顾特定类型练习；
6. 用 WorkBuddy 复盘 skill 生成 .docx 报告，点击录音条目的「📄 上传复盘」关联，点「👁 预览」查看，文档过大时可点「⤢ 放大」。

### 3. 数据说明

所有录音元数据、目标配置、待办与复盘文档均保存在**浏览器 localStorage**，不会上传到任何服务器。清除浏览器数据会导致本地记录丢失，重要数据请自行备份。

---

## 🤖 AI 工具

本项目的设计与开发过程中使用了以下 AI 能力：

| 工具 | 用途 |
|-----|------|
| **多模态内容生成（文生图）** | 生成 Banner 中的卡通督促员形象，与原参考图风格保持一致（黑发、圆框眼镜、耳机、向上指引手势） |
| **Python / PIL** | 对生成图片进行背景抠除、水印清理与边缘裁剪，得到透明 PNG 以融入页面 |
| **WorkBuddy / CodeBuddy 编程助手** | 完成全部 HTML / CSS / JavaScript 编码与多轮功能迭代 |
| **docx 技能** | 提供 .docx 文件结构解析与转换方案的技术参考，辅助选定本地预览实现路径 |
| **WorkBuddy 复盘 skill（用户侧）** | 用户将录音交由该 skill 生成 .docx 复盘报告，再通过半自动方式关联到本项目 |
| **mammoth.js**（开源库，非 AI） | 在浏览器本地将 .docx 转换为 HTML 实现预览，无需联网 |

> 说明：录音转写与 AI 自动复盘并非本项目内置功能。项目采用**半自动工作流**——由用户在本机 WorkBuddy 中完成复盘，再将结果文档导入页面，兼顾能力复用与本地隐私。

---

## 🗣️ 用户反馈与改进

以下内容整理自项目迭代过程中收集的真实使用反馈，每一条都直接推动了对应功能的落地。

### 反馈 1 · 用户 W（MATI 研究生）

> "页面一打开就是密密麻麻的表格，没有一点想练的冲动。我目标定的是 100 小时，但每次打开都忘了还差多少，能不能有个东西时不时督促我一下？"

**改进措施：**
- 生成卡通督促员插画并置于 Banner，与页面暖黄色便利贴风格统一；
- 新增**动态督促语**：未录音时提示"今天第一句，什么时候开录？"，录音不足 1 小时时提示"再加把劲，凑满 1 小时！"，超过 1 小时后提示"稳住节奏，向目标冲刺！"；
- 标语中的目标小时数与「目标设置」实时联动，修改目标后 Banner 自动同步。

---

### 反馈 2 · 用户 M（MASI 研究生）

> "录音一多就乱，分不清哪段是英译中、哪段是中译英，也不记得哪段表现有问题。侧栏东西堆在一起，找个筛选要滚半天，右上角那个圆按钮也不太好点。"

**改进措施：**
- 录音条目新增**翻译方向**下拉（英译中 / 中译英）与**自定义表现标签**输入框；
- 时长显示改为 `时:分:秒` 格式，精确到秒；
- 侧栏重构为两个 Tab：**「📅 目标 · 待办」**（每日目标与待办同列）和 **「🎙️ 录音管理」**（独立分区）；
- 录音管理支持语言类型、标签、日期范围三维筛选，默认显示全部时间，并可一键重置；
- 右上角圆形按钮改为**屏幕边缘竖向图标把手**，展开/收起更顺手；
- 录音记录与复盘文档纳入 localStorage 持久化，刷新不丢失。

---

### 反馈 3 · 用户 L（MASI 研究生）

> "我让 AI 帮我复盘生成了 Word 文档，但没法跟具体录音对上号。想在页面里直接看。"

**改进措施：**
- 每条录音支持**关联 .docx 复盘文档**，可更换、移除，删除录音时一并清理；
- 引入本地 mammoth.js，在浏览器内将 docx 转为 HTML **弹窗预览**，保留标题、表格等结构，完全离线；
- 侧栏录音列表中，带复盘的条目显示「📄 复盘」标记，可直接跳转预览。

---

## 📁 文件结构

```
.
├── index.html                  # 主页面（HTML + CSS + JavaScript 单文件）
├── banner-cutout.png           # Banner 插画（透明背景，页面实际使用）
├── banner-illustration.png     # 插画原图（保留存档）
├── mammoth.browser.min.js      # 本地 docx 预览依赖
└── README.md                   # 本文档
```

---

## 🔧 技术栈

- **HTML5 / CSS3**：响应式布局、便利贴视觉风格、Tab 分区、模态弹窗
- **原生 JavaScript**：状态管理、localStorage 持久化、音频元数据读取、筛选逻辑
- **Web Audio API**：`audio` 元素读取录音时长
- **mammoth.js**：浏览器端 docx → HTML 转换
- **零依赖后端**：纯静态页面，可直接部署至 GitHub Pages

---

## 📄 许可

本项目仅供个人学习与本地非商业使用。插画由 AI 生成，仅供本项目演示。

---

<h1 id="english">🎧 Interpreting Practice Check-in · Sticky Note Edition</h1>

![Project mascot: Interpreting practice supervisor](./banner-cutout.png)

A **web-based practice check-in tool** designed for interpreting learners. Upload recordings to automatically count duration, generate a calendar heatmap, manage daily goals and to-dos, and link AI-generated review documents to each recording. It uses a warm yellow sticky-note visual style, is pure front-end, and requires no server, no internet and no sign-up.

> 🔗 **Try it online**: <https://linapple2288.github.io/interpreting-check/>
>
> 📦 **GitHub repository**: <https://github.com/LinApple2288/interpreting-check>

---

## 🎯 Target Users

| User group | Typical scenario |
|---------|---------|
| Interpreting undergraduates / MTI graduates | Preparing for CATTI or graduate entrance re-exams, needing long-term quantified practice |
| Self-taught interpreting learners | Away from class, lacking supervision, needing visible progress to stay motivated |
| Interpreting teachers / TAs (light use) | Reviewing students' practice trends over time to support personalized guidance |

Core profile: **interpreting learners who want to keep practicing but lack tracking and feedback mechanisms**.

---

## 😣 Problems It Solves

1. **Unclear how much has been practiced** — recordings are scattered across the computer, hours are added up by hand, and progress is just a feeling.
2. **Hard to keep going** — no instant feedback or visual encouragement; goals feel far away and it is easy to give up.
3. **Practice quality cannot be reviewed** — hard to tell which recording is EN→CN or CN→EN, and easy to forget the performance issues at the time.
4. **Review documents are detached from recordings** — AI-generated review reports cannot be matched to the recordings they belong to.
5. **Existing check-in tools are too heavy** — they require sign-up, internet and payment, which is unfriendly to individual learners.

---

## ✨ Features

```mermaid
flowchart LR
    A[Upload recording] --> B[Auto-read duration]
    B --> C[Progress / weekly plan]
    B --> D[Calendar heatmap]
    B --> E[Recording management]
    E --> F[Direction / tag / date filter]
    E --> G[Link docx review]
    G --> H[Popup preview · zoomable]
    C --> I[Dynamic banner slogan]
    J[Sidebar] --> K[Daily goals]
    J --> L[To-do list]
```

| Module | Description |
|-----|------|
| 🏠 Banner encouragement area | Cartoon supervisor mascot + slogans that switch based on recording progress |
| ① Goal settings | Set total hours and start/end dates, supports custom periods |
| ② Progress overview | Recorded / remaining hours, weeks left, weekly requirement, progress bar |
| ③ Upload recordings | Click or drag to upload, auto-reads audio duration (accurate to the second) |
| ④ Check-in heatmap | Monthly calendar view, color depth reflects daily practice intensity |
| ⑤ Recording records | Edit date, translation direction, performance tags, link review documents |
| 🎙️ Recording management (sidebar) | Filter by language type / tag / date range, view total duration |
| 📅 Goals & To-dos (sidebar) | Weekly daily goal tracking + to-do list (saved in localStorage) |
| 📄 Review preview | Link .docx files generated by WorkBuddy, preview locally in a popup |

---

## 🚀 How to Use

### 1. Open the page

Visit the GitHub Pages site: <https://linapple2288.github.io/interpreting-check/>

No installation needed, just open and use. Data is saved in the current browser.

### 2. Daily workflow

1. In "① Goal settings", enter the total target hours and start/end dates;
2. Drag practice recordings into the "③ Upload recordings" area; duration is detected automatically;
3. For each recording, choose the translation direction (EN→CN / CN→EN) and fill in performance tags;
4. Open the sidebar "📅 Goals · To-dos" to check daily goals and add to-dos;
5. In "🎙️ Recording management", filter by conditions to review specific types of practice;
6. Generate a .docx report with the WorkBuddy review skill, click "📄 Upload review" on the recording to link it, click "👁 Preview" to read it, and click "⤢ Zoom" if the document is large.

### 3. Data note

All recording metadata, goal settings, to-dos and review documents are saved in **browser localStorage** and are never uploaded to any server. Clearing browser data will delete local records, so please back up important data yourself.

---

## 🤖 AI Tools

The following AI capabilities were used in the design and development of this project:

| Tool | Purpose |
|-----|------|
| **Multimodal generation (text-to-image)** | Generated the cartoon supervisor mascot in the banner, matching the reference style (black hair, round glasses, headphones, upward pointing gesture) |
| **Python / PIL** | Removed the background, cleaned the watermark and trimmed edges of the generated image into a transparent PNG |
| **WorkBuddy / CodeBuddy coding assistant** | Wrote all HTML / CSS / JavaScript code and supported multiple rounds of feature iteration |
| **docx skill** | Provided technical reference on .docx structure and conversion options to help choose the local preview approach |
| **WorkBuddy review skill (user side)** | The user feeds recordings to this skill to generate .docx review reports, then links them to this project semi-automatically |
| **mammoth.js** (open-source library, not AI) | Converts .docx to HTML locally in the browser for preview, no internet needed |

> Note: Audio transcription and AI auto-review are not built-in features. The project uses a **semi-automatic workflow** — the user completes the review in WorkBuddy locally and imports the result into the page, balancing capability reuse with local privacy.

---

## 🗣️ User Feedback & Improvements

The following is real feedback collected during project iteration, and each item directly led to a feature improvement.

### Feedback 1 · User W (MATI graduate student)

> "The page is just dense tables when you open it — it doesn't make me want to practice. My goal is 100 hours, but every time I open it I forget how much is left. Can something remind me from time to time?"

**Improvements:**
- Generated a cartoon supervisor illustration and placed it in the banner, matching the warm yellow sticky-note style;
- Added **dynamic encouragement slogans**: when there is no recording "Today's first line — when will you start?", when under 1 hour "Keep going, make it 1 hour!", when over 1 hour "Keep the pace, sprint to the goal!";
- The goal hours in the slogan are linked live to "Goal settings" and update automatically when the goal changes.

---

### Feedback 2 · User M (MASI graduate student)

> "When there are many recordings it gets messy — I can't tell which is EN→CN and which is CN→EN, and I don't remember the performance issues. Everything is piled up in the sidebar, filtering takes forever, and that round button in the corner is hard to click."

**Improvements:**
- Added a **translation direction** dropdown (EN→CN / CN→EN) and a **custom performance tag** input to each recording;
- Changed duration display to `HH:MM:SS`, accurate to the second;
- Restructured the sidebar into two tabs: **"📅 Goals · To-dos"** (daily goals and to-dos in one column) and **"🎙️ Recording management"** (a separate section);
- Recording management supports three-way filtering by language type, tag and date range, defaults to all time, and has a one-click reset;
- Replaced the round corner button with a **vertical icon handle on the screen edge**, easier to open and close;
- Recording records and review documents are saved in localStorage and survive refresh.

---

### Feedback 3 · User L (MASI graduate student)

> "I had AI generate a Word review document but couldn't match it to the right recording. I want to read it directly in the page."

**Improvements:**
- Each recording supports **linking a .docx review document**, which can be replaced or removed, and is cleaned up when the recording is deleted;
- Added local mammoth.js to convert docx to HTML for **popup preview**, preserving headings, tables and other structure, fully offline;
- In the sidebar recording list, entries with reviews show a "📄 Review" marker that opens the preview directly.

---

## 📁 File Structure

```
.
├── index.html                  # Main page (single HTML + CSS + JavaScript file)
├── banner-cutout.png           # Banner illustration (transparent background, used by the page)
├── banner-illustration.png     # Original illustration (kept as archive)
├── mammoth.browser.min.js      # Local docx preview dependency
└── README.md                   # This document
```

---

## 🔧 Tech Stack

- **HTML5 / CSS3**: responsive layout, sticky-note visual style, tab sections, modal popup
- **Vanilla JavaScript**: state management, localStorage persistence, audio metadata reading, filtering logic
- **Web Audio API**: `audio` element reads recording duration
- **mammoth.js**: browser-side docx → HTML conversion
- **No backend dependency**: pure static page, deployable directly to GitHub Pages

---

## 📄 License

This project is for personal study and local non-commercial use only. The illustration is AI-generated and is for demonstration in this project only.
