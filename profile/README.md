breakevery

开源内核研究组织 / An open-source kernel research organization

---

关于我们 / About Us

中文：
breakevery 是一个专注于低层开发与 AI 协同运行时的开源组织。我们相信，AI 应该在一个可审计、可隔离的环境中协作，而人类保留最终控制权。我们正在构建的不仅是一个工具，更是一套让 AI 协同工作可对账、可归因的基础设施。

English:
breakevery is an open-source organization focused on low-level development and AI collaborative runtimes. We believe AI should collaborate inside auditable, isolated environments, with humans retaining ultimate control. What we are building is not just a tool, but an infrastructure that makes AI collaboration reconcilable and attributable.

---

我们在构建什么 / What We're Building

RiscDom（智芯城） —— AI 协同工作运行时。
RiscDom (智芯城) — an AI collaborative work runtime.

让一群 AI 在可审计、可隔离的沙箱里分工干活。一切动作进哈希链——事后可对账、可归因。这是合规场景的门票，也是我们唯一真正的护城河。

Let a fleet of AIs divide work inside auditable, isolated sandboxes. Every action enters a hash chain — reconcilable and attributable after the fact. This is the ticket to compliance scenarios, and our only real moat.

---

格言 / Motto

Freedom inside boundaries, audit outside the AI, root privilege with humans.
边界之内自由，AI 之外审计，root 权限归人。

---

项目 / Repositories

仓库 / Repository 说明 / Description
riscdom 内核：agent / sandbox / audit / net / relay
riscdom-server 控制平面：单机节点 HTTP 服务 + 最小 web 状态页
riscdom-adminapp 管理程序：桌面（Tauri）+ 移动（Android）

---

架构 / Architecture

```
Human (root)
     ↓
host（Rust + Tauri，唯一前端入口）
     ↓
{agent, sandbox, audit}
↑ 依赖方向单向无环
agent → sandbox → audit
```

三仓单向依赖 / Three repositories, one-directional dependencies:

· riscdom-adminapp → riscdom-server（HTTP API）
· riscdom-adminapp → riscdom（host-core / net，编译期）
· riscdom-server → riscdom（host-core，编译期）

内核内部的单向依赖为：host-core → {agent, sandbox, audit, net}，agent → sandbox → audit，net → audit。管理程序与控制平面不链接任何 Tauri crate 到内核中，依赖通过 git tag（当前均为 v1.0.0）锁定，Cargo.lock 已提交。

---

四条红线 / Four Red Lines

无内置 supervisor —— 内核只给机制，不给策略。
No built-in supervisor — the kernel provides mechanisms, not policies.

无官方运营服务 —— 部署者自己跑节点 / 服务器。
No official hosted service — deployers run their own nodes and servers.

非通用沙箱 —— RISC-V 是主调、基底、默认实现，但不是唯一。
Not a general-purpose sandbox — RISC-V is the primary, base, and default implementation, but not the only one.

审计不变量不动 —— 哈希公式不动，audit v2 只扩语义。
Audit invariants are frozen — the hash formula never changes; audit v2 only extends semantics.

---

当前状态 / Current Status

· v1.0 主体完成（2026-10）
· 内核 v1.0.1 · 控制平面 v1.0.2 · 管理程序 v1.1.0（规划中）
· v1.x 方向： server 产品化 · APP 移动端 · 跨区域管理 · 商业化

English:

· v1.0 core complete (2026-10)
· Kernel v1.0.1 · Control plane v1.0.2 · Admin app v1.1.0 (planned)
· v1.x directions: server productization · mobile app · cross-region management · commercialization

---

加入我们 / Join Us

中文：
breakevery 正在寻找志同道合的伙伴！无论你是经验丰富的开发者，还是刚刚起步的新人，只要你对以下方向有热情，都欢迎加入：

· Rust / 低层开发 —— 参与内核、沙箱、网络协议等核心模块
· 前端 / Tauri —— 开发管理程序的桌面端与移动端
· 美术 / UI 设计 —— 负责产品界面与视觉设计
· 技术写作 / 文档 —— 帮助完善文档与教程
· 测试 / QA —— 参与测试与质量保障
· 任何对 AI 协同、内核研究、开源有热情的人

为什么加入？

· 参与前沿的 AI 协同运行时开发
· 接触 Rust、Tauri、RISC-V 等低层技术
· 与一群有热情的开发者共同成长
· 在合规与审计场景中构建真正的护城河

如何加入？

· 发送邮件至 chenyindrager@outlook.com
· 或在任意仓库提交 Issue / PR，介绍你自己
· 我们期待你的加入！

English:
breakevery is looking for like-minded partners! Whether you are an experienced developer or just starting out, as long as you are passionate about the following areas, you are welcome to join:

· Rust / Low-level development — work on kernel, sandbox, network protocol, and other core modules
· Frontend / Tauri — develop desktop and mobile admin applications
· Art / UI Design — responsible for product interface and visual design
· Technical Writing / Documentation — help improve docs and tutorials
· Testing / QA — participate in testing and quality assurance
· Anyone passionate about AI collaboration, kernel research, and open source

Why join?

· Work on cutting-edge AI collaborative runtime development
· Get hands-on with Rust, Tauri, RISC-V, and other low-level technologies
· Grow together with a group of passionate developers
· Build a real moat in compliance and audit scenarios

How to join?

· Send an email to chenyindrager@outlook.com
· Or submit an Issue / PR in any repository to introduce yourself
· We look forward to having you!

---

联系 / Contact

· 📧 邮箱 / Email: chenyindrager@outlook.com
· 🐙 GitHub: @breakevery

---

许可 / License

各仓库采用独立许可证，详见对应仓库的 LICENSE 文件。
Each repository carries its own license. See the LICENSE file in each repository.

---

⭐️ breakevery · 保持好奇，持续创造。
⭐️ breakevery · Stay curious, keep creating.