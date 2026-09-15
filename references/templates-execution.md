# 执行模式模板（execution-patterns）

> 从真实项目提炼的执行期模板，适用于进入执行阶段的中大型项目。
> 生命周期类模板（目录/总纲/治理卡/ADR/台账/门决策/退役/关闭）见 [templates.md](templates.md)。

---

## 1. TASK_STATUS.md 模板（活跃任务台账）

```markdown
# 任务状态台账

> 本页是"当前做什么、到哪"的唯一进度真相，实时更新。
> 需求溯源看 docs/REQUIREMENTS.md，开放缺陷看 ISSUES.md。
> 稳定技术结论的权威版在 ADR / 工程记忆，本页只放指针、不复制结论。

## 依赖与并行前沿
- **阶段1**：✅ 完成（commit xxx）
- **阶段2**：⏳ 进行中
- **阶段3**：📋 待启动
- 可并行：A（后台运行）与 B（前台开发）可同时进行

## 工单清单

| 编号 | 标题 | 类型 | 前置 | 状态 | 验收 / 落点 |
|------|------|------|------|------|------------|
| T-01 | xxx | feature | 无 | done | 产出物路径 |
| T-02 | xxx | feature | T-01 | doing | 预期产出 |
| T-03 | xxx | bugfix | 无 | blocked | 阻塞原因 |
| T-04 | xxx | refactor | 无 | todo | 预期产出 |

状态四档：todo / doing / blocked / done

## 关键口径（指针，不展开）
- **技术点A**：结论一句话 → 见工程记忆 concepts/xxx
- **技术点B**：结论一句话 → 见 ADR-002

## 下一步（按优先级）
1. 最高优先级任务（T-xx）
2. 次优先级任务（T-xx）
3. 可后台运行的任务（T-xx）
```

---

## 2. ISSUES.md 模板（问题清单）

```markdown
# 问题清单

## 开放问题（Open）

### ISSUE-001: 问题标题
- **状态**：待启动 / 研究中 / 修复中
- **发现时间**：YYYY-MM-DD
- **问题描述**：具体现象、影响范围
- **根因**：（找到后填写）
- **方案**：（确定后填写）
- **验证**：（修复后填写验证方法和结果）

## 已解决问题（Closed）
### ISSUE-00x: 问题标题 ✅
- **解决时间**：YYYY-MM-DD
- **根因**：一句话
- **方案**：一句话

## 已验证做不通的方向（Won't Fix）
- 方向A → 原因（什么情况下试过、结果是什么）
```

---

## 3. memory/index.md 模板（工程记忆入口）

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

---

## 4. 批次状态 JSON 模板（批量任务）

```json
{
  "batch_id": "<task_type>_<date>_<seq>",
  "task_type": "<task_type>",
  "started_at": "2026-01-01T10:00:00+08:00",
  "updated_at": "2026-01-01T10:30:00+08:00",
  "status": "running",
  "total": 313,
  "completed": 150,
  "failed": 2,
  "skipped": 0,
  "current_item": "item_150_xxx",
  "failed_items": [
    {"name": "item_023_xxx", "reason": "下载超时", "retry_count": 3}
  ]
}
```

进度文件用 JSONL 增量写：`{"time":"...","action":"start|complete|fail","item":"...","...":""}`。

---

## 5. 文档同步检查清单模板（提交前必跑）

```markdown
## 一、任务状态同步
- [ ] TASK_STATUS.md 已更新（工单状态正确、"下一步"已更新）
- [ ] ISSUES.md 已更新（新问题已记录、已解决问题已标注）

## 二、文档关联同步
- [ ] DOCUMENTATION_MAP.md 已更新（新增文档已加入、链接有效）
- [ ] WORKFLOW.md 已更新（如流程变更）
- [ ] REQUIREMENTS.md 已更新（如需求变更）

## 三、目录结构同步
- [ ] DIRECTORY_STRUCTURE.md 已更新
- [ ] .gitignore 已检查（git status 确认没有不该提交的文件）

## 四、工具与脚本同步
- [ ] 新增脚本已加入文档地图
- [ ] 脚本参数变更已更新到对应 SOP

## 五、工程记忆同步（如稳定结论变更）
- [ ] memory/index.md 已更新
- [ ] 相关 concept 已修订

## 六、ADR 决策记录（如重要决策）
- [ ] 重要决策已记录到 ADR-xxx.md
- [ ] 决策状态正确
```

