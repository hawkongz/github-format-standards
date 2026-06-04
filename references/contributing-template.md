# 贡献指南

感谢你对本项目的关注！以下是一些参与贡献的指引。

## 如何贡献

### 报告 Bug

1. 在 [Issues](../../issues) 中搜索是否已有相同问题
2. 如果没有，使用 Bug 报告模板创建新的 Issue
3. 尽可能提供复现步骤和环境信息

### 提交代码

1. Fork 本项目
2. 创建功能分支：`git checkout -b feature/your-feature`
3. 编写代码和测试
4. 确保代码风格符合规范
5. 提交变更：`git commit -m "feat: 添加 XX 功能"`
6. 推送到分支：`git push origin feature/your-feature`
7. 创建 Pull Request

## 开发环境

```bash
# 克隆项目
git clone https://github.com/username/project.git
cd project

# 安装依赖
npm install

# 运行测试
npm test

# 启动开发服务器
npm run dev
```

## 代码风格

- 使用 [Prettier](https://prettier.io) 格式化代码
- 遵循项目的 ESLint 配置
- 变量和函数命名使用驼峰命名法（camelCase）
- 提交信息遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范

## 提交信息规范

```
feat: 添加 XX 功能
fix: 修复 XX 问题
docs: 更新文档
style: 代码格式调整
refactor: 重构 XX 模块
test: 添加测试
chore: 构建/工具配置变更
```
