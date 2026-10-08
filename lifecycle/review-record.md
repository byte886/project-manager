# lifecycle 文档评审记录

> 记录对 lifecycle/ 全部文档的评审结论。
> 各阶段"应该有什么文档"的标准清单，见 [项目管理标准](../standards/project-management-standard.md)（第四节），本页不重复。

---

## 评审依据

- [项目管理标准](../standards/project-management-standard.md)：PMBOK五阶段、个人项目管理、SOP标准结构
- [文档评审标准](../standards/document-review-standard.md)

---

## 评审结论（已全部完成）

| 阶段 | 文档 | 结论 |
|---|---|---|
| **启动 start** | `initiate.md` | ✅ 已按标准重写，聚焦启动步骤+目录模板+总纲模板+检查清单 |
| **规划 planning** | `project-templates.md` | ✅ 已优化，开头加"场景/项目规模→模板"快速路由 |
| | `idea-to-tickets/` | ✅ 完整保留，流水线清晰（clarify→spec→slice→explain） |
| **执行 execution** | `status/active-ledger.md` | ✅ 结构清晰、内容通用（任务状态+问题台账） |
| | `memory/decision-memory.md` | ✅ 内容通用（决策记录+记忆） |
| | `handoff/handoff.md`、`handover-sop.md` | ✅ 分工清晰（活日志写什么 + 交接怎么做） |
| | `batch/batch-execution.md` | ✅ 内容通用（批量纪律+并行长任务） |
| | `governance/execution-governance.md` | ✅ 结构清晰、内容通用（冷启动+动作机制+文档同步） |
| **监控 monitor** | `monitor.md` | ✅ 已按标准重写，通俗化（决策权/暂停条件/自查） |
| | `maintenance-sop.md` | ✅ 已按标准重写，通俗化（信息路由/提交检查/接手六问） |
| **收尾 close** | `close.md` | ✅ 已按标准重写，聚焦收尾，月度巡检内容移至monitor |

---

## 本次重写解决的问题

1. **通俗化**：去掉/解释了专业术语（SSOT、ADR、治理卡、健康灯等），用大白话说明。
2. **去重叠**：
   - initiate.md 删掉与目录模板重复的"五条规律、设计依据"
   - close.md 删掉属于监控阶段的"月度巡检"，改放指针
3. **去企业级内容**：删除干系人签字、预算结算、变更分级、RACI等个人用不上的内容。
4. **去业务绑定**：全部用虚构 bookshelf 项目做示例，无具体业务/项目名残留。
5. **加路由**：每个大文件开头加"场景/项目规模→用哪个"的快速定位表。
6. **标准对齐**：SOP按"目的范围/前置条件/流程步骤/成功标准/异常处理/参考"组织，按需裁剪。

---

## 各阶段无重叠确认

- 启动 → 规划 → 执行 → 收尾，各阶段文档职责清晰。
- 监控贯穿执行，维护操作统一在 monitor/maintenance-sop.md，其他阶段只放指针。
- 决策记录、状态台账每个项目只在一处（六槽位或工程目录二选一）。
