# Ant Design React Skill

[中文文档](./README.zh-CN.md)

A production-oriented Agent Skill for building, modifying, reviewing, and troubleshooting React applications that use [Ant Design](https://ant.design/).

This skill is designed for AI coding agents such as Claude Code, Codex, OpenCode, OpenClaw, and other tools that can read a `SKILL.md` file plus bundled reference material. It helps the agent inspect the target project, follow local conventions, choose appropriate Ant Design patterns, and avoid stale or framework-mismatched APIs.

## Highlights

- Standard `SKILL.md` skill layout for broad AI-agent compatibility.
- React, TypeScript, Ant Design 5.x, hooks, function components, Vite, and Next.js oriented guidance.
- Production patterns for forms, tables, modals, drawers, uploads, navigation, permissions, themes, i18n, request state, and feedback APIs.
- Enterprise admin scenarios for OA, MES, CRM, CMS, ERP, commerce, dashboards, internal tools, and operations consoles.
- Progressive-disclosure references so agents load only the files relevant to the current task.
- Quality gates for loading, empty, error, disabled, validation, permission, accessibility, responsive layout, and server-side validation handling.

## When To Use

Use this skill when an AI coding agent needs to work on React + Ant Design code, especially for:

- Creating or refactoring admin pages, CRUD workflows, dashboards, and data-management screens.
- Building production forms with typed values, async validation, reset behavior, submit loading, and server error mapping.
- Building data tables with filters, sorting, pagination, selection, bulk actions, inline editing, export, and stable row keys.
- Implementing modals, drawers, uploads, confirmation flows, permission-aware actions, and feedback services.
- Configuring Ant Design installation, `ConfigProvider`, `App`, global locale, theme tokens, dark mode, and compact mode.
- Reviewing existing Ant Design code for production readiness and API correctness.

## Supported Agents

This repository follows the common Agent Skills convention: a folder with a required `SKILL.md` file and optional bundled resources.

| Tool | Usage |
|---|---|
| Claude Code | Install as a personal or project skill, then invoke `/ant-design-react-skill` or ask Claude to use the skill. |
| Codex | Install under a user or repository skills directory. If your Codex environment supports repository-based skill installation, use this repository URL after publishing. |
| OpenCode / OpenClaw | Install the folder in the tool's skill/plugin location if supported, or point the agent at this repository and ask it to read `SKILL.md`. |
| Other agents | Provide `SKILL.md` and the relevant files from `references/`, `examples/`, or `templates/` as task context. |

The important rule is: read `SKILL.md` first, then follow its routing table to load only the reference files needed for the task.

## Installation

Keep the repository contents together. `SKILL.md` should remain at the root of the skill folder, next to `examples/`, `references/`, and `templates/`.

### Claude Code

Personal skill:

```bash
~/.claude/skills/ant-design-react-skill/
```

Project skill:

```bash
<project>/.claude/skills/ant-design-react-skill/
```

Typical invocation:

```text
/ant-design-react-skill
```

### Codex

User skill:

```bash
~/.agents/skills/ant-design-react-skill/
```

Repository skill:

```bash
<repo>/.agents/skills/ant-design-react-skill/
```

After publishing, install the full folder manually or use repository-based installation if your Codex environment supports it.

### Other SKILL.md Agents

Install the full folder into the agent's personal, project, or plugin skills directory. If the tool does not provide automatic discovery, use an explicit instruction:

```text
Use the ant-design-react-skill skill from <repo-url>. Read SKILL.md first, follow its routing table, and implement this React + Ant Design task using the local project conventions.
```

## Repository Structure

```text
ant-design-react-skill/
├── SKILL.md                         # Agent entrypoint: workflow, routing, hard rules
├── README.md                        # English documentation
├── README.zh-CN.md                  # Chinese documentation
├── LICENSE                          # MIT license
├── metadata.json                    # Optional project metadata
├── agents/
│   └── openai.yaml                  # Optional Codex UI metadata
├── examples/
│   ├── guide/                       # Installation, Next.js, App provider, i18n, theme
│   ├── components/                  # Form, Table, Select, DatePicker, Drawer, Upload, status
│   ├── advanced-forms/              # Dynamic Form.List and nested validation
│   ├── advanced-tables/             # Search table, query state, selection cleanup
│   ├── auth/                        # Permission-aware actions
│   ├── layout/                      # Admin shell and layout patterns
│   ├── router/                      # Route metadata and menu generation
│   ├── production/                  # CRUD, dashboard, import/export, approval, CMS, order flows
│   ├── integrations/                # Query state, Axios errors, TanStack Query
│   ├── troubleshooting/             # Common Ant Design issues
│   └── typescript/                  # Typed columns, forms, upload patterns
├── references/
│   ├── component-index.md           # Local coverage and missing-component policy
│   ├── component-routing.md         # Component selection guidance
│   ├── business-scenarios.md        # Business workflow routing matrix
│   ├── enterprise-patterns.md       # Enterprise domain patterns
│   ├── modern-antd.md               # Ant Design 5 and version-sensitive notes
│   ├── advanced-forms.md            # Complex form and server error mapping
│   ├── advanced-tables.md           # Heavy table state, selection, performance
│   ├── request-error-handling.md    # Request state and error UI mapping
│   ├── permission-architecture.md   # Route, menu, action, field permissions
│   ├── theme-system.md              # Token and theme system guidance
│   ├── procomponents.md             # Ant Design Pro / ProComponents guidance
│   ├── testing-performance.md       # Validation, testing, performance, accessibility
│   └── production-checklist.md      # Production quality gates
└── templates/
    ├── component-usage.md           # Component implementation workflow
    └── project-setup.md             # React + Ant Design setup template
```

## What Is Included

| Area | Contents |
|---|---|
| Guides | Installation, Next.js, provider setup, i18n, theme tokens, dark mode, Ant Design 5 app context. |
| Components | Form, dynamic forms, Table, search tables, Select, DatePicker, TreeSelect, Cascader, Descriptions, Tabs, Steps, Modal, Drawer, Upload, status, dropdowns, layout, routing, and permissions. |
| Production workflows | CRUD pages, detail drawers, dashboards, import/export, settings, approval, bulk actions, CMS editing, order/refund flows, error/empty states, server validation. |
| Integrations | Request state, existing API clients, Axios error mapping, TanStack Query/SWR/Redux/Zustand compatibility, Ant Design Pro / ProComponents guidance. |
| TypeScript | Typed forms, table rows, columns, upload handlers, callbacks, and domain payloads. |
| Enterprise domains | OA, MES, CRM, CMS, ERP, commerce, dashboards, and operations-console patterns. |

## Production Standards

Generated or reviewed code should cover real production states, not just the success path:

- Use React and Ant Design APIs, not Vue, Ant Design Vue, or legacy antd patterns.
- Match the target project's package manager, framework, import strategy, directory structure, and component style.
- Verify version-sensitive props, events, slots, exposed methods, and theme tokens against the installed `antd` package or official documentation.
- Include loading, empty, error, disabled, validation, permission, and responsive states where relevant.
- Use typed form values, typed table rows, stable `rowKey`, controlled upload `fileList`, and clear reset behavior.
- Prefer dense, scannable, task-oriented layouts for admin and operational tools.

## Example Prompts

```text
Build a React + Ant Design user management page with filters, server-side pagination, row actions, a create/edit drawer, and delete confirmation.
```

```text
Review this Ant Design Form implementation for production readiness and fix validation, submit loading, server error handling, reset behavior, and dirty-state protection.
```

```text
Set up Ant Design 5 ConfigProvider, App provider, theme tokens, and dark mode in this Vite React project.
```

```text
Refactor this Ant Design Table to use typed columns, stable rowKey, explicit query state, selection cleanup, and accessible row actions.
```

## Maintenance Notes

Before publishing a release:

- Keep the skill folder name and `SKILL.md` frontmatter name as `ant-design-react-skill`.
- Confirm all references in `SKILL.md` point to existing files.
- Check that examples do not contain private endpoints, credentials, company data, or proprietary business rules.
- Keep `metadata.json` aligned with the release version and license.
- Add or update a root `LICENSE` file for open-source distribution.

## License

MIT

