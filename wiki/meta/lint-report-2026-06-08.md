---
type: meta
title: "Lint Report 2026-06-08"
created: 2026-06-08
updated: 2026-06-08
tags: [meta, lint]
status: developing
---

# Lint Report: 2026-06-08

## Summary

- **Pages scanned**: 49
- **Issues found**: 79
- **Auto-fixed**: 0
- **Needs review**: 79

| Category | Count | Severity |
|----------|-------|----------|
| Dead Links | 20 | HIGH |
| Empty Sections | 28 | MEDIUM |
| Frontmatter Gaps | 11 | MEDIUM |
| Orphan Pages | 7 | MEDIUM |
| Naming Convention Violations | 9 | LOW |
| Stale Index Entries | 1 | HIGH |
| Address Validation | 1 error (infra) | HIGH |
| Semantic Tiling | skipped | — |

---

## Dead Links (20)

这些 wikilink 目标在 vault 中不存在对应页面。

### Skill/Docs 引用（可能需要跨文件链接或创建 stub）

| Dead Target | Referenced From | Note |
|-------------|-----------------|------|
| `[[wiki-cli]]` | `wiki/references/transport-fallback.md` | 指向 skill，非 wiki page。建议：链接到 `docs/` 或创建 stub |
| `[[wiki-fold]]` | `wiki/folds/fold-k3-from-2026-04-23-to-2026-04-24-n8.md` | 同上 |
| `[[wiki-mode]]` | `wiki/references/methodology-modes.md` | 同上 |
| `[[mcp-setup]]` | `wiki/references/transport-fallback.md` | 实际路径可能在 `skills/wiki/references/mcp-setup.md` |
| `[[methodology-modes-guide]]` | `wiki/references/methodology-modes.md` | 实际路径在 `docs/methodology-modes-guide.md` |
| `[[dashboard.base]]` | `wiki/meta/dashboard.md` | 可能是 Obsidian Bases 文件 `wiki/meta/dashboard.base` |

### 文件名拼写/格式问题

| Dead Target | Referenced From | Note |
|-------------|-----------------|------|
| `[[How does the LLM Wiki pattern work?]]` | `wiki/concepts/Persistent Wiki Artifact.md`, `wiki/concepts/Query-Time Retrieval.md`, `wiki/concepts/Source-First Synthesis.md`, `wiki/hot.md`, `wiki/log.md` | **带问号**。实际文件名为 `How does the LLM Wiki pattern work`（无 `?`）。macOS 不允许文件名含 `?`。另有 2 处正确引用（无问号）|
| `[[Wiki Map]]` | `wiki/concepts/_index.md`, `wiki/getting-started.md`, `wiki/hot.md`, `wiki/index.md` (6次) | 引用的页面不存在。可能指 `wiki/meta/overview.canvas` 或尚未创建的概念页 |

### 概念页/Entity 页缺失

| Dead Target | Referenced From | Note |
|-------------|-----------------|------|
| `[[E-commerce SEO]]` | `wiki/entities/Claude SEO.md`, `wiki/meta/2026-04-14-claude-seo-v190-session.md` | 被多次引用但无独立页面。建议创建 entity 页或 concept 页 |
| `[[Claude Obsidian]]` | `wiki/meta/2026-04-10-backlink-empire-session.md` | 可能指这个 vault 自身或 `claude-obsidian-ecosystem` |
| `[[Claude Canvas]]` | `wiki/meta/2026-04-10-backlink-empire-session.md` | 无对应页面 |
| `[[Karpathy LLM Wiki Pattern]]` | `wiki/meta/2026-04-10-backlink-empire-session.md` | 可能指 `LLM Wiki Pattern` + `Andrej Karpathy` 的组合引用 |
| `[[Rankenstein]]` | `wiki/meta/2026-04-10-backlink-empire-session.md` | 无对应页面 |
| `[[claude-obsidian-presentation]]` | `wiki/overview.md` | 无对应页面 |
| `[[AI Marketing Hub Cover Images Canvas]]` | `wiki/overview.md` | 无对应页面 |

### 测试/Stale 数据

