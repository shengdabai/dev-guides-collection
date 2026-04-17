# 🎯 Vibe Coding 完全指南

> **一个通过与 AI 结对编程，将想法变为现实的终极工作流程**
> 
> 本指南基于 [vibe-coding-cn](https://github.com/tukuaiai/vibe-coding-cn) 仓库整理，旨在帮助开发者高效、准确地使用 AI 进行编程开发，避免反复修改 bug。

---

## 📋 目录

1. [核心理念：道](#-核心理念道)
2. [方法论：法](#-方法论法)
3. [实践技巧：术](#-实践技巧术)
4. [工具推荐：器](#-工具推荐器)
5. [完整设置流程](#-完整设置流程)
6. [编码规范与最佳实践](#-编码规范与最佳实践)
7. [系统提示词构建原则](#-系统提示词构建原则)
8. [项目架构模板](#-项目架构模板)
9. [调试与问题解决](#-调试与问题解决)
10. [常见问题解答](#-常见问题解答)

---

## 🧭 核心理念：道

### 第一性原理

> **核心理念：规划就是一切。谨慎让 AI 自主规划，否则你的代码库会变成一团无法管理的乱麻。**

Vibe Coding 的精髓在于：**规划驱动 + 上下文固定 + AI 结对执行**，让"从想法到可维护代码"变成一条可审计的流水线。

### 核心原则

| 原则 | 说明 |
|------|------|
| **凡是 AI 能做的，就不要人工做** | 充分利用 AI 的能力，解放人力 |
| **一切问题问 AI** | AI 是你的最佳搭档，有问题直接问 |
| **目的主导** | 开发过程中的一切动作围绕"目的"展开 |
| **上下文第一** | 垃圾进，垃圾出。上下文是 Vibe Coding 的第一性要素 |
| **系统性思考** | 从实体、链接、功能/目的三个维度思考 |
| **数据与函数** | 这就是编程的一切：输入 → 处理 → 输出 |
| **先结构，后代码** | 一定要规划好框架，不然后面技术债还不完 |
| **奥卡姆剃刀** | 如无必要，勿增代码 |
| **帕累托法则** | 关注重要的那 20% |
| **逆向思考** | 先明确需求，从需求逆向构建代码 |
| **重复尝试** | 多试几次，实在不行重新开个窗口 |
| **极致专注** | 一次只做一件事，专注可以击穿代码 |

### 元方法论（Meta-Methodology）

构建一个能够自我优化的 AI 系统：

```
                    ┌─────────────────┐
         ┌────────▶│  α-提示词 (生成器) │◀────────┐
         │         └────────┬────────┘         │
         │                  │                  │
         │                  ▼                  │
         │         ┌─────────────────┐         │
    优化  │         │   目标提示词/技能  │         │ 反馈
         │         └─────────────────┘         │
         │                                     │
         │         ┌─────────────────┐         │
         └─────────│  Ω-提示词 (优化器) │─────────┘
                   └─────────────────┘
```

#### 递归生命周期：

1. **创生 (Bootstrap)**：使用 AI 生成 α-提示词 和 Ω-提示词 的初始版本
2. **自省与进化**：使用 Ω-提示词 优化 α-提示词，得到更强大的版本
3. **创造 (Generation)**：使用进化后的 α-提示词 生成所有需要的目标提示词和技能
4. **循环与飞跃**：将新生成的产物反馈给系统，启动持续进化

---

## 🧩 方法论：法

### 需求定义

- **一句话目标 + 非目标**：清晰定义你要什么，不要什么
- **正交性**：功能不要太重复（分场景考虑）
- **能抄不写**：不重复造轮子，先问 AI 有没有合适的仓库

### 开发准则

| 准则 | 详细说明 |
|------|---------|
| **一定要看官方文档** | 先把官方文档爬下来喂给 AI |
| **按职责拆模块** | 模块化，职责单一 |
| **接口先行，实现后补** | 先定义接口，再填充实现 |
| **一次只改一个模块** | 避免同时修改多处导致混乱 |
| **文档即上下文** | 文档不是事后补，而是开发的一部分 |

### Make it work → Make it right → Make it fast

```
第一阶段：先能跑起来
    ↓
第二阶段：让代码正确、优雅
    ↓
第三阶段：优化性能
```

---

## 🛠️ 实践技巧：术

### 高效沟通

1. **明确写清**：能改什么，不能改什么
2. **Debug 只给**：预期 vs 实际 + 最小复现
3. **测试可交给 AI，断言人审**
4. **代码一多就切会话**：保持上下文清洁

### 提示词优化技巧

```markdown
# 基础提示词
"帮我写一个登录功能"

# 优化后的提示词
"慢慢想，不着急，重要的是严格按我说的做，执行完美。如果我表达不够精确请提问。

需求：实现用户登录功能
技术栈：React + Express + MongoDB
要求：
1. 前端表单验证
2. 后端 JWT 认证
3. 密码加密存储
4. 错误处理完善"
```

### Claude Code 深度思考触发词

```
think < think hard < think harder < ultrathink
```

强度递增，复杂问题可以使用更强的触发词。

### 常用命令

| 命令 | 说明 |
|------|------|
| `/init` | 初始化项目规则 |
| `/new` 或 `/clear` | 新建聊天，清理上下文 |
| `/compact` | 压缩历史对话但保留 |
| `/rewind` | 回退到之前状态 |
| `shift+tab` | 切换到 Plan Mode |
| `claude --dangerously-skip-permissions` | 跳过确认弹窗（谨慎使用） |

---

## 📋 工具推荐：器

### 集成开发环境 (IDE) & 终端

| 工具 | 说明 |
|------|------|
| [Visual Studio Code](https://code.visualstudio.com/) | 功能强大的 IDE，Local History 插件便于版本管理 |
| [Cursor](https://cursor.com/) | AI 编程助手，已占领用户心智高地 |
| [Warp](https://www.warp.dev/) | 集成 AI 功能的现代化终端 |
| [Neovim](https://github.com/neovim/neovim) | 高性能的现代化 Vim 编辑器 |
| [LazyVim](https://github.com/LazyVim/LazyVim) | Neovim 配置框架，开箱即用 |
| 虚拟环境 (.venv) | 项目环境隔离，强烈推荐 |

### AI 模型 & 服务

#### 模型性能分级

| 梯队 | 模型 |
|------|------|
| **第一梯队** | codex-5.1-max-xhigh, claude-opus-4.5-xhigh, gpt-5.2-xhigh |
| **第二梯队** | claude-sonnet-4.5, kimi-k2-thinking, minimax-m2, glm-4.6, gemini-3.0-pro, gemini-2.5-pro |
| **第三梯队** | qwen3, SWE, grok4 |

> ⚠️ **建议只选择第一梯队模型处理复杂任务，以确保最佳效果与效率**

#### 推荐服务

| 服务 | 说明 |
|------|------|
| [Claude Opus 4.5](https://claude.ai/new) | 通过 Claude Code 使用，性能强大 |
| [gpt-5.1-codex](https://chatgpt.com/codex/) | 在 Codex CLI 中使用，适合大型项目 |
| [Gemini CLI](https://geminicli.com/) | 免费访问 Gemini 模型 |
| [antigravity](https://antigravity.google/) | Google 免费服务，支持多种模型 |
| [AI Studio](https://aistudio.google.com/) | Google 免费 Gemini 服务 |
| [GitHub Copilot](https://github.com/copilot) | 代码补全工具 |
| [Kimi K2](https://www.kimi.com/) | 国产 AI 模型 |
| [Qwen CLI](https://qwenlm.github.io/qwen-code-docs/zh/cli/) | 阿里模型，有免费额度 |

### 开发与辅助工具

| 工具 | 说明 |
|------|------|
| [Augment](https://app.augmentcode.com/) | 强大的上下文引擎和提示词优化 |
| [Windsurf](https://windsurf.com/) | 新用户免费额度的 AI 开发工具 |
| [Ollama](https://ollama.com/) | 本地大模型管理工具 |
| [Mermaid Chart](https://www.mermaidchart.com/) | 文本转架构图 |
| [NotebookLM](https://notebooklm.google.com/) | AI 解读资料、生成思维导图 |
| [Zread](https://zread.ai/) | GitHub 仓库快速阅读工具 |
| [tmux](https://github.com/tmux/tmux) | 终端复用工具 |
| [DBeaver](https://dbeaver.io/) | 通用数据库管理客户端 |

---

## 🚀 完整设置流程

### 第一步：创建游戏/产品设计文档

```markdown
# 示例：game-design-document.md

## 游戏概述
[游戏类型、核心玩法、目标用户]

## 核心机制
[详细描述玩法机制]

## 技术需求
[性能要求、平台支持]

## 里程碑
[开发阶段划分]
```

将你的创意交给 AI，让它生成简洁的设计文档。

> 💡 如果是应用开发，将 GDD (游戏设计文档) 换成 PRD (产品需求文档)

### 第二步：确定技术栈

让 AI 推荐最合适的技术栈，保存为 `tech-stack.md`。

**关键要求**：要求提出**最简单但最健壮**的技术栈。

### 第三步：初始化项目规则

1. 在终端打开 Claude Code 或 Codex CLI
2. 使用 `/init` 命令
3. **关键：审查生成的规则**

确保规则强调：
- ✅ 模块化（多文件）
- ❌ 禁止单体巨文件（monolith）

### 第四步：设置 "Always" 规则

将以下规则标记为 "Always"（始终应用）：

```markdown
# 重要提示：
# 写任何代码前必须完整阅读 memory-bank/@architecture.md（包含完整数据库结构）
# 写任何代码前必须完整阅读 memory-bank/@game-design-document.md
# 每完成一个重大功能或里程碑后，必须更新 memory-bank/@architecture.md
```

### 第五步：生成实施计划

提供给 AI：
- 游戏/产品设计文档
- 技术栈推荐

让它生成详细的**实施计划（implementation-plan.md）**，包含分步指令。

**计划要求**：
- ✅ 每一步要小而具体
- ✅ 每一步都必须包含验证正确性的测试
- ❌ 严禁包含代码——只写清晰、具体的指令
- 🎯 先聚焦于基础功能，完整功能后面再加

### 第六步：创建项目文件夹

创建 `memory-bank` 文件夹，放入：

```
memory-bank/
├── game-design-document.md    # 设计文档
├── tech-stack.md              # 技术栈
├── implementation-plan.md     # 实施计划
├── progress.md                # 进度记录（空文件）
└── architecture.md            # 架构说明（空文件）
```

### 第七步：澄清实施计划

提示词：

```
阅读 /memory-bank 里所有文档，implementation-plan.md 是否完全清晰？
你有哪些问题需要我澄清，让它对你来说 100% 明确？
```

回答 AI 的所有问题，让它修改完善计划。

### 第八步：分步执行

提示词：

```
阅读 /memory-bank 所有文档，然后执行实施计划的第 1 步。
我会负责跑测试。在我验证测试通过前，不要开始第 2 步。
验证通过后，打开 progress.md 记录你做了什么供后续开发者参考，
再把新的架构洞察添加到 architecture.md 中解释每个文件的作用。
```

**重要**：
- 先用 "Ask" 模式或 "Plan Mode"（`shift+tab`）确认满意后再执行
- 完成每步后提交 Git
- 新建聊天（`/new` 或 `/clear`）再继续下一步

### 第九步：迭代完善

完成基础功能后：
- 每增加一个主要功能，新建 `feature-implementation.md`
- 写短步骤 + 测试
- 继续增量式实现和测试

---

## 📝 编码规范与最佳实践

### 程序设计核心思想

1. **从问题开始，而不是从代码开始**
2. **大问题拆小问题（Divide & Conquer）**
3. **KISS 原则**：保持简单
4. **DRY 原则**：不要重复
5. **清晰的命名**：`user_age` > `a`，`get_user_profile()` > `gp()`
6. **单一职责**：一个函数只处理一个任务
7. **代码可读性优先**：代码是给人理解的
8. **合理注释**：解释"为什么"，不是"怎么做"

### 编码规范

```python
# ❌ 错误示例
def gp(a):
    return db.query(a)

# ✅ 正确示例
def get_user_profile(user_id: str) -> UserProfile:
    """从数据库获取用户资料"""
    return database.query_user(user_id)
```

### 系统行为划分

| 概念 | 说明 |
|------|------|
| **消费端** | 接收外部数据或依赖输入的地方 |
| **生产端** | 生成数据、输出结果的地方 |
| **状态（变量）** | 存储当前系统信息的变量 |
| **变换（函数）** | 处理状态、改变数据的逻辑 |

明确区分：**输入 → 处理 → 输出**

### 系统架构原则

在写代码前先明确：
- 模块划分
- 输入输出
- 数据流向
- 服务边界
- 技术栈
- 依赖关系

开发流程：**理解需求 → 保持简单 → 自动化测试 → 小步迭代**

---

## 🔧 系统提示词构建原则

### 核心身份与行为准则

1. 严格遵守项目现有约定，优先分析周围代码和配置
2. 绝不假设库或框架可用，务必先验证
3. 模仿项目代码风格、结构、框架选择
4. 未经用户确认，不执行超出范围的重大操作
5. 优先考虑技术准确性

### 沟通与互动

- 采用专业、直接、简洁的语气
- 使用 Markdown 格式化响应
- 拒绝请求时提供替代方案
- 减少输出冗余
- 沟通语言与用户保持一致

### 任务执行与工作流

```
理解 → 计划 → 执行 → 验证
```

- 复杂任务使用 TODO 列表规划
- 分解为小的、可验证的步骤
- 优先探索（Read-only），而非立即行动
- 保持 SEARCH/REPLACE 块的简洁和唯一性

### 技术与编码规范

- 避免短变量名：函数名为动词，变量名为名词
- 使用卫语句/提前返回，避免深层嵌套
- 功能拆分为小的、可重用的模块
- 绝不编辑已有的数据库迁移文件

### 安全与防护

- 执行危险命令前必须解释其影响
- 绝不提交敏感信息
- 验证和清理所有用户输入
- 实施最小权限原则

---

## 📁 项目架构模板

### Python Web/API 项目标准结构

```
项目名称/
├── README.md                 # 项目说明文档
├── LICENSE                   # 开源协议
├── requirements.txt          # 依赖管理
├── pyproject.toml           # 现代Python项目配置
├── .gitignore              
├── .env.example            
├── CLAUDE.md               # Claude 持久上下文
├── AGENTS.md               # Codex 持久上下文
│
├── docs/                   # 文档目录
│   ├── api.md
│   ├── development.md
│   └── architecture.md
│
├── scripts/                # 脚本工具
│   ├── deploy.sh
│   ├── backup.sh
│   └── init_db.sh
│
├── tests/                  # 测试代码
│   ├── __init__.py
│   ├── conftest.py
│   ├── unit/
│   └── integration/
│
├── src/                    # 源代码
│   ├── __init__.py
│   ├── main.py
│   ├── config.py
│   │
│   ├── core/              # 核心业务逻辑
│   │   ├── models/
│   │   ├── services/
│   │   └── utils/
│   │
│   ├── api/               # API接口层
│   │   ├── v1/
│   │   └── dependencies.py
│   │
│   └── data/              # 数据处理
│       ├── repository/
│       └── migrations/
│
├── logs/                   # 日志（不提交）
└── data/                   # 数据（不提交）
```

### 核心设计原则

| 原则 | 说明 |
|------|------|
| **关注点分离** | API → 服务 → 数据访问 → 数据库 |
| **可测试性** | 每个模块可独立测试，依赖可 mock |
| **可配置性** | 环境变量 > 配置文件 > 默认值 |
| **可维护性** | 代码自解释，合理命名 |
| **版本控制友好** | data/、logs/ 添加到 .gitignore |

### 新项目检查清单

- [ ] 创建 README.md
- [ ] 创建 LICENSE 文件
- [ ] 设置虚拟环境
- [ ] 创建 requirements.txt 并锁定版本
- [ ] 创建 .gitignore
- [ ] 创建 .env.example
- [ ] 设计目录结构
- [ ] 创建基础配置文件
- [ ] 设置代码格式化工具（black）
- [ ] 设置代码检查工具（flake8/ruff）
- [ ] 编写第一个测试用例
- [ ] 初始化 Git 仓库
- [ ] 创建 CHANGELOG.md

---

## 🐛 调试与问题解决

### 错误处理流程

1. **JavaScript 错误**：打开浏览器控制台（F12），复制错误给 AI
2. **视觉问题**：截图发给 AI
3. **自动化方案**：安装 [BrowserTools](https://browsertools.agentdesk.ai/installation)

### 回退策略

```bash
# Claude Code 回退
/rewind

# Git 回退
git reset --hard HEAD~1
```

### 极度卡壳时

使用以下工具将代码库合成一个文件：
- [RepoPrompt](https://repoprompt.com/)
- [uithub](https://uithub.com/)

然后丢给 AI 求救。

### 专业工具使用建议

| 任务 | 推荐工具 |
|------|---------|
| 小修改 | gpt-5.1-codex (medium) |
| 营销文案 | Opus 4.1 |
| 2D 精灵图 | ChatGPT + Nano Banana |
| 音乐生成 | Suno |
| 音效生成 | ElevenLabs |
| 视频生成 | Sora 2 |

---

## ❓ 常见问题解答

### Q: 我在做应用不是游戏，这个流程一样吗？

**A**: 基本完全一样！把 GDD（游戏设计文档）换成 PRD（产品需求文档）即可。也可以先用 v0、Lovable、Bolt.new 快速原型，再用本指南继续开发。

### Q: 一个提示词做不出复杂功能怎么办？

**A**: 复杂功能不是一个提示词能完成的，需要 ~30 个提示词 + 专门的实现文档引导。用精准指令如"在机翼上为副翼切出空间"，而不是"做一个飞机"这种模糊指令。

### Q: Claude Code 或 Codex CLI 比 Cursor 更强吗？

**A**: 这取决于个人喜好。核心观点是：
- Claude Code 能更好发挥 Claude Opus 4.5 的实力
- Codex CLI 能更好发挥 gpt-5.1-codex 的实力
- 终端版还能在任意 IDE、SSH 远程服务器等场景工作

### Q: 我不会搭建服务器怎么办？

**A**: 问你的 AI！

---

## 📚 资源链接

### 核心资源

- [在线提示词数据库](https://docs.google.com/spreadsheets/d/1ngoQOhJqdguwNAilCl1joNwTje7FWWN9WiI2bo5VhpU/edit?gid=2093180351)
- [元技能 (Meta-Skill)](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/skills/claude-skills/SKILL.md)
- [技能库 (Skills)](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/skills)
- [技能生成器](https://github.com/yusufkaraaslan/Skill_Seekers)
- [第三方系统提示词仓库](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools)

### 项目内部文档

- [coding_prompts 集合](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/prompts/coding_prompts)
- [系统提示词构建原则](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/documents/Methodology%20and%20Principles/系统提示词构建原则.md)
- [开发经验总结](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/documents/Methodology%20and%20Principles/开发经验.md)
- [通用项目架构模板](https://github.com/tukuaiai/vibe-coding-cn/blob/main/i18n/zh/documents/Templates%20and%20Resources/通用项目架构模板.md)

### 交流社区

- [Telegram 交流群](https://t.me/glue_coding)
- [Telegram 频道](https://t.me/tradecat_ai_channel)

---

## 🎯 总结：Vibe Coding 黄金法则

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  1. 规划先行：先写设计文档，再写代码                      │
│                                                         │
│  2. 上下文为王：提供完整、准确的上下文给 AI              │
│                                                         │
│  3. 小步快跑：一次只做一件事，频繁验证                   │
│                                                         │
│  4. 模块化：禁止单体巨文件，按职责拆分                   │
│                                                         │
│  5. 持续记录：更新 progress.md 和 architecture.md       │
│                                                         │
│  6. 勤提交：Git commit 是你的保险                       │
│                                                         │
│  7. 清理上下文：代码一多就切会话                         │
│                                                         │
│  8. 先问再做：用 Plan Mode 确认后再执行                 │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

> 📅 文档更新日期：2025-12-16
> 
> 📖 基于 [vibe-coding-cn](https://github.com/tukuaiai/vibe-coding-cn) 仓库整理
