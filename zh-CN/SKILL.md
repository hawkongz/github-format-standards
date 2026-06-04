---
name: github-format-standards
description: "当用户想把项目分享到 GitHub 时使用。执行完整流水线：根目录审查、文件命名与目录结构、文档修复（标题层级、代码块语言标注、表格对齐、命令显式解释器）、生成缺失文件（LICENSE .gitignore CONTRIBUTING.md Issue/PR 模板）、README 重写（居中标题 目录）、双语设置、git init、约定式提交、gh repo create、push、设置仓库 About（描述 话题标签）、语义化标签。触发词：分享到 GitHub、/GitHub格式规范、上传到 GitHub、发布到 GitHub、推到 GitHub、发到 GitHub、上传GitHub、发布GitHub。"
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
- [ ] 禁止模糊/口语化表达：将「你懂的」「you know the drill」「just works」替换为精确说明。平台标注用规范的 `macOS / Linux:` 格式，不用「你懂的 😄」这类写法。

### 阶段四：生成缺失文件

- **`LICENSE`**（必选）：用户未指定则默认 MIT
- **`.gitignore`**（必选）：根据项目语言生成
- **`AUTHORS.md`**（必选）：标注创作者和重要贡献者。用户是主要作者；如果项目借助 Claude Code 协作完成，将 Claude 列为贡献者。格式：创作者姓名/GitHub 用户名、贡献者姓名、每人一句话说明角色。
- **`CONTRIBUTING.md`**（推荐）：多文件项目都应该有
- **`SECURITY.md`**（推荐）：安全漏洞报告说明
- **`.github/ISSUE_TEMPLATE/`**：bug 报告 + 功能建议 + `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`**：改动摘要、测试计划、截图区域

### 阶段五：README 重写

按以下结构重写 README。**标题居中、带目录。**

#### Badge 颜色标准（必须遵守）

每个 badge 必须显式设置 shields.io 颜色。如果项目没有标准颜色，默认用 `lightgrey`。绝不能让颜色字段为空 —— shields.io 空颜色默认 `green`，这会让人误以为 badge 表示「通过/健康」，对非状态类 badge 是误导。

| Badge | 颜色 | 示例 |
| :--- | :--- | :--- |
| License (MIT) | `yellow` | `[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)` |
| License (Apache 2.0) | `blue` | `[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)` |
| License (GPL v3) | `blue` | `[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)` |
| Platform: Claude Code | `blue` | `[![Platform](https://img.shields.io/badge/Platform-Claude%20Code-blue)](https://code.claude.com)` |
| Platform: Python | `3776AB` | `[![Python](https://img.shields.io/badge/Python-3776AB)](https://python.org)` |
| Platform: Node.js | `339933` | `[![Node.js](https://img.shields.io/badge/Node.js-339933)](https://nodejs.org)` |
| Platform: Shell/Bash | `4EAA25` | `[![Shell](https://img.shields.io/badge/Shell-4EAA25)]()` |
| GitHub Stars | social | `[![Stars](https://img.shields.io/github/stars/owner/repo)](https://github.com/owner/repo)` |

**Badge 规则（放置任何 badge 前必读）：**
1. **每个 README 至少 3 个 badge**：License、Platform、Stars
2. License badge 链接到仓库的 `LICENSE` 文件
3. Platform badge 链接到平台的官方网站（没有规范 URL 则省略链接）
4. Stars badge 使用 shields.io GitHub 社交 badge — 不需要显式颜色，自动样式
5. Badge 放在居中 header `<div>` 中，紧接 tagline 下方
6. **禁止使用自定义/随意颜色。**从上表中选择。表中未列出的平台默认用 `lightgrey`。
7. **永远不要省略颜色字段。**`...badge/Platform-Claude%20Code`（无颜色）→ 显示为 `green` —— 语义完全错误。

```
<div align="center">
  <h1>[项目名称]</h1>
  <p>一句话简介</p>

  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
  [![Platform](https://img.shields.io/badge/Platform-Claude%20Code-blue)](https://code.claude.com)
  [![Stars](https://img.shields.io/github/stars/owner/repo)](https://github.com/owner/repo)

  <p><strong>Language:</strong> <a href="README.md">English</a> | <a href="zh-CN/README.md">简体中文</a></p>
</div>

---

## 📋 Table of Contents
- [Features](#features)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)

---

（描述段落——先说 WHY，再说 WHAT。不加标题。）

## ✨ Features
* **Feature 1:** description
* **Feature 2:** description

## 🚀 Quick Start

> **必须采用新手友好格式。**每个 Quick Start 必须回答三个问题：在哪运行命令、粘贴什么、「这就算装好了吗」。

**模板：**
```
> **What you need:** [前置条件 — 例如 "python 3.8+"]

