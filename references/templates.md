# 模板汇总（templates）

> 一页索引：所有模板在哪、用在哪个模块、哪一步。需要哪个就去对应 reference 复制完整模板。
> **执行期模板**（TASK_STATUS / ISSUES / 工程记忆 / 批次状态 / 文档同步清单 / 项目级 AGENTS / 交接档 handoff）见 [templates-execution.md](templates-execution.md)。

## 模板索引表

| 模板 | 用在哪个模块 | 哪个 SOP 步骤 | 完整模板位置 |
|---|---|---|---|
| 目录结构模板（双层：六槽位+工程扩展层） | initiate 启动 | 启动 SOP 第 5 步：按目录建结构 | [initiate.md](initiate.md) |
| 项目总纲（Project Charter） | initiate 启动 | 启动 SOP 第 3 步：写一页项目总纲 | [initiate.md](initiate.md) |
| README.md（项目概览，给人看） | initiate 启动 | 启动 SOP：创建标配文件 | 本文件 §9 |
| PROFILE.md（项目事实层） | initiate 启动 | 启动 SOP：创建标配文件 | 本文件 §10 |
| .gitignore（通用忽略规则） | initiate 启动 | 启动 SOP：创建标配文件 | 本文件 §11 |
| DIRECTORY_STRUCTURE.md（目录结构说明） | initiate 启动 | 工程项目扩展层启用时 | 本文件 §12 |
| DOCUMENTATION_MAP.md（文档地图） | initiate 启动 | 工程项目扩展层启用时 | 本文件 §13 |
| BRD 商业需求文档（产品/业务类可选） | initiate 启动 | 启动 SOP 第 3 步：总纲后论证商业可行性 | [brd.md](brd.md) |
| 创建 Checklist | initiate 启动 | 启动 SOP 收尾自检 | [initiate.md](initiate.md) |
| 治理卡 | monitor 监控 | 启动 SOP 第 7 步 + 日常治理 | [monitor.md](monitor.md) |
| 决策记录（ADR） | monitor 监控 | 启动 SOP 第 8 步 + 关键决策时 | [monitor.md](monitor.md) |
| 风险登记册（轻量版） | monitor 监控 | 每周 15 分钟自查时更新 | [monitor.md](monitor.md) |
| 项目台账表（列定义） | portfolio 组合层 | 季度盘点 SOP 第 6 步：更新台账 | [portfolio.md](portfolio.md) |
| PPM 评分法 | portfolio 组合层 | 季度盘点 SOP 第 5 步：算优先级分 | [portfolio.md](portfolio.md) |
| 门决策记录 | gates 阶段门 | 批量评审时每项目填一份 | [gates.md](gates.md) |
| 评审 Checklist | gates 阶段门 | 过门前必过 | [gates.md](gates.md) |
| 批量评审议程 | gates 阶段门 | 季度批量评审开场 | [gates.md](gates.md) |
| 退役总结 | close 收尾 | 关闭 SOP 第 2 步：正式总结 | [close.md](close.md) |
| 关闭六步 Checklist | close 收尾 | 关闭 SOP 全程 | [close.md](close.md) |
| 技术退役清单 | close 收尾 | 关闭 SOP 第 5 步：资源释放 | [close.md](close.md) |
| 月度巡检 Checklist | close 维护 | 项目执行中每月巡检 | [close.md](close.md) |
| 工程记忆 index | 执行期治理 | 跨会话恢复架构/链路/治理 | [execution-governance.md](execution-governance.md) §一 |
| TASK_STATUS / ISSUES | 执行期治理 | 执行期唯一进度真相 | [execution-governance.md](execution-governance.md) §二 |
| 项目级 AGENTS | 执行期治理 | 项目开工即建 | [execution-governance.md](execution-governance.md) §三 |
| 冷启动/续接双路径 | 执行期治理 | 新会话怎么读项目 | [execution-governance.md](execution-governance.md) §四 |
| 变更影响分级 L0/L1/L2 | 执行期动作 | 改文件/规范前先定级 | [execution-ops.md](execution-ops.md) §一 |
| 批次状态 JSON / JSONL | 执行期动作 | 批量任务断点续传 | [templates-execution.md](templates-execution.md) §4 |
| 文档同步检查清单 | 执行期动作 | 每次 git 提交前 | [templates-execution.md](templates-execution.md) §5 |
| 项目交接档 handoff | 执行期治理 | 交给新会话/另一台机/另一个 AI | [templates-execution.md](templates-execution.md) §7 |

