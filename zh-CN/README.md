# GitHub 格式规范 Skill

**Language:** [English](../README.md) | [简体中文](README.md)

[![GitHub stars](https://img.shields.io/github/stars/20kiki/github-format-standards?style=social)](https://github.com/20kiki/github-format-standards/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform: Claude Code](https://img.shields.io/badge/Platform-Claude%20Code-orange)](https://claude.ai/code)

一个 Claude Code skill，自动按照 GitHub 最佳实践检查和修正项目文档格式。

**先分类，再检查。逐项审计，统一规范。**

---

## 它能做什么

每次做好项目准备分享到 GitHub，都要手动调整格式？用这个 skill 一次性搞定：

* **Markdown 规范检查**：标题层级、代码块语言标注、表格对齐、列表缩进统一
* **README 结构优化**：按照 React / FastAPI / TensorFlow 等热门项目的通用模式重组
* **模板文件生成**：Issue 模板、PR 模板、CONTRIBUTING.md、SECURITY.md
* **中文项目专项**：中英文空格、专有名词大小写、标点符号匹配

## 安装

```bash
# 克隆到 Claude Code skills 目录
git clone https://github.com/20kiki/github-format-standards.git \
  ~/.claude/skills/github-format-standards
```

或者直接把 `SKILL.md` 放到任何 Claude Code 能识别为 skill 的目录。

## 使用

在 Claude Code 中说：

- `/GitHub格式规范` — 直接调用
- 「帮我看下格式」— 自动触发
- 「整理下 README，准备发 GitHub」— 自动触发
- 「创建 Issue 和 PR 模板」— 自动触发

## 工作流程

1. 扫描项目中所有 `.md` 文件和 `.github/` 目录
2. 逐文件检查，发现问题直接修正
3. 输出改动摘要，列出每处修改及原因

## 规范覆盖

| 类别 | 内容 |
| :--- | :--- |
| Markdown 基础 | 标题层级不跳级、代码块标注语言、表格对齐、链接有描述、图片有 alt、列表缩进统一 |
| README 结构 | 标题+简介→Badges→描述→功能特性→快速开始→安装→API→配置→贡献→许可证 |
| 社区文件 | ISSUE_TEMPLATE、PULL_REQUEST_TEMPLATE、CONTRIBUTING.md、SECURITY.md |
| 中文专项 | 中英文间空格、专有名词大小写、中文标点对应中文段落 |

## 规范来源

格式规则基于对热门项目的实际分析：

* **列表符号 `*`**：React、TensorFlow、FastAPI 均使用 `*`
* **功能特性格式**：`* **关键词：** 说明` 模式来自 React
* **标题 + Badges 居中**：来自 FastAPI / Next.js / TensorFlow
* **`<details>` 折叠**：来自 FastAPI 的长文档
* **项目结构树**：来自大多数成熟项目

## 文件结构

```
├── SKILL.md                              # Skill 主文件
├── README.md                             # 本文件
└── references/
    ├── readme-template.md                # README 完整模板
    ├── issue-template.md                 # Issue 模板
    ├── pr-template.md                    # Pull Request 模板
    └── contributing-template.md          # 贡献指南模板
```

## 许可证

MIT
