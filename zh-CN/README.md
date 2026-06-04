<div align="center">
  <h1>GitHub 格式规范</h1>
  <p>一个 <a href="https://claude.ai/code">Claude Code</a> skill — 一行命令，审计、修正、发布任何项目到 GitHub。</p>

  <a href="https://github.com/20kiki/github-format-standards/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/20kiki/github-format-standards?style=social"></a>
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-blue.svg"></a>
  <a href="https://claude.ai/code"><img alt="Platform: Claude Code" src="https://img.shields.io/badge/Platform-Claude%20Code-orange"></a>
</div>

**Language:** [English](../README.md) | [简体中文](README.md)

---

## 📋 目录
- [它能做什么](#它能做什么)
- [安装](#安装)
- [使用](#使用)
- [七阶段流水线](#七阶段流水线)
- [文件结构](#文件结构)
- [相关项目](#相关项目)
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
| 7. 发布 | `git init` → 约定式提交 → `gh repo create` → push → 打 tag |

## 安装

```bash
git clone https://github.com/20kiki/github-format-standards.git \
  ~/.claude/skills/github-format-standards
```

也可通过 [Claude Code 插件市场](https://claude.ai/code) 安装。

## 使用

在 [Claude Code](https://claude.ai/code) 中：

| 你说 | 触发 |
| :--- | :--- |
| `/GitHub格式规范` | 直接调用 |
| "把这个分享到 GitHub" | 完整流水线 |
| "帮我看下格式" | 审计 + 修复 |
| "创建 Issue 和 PR 模板" | 仅生成文件 |

## 七阶段流水线

### 1. 根目录审查
- 标记大文件、临时文件、编译产物、[`.env` 密钥](https://github.com/github/gitignore)、IDE 残留
- 根据语言自动生成 `.gitignore` — 参考 [gitignore.io](https://www.toptal.com/developers/gitignore)

### 2. 文件命名与目录结构
- 强制小写 + 连字符命名 — 参考 [Google 文件命名规范](https://google.github.io/styleguide/)
- 源码 → `src/`、测试 → `tests/`、脚本 → `scripts/`

### 3. 文档修复
- 标题层级、[代码块语言标注](https://docs.github.com/zh/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)、表格对齐
- 中英文空格（参考 [W3C 中文排版需求](https://www.w3.org/TR/clreq/)）、专有名词大小写
- 图片路径（[仅相对路径或 CDN](https://docs.github.com/zh/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#%E5%9B%BE%E7%89%87)）

### 4. 生成缺失文件
- [`LICENSE`](https://choosealicense.com/)（默认 MIT）、`.gitignore`、[`CONTRIBUTING.md`](https://docs.github.com/zh/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors)、[`SECURITY.md`](https://docs.github.com/zh/code-security/getting-started/adding-a-security-policy-to-your-repository)
- [`.github/ISSUE_TEMPLATE/`](https://docs.github.com/zh/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) + [`.github/PULL_REQUEST_TEMPLATE.md`](https://docs.github.com/zh/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)

### 5. README 重写
- 居中标题 + badges（参考 [FastAPI](https://github.com/fastapi/fastapi)、[React](https://github.com/facebook/react)、[Next.js](https://github.com/vercel/next.js) 等热门项目）
- 自动生成[带锚点链接的目录](https://docs.github.com/zh/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#%E5%88%86%E5%8C%BA%E9%93%BE%E6%8E%A5)
- 结构：功能特性 → 快速开始 → 安装 → 使用方法 → API → 贡献 → 许可证

### 6. 双语设置
- 根目录：英文、`zh-CN/`：中文 — 与[本项目](https://github.com/20kiki/causal-explanation-protocol)结构相同
- 自然翻译，非机翻感

### 7. 发布
- [约定式提交](https://www.conventionalcommits.org/zh-hans/)（`feat:`、`fix:`、`docs:`）
- [语义化版本](https://semver.org/lang/zh-CN/)标签（`v1.0.0`）
- 创建 GitHub 仓库、推送、输出 URL

## 相关项目

- [github-format-demo](https://github.com/20kiki/github-format-demo) — 格式优化效果演示
- [causal-explanation-protocol](https://github.com/20kiki/causal-explanation-protocol) — 使用本 skill 规范的真实项目

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

## 许可证

MIT
