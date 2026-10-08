# planning · 项目规划

> 项目启动后，具体怎么做？需求是什么？怎么拆成小工单？

---

## 这个阶段回答什么问题

| 核心问题 | 通俗解释 |
|---|---|
| 要做什么？ | 需求范围、验收标准、不做什么 |
| 具体怎么做？ | 拆成小工单、定先后顺序、识别依赖 |

---

## 目录内容

| 内容 | 作用 |
|---|---|
| `project-templates.md` | 规划阶段文档模板（商业论证、需求、系统要求等） |
| `idea-to-tickets/` | 从"模糊想法"到"可执行工单"的完整方法 |

### idea-to-tickets 的流水线

```
模糊想法
  → clarify（拷问澄清）：把需求问清楚
  → spec（写成规范）：对齐结论，换会话不忘
  → slice（拆工单）：拆成可独立完成的小工单
  → 执行
  → explain（讲清楚）：改动/方案讲给别人听
```

---

## 你遇到什么，看哪里

| 你遇到什么情况 | 看哪里 |
|---|---|
| 需求模糊，怕做完不对，要把需求问清楚 | `idea-to-tickets/references/clarify.md` |
| 问清楚了，要写成规范，换会话不忘 | `idea-to-tickets/references/spec.md` |
| 任务太大，要拆成可执行的小工单 | `idea-to-tickets/references/slice.md` |
| 改完了/做完了，要把方案讲清楚 | `idea-to-tickets/references/explain.md` |
| 要派任务给不同角色/AI协作 | `idea-to-tickets/references/role-collaboration.md` |
| 想走完整流程（澄清→规范→拆单） | `idea-to-tickets/references/playbook.md` |
| 要写商业论证（BRD）、需求文档（PRD）等 | `project-templates.md` |

---

## 规划阶段核心产出

完成规划后，你应该有：
1. ✅ 明确的**需求范围**和验收标准
2. ✅ 拆好的**小工单**（每个能独立完成、独立验收）
3. ✅ 工单的**先后顺序和依赖关系**
4. ✅ 识别出的**主要风险**

> 规划完成后进入**执行阶段**（execution/）：按工单做。
