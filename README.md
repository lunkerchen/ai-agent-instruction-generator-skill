<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT">
  <img src="https://img.shields.io/badge/hermes-skill-purple" alt="Hermes Skill">
  <img src="https://img.shields.io/badge/status-active-brightgreen" alt="Active">
</p>

# AI Agent Instruction Generator Skill

> Transform vague requirements into structured, executable agent task instructions.
> 將使用者模糊、簡短或不完整的需求，轉換成一份清楚、完整、可執行、可驗收的 AI Agent 任務指令。

## Overview / 概述

This Hermes skill converts fuzzy user input — keywords, short sentences, half-baked drafts — into a structured AI Agent task specification. The output is ready to paste directly into another agent session.

本 Hermes skill 能將模糊的輸入（關鍵字、一句話、半成品草稿）轉換為結構化的 AI Agent 任務規格，產出可直接貼給其他 Agent 使用的完整指令。

### Key Improvements (v1.0.0)

- **6-section template** — reduced from 11 overlapping sections, quality/restrictions/prohibitions merged into one block
- **Input type classifier** — keyword / one-liner / draft / debug requests routed to different expansion strategies
- **Iteration mode** — incremental updates instead of full rewrites
- **Reverse-verification** — each quality rule has a checkable test
- **Anti-patterns** — explicit when-not-to-use scenarios

## Installation / 安裝

```bash
# Clone to your Hermes skills directory
git clone https://github.com/lunkerchen/ai-agent-instruction-generator-skill.git ~/.hermes/skills/ai-agent-instruction-generator/
```

Or copy `SKILL.md` directly into your `.hermes/skills/` directory.

## Usage / 使用方式

Trigger this skill when the user says:

- 「幫我生成 agent 指令」
- 「把這個需求寫成 agent 任務」
- 「產生 task instruction」
- 「寫給 agent 執行的步驟」
- 「展開成 agent 可用的指令」

Or any time you need to turn a high-level description into structured agent instructions.

### Output template

The generated instruction includes:

| Section | Description |
|---------|-------------|
| 1. Agent Role | Who the agent is + one-line mission |
| 2. Context | Background, purpose, scenario |
| 3. Objectives | Quantified goals |
| 4. Available Data | Data sources with confidence markers |
| 5. Output Format | Expected deliverable structure |
| 6. Quality & Restrictions | Must-haves, prohibitions, human-approval triggers |

## Input Types / 輸入類型

| Type | Strategy |
|------|----------|
| **Keywords** ("客服機器人") | Infer scope, produce full instruction + mark assumptions |
| **One-liner** ("幫我寫個爬蟲抓 PTT") | Expand to full instruction, focus on steps & output |
| **Draft** (half-written spec) | Fill gaps, merge format, flag inconsistencies |
| **Debug/Revision** ("第三步不夠清楚") | Incremental iteration, patch only affected sections |

## Project Structure

```
.
├── .hermes/
│   └── skills/
│       └── ai-agent-instruction-generator/
│           └── SKILL.md       # The skill definition
├── README.md                  # This file
├── LICENSE                    # MIT
```

## License / 授權

MIT — free to use, modify, and distribute.

## Related Skills

- [prompt-master](https://github.com/lunkerchen/prompt-master) — Optimized prompts for any AI tool
- [multi-agent-debate-skill](https://github.com/lunkerchen/multi-agent-debate-skill) — Structured debate for better decisions
- [ai-project-blueprint-skill](https://github.com/lunkerchen/ai-project-blueprint-skill) — 6-part framework for AI agent projects
