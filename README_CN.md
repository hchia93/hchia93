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
> *我仍然手动跑的那道筛子，有 AI 之后尤甚：这件事的回报值不值得投入，它有没有解决实际问题。*

</div>

---

### 现在

**Intermediate Gameplay Programmer，TenTen Studios。** UE5 单机 action RPG，vertical-slice 原型阶段。一个人撑起项目的 tech 担当，主导技术决策。

- **C++ gameplay 系统**：data-driven 架构（DataAsset、DeveloperSettings、payload 定义）、UI/UX（HUD、菜单、浮空生命条）、state machines、attack payloads（damage、status、interrupt）、shield / health、3C。能力 / AI 框架搭在 GAS + Gameplay Tags + Behavior Tree 上。
- **Tooling**：编辑器 commandlet、资产命名 linter、构建流程纪律。动机来自反复出现的内容团队痛点（SVN 冲突、版本问题、数据引用损坏）。已公开：[uasset-json-exporter](https://github.com/hchia93/uasset-json-exporter)、[uasset-name-linter](https://github.com/hchia93/uasset-name-linter)。
- **Workflow**：2026 年 3 月起用 Claude Code 协同交付。重心从 "代码技术导向" 转到 "系统交付导向"。
- **Code shape**：系统写得 debuggable 且 regression-testable，harness 一旦值得上就能直接接入。

欢迎就 C++ 系统、gameplay 工程、tooling 方向聊。当前项目的细节受 NDA 约束。

---

### 过往

AAA 制作，2016 – 2024。

| 作品 | 引擎 | 工作室 |
|--|--|--|
| *Skull & Bones* | Anvil (Ubisoft 自研) | Ubisoft Singapore |
| *Final Fantasy XV* | Luminous (Square Enix 自研) | Streamline Studios (外包) |
| *Sniper Ghost Warrior: Contracts* | CryEngine 3 | Streamline Studios (外包) |

- **引擎轨迹**：UE4、Luminous、CryEngine 3、Anvil、UE4/UE5。UE 经验非连续。
- **AAA 出货过的系统**：multi-verb RPC API（Send / Fetch / Claim / Update）+ 跨团队 paginated fetch、async callback chain sequencing（Lazy → Periodic Sync）、simulation vs actual claim 和解、runtime ↔ backend 桥接、account persistence、progression 系统（codex、crafting、tracker）。
- **CI 关卡下的 auto-testable C++**：生产级单元测试，失败 flag 团队。
- **Modern C++**：C++20/23、concepts、小 template wrapper。
- **日常工具链**：`C++` · `Python` · `SQL` · `Unreal Engine` · `Perforce` · `SVN` · `Git` · `Claude Code` · `JIRA` · `Confluence`。

<div align="center">

---

通过 GitHub 联系。

</div>
