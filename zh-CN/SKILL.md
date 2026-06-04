---
name: github-format-standards
description: "当用户想把项目分享到 GitHub 时使用。执行完整流水线：根目录审查、文件命名与目录结构、文档修复、生成缺失文件（LICENSE .gitignore CONTRIBUTING.md Issue/PR 模板）、README 重写（居中标题 目录）、双语设置、git init、约定式提交、gh repo create、push、语义化标签。触发词：分享到 GitHub、/GitHub格式规范。"
---

# GitHub 格式规范

当用户想把项目分享到 GitHub 时，运行完整流水线。**直接动手，不要只念规则。**

## 完整流水线（七个阶段）

### 阶段一：根目录审查

检查项目根目录是否整洁：

- **红线**：大文件（>1MB）、临时文件（`*.tmp`、`*.bak`、`~*`）、编译产物（`dist/`、`build/`、`*.pyc`）、敏感文件（`.env`、`credentials.*`、`*.pem`）、IDE 残留（`.vscode/`、`.idea/`）
- 发现后：警告用户，加入 `.gitignore`
- 确保 `.gitignore` 存在且至少覆盖：`node_modules/`、`__pycache__/`、`*.pyc`、`.env`、`.DS_Store`、`dist/`、`build/`、IDE 目录

```
根目录审查：
  ⚠  node_modules/ 存在 — 已加入 .gitignore
  ✓  无大文件、无密钥、无编译产物
  ✓  .gitignore 已创建，含 12 条规则
```

### 阶段二：文件命名与目录结构

**命名规则**：
- 全小写 + 连字符（`my-project`）或下划线（`my_project`），同一项目统一
- 文件名/目录名禁止空格、禁止中文（多语言文档项目除外）
- 脚本放 `scripts/`、示例放 `examples/`、文档放 `docs/`、测试放 `tests/` 或 `__tests__/`、源码放 `src/` 或 `lib/`
- 发现问题直接改名/移动

**标准结构**：
```
project/
├── src/           # 源码（或 lib/）
├── tests/         # 测试（或 __tests__/）
├── docs/          # 文档（可选，也可集中在 README）
├── scripts/       # 工具脚本
├── examples/      # 使用示例
├── README.md
├── LICENSE
├── .gitignore
└── CONTRIBUTING.md
```

小项目（单文件脚本）保持扁平结构即可，不要过度设计。

### 阶段三：文档检查与修复

逐文件检查所有 `.md`，直接改：

- [ ] 标题：`# 标题` 不是 `#标题`，不跳级（`#` → `##` → `###`）
- [ ] 代码块：每个 ` ``` ` 都标注语言
- [ ] 表格：分隔行加 `:---` 对齐标记
- [ ] 列表：符号统一（`*` 优先），子列表缩进 2 空格
- [ ] 命令可执行：每条 shell 命令必须显式标注解释器（`python script.py` 而非 `./script.py`；`bash script.sh` 而非 `./script.sh`；Windows 专用命令用 `powershell ...`）。读者不应猜测如何运行一条命令。
- [ ] 链接：无裸 URL，图片有 alt 文本
- [ ] 中英文空格：`使用 GitHub` 不是 `使用GitHub`；`支持 10 个` 不是 `支持10个`
- [ ] 专有名词：`GitHub` 不是 `github`，`JavaScript` 不是 `Javascript`
- [ ] 文件末尾：恰好一个空行
- [ ] 图片路径：相对路径或 CDN，禁止本地绝对路径

### 阶段四：生成缺失文件

- **`LICENSE`**（必选）：用户未指定则默认 MIT
- **`.gitignore`**（必选）：根据项目语言生成
- **`CONTRIBUTING.md`**（推荐）：多文件项目都应该有
- **`SECURITY.md`**（推荐）：安全漏洞报告说明
- **`.github/ISSUE_TEMPLATE/`**：bug 报告 + 功能建议 + `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`**：改动摘要、测试计划、截图区域

### 阶段五：README 重写

按以下结构重写 README。**标题居中、带目录。**

```
<div align="center">
  <h1>[项目名称]</h1>
  <p>一句话简介 — 5 秒看懂这个项目是做什么的</p>

  [![License](...)](LICENSE)
  [![Platform](...)](...)
  [![Stars](...)](...)
</div>

---

## 📋 目录
- [功能特性](#功能特性)
- [快速开始](#快速开始)
- [安装](#安装)
- [使用方法](#使用方法)
- [API 文档](#api-文档)
- [贡献指南](#贡献指南)
- [许可证](#许可证)

---

（描述段落——先说 WHY，再说 WHAT。不加标题。）

## ✨ 功能特性
* **功能一：** 说明
* **功能二：** 说明

## 🚀 快速开始
```bash
# 每条命令必须带解释器——不让人猜
python script.py input.txt
bash setup.sh
powershell -Command "..."
```

## 📦 安装
## 📖 使用方法
## 🔧 API 文档
## 🤝 贡献指南
## 📄 许可证
```

**目录规则**：
- 从 README 中的 `##` 标题自动生成
- 使用锚点链接：`[功能特性](#功能特性)`、`[快速开始](#快速开始)`
- 每个章节可用 emoji 前缀增强可扫描性（用户不喜欢则跳过）

### 阶段六：双语设置（中文项目）

如果项目是中文的或用户需要双语：

```
project/
├── README.md          # 英文
├── SKILL.md           # 英文（如适用）
├── LICENSE
└── zh-CN/
    ├── README.md      # 简体中文
    └── SKILL.md       # 简体中文（如适用）
```

两份 README 顶部都有 `**Language:** [English](../README.md) | [简体中文](README.md)`。

翻译要自然，不能机翻感。中文版读起来要像母语者写的。

### 阶段七：发布

1. 不是 git 仓库则 `git init`
2. `git add` 所有文件（排除密钥、`.env`、二进制文件）
3. 用约定式提交格式 commit：

```
type(scope): subject

feat(readme): 添加安装指南
fix: 修复 API 文档表格对齐
docs: 添加 CONTRIBUTING.md
```

**提交类型**：`feat`、`fix`、`docs`、`style`、`refactor`、`test`、`chore`
**主题**：英文 ≤72 字符；中文适当放宽但保持简洁

4. 如果远程仓库不存在，`gh repo create` 创建（公开，描述用 README 的 tagline）
5. `git push`
6. 如果是发布版：打语义化版本标签 `git tag v1.0.0`，推送标签
7. 输出最终 GitHub URL

如果用户只想本地预览，到阶段六结束，输出改动摘要。

---

## 摘要格式

完成后输出：

| 阶段 | 状态 | 详情 |
| :--- | :--- | :--- |
| 根目录审查 | ✓ | .gitignore 已创建，node_modules/ 已排除 |
| 目录结构 | ⚠ | `My Script.sh` → `scripts/my-script.sh` |
| 文档修复 | 6 处 | 3 张表格对齐、2 个代码块标注语言、1 个链接修复 |
| 文件生成 | 5 个 | LICENSE、.gitignore、CONTRIBUTING.md、Issue/PR 模板 |
| README | 重写 | 居中标题、目录、8 个章节 |
| 双语 | 已创建 | zh-CN/README.md + zh-CN/SKILL.md |
| 发布 | 已推送 | https://github.com/... |

---

## 读取 references/ 获取模板

- `references/readme-template.md` — 完整 README 模板
- `references/issue-template.md` — Issue 模板
- `references/pr-template.md` — PR 模板
- `references/contributing-template.md` — 贡献指南模板
