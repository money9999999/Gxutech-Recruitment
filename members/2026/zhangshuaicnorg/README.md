# 个人资料 - zhangshuaicnorg

## 基本资料
- **姓名**: 张帅
- **学号**: 2531240152
- **年级专业**: 物理学
- **GitHub**: [zhangshuaicnorg](https://github.com/zhangshuaicnorg)
- **QQ**: 2019344695

## 技术栈与工具
- **前端**: Kotlin, Compose Multiplatform (CMP)
- **后端**: Java, C++ (通过 JNA 交互)
- **异构计算**: TornadoVM, CUDA Backend
- **开发工具**: IntelliJ IDEA, Typora (重度 Markdown 笔记用户)
- **熟练度**: Java (熟练), Kotlin/CMP (熟悉), C++/CUDA (了解)

## 个人项目经历 (Projects)
除了日常技术探索，我热衷于通过动手做项目来解决实际痛点，目前已完成/正在进行以下项目：

1. **XLink 虚拟局域网组网程序 (核心项目)**
   - **架构**: CMP 构建现代化跨平台前端，Java 通过 JNA 调用 C++ 后端。
   - **技术点**: 底层基于 **wintun** 虚拟网卡实现网络数据包的拦截与转发。
   - **收获**: 深入理解了跨语言调用机制（JNI/JNA）、底层网络协议以及虚拟网卡(wintun)的工作原理。
2. **现代化游戏启动器**
   - **描述**: 基于 CMP 独立开发，注重 UI/UX 设计，实现了现代化、美观且流畅的游戏管理界面，锻炼了跨平台 UI 布局与自定义组件开发能力。
3. **Android 端纯净小说阅读器 (开发中)**
   - **动机**: 苦于市面上小说 App 广告泛滥，决定自己动手打造一个纯净、无广告的沉浸式阅读环境。
   - **状态**: 核心解析与阅读渲染模块正在开发中，持续迭代。
4. **手搓静态 TornadoVM 3D 光栅化渲染管线**
   - **描述**: 完全脱离现有图形 API，基于 TornadoVM 从零实现了一套纯 Java 的 3D 光栅化渲染管线。
   - **技术点**: 手动推导并实现了顶点变换、裁剪、透视除法、三角形装配及片段着色等核心光栅化阶段；利用 TornadoVM 将几何处理与像素填充卸载至 GPU 并行执行。
   - **收获**: 彻底打通了从数学公式到 GPU 并行计算的底层认知，深刻理解了光栅化本质与异构计算在图形渲染中的性能边界。

## 开放性问题回答

### 1. 加入动机
出于对技术的纯粹热爱，希望寻找志同道合的伙伴。

### 2. 最近一次主动学习经历
近期正在系统学习 Compose Multiplatform (CMP)。通过 Bilibili [Jetpack Compose](https://www.bilibili.com/video/BV1y5WmzQEDN) 教学视频建立初步认知，结合官方文档深入理解声明式 UI 框架原理，并参考优质开源项目进行实践，逐步将其应用到我的 XLink 和阅读器项目中。日常学习均使用 Typora 沉淀结构化笔记。

### 3. 最感兴趣的技术方向
**游戏智能辅助与实时图形学渲染**。

- **AI 层面**: 关注计算机视觉与 AI 推理在游戏场景下的实时交互（如 BetterGI）。
- **图形学层面**: 作为 Steam 重度玩家，持续关注 **光线追踪 (Ray Tracing)**、**路径追踪 (Path Tracing)** 以及 **DLSS** 等基于 CUDA 的硬件加速技术。

### 4. AI 使用习惯
日常小问题使用 Qwen，复杂问题使用 Mimo v2.5 Pro；IDEA 安装 Qoder 插件并接入自订阅大模型。整体采用“半古法半AI”模式——AI 仅作为思路启发，报错修复思路和代码补全工具。核心逻辑与生产级代码必须依赖人工验证与重构，以减少黑盒依赖、确保代码可控，而且当前个人级 AI 尚难以独立支撑大型项目。

### 5. AI 答案错误时的处理方式
以 TornadoVM 开发为例：AI 常误将 Java 标准库的 `AtomicInteger` 用于 GPU kernel，导致编译失败。我的处理流程是：先理解 AI 代码中“需原子操作”的设计意图，再查阅 TornadoVM 官方文档，找到正确的 GPU 原子操作方法并手动重写实现。最终修复了错误，充分发挥了 GPU 的大规模并行优势——在数据量呈指数级增长时，计算耗时并未显著增加，性能表现远超 CPU。

## 技术资源分享

### BetterGI
- **链接**: https://github.com/babalae/better-genshin-impact
- **检索过程**: 最初在 Bilibili 看到演示视频后，顺着视频简介找到 GitHub 仓库；随后通过 README 中的架构说明反向检索 YOLOv8、OpenCvSharp 等关键技术文档，并 clone 源码本地调试，从而理解 AI 推理与游戏交互的实现链路。
- **参考价值**: 对想探索计算机视觉与 AI 游戏辅助的同学具有强启发性。其清晰的模块化设计和详尽的文档，为从零构建自己的 AI 推理游戏辅助提供了可复用的工程范式。目前我正在研读其源码以深化理解。

## AI 辅助记录：TornadoVM 原子操作幻觉修复

### 问题描述
在 TornadoVM GPU kernel 中实现Z-Buffer深度测试时，AI 生成代码直接使用 `java.util.concurrent.atomic.AtomicInteger`，导致编译阶段报错。

### 提问方式
向 AI 提供其生成的错误源码 + TornadoVM 官方文档中 "Supported APIs" 子章节链接，要求修正 GPU kernel 中的原子操作实现。

### 有效性验证
IDEA 中的TornadoVM插件直接报红提示类型不支持，无需运行即可判定 AI 混淆了 CPU 与 GPU 的原子对象模型。

### 后续处理
放弃 AI 生成的具体代码，仅保留“需原子累加”的设计思路。依据官方文档改用 TornadoVM 的 `KernelContext` 机制实现 GPU 端原子操作，并基于该上下文对象调用对应的原子方法重写 kernel。修正后代码成功编译并在 GPU 上稳定运行。测试代码成功编译并在 RTX 5070 Laptop GPU 上稳定运行。在 8192×8192 方阵乘法实测中，GPU 并行计算耗时仅约 80ms（已剔除编译开销和copy开销）；而作为对照的 Java 原生 CPU 串行代码运行 4 小时仍未出结果（手动终止进程），以超 18 万倍的极致性能反差，直观展现了 GPU 在大规模计算中的压倒性优势。

## 未来一年 Flag 🚩
1. **继续学习 CMP**：完成 Compose Multiplatform 的系统学习，并完成我的小说阅读器。
2. **打通 AI 推理链路**：掌握深度学习基础理论，配合 TornadoVM 的张量加速能力，**写出属于自己的第一个 AI 推理游戏辅助 Demo**。
