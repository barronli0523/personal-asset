---
type: review-item
title: "{{需要使用者决定什么}}"
status: draft
created: "{{YYYY-MM-DD}}"
updated: "{{YYYY-MM-DD}}"
owner: "{{owner}}"
tags:
  - type/review-item
  - state/needs-review
severity: "{{blocker | major | minor}}"
category: "{{taxonomy | schema | promotion | conflict | missing-evidence | duplicate | deletion | scope | asset-intake}}"
affected_files: []
blocking: "{{true | false}}"
resolved: false
---

## 复盘候选专用（普通 review 不填写）

当 `category: asset-intake` 时，把以下字段合入顶部 frontmatter，并将 `blocking` 设为布尔值 `false`；不要保留占位符：

```yaml
candidate_id: "{{稳定编号}}"
candidate_version: 1
origin: "{{来源项目名称}}"
source: []
privacy: private
review_state: pending
```

若缺少可引用证据，允许 `source: []`，同时改为 `review_state: needs-evidence` 和 `state/needs-evidence`；证据存在时填写已核实的 Sources 双链。

- 来源项目地址、报告定位、上游候选编号：{{缺项写 unknown}}
- 解决的问题与实际处理：{{问题、方法、观察结果}}
- 复用场景与具体行动：{{未来什么时候先做什么或避免什么}}
- 适用范围：{{环境、版本、前置条件}}
- 例外与失效条件：{{不适用场景、复验触发条件}}
- 隐私检查：{{凭据 / 个人信息 / 第三方商业信息分别检查的范围、方法和未检查项；不复制敏感原文}}

### 声明与证据

| 声明 | 类型 | 原始证据定位 / 作者 | 核验动作与时间 | 依据与未确认部分 |
|---|---|---|---|---|
| {{}} | {{已验证事实 / 推断 / 估算 / 个人判断 / 未知}} | {{}} | {{未核验写无法确认}} | {{推断写前提；估算写输入来源、方法、假设和误差或范围}} |

### 查重与推荐目的地

- 查重记录：{{检查过的 index / review / 来源 / 资产与查询方式}}
- 相似候选或资产：{{存在则链接并说明差异；没有则写未发现}}
- 推荐目的地及理由：{{项目专用 / 模板脚本Skill / Personal Asset / 全局规则候选 / 不沉淀}}
- 拟用模板、目标路径、动作：{{Work/Thinking 须具体}}
- 所需人工决定：{{收录当前版本 / 补证 / 暂缓 / 拒绝 / 确认重复}}

接收候选不等于批准候选；批准候选不等于 verified。实质变化后递增 `candidate_version` 并重新审核。

## 问题

{{}}

## 事实与未知

{{}}

## 选项

| 方案 | 好处 | 代价 |
|---|---|---|
| A | {{}} | {{}} |
| B | {{}} | {{}} |

## 推荐与例外

{{}}

## Resolution

{{记录决定人、时间、候选版本、批准的目的地/模板/路径/动作、验证结果和实际产物；移动到 resolved 需单独授权。}}

## changelog

| 日期 | 改动 | 操作者 |
|---|---|---|
| {{YYYY-MM-DD}} | 初稿 | {{owner}} |
