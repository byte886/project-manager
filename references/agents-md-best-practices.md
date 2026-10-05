# AGENTS.md 写作最佳实践

> 解决"项目级 AGENTS.md 该写什么、不写什么、写多长"的问题——避免写成长篇手册、堆 README 重复内容、塞训练数据里已有的常识。
> 模板见 [templates-execution.md](templates-execution.md) §6（项目级 AGENTS.md 模板）；本篇管"怎么写得对 AI 有效"。
> 来源：综合 Anthropic Claude Code 官方指南、OpenAI Codex Prompting Guide、Google Gemini CLI 指南及 2026 年同行评审研究（McMillan 2026, Lulla et al. 2026）；自真实项目提炼。

## 一、核心原则

### 1.1 非可推断测试（最重要）

对每条规则问自己：**"如果删除它，AI 会犯错吗？"**

- 不会 → 删除
- 会 → 保留

应用后通常能消除 70–80% 本能想写的内容。

### 1.2 四个高价值类别（只写这四类）

| 类别 | 说明 | 示例 |
|------|------|------|
| 精确的工具和版本 | AI 无法可靠猜测的具体命令与版本号 | "Python 3.12, not 3.11"、"pnpm, not npm" |
| 逐字可执行命令 | 安装、测试、构建、部署的精确 CLI 字符串 | "Run `pnpm install --frozen-lockfile`" |
| 反直觉的约定 | 项目偏离默认值的地方 | 非标准目录布局、自定义错误处理模式 |
| 权限边界 | AI 可以做什么、要确认什么、永远不能做什么 | "Never push to main directly" |

### 1.3 不应该包含的内容

| 内容类型 | 原因 | 处理方式 |
|----------|------|----------|
| README 中已有的内容 | 冗余会降低任务成功率约 3%、增加推理成本 20%+ | 链接或引用，不重复 |
| 长篇架构解释 | 对人有用，对始终加载的上下文是负担 | 移到 references/，按需读取 |
| 详细 API 文档 | AI 可以在需要时获取 | 链接到实际文档 |
| 标准语言/框架约定 | 已在模型训练数据里 | 不写（如"遵循 PEP 8"） |
| 不言而喻的建议 | 不约束行为，只消耗上下文 | 删除（如"写干净的代码"） |
| 频繁变化的信息 | 应放工作记忆/会话提示 | 不写（如当前冲刺任务列表） |
| 营销语言和项目历史 | 对 AI 无用，还会引导营销语气 | 删除 |

## 二、结构建议

### 2.1 根文件保持简短

- 理想长度：**50–200 行**；超过 200 行，边际指令开始互相竞争注意力。
- 把根文件当**高密度摘要**，不当手册。

### 2.2 渐进式披露（Progressive Disclosure）

2026 年主要平台（Anthropic/OpenAI/Google）共享的模式：

```
/AGENTS.md              # 短根文件：工具、命令、权限、约定
/skills/                # 领域特定技能，按需加载
/references/            # 长篇参考资料，仅在需要时读取
  data-model.md
  deployment.md
/code/scripts/          # 确定性验证脚本
  run-tests.sh
```

### 2.3 嵌套指令文件

大型仓库：根 `AGENTS.md` 管组织范围标准；子包/服务特定的 `AGENTS.md` 就近放——最接近活动代码的文件优先。

### 2.4 章节标题

用简短标题（`## Setup` / `## Commands` / `## Permissions`）。研究显示特定标题方案与更好 AI 行为无因果，标题主要帮人定位；不要过度设计分类法。

## 三、最小工作模板（约 50 行）

```markdown
# AGENTS.md

## Tooling and versions
- Python 3.12 (not 3.11)
- Node 20.x via pnpm (not npm or yarn)
- Postgres 16 for local development

## Commands
- Install: `pnpm install --frozen-lockfile`
- Test: `pnpm test --watchAll=false`
- Lint: `pnpm lint --max-warnings 0`
- Build: `pnpm build`

## Conventions
- All React components use the `*Widget.tsx` suffix
- Database migrations are immutable after merge
- API errors use the `AppError` class in `src/lib/errors.ts`

## Permissions
- YOU MUST run the full test suite before reporting a task complete
- Never push directly to main; open a PR
- Ask for confirmation before deleting any file outside src/ or tests/

## References
- Architecture overview: @references/architecture.md
- Deployment: @references/deployment.md
```

这个模板刻意不做的事：不写使命陈述、不写语言约定（已在模型中）、命令给精确字符串、权限表述为正面命令、信任边界明确、参考资料用链接导入。

## 四、部署前检查清单

1. 一个没有其他上下文的 AI，仅凭本文件+代码库，能完成典型任务吗？
2. 每一行都通过非可推断测试吗——删除它会导致真正的错误吗？
3. 精确的版本、精确的命令、精确的权限都说明了吗？
4. 可信与不可信输入之间的信任边界明确吗？
5. "完成"标准是确定性和可检查的（脚本/模式/测试套件），不是期望性的吗？
6. 文件在 ~200 行以内，还是额外内容已模块化到 skills/references？
7. 文件在版本控制下，有真正的审查流程吗？
8. 文件中没有秘密、凭证或通过隐蔽性维持的安全措施吗？
9. 实际用 AI 在代表性任务上测试过吗？
10. 有运行时监控或跟踪机制捕获文件遗漏的内容吗？

## 五、与本技能其它模板的衔接

- 项目级 AGENTS.md 的**结构与栏目骨架**：用 [templates-execution.md](templates-execution.md) §6 模板（定位与边界/目录约定/数据约定/凭证安全/工具坑/Git 工作流/恢复顺序/提交前检查）。
- 本篇管**内容取舍与精炼**：先用 §1 非可推断测试过滤，再按 §2 控制篇幅，最后用 §4 清单验收。
- 与全局 AGENTS.md（`~/Doubao/AGENTS.md`）冲突时项目级优先（仅该项目内）；协作关系见 [initiate.md](initiate.md)。
- 写完 AGENTS.md 后按 [templates-standards.md](templates-standards.md) §5 做健康度体检（类型标注、断链、重叠）。
