# taxonomy

## 为什么要受控词表

自由标签的必然结局：`#codex`、`#Codex`、`#CODEX`、`#codex-cli`、`#openai-codex` 五个标签指同一件事，检索全部失效。

规则很简单：

> **标签必须来自本文件。需要新标签 → 先登记到本文件，再使用。**

AI 不得自行创造标签。发现使用了未登记标签，`lint` 会报错。

---

## 标签语法约定

- 全部**小写英文**，词内用 `-` 连接
- 最多两级，用 `/` 分隔：`domain/ai-agent`
- 中文不进标签（中文进 `title` 和正文）
- 一个文件建议 **3–6 个标签**：1 个 `type/` + 1–2 个 `domain/` + 1–2 个 `tech/` + 可选 `status/` 或 `biz/`
- 标签表达「这是什么类别」，不表达「这有多重要」（重要性用 frontmatter 字段）

---

## 1. `type/` —— 条目类型（每篇必选且只选一个）

| 标签 | 用于 |
|---|---|
| `#type/project` | 项目复盘 |
| `#type/agent` | Agent 资产 |
| `#type/skill` | Skill 资产 |
| `#type/data-governance` | 数据治理资产 |
| `#type/lesson` | 踩坑与经验 |
| `#type/decision` | 关键决策 |
| `#type/playbook` | 可复用标准做法 |
| `#type/side-quest` | 主线外的顺手问题 |
| `#type/book` | 书与长文 |
| `#type/idea` | 想法与构想 |
| `#type/reflection` | 阶段性复盘 |
| `#type/mental-model` | 思维模型 |
| `#type/insight` | 洞见 |
| `#type/source` | 原始证据 |
| `#type/capture` | Inbox 速记 |
| `#type/review-item` | 待决条目 |

---

## 2. `domain/` —— 知识领域

### AI 工程

| 标签 | 覆盖范围 |
|---|---|
| `#domain/ai-agent` | Agent 架构、编排、多智能体 |
| `#domain/llm-ops` | 模型调用、路由、成本、限流、降级 |
| `#domain/prompt` | 提示词设计与调优 |
| `#domain/context` | 上下文工程、记忆、压缩 |
| `#domain/mcp` | MCP 协议、Server、工具接入 |
| `#domain/skill` | Skill 编写、安装、管理 |
| `#domain/eval` | 效果评估、测试、质量分层 |
| `#domain/rag` | 检索增强（含本库未来的检索机制） |

### 软件工程

| 标签 | 覆盖范围 |
|---|---|
| `#domain/frontend` | Web 前端 |
| `#domain/backend` | 服务端、API |
| `#domain/git` | 分支、worktree、rebase、冲突 |
| `#domain/env` | 环境配置、依赖、运行时 |
| `#domain/network` | 代理、端口、DNS、连通性 |
| `#domain/security` | 密钥、权限、脱敏、注入 |
| `#domain/perf` | 性能、耗时、资源 |
| `#domain/debug` | 排错方法与工具 |

### 数据

| 标签 | 覆盖范围 |
|---|---|
| `#domain/data-governance` | 数据治理总体 |
| `#domain/data-cleaning` | 清洗 |
| `#domain/data-anonymization` | 脱敏 |
| `#domain/data-structuring` | 非结构化转结构化 |
| `#domain/spreadsheet` | Excel / 表格处理 |

### 商业

| 标签 | 覆盖范围 |
|---|---|
| `#domain/bidding` | 标书、招投标 |
| `#domain/brand` | 品牌战略 |
| `#domain/marketing` | 市场营销、增长 |
| `#domain/pricing` | 定价与打包 |
| `#domain/product` | 产品设计与需求 |
| `#domain/strategy` | 商业战略 |
| `#domain/saas` | SaaS 业务模型 |

### 认知与方法

| 标签 | 覆盖范围 |
|---|---|
| `#domain/thinking` | 思维方法总类 |
| `#domain/decision-making` | 决策方法 |
| `#domain/learning` | 学习方法 |
| `#domain/writing` | 写作与表达 |
| `#domain/knowledge-mgmt` | 知识管理本身 |

