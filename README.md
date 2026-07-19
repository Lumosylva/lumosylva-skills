# Lumosylva Skills

Claude Code 插件集合，提供结构化的编程专家 Skill 工作流。

## 设计理念

AI 编程工具往往过于急切——在未获得明确许可的情况下擅自修改代码，假设自己比用户更了解情况。Lumosylva Skills 通过强制性的模式声明和严格的职责边界，确保 AI 始终在正确的阶段做正确的事，避免未经授权的修改和破坏性变更。

## 插件列表

| 插件 | 说明 | 路径 |
|------|------|------|
| [project](plugins/project) | 结构化编程专家 Skill，五种协作模式引导严谨的软件开发工作流 | `plugins/project` |

## 工作流概览

```
研究 → 创新 → 规划 → 执行 → 审查
  ↑                           │
  └───── 发现问题时回退 ──────┘
```

每次新对话默认进入 **研究模式**，通过明确的信号指令切换到下一阶段。

## 五种协作模式

| 模式 | 指令 | 目的 | 核心能力 |
|------|------|------|----------|
| 研究 | `/project-research` | 信息收集与深入理解 | 读取文件、分析架构、识别技术债务 |
| 创新 | `/project-innovate` | 头脑风暴潜在方法 | 探索多种方案、评估利弊、记录发现 |
| 规划 | `/project-plan` | 创建详尽的技术规范 | 文件路径、函数签名、清单生成 |
| 执行 | `/project-execute` | 准确实施已批准的计划 | 按清单逐项实施、记录进度 |
| 审查 | `/project-review` | 验证实施与计划的符合度 | 逐行对比、标记偏差、准备提交 |

## 安装

### 从 GitHub 安装

```bash
# Claude Code
claude plugin install Lumosylva/lumosylva-skills

# MiMoCode
mimo plugin install Lumosylva/lumosylva-skills
```

### 手动安装

将 `plugins/` 目录下的插件文件夹复制到你的 Skill 目录中：

- Claude Code: `.claude/skills/`
- MiMoCode: `.mimocode/skills/`

## 核心协议

- **模式声明**：每个响应开头必须用 `[MODE: XXX]` 声明当前模式
- **职责隔离**：每种模式只能做该阶段允许的事
- **回退机制**：执行阶段发现问题时，自动回到规划模式重新调整
- **模式切换**：必须通过明确信号（如 `/project-execute`）触发，不可自行切换

## 占位符说明

| 占位符 | 说明 | 示例 |
|--------|------|------|
| `TASK_FILE_NAME` | 任务文件名 | `2025-01-14_1` |
| `TASK_IDENTIFIER` | 任务短标识 | `fix-cache-bug` |
| `MAIN_BRANCH` | 主分支名 | `main` |
| `YOLO_MODE` | 确认模式 | `Ask` / `On` / `Off` |

### Yolo 模式

- **Ask**：每个步骤前询问用户确认
- **On**：自动执行所有步骤（高风险）
- **Off**（默认）：要求每个重要步骤的用户确认

## 贡献

欢迎提交 Issue 和 Pull Request。

## 许可

MIT License - 详见 [LICENSE](LICENSE)
