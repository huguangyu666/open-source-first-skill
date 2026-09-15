# 视觉特效、Shader 与高难度算法移植指南 (Creative & Shader Harvesting)

在图形学、3D 渲染与物理模拟领域，**“从零手搓”的代价极其高昂**：
1. **Token 消耗海量**：手搓光线步进（Raymarching）、SDF 或微积分偏折公式，需要消耗数万 Token 反复试错调试，极易造成上下文膨胀。
2. **复刻精度不足**：吸积盘相对论光行差、真实流体 Navier-Stokes 方程等深度细节，大模型单次生成极易出现视觉假感、边缘撕裂或帧率崩塌。

**实战工程最优解：去 GitHub、Shadertoy、Three.js 社区提取成熟先验（Prior Art），以极低 Token 成本实现工业级复现。**

---

## 经典案例：网页端“黑洞（Black Hole）”模拟移植

### 1. 为什么手搓性比极低？
* **真实黑洞的核心要素**：
  1. **事件视界 (Event Horizon)**：不可逃逸的绝对黑区。
  2. **引力透镜 (Gravitational Lensing)**：广义相对论时空弯曲产生的爱因斯坦环。
  3. **吸积盘相对论聚束 (Relativistic Beaming)**：旋转流体因多普勒频移导致一侧明亮一侧暗淡。
* 手搓需要消耗海量推理 Token 调参；而开源社区（如 Shadertoy 上的 Schwarzschild/Kerr 黑洞着色器）早已有经过验证的顶级公式。

### 2. 极简移植流程 (Shadertoy / GitHub ➔ Three.js / React)

#### Step 1: 定向检索开源先验
使用 `web_search` 定向查询：
* `site:shadertoy.com "black hole" "lensing"`
* `github "black hole" (threejs OR webgl) stars:>50`

#### Step 2: 提取核心片元着色器 (Fragment Shader)
大牛的核心逻辑通常是纯 GLSL 代码：
```glsl
// 核心数学：光线步进与引力偏折微元
vec3 traceBlackHole(vec3 rayOrigin, vec3 rayDir, vec3 bhPos, float bhMass) {
    vec3 p = rayOrigin;
    vec3 dir = rayDir;
    float stepSize = 0.05;
    for (int i = 0; i < 128; i++) {
        vec3 toBH = bhPos - p;
        float dist = length(toBH);
        if (dist < 0.2) return vec3(0.0); // 视界
        vec3 accel = bhMass * normalize(toBH) / (dist * dist);
        dir = normalize(dir + accel * stepSize);
        p += dir * stepSize;
    }
    return sampleBackgroundStars(dir);
}
```

#### Step 3: 低成本胶水适配
将 Shadertoy 原生变量映射到 Three.js / WebGL：
* `iResolution.xy` ➔ `uniform vec2 u_resolution`
* `iTime` ➔ `uniform float u_time`
* `iMouse` ➔ `uniform vec2 u_mouse`
* `mainImage(out vec4 fragColor, in vec2 fragCoord)` ➔ `void main()` 配合 `gl_FragColor`

直接挂载到全屏 Quad 或 `THREE.ShaderMaterial`，几百 Token 即可在项目中还原顶级视觉。

#### Step 4: 强制开源致敬声明 (Mandatory Attribution)
**在生成的着色器或封装组件文件头部，必须保留以下致敬注释块，严禁抹去原作者信息：**

```typescript
/**
 * ============================================================================
 * 来源致敬 (Open-Source Attribution)
 * 原作项目: Interstellar Black Hole Raymarcher
 * 原作者:   Wyatt (Shadertoy)
 * 原始链接: https://www.shadertoy.com/view/llj3Rz
 * 开源协议: CC BY-NC-SA 3.0 / MIT
 * 移植说明: 将原生 Shadertoy GLSL 变量映射至 Three.js ShaderMaterial，
 *          并针对移动端降低了 Raymarching 最大步数以保障 60 FPS。
 * ============================================================================
 */
```

---

## 其他高 ROI 移植领域

* **海洋与水面**：直用 Three.js 官方 `Water.js` 或 GLSL FFT Ocean，杜绝手写简陋波浪。
* **物理碰撞与布娃娃**：直接集成 `rapier.js` 或 `cannon-es`，杜绝手写刚体弹力方程。
* **后处理滤镜**：优先使用 `postprocessing` 库标准 Pass。
