---
name: github-format-standards
description: GitHub 项目格式规范 - 当用户准备将项目分享到 GitHub、编写或修改 README.md、ISSUE_TEMPLATE、PULL_REQUEST_TEMPLATE、CONTRIBUTING.md、CODE_OF_CONDUCT.md 等 GitHub 文档时使用此 skill。自动按照 GitHub 最佳实践规范 Markdown 格式、文档结构、中英文混排。即使用户只是说"帮我看下格式"、"整理下 README"、"准备发布到 GitHub"，也应该触发此 skill。
---

# GitHub 格式规范

当用户准备将项目分享到 GitHub 时，按照以下规范检查和修正所有文档格式。

## 工作流程

1. **扫描**：找出项目中所有 `.md` 文件和 `.github/` 目录下的模板文件
2. **逐文件检查**：对每个文件按下方规则逐一检查
3. **修正**：发现问题直接修改，不等待用户确认
4. **输出摘要**：修正完成后列出所有改动及其原因

---

## 一、Markdown 通用规范

### 1.1 标题层级

- `#` 一级标题 = 文件标题（一个文件只有一个 `#`）
- `##` 二级标题 = 大章节
- `###` 三级标题 = 子章节，以此类推
- **绝不跳级**（例如 `#` 后直接 `###` 是不允许的）
- 标题前后各空一行
- `#` 后有一个空格再写文字：`# 标题` 而非 `#标题`

```markdown
# 项目名称

## 快速开始

### 安装依赖
```

### 1.2 代码块

- **必须标注语言类型**：用 ` ```python ` 而非 ` ``` `
- 常用语言标识：`python`, `bash`, `javascript`, `typescript`, `json`, `yaml`, `html`, `css`, `sql`, `dockerfile`, `shell`
- 命令行示例优先用 `bash`，并在需要时加上 `$` 前缀区分命令和输出

```bash
# 正确
```python
print("hello")
```

# 错误
```
print("hello")
```
```

### 1.3 表格

- 列对齐用 `:---`（左对齐）、`:---:`（居中）、`---:`（右对齐）
- 表头和分隔符必须完整，列数一致
- 中英文混排表格推荐左对齐

```markdown
| 参数     | 类型   | 必填 | 说明         |
| :------- | :----- | :--: | :----------- |
| name     | string |  是  | 用户名称     |
| age      | number |  否  | 用户年龄     |
```

### 1.4 链接与图片

- 链接用 `[文字](url)`，避免裸 URL
- 图片用 `![alt文本](url)`，必须写有意义的 alt 文本
- 引用式链接适合重复使用的 URL：

```markdown
[GitHub][1]

[1]: https://github.com
```

### 1.5 列表

- 无序列表用 `*`（主流项目如 React、TensorFlow、FastAPI 均使用 `*`）
- 中文项目如习惯 `-` 也可以，但整个项目必须统一
- 有序列表用 `1.` `2.` `3.`
- 子列表缩进 **2 个空格**，整个项目保持一致
- 列表项前后不需要空行（除非列表项包含多段落）
- 功能特性推荐用 **`* **关键词：** 说明`** 格式，让关键词加粗突出

```markdown
* **Declarative:** React makes it painless to create interactive UIs.
* **Component-Based:** Build encapsulated components that manage their own state.
* **Learn Once, Write Anywhere:** Develop new features without rewriting existing code.
```

### 1.6 空行与分隔

- 每个标题前空一行（文件开头除外）
- 代码块前后各空一行
- 表格前后各空一行
- 列表前后各空一行
- 文件末尾保留**一个**空行

---

## 二、README.md 标准结构

README.md 是项目的门面，按以下顺序组织章节（参考 React / FastAPI / TensorFlow 的通用模式，不适用则跳过）：

```
（可选：居中 Logo，用 <div align="center"> 包裹）
# [项目名称](https://官网)   ← 标题常带链接
（一行简介/tagline，不加 ## 标题，可居中）
（可选：Badges 一行，多个 badge 用 &middot; 或空格分隔）

（直接开始描述段落，不加 "## 简介" 标题）
第一段：项目是什么、解决什么问题、核心定位。
第二段：关键特性或技术亮点。

## 功能特性            ← 或 ## Features
## 演示 / 截图
## 快速开始            ← 最关键的章节，3 分钟内跑起来
## 安装
## 使用方法
## 配置
## API 文档
## 贡献指南
## 许可证
## 致谢
```

**关键原则**（来自热门项目验证）：
- **标题下的简介不加 `##` 标题** — React、FastAPI、TensorFlow 都是直接写段落
- 简介段落先讲 WHY（解决什么问题），再讲 WHAT（怎么做）
- Badges 紧贴标题/Logo 下方，不要单独占一个章节
- 功能特性用 `* **关键词：** 描述` 格式（React 风格）
- "快速开始"决定用户是否留下来——命令必须可直接复制粘贴执行
- 截图放 `## 演示` 章节，用 `<img>` 标签控制宽度

### HTML 混用（常见且推荐）

热门项目普遍在 Markdown 中混用 HTML 来增强排版：

```markdown
<!-- 居中 -->
<div align="center">
  <img src="logo.png" alt="Logo">
</div>

<!-- 折叠详情 -->
<details>
<summary>点击展开更多</summary>
折叠的内容在这里。
</details>

<!-- 暗黑模式图片 -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="img-dark.png">
  <img src="img-light.png" alt="Screenshot">
</picture>
```