**Step 1 — Open terminal**
- macOS / Linux: Open Terminal
- Windows: Win + R, type `powershell`, Enter

**Step 2 — Download only the files the skill needs**

[说明需要哪些文件、为什么：例如 "The skill is a single SKILL.md" 或 "needs SKILL.md + eyes.py"]

macOS / Linux:
`mkdir -p ... && curl -o ... raw.githubusercontent.com/...`

Windows (PowerShell):
`New-Item ... && Invoke-WebRequest ...`

**Step 3 — Done.** [如何验证、如何触发 skill]

> To update: re-run the same commands.
```

**规则：**
- **只下载 skill 运行所需的最少文件。**绝不要 `git clone` 整个仓库 —— README、LICENSE、zh-CN/ 是给 GitHub 访客看的，不是 skill 运行需要的。纯 SKILL.md 的 skill 只需 1 个文件；带脚本的 skill 只需脚本 + SKILL.md。
- 同时提供 Unix（`curl`）和 Windows（`Invoke-WebRequest`）命令。读者不应为了装一个 skill 还得装 `git`。
- 不写模糊笼统的说明。精确告诉读者下载了什么文件、为什么需要这些文件。
- 如果 skill 有额外依赖（pip 包、API key），在「Done」之前用编号步骤列出
- 以明确的成功标志结尾：如何验证装好了、如何触发 skill

## 📦 Installation
## 📖 Usage
## 🔧 API Reference
## 🤝 Contributing
## 📄 License
```

**话题标签章节**（放在贡献指南之前）：
- 必须：`## Topics` 章节，含可点击的 GitHub 话题标签链接
- 格式：`[`tag-name`](https://github.com/topics/tag-name)` — 每个标签链接到 GitHub 的话题发现页
- 包含 5-8 个相关话题，覆盖项目的语言、平台和领域
- 目录中加 `[Topics](#topics)`

**目录规则**：
- 从 README 中的 `##` 标题自动生成
- 使用锚点链接：`[Features](#features)`、`[Quick Start](#quick-start)`
- **关键 — emoji 在标题中会破坏锚点：**GitHub 会从标题 ID 中剥离 emoji，并在前面加 `-`（因为 emoji 与文字之间有空格）。`## 🔍 The Problem` → `#-the-problem`（不是 `#the-problem`）。
- **关键 — 禁止含变体选择符（U+FE0F）的 emoji 出现在标题中：**`⌨️` `☁️` `✈️` 等 emoji 会破坏标题 ID。GitHub 剥离基础符号但留下 U+FE0F 作为不可见字符，产生如 `#️-keyboard-shortcuts` 的 ID（而非 `#-keyboard-shortcuts`），目录链接会静默失效。**只用单码点 emoji**（📋 ⚡ 🔧 🚀 📦 🧠 💬 📖 ✨ 📌 🤝 📄 🔍）——绝不要用变体选择符 emoji。
- **目录链接不能有死链：**每个目录条目必须在文档中有对应的 `##` 标题。删除任何没有对应标题的目录条目。
- **每个 `##` 标题的 emoji 必须在全文档中唯一。**不允许两个章节共用同一个 emoji — 重复 emoji 会导致锚点歧义，扫描效率降低。定稿前审查所有标题。
- **安全 emoji 参考（仅单码点）：**`📋` 目录/命令/列表，`⚡` 快捷键/快速操作，`💬` 对话/聊天，`🔧` 配置/设置，`🚀` 快速开始/工作流，`📦` 安装/打包，`🧠` 策略/思考，`📚` 资源，`✨` 功能特性，`📌` 话题/标签，`🤝` 贡献，`📄` 许可证，`🔍` 问题/调查，`📖` 使用/指南，`❓` FAQ/故障排除，`🛠️` 工具/实用程序
- **禁止使用的 emoji（变体选择符会破坏 GitHub 标题 ID）：**`⌨️` `☁️` `✈️` `❤️` `⭐️` `🌐️` `🎨️` `🔒️` `🔓️` `📡️` —— 任何含不可见 U+FE0F 的 emoji。不确定时检查：如果 emoji 超过一个码点，就不要用。
- 所有 `##` 标题必须用 emoji 前缀，便于视觉扫描。
- **写完 README 后，至少随机验证 2 个目录链接：**用 WebFetch 获取 GitHub 上的 raw README，确认渲染后的标题 ID 与目录锚点一致。如果无法使用 WebFetch，用 Python 获取渲染页面并 grep `id="user-content-`。

