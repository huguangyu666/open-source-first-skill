<div align="right">
  <a href="README.md">简体中文</a> | <strong>English</strong>
</div>

<div align="center">

# Open-Source First (No-Reinventing-Wheels Skill)

**Pragmatic Anti-Wheel-Reinvention Protocol for AI Coding Agents**  
*Research First · Open Source Ethics · Tokenomics Advantage · Three-Tier Defense*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/huguangyu666)
[![Support](https://img.shields.io/badge/Agent-Claude%20Code%20%7C%20DSH%20%7C%20Cursor-orange)](README.md)

</div>

---

## 📌 Mission Statement

In practical software engineering, **the most dangerous pitfall of AI Coding Agents is premature coding and the obsessive urge to reinvent everything from scratch**.  
Whether it's poorly handwritten low-level utilities (drag-and-drop, date-time calculations, virtual scrolling), hallucinated high-difficulty visuals (scratch-building a black hole shader without physics basis), or delusional architectural ambitions (attempting to solo-build an IM to challenge Slack or solo-build an Agent framework to beat Codex) — **this not only leads to brittle, bug-ridden code, but also aggressively burns the most expensive LLM Output Tokens!**

**This project equips Coding Agents (Claude Code, DeepSeek Harness, Cursor, Windsurf) with a production-grade [Research-First] and [Open-Source Ecosystem Priority] protocol, transforming AI from a clumsy wheel-reinventor into a sober architect and high-ROI code harvester.**

---

## ⭐️ Rule #1: Research Before Action

> **Premature action is the root of all software disasters. Writing implementation code without thorough upfront research is strictly prohibited.**  
> Spending 500 cheap input tokens on research saves 50,000+ expensive output tokens wasted on wrong directions, API hallucinations, and endless rewrites.

Before touching a single line of code, the Agent **must conduct Dual-Track Research and report a concise summary upfront**:

```
                  [Development Request]
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│ 1. Internal Research                                   │
│ Inspect package.json / pyproject.toml / go.mod & tree  │
│ Clarify: Existing stack? Versions? Existing tools?     │
└────────────────────────────────────────────────────────┘
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│ 2. External Research                                   │
│ Use web_search & web_fetch for community standards     │
│ Clarify: What is the gold standard? Latest stable API? │
└────────────────────────────────────────────────────────┘
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│ 3. Sync Findings with User                             │
│ Present brief report: Status + Options + Decision      │
└────────────────────────────────────────────────────────┘
                            │
                            ▼
          [Code with precision after alignment]
```

---

## 💰 The Tokenomics Axiom: Input is Vastly Cheaper than Output

In LLM pricing models and runtime hardware constraints, an undeniable economic reality exists:

| Dimension | Input Tokens (Prefill) | Output Tokens (Decode / Generation) |
| :--- | :--- | :--- |
| **API Cost** | **Extremely Cheap** (typically **1/3 to 1/5** of output price; down to **1/10 to 1/20** with Prompt Cache) | **Prohibitively Expensive** (the primary cost driver of all API bills) |
| **Throughput & Latency** | **Instant Parallelism** (ingests thousands of tokens in milliseconds) | **Slow Autoregressive Decode** (bottlenecked by memory bandwidth, takes minutes) |
| **Deterministic Quality** | **100% Battle-Tested** (code hardened by thousands of production PRs) | **Stochastic & Vulnerable** (praying the model doesn't miss edge cases) |

> **🔥 The Economic Law**:  
> **Fetching mature open-source code via `web_fetch` as cheap Input Tokens and generating a 50-token glue adapter is 10x faster, 90% cheaper, and vastly superior to burning thousands of high-cost Output Tokens generating brittle code from scratch!**

---

## ⚖️ Open-Source Ethics: Dual-Track Attribution

> **Harvesting open-source genius while concealing its origin and pretending it was written from scratch is malicious "Code Laundering".**  
> Elite software engineers never conceal standing on giants' shoulders. **Publicly and proudly attributing open-source work in both code and documentation is the pinnacle of engineering integrity.**

Whenever harvesting algorithms, porting shaders from GitHub/Shadertoy, or integrating core libraries, the Agent **must enforce Dual-Track Attribution**:

### 1. In-Code Header
Every ported or heavily referenced file must lead with a structured attribution block:
```typescript
/**
 * ============================================================================
 * Open-Source Attribution
 * Original Project: [Repository name / Shadertoy title]
 * Original Author:  [Author GitHub handle / Name]
 * Source Link:      [GitHub URL / Shadertoy URL]
 * License:          [MIT / Apache-2.0 / BSD / CC-BY etc.]
 * Porting Notes:    [Summary of framework adaptations or glue logic applied]
 * ============================================================================
 */
```

### 2. Project README Credits
**Users and peers judge a project by its README, not its source comments!**  
The project `README.md` must contain an **`## Acknowledgements & Credits`** section:

```markdown
## Acknowledgements & Credits

This project proudly stands on the shoulders of the open-source community:
- **[Feature/Visual Name, e.g., Black Hole Lensing Shader]**: Ported from [@Author](Author profile/URL)'s work [Project Title](Source Link), licensed under [License].
- **[Core Dependency, e.g., Drag & Drop Engine]**: Built upon [@dnd-kit/core](https://github.com/clauderic/dnd-kit).
```

---

## 🛡️ The Three-Tier Wheel Prevention Model

```
┌────────────────────────────────────────────────────────────────────────┐
│ Tier 3: System & Product Level                                         │
│ Scenarios: Solo-building IM/Chat, OS, custom Agent to beat Codex      │
│ Action: [Reality Check Protocol] Quantify complexity, push OSS bases   │
├────────────────────────────────────────────────────────────────────────┤
│ Tier 2: Visuals, Shaders & Deep Algorithms                             │
│ Scenarios: Black hole simulation, GLSL fluid, 3D starfields, Raymarch │
│ Action: [Prior Art Harvesting] Harvest Shadertoy/GitHub + Dual Credits │
├────────────────────────────────────────────────────────────────────────┤
│ Tier 1: Libraries & Engineering Components                             │
│ Scenarios: Drag-and-drop, virtual lists, date-time, schema validation  │
│ Action: [Ecosystem Check] Inspect package.json, use gold standards    │
└────────────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ Scope: Practical Delivery vs. Pure Benchmarking

* **Production Engineering Focused**:  
  This skill is strictly designed for **real-world production velocity, cost reduction, and artifact robustness**. Showing off "model hand-crafting muscles" in production is engineering negligence.
* **Benchmark & Capability Testing Escape Hatch**:  
  If the explicit goal of the current session is **pure model capability evaluation or stress benchmarking** (e.g., testing if raw DeepSeek/Claude can hand-write a relativistic black hole shader unaided), **switch to a raw model mode without this harness skill**.

---

## 📂 Project Structure

```
open-source-first/
├── SKILL.md                          # Core Agent instruction specification
├── README.md                         # Chinese Documentation (Default Landing Page)
├── README.en.md                      # English Documentation
└── references/
    ├── common-ecosystems.md          # Tier 1: Deprecated traps vs Modern standards
    ├── creative-and-shaders.md       # Tier 2: Low-token shader & visual porting guide
    ├── product-level-alternatives.md # Tier 3: Open-source giants (IM, Agents, Docs)
    └── search-playbook.md            # High-signal search queries & raw fetch playbook
```

---

## 🚀 Installation & Usage

### 1. DeepSeek Harness (DSH)
Copy into your global skills directory:
```powershell
~/.dsh/skills/open-source-first/
# or
~/.agents/skills/open-source-first/
```

### 2. Claude Code CLI
Copy into global or project-level directory:
```powershell
# Global:
~/.claude/skills/open-source-first/

# Project-level:
<project-root>/.claude/skills/open-source-first/
```

### 3. Cursor / Windsurf
Paste the body of `SKILL.md` directly into your `.cursorrules` or `.windsurfrules`.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
