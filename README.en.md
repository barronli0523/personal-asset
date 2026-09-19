# Personal Asset · Reusable Project Knowledge

[中文](README.md) | **English**

Turn experience from past projects into guidance you can use in the next one.

Personal Asset is an **Obsidian vault template and an AI collaboration workflow**. It helps you identify useful practices and lessons in project records, check their evidence, and—with your approval—organize them into knowledge you can find and reuse.

> **You decide what is worth keeping. AI handles deduplication, evidence checks, structure, and maintenance.**

Start with Markdown files and ordinary folders. Obsidian provides properties, internal links, and backlinks; no community plugins are required. Other Markdown editors can read the files too. This is a documented workflow, not a program that automatically scans projects, approves candidates, or creates assets.

## Why this library exists

After a project ends, the most useful knowledge often goes beyond a list of features:

- Which approach worked, and under what conditions?
- Which attempts failed, and how could the problem be detected earlier?
- Which project-specific problem can become a useful check in another project?

**A retrospective is the starting point. Changing how you build the next project is the goal.** The kit is intended for independent developers, AI practitioners, and people using AI to help build software.

For example, the included **fictional teaching example** starts with a missing price being treated as zero and incorrectly passing a budget filter. It develops a reusable approach: define the inputs needed for a decision, distinguish missing data from a valid zero, and check boundary cases. This can inform other numeric filtering tasks. The example is not evidence of a real incident, executed test, or measured benefit.

[Source](examples/example-source.md) → [Project retrospective](examples/example-project.md) → [Lesson](examples/example-lesson.md) → [Reusable checklist](examples/example-playbook.md)

## Quick start

### 1. Get the template

With Git installed, run:

```sh
git clone https://github.com/barronli0523/personal-asset.git personal-asset-template
```

If you already use GitHub CLI, this is an alternative—choose either command:

```sh
gh repo clone barronli0523/personal-asset personal-asset-template
```

These commands download the template files. They do not install Obsidian or start an AI assistant.

### 2. Create your working copy

Keep `personal-asset-template` as a clean template and store your own knowledge in a separate directory. On macOS or Linux with Git and tar installed, run this from the directory containing the clone:

```sh
mkdir my-assets && (git -C personal-asset-template archive HEAD | tar -x -C my-assets)
```

`my-assets` must not already exist. This exports the committed template files without the `.git` history directory.

On Windows, create `my-assets` and copy the template files and folders, including the hidden `.gitignore` file but excluding `.git`. You can also download a ZIP from GitHub and extract it into a separate directory. These commands and copying steps have not been validated on every operating system.

### 3. Open it and try one project

In Obsidian, choose **Open folder as vault** and select `my-assets`. A vault is simply a folder of notes; it does not require Git.

Read the [AI instructions](AGENTS.md) and [directory and field specification](30_System/schema.md), then start with a small project. When filling in templates, replace `owner` with your name, replace placeholders, and choose [registered tags](30_System/taxonomy.md). Keep items with insufficient evidence in review instead of rushing to create assets.

## How to review a project

**Source material → Extract lessons → Check evidence and duplicates → Review candidates → Your approval → Assets → Reuse**

1. **Preserve evidence.** Reuse an existing source, or add original material or a source pointer to `01_Sources/`. Do not overwrite existing sources or update them to add backlinks.
2. **Propose candidates.** Extract successful approaches, failed attempts, decision rationale, and environment issues. State when each lesson could be reused, its conditions and exceptions, and its evidence.
3. **Review before accepting.** After checking for duplicates, create one record per candidate in `30_System/review/`. You decide whether to accept it, request evidence, defer it, reject it, or confirm a duplicate.
4. **Create assets after approval.** Approve the candidate version, template, destination path, and action before it enters `10_Work/`. Personal viewpoints in `20_Thinking/` also need your explicit confirmation of the viewpoint. Then update the index, record the work in the log, and check links.

