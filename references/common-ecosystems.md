# 现代生态避坑与事实标准速查 (High-Signal Ecosystems)

> **原则**：只记录 AI 最容易产生旧版本幻觉、最容易手搓翻车的领域。凡属于通用模式，优先胶水集成，拒绝重写。

---

## 避坑与现代事实标准对照表

| 领域 / 需求 | ⚠️ AI 易踩的旧记忆/手搓陷阱 | ✅ 现代事实标准 (2024-2026) | 为什么必须切换？ |
| :--- | :--- | :--- | :--- |
| **拖拽排序 (Drag & Drop)** | 手写原生拖拽 或 推荐 `react-beautiful-dnd` | **`@dnd-kit/core`** / **`@hello-pangea/dnd`** | 原库已被 Atlassian 弃用；dnd-kit 原生支持移动端 Touch 与 a11y |
| **日期时间计算** | 手写 Date 加减 或 推荐 `moment.js` | **`date-fns`** / **`dayjs`** | Moment 极其臃肿且无法 Tree-shaking；date-fns 为纯函数不可变设计 |
| **模式校验与类型推导** | 手写正则 与 `typeof` 检查 | **`zod`** / **`valibot`** | 手写正则漏洞百出；Zod 直接单源生成静态 TypeScript 类型 |
| **大数据虚拟列表** | 暴力全量渲染 或 手写 scroll 监听 | **`@tanstack/react-virtual`** / **`virtua`** | 动态高度计算极易造成掉帧重排；TanStack Virtual 极致平滑 |
| **浮动元素定位 (Tooltip/Pop)** | 手写绝对定位坐标计算 | **`@floating-ui/react`** | 自动避障、翻转、贴边偏移，彻底杜绝元素飘出视口 |
| **JWT 与现代加解密** | 手写 Base64 解码与原生 HMAC | **`jose`** | 零依赖、多端运行时通用、经密码学审计无侧信道漏洞 |
| **Python 数据解析校验** | 手写字典 `get` 校验 | **`pydantic` (v2)** | Rust 核心加速、性能提升 20 倍、类型推断生态基石 |
| **Python 异步 HTTP** | 原生 `urllib` 或同步阻塞 requests | **`httpx`** | 原生 HTTP/2 与全异步支持，现代标准 |
| **Python 优雅重试** | 手写 `for i in range(3): try...` | **`tenacity`** | 指数退避、抖动算法（Jitter）、条件异常重试全开箱即用 |

---

## 判定：何时必须胶水集成？

1. **涉及外部网络/协议规范**：JWT、OAuth2、SSE、Cron 表达式、Markdown/AST。
2. **涉及平台/设备差异**：跨端 Touch、视口定位滚动、跨时区夏令时换算。
3. **涉及密码与注入安全**：加解密、密码 Hash、HTML XSS 防御（如 `dompurify`）。
