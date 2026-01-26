# Agent Skills

文档驱动的项目开发工作流技能集合。

## 简介

这个仓库包含了一系列可以在 Claude Code 中使用的 AI Agent Skills，旨在提高开发效率和标准化工作流程。

## 可用 Skills

### project-workflow

文档驱动的项目开发工作流。按标准操作流程 (SOP) 执行项目开发任务：
- 读取文档索引
- 查找/制定计划
- 按步骤执行
- 更新文档

**触发场景：**
- 用户请求开发新功能或模块
- 用户说"开始开发"、"执行计划"、"继续上次的任务"
- 需要按 plans/ 目录中的计划文件执行开发任务
- 项目包含 docs/ 和 plans/ 目录结构

## 安装方法

### 从 GitHub 安装

```bash
npx skills add https://github.com/zhucl1006/skills --skill project-workflow
```

### 本地安装

```bash
cd /path/to/this/repo
npx skills add . --skill project-workflow
```

## 使用方法

在 Claude Code 中，当触发场景匹配时，系统会自动激活相应的 skill。你也可以显式调用：

```bash
# 在 Claude Code 中
/project-workflow
```

## 目录结构

```
skills/
├── README.md                    # 本文件
├── package.json                 # npm 包配置
├── .gitignore                   # Git 忽略文件
└── project-workflow/           # project-workflow skill
    ├── skill.json              # Skill 配置文件
    └── prompt.md               # Skill 提示词
```

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT
