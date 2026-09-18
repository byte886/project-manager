---
name: project-manager
description: "个人/小团队多项目并行的轻量项目管理方法论：项目组合 PPM（选对项目、季度盘点、优先级、健康灯、活跃项目 7±2）、单项目生命周期（启动写总纲搭目录、执行期治理卡与决策记录、收尾归档）、阶段门 G1/G2/G3 评审。适用于新立项、项目太多要盘或要砍、失控要定拍板边界、季度集中评审、做完想收尾时。轻量版，重型指标按需启用。"
compatibility: "纯方法论与 Markdown 模板，不随附脚本、不依赖 OS，Windows/macOS/Linux 通用、无需判平台；外部环节（飞书建空间/多维表格/终端操作）是可替换插槽，平台要求由对应工具决定。"
---

# project-manager · 个人项目管理方法论（PPM + 生命周期 + 阶段门，轻量版）

## 平台适用（执行前先读）
- 本技能是**纯方法论 + Markdown 模板**，不含可执行脚本、不依赖操作系统，Windows / macOS / Linux 均可直接使用，无需判平台。
- 文中外部环节（飞书 lark-wiki 建空间、lark-base 建台账、浏览器/终端操作等）是可替换插槽，平台要求由对应工具决定。
- 路径示例一律 `~` 或相对路径，不硬编码 `/Users/<用户名>`。

> 一句话：**用企业级项目管理的骨架（PPM + 生命周期 + 阶段门），但把肌肉换成个人轻量做法——知道该做哪些项目、每个项目走到哪一步、什么时候停、做完怎么收。**

## 什么时候用 / 反触发

- **新项目启动**（新站/新调研/新课程/新业务线），不知怎么立项、目录怎么搭 → [initiate](references/initiate.md)
- **产品/业务/对外收费类项目，要先论证"值不值得做、怎么赚钱"** → 立项后写一页 [BRD 商业需求文档](references/brd.md)（Charter 管项目、BRD 管生意、PRD 管产品）
- **项目太多、脑子里一团浆糊**，想盘哪些在做、该砍哪个 → [portfolio](references/portfolio.md)
- **做着做着开始失控**：不知道能拍板什么、什么情况该喊停 → [monitor](references/monitor.md)
- **季度末/半年末，集中判断一批项目继续还是砍** → [gates](references/gates.md)
- **项目做完了/想砍了**，直接丢着不踏实 → [close](references/close.md)
- **进入执行阶段**：要任务台账/问题清单/工程记忆/文档同步/冷启动怎么读项目 → [execution-governance](references/execution-governance.md)
- **执行期要改东西/跑批量/同步文档/评审改进/多项目并行评审**：变更分级 L0/L1/L2、批量断点、存储分工、并行委托判断 → [execution-ops](references/execution-ops.md)
- **工程项目要补"常规规范文档"**：环境配置、命名规范、编码规范、文档写作规范、质量验证、状态查询协议、任务报告/测试/验证/整改模板 → [templates-standards](references/templates-standards.md)
- **反触发**：一两天能做完、单线程、无长期归档需求的小任务，不必走本技能。

## 三层架构

| 层 | 模块 | 解决什么 | 详细 SOP |
|---|---|---|---|
| **L1 组合** | portfolio | 项目太多不知砍哪个、僵尸项目占名额 | [references/portfolio.md](references/portfolio.md) |
| **L2 启动** | initiate | 新项目目标模糊、目录乱 | [references/initiate.md](references/initiate.md) |
| **L2 监控** | monitor | 做着做着不知道能拍板什么、硬扛到爆 | [references/monitor.md](references/monitor.md) |
| **L3 评审** | gates | 到节点判断继续/砍掉 | [references/gates.md](references/gates.md) |
| **L2 收尾** | close | 做完/砍掉后资料散落、订阅还在扣费 | [references/close.md](references/close.md) |
| **执行期治理** | execution-governance | 工程记忆、TASK_STATUS+ISSUES、项目级 AGENTS、冷启动/续接双路径 | [references/execution-governance.md](references/execution-governance.md) |
| **执行期动作** | execution-ops | 变更分级 L0/L1/L2、批量任务断点、文档同步、存储分工、评审批次 | [references/execution-ops.md](references/execution-ops.md) |
| **工程规范与过程件** | templates-standards | 环境配置/命名/编码/文档写作/质量验证/状态查询规范，任务报告/测试/验证/整改/CHANGELOG 模板 | [references/templates-standards.md](references/templates-standards.md) |
| 汇总 | templates | 全部模板索引 | [references/templates.md](references/templates.md)、[references/templates-execution.md](references/templates-execution.md)、[references/templates-standards.md](references/templates-standards.md) |

## 核心概念（大白话）