---

## 3. `tech/` —— 具体技术 / 工具

| 标签 | 说明 |
|---|---|
| `#tech/codex` | OpenAI Codex（CLI / IDE / App） |
| `#tech/claude-code` | Claude Code |
| `#tech/chatgpt` | ChatGPT |
| `#tech/obsidian` | Obsidian |
| `#tech/dify` | Dify |
| `#tech/n8n` | n8n |
| `#tech/mcp` | MCP 实现相关 |
| `#tech/omniroute` | OmniRoute 模型路由 |
| `#tech/dashscope` | 阿里百炼 / DashScope 模型服务（含 anthropic 兼容网关）。与 `omniroute` 的区别：本标签是**供应商**，omniroute 是**路由层** |
| `#tech/python` | Python |
| `#tech/node` | Node.js |
| `#tech/typescript` | TypeScript |
| `#tech/javascript` | JavaScript |
| `#tech/react` | React |
| `#tech/vue` | Vue |
| `#tech/uniapp` | uni-app / HBuilderX |
| `#tech/git` | Git |
| `#tech/github` | GitHub / gh CLI |
| `#tech/docker` | Docker |
| `#tech/vscode` | VS Code |
| `#tech/macos` | macOS 系统层 |
| `#tech/clashx` | ClashX / 代理客户端 |
| `#tech/lark` | 飞书 / Lark |
| `#tech/wechat` | 微信生态（小程序、公众号） |
| `#tech/excel` | Excel |
| `#tech/yt-dlp` | yt-dlp 视频/字幕抓取（YouTube / B站 / 抖音等平台内容入库） |
| `#tech/remotion` | Remotion 视频 |
| `#tech/threejs` | Three.js |

**新工具出现时**：先在本表登记，再使用。登记格式照抄上表。

---

## 4. `biz/` —— 业务 / 客户上下文

用于区分「这是给哪个业务场景做的」，方便按业务线复用。

| 标签 | 说明 |
|---|---|
| `#biz/bid-agent` | 标书自动生成 |
| `#biz/store-marketing` | 门店营销 |
| `#biz/medical-data` | 医疗数据 |
| `#biz/ai-saas` | AI SaaS 产品 |
| `#biz/enterprise-ai` | 企业 AI 落地 |
| `#biz/personal` | 个人项目，非商业 |

**客户名不进标签**（隐私 + 标签爆炸）。具体客户写在正文或 frontmatter 的 `related_project`。

---

## 5. `state/` —— 处理状态标签

| 标签 | 含义 |
|---|---|
| `#state/needs-review` | 需要 使用者 确认 |
| `#state/needs-evidence` | 缺证据，结论待补 |
| `#state/needs-update` | 内容过期，需重新验证 |
| `#state/wip` | 进行中 |
| `#state/blocked` | 被阻塞，写明阻塞原因 |
| `#state/reusable` | 已验证可直接复用 ← **检索时优先看这个** |

`state/` 标签与 frontmatter 的 `status` 字段**不重复**：
- `status` 是条目生命周期（draft / verified / stale / archived）
- `state/` 是当前待办动作（要不要人处理）

条目处理完毕后，`state/` 标签应被移除。

---

## 6. `source-kind/` —— 证据来源类型

| 标签 | 说明 |
|---|---|
| `#source-kind/repo` | 代码仓库 |
| `#source-kind/codex-thread` | Codex 会话 |
| `#source-kind/chatgpt-thread` | ChatGPT 会话 |
| `#source-kind/web` | 网页 |
| `#source-kind/book` | 书籍 |
| `#source-kind/doc` | 文档（合同、标书、PRD 等） |
| `#source-kind/image` | 截图 |
| `#source-kind/log` | 运行日志 |
| `#source-kind/dataset` | 数据集 |
| `#source-kind/conversation` | 线下对话、会议 |

---

新增标签前先查同义词并取得维护者授权。模板中的 domain/{{领域}} 等是占位符，实例中必须替换。草稿不使用 state/reusable。

相关：[[schema]] · [[linking-rules]]
