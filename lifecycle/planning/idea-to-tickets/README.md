# idea-to-tickets · 从想法到工单

> 把模糊的想法，变成AI真正能执行、能验收的东西。

---

## 源头
- 内核来源：Matt Pocock 开源 Skills 的 `grill-me` / `to-spec` / `to-tickets`
- 仓库：https://github.com/mattpocock/skills
- 本目录是其与工具解耦的方法论封装：不依赖特定 IDE、命令或 GitHub，只固化"怎么想、怎么问、怎么拆、怎么讲"
- 我们额外加了：explain（讲清楚）、role-collaboration（派任务）

---

## 目录结构

```
idea-to-tickets/
├── references/          # 方法论文档
│   ├── clarify.md      # 动手前先反问清楚
│   ├── spec.md          # 写成带验收的规范
│   ├── slice.md         # 拆成可独立验收的小工单
│   ├── explain.md       # 选最小视图讲清楚
│   ├── role-collaboration.md  # 角色分工
│   └── playbook.md      # 完整链路怎么串
└── templates/           # 直接抄的模板
    ├── consensus.md    # 共识小结模板
    ├── spec.md          # 规范模板
    ├── ticket.md       # 工单模板
    └── tickets-index.md # 工单总索引模板
```

---

## 流程顺序

### 纵向流水线（一步一步来）
```
clarify（拷问澄清）→ 刚开始做项目，先提问，把需求问清楚
    ↓
spec（共识成规范）→ 问清楚了，写成文档，换会话也不会忘
    ↓
slice（垂直拆工单）→ 规范写好了，拆成小工单，一步一步做
```

### 横向贯穿（随时都能用）
- **explain（视图讲清楚）** → 改了一堆东西，要跟别人讲清楚

### 拆完工单后
- **role-collaboration（角色分工）** → 要派任务给不同的人/AI

---

## 简单记
- **刚开始做项目**：clarify → spec → slice
- **要讲清楚的时候**：explain
- **要派任务的时候**：role-collaboration
