# project-manager

个人 / 小团队多项目并行时的轻量项目管理方法论技能：PPM 项目组合层（选对项目、季度盘点、优先级排序、状态与健康灯）、单项目生命周期层（启动 / 执行监控 / 收尾归档）、阶段门评审层（G1/G2/G3、Go-Conditional-Hold-Kill），纯 Markdown 模板、全平台通用。

## 使用

这是豆包（及兼容 Agent）的**本地技能（Skill）**。完整能力、触发场景与操作流程见入口文档 **[`SKILL.md`](SKILL.md)**，Agent 命中时首先读取它；下列子目录按需加载，不必一次全读。

## 目录

- `SKILL.md`：技能入口、三层架构与模块路由
- `references/`：按需细读的方法论与模板
  - 生命周期：`portfolio`（组合盘点）/ `initiate`（启动建目录）/ `monitor`（治理监控）/ `gates`（阶段门）/ `close`（收尾归档）/ `brd`（商业需求）
  - 执行期：`execution-governance`（记忆/台账/AGENTS/冷启动）/ `execution-ops`（变更分级/批量/同步/存储）
  - 模板：`templates`（生命周期+标配文件）/ `templates-execution`（执行期台账与 SOP）/ `templates-standards`（工程规范与过程件：环境/命名/编码/文档写作/质量验证/状态查询/报告/测试/整改/CHANGELOG）

## 许可

[MIT](LICENSE) © 2026 byte886
