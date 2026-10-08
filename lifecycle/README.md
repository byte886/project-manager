# lifecycle · 项目生命周期

> 一个项目从开头到收尾的完整过程，分5个标准阶段（对应PMBOK五过程组）。
> **标准依据**：[项目管理标准](../standards/project-management-standard.md)

---

## 5个阶段一句话定位

| 阶段 | 核心问题 | 通俗理解 |
|---|---|---|
| **1. start 启动** | 值不值得做？目标是什么？ | 想清楚、定目标、搭骨架 |
| **2. planning 规划** | 具体怎么做？怎么拆？ | 写需求、拆工单、定顺序 |
| **3. execution 执行** | 按计划做出来 | 干就完了，边做边记录 |
| **4. monitor 监控** | 做得怎么样？跑偏没？ | 定期自查、定暂停条件 |
| **5. close 收尾** | 怎么结束？学到什么？ | 交付、归档、释放、复盘 |

> 监控贯穿执行全程；敏捷项目里规划/执行/监控在短周期中重复。

---

## 目录结构

```
lifecycle/
├── start/              # 启动
│   └── initiate.md
├── planning/           # 规划
│   ├── project-templates.md     # 开头文档模板（PRD/BRD/系统要求等）
│   └── idea-to-tickets/          # 从模糊想法到可执行工单
├── execution/          # 执行
│   ├── status/                   # 进度和问题台账
│   ├── memory/                   # 决策和工程记忆
│   ├── handoff/                  # 交接协作
│   ├── batch/                    # 批量执行
│   └── governance/               # 执行治理
├── monitor/            # 监控
│   ├── monitor.md                # 监控方法论（决策权/暂停条件/自查）
│   └── maintenance-sop.md        # 维护操作（信息路由/提交检查/接手）
└── close/              # 收尾
    └── close.md
```

---

## 你遇到什么，用哪个

| 你遇到什么 | 用哪个 |
|---|---|
| 刚开始新项目，不知道怎么开头 | [start/initiate.md](start/initiate.md) |
| 需求模糊，要问清楚 / 要拆工单 | [planning/idea-to-tickets/](planning/idea-to-tickets/README.md) |
| 要写PRD、BRD等开头文档 | [planning/project-templates.md](planning/project-templates.md) |
| 要追踪进度、记问题 | [execution/status/active-ledger.md](execution/status/active-ledger.md) |
| 要留决策记录、存工程记忆 | [execution/memory/decision-memory.md](execution/memory/decision-memory.md) |
| 要开新窗口交接、派任务给AI | [execution/handoff/](execution/handoff/README.md) |
| 要跑批量/并行长任务 | [execution/batch/batch-execution.md](execution/batch/batch-execution.md) |
| 换会话不知道从哪开始、怕漏改文档 | [execution/governance/execution-governance.md](execution/governance/execution-governance.md) |
| 要定监控规则、每周自查 | [monitor/monitor.md](monitor/monitor.md) |
| 要提交、要新窗口接手验收 | [monitor/maintenance-sop.md](monitor/maintenance-sop.md) |
| 项目做完/砍掉，要收尾 | [close/close.md](close/close.md) |
