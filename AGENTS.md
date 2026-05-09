# OpenCode 工作区 — 项目宪法

## 项目定位

本仓库是 **OpenCode 会话暂存区与能力增强工作区**。核心用途有三：

1. **会话暂存（Staging）**：当用户有一个 OpenCode 会话不确定应归入哪个项目时，先放在这里处理、整理或等待归档。
2. **技能适配（Skill Adaptation）**：将 Codex 生态中的 skills、hooks、工作流和最佳实践适配到 OpenCode 环境；记录差异、补丁和迁移指南。
3. **能力增强（Enhancement）**：探索、实验和沉淀能提升 OpenCode 使用效率的规则、脚本、prompt 模板和自动化流程。

本项目 **不是** 谣言识别 / 虚假信息检测研究的正式仓库。该研究的正式仓库另有其地，本仓库中若出现遗留的谣言识别文件，视为历史误放，应归档或删除，不得作为本项目的正式内容引用。

## 语言规则

- 本项目的 Agent 默认使用**中文**与用户交流，除非用户明确要求使用其他语言。

## 核心目标

- 让 OpenCode 的使用体验逐步接近甚至超越 Codex 的工作流成熟度。
- 建立可复用的项目级规则，使 OpenCode 在处理复杂、长程任务时具备对齐、防漂移和状态续接能力。
- 成为 Codex → OpenCode 技能迁移的试验田和文档库。

## 目录约定

```
├── AGENTS.md                  # 本项目宪法（本文件）
├── README.md                  # 面向人类贡献者的快速入口
├── docs/                      # 项目文档、迁移指南和规则草案
│   ├── PROJECT_STATUS.md      # 当前状态、风险和待办的唯一入口
│   ├── codex_to_opencode/     # Codex → OpenCode 迁移专题
│   └── enhancement_notes/     # 能力提升实验记录
├── sessions/                  # 暂存的 OpenCode 会话材料
│   ├── archive/               # 已归档或已迁移到其他项目的会话
│   └── active/                # 当前活跃、尚未归档的暂存会话
├── skills/                    # 本地技能文件、补丁和适配脚本
│   ├── adaptive-intent-loop/  # adaptive-intent-loop 的 OpenCode 适配
│   └── other/                 # 其他技能的 OpenCode 适配
├── scripts/                   # 本项目使用的自动化脚本
├── .ai_state/                 # adaptive-intent-loop 任务状态（由脚本管理）
└── .codex/                    # Codex 相关配置（如有需要保留对照）
```

## 文件操作原则

- 除非用户明确要求，否则执行文件修改前无需主动创建备份。
- 如 Agent 认为某操作风险较高、确实需要备份，必须先向用户说明理由并征得同意。

## 工作流规则

### 会话暂存规则

- 放入 `sessions/active/` 的暂存会话必须附带一个简短的 `README.md` 或 `manifest.md`，说明：
  - 会话主题和来源
  - 预计最终归属项目
  - 当前阻塞点或待决策事项
  - 建议的下一步动作
- 暂存会话不应长期停留；用户或 Agent 应定期审阅 `sessions/active/`，将已完成或已确定归属的内容迁移到目标项目。
- 迁移完成后，在原位置保留一个指向最终归档位置的链接文件或记录，然后移入 `sessions/archive/`。

### 技能适配规则

- 每个 Codex 技能适配到 OpenCode 时，应在 `skills/<skill_name>/` 下建立独立目录。
- 目录中至少包含：
  - `ORIGIN.md`：原始 Codex 技能来源和链接。
  - `DIFF.md`：Codex 与 OpenCode 的能力差异、限制和变通方案。
  - `ADAPTATION.md`：实际适配后的使用说明和文件清单。
  - `patch/`：具体的补丁脚本或修改后的模板文件。
- 适配工作优先处理用户当前正在使用的技能；未请求的适配只记录需求，不主动实施。

### 能力提升规则

- 任何对 OpenCode 的增强实验（新脚本、新 prompt、新工作流）必须先在 `docs/enhancement_notes/` 中记录假设、实验设计和预期收益。
- 实验完成后必须记录结果、是否采纳、以及采纳后的使用方式。
- 被验证有效的增强应逐步沉淀为 `AGENTS.md` 的更新或 `skills/` 中的本地技能文件。