### 可选但推荐的章节

- **Security / 安全披露**：Next.js 风格，告知用户如何报告安全漏洞
- **Good First Issues**：React/Next.js 风格，引导新贡献者入门
- **相关项目 / Ecosystem**：FastAPI 推广 Typer 的模式
- **用户评价 / 谁在用**：FastAPI 风格，展示大厂用户增加信任

---

## 三、常见 GitHub 模板

### 3.1 ISSUE_TEMPLATE

存放位置：`.github/ISSUE_TEMPLATE/` 目录下，或 `.github/ISSUE_TEMPLATE.md`

必须包含：
- **问题描述**：清晰描述 bug 或功能请求
- **复现步骤**（bug）：最小化的复现步骤
- **期望行为**：你期望发生什么
- **实际行为**：实际发生了什么
- **环境信息**：操作系统、版本号、浏览器等
- **截图/日志**（可选）

### 3.2 PULL_REQUEST_TEMPLATE

存放位置：`.github/PULL_REQUEST_TEMPLATE.md`

必须包含：
- **改动摘要**：简要说明做了什么
- **改动原因**：为什么要做这个改动
- **测试计划**：如何验证改动正确
- **截图**（前端改动）
- **关联 Issue**：`Closes #123` 或 `Fixes #456`

### 3.3 CONTRIBUTING.md

存放位置：项目根目录 `CONTRIBUTING.md`

必须包含：
- 如何提交 Issue
- 如何提交 Pull Request
- 代码风格要求
- 本地开发环境搭建
- 测试要求

### 3.4 CODE_OF_CONDUCT.md

存放位置：项目根目录 `CODE_OF_CONDUCT.md`

可以用 GitHub 提供的标准版本或自己编写。

---

## 四、中文项目特别注意

### 4.1 中英文混排空格

**必须加空格**的场景：
- 中文与英文之间：`使用 GitHub 托管代码`（不是 `使用GitHub托管代码`）
- 中文与数字之间：`支持 10 个节点`（不是 `支持10个节点`）
- 数字与单位之间（中文语境）：`10 MB`、`5 分钟`、`3 小时`

**不加空格**的场景：
- 中文标点与中文之间
- 英文单词与英文标点之间

### 4.2 专有名词大小写

常见专有名词的正确写法：
- GitHub（不是 Github、github、Github）
- JavaScript（不是 Javascript、javascript）
- TypeScript、Python、Node.js、React、Vue、Django
- macOS（不是 MacOS）
- API、URL、HTML、CSS、JSON、YAML
- VS Code（不是 VSCode、VsCode）
- ChatGPT、OpenAI、Claude、Anthropic
- npm、pip、cargo

### 4.3 标点符号

- **中文段落**使用中文标点：`，` `。` `：` `（）` `「」`
- **英文段落**使用英文标点：`,` `.` `:` `()` `""`
- 技术文档推荐用中文书写但保留英文术语，术语不加书名号
- 代码、文件名、命令 用反引号包裹：\`config.json\`、\`npm install\`

### 4.4 数字格式

- 大数字用千分位：`1,000` 而非 `1000`（中文语境也可写 `1000`，但英文必须加逗号）
- 货币金额说明币种：`$99`、`¥199`、`€49`

---

## 五、检查清单

修正或创建 GitHub 文档时，逐项确认：

### Markdown 基础
- [ ] 标题层级不跳级（`#` → `##` → `###`）
- [ ] 代码块标注语言
- [ ] 表格列对齐、列数一致
- [ ] 链接有描述文字（非裸 URL）
- [ ] 图片有 alt 文本
- [ ] 列表缩进统一（推荐 2 空格）
- [ ] 文件末尾一个空行

### README.md
- [ ] 标题下一句话简介
- [ ] 有安装/快速开始章节
- [ ] 命令可直接复制执行
- [ ] 许可证明确

### 模板文件
- [ ] ISSUE_TEMPLATE 包含复现步骤和环境信息
- [ ] PULL_REQUEST_TEMPLATE 包含测试计划
- [ ] CONTRIBUTING.md 说明贡献流程

### 中文项目
- [ ] 中英文之间有空格
- [ ] 中文与数字之间有空格
- [ ] 专有名词大小写正确
- [ ] 标点符号与语言匹配

---

## 六、常见错误速查

| 错误写法 | 正确写法 | 原因 |
| :------- | :------- | :--- |
| `#标题` | `# 标题` | `#` 后缺空格 |
| ```` ``` ```` | ```` ```python ```` | 代码块缺语言标识 |
| `使用GitHub` | `使用 GitHub` | 中英文间缺空格 |
| `支持10个` | `支持 10 个` | 中文与数字间缺空格 |
| `[https://...](https://...)` | `[文档](https://...)` | 链接缺描述文字 |
| `## 简介` 紧跟 `#### 详情` | `## 简介` → `### 详情` | 标题跳级 |
| 文件末尾无空行 | 文件末尾一个空行 | 不符合 POSIX 规范 |
| `Github` / `github` | `GitHub` | 专有名词大小写错误 |

---

## 七、引用模板

详细的模板文件在 `references/` 目录中，按需读取：
- `references/readme-template.md` — 完整 README 模板
- `references/issue-template.md` — Issue 模板
- `references/pr-template.md` — Pull Request 模板
- `references/contributing-template.md` — 贡献指南模板
