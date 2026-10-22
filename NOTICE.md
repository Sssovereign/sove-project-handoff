# 来源与本地修改

本技能依据 duoduoler-ops/Table-skills 的 project-handoff 机制改写。

- 上游：https://github.com/duoduoler-ops/Table-skills/tree/main/project-handoff
- 核对日期：2026-09-21（main 分支当日内容，未固定提交版本）
- 上游版权：Copyright (c) 2026 duoduoler-ops
- 许可：MIT，完整原始文本见 LICENSE。

个人版调整：改名为 sove-project-handoff；去除 Windows 专用 Hook、计数器和强制压缩提醒；使用跨平台 Markdown 状态记录；加入已有状态文档的阶段维护约定。2026-10-23增加决定生命周期、任务阶段、基准修订、指定写入者汇总、交付去重与失败接手规则，并更新状态模板；加入有范围限制的首次回填、候选流程引用与归档规则。同步可选记忆服务协作说明，保留本地核对、项目范围和授权边界。

信息分层、来源与版本治理、可复用流程等设计参考 [TencentDB Agent Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)；本技能中的决定状态与协作约定是本地设计，不是上游接口能力或性能承诺。只提供文本流程，未内置 TencentDB 连接器、引入其运行时或复制其实现代码；来源版本与适配边界见 references/memory-backed-handoff.md。未引入网页替身功能。此版本为本地改编，不代表上游维护者发布。