Candidate lists from [project-review-skill](https://github.com/barronli0523/project-review-skill) or other retrospective workflows use the same intake process. That Skill is not required to use this library. See the [intake specification](30_System/schema.md#复盘候选接收) and [review template](30_System/templates/Review-Item.md) for fields and states.

**Approval to keep an item is not proof that it is correct.** New assets default to `draft`. Inferences and estimates retain their labels and supporting basis; missing information stays `unknown`. Use `verified` only when you have confirmed the conclusion and its evidence is complete. Rejecting a candidate does not authorize deleting its source material.

### A prompt you can copy

Run this in your personal working copy with an AI assistant that can read local files. Otherwise, provide only material you have screened for sharing.

```text
Read this vault's AGENTS.md and the rules it references first.
Read only this project's material: [project directory or retrospective report path].
Do not run or modify the source project.
Extract successful practices, failed attempts, decision rationale, and environment issues.
Check evidence and duplicates, then create one review record per reusable candidate
using the existing Review-Item template. Include sources, reuse scenarios, scope,
exceptions, claim types, privacy, and a recommended destination.
Update the candidate index and log, list the decisions I need to make, then stop.
Do not write to Work or Thinking until I approve the specific candidate version,
destination, and action.
```

## How to use it in your next project

Search the [index](30_System/index.md) for the current problem, read only relevant assets, and translate them into development actions or acceptance checks. Record outcomes and exceptions after use so the knowledge can improve.

```text
Search the local asset index for the current requirements and read only relevant items.
Explain why each lesson applies and which development or acceptance actions follow.
Do not force an irrelevant lesson into the project.
Read assets first; follow source links only when more evidence is needed.
Do not load the entire vault or invent extra features, scoring weights, or architecture.
Respect the target project's permissions. Report results, steps not performed, and
suggested revisions; update records only within the authorized scope.
```

Success means finding relevant knowledge and using it correctly—not accumulating more notes. Reading material adds to an AI assistant's context; costs depend on how you use it. This project does not promise unmeasured net savings.

## Directory guide

| Directory | Contents | Main boundary |
|---|---|---|
| `00_Inbox/` | Your quick notes | AI does not rewrite your words |
| `01_Sources/` | Original evidence or external source pointers | Add only; existing sources are immutable |
| `10_Work/` | Retrospectives, lessons, decisions, playbooks, and capability notes | Retrospective candidates require approval first |
| `20_Thinking/` | Personal viewpoints, mental models, and insights | Explicit confirmation from you |
| `30_System/` | Rules, index, 16 templates, reviews, and logs | Rule and template changes require approval; logs are append-only |
| `90_Archive/` | Outdated material retained for traceability | Moving items requires authorization |
| `examples/` | Four fictional teaching notes | Not evidence from real projects |

Useful references: [Purpose](30_System/purpose.md) · [Field specification](30_System/schema.md) · [Tag vocabulary](30_System/taxonomy.md) · [Linking rules](30_System/linking-rules.md) · [Templates](30_System/templates/)

## Related project

[Project Review Skill](https://github.com/barronli0523/project-review-skill) supports project retrospectives, evidence review, and the extraction of reusable lesson candidates. Personal Asset receives those candidates for deduplication, evidence checks, and your approval before organizing them into assets. The two projects can be used together or independently; this link does not imply automatic synchronization or asset creation.

## Privacy, updates, and license

- **Separate the public template from your working copy.** This repository provides methods, templates, and fictional examples, not private project records. Do not replace the public repository with your personal vault.
- **Inspect the actual files before sharing.** `.gitignore` excludes personal directories, logs, reviews, and application state by default. It does not protect tracked or force-added files. READMEs, indexes, and rules can still contain personal information you add later.
- **Update templates without overwriting your notes.** Update only the clean template directory, inspect the changes, and apply relevant changes to your working copy.
- **Documentation languages:** the README is available in Chinese and English. Rules, templates, and examples are currently mostly in Chinese.
- **License status:** no `LICENSE` file has been added. Public visibility does not grant redistribution rights; licensing terms are still pending the maintainer's decision.
