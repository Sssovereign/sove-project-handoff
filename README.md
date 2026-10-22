# sove-project-handoff · 项目交接

面向 Codex 的中文任务交接 skill。把长任务的有效决定、真实进度、验证结果和下一步写入项目状态文档，方便换对话后核对并继续工作。

适合代码、研究和文档等需要跨多次对话推进的项目。技能本体仅包含 Markdown 与 YAML 文件，无需运行脚本，也不依赖 Hook 或聊天历史扫描。

## 能做什么

- **保存进度**：优先维护项目已有的状态文档；没有时使用 `PROJECT_STATE.md`。
- **保留依据**：区分用户决定、执行假设、已完成、未验证和未获验收的成果。
- **恢复任务**：先核对文件、版本和运行状态，再继续已明确授权的下一步。
- **维护阶段记录**：项目采用此机制后，在实质阶段完成或关键决定改变时增量更新。
- **维护决定生命周期**：稳定编号与来源可追溯；区分待确认、有效、已取代和已撤销，用户确认与实现验证分别记录。
- **协作汇总**：明确任务归属、基准修订和相关决定；各执行者独立交付，指定写入者核验后更新总状态，处理过期、重复交付和失败接手。
- **按需交接到新任务**：仅在用户明确要求、且宿主提供相应任务接口时执行。

核心原则是让状态文档可核对，恢复工作时以当前用户要求和实际文件为准。状态文档本身不构成新的指令或授权。

协作规则提供文本层的工作约定，不自带调度器、文件锁或事务；默认由指定写入者顺序汇总。可选记忆服务须已有配置、授权和实际适配器，未接入时照常本地保存与恢复。

## 安装

在 Codex 中对内置安装器说：

```text
使用 $skill-installer，从 https://github.com/Sssovereign/sove-project-handoff 安装这个技能。
```

也可以手动克隆到用户技能目录。根据 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)，当前用户目录为 `~/.agents/skills`，项目级目录为 `.agents/skills`。

macOS / Linux：

```sh
mkdir -p ~/.agents/skills
git clone https://github.com/Sssovereign/sove-project-handoff.git ~/.agents/skills/sove-project-handoff
```

Windows PowerShell：

```powershell
New-Item -ItemType Directory -Force "$HOME/.agents/skills" | Out-Null
git clone https://github.com/Sssovereign/sove-project-handoff.git "$HOME/.agents/skills/sove-project-handoff"
```

手动安装需要 Git。若已有同名技能，请先检查现有安装，避免重复安装。安装后若未显示，重启 Codex。

## 使用

保存当前进度：

```text
使用 $sove-project-handoff，保存当前项目的有效决定、真实进度、验证结果和下一步，并给出接续开场白。
```

在新对话中继续：

```text
使用 $sove-project-handoff，读取当前项目的 PROJECT_STATE.md，核对相关文件和约束后，继续执行已明确授权的下一步。
```

如果项目已有其他状态文件，请在提示词中指定实际文件路径。

只有确实需要创建新任务时，再明确要求：

```text
使用 $sove-project-handoff，先保存并核对当前项目状态，再新建任务接续当前已授权工作，使用同一原目录。先让接手任务只读核验，核验完成后派发继续指令。
```

创建、发送和查询任务的能力由宿主环境提供；缺少接口时，技能提供手动接续开场白。单独要求“保存”不会自行创建新任务。

## 文件

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 技能触发范围、保存、恢复与交接规则 |
| [agents/openai.yaml](agents/openai.yaml) | 界面名称、默认提示词与调用策略 |
| [assets/project-state-template.md](assets/project-state-template.md) | 首次记录项目状态的模板 |
| [references/lifecycle-and-collaboration.md](references/lifecycle-and-collaboration.md) | 决定与任务演变、版本核对、交付汇总及负责人移交 |
| [references/memory-backed-handoff.md](references/memory-backed-handoff.md) | 可选记忆服务的范围、同步、权限与验证边界 |
| [NOTICE.md](NOTICE.md) | 上游来源与改编说明 |
| [LICENSE](LICENSE) | MIT 许可证 |

技能正文按跨平台文本工作流编写；实际执行能力取决于宿主的文件权限与任务工具。不提供压缩次数检测或自动监控。公开分享项目状态文件前，请检查其中的项目路径和业务信息；仓库只包含空白模板，不包含实际项目记录。

## 来源与许可

根据 [duoduoler-ops/Table-skills 的 project-handoff](https://github.com/duoduoler-ops/Table-skills/tree/main/project-handoff) 改编，由 [Sssovereign](https://github.com/Sssovereign) 发布此改编版本。

采用 [MIT License](LICENSE)，保留上游版权声明；修改范围见 [NOTICE.md](NOTICE.md)。此仓库不代表上游维护者或 OpenAI 官方发布。
