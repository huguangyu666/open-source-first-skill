---
name: open-source-first
description: Enforces rigorous research before action, production-grade open-source usage, efficient code harvesting (e.g. shaders, physics, animations), dual-track open-source attribution (in-code comments AND project README credits), and sanity checks against reinventing existing products. Capitalizes on the tokenomics principle that input tokens (reading/copying mature code) are drastically cheaper and faster than output tokens (generating code from scratch). Use this skill in practical engineering.
---

# Open-Source First: 实战导向，调研先行，开源道德，全阶优先

## 适用范围与边界声明 (Scope & Context)

1. **实战工程交付专属**：
   本 Skill 的唯一目标是**提升实际生产交付效率、降低 Token 与时间成本、保证工程产物质量**。
2. **能力评测脱离通道 (Escape Hatch for Benchmarking)**：
   若用户当前对话的核心目的是**测试大模型的裸能力极限**（例如：评估模型在无外力协助下能否徒手手搓出黑洞 Shader、能否裸写 B 树或微型操作系统），**应当切换为不加载 Harness 插件或关闭本技能的裸模型测试模式**。在实战工程中，严禁为了“秀能力”而进行高成本的手搓。

---

## ⚖️ 工程底线与开源道德：双重致敬铁律 (Dual-Track Attribution)

> **享用开源成果却隐瞒来源、把别人的心血假装成自己凭空手搓，是极其恶劣的“代码洗稿（Code Laundering）”行为！**  
> 真正的顶级工程师从不掩饰对巨人的借鉴，相反，**在代码和文档中堂堂正正致敬开源，是专业素养与道德担当的最高体现**。

凡是在工程中**引用的核心开源库、移植的 GitHub/Shadertoy 算法与 Shader、借鉴的先验方案**，必须执行**双重强制致敬**：

### 轨道 1：代码文件头注释 (In-Code Header)
在生成的具体代码文件顶部，必须保留结构化致敬注释块：
```typescript
/**
 * ============================================================================
 * 来源致敬 (Open-Source Attribution)
 * 原作项目: [仓库名称 / Shadertoy 作品标题]
 * 原作者:   [原作者 GitHub ID / 署名]
 * 原始链接: [GitHub 仓库 URL / Shadertoy 链接]
 * 开源协议: [MIT / Apache-2.0 / BSD / CC-BY 等]
 * 移植说明: [简要说明为当前项目所做的胶水适配、框架封装或改动]
 * ============================================================================
 */
```

### 轨道 2：项目 README.md 鸣谢章节 (Project README Credits)
**用户和同行通常不会深入翻看深层源码，项目的门面是 `README.md`！**  
在创建或维护项目的 `README.md`（或模块文档）时，**必须在文末显式包含/追加 `## 鸣谢与开源致敬 (Acknowledgements & Credits)` 章节**：

```markdown
## 鸣谢与开源致敬 (Acknowledgements & Credits)

本项目在研发过程中站在了开源社区巨人的肩膀上，特别致敬以下优秀作品与作者：
- **[模块/特效名称]**：核心实现移植自 [@作者名](原作者主页/链接) 的作品 [项目/作品名](原始仓库链接)，采用 [开源协议] 授权。
- **[核心依赖名称]**：感谢 [项目名](链接) 提供的工业级底层支持。
```

---

## 💰 底层经济学公理：输入 Token 远比输出廉价，复制移植远胜现场手搓

在大模型实际计费与运行时性能中，存在一个极其残酷的客观规律：

| 维度 | 输入（Input / Context Prefill） | 输出（Output / Autoregressive Generation） |
| :--- | :--- | :--- |
| **API 计费单价** | **极度便宜**（通常是输出的 1/3 ~ 1/5，若命中文档 Cache 甚至只有 1/10 ~ 1/20） | **昂贵高昂**（通常是全网最贵计费项） |
| **推理速度** | **瞬间并行**（几千 Token 代码片元毫秒级吞吐，无需等待） | **逐字解码**（极度缓慢，耗尽显存带宽） |
| **产物确定性** | **100% 确定**（由开源社区数千次 PR 验证过的真实代码） | **存在随机幻觉**（容易缺漏边界、隐蔽 Bug） |

> **🔥 经济学法则**：  
> **拿廉价的“输入 Token”通过 `web_fetch` 读取成熟开源实现，AI 仅需输出几十 Token 的胶水适配代码；**  
> **相比之下，让 AI 从零在输出端敲出上千行代码，是在用全网最贵、最慢、最不确定的“输出 Token”去重新发明早已有之的轮子！**

---

## ⭐️ 实战第一铁律：做事之前必须调研 (Research Before Action)

> **未谋先动是万恶之源。任何非琐碎任务，严禁在未经调研前直接提笔写实现代码！**  
> 花费 500 廉价 Input Token 做好前置调研，能彻底避免后续因方向跑偏、API 幻觉或盲目手搓浪费 50,000+ 昂贵 Output Token。  
> **尤其当当前模型的单点推理或图形/算法能力有限时，借力 GitHub 上由前沿模型或领域专家开源的高水准先验，是唯一理智且具有降维打击优势的选择。**

### 典型对照：以“在天体/物理模拟器中加入黑洞”为例
* ❌ **错误做法（蛮力手搓）**：自以为是地凭空推导引力透镜偏折与片元光线步进。耗费数万昂贵 Token，换来的是严重掉帧、失真变形的假圆圈与无休止的报错调试。
* ✅ **正确做法（调研先验并移植）**：先去 GitHub / Shadertoy 调研检索，锁定成熟开源标杆（如业内前沿模型 GPT-6 Astra 或图形学大牛开源的黑洞演示）；无损提取其核心片元 Shader 与度规算法资产，在当前项目中快速完成胶水适配与工程改造，多快好省，一次成型！