---

## 快速复制区（生命周期模板，按使用顺序）

> 执行期模板（TASK_STATUS/ISSUES/记忆/批次/同步/AGENTS/交接档）见 [templates-execution.md](templates-execution.md)。

### 1. 目录结构模板（initiate，双层结构）

> 完整版含每层说明和六槽位与 docs/ 的关系，见 [initiate.md](initiate.md)。

```
📁 <项目名>/
├── 📄 00_项目总纲.md          ← 第一层：项目管理层（六槽位，必选）
├── 📁 01_结论与产出/
├── 📁 02_决策记录/
├── 📁 03_进行中的任务/
├── 📁 09_调研底稿与素材/
├── 📄 99_复盘与退役总结.md
├── 📄 README.md               ← 标配文件（必选）
├── 📄 AGENTS.md
├── 📄 PROFILE.md
├── 📄 .gitignore
├── 📁 src/ config/ scripts/ tests/ notebooks/   ← 第二层：工程扩展层（可选，进入开发时启用）
├── 📁 data/ results/ docs/ .secrets/
└── 📄 CHANGELOG.md LICENSE（可选）
```

### 2. 项目总纲模板（initiate）

```markdown
# 项目总纲 · <项目名>
> 最后更新：YYYY-MM-DD ｜ 状态：Active/On Hold/To Be Started ｜ 健康灯：🟢🟡🔴

## 1. 一句话目标
<项目完成后世界/我会变成什么样>

## 2. 成功标准（可量化）
- [ ] <硬指标 1>
- [ ] <硬指标 2>

## 3. 期限
- 立项：YYYY-MM-DD ｜ 计划完成：YYYY-MM-DD ｜ 里程碑：<M1/M2/M3>

## 4. 当前状态
- 现在在做：<>
- 下一步：<>
- 主要风险：<>

## 5. Owner 与资源
- Owner：<我> ｜ 时间投入：<每周 X 小时> ｜ 预算：<>

## 6. 治理卡（详见 02_决策记录/治理卡）
- 独立决定：<影响 < X / 预算 < $Y>
- 暂停重评：<进度偏离> 2周 / 预算超支> 20% / 新风险使假设失效>
- 碰节奏：<每周 15 分钟>
```

### 3. 治理卡模板（monitor）

```markdown
# 治理卡 · <项目名>
## 基本信息
- 目标：<> ｜ 截止：YYYY-MM-DD ｜ Owner：<我>

## 我可以独立决定的范围
- 影响范围：<>
- 预算/支出：<单笔 ≤ $X / 累计 ≤ $Y>
- 时间：<不影响关键里程碑的微调>

## 必须暂停重评的触发条件
- [ ] 进度偏离 > 2 周
- [ ] 预算超支 > 20%
- [ ] 新风险使核心假设失效
- [ ] <项目特有>

## 碰节奏
- 每周 15 分钟三问自查
- 每季度批量评审
- 门节点：G1 / G2 / G3
```

### 4. 决策记录 ADR 模板（monitor）

```markdown
# 决策记录 #NN · <一句话标题>
- 日期：YYYY-MM-DD ｜ 项目：<> ｜ 状态：Accepted / Superseded by #XX

## 背景
<当时处境>

## 决策
<最后选了什么>

## 备选（被放弃的）
- 方案 A：<>，放弃因为 <>
- 方案 B：<>，放弃因为 <>

## 后果 / 何时重新评估
<>
```

### 5. 项目台账表（portfolio）

| 项目名 | 状态 | 健康灯 | 战略对齐 | 预期价值 | 资源占用 | 风险 | 上次盘点 | 下次盘点 | 知识空间 | 备注 |
|---|---|---|---|---|---|---|---|---|---|---|
| | Active/Completed/Cancelled/On Hold/To Be Started | 绿/橙/红 | 1-5 | 1-5 | 1-5 | 1-5 | 日期 | 日期 | 链接 | |