| Dead Target | Referenced From | Note |
|-------------|-----------------|------|
| `[[Foo]]` | `wiki/concepts/DragonScale Memory.md` | 测试数据，应清理 |
| `[[notes/Foo]]` | `wiki/concepts/DragonScale Memory.md`, `wiki/log.md` | 同上 |
| `[[Three laws of motion]]` | `wiki/concepts/Persistent Wiki Artifact.md` | 示例数据，应考虑移除或创建实际 page |
| `[[wikilinks]]` | `wiki/concepts/cherry-picks.md` | 可能指概念本身而非具体页面 |
| `[[fold-template]]` | `wiki/folds/fold-k3-from-2026-04-23-to-2026-04-24-n8.md` | 可能是 `_templates/` 下的模板文件 |

---

## Orphan Pages (7)

没有任何 inbound wikilink 的页面。它们存在但无法通过链接网络被发现。

| Page | Path | 建议 |
|------|------|------|
| `[[methodology-modes]]` | `wiki/references/methodology-modes.md` | 从 `index.md` 或 `getting-started.md` 添加链接 |
| `[[transport-fallback]]` | `wiki/references/transport-fallback.md` | 从 `index.md` 或相关 skill 文档链接 |
| `[[2026-04-10-backlink-empire-session]]` | `wiki/meta/2026-04-10-backlink-empire-session.md` | 从 `log.md` 链接（session 存档） |
| `[[tiling-report-2026-04-24]]` | `wiki/meta/tiling-report-2026-04-24.md` | 从 `DragonScale Memory` 或 `log.md` 链接 |
| `[[retrieval-benchmark-v1.7]]` | `wiki/meta/retrieval-benchmark-v1.7.md` | 从 `log.md` 或 `index.md` 链接 |
| `[[fold-k3-from-2026-04-23-to-2026-04-24-n8]]` | `wiki/folds/fold-k3-from-2026-04-23-to-2026-04-24-n8.md` | 从 `log.md` 链接（fold 页面） |
| `[[_index]]` (entities/) | `wiki/entities/_index.md` | 从 `index.md` 已有引用（`entities/_index` 路径形式），但 base name 匹配为 orphan。可能是 scripting 问题 — 需人工确认 |

---

## Frontmatter Gaps (11)

### 完全缺失 Frontmatter（BLOCKER）

- **`wiki/meta/tiling-report-2026-04-24.md`**: 完全没有 YAML frontmatter。必须添加至少 `type`、`status`、`tags`、`title`。

### `sources: None` — Python None 而非 YAML null（MEDIUM）

以下页面使用了 Python 的 `None` 而非 YAML 的 `null` 或空列表 `[]`。Obsidian Dataview 查询可能异常：

- `wiki/overview.md`
- `wiki/concepts/LLM Wiki Pattern.md`
- `wiki/concepts/Compounding Knowledge.md`
- `wiki/concepts/Hot Cache.md`
- `wiki/concepts/DragonScale Memory.md`
- `wiki/entities/Andrej Karpathy.md`

修复：将 `sources: None` 改为 `sources: null` 或 `sources: []`。

### 缺少必填字段

| Page | Type | Missing |
|------|------|---------|
| `wiki/references/transport-fallback.md` | reference | `tags` |
| `wiki/meta/retrieval-benchmark-v1.7.md` | meta | `tags` |

### 缺少 `created` 字段（非 meta/fold 类型）

- `wiki/references/methodology-modes.md` (type: reference)
- `wiki/references/transport-fallback.md` (type: reference)

### 缺少 `updated` 字段

- `wiki/references/methodology-modes.md`

---

## Empty Sections (28)

以下 heading 下方无内容。可能是占位符遗留或内容被误删。

### HIGH（关键页面内容缺失）

| Page | Section |
|------|---------|
| `wiki/concepts/Hot Cache.md` | `# Recent Context` — 该页面为 hot cache 机制的核心概念页，最近上下文为空 |
| `wiki/concepts/cherry-picks.md` | 4 个 Tier 全部为空 — 整个 backlog 内容缺失 |

### MEDIUM（session/entity 页面）

