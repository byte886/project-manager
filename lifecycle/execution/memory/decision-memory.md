# 决策与记忆

> 做了不可逆决策要留痕、跨会话稳定结论要编译成可查的记忆。
> 达到什么效果：为什么这么决策、稳定结论是什么，随时能查到，不用重新争论。

---

## 目录
1. [架构决策记录（ADR）](#1-架构决策记录adr)
2. [记忆索引](#2-记忆索引)
3. [记忆概念](#3-记忆概念)

---

## 1. 架构决策记录（ADR）
> 什么时候用：做了一个不可逆的决策，要留痕

## 模板本体

```markdown
# ADR-NNN: <决策一句话标题>

> **状态**：已采纳 | 已否决 | 已被 ADR-XXX 取代
> **日期**：YYYY-MM-DD
> **决策者**：AI + <用户名>
> **影响范围**：<只在大决策时写，例如"全项目目录结构"；小决策省略>

## 背景
<遇到什么问题、压力来自哪、为什么现在必须做这个决策。不要写"因为技术先进"，要写"不解决会怎样">

## 决策
<具体决定，分小节或表格。例如：

### 目录分工
| 目录 | 职责 | 是否入库 |
|---|---|---|
| ... | ... | ... |
>

## 踩坑记录（可选，踩过才写）
- **现象**：<看到什么> → **根因**：<为什么> → **正确做法**：<以后怎么办>

## 紧急恢复（可选，有破坏性操作时写）
```bash
# 出问题时怎么回滚
<命令>
```

## 迁移策略（可选，替换旧方案时写）
| 阶段 | 内容 | 状态 |
|---|---|---|
| 1 | <先加新的> | ⏳ |
| 2 | <迁移数据> | ⏳ |
| 3 | <删旧的> | ⏳ |

## 后果

### 正面
- <带来什么好处>

### 负面
- <付出什么代价 / 放弃了什么>

### 风险（大决策才写）
- <风险>：缓解 = <怎么做>

## 参考
- <来源文档/最佳实践/调研链接>

*本文档只增不改。后续变更新建 ADR，本文档末尾加演进注记。*
```

---

## 填好的示例（虚构项目：个人读书清单站 bookshelf）

```markdown
# ADR-003: 书单数据用 JSON 文件入库，不上数据库

> **状态**：已采纳
> **日期**：2026-10-05
> **决策者**：AI + wenjiechen
> **影响范围**：数据层、部署方式

## 背景
bookshelf 目前 200 本书，预计一年后到 1000 本。需要选一种存储方式：
- 用 GitHub 仓库里的 JSON 文件
- 加 SQLite / Postgres
- 用 Notion / Airtable 当后端

痛点：之前试过 Notion API，每次构建要等 3-5 秒拉取，且 API 限流不稳定。
静态站部署在 Vercel，不想引入服务端。

## 决策
书单全部存 `data/books.json`，跟着 Git 仓库走，构建时打包进静态产物。

| 字段 | 类型 | 说明 |
|---|---|---|
| slug | string | URL 用，唯一 |
| title | string | 书名 |
| author | string | 作者 |
| tags | string[] | 标签 |
| rating | number | 1-5 |
| finished_on | date | 读完日期 |

## 后果

### 正面
- 构建一次成型，Vercel 无需数据库连接
- 数据可 git diff、可回滚、可 code review
- 离线可改

### 负面
- 没法做多用户协作编辑
- 超过 5000 本时 JSON 单文件可能变慢（届时再拆）
- 改一本书要走 git commit，不能手机上随手改

### 风险
- JSON 文件越来越大：缓解 = 超过 2000 本时按年份拆成 `data/books/2026.json`

## 参考
- 调研记录：`docs/research/data-storage.md`

*本文档只增不改。后续变更新建 ADR，本文档末尾加演进注记。*
```

---

## 什么时候**不**用 ADR
- 改一行 typo、调个颜色、重命名个变量——commit message 就够了
- 试用一下不确定的方案，还没定——写在 HANDOFF 日志里，定稿了再升 ADR
- 个人小项目一锤子买卖（写完就扔的脚本）——不用写

---

## 2. 记忆索引
> 什么时候用：跨会话稳定结论要编译成可查的记忆

## 模板本体

```markdown
# 工程记忆 bundle（project-memory）

> 这是项目的**跨会话工程记忆入口**：把散落在 ADR / SOP / 代码里、跨会话仍有效的稳定结论"编译"成少量高密度 concept。
> 新会话恢复顺序：根 `AGENTS.md`（规则）→ 本页 index（有什么、在哪）→ 按需沿每篇的「来源与下钻」深读原始文档。
> 本 bundle 只做"结论 + 指针"，**不复制、不替代**原文；权威细节以被链接的源文档为准。易变状态（进度、计数、当天日期）不进本 bundle，需要时实时读台账。

---

# 架构（Architecture）

* [<concept 标题 1>](concepts/<kebab-case-1>.md) - <一句话摘要，含来源 ADR 编号>
* [<concept 标题 2>](concepts/<kebab-case-2>.md) - <一句话摘要，含来源 ADR 编号>

# 链路（Workflow）

* [<concept 标题 3>](concepts/<kebab-case-3>.md) - <一句话摘要>
* <某领域尚未单独立 concept>：权威源见 `<相对路径到权威文档>`（<一句话说明这个文档管什么>）

# 治理（Standard）

* [<concept 标题 4>](concepts/<kebab-case-4>.md) - <一句话摘要>
* <某条治理规则>：见 `<相对路径到 ADR 或 SOP>`（<一句话说明>）

---

*最后更新：YYYY-MM-DD*
```

---

## 填好的示例（虚构项目：个人读书清单站 bookshelf）

```markdown
# 工程记忆 bundle（project-memory）

> 这是项目的**跨会话工程记忆入口**：把散落在 ADR / SOP / 代码里、跨会话仍有效的稳定结论"编译"成少量高密度 concept。
> 新会话恢复顺序：根 `AGENTS.md`（规则）→ 本页 index（有什么、在哪）→ 按需沿每篇的「来源与下钻」深读原始文档。
> 本 bundle 只做"结论 + 指针"，**不复制、不替代**原文；权威细节以被链接的源文档为准。易变状态（进度、计数、当天日期）不进本 bundle，需要时实时读台账。

---

# 架构（Architecture）

* [书单数据用 JSON 文件入库，不上数据库](concepts/architecture-data-storage.md) - `data/books.json` 跟 Git 走、构建时打包、不引入后端；超 2000 本再按年份拆（ADR-001）
* [前端搜索用 fuse.js 做内存模糊匹配](concepts/architecture-search.md) - 200 本数据量 < 50ms，不上 Lunr/Algolia；中文标签用数组 includes 不用 indexOf（ADR-002）

# 链路（Workflow）

* 新增一本书的发布流程：尚未单独立 concept，权威源见 `docs/guides/add-a-book.md`（手工编辑 books.json → pnpm build → Vercel 自动部署）

# 治理（Standard）

* 批量补数据的执行纪律：见 `../standards/BATCH_TASK_EXECUTION.md`（>3 个 / >1h / 多工具链必须建状态记录）
* 文档同步检查：见 `../standards/DOC_SYNC_CHECKLIST.md`（commit 前必跑四组 checklist）

---

*最后更新：2026-10-08*
```

---

## 什么时候**不**用这个 index

- 还在频繁试方案、结论没定稿——先写在 HANDOFF 日志里，定稿了再编译进 memory
- 易变的东西（当前做到第几本、今天跑了几个批次、当前 HEAD 是什么）——这些进 TASK_STATUS，不进 memory
- 一次性的脚本用法、命令行参数——那是脚本 --help 或 README 的事，不立 concept

---

## 3. 记忆概念
> 什么时候用：单个概念的详细说明

## 模板本体

```markdown
---
concept: <short-kebab-id>
title: <标题，一句话说清这条结论是什么>
type: architecture | workflow | standard
tags: [<tag1>, <tag2>]
status: stable
verified: ai | machine
last_updated: YYYY-MM-DD
sources:
  - {id: ADR-NNN, resource: ../decisions/ADR-NNN-xxx.md, title: <决策标题>}
---

# <标题>

## 核心结论

<先给一句话结论，别绕。例如："书单全部存 data/books.json，跟 Git 仓库走，构建时打包进静态产物，不引入数据库。">

## 关键规则

1. <规则 1：例如"数据文件就一个 data/books.json，不要拆成多文件">
2. <规则 2>
3. <规则 3>

<!-- 迁移类才写这一节；全新项目没有旧方案就删掉 -->
## 与旧方案的关键差异（迁移类才写）

| 维度 | 旧 | 新 |
|------|----|----|
| <维度 1> | <旧做法> | <新做法> |
| <维度 2> | <旧做法> | <新做法> |

## 来源与下钻

- 完整背景与取舍论证 → <ADR-NNN 相对路径>
- 接口/字段定义 → <具体代码或配置文件路径>
- 相关 SOP → <具体 SOP 文件路径>
```

---

## 填好的示例（虚构项目：个人读书清单站 bookshelf）

```markdown
---
concept: architecture-data-storage
title: 书单数据用 JSON 文件入库，不上数据库
type: architecture
tags: [storage, data]
status: stable
verified: machine
last_updated: 2026-10-08
sources:
  - {id: ADR-001, resource: ../decisions/ADR-001-data-storage.md, title: 数据存储决策}
---

# 书单数据用 JSON 文件入库，不上数据库

## 核心结论

书单全部存 `data/books.json`，跟 Git 仓库走，`pnpm build` 时打包进静态产物，不引入数据库 / 后端 / Notion API。

## 关键规则

1. 数据文件就一个 `data/books.json`，每本书一条记录，字段固定为 `{slug, title, author, tags[], rating, finished_on}`
2. 改书 = 改 JSON + git commit，走 code review，不做后台编辑
3. 超过 2000 本时才按年份拆成 `data/books/2026.json` 这种分片；不到不拆
4. 不接 Notion / Airtable 当数据源——之前试过，每次构建等 3-5 秒且 API 限流不稳定

## 与旧方案的关键差异

| 维度 | 旧（Notion API） | 新（Git 仓库 JSON） |
|------|------------------|---------------------|
| 构建耗时 | 每次 3-5 秒拉 API | 0 秒，本地文件直接读 |
| 可用性 | API 限流会构建失败 | 离线可改可构建 |
| 版本历史 | Notion 内部数据库 | git diff 可 review、可回滚 |
| 编辑方式 | 手机上随手改 | 必须走 git commit |

## 来源与下钻

- 完整背景与取舍论证 → `../decisions/ADR-001-data-storage.md`
- 数据字段定义 → `data/books.json`（schema 见 `scripts/validate-books.mjs`）
- 新增一本书的操作流程 → `docs/guides/add-a-book.md`
```

---

## 什么时候**不**立 concept

- 结论还在试、没定稿——先写 HANDOFF，定稿了再升 concept
- 一次性排障经验、坑——那是 ISSUES 的事，不是稳定架构结论
- 会频繁变动的东西（当前书目数量、今天读了几本）——进台账，不进 memory
- 一条只跟某个脚本相关的参数说明——那是脚本注释/README 的事
