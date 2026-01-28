# Agent Skills

文档驱动的项目开发工作流技能集合。

## 简介

这个仓库包含了一系列可以在 Claude Code 中使用的 AI Agent Skills，旨在提高开发效率和标准化工作流程。

核心理念：**文档先行，计划驱动** - 通过完善的项目文档和结构化的开发计划，确保项目开发有据可循、可追溯。

## 可用 Skills

### project-docs-setup

**项目文档结构创建助手** - 作为资深产品经理，通过多轮对话深入了解项目需求，分析合理性并提供最佳实践建议，最终生成完整的技术文档体系。

**使用时机：**
- 新项目启动，需要建立文档体系（推荐第一步）
- 现有项目缺少规范文档，需要补充完善
- 已有代码但缺少文档，需要根据代码回补文档
- 需要专业的产品和架构分析建议

**触发方式：**
- "创建项目文档" / "初始化项目文档" / "设置项目文档"
- "根据代码生成文档" / "回补项目文档" / "补充项目文档"
- 直接描述项目需求，如"帮我创建一个在线教育平台的文档"

**生成内容：**
- 📄 docs/README.md - 文档索引
- 📋 docs/specs/PRD.md - 产品需求文档
- 🏗️ docs/specs/SAD.md - 软件架构设计
- 📖 docs/guides/AI-DEVELOPMENT-GUIDE.md - AI 开发指南
- 📦 docs/modules/*.md - 模块文档
- 🗂️ 目录结构（plans/、database/、api/ 等）

---

### project-planning

**项目计划产出工具** - 通过需求澄清、设计讨论、计划编写，产出可执行的开发计划。

**使用场景：**
- 需求不明确，需要多轮讨论澄清（Brainstorming 模式）
- 需求明确，直接编写详细实现计划（Writing Plans 模式）
- 为 project-workflow 准备可执行的计划文档

**触发方式：**
- "帮我规划 XXX 功能" / "设计 XXX 模块"
- "我想实现 XXX，但不确定怎么做"
- "为 XXX 功能编写实现计划"

**输出：**
- 📝 docs/plans/001-feature-name.md - 开发计划（包含设计和实施，根据复杂度决定详细程度）

**工作模式：**
- **Brainstorming 模式**：需求不明确时，通过多轮对话澄清需求、探索方案、展示设计
- **Writing Plans 模式**：需求明确时，直接编写详细的 TDD 实现计划

---

### project-workflow

**文档驱动的项目开发工作流** - 智能判断任务类型，执行已有计划。

**前置条件：**
- 项目应该已有 docs/ 文档结构（PRD、SAD 等）
- 如果是新项目，建议先使用 **project-docs-setup** skill 创建完整文档
- 如果需要制定计划，建议使用 **project-planning** skill

**功能特性：**
- ✅ 执行指定的开发计划（如 "执行 plan 001"）
- ✅ TDD 驱动开发流程
- ✅ 自动代码质量检查（使用通用型 agent）
- ✅ 自动更新项目文档

**触发方式：**
- "执行 plan 001" / "继续 001-user-authentication"
- "开始开发" / "执行计划" / "继续上次的任务"

---

## 推荐工作流

```
1. 项目启动
   ↓
2. 使用 project-docs-setup 创建完整文档
   ├─ 模式 A：新项目文档创建（从需求到文档）
   │   ├─ 多轮对话了解需求
   │   ├─ 产品经理式的分析和建议
   │   └─ 生成 PRD、SAD、开发指南等
   │
   └─ 模式 B：代码回补文档（从代码到文档）
       ├─ 分析现有代码库
       ├─ 提取架构和功能信息
       └─ 生成完整文档体系
   ↓
3. 使用 project-planning 制定开发计划
   ├─ Brainstorming 模式：需求不明确时
   │   ├─ 多轮对话澄清需求
   │   ├─ 探索多种方案
   │   └─ 产出设计和实施计划
   │
   └─ Writing Plans 模式：需求明确时
       └─ 直接编写详细的 TDD 实现计划
   ↓
4. 使用 project-workflow 执行开发
   ├─ 执行已有计划："执行 plan 001"
   ├─ TDD 驱动开发
   ├─ 自动代码审查
   └─ 更新项目文档
   ↓
5. 持续迭代
   └─ 文档和代码保持同步
```

**三个 skill 的关系：**
- **project-docs-setup**: 文档创建（产品经理角色）→ 创建项目文档体系
- **project-planning**: 计划制定（架构师角色）→ 制定功能开发计划
- **project-workflow**: 开发执行（工程师角色）→ 执行计划并更新文档

**建议流程：**
```
project-docs-setup → project-planning → project-workflow
```

## 安装方法

### 从 GitHub 安装

```bash
# 安装所有 skills（推荐）
npx skills add https://github.com/zhucl1006/skills --skill project-docs-setup --skill project-planning --skill project-workflow

# 或单独安装
npx skills add https://github.com/zhucl1006/skills --skill project-docs-setup
npx skills add https://github.com/zhucl1006/skills --skill project-planning
npx skills add https://github.com/zhucl1006/skills --skill project-workflow
```

### 本地安装

```bash
cd /path/to/this/repo

# 安装所有 skills
npx skills add . --skill project-docs-setup --skill project-planning --skill project-workflow

# 或单独安装
npx skills add . --skill project-docs-setup
npx skills add . --skill project-planning
npx skills add . --skill project-workflow
```

## 使用方法

### 新项目启动

```bash
# 1. 首先创建项目文档
/project-docs-setup
# 或直接说："创建项目文档"
# 或描述你的项目："帮我创建一个在线教育平台的文档"

# 2. 制定功能开发计划
/project-planning
# 或说："帮我规划用户认证功能"
# 或说："为 XXX 功能编写实现计划"

# 3. 执行开发任务
/project-workflow
# 或说："执行 plan 001"
```

### 现有项目

```bash
# 如果缺少文档，先补充文档
/project-docs-setup
# 可以选择"根据代码生成文档"模式

# 如果已有文档但需要新功能计划
/project-planning

# 如果已有计划，直接执行
/project-workflow
```

### 显式调用

在 Claude Code 中，当触发场景匹配时，系统会自动激活相应的 skill。你也可以显式调用：

```bash
# 创建文档
/project-docs-setup

# 制定计划
/project-planning

# 执行开发
/project-workflow
```

## 目录结构

```
skills/
├── README.md                              # 本文件
├── package.json                           # npm 包配置
├── .gitignore                             # Git 忽略文件
├── _shared/                               # 共享资源
│   ├── docs-templates/                   # 文档模板（project-docs-setup 使用）
│   │   ├── README-template.md            # 文档索引模板
│   │   ├── PRD-template.md               # 产品需求文档模板
│   │   ├── SAD-template.md               # 架构设计文档模板
│   │   ├── AI-DEVELOPMENT-GUIDE-template.md  # 开发指南模板
│   │   └── module-template.md            # 模块文档模板
│   └── plan-templates/                   # 计划模板（project-planning 使用）
│       └── combined-plan-template.md     # 综合���划模板
├── project-docs-setup/                    # 项目文档创建 skill
│   └── SKILL.md                          # Skill 主文件
├── project-planning/                      # 项目计划制定 skill
│   └── SKILL.md                          # Skill 主文件
└── project-workflow/                      # 项目开发工作流 skill
    └── SKILL.md                          # Skill 主文件
```

## 核心特性

### 📋 完整的文档体系
- 产品需求文档（PRD）
- 软件架构设计（SAD）
- AI 开发指南
- 模块文档
- API 和数据库设计文档

### 🤖 智能开发工作流
- 三阶段工作流：文档创建 → 计划制定 → 开发执行
- 自动识别任务类型和需求清晰度
- TDD 驱动开发
- 自动代码质量检查和优化

### 💬 产品经理式对话
- 多轮对话深入了解需求
- 合理性分析和风险识别
- 基于最佳实践的专业建议
- 架构设计和技术选型指导

### 📋 灵活的计划制定
- Brainstorming 模式：需求不明确时的探索式对话
- Writing Plans 模式：需求明确时的快速计划编写
- 支持多种方案对比和权衡分析
- 详细的 TDD 实施步骤

### ✅ 质量保证
- 代码审查自动化（BLOCKER/MAJOR/MINOR 分级）
- 测试驱动开发
- 文档与代码同步更新
- 执行记录可追溯

## 文档结构示例

使用这两个 skills 后，你的项目会有如下结构：

```
your-project/
├── docs/
│   ├── README.md                          # 文档索引
│   ├── specs/
│   │   ├── PRD.md                        # 产品需求文档
│   │   └── SAD.md                        # 架构设计文档
│   ├── guides/
│   │   └── AI-DEVELOPMENT-GUIDE.md       # AI 开发指南
│   ├── modules/
│   │   ├── user-module.md                # 用户模块文档
│   │   └── auth-module.md                # 认证模块文档
│   ├── plans/
│   │   ├── 001-user-authentication.md    # 开发计划 001
│   │   └── 002-payment-integration.md    # 开发计划 002
│   ├── database/
│   │   ├── SCHEMA.md                     # 数据库设计
│   │   └── MIGRATIONS.md                 # 迁移记录
│   └── api/
│       └── api-spec.md                   # API 规范
└── src/                                   # 你的源代码
```

## 贡献

欢迎提交 Issue 和 Pull Request！

## 许可证

MIT