| Page | Section |
|------|---------|
| `wiki/getting-started.md` | `## Three-Step Quick Start` |
| `wiki/comparisons/Wiki vs RAG.md` | `# Wiki vs RAG` (正文标题下无内容) |
| `wiki/meta/2026-04-14-claude-seo-v190-session.md` | `## What Was Done` |
| `wiki/meta/2026-04-10-backlink-empire-session.md` | `## What Was Done` |
| `wiki/meta/2026-04-24-v1.6.0-release-session.md` | `## Phase Timeline For 2026-04-24`, `## What Shipped In v1.5.0`, `## What Shipped In v1.6.0`, `## Git State And Release State` |
| `wiki/meta/2026-04-15-slides-and-release-session.md` | `## What Was Built` |
| `wiki/meta/claude-obsidian-v1.2.0-release-session.md` | `## What Was Built`, `## Legal & Security`, `## Visual / README` |
| `wiki/meta/retrieval-benchmark-v1.7.md` | `## Derived Queries (25)`, `## Hard Queries (25)` |
| `wiki/concepts/SVG Diagram Style Guide.md` | `## Color Palette`, `## Layout Primitives` |
| `wiki/entities/Claudian-YishenTu.md` | `## Key Features` |
| `wiki/entities/Ar9av-obsidian-wiki.md` | `## Key Innovations` |
| `wiki/entities/rvk7895-llm-knowledge-bases.md` | `## Key Innovations` |
| `wiki/entities/ballred-obsidian-claude-pkm.md` | `## Key Innovations` |

### LOW（模板占位符）

| Page | Section |
|------|---------|
| `wiki/concepts/_index.md` | `## Add new concepts here...` |
| `wiki/sources/_index.md` | `## Add new sources here...` |
| `wiki/entities/_index.md` | `## Add new entities here...` |

---

## Stale Index Entries

- **`[[Wiki Map]]`** in `wiki/index.md`: 被索引页引用（与其他核心导航页并列），但 **页面不存在**。需要创建 `Wiki Map.md` 或从 index 中移除链接。

---

## Naming Convention Violations (9)

skill 文档要求 filename 使用 Title Case。以下文件使用 lowercase 或 lowercase-dashed 命名：

| File | Convention | Expected |
|------|-----------|----------|
| `wiki/overview.md` | lowercase | `Overview.md` |
| `wiki/hot.md` | lowercase | `Hot.md` |
| `wiki/log.md` | lowercase | `Log.md` |
| `wiki/index.md` | lowercase | `Index.md` |
| `wiki/references/methodology-modes.md` | lowercase-dashed | `Methodology Modes.md` |
| `wiki/references/transport-fallback.md` | lowercase-dashed | `Transport Fallback.md` |
| `wiki/meta/dashboard.md` | lowercase | `Dashboard.md` |
| `wiki/meta/boundary-frontier-2026-04-24.md` | lowercase-dashed | `Boundary Frontier 2026-04-24.md` |
| `wiki/meta/retrieval-benchmark-v1.7.md` | lowercase-dashed | `Retrieval Benchmark v1.7.md` |

> **注意**: 这些文件中有多个是核心导航页面（`index.md`、`hot.md`、`log.md`、`overview.md`），改名会破坏大量 wikilink。建议先评估影响范围再决定是否修复。

---

## Stale Claims

本次 lint 未自动化检测 stale claims。以下为人工推荐检查项：

- `wiki/concepts/Hot Cache.md` 的 `updated: 2026-05-17 04:30:00` — 日期格式异常（含时间部分，非 ISO 8601），且过去近一个月未更新。需验证内容是否仍然准确。
- `wiki/concepts/DragonScale Memory.md` 的 `status: proposed` — 但 fold 记录显示 Phase 1-4 均已 ship。status 可能应更新为 `developing` 或 `evergreen`。

---

## Cross-Reference Gaps

以下为基于内容扫描的 cross-reference 候选（未自动化检测，人工推荐）：

- `wiki/meta/2026-04-10-backlink-empire-session.md` 引用了 `[[Claude Obsidian]]`、`[[Claude Canvas]]`、`[[Rankenstein]]`、`[[Karpathy LLM Wiki Pattern]]` — 全部为 dead link。这些可能是当时未完成提取的 entity/concept，应在 `entities/` 或 `concepts/` 下创建对应页面。
- `wiki/entities/Claude SEO.md` 引用了 `[[E-commerce SEO]]` — 该概念页面未创建。

---

## Writing Style Issues

以下为人工检查发现：

