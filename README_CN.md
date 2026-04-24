<div align="center">

[English](README.md) | **中文**

# Hyrex Chia

**Gameplay / Systems Programmer** · AAA 跨 Anvil / Luminous / CryEngine 3 · 当前 UE5

![C++](https://img.shields.io/badge/C++-00599C?logo=cplusplus&logoColor=white)
![Unreal Engine 5](https://img.shields.io/badge/Unreal_Engine_5-0E1128?logo=unrealengine&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?logo=anthropic&logoColor=white)

马来西亚 · 新加坡 PR · 接受远程

> *交付 gameplay 系统，以及让它们能交付的工具。*
>
> *我仍然手动跑的那道筛子 — 这件事的回报值不值得投入？它有没有解决实际问题？有 AI 之后尤甚。*

</div>

---

<div align="center">

### ![现在](https://img.shields.io/badge/现在-8B6F47?style=for-the-badge)

</div>

**Intermediate Gameplay Programmer @ TenTen Studios。** UE5 单机 action RPG，vertical-slice 原型阶段。撑起项目的 tech 担当，主导技术决策。

- **C++ gameplay 核心系统**：覆盖 UI/UX、state machines、3C、behavior-oriented actor components、GAS、Gameplay Tags、Behavior Tree、按需 Subsystems，服务于 prototype。
- **Data-driven 系统架构**：DataAsset + DeveloperSettings 作为作者层，runtime validator 和 linter 作为审计层。设计师无需动代码即可迭代。
- **Tooling**：基于内容团队反复出现的痛点（source control 冲突、数据引用损坏、批量操作）做 tooling。示例：[uasset-json-exporter](https://github.com/hchia93/uasset-json-exporter)、[uasset-name-linter](https://github.com/hchia93/uasset-name-linter)。
- **Workflow**：2026 年 3 月起用 Claude Code 协同。重心从 code-technique 导向转到 system-delivery 导向。

---

<div align="center">

### ![过往](https://img.shields.io/badge/过往-8B6F47?style=for-the-badge)

AA & AAA 制作，2016 - 2024，2025 - 2026。

| 作品 | 类型 | 引擎 | 工作室 |
|--|--|--|--|
| *Bloodwell* | `单` | Unreal Engine 5 | TenTen Studios |
| *Skull & Bones* | `多` | Anvil & Phoenix (Ubisoft 自研) | Ubisoft Singapore |
| *Final Fantasy XV* | `单` | Luminous (Square Enix 自研) | Streamline Studios (外包) |
| *Sniper Ghost Warrior: Contracts* | `多` | CryEngine 3 | Streamline Studios (外包) |
| *NDA Projects* | `单` `多` | Unreal Engine 4 | Streamline Studios (未发行) |

</div>

- **引擎经验**：Anvil、Luminous、CryEngine 3 在出货 AAA 上；UE4 / UE5 在内部与原型上。UE 经验非连续。
- **GaaS gameplay 系统 (Skull & Bones)**：Codex、crafting、Mail（Send / Fetch / Claim / Update 多动词 RPC + 跨团队分页 fetch）、captain customization、shop / offer extension。内容团队可扩展，无需改代码。Gameplay Runtime 侧 ownership；与 backend 侧协作保证 feature 一致性与交付。
- **Async + server-authoritative 模式**：callback chain 排序（Lazy → Periodic Sync）、simulation-vs-actual claim 和解、runtime ↔ backend 桥接、account persistence。
- **Production CI 纪律**：CI 下 regression-testable 的 C++（DTest — 每日在 build artifact 上跑 regression，flag-not-block submit）。

<div align="center">

---

通过 GitHub 联系。

</div>