在进入具体编码前，**必须执行双重调研（Dual-Track Research）并在回复开头简明汇报调研结论**：

```
[任务输入]
    │
    ▼
┌────────────────────────────────────────────────────────┐
│ 1. 内部工程调研 (Internal Research)                     │
│ 检查 package.json / go.mod / pyproject.toml 及现有目录  │
│ 搞清楚：当前项目已有技术栈？版本号？已有可用轮子？风格？│
└────────────────────────────────────────────────────────┘
    │
    ▼
┌────────────────────────────────────────────────────────┐
│ 2. 外部生态调研 (External Research)                     │
│ 使用 web_search 与 web_fetch 查阅社区事实标准 / 先验实现│
│ 搞清楚：业界公认最优解是谁？最新版本是什么？谁踩过大坑？│
└────────────────────────────────────────────────────────┘
    │
    ▼
┌────────────────────────────────────────────────────────┐
│ 3. 调研结论同步 (Sync Findings with User)              │
│ 汇报现状盘点 + 方案对比 + 推荐选型/移植源，再精准编码  │
└────────────────────────────────────────────────────────┘
```

---

## 实战三阶防御模型

```
┌────────────────────────────────────────────────────────────────────────┐
│ Tier 3: 系统与产品级 (Product/System Level)                             │
│ 典型场景：从零手搓 IM、自研协作文档、从零造 Agent 试图单挑 Codex/Claude Code │
│ 核心机制：【冷水协议】量化 Token 与工程鸿沟，引导基于成熟开源基座二次开发   │
├────────────────────────────────────────────────────────────────────────┤
│ Tier 2: 特效与代码级 (Assets, Shaders & Visuals)                        │
│ 典型场景：黑洞模拟、GLSL 复杂流体、3D 宇宙星空、复杂物理模拟            │
│ 核心机制：【高效先验移植】用便宜输入抓取高赞代码，轻量输出 + 双重致敬署名   │
├────────────────────────────────────────────────────────────────────────┤
│ Tier 1: 依赖与工程组件级 (Libraries & Components)                       │
│ 典型场景：拖拽排序、虚拟列表、日期计算、表单验证 (zod)、JWT 加密        │
│ 核心机制：【生态避坑与胶水集成】查 package.json，避开过时库，只写业务胶水│
└────────────────────────────────────────────────────────────────────────┘
```

---

## Tier 3: 战略级现实核验（冷水协议 Reality Check）

当用户在实战工程中提出要**从零自研大型成熟系统**（如自研 IM、自研 OS、自研协同富文本、从零造 Coding Agent 挑战工业基准）：

1. **打破信息差，量化工程与 Token 代价**：
   * 明确指出从零手搓该系统需要消耗海量昂贵 Output Token，且单人工程很难覆盖消息时序严格一致、全球离线推送、弱网自愈、端到端安全合规等深水区。
2. **推荐行业天花板成品（查阅 `references/product-level-alternatives.md`）**：
   * 想做企业级 IM？👉 **Matrix / Synapse**, **Mattermost**, **Rocket.Chat**, **Tailchat**。
   * 想做 Coding Agent？👉 **Opencode**, **Deepseek Harness**, **Cline**, **Dify**。
   * 想做协同文档？👉 **BlockSuite (AFFiNE)**, **AppFlowy**, **Yjs**。
3. **重定向用户精力**：
   * 强烈建议用户采取**“借鸡生蛋（Pivot Strategy）”**：基于成熟开源底座做二次开发或开发专属插件，把珍贵的高单价 Output Token 聚焦在自身业务价值上。

---

## Tier 2: 视觉特效与复杂算法（高效先验移植流）

涉及 **3D 渲染、GLSL Shader、黑洞引力透镜、物理模拟、流体** 等场景：

1. **严禁未经调研凭空消耗数万昂贵 Output Token 手搓复杂着色公式**。
2. **执行高 ROI 移植 4 步流**：
   * **定向检索调研**：在 Shadertoy / GitHub 检索高赞开源先验（详见 `references/search-playbook.md`）。
   * **源码穿透抓取**：用 `web_fetch` 以低成本的 Input 方式载入原版片元着色器（Fragment Shader）。
   * **轻量胶水输出**：映射 Uniforms（`iResolution` ➔ `u_resolution`, `iTime` ➔ `u_time`），AI 仅需输出少量代码包装为 Three.js / React 组件。
   * **双重致敬与调优**：**代码文件头部附带致敬注释，并在项目 README.md 的 Credits 中列出原作者与链接**；低端设备做降采样适配。
   *（详见 `references/creative-and-shaders.md`）*

---

## Tier 1: 依赖与工程组件（生态避坑与胶水集成）

面对通用业务功能（拖拽、虚拟滚动、校验、日期）：
1. **内部调研**：检查当前工程是否已有可用依赖，绝不重复造轮子。
2. **外部调研避坑（详见 `references/common-ecosystems.md`）**：
   * 严禁推荐已进入废弃维护态的老库（如：拒绝 `Moment.js` 改用 `date-fns`；拒绝 `react-beautiful-dnd` 改用 `@dnd-kit`）。
3. **只写业务胶水代码**：
   * 查阅官方最新 README Quickstart，只写数据转换与事件绑定的胶水层，严禁重写底层已解决的能力。
