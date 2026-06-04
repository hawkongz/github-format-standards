---
name: github-format-standards
description: GitHub 项目格式规范 - 当用户准备将项目分享到 GitHub、编写或修改 README.md、ISSUE_TEMPLATE、PULL_REQUEST_TEMPLATE、CONTRIBUTING.md、CODE_OF_CONDUCT.md 等 GitHub 文档时使用此 skill。自动按照 GitHub 最佳实践规范 Markdown 格式、文档结构、中英文混排。即使用户只是说"帮我看下格式"、"整理下 README"、"准备发布到 GitHub"，也应该触发此 skill。
---

# GitHub 格式规范

当用户想把项目分享到 GitHub 时，执行以下完整流水线。**不要只输出规则——直接动手改。**

## 完整流水线

### 阶段一：审计

扫描项目，列出已有 vs 缺失：

```
已有：README.md ✓  CONTRIBUTING.md ✗  .github/ ✗  SECURITY.md ✗
问题：3 张表格缺对齐、2 个代码块缺语言标注
```

### 阶段二：修复现有文件

逐文件检查所有 `.md` 文件，发现问题直接改，不要等用户确认。

- [ ] 标题：`#` 后空格、不跳级
- [ ] 代码块：每个 ` ``` ` 都标注语言（` ```python `、` ```bash `）
- [ ] 表格：分隔行加 `:---` 对齐标记
- [ ] 列表：符号统一（`*` 或 `-`）、子列表缩进 2 空格
- [ ] 链接：无裸 URL、图片有 alt 文本
- [ ] 中英文空格：`使用 GitHub` 不是 `使用GitHub`
- [ ] 专有名词：`GitHub` 不是 `github`、`JavaScript` 不是 `Javascript`
- [ ] 文件末尾：恰好一个空行

### 阶段三：生成缺失文件

- **`.github/ISSUE_TEMPLATE/`** — bug 报告 + 功能建议模板 + `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`** — 含改动摘要、测试计划、截图区域
- **`CONTRIBUTING.md`** — 贡献流程、本地开发、提交规范
- **`SECURITY.md`** — 安全漏洞报告说明
- **`.gitignore`** — 如果没有，根据项目语言生成

### 阶段四：README 优化

按热门项目模式（React / FastAPI / TensorFlow）重写 README：

```
（可选：居中 Logo）
# [项目名称]
（一句话简介，不加 ## 标题）
（可选：Badges 行）

（直接描述——先说 WHY，再说 WHAT，不加标题）

## 功能特性          ← * **关键词：** 描述
## 快速开始          ← 必须可直接复制粘贴
## 安装
## 使用方法
## API 文档
## 贡献指南
## 许可证
```

### 阶段五：双语支持（中文项目）

如果项目是中文或双语的：

- 根目录：英文 `README.md` + 英文 `SKILL.md`
- `zh-CN/`：中文 `README.md` + 中文 `SKILL.md`
- 顶部都有 `**Language:** [English](../README.md) | [简体中文](README.md)`

### 阶段六：发布

所有文件生成并修复后：

1. 如果不是 git 仓库，`git init`
2. `git add` 所有文件（排除密钥、`.env`、大二进制文件）
3. 用清晰的信息 commit
4. 如果 GitHub repo 不存在，`gh repo create` 创建
5. `git push`
6. 输出最终 GitHub URL

如果用户只想本地预览，到阶段五停止，输出改动摘要。

---

## 摘要格式

完成后输出：

| 阶段 | 内容 |
| :--- | :--- |
| 审计 | 发现 3 个问题：... |
| 修复 | 5 处改动，涉及 2 个文件 |
| 生成 | 创建 4 个文件：.github/...、CONTRIBUTING.md、... |
| 优化 | 重写 README 结构 |
| 发布 | 已推送至 https://github.com/... |

---

## README 结构参考

```
（可选：<div align="center"> 居中 Logo）
# [项目名称]
（一句话简介，不加 ## 标题，可居中）
Badges 行

（描述段落——不加标题，先说 WHY）
## 功能特性            ← * **关键词：** 描述
## 演示 / 截图
## 快速开始             ← 3 分钟跑起来
## 安装
## 使用方法
## 配置
## API 文档
## 贡献指南
## 许可证
## 致谢
```

可选：Security、Good First Issues、相关项目。

## 中文专项规则

- 中文 + 英文：`使用 GitHub`（加空格）
- 中文 + 数字：`支持 10 个`（加空格）
- 专有名词：`GitHub`、`JavaScript`、`TypeScript`、`Python`、`Node.js`、`React`、`Vue`、`macOS`、`API`、`URL`、`VS Code`、`npm`
- 中文段落 → 中文标点 `，。：（）`
- 英文段落 → 英文标点 `,.:()`

## 模板引用

生成文件时读取 `references/` 下的完整模板：

- `references/readme-template.md`
- `references/issue-template.md`
- `references/pr-template.md`
- `references/contributing-template.md`
