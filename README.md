<p align="center">
  <img src="https://em-content.zobj.net/source/apple/391/rock_1faa8.png" width="120" />
</p>

<h1 align="center">caveman</h1>

<p align="center">
  <strong>ทำไมต้องใช้ token เยอะ ในเมื่อน้อยก็พอ</strong>
</p>

<p align="center">
  <a href="https://github.com/JuliusBrussee/caveman/stargazers"><img src="https://img.shields.io/github/stars/JuliusBrussee/caveman?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/JuliusBrussee/caveman/commits/main"><img src="https://img.shields.io/github/last-commit/JuliusBrussee/caveman?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/JuliusBrussee/caveman?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#before--after">Before/After</a> •
  <a href="#install">ติดตั้ง</a> •
  <a href="#intensity-levels">ระดับ</a> •
  <a href="#caveman-skills">Skills</a> •
  <a href="#benchmarks">Benchmarks</a> •
  <a href="#evals">Evals</a>
</p>

<p align="center">
  <strong>🪨 Caveman Ecosystem</strong> &nbsp;·&nbsp;
  <strong>caveman</strong> <em>พูดน้อย</em> <sub>(คุณอยู่ที่นี่)</sub> &nbsp;·&nbsp;
  <a href="https://github.com/JuliusBrussee/cavemem">cavemem</a> <em>จำได้มากขึ้น</em> &nbsp;·&nbsp;
  <a href="https://github.com/JuliusBrussee/cavekit">cavekit</a> <em>สร้างได้ดีขึ้น</em>
</p>

---

