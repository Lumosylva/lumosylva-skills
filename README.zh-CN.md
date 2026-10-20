<p align="center">
  <img src="assets/lumosylva-skills-logo.svg" alt="Lumosylva Skills logo" width="112" height="112">
</p>

<h1 align="center">Lumosylva Skills</h1>

<p align="center">
  <a href="https://github.com/Lumosylva/lumosylva-skills/releases/latest"><img src="https://img.shields.io/github/v/release/Lumosylva/lumosylva-skills" alt="Latest Release"></a>
  <a href="https://github.com/Lumosylva/lumosylva-skills/stargazers"><img src="https://img.shields.io/github/stars/Lumosylva/lumosylva-skills" alt="GitHub Stars"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/Lumosylva/lumosylva-skills" alt="License"></a>
  <a href="https://skills.sh/"><img src="https://img.shields.io/badge/Lumosylva%20Skills-skills.sh%20Compatible-2ea44f" alt="Lumosylva Skills - skills.sh Compatible"></a>
</p>

<p align="center"><a href="README.md">English</a> | <a href="README.zh-CN.md">简体中文</a></p>

一组用于规范化软件开发流程的 Agent Skills，可通过 `skills` CLI 安装。

## 设计理念

Lumosylva Skills 将调研、方案探索、规划、实施和审查分为不同模式。每种模式分别规定职责和授权范围。安装技能不会自动启用模式，也不会覆盖 Agent 原有的指令和权限。

## 技能列表

仓库采用 `skills/<skill-name>/SKILL.md` 结构：

| 技能 | 用途 |
|------|------|
| [general-spec](skills/general-spec/SKILL.md) | 可选的流程说明与任务文件模板 |
| [project-research](skills/project-research/SKILL.md) | 调研代码库 |
| [project-innovate](skills/project-innovate/SKILL.md) | 探索可选方案 |
| [project-plan](skills/project-plan/SKILL.md) | 制定实施计划 |
| [project-execute](skills/project-execute/SKILL.md) | 执行已批准的计划 |
| [project-review](skills/project-review/SKILL.md) | 核查实施结果 |

每个模式技能都可独立使用。如需流程概览与可选的任务文件模板，再安装 `general-spec`。

## 工作流程

```
调研 -> 构思 -> 规划 -> 执行 -> 审查
                ^        |
                +-- 发现问题（请求 project-plan）
```

需要哪个阶段，就明确调用对应技能。新会话不会自动进入任何模式；完成任务或遇到失败也不会自动切换模式。

## 五种协作模式

| 模式 | 技能 | 目标 | 主要工作 |
|------|------|------|----------|
| 调研 | `project-research` | 理解任务和代码库 | 阅读文件、报告约束；默认不改动工作区 |
| 构思 | `project-innovate` | 比较可选方案 | 探索方案与取舍，不实施修改 |
| 规划 | `project-plan` | 制定实施方案 | 编写待用户批准的清单，不修改代码 |
| 执行 | `project-execute` | 实施已批准的计划 | 按授权步骤修改并验证结果 |
| 审查 | `project-review` | 核查实施结果 | 报告偏差与风险，默认不修复或提交 |

## 安装

```bash
npx skills add Lumosylva/lumosylva-skills
```

CLI 可能自动识别 Agent，也可能提示选择目标。选择所需技能即可；每个模式都可独立使用。如需只查看可用技能而不安装：

```bash
npx skills add Lumosylva/lumosylva-skills --list
```

## 使用模式

请通过 Agent 的技能界面，或使用“请用 project-research 调研这个问题”之类的提示明确调用技能。有些 Agent 支持 `/project-research` 等快捷指令，具体取决于客户端。回答“同意”只表示批准计划，不会自动启用 `project-execute`；准备实施时请另行调用该技能。

模式生效期间，回复以 `[MODE: RESEARCH]`、`[MODE: INNOVATE]`、`[MODE: PLAN]`、`[MODE: EXECUTE]` 或 `[MODE: REVIEW]` 开头，其余内容遵循用户使用的语言。调研、构思、规划和审查默认只读。创建任务文件、分支、提交和推送都需另行授权。执行还必须有已批准的计划；超出计划的改动需要重新批准。

可选的 `general-spec` 技能提供任务文件模板，但不会自动加载或启用各模式技能。

### 步骤确认

`YOLO_MODE` 仅决定用户批准执行计划后是否逐步确认；它不会授权额外改动或破坏性操作。

- **Off**（默认）：每个重要实施步骤执行前确认。
- **Ask**：每个实施步骤执行前确认。
- **On**：在已批准的范围内连续执行，无需逐步确认。

## 参与贡献

欢迎提交 Issue 和 Pull Request。

## 许可证

MIT 许可证，详见 [LICENSE](LICENSE)。