## 与其他项目的关系

- **谣言识别 / MERA 研究项目**：这是用户的主要科研项目，有独立的正式仓库和完整的 `AGENTS.md`、`docs/PROJECT_STATUS.md` 体系。本仓库中出现的谣言识别遗留文件（如 `rumor_AGENTS.md`、`rumor_README.md`、`my_paper.md`）是历史误放，不属于本项目内容，应删除或归档。
- **全局 OpenCode 配置**：`C:\Users\duanz\.config\opencode\` 下的全局配置（如 `AGENTS.md`、`STRUCTURE.md`、`skills/`）是跨项目默认。本项目的 `AGENTS.md` 只覆盖本项目范围内的特殊规则；不重复全局已明确的通用约定。

## 状态维护规则

- `docs/PROJECT_STATUS.md` 是本项目状态的唯一入口。每次完成以下任一事项后，Agent 必须主动更新它：
  - 新增、迁移或归档一个暂存会话。
  - 完成或放弃一项技能适配。
  - 完成一项增强实验并得出采纳/否决结论。
  - 项目规则、目录结构或下一步优先级发生变化。
- 状态文件至少要同步更新：已完成、未完成、当前阻塞点、下一步最优先事项、最近更新时间。

## Git 进度保存规则

- 本项目 GitHub 远程仓库为 `origin`：`https://github.com/Duanzhoutao/opencode.git`。
- 每次完成规则更新、技能适配、脚本或状态文档后，必须检查 `git status` 和必要 diff，只暂存本次任务相关文件，使用清晰提交信息保存进度，并推送到远程仓库；用户明确要求不提交或不推送时除外。
- 提交前必须用 `git status --short` 和 `git diff --cached --name-status` 确认暂存区只包含本次任务相关文件。
- 不得提交 `.ai_state/` 中的运行产物、SSH 私钥、API Key、大型二进制文件或临时归档。`.ai_state/` 本身应列入 `.gitignore`。
- `desktop/` 目录下的 OpenCode 安装二进制文件只作本地使用，不提交 Git。

## 命名规范

- 文档使用大写英文文件名或清晰中文名。
- 脚本文件使用小写英文、下划线或连字符命名。
- 暂存会话目录使用 `YYYYMMDD_short_description` 格式。
- 禁止用 `test`、`new`、`final`、`temp` 这类无法追踪的名字作为正式目录或文件名。

## 禁止事项

- 不得将谣言识别项目的实验代码、数据、论文材料或正式文档作为本项目内容处理或提交。
- 不得在 `sessions/active/` 中无限堆积无说明、无归属的会话材料。
- 不得未经记录直接修改 `AGENTS.md` 或其他项目级规则；修改前应在 `docs/` 中留下变更理由和版本记录。
- 不得用旧对话印象替代 `docs/PROJECT_STATUS.md` 判断项目状态。

## 完成定义

- 一个暂存会话完成：已明确最终归属项目，已迁移或已归档，原位置已记录去向。
- 一项技能适配完成：差异文档完整，适配文件可用，至少有一个成功使用记录。
- 一项增强实验完成：假设、过程、结果和采纳结论均已记录，且已沉淀为可复用规则或脚本。
- 一个文档完成：说明事实来源、当前结论、待确认项和更新时间。

## Adaptive Intent Loop

本项目已启用 adaptive-intent-loop 工作流。当用户要求开始复杂任务时：

1. 先运行 `start_task.py` 初始化任务（三种模式：全新 / 继承前任务 / 继续当前）。
2. 对齐阶段：完成核心意图对齐，填充 `.ai_state/` 下的 alignment 文件。
3. 执行阶段：运行 `enter_execution.py --confirmed --agent opencode` 后进入。
4. 工作过程中：每轮更新 `20_work/thinking_analysis.md` 和 `40_resume/resume_prompt.md`。
5. 任务结束：运行 `close_task.py` 关闭任务。

详见全局 skill：`C:\Users\duanz\.agents\skills\adaptive-intent-loop\SKILL.md`