### 阶段六：双语设置

**主动询问用户：**「这个项目需要中英双语文档吗？(Does this project need bilingual Chinese/English docs?)」

如果用户确认需要：

```
project/
├── README.md          # 英文
├── SKILL.md           # 英文（如适用）
├── LICENSE
└── zh-CN/
    ├── README.md      # 简体中文
    └── SKILL.md       # 简体中文（如适用）
```

两份 README 都在居中 header `<div>` 内、badge 下方放语言切换行：

- 根目录 `README.md` → `<a href="README.md">English</a> | <a href="zh-CN/README.md">简体中文</a>`
- `zh-CN/README.md` → `<a href="../README.md">English</a> | <a href="README.md">简体中文</a>`

**翻译规则（上下文感知，非字面直译）：**

1. **先识别领域。**翻译前，列出项目的关键领域（如支付/金融、容器/基础设施、AI/ML、安全）。领域术语有既定译法 —— 使用它们，不要自创。
2. **建立术语表。**从原文中提取 5-15 个关键术语，写出它们在目标语言中的正确对应。这能提前发现歧义（如 `settlement` → 结算还是清算，取决于上下文）。
3. **动词-宾语匹配。**英文动词可以跨宾语复用（`run a command` / `run a container`）；中文往往需要不同动词（运行命令 / 启动容器）。根据宾语调整动词，确保搭配自然。
4. **社区惯例优先。**如果项目社区已在使用某个术语（如「容器」对应 container，「工件」对应 artifact），直接用 —— 即使另一个翻译在技术上更准确。与生态一致 > 字典准确。
5. **代码引用保持原样。**变量名、函数名、CLI 标志、文件路径 —— 一律不翻译。只翻译外围说明文字。

**双视角审查（翻译后必须执行）：**

翻译完成后，从两个视角各审查一次：

| 轮次 | 角色 | 检查什么… |
| :--- | :--- | :--- |
| 🇨🇳 **中文母语者** | 读起来像地道中文吗？ | ① 词语搭配自然（不是翻译腔）② 技术术语符合社区用法 ③ 句子长度 —— 英文长句拆成中文短句 ④ 语气匹配项目（正式？随意？开发者友好？） |
| 🇬🇧 **英文母语者** | 原意是否完整保留？ | ① 信息无丢失或扭曲 ② 代码示例仍可运行（标志、路径、值未改动）③ 警告/注意事项的紧迫程度相同 ④ 脑中回译关键句 —— 意思是否一致？ |

**任一审查者发现问题都要修正。**两个视角冲突时：措辞以中文母语者为准，准确性以英文母语者为准。记录任何有意的偏离（如「此英文习语无中文对应，改为功能性描述」）。

最终效果：中文读者应感觉文档*原本就是用中文写的*，英文读者检查翻译时应发现每个技术细节都被忠实保留。

### 阶段七：发布

1. 不是 git 仓库则 `git init`
2. `git add` 所有文件（排除密钥、`.env`、二进制文件）
3. 用约定式提交格式 commit。**提交作者是用户本人**（使用 `git config user.name` / `user.email` 的配置）。提交前确认用户的 git 邮箱已在 GitHub 账号中验证——否则提交不会关联到 GitHub 头像。如果不确定，建议使用 `username@users.noreply.github.com`。询问用户是否需要在提交信息末尾加上 `Co-Authored-By: Claude <noreply@anthropic.com>`，只有用户同意才添加。

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
6. **设置仓库 About（描述 + 话题标签）**——GitHub 右侧栏元数据。用 `gh repo edit`：
   ```bash
   gh repo edit owner/repo --description "README tagline 一句话概述"
   gh repo edit owner/repo --add-topic "topic1" --add-topic "topic2" ...
   ```
   话题标签与 README 的 `## Topics` 章节保持一致，5-8 个，覆盖语言、平台和领域。
7. 如果是发布版：打语义化版本标签 `git tag v1.0.0`，推送标签
8. 输出最终 GitHub URL

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
| 发布 | 已推送 + About 已设置 | https://github.com/... |

---

## 读取 references/ 获取模板

- `references/readme-template.md` — 完整 README 模板
- `references/issue-template.md` — Issue 模板
- `references/pr-template.md` — PR 模板
- `references/contributing-template.md` — 贡献指南模板