skill/plugin สำหรับ [Claude Code](https://docs.anthropic.com/en/docs/claude-code) และ plugin สำหรับ Codex ที่ทำให้ agent พูดแบบคนถ้ำ — ลด **~75% ของ output tokens** โดยยังคงความถูกต้องทางเทคนิคครบถ้วน รองรับ [โหมด 文言文](#文言文-wenyan-mode), [commit กระชับ / review บรรทัดเดียว / สถิติตลอดชีพ](#caveman-skills) และ [เครื่องมือบีบอัด](#caveman-compress-receipts) ที่ลด **~46% ของ input tokens** ทุก session

มาจากการค้นพบที่แพร่หลายว่าการพูดแบบคนถ้ำลดการใช้ token ของ LLM ได้อย่างมากโดยไม่สูญเสียสาระเทคนิค เราจึงทำให้ติดตั้งได้ด้วยคำสั่งเดียว

## Before / After

<table>
<tr>
<td width="50%">

### 🗣️ Claude ปกติ (69 tokens)

> "The reason your React component is re-rendering is likely because you're creating a new object reference on each render cycle. When you pass an inline object as a prop, React's shallow comparison sees it as a different object every time, which triggers a re-render. I'd recommend using useMemo to memoize the object."

</td>
<td width="50%">

### 🪨 Caveman Claude (19 tokens)

> "New object ref each render. Inline object prop = new ref = re-render. Wrap in `useMemo`."

</td>
</tr>
<tr>
<td>

### 🗣️ Claude ปกติ

> "Sure! I'd be happy to help you with that. The issue you're experiencing is most likely caused by your authentication middleware not properly validating the token expiry. Let me take a look and suggest a fix."

</td>
<td>

### 🪨 Caveman Claude

> "Bug in auth middleware. Token expiry check use `<` not `<=`. Fix:"

</td>
</tr>
</table>

**แก้เหมือนกัน ใช้คำน้อยกว่า 75% แต่สมองยังใหญ่เท่าเดิม**

**เลือกระดับความดึกดำบรรพ์ของคุณ:**

<table>
<tr>
<td width="25%">

#### 🪶 Lite

> "Your component re-renders because you create a new object reference each render. Inline object props fail shallow comparison every time. Wrap it in `useMemo`."

</td>
<td width="25%">

#### 🪨 Full

> "New object ref each render. Inline object prop = new ref = re-render. Wrap in `useMemo`."

</td>
<td width="25%">

#### 🔥 Ultra

> "Inline obj prop → new ref → re-render. `useMemo`."

</td>
<td width="25%">

#### 📜 文言文

> "物出新參照，致重繪。useMemo Wrap之。"

</td>
</tr>
</table>

**คำตอบเหมือนกัน แค่เลือกว่าจะใช้คำเท่าไหร่**

```
┌─────────────────────────────────────┐
│  TOKENS SAVED          ████████ 75% │
│  TECHNICAL ACCURACY    ████████ 100%│
│  SPEED INCREASE        ████████ ~3x │
│  VIBES                 ████████ OOG │
└─────────────────────────────────────┘
```

- **ตอบเร็วขึ้น** — generate token น้อย = เร็วฉิบ
- **อ่านง่ายขึ้น** — ไม่มีกำแพงข้อความ ได้คำตอบตรงๆ
- **ความแม่นยำเท่าเดิม** — ข้อมูลเทคนิคครบ ตัดแค่ส่วนเกิน ([มีงานวิจัยรองรับ](https://arxiv.org/abs/2604.00025))
- **ประหยัดเงิน** — ลด output เฉลี่ย 65% จาก [benchmark ของเรา](#benchmarks) (ช่วง 22-87%)
- **สนุก** — code review ทุกอันกลายเป็นความบันเทิง

## ติดตั้ง

**บรรทัดเดียว ตรวจจับทุก agent ติดตั้งให้ทันที**

```bash
# macOS / Linux / WSL / Git Bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash

# Windows (PowerShell)
irm https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.ps1 | iex
```

ตรวจจับได้ 30+ agent (Claude Code, Gemini CLI, Codex, Cursor, Windsurf, Cline, Copilot, Continue, Kilo, Roo, Augment, Aider Desk, Amp, Bob, Crush, Devin, Droid, ForgeCode, Goose, iFlow, JetBrains Junie, Kiro CLI, Mistral Vibe, OpenHands, opencode, Qwen Code, Qoder, Rovo Dev, Tabnine, Trae, Warp, Replit Agent, Antigravity, …) รันการติดตั้งแบบ native ของแต่ละตัว ข้ามสิ่งที่ไม่มี รันซ้ำได้อย่างปลอดภัย

ค่าเริ่มต้น: installer เชื่อม hooks + statusline + stats badge ของ Claude Code และลงทะเบียน MCP proxy [`caveman-shrink`](#caveman-shrink-mcp-middleware) ต่อท้าย plugin install ใช้ `--minimal` เพื่อข้ามส่วนเสริมและติดตั้งแค่ plugin/extension ใช้ `--all` เพื่อเพิ่ม rule files ต่อ repo ในไดเรกทอรีปัจจุบัน

| Flag | ทำอะไร |
|---|---|
| `--all` | Plugin + hooks + statusline + MCP shrink + per-repo rule files ใน `$PWD` ครบทุกอย่าง |
| `--minimal` | แค่ plugin/extension ไม่มี hooks, MCP shrink, per-repo rules |
| `--dry-run` | ดูตัวอย่าง ไม่เขียนไฟล์ |
| `--only <agent>` | เลือก target เดียว (ใช้ซ้ำได้) |
| `--with-hooks` | Claude Code: เชื่อม standalone hooks + statusline + stats badge **เปิดอยู่ตามค่าเริ่มต้น** |
| `--with-mcp-shrink` | Claude Code: ลงทะเบียน MCP proxy [caveman-shrink](#caveman-shrink-mcp-middleware) ผ่าน `npx caveman-shrink` **เปิดอยู่ตามค่าเริ่มต้น** |
| `--with-init` | วาง rule files แบบ always-on ลงใน repo ปัจจุบัน (Cursor / Windsurf / Cline / Copilot / AGENTS.md) ปิดอยู่ตามค่าเริ่มต้น เปิดได้ด้วย `--all` |
| `--list` | แสดง agent matrix ทั้งหมดแล้วออก |
| `--force` | รันใหม่แม้ติดตั้งไปแล้ว |

`install.sh --help` สำหรับ reference เต็ม

**ติดตั้งแบบ manual ต่อ agent:**

| Agent | คำสั่ง |
|---|---|
| **Claude Code** | `claude plugin marketplace add JuliusBrussee/caveman && claude plugin install caveman@caveman` |
| **Gemini CLI** | `gemini extensions install https://github.com/JuliusBrussee/caveman` |
| **Cursor / Windsurf / Cline / Copilot** | `npx skills add JuliusBrussee/caveman -a <cursor\|windsurf\|cline\|github-copilot>` |
| **Codex / opencode / Roo / Amp / Goose / Kiro / Augment / Aider Desk / Continue / Kilo / Junie / Trae / Warp / Tabnine / Mistral / Qwen / Devin / Droid / ForgeCode / Bob / Crush / iFlow / OpenHands / Qoder / Rovo Dev / Replit / Antigravity** | `npx skills add JuliusBrussee/caveman -a <profile>` (ดู `install.sh --list` สำหรับ slug list ครบ) |
| **อื่นๆ (40+ agent)** | `npx skills add JuliusBrussee/caveman` (auto-detect) |

hooks สำหรับ Claude Code แบบ standalone (ไม่ต้องมี plugin): `bash <(curl -s https://raw.githubusercontent.com/JuliusBrussee/caveman/main/hooks/install.sh)` Windows: `irm https://raw.githubusercontent.com/JuliusBrussee/caveman/main/hooks/install.ps1 | iex` วิธีทำ manual สำหรับ Windows ที่ดื้อเป็นพิเศษอยู่ใน [`docs/install-windows.md`](docs/install-windows.md)

ถอนการติดตั้ง: ปิด Claude plugin, `gemini extensions uninstall caveman` หรือ `npx skills remove caveman`

### สิ่งที่คุณได้รับ

| ฟีเจอร์ | Claude Code | Codex | Gemini CLI | Cursor / Windsurf | Cline / Copilot | อื่นๆ* |
|---|:-:|:-:|:-:|:-:|:-:|:-:|
| Caveman mode | Y | Y | Y | Y | Y | Y |
| เปิดอัตโนมัติทุก session | Y | Y¹ | Y | ต้องใช้ `--with-init` | ต้องใช้ `--with-init` | ต้องใช้ `--with-init` |
| คำสั่ง `/caveman` | Y | Y¹ | Y | — | — | — |
| สลับโหมด (lite/full/ultra) | Y | Y¹ | Y | Y² | — | — |
| Statusline badge | Y | — | — | — | — | — |
| caveman-commit / caveman-review | Y | — | Y | Y | Y | Y |
| caveman-compress / caveman-help | Y | Y³ | Y | Y | Y | Y |
| caveman-stats | Y | — | — | — | — | — |
| cavecrew (subagents) | Y | — | — | — | — | — |

\* opencode, Roo, Amp, Goose, Kiro CLI, Augment, Aider Desk, Continue, Kilo, Junie (JetBrains), Trae, Warp, Tabnine, Mistral, Qwen, Devin, Droid, ForgeCode, Bob, Crush, iFlow, OpenHands, Qoder, Rovo Dev, Replit, Antigravity และอื่นๆ ผ่าน `npx skills` AGENTS.md / IDE rule files รองรับ Zed และ agent ทั่วไปผ่าน `--with-init`
¹ Codex ใช้ `$caveman` แทน `/caveman` การเปิดอัตโนมัติใช้งานได้เมื่อรัน Codex ภายใน repo นี้ (ผ่าน `.codex/hooks.json`) สำหรับ repo อื่น คัดลอก hook หรือใช้ `$caveman` เอง ² การสลับโหมดเป็นแบบ on-demand ผ่าน skill ไม่มี slash command ³ Compress เท่านั้น

`--with-init` เขียน `.cursor/rules/caveman.mdc`, `.windsurf/rules/caveman.md`, `.clinerules/caveman.md`, `.github/copilot-instructions.md` และ `AGENTS.md` ลงใน repo ปัจจุบัน ให้ caveman เปิดอัตโนมัติที่นั่น

## การใช้งาน

เปิดใช้ด้วย:
- `/caveman` หรือ Codex `$caveman`
- "talk like caveman"
- "caveman mode"
- "less tokens please"

หยุดด้วย: "stop caveman" หรือ "normal mode"

### ระดับความเข้ม

| ระดับ | ตัวกระตุ้น | ทำอะไร |
|-------|---------|------------|
| **Lite** | `/caveman lite` | ตัดคำฟุ่มเฟือย คงไวยากรณ์ เป็นมืออาชีพแต่ไม่มีส่วนเกิน |
| **Full** | `/caveman full` | caveman มาตรฐาน ตัด articles พูดเป็น fragments เต็มที่ |
| **Ultra** | `/caveman ultra` | บีบอัดสูงสุด กระชับแบบโทรเลข ย่อทุกอย่าง |

### โหมด 文言文 (Wenyan)

การบีบอัดด้วยภาษาจีนคลาสสิก — ความแม่นยำเทคนิคเท่าเดิม แต่ในภาษาเขียนที่ประหยัด token ที่สุดในประวัติศาสตร์มนุษย์

| ระดับ | ตัวกระตุ้น | ทำอะไร |
|-------|---------|------------|
| **Wenyan-Lite** | `/caveman wenyan-lite` | กึ่งคลาสสิก คงโครงสร้างประโยค ตัดส่วนเกิน |
| **Wenyan-Full** | `/caveman wenyan` | 文言文 เต็มรูปแบบ กระชับแบบคลาสสิกสูงสุด |
| **Wenyan-Ultra** | `/caveman wenyan-ultra` | สุดขีด นักปราชญ์โบราณรัดเข็มขัด |

ระดับจะคงอยู่จนกว่าจะเปลี่ยนหรือจบ session

## Caveman Skills

| Skill | ทำอะไร |
|---|---|
| `/caveman-commit` | commit message กระชับ Conventional Commits หัวข้อ ≤50 ตัวอักษร เน้น "ทำไม" มากกว่า "ทำอะไร" |
| `/caveman-review` | PR comment บรรทัดเดียว: `L42: 🔴 bug: user null. Add guard.` ไม่มีการกล่าวนำ |
| `/caveman-help` | การ์ดอ้างอิงด่วน ทุกโหมด skills และคำสั่ง |
| `/caveman-stats` | การใช้ token จริงต่อ session + ประมาณการประหยัด + USD รวมตลอดชีพผ่าน `--all` กรองช่วงเวลาผ่าน `--since 7d` บรรทัดแชร์ผ่าน `--share` อ่าน JSONL ของ Claude Code โดยตรง ไม่เดาจาก model Claude Code เท่านั้น |
| `/caveman:compress <file>` | เขียน memory file ใหม่ (เช่น `CLAUDE.md`) ให้เป็น caveman-speak สำรองไฟล์เดิมเป็น `<file>.original.md` ลด *input* tokens ~46% ทุกครั้งที่เริ่ม session โค้ด/URL/path คงอยู่ครบทุกไบต์ |
| `cavecrew-investigator/builder/reviewer` | subagent แบบ caveman สำหรับ Claude Code output ของ subagent ถูกฉีดกลับ main context — ส่ง token น้อยกว่า agent vanilla `Explore` / reviewer ~60% ทำให้ main context อยู่ได้นานขึ้นใน session ยาว Investigator (ค้นหาแบบ read-only, haiku), builder (แก้ไขแม่นยำ 1-2 ไฟล์ ปฏิเสธ 3+), reviewer (ผลลัพธ์บรรทัดเดียว, haiku) |

**Statusline savings badge** — เปิดอยู่ตามค่าเริ่มต้น หลังรัน `/caveman-stats` ครั้งแรก statusline จะเพิ่ม `[CAVEMAN] ⛏ 12.4k` (token ที่ประหยัดได้ตลอดชีพ) และอัปเดตทุกครั้งที่รัน `/caveman-stats` ไม่ต้องการ? ตั้ง `CAVEMAN_STATUSLINE_SAVINGS=0` เพื่อปิด

### ผลลัพธ์ caveman-compress

| ไฟล์ | ต้นฉบับ | หลังบีบอัด | ประหยัด |
|---|---:|---:|---:|
| `claude-md-preferences.md` | 706 | 285 | **59.6%** |
| `project-notes.md` | 1145 | 535 | **53.3%** |
| `claude-md-project.md` | 1122 | 636 | **43.3%** |
| `todo-list.md` | 627 | 388 | **38.1%** |
| `mixed-with-code.md` | 888 | 560 | **36.9%** |
| **เฉลี่ย** | **898** | **481** | **46%** |

เอกสารฉบับเต็ม: [caveman-compress README](caveman-compress/README.md) [หมายเหตุ Snyk false-positive](./caveman-compress/SECURITY.md)

## caveman-shrink (MCP middleware)

Stdio proxy ที่ครอบ MCP server ใดก็ได้ ดัก `tools/list` / `prompts/list` / `resources/list` responses แล้วบีบอัด field `description` โค้ด, URL, path, identifier คงอยู่ครบทุกไบต์

```jsonc
{
  "mcpServers": {
    "fs-shrunk": {
      "command": "npx",
      "args": ["caveman-shrink", "npx", "@modelcontextprotocol/server-filesystem", "/path/to/dir"]
    }
  }
}
```

เผยแพร่บน npm ในชื่อ [`caveman-shrink`](https://www.npmjs.com/package/caveman-shrink) V1 ยังไม่แตะ response body ของ tool-call หรือ request payload ลงทะเบียนอัตโนมัติโดย `install.sh` (ใช้ `--minimal` เพื่อข้าม) เอกสารฉบับเต็ม: [`mcp-servers/caveman-shrink/`](mcp-servers/caveman-shrink)

## Benchmarks

จำนวน token จริงจาก Claude API ([ทดสอบเองได้](benchmarks/)):

<!-- BENCHMARK-TABLE-START -->
| งาน | ปกติ (tokens) | Caveman (tokens) | ประหยัด |
|------|---------------:|----------------:|------:|
| Explain React re-render bug | 1180 | 159 | 87% |
| Fix auth middleware token expiry | 704 | 121 | 83% |
| Set up PostgreSQL connection pool | 2347 | 380 | 84% |
| Explain git rebase vs merge | 702 | 292 | 58% |
| Refactor callback to async/await | 387 | 301 | 22% |
| Architecture: microservices vs monolith | 446 | 310 | 30% |
| Review PR for security issues | 678 | 398 | 41% |
| Docker multi-stage build | 1042 | 290 | 72% |
| Debug PostgreSQL race condition | 1200 | 232 | 81% |
| Implement React error boundary | 3454 | 456 | 87% |
| **เฉลี่ย** | **1214** | **294** | **65%** |

*ช่วง: ประหยัด 22%–87% ตาม prompt ต่างๆ*
<!-- BENCHMARK-TABLE-END -->

> [!IMPORTANT]
> caveman กระทบเฉพาะ output tokens — thinking/reasoning tokens ไม่ถูกแตะ caveman ไม่ได้ทำให้สมองเล็กลง caveman ทำให้ *ปาก* เล็กลง ชัยชนะที่ใหญ่ที่สุดคือ **ความอ่านง่ายและความเร็ว** ส่วนการประหยัดเงินเป็นโบนัส

งานวิจัยเดือนมีนาคม 2026 ["Brevity Constraints Reverse Performance Hierarchies in Language Models"](https://arxiv.org/abs/2604.00025) พบว่าการบังคับให้ model ใหญ่ตอบกระชับ **ช่วยเพิ่มความแม่นยำ 26 เปอร์เซ็นต์พอยต์** ในบาง benchmark และพลิกลำดับประสิทธิภาพอย่างสิ้นเชิง คำพูดยืดยาวไม่ได้ดีกว่าเสมอไป บางทีคำน้อย = ถูกต้องกว่า

## Evals

caveman ไม่ได้แค่อ้าง 75% — caveman **พิสูจน์** มันด้วย

ไดเรกทอรี `evals/` มี eval harness แบบสามกลุ่มที่วัดการบีบอัด token จริงเทียบกับ control ที่เหมาะสม — ไม่ใช่แค่ "verbose vs skill" แต่เป็น "terse vs skill" เพราะการเปรียบ caveman กับ Claude ที่พูดยาวๆ ปนความสามารถของ skill กับการกระชับทั่วไป นั่นคือการโกง caveman ไม่โกง

```bash
# Run the eval (needs claude CLI)
uv run python evals/llm_run.py

# Read results (no API key, runs offline)
uv run --with tiktoken python evals/measure.py
```

## กด Star Repo นี้

ถ้า caveman ช่วยประหยัด token และเงินให้คุณ — ฝาก star ไว้ด้วย ⭐

[![Star History Chart](https://api.star-history.com/svg?repos=JuliusBrussee/caveman&type=Date)](https://star-history.com/#JuliusBrussee/caveman&Date)

## 🪨 Caveman Ecosystem

สามเครื่องมือ ปรัชญาเดียว: **agent ทำได้มากขึ้นด้วยน้อยลง**

| Repo | ทำอะไร | สรุปสั้นๆ |
|------|------|-----------|
| [**caveman**](https://github.com/JuliusBrussee/caveman) *(คุณอยู่ที่นี่)* | skill บีบอัด output | *ทำไมต้องใช้ token เยอะ ในเมื่อน้อยก็พอ* — output tokens น้อยกว่า ~75% ใน Claude Code, Cursor, Gemini, Codex |
| [**cavemem**](https://github.com/JuliusBrussee/cavemem) | หน่วยความจำถาวรข้าม agent | *ทำไม agent ต้องลืม ในเมื่อ agent จำได้* — SQLite บีบอัด + MCP เก็บข้อมูลในเครื่องตามค่าเริ่มต้น |
| [**cavekit**](https://github.com/JuliusBrussee/cavekit) | loop build อัตโนมัติขับเคลื่อนด้วย spec | *ทำไม agent ต้องเดา ในเมื่อ agent รู้ได้* — ภาษาธรรมชาติ → kits → build คู่ขนาน → ตรวจสอบแล้ว |

ทำงานร่วมกัน: **cavekit** ควบคุมการ build, **caveman** บีบอัดสิ่งที่ agent *พูด*, **cavemem** บีบอัดสิ่งที่ agent *จำ* ติดตั้งหนึ่ง บาง หรือทั้งหมด — แต่ละตัวใช้งานได้อิสระ

## ผลงานอื่นของ Julius Brussee

- **[Revu](https://github.com/JuliusBrussee/revu-swift)** — macOS study app แบบ local-first พร้อม FSRS spaced repetition, decks, exams และ study guides [revu.cards](https://revu.cards)

## License

MIT — อิสระเหมือนแมมมอธกลางทุ่งกว้าง
