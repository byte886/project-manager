---
name: project-manager
description: 个人/小团队的轻量项目管理。覆盖项目全生命周期（启动、规划、执行、监控、收尾），并提供需求澄清到拆单（idea-to-tickets）、工程规范（命名/代码风格/文档/AGENTS）、文档评审与技能优化方法。适用于新项目立项、需求拆解、进度追踪、交接归档、文档与技能优化。纯方法论，跨平台通用。
compatibility: 纯方法论，跨平台通用
---

# project-manager · 个人轻量项目管理

> 按"你遇到什么问题"找对应文档，不用全读。
> **总标准**：[standards/project-management-standard.md](standards/project-management-standard.md)（生命周期、个人项目管理、SOP结构的权威依据）

---

## 执行原则

- **个人版，别搞复杂**：能用一句话说清，别写一页纸。
- **按需读**：遇到什么问题，读对应文档。
- **小项目反触发**：一两天能做完的小任务，README + AGENTS + 任务状态就够，不必用全套。
- **一条信息只放一处**：其他地方放指针，避免改漏、说法打架。

---

## 场景总表

### 〇、先看标准

| 你遇到什么 | 用什么 |
|---|---|
| 想了解项目管理标准方法、生命周期怎么分、SOP怎么写 | `standards/project-management-standard.md` |
| 要评审/优化一批文档，需要评审标准 | `standards/document-review-standard.md` |

---

### 一、项目生命周期

#### 1. 启动（lifecycle/start/）
| 你遇到什么 | 用什么 |
|---|---|
| 新项目第一步做什么、建什么目录、怎么写总纲 | `lifecycle/start/initiate.md` |

#### 2. 规划（lifecycle/planning/）
| 你遇到什么 | 用什么 |
|---|---|
| 要写PRD、BRD、系统要求、工作流等开头文档 | `lifecycle/planning/project-templates.md` |
| 需求没说清，要拷问澄清 | `lifecycle/planning/idea-to-tickets/references/clarify.md` |
| 要把需求写成带验收的规范 | `lifecycle/planning/idea-to-tickets/references/spec.md` |
| 要把大任务拆成小工单 | `lifecycle/planning/idea-to-tickets/references/slice.md` |
| 要把改动/方案讲清楚 | `lifecycle/planning/idea-to-tickets/references/explain.md` |
| 要做角色分工 | `lifecycle/planning/idea-to-tickets/references/role-collaboration.md` |

#### 3. 执行（lifecycle/execution/）
| 你遇到什么 | 用什么 |
|---|---|
| 要追踪进度、记问题 | `lifecycle/execution/status/active-ledger.md` |
| 要留决策记录、存工程记忆 | `lifecycle/execution/memory/decision-memory.md` |
| 要开新窗口交接 | `lifecycle/execution/handoff/handover-sop.md` |
| 要派任务给另一个AI（任务交接书） | `lifecycle/execution/handoff/handover-sop.md` |
| 交接活日志怎么写 | `lifecycle/execution/handoff/handoff.md` |
| 要跑批量/并行长任务 | `lifecycle/execution/batch/batch-execution.md` |
| 换新会话冷启动、批量改文件、怕漏改文档 | `lifecycle/execution/governance/execution-governance.md` |

#### 4. 监控（lifecycle/monitor/）
| 你遇到什么 | 用什么 |
|---|---|
| 定决策权、暂停条件、每周自查 | `lifecycle/monitor/monitor.md` |
| 信息放哪、提交前检查、新窗口接手验收 | `lifecycle/monitor/maintenance-sop.md` |

#### 5. 收尾（lifecycle/close/）
| 你遇到什么 | 用什么 |
|---|---|
| 项目做完/砍掉，要收尾、归档、复盘 | `lifecycle/close/close.md` |

---

### 二、工程规范（写代码/写文档）

| 你遇到什么 | 用什么 |
|---|---|
| 要定命名规范 | `standards/naming-convention.md` |
| 要定代码风格 | `standards/code-style.md` |
| 要写文档指南 | `standards/documentation-guide.md` |
| 要写 AGENTS.md | `standards/agents.md` |

---

### 三、技能类项目

| 你遇到什么 | 用什么 |
|---|---|
| 要优化一个技能（目录、命名、SKILL.md、文档合并） | `skills/skill-optimization.md` |

---

## 砍掉了什么（个人用不上的企业级内容）

- ❌ 变更分级 L0/L1/L2
- ❌ RACI、健康灯等企业术语
- ❌ 重型质量验证规范、状态查询协议
- ❌ 干系人签字、预算结算等企业收尾流程
