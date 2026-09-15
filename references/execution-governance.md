# 执行期治理骨架：工程记忆 / 活跃任务 / 项目级 AGENTS / 冷启动

> 项目已启动、进入执行阶段后"能跑起来"的轻量治理机制。本篇管**项目治理骨架**（记忆、任务台账、AI 操作手册、新会话怎么进）；
> 执行期的**动作机制**（批量任务断点、文档同步、存储分工、数据层编号、评审批次、变更影响分级）见 [execution-ops.md](execution-ops.md)。
> 模式不是理论，从真实项目提炼；模板见 [templates-execution.md](templates-execution.md)。

---

## 〇、模式选用指南（先看这个，别一上来全搭）

| 项目规模 | 建议启用的模式 |
|----------|---------------|
| 小项目（1-2周，单线程） | TASK_STATUS + ISSUES 即可，其他可选 |
| 中项目（1-3月，多任务并行） | + 工程记忆 + 项目级 AGENTS + 文档同步清单 |
| 大项目（3月+，批量处理，多平台） | + 批量任务执行规范 + 存储分工/数据层编号 + 评审改进批次 |
| 所有项目 | 项目级 AGENTS.md（强烈建议，成本低收益高） |

**原则**：从 TASK_STATUS + ISSUES 开始，项目长大到需要时再加；每个模式启用时在 TASK_STATUS 记录"已启用 XX 模式"。

---

## 一、工程记忆体系（project-memory bundle）

### 解决什么问题
每次新对话 AI 都要重新理解项目架构、踩过的坑、关键决策——重复问、重复查、容易遗漏。ADR 记录了"决策是什么"，但散落多处，新会话找不到入口。

### 怎么做
在项目 `docs/project-management/memory/` 下建轻量记忆 bundle：

```
docs/project-management/memory/
├── index.md              # 记忆入口（有什么、在哪、按领域分类）
└── concepts/             # 概念文档（每个是"结论+指针"，不复制原文）
    ├── architecture-xxx.md
    ├── workflow-xxx.md
    └── standard-xxx.md
```

### index.md 写法

```markdown
# 工程记忆 bundle

> 新会话恢复顺序：根 AGENTS.md（规则）→ 本页 index（有什么、在哪）
> → 按需沿每篇的「来源与下钻」深读原始文档。
> 本 bundle 只做"结论 + 指针"，不复制、不替代原文。
> 易变状态（进度、计数、当天日期）不进本 bundle，需要时实时读台账。

# 架构（Architecture）
* [架构名称](concepts/architecture-xxx.md) - 一句话说明（来源 ADR-xxx）

# 链路（Workflow）
* [链路名称](concepts/workflow-xxx.md) - 一句话说明

# 治理（Standard）
* [规则名称](concepts/standard-xxx.md) - 一句话说明
```

### concept 文档写法
每个 concept 50-150 行，结构固定：①一句话结论；②关键细节（3-5 条要点，带数字和做法）；③来源与下钻（指向 ADR/SOP/代码，不复制正文）；④常见坑（2-3 条）。

### 维护规则
- **只增不删**：过时加"[已退役 YYYY-MM-DD：原因]"，不硬删。
- **问题驱动更新**：发现记忆和实际不符当场更新。
- **不抄易变计数**：已完成多少以现场文件为准。
- **稳定结论指针化**：过程件只放指针指向 ADR/记忆，不复制正文。

---

## 二、活跃任务管理（active/）

### 解决什么问题
项目做着做着不知道"现在做到哪、下一步、卡在哪"。TODO 散落对话/脑子/便签，没有唯一真相源。

### 怎么做
在项目 `project-management/active/` 放两个动态文件：`TASK_STATUS.md`（当前做什么、到哪）+ `ISSUES.md`（开放/已解决/做不通的问题）。完整模板见 [templates-execution.md](templates-execution.md)。

### 维护规则
- **TASK_STATUS 立即更新**：任务开始/子任务完成/任务完成/遇阻塞/项目结构重大变更/每次 git 提交前。
- **ISSUES 发现即记录**：不等"攒够了再写"；解决后当场标注。
- **Won't Fix 很有价值**：记录"做不通的方向"，避免后来人重复踩坑。
- **不抄易变计数**：已完成多少以现场成品文件为准。

---

## 三、项目级 AGENTS.md（AI 操作手册）

### 解决什么问题
每个项目有自己的"怎么干活"规则（目录约定、工具用法、禁止事项），散在对话/README/脑子里。新会话 AI 容易犯"通用做法但本项目不行"的错。

### 怎么做
项目根目录放 `AGENTS.md`，与 `README.md` 分离：

| 文件 | 给谁看 | 写法 |
|------|--------|------|
| README.md | 人 | 项目概览、目标、架构、快速开始（描述性） |
| AGENTS.md | AI | 操作手册、命令式、可执行、禁止事项、路径约定（指令性） |

### 核心内容
①项目定位与边界；②目录约定（什么放哪、禁硬编码路径、用 `$HOME`/相对路径）；③工具用法与坑；④禁止事项（如"不要改 data/ 原始素材"）；⑤新会话恢复顺序；⑥提交前检查清单。完整模板见 [templates-execution.md](templates-execution.md)。

### 与全局 AGENTS.md 的关系
`~/Doubao/AGENTS.md` 是全局规则；项目根 `AGENTS.md` 是项目特有规则。冲突时**项目 AGENTS.md > 全局 AGENTS.md**（仅该项目内）。

---

## 四、冷启动 / 续接双路径（新会话怎么读项目）

> 同一项目，"第一次接触"和"接着上次做"读的文件不一样。判不准走 A。

### 路径 A · 冷启动（首次接触 / 跨阶段切换 / 对任务归属没把握）
1. 读 `README.md` — 项目概览
2. 读工程记忆 `memory/index.md` — 稳定结论定位
3. 读 `REQUIREMENTS.md` — 项目目标与验收标准
4. 读 `WORKFLOW.md` 对应环节 — 沿链接读专项 SOP
5. 读 `TASK_STATUS.md` + `ISSUES.md` — 当前状态

### 路径 B · 续接（用户说"继续/接着做 X"，仍是同一阶段同类活）
1. 只读 `memory/index.md`（扫结论定位）
2. 读 `TASK_STATUS.md` + `ISSUES.md`（到哪、下一步）
3. 读该环节那一篇 SOP + 上一单元样板成品

> 判不准走 A 还是 B 时，**就高走 A**。

### 交接（handoff）
要把项目交给新会话 / 另一台机 / 另一个 AI 时，用「项目交接档模板」（见 [templates-execution.md](templates-execution.md) §交接档），与"单会话单主题"纪律配套。
