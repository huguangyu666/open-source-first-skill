# 原生搜索与直连抓取官方文档战术手册 (Search Playbook)

本手册指导 AI **如何善用宿主环境自带的 `web_search` 和 `web_fetch` 工具**，以极高的信噪比和极低的网络消耗完成技术选型、特效移植与方案论证，并彻底消除“API 幻觉”。

---

## 一、定向搜索查询模式 (High-Signal Query Patterns)

当需要为某项功能、特效或系统寻找成熟开源方案时，**禁止使用宽泛无意义的自然语言**，必须使用以下战术级组合查询：

### 1. 寻找 Tier 1 生态事实标准 (Finding Industry Standards)
* `awesome-<生态/语言> <功能关键词> github`
  * *示例*：`awesome-react virtual scroll github` 或 `awesome-python retry library`
* `best <技术栈> <需求> library 2024 OR 2025`
  * *示例*：`best react drag and drop library 2024 OR 2025`
* `site:npmtrends.com <候选1> vs <候选2>`
  * *示例*：`site:npmtrends.com @dnd-kit/core vs react-beautiful-dnd`

### 2. 寻找 Tier 2 视觉特效、Shader 与物理模拟 (Visuals, Shaders & 3D)
* `site:shadertoy.com "<特效关键词>"`
  * *示例*：`site:shadertoy.com "black hole" "lensing"`
  * *示例*：`site:shadertoy.com "water caustics" raymarching`
* `github <关键词> (threejs OR webgl OR shader) stars:>50`
  * *示例*：`github "black hole" threejs stars:>50`
  * *示例*：`github gravitational lensing glsl`
* `site:codepen.io <视觉关键词> canvas OR webgl`
  * *示例*：`site:codepen.io black hole webgl`

### 3. 寻找 Tier 3 顶级开源系统成品 (Finding Open Source Giants)
* `best open source alternatives to "<商业巨头产品>"`
  * *示例*：`best open source alternatives to "Slack"`
  * *示例*：`best open source alternatives to "Notion"`
  * *示例*：`best open source "coding agent" github 2024 OR 2025`

### 4. 探查维护活跃度与破坏性更新 (Liveness & Migration)
* `"<库名>" github releases OR changelog`
  * *示例*：`"pydantic" github releases`
* `"<库名>" migration guide v<上一版本> to v<最新版本>`
  * *示例*：`"tanstack query" migration guide v4 to v5`

---

## 二、利用 `web_fetch` 直连穿透获取权威数据

很多时候，阅读一整页庞大的文档网站既慢又耗费大量 Context。**最干净、最准确的信息直接藏在开源仓库的原生资产中**。

一旦通过搜索锁定了仓库名（如 `owner/repo`）或包名，直接使用 `web_fetch` 抓取以下纯文本端点：

### 1. 瞬间抓取官方 README（消除 API 幻觉的最佳方式）
官方仓库的根目录 README 通常包含最权威的 Quick Start 代码。直接抓取 Raw 链接：
```
https://raw.githubusercontent.com/<owner>/<repo>/HEAD/README.md
```
*(注：若 HEAD 不生效，可尝试 main 或 master)*。

> **收益**：AI 读到的是当前主分支由作者亲自维护的官方代码范例，导入路径、函数签名 100% 真实，从根源上杜绝凭空捏造不存在的 API。

### 2. 瞬间抓取开源仓库的核心 Shader 代码
很多黑洞、特效仓库的代码结构非常简单，核心往往在 `shaders/` 或 `src/fragment.glsl`：
```
https://raw.githubusercontent.com/<owner>/<repo>/HEAD/shaders/fragment.glsl
```
直接抓取纯 GLSL，免去理解杂乱构建配置的开销。

### 3. 秒查 npm 包的最新版本与依赖
```
https://registry.npmjs.org/<package-name>/latest
```
直接提取 JSON 中的 `version`、`types` 和 `peerDependencies`。

### 4. 秒查 Python PyPI 包的最新版本
```
https://pypi.org/pypi/<package-name>/json
```
直接提取 JSON 中的 `info.version` 与 `info.requires_python`。

---

## 三、闭环落地流线

```
   [1. 定向搜索：锁定顶级依赖库、神级 Shader 或成熟系统]
                       │
                       ▼
   [2. web_fetch 直连穿透：抓取官方 README、GLSL 或部署架构]
                       │
                       ▼
   [3. 落地输出：编写业务胶水适配层 / Shader 移植 / 或给出冷静的选型决策]
```