| 术语 | 大白话 |
|---|---|
| **PPM** | 不是把每个项目做快，而是**选对一篮子项目**——资源就这么多，哪些投、哪些砍。 |
| **Project Charter** | 立项一页纸：为什么做、做成什么样算成功、什么时候完。 |
| **项目治理** | 提前写清：什么事自己能定、什么事必须停下重评、多久碰一次头。 |
| **健康灯** | 🟢 On Track / 🟡 At Risk / 🔴 Off Track。 |
| **阶段门** | 阶段间"检查点"：到点回答继续/卡住/砍掉，是真决策不是汇报。 |
| **Go/Conditional/Hold/Kill** | 门决策四档：通过/带条件通过/卡住/砍掉。 |
| **ADR** | 把关键决策和"为什么"写下来，半年后不后悔。 |
| **RACI** | 谁执行(R)/谁拍板(A)/被咨询(C)/被告知(I)；个人场景简化为"我=R=A"。 |
| **项目状态五档** | Active 在做 / Completed 完成 / Cancelled 取消不回头 / On Hold 暂停 / To Be Started 待启动。 |
| **活跃项目 7±2** | 同时推进的 Active 项目控制在 5–9 个，超了就砍或暂停，否则每个都做不好。 |
| **工程记忆** | 把散在 ADR/SOP/代码里的稳定结论"编译"成少量高密度 concept（结论+指针），新会话快速恢复。 |
| **Won't Fix** | 记录已验证"做不通"的方向和原因，避免未来的自己/别的 AI 重复踩坑。 |

## 文件指引（按需读，不要一次全读）

| 你要 | 读 | 用模板 |
|---|---|---|
| 盘所有项目、定优先级、季度重排 | `references/portfolio.md` | 台账表、PPM 评分法 |
| 新项目启动、写总纲、搭目录、创建标配文件 | `references/initiate.md` | 总纲模板、双层目录模板（六槽位+工程扩展层）、标配文件清单、创建Checklist、**项目创建后使用指南**（文档角色表/读取顺序/扩展规则/自由发挥空间/全局AGENTS协作） |
| 产品/业务类项目论证商业可行性、怎么赚钱 | `references/brd.md` | BRD 轻量模板、BRD/Charter/PRD 边界 |
| 定"什么自己拍板、什么暂停重评" | `references/monitor.md` | 治理卡、ADR、风险登记册 |
| 季度集中评审、过阶段门 | `references/gates.md` | 门决策记录、评审 Checklist |
| 做完/砍掉怎么收尾归档 | `references/close.md` | 退役总结、关闭 Checklist |
| 执行期搭治理骨架、新会话冷启动、治理目录位置约定 | `references/execution-governance.md` | TASK_STATUS、ISSUES、工程记忆、项目级 AGENTS、冷启动/续接双路径、**六槽位vs docs/分层二选一约定** |
| 执行期改文件/跑批量/同步/评审/判断要不要并行 | `references/execution-ops.md` | 变更分级 L0/L1/L2、批量断点、文档同步、存储分工、多智能体并行判断 |
| 工程项目补常规规范文档（环境/命名/编码/文档规范/质量验证/状态查询）与过程件模板（报告/测试/验证/整改/CHANGELOG） | `references/templates-standards.md` | SYSTEM_REQUIREMENTS、NAMING_CONVENTION、CODE_STYLE、DOCUMENTATION_GUIDE、变更驱动与健康度体检、STATUS_QUERY、QA、结构维护去留判据、REPORT/TEST/VERIFICATION/REFACTOR_PLAN 模板 |
| 一次性复制所有模板（生命周期+标配文件+执行期+工程规范） | `references/templates.md`、`references/templates-execution.md`、`references/templates-standards.md` | 全模板索引：目录/总纲/治理卡/ADR/台账/门决策/退役 + **README/PROFILE/.gitignore/DIRECTORY_STRUCTURE/DOCUMENTATION_MAP** + **SOP/REQUIREMENTS/WORKFLOW** + TASK_STATUS/ISSUES/记忆/AGENTS/交接档 + **SYSTEM_REQUIREMENTS/命名/编码/文档规范/QA/状态查询 + 报告/测试/验证/整改/CHANGELOG** |

## 与其它技能的边界（只点能力名）

| 本技能负责 | 协作对象 | 怎么取舍 |
|---|---|---|
| 项目这一层（立项/治理/盘点/评审/收尾） | **idea-to-tickets** | 总纲里"接下来做什么"落到工单时交它 clarify→spec→slice |
| 项目内部大量会复利的知识 | **okf-wiki** | 本技能只规定目录结构；知识沉淀按 okf-wiki，不另建记忆体系 |
| 环境/机器层面维护 | **dual-machine-manager** | 退役时的双机同步、备份、双机凭证落点由它负责 |
| 凭证与公开仓安全 | **security-baseline** | 立项/收尾只点"凭证要有处放、退役要吊销"，方法按它 |
| 飞书空间/台账的实际创建 | **lark-wiki** / **lark-base** | 真要在飞书动手时调对应技能 |

## 来源与边界

方法论来源（详见各 reference 末尾）：PMBOK 8 治理绩效域、PPM 四步流程、伯克利 BPM 项目状态、阶段门五领域、PARA/GTD，均做了减法默认轻量版。

**不覆盖**：具体任务执行（交 idea-to-tickets 之后）；财务记账/投资决策本身；团队多人协作重型流程（CCB/PMO/签字流）；不替代 lark-wiki/lark-base 本身操作。
