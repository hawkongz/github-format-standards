<div align="center">
  <h1>GitHub 格式规范</h1>
  <p>一个 Claude Code skill — 一行命令，审计、修正、发布任何项目到 GitHub。</p>

  [![GitHub stars](https://img.shields.io/github/stars/20kiki/github-format-standards?style=social)](https://github.com/20kiki/github-format-standards/stargazers)
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
  [![Platform: Claude Code](https://img.shields.io/badge/Platform-Claude%20Code-orange)](https://claude.ai/code)
</div>

**Language:** [English](../README.md) | [简体中文](README.md)

---

## 📋 目录
- [它能做什么](#它能做什么)
- [安装](#安装)
- [使用](#使用)
- [七阶段流水线](#七阶段流水线)
- [文件结构](#文件结构)
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

## 使用

在 Claude Code 中：

| 你说 | 触发 |
| :--- | :--- |
| `/GitHub格式规范` | 直接调用 |
| "把这个分享到 GitHub" | 完整流水线 |
| "帮我看下格式" | 审计 + 修复 |
| "创建 Issue 和 PR 模板" | 仅生成文件 |

## 七阶段流水线

### 1. 根目录审查
- 标记大文件、临时文件、编译产物、`.env`、IDE 残留
- 根据语言自动生成 `.gitignore`

### 2. 文件命名与目录结构
- 强制小写 + 连字符命名
- 源码 → `src/`、测试 → `tests/`、脚本 → `scripts/`

### 3. 文档修复
- 标题层级、代码块语言标注、表格对齐
- 中英文空格、专有名词大小写
- 图片路径（仅相对路径或 CDN）

### 4. 生成缺失文件
- `LICENSE`（默认 MIT）、`.gitignore`、`CONTRIBUTING.md`、`SECURITY.md`
- `.github/ISSUE_TEMPLATE/` + `.github/PULL_REQUEST_TEMPLATE.md`

### 5. README 重写
- 居中标题 + badges、自动生成目录
- 结构：功能特性 → 快速开始 → 安装 → 使用方法 → API → 贡献 → 许可证

### 6. 双语设置
- 根目录：英文、`zh-CN/`：中文
- 自然翻译，非机翻感

### 7. 发布
- 约定式提交（`feat:`、`fix:`、`docs:`）
- 语义化版本标签（`v1.0.0`）
- 创建 GitHub 仓库、推送、输出 URL

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
