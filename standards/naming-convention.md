# NAMING_CONVENTION.md（命名规范）

> **什么时候用**：只要写代码/写文件，就用得上，不分项目大小
> **怎么用**：直接抄这个模板，把你项目的命名规则填进去就行
> **达到什么效果**：所有文件命名统一，不会一会儿这个风格一会儿那个风格

---

## 模板本体

```markdown
# 命名规范

> **文档类型**：Governance（治理规范）
> **读者**：AI代理 + 开发者

## 总原则
1. 先判性质，再定名字：是代码？是文档？是数据？
2. 工程侧用英文，内容侧用中文
3. 同职责文件风格一致，禁止大小写混排

## 脚本：全小写 snake_case
- 示例：`fetch_data.py`、`check_directory.sh`
- 禁止：`fetch-data.py`、`FetchData.js`

## 文档：方法文档用小写+连字符，规范文档用大写
- 方法文档：`git-workflow.md`、`data-download.md`
- 规范文档：`NAMING_CONVENTION.md`、`CODE_STYLE.md`

## 目录：全小写 kebab-case
- 示例：`decisions/`、`standards/`
- 不用空格、不用大写
```

---

## 填好的示例（虚构bookshelf项目）

```markdown
# 命名规范

## 脚本：全小写 snake_case
- `sort_books.py`、`check_catalog.sh`

## 文档：方法文档用小写+连字符
- `sort-books.md`、`add-to-catalog.md`

## 目录：全小写 kebab-case
- `books/`、`scripts/`
```
