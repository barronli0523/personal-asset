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

- `status`：draft / verified / stale / archived。AI 起草默认 draft，使用者确认结论后才 verified；状态不是软件上线等级。
- `type`：project / agent / skill / data-governance / lesson / decision / playbook / book / idea / reflection / mental-model / insight / source / source-pointer / capture / side-quest / review-item / doc / index / log。
- 日期用 YYYY-MM-DD；未知值写 unknown 或无法确认，合法空列表用 `[]`。
- YAML 是文件开头两条 `---` 之间的属性。占位符与双链值必须加引号；标签仅选 taxonomy 中实际词条，不能保留模板标签占位符。
- 其他类型专属字段以模板为准。`source` 指证据，`derived_from` 指提炼来源，`related_project` 指所属项目，`reusable_assets` 列项目产出，`applies` 指适用场景。字段不是完成证明。

## 正文

按模板保留事实、判断、失败尝试、复用步骤、适用范围、未知项与变更记录。事实与建议分开。单篇以便于查用为准，目标400–1200中文字；内容过长先提议拆分并保持来源链，不自行合并或删除。

## 保存与公开

个人资料应只写在本地工作副本。仓库 .gitignore 默认排除个人内容，只保留目录占位；examples 是唯一随公开包提供的示范材料。忽略规则不能阻止强制添加，也不能移除已跟踪文件；每次公开前仍检查实际提交内容。index.md、README和规则不在忽略范围；更新后的索引可能含个人资产名称，公开模板与个人工作副本必须分开。

来源包含秘密或个人信息时不复制秘密原文；记录可核对的非敏感证据或访问受限的指针。无权再分发的第三方文件不进入公开包。

相关：[[taxonomy]] · [[linking-rules]] · [[index]]
