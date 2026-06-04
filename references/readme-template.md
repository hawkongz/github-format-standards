# [项目名称]

[一句话简介 — 用最少的字说清楚项目是什么、解决什么问题]

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Claude%20Code-blue)](https://code.claude.com)
[![Stars](https://img.shields.io/github/stars/username/project)](https://github.com/username/project)

## 📋 目录

- [功能特性](#功能特性)
- [快速开始](#快速开始)
- [安装](#安装)
- [标签](#标签)
- [贡献指南](#贡献指南)
- [许可证](#许可证)

> **TOC 锚点规则：** GitHub 会把标题里的 emoji 从锚点 ID 中删掉并补一个 `-`。
> `## 🔍 功能特性` → 锚点是 `#-功能特性`（不是 `#功能特性`）。
> 生成 TOC 后必须逐个验证锚点与实际标题匹配，且每个 TOC 条目必须有对应的 `##` 标题。

---

[项目背景描述 — 2-3 段，先讲 WHY 再讲 WHAT。不要直接跳到功能列表。]

## ✨ 功能特性

- **特性一：** 简要说明
- **特性二：** 简要说明
- **特性三：** 简要说明

## 🚀 快速开始

> **快速开始必须对零基础用户友好。** 交代清楚：需要哪些文件、在哪执行命令、装完怎么确认成功。

> **前置条件：** [列出必需的环境，如 `python 3.8+`。不要列 `git`，除非项目本身就是 git 工具。]

**第一步 — 打开终端**
- macOS / Linux：打开终端（Terminal）
- Windows：`Win + R`，输入 `powershell`，回车

**第二步 — 只下载 skill 需要的文件**

[说明需要哪些文件、为什么]

macOS / Linux：
```bash
mkdir -p ~/.claude/skills/project-name
curl -o ~/.claude/skills/project-name/SKILL.md https://raw.githubusercontent.com/username/project/main/SKILL.md
```

Windows（PowerShell）：
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\project-name"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/username/project/main/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\project-name\SKILL.md"
```

**第三步 — 完成。** [说明安装后如何验证、如何使用。]

> 以后想更新：重新执行同样的命令，覆盖旧文件即可。

> **原则：只下载 skill 运行需要的文件。** 不要 `git clone` 整个仓库——README、LICENSE、zh-CN/ 是给 GitHub 访客看的，skill 不需要它们。

## 📦 安装

[详细安装说明 — 各平台差异、多种安装方式等。如果快速开始已覆盖全部内容，本节可简化或省略。]

### 前置条件

- [依赖项 1 及版本要求]
- [依赖项 2 及版本要求]

### 安装步骤

```bash
# 具体安装命令
```

## 📖 使用方法

```bash
# 每个命令前加注释说明用途
python script.py input.txt
```

## 标签

[`tag1`](https://github.com/topics/tag1) [`tag2`](https://github.com/topics/tag2) [`tag3`](https://github.com/topics/tag3) [`tag4`](https://github.com/topics/tag4) [`tag5`](https://github.com/topics/tag5)

> 5-8 个标签，覆盖语言、平台、领域。每个标签链接到 `https://github.com/topics/<tag>`。

## 🤝 贡献指南

请参阅 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 📄 许可证

本项目基于 [MIT](LICENSE) 协议开源。
