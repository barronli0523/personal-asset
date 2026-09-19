# 目录与字段规范

## 目录

| 路径 | 内容 | 边界 |
|---|---|---|
| 00_Inbox | 人的随手记录 | AI 只读 |
| 01_Sources | 原文或来源指针 | 只新增，不覆盖 |
| 10_Work/Projects | 完整项目复盘 | 指向独立产出的资产 |
| 10_Work/Lessons | 一个具体问题、原因与解法 | 保留失败与适用环境 |
| 10_Work/Playbooks | 下次可照做的步骤 | 必须有例外与验收 |
| 10_Work/Agents、Skills | 可复用能力的说明和使用条件 | 文档不等于已安装能力 |
| 10_Work/Data-Governance | 数据清洗、结构化与脱敏做法 | 保留来源与口径 |
| 10_Work/Decisions | 有代价的选择与舍弃原因 | 不删除历史证据 |
| 20_Thinking | Books、Ideas、Reflections、Mental-Models、Insights | 仅明确授权形成个人观点 |
| 30_System | 规则、索引、模板、日志与待决事项 | 规则与模板修改先授权 |
| 90_Archive | 已失效但保留追溯的内容 | 迁移前取得授权 |
| examples | 虚构的完整教学链路 | 不混入真实项目统计或证据 |

新文件先查重。使用 templates 中的对应类型，不为一次性内容增加目录或字段。

## 文件命名

工作资产和来源：`YYYY-MM-DD-简短描述.md`；认知资产：`简短标题.md`；规则使用既有固定名。全库文件名唯一，不用 final、v2、副本。虚构示例使用 `example-` 前缀，不能被误认作历史事件。

## 文件头

资产必填 `type`、`title`、`status`、`created`、`updated`、`owner`、`tags`、`source`。特例：source-pointer 本身就是来源，以 external_path、captured_at、immutable 记录追溯信息；capture 使用捕获模板；review-item 用背景证据与 affected_files；规则和索引允许纯 Markdown。

- `status`：draft / verified / stale / archived。AI 起草默认 draft；只有使用者明确确认结论正确且证据齐全后才 verified。批准候选的去向或执行动作不等于确认其全部声明为事实；状态不是软件上线等级。
- `type`：project / agent / skill / data-governance / lesson / decision / playbook / book / idea / reflection / mental-model / insight / source / source-pointer / capture / side-quest / review-item / doc / index / log。
- 日期用 YYYY-MM-DD；未知值写 unknown 或无法确认，合法空列表用 `[]`。工作资产实例的 source 必须指向可核对证据，不能用空列表或 unknown 代替来源；找不到来源时先写 review，不生成无证据资产。模板占位符必须在入库前替换。
- YAML 是文件开头两条 `---` 之间的属性。占位符与双链值必须加引号；标签仅选 taxonomy 中实际词条，不能保留模板标签占位符。
- 其他类型专属字段以模板为准。`source` 指证据，`derived_from` 指提炼来源，`related_project` 指所属项目，`reusable_assets` 列项目产出，`applies` 指适用场景。字段不是完成证明。

## 复盘候选接收

复用 `30_System/review/` 和 `Review-Item.md`，不新增接收目录或模板。一候选一文件，先查全库 index、已有 review、来源和正式资产。优先使用上游候选编号定位；无编号时用来源项目、证据锚点和候选问题/结论联合查重。同一来源可支持不同候选，不能仅凭路径相同判重。

当 `category: asset-intake` 时，在普通 review 字段上增加：

| 字段 | 要求 |
|---|---|
| `candidate_id` | 稳定且全库唯一；首次分配后不改 |
| `candidate_version` | 正整数，从 1 开始；声明、证据、范围或目的地实质变化时递增 |
| `origin` | 来源项目名称；项目地址、报告定位、上游编号放正文 |
| `source` | 已核实 Sources / Source Pointer 链接列表；缺证据可为 `[]`，同时进入 needs-evidence |
| `privacy` | private / restricted / public / unknown；unknown 按受限处理，public 不是发布授权 |
| `review_state` | pending / needs-evidence / deferred / approved / rejected / duplicate / applied |
| `resolved` | applied / rejected / duplicate 为 true；其余 false；与文件是否移动无关 |

正文必须记录：解决的问题、复用场景与下一次具体动作、适用范围、例外与失效条件、逐条声明类型与核验结果、隐私检查范围、相似候选或资产、查重方法、推荐目的地与理由、需要人工决定的事项。

声明类型只有五类：

- **已验证事实**：有原始证据定位、核验动作和时间。
- **推断**：列出事实前提、推理过程和未验证部分；无依据不能靠标注“推断”入库。
- **估算**：允许明确标注的估算；记录输入来源、公式或方法、假设、误差或范围，无法量化时说明原因。
- **个人判断**：标明判断者和来源；AI 建议不能冒充使用者观点。
- **未知**：证据不足写 unknown / 无法确认，不补造数字或原因。

状态约束：pending 等待决定；needs-evidence 先补证；deferred 记录再议条件；approved 表示当前版本的具体目的地和动作已获批准但尚未完全落盘；rejected / duplicate 原地结案；applied 表示授权动作、来源链接、索引和日志已经完成并验证。`applied` 不自动改变正式资产的 `status: draft`。失败时保留 approved，记录已完成动作、阻塞和重试检查，不重复创建同一产物。

`20_Thinking` 仍需使用者明确确认具体观点。拒绝、暂缓和重复不自动创建 Decision，也不授权删除、合并或移动已有材料。

## 正文

按模板保留事实、判断、失败尝试、复用步骤、适用范围、未知项与变更记录。事实与建议分开。单篇以便于查用为准，目标400–1200中文字；内容过长先提议拆分并保持来源链，不自行合并或删除。

## 保存与公开

个人资料应只写在本地工作副本。仓库 .gitignore 默认排除个人内容，只保留目录占位；examples 是唯一随公开包提供的示范材料。忽略规则不能阻止强制添加，也不能移除已跟踪文件；每次公开前仍检查实际提交内容。index.md、README和规则不在忽略范围；更新后的索引可能含个人资产名称，公开模板与个人工作副本必须分开。

来源包含秘密或个人信息时不复制秘密原文；记录可核对的非敏感证据或访问受限的指针。无权再分发的第三方文件不进入公开包。

相关：[[taxonomy]] · [[linking-rules]] · [[index]]