### 6. 门决策记录模板（gates）

```markdown
# 门决策 · <项目名> · G<1/2/3> · YYYY-MM-DD
## 阶段交付物
<清单 + 完成状态>

## 门标准评估
| 领域 | 标准 | 是否通过 |
|---|---|---|
| 战略对齐 | <二元判断题> | ✅/❌ |
| 财务健康 | <> | ✅/❌ |
| 进度绩效 | <> | ✅/❌ |
| 风险状态 | <> | ✅/❌ |
| 交付物合规 | <> | ✅/❌ |

## 门决策
- 决策：Go / Conditional Go / Hold / Kill
- 决策者：<我> ｜ 日期：YYYY-MM-DD

## 若 Conditional Go
| 条件 | 可测量标准 | owner | 截止日 |
|---|---|---|---|
```

### 7. 退役总结模板（close）

```markdown
# 退役总结 · <项目名>
> 退役日期：YYYY-MM-DD ｜ 结果：✅成功 / ⏸暂停 / ❌取消

## 1. 概况
- 目标：<> ｜ 实际结果：<>

## 2. 关键数据
- 投入：<> ｜ 产出：<> ｜ 收益：<>

## 3. 三问复盘
- 什么让我意外？<>
- 什么值得重复？<>
- 下次怎么做？<>

## 4. 数据去向
- 保留在哪：<> ｜ 已备份：是/否

## 5. 残留事项
- 域名/服务已停？<>
- 是否还有人依赖？<>
```

### 8. 关闭六步 Checklist（close）

- [ ] 第 1 步：交付物存入 `01_结论与产出/`
- [ ] 第 2 步：写退役总结（三问复盘）
- [ ] 第 3 步：项目子树移入 `99_归档/`，保持原结构
- [ ] 第 4 步：台账状态改 Completed / Cancelled
- [ ] 第 5 步：停订阅/域名/服务，撤销 token
- [ ] 第 6 步：对外项目发 EOL 公告

---

### 9. README.md 模板（项目概览，给人看）

> 与 AGENTS.md（给AI看）、PROFILE.md（事实层）分离，不重复。描述性语言，不写命令。

```markdown
# <项目名>

> 一句话定位：<这个项目是做什么的>
> 状态：Active / On Hold / To Be Started ｜ 最后更新：YYYY-MM-DD

## 项目目标
<完成后世界/我会变成什么样，1-3句>

## 成功标准（可量化）
- [ ] <硬指标1>
- [ ] <硬指标2>

## 快速开始
> 新接手的人/AI 按此顺序读：

1. 本文件（README）— 项目概览
2. `00_项目总纲.md` — 目标/期限/当前状态
3. `PROFILE.md` — 技术栈/外部资源/稳定事实
4. `AGENTS.md` — AI操作规则（如你是AI）
5. `03_进行中的任务/TASK_STATUS.md` — 当前进度

## 目录结构
> 详细说明见 `docs/DIRECTORY_STRUCTURE.md`（工程项目）或下方简表。

| 目录/文件 | 放什么 |
|---|---|
| `00_项目总纲.md` | 项目章程（目标/期限/成功标准/状态） |
| `01_结论与产出/` | 最终交付物（报告/方案） |
| `02_决策记录/` | ADR决策记录、治理卡 |
| `03_进行中的任务/` | TASK_STATUS、ISSUES、进行中草稿 |
| `09_调研底稿与素材/` | 原始资料、引用、转写稿 |
| `99_复盘与退役总结.md` | 完成后写 |
| `src/` | 源代码（工程项目） |
| `data/` | 数据（不入库，gitignore） |
| `docs/` | 工程文档（工程项目） |

## 技术栈（工程项目填）
- 语言：<Python 3.11 / Node 20 / ...>
- 核心依赖：<baostock / pandas / ...>
- 数据来源：<AkShare / Baostock / ...>

## 常用命令（工程项目填）
```bash
# 安装依赖
pip install -r requirements.txt

