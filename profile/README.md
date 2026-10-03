# breakevery

> 开源内核研究组织。
> An open-source kernel research organization.

---

## 我们在做什么

**RiscDom（智芯城）** —— AI 协同工作运行时。
**RiscDom (智芯城)** — an AI collaborative work runtime.

让一群 AI 在可审计、可隔离的沙箱里分工干活。
Let a fleet of AIs divide work inside auditable, isolated sandboxes.

**一切动作进哈希链** —— 事后可对账、可归因。
**Every action enters a hash chain** — reconcilable and attributable after the fact.

这是合规场景的门票，也是我们唯一真正的护城河。
This is the ticket to compliance scenarios, and our only real moat.

---

## 格言

> **Freedom inside boundaries, audit outside the AI, root privilege with humans.**
> **边界之内自由，AI 之外审计，root 权限归人。**

---

## 项目

| 仓库 | 说明 |
|---|---|
| [`riscdom`](https://github.com/breakevery/riscdom) | 内核：agent / sandbox / audit / net / relay |
| [`riscdom-server`](https://github.com/breakevery/riscdom-server) | 控制平面：单机节点 HTTP 服务 + 最小 web 状态页 |
| [`riscdom-adminapp`](https://github.com/breakevery/riscdom-adminapp) | 管理程序：桌面（Tauri）+ 移动（Android） |

---

## 架构

```
Human (root)
  ↓
host（Rust + Tauri，唯一前端入口）
  ↓
{agent, sandbox, audit}
  ↑ 依赖方向单向无环
agent → sandbox → audit
```

三仓单向依赖：
Three repositories, one-directional dependencies:

- `riscdom-adminapp` → `riscdom-server`（HTTP API）
- `riscdom-adminapp` → `riscdom`（host-core / net，编译期）
- `riscdom-server` → `riscdom`（host-core，编译期）

---

## 四条红线

1. **无内置 supervisor** —— 内核只给机制，不给策略。
   **No built-in supervisor** — the kernel provides mechanisms, not policies.

2. **无官方运营服务** —— 部署者自己跑节点 / 服务器。
   **No official hosted service** — deployers run their own nodes and servers.

3. **非通用沙箱** —— RISC-V 是主调、基底、默认实现，但不是唯一。
   **Not a general-purpose sandbox** — RISC-V is the primary, base, and default implementation, but not the only one.

4. **审计不变量不动** —— 哈希公式不动，audit v2 只扩语义。
   **Audit invariants are frozen** — the hash formula never changes; audit v2 only extends semantics.

---

## 当前状态

- **v1.0 主体完成**（2026-10）
- 内核 `v1.0.1` · 控制平面 `v1.0.2` · 管理程序 `v1.1.0`（规划中）
- **v1.x 方向**：server 产品化 · APP 移动端 · 跨区域 M · 商业化

---

## 许可

[Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)