- `wiki/concepts/cherry-picks.md`: 整个 Tier 1-4 部分为空 — 非 style 问题，是内容缺失。
- `wiki/overview.md`: `sources: None` — 应使用 YAML `null`。
- `wiki/meta/tiling-report-2026-04-24.md`: 无 frontmatter、无 status 指示、无 title — 无法确定该报告是否为草稿。

---

## Address Validation (DragonScale Mechanism 2)

- **Infrastructure error**: `./scripts/allocate-address.sh` 依赖 `flock` 命令，但系统未安装 `flock`。
  ```
  ./scripts/allocate-address.sh: line 36: flock: command not found
  ```
  这导致以下检查无法完成：
  - Counter peek（无法获取下一个 address 值）
  - Counter consistency（无法验证 c-000001 是否 ≤ peek）
  - 新页面 address 分配（wiki-ingest 也会受影响）

  **修复**: `brew install flock` (macOS)，或将 `allocate-address.sh` 改为使用 macOS 原生 `shlock` 或基于 `mkdir` 的 advisory lock。

- **现有 address 状态**:
  - `wiki/concepts/DragonScale Memory.md`: `address: c-000001` ✅ 格式正确
  - `.raw/.manifest.json` address_map: `wiki/concepts/DragonScale Memory.md` → `c-000001` ✅ 一致
  - Counter 文件存在 (`.vault-meta/address-counter.txt` = `3`)，但因 `flock` 缺失无法 peek

- **Legacy baseline**: `.vault-meta/legacy-pages.txt` 存在，rollout date 为 2026-04-23。

- **跳过检查**: 由于 `flock` 无法获取，未执行完整的 uniqueness / counter consistency / post-rollout enforcement 检查。修复 `flock` 后需重新验证。

---

## Semantic Tiling (DragonScale Mechanism 3)

**跳过**: `tiling-check.py --peek` 返回 exit code 10 — ollama 不可达，模型 `nomic-embed-text` 未安装。

启用步骤：
1. 安装 ollama: `brew install ollama` 或从 https://ollama.com 下载
2. 拉取模型: `ollama pull nomic-embed-text`
3. 启动 ollama 服务
4. 重新运行 lint 或 `./scripts/tiling-check.py --peek`

---

## 建议修复优先级

### BLOCKER
1. 修复 `allocate-address.sh` 的 `flock` 依赖 — 影响所有 DragonScale 操作

### HIGH
2. 修复 `[[How does the LLM Wiki pattern work?]]` → `[[How does the LLM Wiki pattern work]]`（5 处，去掉问号）
3. 创建 `Wiki Map.md` 或从 index.md 和相关页面移除引用
4. 决定 `[[E-commerce SEO]]` 是否建页（2 处引用）
5. 为 `wiki/meta/tiling-report-2026-04-24.md` 添加 frontmatter
6. 决定 `cherry-picks.md` 空 tier 的处理（填充内容或移除空 section）

### MEDIUM
7. 修复 6 处 `sources: None` → `sources: null`
8. 清理测试数据 `[[Foo]]`、`[[notes/Foo]]`、`[[Three laws of motion]]`
9. 为 7 个 orphan page 添加 inbound link
10. 填充或移除 28 个空 section
11. 补充缺失的 `tags`、`created`、`updated` 字段

### LOW
12. 评估 naming convention violations 的修复成本（9 个文件，涉及大量 wikilink 更新）
13. 更新 `DragonScale Memory.md` 的 status（`proposed` → `developing`/`evergreen`）
14. 安装 ollama + nomic-embed-text 以启用 semantic tiling

---

## 补充说明

- Skill 引用（`[[wiki-cli]]`、`[[wiki-fold]]`、`[[wiki-mode]]`）在当前 vault 结构中无对应 wiki page。这类跨 skill 的引用是设计上的正常现象，建议统一决策：是否在 `wiki/references/` 下为每个 skill 创建 stub page。
- `[[methodology-modes-guide]]` 实际存在于 `docs/methodology-modes-guide.md`（非 wiki 目录），为非标准 wikilink 路径。可创建 `wiki/references/methodology-modes-guide.md` 作为 alias。
- `[[mcp-setup]]` 实际路径可能在 `skills/wiki/references/mcp-setup.md`。

---

*Lint completed at 2026-06-08T14:10:00Z. Transport: filesystem (CLI available but not used for bulk scan). Next lint recommended after 10+ ingests or by 2026-06-22.*