# 运行数据下载
python scripts/download_data.py

# 运行测试
pytest tests/
```

## 存储分工
| 内容 | 在哪 | 是否入库 |
|---|---|---|
| 代码/文档/配置/脚本 | 项目根目录 | ✅ |
| 原始数据 | `data/raw/` | ❌（gitignore） |
| 运行时过程件 | `data/_workspace/` | ❌ |
| 回测/分析结果 | `results/` | ❌（或只入库摘要） |
| 加密凭证 | `.secrets/*.enc` | ✅（明文不入库） |

## 相关链接
- 项目总纲：`00_项目总纲.md`
- 需求文档：`docs/REQUIREMENTS.md`（工程项目）
- 工作流：`docs/WORKFLOW.md`（工程项目）
- 飞书知识库：<链接，如有>
- GitHub：<链接，如有>
```

---

### 10. PROFILE.md 模板（项目事实层）

> 只记"当前仍有效"的稳定事实，供新对话快速恢复。易变状态（进度/计数/当天日期）不写，需要时实时读 TASK_STATUS。
> 与 README（概览）、AGENTS（规则）分离，不重复。

```markdown
# 项目 PROFILE · <项目名>

> 定位：项目级白盒事实层。只记跨会话仍成立的稳定事实，不记规则（→AGENTS.md）、不记概览（→README.md）、不记进度（→TASK_STATUS.md）。
> 最后更新：YYYY-MM-DD

## 1. 技术栈与环境
- 语言/版本：<Python 3.11>
- 包管理：<pip + requirements.txt / poetry / npm>
- 核心依赖：<baostock, pandas, numpy, jupyter>
- 运行环境：<本地 Mac / 服务器 / Docker>
- 已知环境坑：<如 baostock 需先 login()、FunASR 首次下载模型需联网>

## 2. 数据来源与凭证
| 数据源 | 用途 | 是否免费 | 凭证存哪 |
|---|---|---|---|
| <Baostock> | <A股日线/财务数据> | <是> | <无需凭证> |
| <AkShare> | <补充数据> | <是> | <无需凭证> |
| <Tushare> | <可选> | <免费版有积分限制> | <环境变量 TUSHARE_TOKEN> |

> 凭证只记"存哪里"的指针，不写明文。加密凭证在 `.secrets/`。

## 3. 外部资源指针
- 飞书知识库：<空间名 + 链接>
- GitHub 仓库：<链接>
- 百度网盘备份：<路径，如有>
- 参考项目/竞品：<名称 + 链接>

## 4. 关键约定（项目特有，非通用规则）
- 命名约定：<如股票代码用 6位数字.sh / 数据文件用 parquet>
- 数据更新频率：<每日收盘后 / 每周>
- 回测默认参数：<初始资金/手续费/滑点>
- <其他项目特有事实>

## 5. 已验证的结论（带日期，不写过程）
- <结论一句话> [YYYY-MM-DD]
- <结论一句话> [YYYY-MM-DD]

## 6. 已验证做不通的方向（Won't Fix，避免重复踩坑）
- <方向> → <原因，什么情况下试过> [YYYY-MM-DD]
```

---

### 11. .gitignore 模板（通用）

```gitignore
# ===== 数据（整体不入库）=====
data/
results/

# ===== Python =====
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
venv/
.venv/
env/
ENV/
*.egg-info/
.eggs/
*.egg

# ===== Node =====
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# ===== Jupyter =====
.ipynb_checkpoints/
*.ipynb_checkpoints

# ===== IDE / 编辑器 =====
.vscode/
.idea/
*.swp
*.swo
*~
.DS_Store

# ===== 凭证（明文不入库，加密 *.enc 可入库）=====
.secrets/*.json
.secrets/*.txt
.secrets/*.key
.secrets/*.pem
config/local_*.py
config/local_*.json
.env
.env.*

# ===== 日志 / 临时文件 =====
*.log
logs/
tmp/
*.tmp
*.bak

# ===== 操作系统 =====
Thumbs.db
ehthumbs.db
Desktop.ini

# ===== 项目特定（按需添加）=====
# <如：notebooks/*.html（导出的HTML不入库）>
```

---

### 12. DIRECTORY_STRUCTURE.md 模板（目录结构详细说明，工程项目用）

> 说明各目录职责、存储分工、命名规则。README 只留摘要和链接，详细内容见本文档。

```markdown
# 目录结构详细说明

> 文档类型：Reference（参考资料）
> 更新频率：目录结构变更时
> 读者：AI代理 + 人类

## 〇、存储分工总表（先看这张）

| 内容 | Git仓库 | 本地data/ | 网盘备份 | 飞书知识库 |
|------|:---:|:---:|:---:|:---:|
| 代码/文档/配置/脚本/ADR | ✅ 唯一源 | — | — | — |
| 原始数据（raw/） | ❌ 忽略 | ✅ | ✅（如需） | ❌ |
| 处理后数据（processed/） | ❌ 忽略 | ✅ | ✅（如需） | ❌ |
| 运行时过程件（_workspace/） | ❌ 忽略 | ✅ | ❌ | ❌ |
| 回测/分析结果（results/） | ❌ 忽略 | ✅ | ❌ | ❌ |
| 知识成品/报告 | ✅（01_结论与产出/） | — | — | ✅（如需同步） |
| 加密凭证 .secrets/*.enc | ✅ | ✅ | ❌ | ❌ |

**一句话**：Git 只放"怎么做"的工程资产 + 结论性文档；"原料和过程件"在本地 data/，不入库。

## 一、项目根目录结构

```
<项目名>/
├── 00_项目总纲.md              # 项目章程
├── 01_结论与产出/              # 最终交付物
├── 02_决策记录/                # ADR、治理卡（轻量项目用；工程项目迁移至 docs/project-management/decisions/）
├── 03_进行中的任务/            # TASK_STATUS、ISSUES（轻量项目用；工程项目迁移至 project-management/active/）
├── 09_调研底稿与素材/          # 原始资料、转写稿、引用
├── 99_复盘与退役总结.md        # 完成后写
├── README.md                   # 项目概览（给人看）
├── AGENTS.md                   # AI操作手册（命令式）
├── PROFILE.md                  # 项目事实层
├── .gitignore
├── src/                        # 源代码
├── config/                     # 配置
├── scripts/                    # 可执行脚本
├── tests/                      # 测试
├── notebooks/                  # Jupyter研究
├── data/                       # 数据（整体gitignore）
│   ├── raw/                    # 原始数据（只读）
│   ├── processed/              # 处理后数据
│   └── _workspace/             # 运行时过程件（可随时清理）
├── results/                    # 回测/分析结果
├── docs/                       # 工程文档
│   ├── WORKFLOW.md             # 工作流总纲
│   ├── REQUIREMENTS.md         # 需求与验收标准
│   ├── DIRECTORY_STRUCTURE.md  # 本文档
│   ├── DOCUMENTATION_MAP.md    # 文档地图
│   └── project-management/
│       ├── decisions/          # ADR
│       ├── memory/             # 工程记忆
│       └── standards/          # 规范
├── project-management/
│   └── active/                 # TASK_STATUS + ISSUES（活态台账）
├── .secrets/                   # 加密凭证
├── CHANGELOG.md                # 变更日志（可选）
└── LICENSE                     # 开源协议（可选）
```

## 二、data/ 目录说明

### 2.1 raw/ — 原始数据（只读，绝不修改）
- 从数据源下载的原始文件，保持原样
- 命名：`<数据源>_<标的>_<时间范围>.<扩展名>`，如 `baostock_600519_2020-2026.csv`

### 2.2 processed/ — 处理后数据
- 经过清洗/转换/特征工程的数据
- 命名：`<处理步骤>_<标的>_<日期>.<扩展名>`

### 2.3 _workspace/ — 运行时过程件
- 下载临时文件、中间结果、断点状态、日志
- 可随时清理，不影响成品
- 不传网盘、不同步飞书

## 三、docs/ 目录说明

| 文档 | 职责 | 何时更新 |
|---|---|---|
| WORKFLOW.md | 工作流总纲，各环节SOP的入口和链接 | 流程变更时 |
| REQUIREMENTS.md | 需求定义、功能范围、验收标准 | 需求变更时 |
| DIRECTORY_STRUCTURE.md | 本文档，目录结构与存储分工 | 目录变更时 |
| DOCUMENTATION_MAP.md | 所有文档的快速入口 | 新增/删除文档时 |
| project-management/decisions/ | ADR决策记录（只增不改） | 关键决策时 |
| project-management/memory/ | 工程记忆（结论+指针） | 稳定结论变更时 |
| project-management/standards/ | 规范文档（命名/质量/编码等） | 规范变更时 |
```

---

### 13. DOCUMENTATION_MAP.md 模板（文档地图，工程项目用）

> 所有文档的快速入口，新会话先读这个。保持更新，新增文档必须加入。

```markdown
# 文档地图 · <项目名>

> 本文档是所有项目文档的索引入口。新会话先读这里，按需沿链接深读。
> 最后更新：YYYY-MM-DD

## 一、核心文档（新会话必读）

| 文档 | 职责 | 路径 |
|---|---|---|
| README | 项目概览（给人看） | [README.md](../README.md) |
| AGENTS | AI操作手册（命令式） | [AGENTS.md](../AGENTS.md) |
| PROFILE | 项目事实层（技术栈/资源/约定） | [PROFILE.md](../PROFILE.md) |
| 项目总纲 | 目标/期限/成功标准/当前状态 | [00_项目总纲.md](../00_项目总纲.md) |
| 任务状态 | 当前做什么、到哪、下一步 | TASK_STATUS.md |
| 问题清单 | 开放问题/已解决/Won't Fix | ISSUES.md |

## 二、需求与设计

| 文档 | 职责 | 路径 |
|---|---|---|
| 需求文档 | 功能范围/验收标准/不做什么 | [REQUIREMENTS.md](REQUIREMENTS.md) |
| BRD | 商业需求（产品/业务类） | ../01_结论与产出/BRD_*.md |
| PRD | 产品需求（如需要） | ../01_结论与产出/PRD_*.md |
| 工作流 | 各环节SOP入口 | [WORKFLOW.md](WORKFLOW.md) |
| 目录结构 | 存储分工/各目录职责 | [DIRECTORY_STRUCTURE.md](DIRECTORY_STRUCTURE.md) |

## 三、项目治理

| 文档 | 职责 | 路径 |
|---|---|---|
| 治理卡 | 决策权限/暂停重评条件/碰节奏 | ../02_决策记录/治理卡.md |
| ADR索引 | 所有决策记录 | decisions/ |
| 工程记忆 | 跨会话稳定结论（结论+指针） | memory/index.md |
| 规范文档 | 命名/质量/编码/文档同步 | standards/ |

## 四、SOP / 操作指南

| SOP | 用途 | 路径 |
|---|---|---|
| <数据下载SOP> | <怎么下载全量数据> | <路径> |
| <回测SOP> | <怎么跑回测> | <路径> |
| <新增SOP...> | <...> | <...> |

> SOP 命名：`<动作>_SOP.md`，如 `数据下载_SOP.md`。模板见 templates-execution.md §8。

## 五、调研底稿与素材

| 类别 | 位置 | 说明 |
|---|---|---|
| 已有讨论整理 | ../09_调研底稿与素材/已有讨论整理.md | 量化讨论归纳 |
| 操盘手经验 | ../09_调研底稿与素材/操盘手经验/ | 经验沉淀+原始文稿 |
| 竞品视频 | ../09_调研底稿与素材/竞品视频/ | 需求输入+转写稿 |
| <其他...> | <路径> | <说明> |

## 六、外部资源

| 资源 | 链接 | 说明 |
|---|---|---|
| GitHub | <链接> | 代码仓库 |
| 飞书知识库 | <链接> | 成品知识同步 |
| 数据源 | <链接> | <Baostock/AkShare> |
| <参考项目> | <链接> | <说明> |
```

---

> 本文件只做索引。模板改动请回到对应 reference 改，不要在这里双写（DRY）。
