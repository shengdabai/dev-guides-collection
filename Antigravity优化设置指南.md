# 🚀 Antigravity 优化设置指南

> 专为新手小白设计，帮助你高效使用 Google Antigravity IDE，节省月度会员用量

---

## 📋 目录

1. [确保使用 Cloud 模式](#1-确保使用-cloud-模式)
2. [关键设置优化](#2-关键设置优化)
3. [开发模式选择](#3-开发模式选择)
4. [GEMINI.md 配置](#4-geminimd-配置)
5. [Agent Rules 规则配置](#5-agent-rules-规则配置)
6. [MCP 云服务配置](#6-mcp-云服务配置)
7. [节省用量技巧](#7-节省用量技巧)
8. [高级功能活](#8-高级功能激活)

---

## 1. 确保使用 Cloud 模式

### ✅ 验证 Cloud 模式

Antigravity 默认使用 **Cloud 模式**（Gemini 云端 API），而非本地模式。确认方法：

1. **打开 Antigravity** → 点击左下角的 **齿轮图标** (Settings)
2. 查看 **Account** 页面，确认你已登录 Google 账户
3. 确保显示 **"Connected to Gemini"** 或类似的云连接状态

> [!TIP]
> 如果你使用的是 **Google AI Pro**（$20/月）订阅，Antigravity 会自动识别并提供更高的配额限制！

### ⚠️ 确认订阅已激活

在 Antigravity 中输入以下命令检查状态：
```
/status
```

查看输出中的 **Plan** 字段，应显示为 `Pro` 或 `Individual`。

---

## 2. 关键设置优化

### 📁 创建全局设置文件

在你的用户目录创建 `~/.gemini/settings.json`：

```json
{
  "gemini.model": "gemini-2.5-flash",
  "gemini.contextWindow": "1m",
  "gemini.agentMode": true,
  "gemini.planningMode": true,
  "gemini.autoSave": true
}
```

#### 设置说明：

| 设置项 | 推荐值 | 说明 |
|--------|--------|------|
| `gemini.model` | `gemini-2.5-flash` | ⚡ Flash 模型速度快、消耗少（推荐日常使用） |
| `gemini.model` | `gemini-2.5-pro` | 🧠 Pro 模型推理更强（复杂任务时切换） |
| `gemini.contextWindow` | `1m` | AI 能理解的代码上下文大小（100万 tokens） |
| `gemini.planningMode` | `true` | Agent 会先规划再执行，减少错误 |

> [!IMPORTANT]
> **节省用量关键**：日常使用 `gemini-2.5-flash`，只在需要复杂推理时切换到 `gemini-2.5-pro`！

---

## 3. 开发模式选择

### 🎮 三种开发模式

在 Settings → **Development Mode** 中选择：

| 模式 | 推荐度 | 说明 |
|------|--------|------|
| **Agent-assisted** | ⭐⭐⭐ 推荐 | 你控制，AI 辅助。最省用量！ |
| Review-driven | ⭐⭐ | AI 执行前会询问你确认 |
| Agent-driven (Autopilot) | ⭐ | 全自动，消耗最大 |

> [!CAUTION]
> 新手请避免使用 **Agent-driven (Autopilot)** 模式！它会自动执行命令，消耗大量配额，还可能执行你不想要的操作。

### 推荐配置

```
Development Mode: Agent-assisted（代理辅助）
Terminal Policy: Ask（询问后执行）
Review Policy: On（开启审核）
```

---

## 4. GEMINI.md 配置

### 📝 创建全局规则文件

在 `~/.gemini/GEMINI.md` 中添加：

```markdown
# 我的编程助手配置

## 语言偏好
- 请用中文回答所有问题
- 代码注释使用中文
- 解释清晰简洁，适合新手理解

## 编码风格
- 遵循项目现有的代码风格
- 添加必要的注释解释关键逻辑
- 提供代码示例时包含使用说明

## 执行限制
- 执行任何命令前先解释其作用
- 修改文件前先告知将要改动的内容
- 遇到复杂决策时询问我的意见

## 节省用量
- 回答尽量简洁精准
- 避免不必要的代码重复生成
- 一次性完成任务，减少多轮对话
```

### 📂 项目级规则

在项目根目录创建 `.gemini/GEMINI.md`：

```markdown
# 项目特定规则

## 项目信息
- 项目类型: [填写你的项目类型，如 Web 应用]
- 技术栈: [如 React, TypeScript]
- 目标: [项目目标简述]

## 开发指南
- 新增功能前请先阅读 README.md
- 遵循项目的文件结构规范
- 测试后再提交代码
```

---

## 5. Agent Rules 规则配置

### 📂 创建工作区规则

在项目中创建 `.agent/rules/` 文件夹，添加以下规则文件：

#### `.agent/rules/chinese.md`（中文交流规则）
```markdown
---
description: 使用中文进行所有交流
activation: always_on
---
- 所有输出使用简体中文
- 技术术语可保留英文但需中文解释
- 错误信息需翻译为中文
```

#### `.agent/rules/beginner-friendly.md`（新手友好规则）
```markdown
---
description: 新手友好的详细解释
activation: always_on
---
- 执行每个步骤前解释原因
- 使用简单易懂的语言
- 提供代码时加上使用示例
- 遇到错误时提供完整的解决方案
```

#### `.agent/rules/cost-saving.md`（节省用量规则）
```markdown
---
description: 优化 API 用量
activation: always_on
---
- 优先使用简洁回答
- 避免重复生成相似代码
- 合并多个小任务为一个完整任务
- 使用增量编辑而非完全重写文件
```

---

## 6. MCP 云服务配置

### ☁️ 启用云服务连接

MCP（Model Context Protocol）让 Antigravity 连接到各种云服务。

在 `~/.gemini/antigravity/mcp_config.json` 中配置：

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-server-filesystem", "/Users/tonysheng/Desktop/编程"]
    }
  }
}
```

### 🔌 推荐的 MCP 服务

在 Antigravity 中点击 **MCP Store** 可以安装以下服务：

| 服务 | 用途 |
|------|------|
| **GitHub** | 直接管理 Git 仓库 |
| **Notion** | 连接 Notion 笔记 |
| **Figma** | 设计稿转代码 |
| **Supabase** | 数据库操作 |

---

## 7. 节省用量技巧

### 💰 优化策略

#### 1. 模型选择策略

| 任务类型 | 推荐模型 | 消耗估算 |
|----------|----------|----------|
| 简单问答、代码补全 | `gemini-2.5-flash` | 低 ⬇️ |
| 代码重构、复杂架构设计 | `gemini-2.5-pro` | 高 ⬆️ |
| 深度推理、难题调试 | `gemini-3-deep-think` | 非常高 ⬆️⬆️ |

#### 2. 减少消耗的习惯

```
✅ DO（推荐做法）:
- 一次性描述清楚需求，减少来回对话
- 使用具体的任务描述，减少 AI 猜测
- 先用 Flash 模型尝试，不行再换 Pro
- 利用规则文件减少重复解释

❌ DON'T（避免做法）:
- 避免开启 Autopilot 模式长时间运行
- 避免让 AI 生成大量你不需要的代码
- 避免模糊的提示词导致多次重试
- 避免同时打开多个 Agent 任务
```

#### 3. 配额监控

在 Antigravity 中使用：
```
/usage
```
查看当前的使用情况和剩余配额。

> [!TIP]
> **Pro 订阅用户**：配额每 5 小时刷新一次！合理安排工作时间，避免短时间内集中消耗。

---

## 8. 高级功能激活

### 🧠 Planning Mode（规划模式）

让 AI 在执行前先创建计划：

1. Settings → **Agent Settings**
2. 开启 **Planning Mode**

效果：AI 会先生成 `implementation_plan.md`，你确认后再执行。

### 🔄 Workflows（工作流）

创建可复用的工作流，在 `.agent/workflows/` 目录：

#### `.agent/workflows/new-component.md`
```markdown
---
description: 创建新的 React 组件
---

1. 创建组件文件 `src/components/{ComponentName}.tsx`
2. 添加基础 TypeScript 类型定义
3. 创建对应的样式文件 `{ComponentName}.css`
4. 在 `index.ts` 中导出组件
5. 添加基础单元测试
```

使用方式：在 Chat 中输入 `/new-component`

### 🎯 Terminal Policy

设置终端命令执行策略：

| 策略 | 说明 | 推荐 |
|------|------|------|
| Off | 不自动执行任何命令 | 最安全 |
| Ask | 执行前询问确认 | ⭐ 推荐 |
| Auto | 安全命令自动执行 | 中等 |
| Turbo | 所有命令自动执行 | ⚠️ 危险 |

---

## 📌 快速检查清单

确保你已完成以下设置：

- [ ] 确认已登录 Google 账户并连接到 Gemini Cloud
- [ ] 开发模式设置为 **Agent-assisted**
- [ ] 默认模型设置为 **gemini-2.5-flash**
- [ ] 终端策略设置为 **Ask**
- [ ] 创建了 `~/.gemini/GEMINI.md` 全局规则
- [ ] 创建了 `~/.gemini/settings.json` 配置文件
- [ ] 项目中添加了 `.agent/rules/` 规则文件

---

## 📚 相关资源

- [Antigravity 官方文档](https://antigravity.google)
- [GitHub 社区模板](https://github.com/topics/antigravity)
- [MCP Store 服务列表](https://antigravity.google/mcp-store)

---

> 💡 **提示**：这份指南会帮助你作为新手高效使用 Antigravity，同时控制 $20/月的用量消耗。建议定期查看 `/usage` 了解使用情况！