---

## 6. 项目级 AGENTS.md 模板（AI 操作手册）

```markdown
# 项目 AGENTS.md（AI 操作手册）

> 本文件是给 AI 看的操作手册，命令式、可执行。
> 给人看的项目概览在 README.md。
> 与全局 AGENTS.md 冲突时，本文件优先（仅本项目内）。

## 1. 项目定位与边界
- 做什么：一句话
- 不做什么：一句话（边界）

## 2. 目录约定
- 什么东西放哪：列出关键目录
- 路径规则：禁止硬编码 /Users/<用户名>，用 $HOME / 相对路径
- 禁止修改：列出绝对不能动的目录/文件

## 3. 工具用法
- 本项目用什么工具、怎么调用、有什么坑

## 4. 新会话恢复顺序
1. 读本文件（AGENTS.md）
2. 读 docs/DOCUMENTATION_MAP.md（文档地图）
3. 读 docs/project-management/memory/index.md（工程记忆）
4. 读 project-management/active/TASK_STATUS.md（当前进度）

## 5. 提交前检查
- 按 docs/project-management/standards/DOC_SYNC_CHECKLIST.md 跑一遍
- git status 确认没有不该提交的文件
```

---

## 7. 项目交接档 / handoff prompt（交给新会话 / 另一台机 / 另一个 AI）

> 与"单会话单主题"纪律配套。要把项目交出去时，先填这份档，新会话照此冷启动。
> 涉及个人技术选型/工具偏好的位置一律用占位符，不写死某台机的具体软件。

```markdown
# 项目交接档 · <项目名>

> 交接日期：YYYY-MM-DD ｜ 交接方：<> ｜ 接收方：<新会话/另一台机/另一个 AI>

## 1. 项目目标
- 一句话目标：<>
- 成功标准（可量化）：<>
- 不做什么（边界）：<>

## 2. 位置
- 项目根目录：<~/path/to/project>
- 仓库：<remote url> ｜ 当前分支/commit：<>
- 关键资产位置：<原始素材/成品/台账各在哪>

## 3. 当前状态
- 进行到哪：<>
- 下一步（按优先级）：<>
- 阻塞/开放问题：<见 ISSUES.md>

## 4. 冷启动读取路径（新会话按此顺序读）
1. README.md
2. docs/project-management/memory/index.md
3. REQUIREMENTS.md
4. WORKFLOW.md 对应环节 → 专项 SOP
5. TASK_STATUS.md + ISSUES.md
（续接同类活可走"路径 B"，判不准走 A；详见 execution-governance.md §四）

## 5. 核心治理规则指针
- 变更影响分级 L0/L1/L2（拿不准就高不就低）：见 execution-ops.md §一
- 文档同步检查清单（每次提交前）：见 execution-ops.md §三
- 存储分工（什么进 git、什么只在本地）：见 execution-ops.md §四
- 凭证：<项目 .secrets/ 结构与责任；主密码来源>

## 6. 关键技术指针
- 技术栈/关键依赖：<>
- 已知坑与做不通的方向：<见 memory / ISSUES Won't Fix>
- 外部服务/账号：<只点名能力名，不写凭证>

## 7. 偏好指针
- 工作风格/约定：<>
- 不要做什么：<>
```

---

> 本文件只放执行期模板。模板改动请回到对应 reference 改，不要双写（DRY）。
