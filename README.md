<div align="center">

**English** | [中文](README_CN.md)

# Hyrex Chia

**Gameplay / Systems Programmer** · AAA across Anvil, Luminous, CryEngine 3 · now on UE5

![C++](https://img.shields.io/badge/C++-00599C?logo=cplusplus&logoColor=white)
![Unreal Engine 5](https://img.shields.io/badge/Unreal_Engine_5-0E1128?logo=unrealengine&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?logo=anthropic&logoColor=white)

Malaysia-based · Singapore PR · Remote-friendly

> *Ship gameplay systems, and the tools that make them shippable.*
>
> *The filter I still run by hand - is the return worth the effort? Does this solve a real problem? Even more so with AI.*

</div>

---

<div align="center">

### ![Currently](https://img.shields.io/badge/Currently-8B6F47?style=for-the-badge)

</div>

**Intermediate Gameplay Programmer @ TenTen Studios.** Developing UE5 single-player action RPG, vertical-slice prototype. Carrying the tech side of the project, leading the technical decisions.

- **C++ gameplay core systems**: Span across UI/UX, state machines, 3C, behavior-oriented actor components, GAS, Gameplay Tags, Behavior Tree, on demand Subsystems for the prototype.
- **Data-driven system architecture**: DataAsset + DeveloperSettings as the authoring surface, runtime validators and linters as the audit layer. Designers iterate without touching code.
- **Tooling**: Build tooling based on recurring content-team pain points (source control conflicts, broken data references, bulk actions). Examples: [uasset-json-exporter](https://github.com/hchia93/uasset-json-exporter), [uasset-name-linter](https://github.com/hchia93/uasset-name-linter).
- **Workflow**: Claude Code co-piloting since March 2026. Shift from code-technique first to system-delivery first.


---

<div align="center">

### ![History](https://img.shields.io/badge/History-8B6F47?style=for-the-badge)


AA & AAA production, 2016 - 2024, 2025 - 2026.



| Title | Type | Engine | Studio |
|--|--|--|--|
| *Bloodwell* | `SP` | Unreal Engine 5 | TenTen Studios |
| *Skull & Bones* | `MP` | Anvil & Phoenix (Ubisoft proprietary) | Ubisoft Singapore |
| *Final Fantasy XV* | `SP` | Luminous (Square Enix proprietary) | Streamline Studios (outsource) |
| *Sniper Ghost Warrior: Contracts* | `MP` | CryEngine 3 | Streamline Studios (outsource) |
| *NDA Projects* | `SP` `MP` | Unreal Engine 4 | Streamline Studios (unreleased) |

</div>


- **Engine exposure**: Anvil, Luminous, CryEngine 3 on shipped AAA; UE4 / UE5 on internal and prototype. UE experience is not continuous.
- **GaaS gameplay systems (Skull & Bones)**: Codex, crafting, mail with Send / Fetch / Claim / Update multi-verb RPC + paginated cross-team fetch, captain customization, shop / offer extension. Extensible by content team without code change. Gameplay Runtime side ownership; collaborate with backend side for feature consistency and delivery.
- **Async + server-authoritative patterns**: Callback chain sequencing (Lazy → Periodic Sync), simulation-vs-actual claim reconciliation, runtime ↔ backend bridging, account persistence.
- **Production CI discipline**: Regression-testable C++ under CI (DTest — daily regression runs on build artifacts, flag-not-block submission).

<div align="center">

---

Feel free to contact me!

</div>
