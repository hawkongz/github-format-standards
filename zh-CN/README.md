<div align="center">
  <h1>GitHub 格式规范</h1>
  <p>一个 Claude Code skill — 一行命令，审计、修正、发布任何项目到 GitHub。</p>

  <a href="https://github.com/20kiki/github-format-standards/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/20kiki/github-format-standards?style=social"></a>
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-blue.svg"></a>
  <a href="https://claude.ai/code"><img alt="Platform: Claude Code" src="https://img.shields.io/badge/Platform-Claude%20Code-orange"></a>
</div>

**Language:** [English](../README.md) | [简体中文](README.md)

---

## 📋 目录
- [它能做什么](#它能做什么)
- [快速开始](#-快速开始)
- [安装](#安装)
- [使用](#使用)
- [七阶段流水线](#七阶段流水线)
- [文件结构](#文件结构)
- [标签](#标签)
- [许可证](#许可证)

---

## 它能做什么

说一句「分享到 GitHub」，这个 skill 自动搞定一切：

| 阶段 | 做什么 |
| :--- | :--- |
| 1. 根目录审查 | 扫描大文件、密钥、编译产物；自动生成 `.gitignore` |
| 2. 目录结构 | 修正文件命名（全小写、无空格），移入 `src/` `tests/` 等目录 |
| 3. 文档修复 | 对齐表格、标注代码块语言、修正中英文空格、专有名词大小写 |
| 4. 文件生成 | 创建 `LICENSE`、`CONTRIBUTING.md`、`SECURITY.md`、Issue/PR 模板 |
| 5. README | 重写 README：居中标题、自动目录、热门项目结构 |
| 6. 双语 | 需要时创建 `zh-CN/`，完整中文翻译 |
| 7. 发布 | `git init` → 约定式提交 → `gh repo create` → push → 语义化标签 |

## 🚀 快速开始

这个 skill 只需要两样东西：`SKILL.md` + `references/`（4 个模板文件）。

**第一步 — 打开终端**
- **macOS / Linux：** 打开终端（Terminal）
- **Windows：** 按 `Win + R`，输入 `powershell`，回车

**第二步 — 下载文件**

macOS / Linux：
```bash
mkdir -p ~/.claude/skills/github-format-standards/references
curl -o ~/.claude/skills/github-format-standards/SKILL.md https://raw.githubusercontent.com/20kiki/github-format-standards/master/SKILL.md
for f in readme-template issue-template pr-template contributing-template; do
  curl -o ~/.claude/skills/github-format-standards/references/$f.md https://raw.githubusercontent.com/20kiki/github-format-standards/master/references/$f.md
done
```

Windows（PowerShell）：
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\github-format-standards\references"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/20kiki/github-format-standards/master/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\github-format-standards\SKILL.md"
@("readme-template","issue-template","pr-template","contributing-template") | ForEach-Object {
  Invoke-WebRequest -Uri "https://raw.githubusercontent.com/20kiki/github-format-standards/master/references/$_.md" -OutFile "$env:USERPROFILE\.claude\skills\github-format-standards\references\$_.md"
}
```

**第三步 — 完成。** 在 Claude Code 中说「/GitHub格式规范」或「把这个分享到 GitHub」即可触发。

> 以后想更新：重新执行同样的命令，覆盖旧文件即可。

## 安装

### Claude Code
把 `SKILL.md` + `references/` 放到 `~/.claude/skills/github-format-standards/` 下即可。详见[快速开始](#-快速开始)。

## 使用

说 `/GitHub格式规范` 或「把这个分享到 GitHub」就会跑完整七阶段流水线。

## 七阶段流水线

### 1. 根目录审查
标记大文件（>1MB）、临时文件、编译产物、`.env` 密钥、IDE 残留。生成 `.gitignore`，覆盖 `node_modules/`、`__pycache__/`、`*.pyc`、`.env`、`.DS_Store`、`dist/`、`build/`、IDE 目录。

### 2. 文件命名与目录结构
强制小写 + 连字符。源码 → `src/`、测试 → `tests/`、脚本 → `scripts/`、示例 → `examples/`、文档 → `docs/`。单文件项目跳过。

### 3. 文档修复
标题层级、代码块语言标注、表格对齐。中英文空格、专有名词大小写（`GitHub` 不是 `github`）。图片路径：仅相对路径或 CDN。

### 4. 生成缺失文件
`LICENSE`（默认 MIT）、`.gitignore`、`CONTRIBUTING.md`、`SECURITY.md`、`.github/ISSUE_TEMPLATE/`（bug 报告 + 功能建议 + config）、`.github/PULL_REQUEST_TEMPLATE.md`。

### 5. README 重写
居中标题 + badges、从 `##` 标题自动生成目录。结构：功能特性 → 快速开始 → 安装 → 使用方法 → API → 贡献 → 许可证。

### 6. 双语设置
根目录：英文、`zh-CN/`：中文。两份 README 顶部都有 `**Language:**` 互链。翻译自然不机翻。

### 7. 发布
`git init` → `git add` → 约定式提交（`feat:`、`fix:`、`docs:`）→ `gh repo create` → `git push` → 正式发布时打语义化标签（`v1.0.0`）。

## 文件结构

```
├── SKILL.md                              # Skill（英文）
├── README.md                             # 本文件（英文）
├── LICENSE                               # MIT
├── references/
│   ├── readme-template.md
│   ├── issue-template.md
│   ├── pr-template.md
│   └── contributing-template.md
└── zh-CN/
    ├── README.md                         # 简体中文
    └── SKILL.md                          # 简体中文 Skill
```

## 标签

[`claude-code`](https://github.com/topics/claude-code) [`skill`](https://github.com/topics/skill) [`github`](https://github.com/topics/github) [`markdown`](https://github.com/topics/markdown) [`readme`](https://github.com/topics/readme) [`formatting`](https://github.com/topics/formatting)

## 许可证

MIT
