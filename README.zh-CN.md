# Ant Design React Skill

[English README](./README.md)

一个面向生产级 React + Ant Design 项目的 Agent Skill，用于帮助 AI 编程工具构建、修改、审查和排查 Ant Design 应用。

这个 skill 适用于 Claude Code、Codex、OpenCode、OpenClaw，以及其他能够读取 `SKILL.md` 和仓库内参考资料的 AI 编程工具。它的目标不是提供零散代码片段，而是让 agent 在动手前先理解目标项目的依赖版本、框架、导入策略、目录结构、组件风格和验证命令，再按任务读取最相关的示例与参考资料。

## 特性

- 使用标准 `SKILL.md` skill 结构，便于在多种 AI 编程工具中安装和迁移。
- 面向 React、TypeScript、Ant Design 5.x、hooks、函数组件、Vite 和 Next.js。
- 覆盖表单、表格、弹窗、抽屉、上传、导航、权限、主题、i18n、请求状态和反馈 API 等生产场景。
- 提供 OA、MES、CRM、CMS、ERP、商城、仪表盘、内部工具、运营后台等企业后台模式。
- 通过 `SKILL.md` 的 Routing 表实现渐进加载，让 agent 只读取当前任务需要的资料。
- 强调 loading、empty、error、disabled、validation、permission、accessibility、responsive 和服务端校验等生产质量要求。

## 适用场景

当 AI 编程工具需要处理 React + Ant Design 项目时使用这个 skill，尤其适合：

- 创建或重构后台页面、CRUD 流程、仪表盘和数据管理页面。
- 构建生产级表单：类型化 values、异步校验、重置逻辑、提交 loading、服务端错误映射。
- 构建数据表格：筛选、排序、分页、多选、批量操作、行内编辑、导出、稳定 rowKey。
- 实现弹窗、抽屉、上传、确认流程、权限按钮和反馈服务。
- 配置 Ant Design 安装、`ConfigProvider`、`App`、全局 locale、主题 token、暗色模式和紧凑模式。
- 审查现有 Ant Design 代码的生产可用性和 API 准确性。

## 支持的 Agent

这个仓库遵循通用 Agent Skills 约定：一个包含必需 `SKILL.md` 文件和可选资源文件的目录。

| 工具 | 使用方式 |
|---|---|
| Claude Code | 安装为个人或项目 skill，然后通过 `/ant-design-react-skill` 调用，或直接要求 Claude 使用该 skill。 |
| Codex | 安装到用户或仓库 skills 目录；如果你的 Codex 环境支持从仓库安装 skill，发布后可使用本仓库 URL。 |
| OpenCode / OpenClaw | 如果工具支持 skill/plugin 目录，把完整目录放入对应位置；否则让 agent 读取本仓库的 `SKILL.md`。 |
| 其他 agent | 将 `SKILL.md` 以及相关的 `references/`、`examples/`、`templates/` 文件作为任务上下文。 |

核心规则：先读 `SKILL.md`，再按其中的 Routing 表只加载当前任务需要的文件。

## 安装

请保持仓库内容完整。`SKILL.md` 应位于 skill 目录根部，并与 `examples/`、`references/`、`templates/` 放在一起。

### Claude Code

个人 skill：

```bash
~/.claude/skills/ant-design-react-skill/
```

项目 skill：

```bash
<project>/.claude/skills/ant-design-react-skill/
```

常用调用方式：

```text
/ant-design-react-skill
```

### Codex

用户 skill：

```bash
~/.agents/skills/ant-design-react-skill/
```

仓库 skill：

```bash
<repo>/.agents/skills/ant-design-react-skill/
```

发布后，可以手动安装完整目录；如果你的 Codex 环境支持从仓库安装 skill，也可以使用本仓库 URL。

### 其他支持 SKILL.md 的 Agent

将完整目录安装到对应工具的个人、项目或插件 skills 目录。如果工具没有自动发现机制，可以使用显式指令：

```text
使用 <repo-url> 中的 ant-design-react-skill skill。先阅读 SKILL.md，按照其中的 Routing 表选择相关资料，并基于当前项目习惯实现这个 React + Ant Design 任务。
```

## 仓库结构

```text
ant-design-react-skill/
├── SKILL.md                         # Agent 入口：工作流、任务路由、硬性规则
├── README.md                        # 英文文档
├── README.zh-CN.md                  # 中文文档
├── LICENSE                          # MIT License
├── metadata.json                    # 可选项目元数据
├── agents/
│   └── openai.yaml                  # 可选 Codex UI 元数据
├── examples/
│   ├── guide/                       # 安装、Next.js、App provider、i18n、主题
│   ├── components/                  # Form、Table、Select、DatePicker、Drawer、Upload、状态展示
│   ├── advanced-forms/              # 动态 Form.List 和嵌套校验
│   ├── advanced-tables/             # 搜索表格、查询状态、多选清理
│   ├── auth/                        # 权限感知操作
│   ├── layout/                      # 后台壳和布局模式
│   ├── router/                      # 路由元信息和菜单生成
│   ├── production/                  # CRUD、仪表盘、导入导出、审批、CMS、订单流程
│   ├── integrations/                # 查询状态、Axios 错误、TanStack Query
│   ├── troubleshooting/             # 常见 Ant Design 问题
│   └── typescript/                  # 类型化 columns、forms、upload 模式
├── references/
│   ├── component-index.md           # 本地覆盖和缺失组件策略
│   ├── component-routing.md         # 组件选择指导
│   ├── business-scenarios.md        # 业务流程路由矩阵
│   ├── enterprise-patterns.md       # 企业领域模式
│   ├── modern-antd.md               # Ant Design 5 和版本敏感说明
│   ├── advanced-forms.md            # 复杂表单和服务端错误映射
│   ├── advanced-tables.md           # 重型表格状态、多选、性能
│   ├── request-error-handling.md    # 请求状态和错误 UI 映射
│   ├── permission-architecture.md   # 路由、菜单、按钮、字段权限
│   ├── theme-system.md              # token 和主题系统指导
│   ├── procomponents.md             # Ant Design Pro / ProComponents 指导
│   ├── testing-performance.md       # 验证、测试、性能、可访问性
│   └── production-checklist.md      # 生产质量门槛
└── templates/
    ├── component-usage.md           # 组件实现工作流
    └── project-setup.md             # React + Ant Design 项目模板
```

## 内容范围

| 领域 | 内容 |
|---|---|
| 指南 | 安装、Next.js、provider 配置、i18n、主题 token、暗色模式、Ant Design 5 App 上下文。 |
| 组件 | Form、动态表单、Table、搜索表格、Select、DatePicker、TreeSelect、Cascader、Descriptions、Tabs、Steps、Modal、Drawer、Upload、状态展示、下拉操作、布局、路由和权限。 |
| 生产流程 | CRUD 页面、详情抽屉、仪表盘、导入导出、设置页、审批、批量操作、CMS 编辑、订单/退款流程、错误/空状态、服务端校验。 |
| 集成 | 请求状态、现有 API client、Axios 错误映射、TanStack Query/SWR/Redux/Zustand 兼容、Ant Design Pro / ProComponents 指导。 |
| TypeScript | 类型化表单、表格行、columns、上传处理、回调和领域 payload。 |
| 企业领域 | OA、MES、CRM、CMS、ERP、商城、仪表盘和运营后台模式。 |

## 生产标准

生成或审查的代码应覆盖真实生产状态，而不是只处理成功路径：

- 使用 React 和 Ant Design API，不使用 Vue、Ant Design Vue 或过时 antd 写法。
- 匹配目标项目的包管理器、框架、导入策略、目录结构和组件风格。
- 对版本敏感的 props、events、slots、exposes 和 theme tokens，检查项目已安装的 `antd` 包或官方文档。
- 根据场景补齐 loading、empty、error、disabled、validation、permission 和响应式状态。
- 使用类型化表单 values、类型化表格行、稳定 `rowKey`、受控上传 `fileList` 和明确 reset 行为。
- 后台和运营工具优先使用密集、可扫描、任务导向的界面。

## 示例 Prompt

```text
帮我做一个 React + Ant Design 用户管理页面，包含筛选、服务端分页、行操作、新增/编辑抽屉和删除确认。
```

```text
检查这个 Ant Design Form 是否符合生产项目标准，并修复校验、提交 loading、服务端错误处理、reset 行为和脏数据关闭保护。
```

```text
给这个 Vite React 项目配置 Ant Design 5 ConfigProvider、App provider、主题 token 和暗色模式。
```

```text
重构这个 Ant Design Table，补齐类型化 columns、稳定 rowKey、显式查询状态、多选清理和可访问的行操作。
```

## 维护说明

发布前请确认：

- skill 目录名和 `SKILL.md` frontmatter 中的 
ame` 都是 `ant-design-react-skill`。
- `SKILL.md` 中引用的文件都真实存在。
- 示例中没有内部接口、密钥、公司数据或私有业务规则。
- `metadata.json` 的版本和 license 与发布状态一致。
- 为开源发布添加或更新根目录 `LICENSE` 文件。

## License

MIT

