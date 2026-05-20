# Terminology

Use this reference when a workspace maintains an official glossary, terminology table, term index, or terminology block in Linear issues.

## Official Glossary

Treat the official glossary as final state, not a collaboration space.

- Add only confirmed terms.
- Do not add draft terms, review status, unresolved questions, or discussion history.
- Use stable term IDs, such as `TERM-story`, for issue references and audits.
- Keep term IDs stable after creation. Rename display terms through the term block, not by changing IDs.
- Do not use free-text matching as the source of truth for term references.

The glossary should define product concepts. It should not duplicate code ownership.

- Keep product term, term ID, alias, definition, related Linear issues, and concise notes in the glossary.
- Do not keep canonical code name, current code name, migration status, or implementation mapping in the glossary.
- Let the code repository or engineering artifacts maintain code-name mapping and migration details.

## Glossary Shape

Prefer an index plus term blocks.

Index columns:

- Term ID, translated to the Linear language when appropriate
- Product term
- Definition summary
- Related issues

Term block shape:

```md
## TERM-example

产品术语：Example

别名：

* 暂无。

定义：

...

相关任务：

* `TEAM-123`

备注：

* ...
```

Use the target Linear language for labels and explanatory prose. Keep terms, term IDs, issue IDs, and necessary quoted identifiers in their original form.

When referencing confirmed terms from an issue, link each term ID to the corresponding term block in the official glossary. Keep unconfirmed terms as plain text so they are not mistaken for accepted glossary entries.

## Issue Terminology Block

When a workspace requires terminology tracking, every applicable issue should include a terminology block. Use the target Linear language for headings and labels.

For confirmed terms:

```md
## 术语

术语表：<正式术语表链接>

涉及术语：

* [`TERM-story`](<正式术语表链接#term-story>)
* [`TERM-scene`](<正式术语表链接#term-scene>)

术语影响：

* 使用已确认术语。
* 不引入新的术语或别名。
```

For unconfirmed new terms:

```md
## 术语

术语表：<正式术语表链接>

涉及术语：

* [`TERM-story`](<正式术语表链接#term-story>)
* 待确认：`TERM-story-guide`

术语影响：

* 使用已确认术语 `TERM-story`。
* 提出新术语 `TERM-story-guide`，但该术语尚未进入正式术语表。
* 确认前，不把 `TERM-story-guide` 写入正式术语表索引或术语块。

## 待解决问题

* 是否批准 `TERM-story-guide` 作为正式术语？
```

Do not use English workflow labels such as `Proposed` when the target Linear language is Chinese. Use the workspace language, for example `待确认`.

## When To Update The Glossary

Update the official glossary only after the product decision is settled.

Update it when a confirmed decision changes:

- product term
- term ID
- alias
- definition
- term relationship to related issues

Do not update the glossary when:

- a new term is only proposed
- the issue still has unresolved product questions about the term
- the change is only a code rename or implementation mapping
- the term belongs only to one implementation detail and has no product meaning

When a term is not confirmed, keep it in the issue's terminology block and unresolved questions. In Chinese workspaces, prefer the workspace's own heading, such as `待解决问题` or `待确认问题`.

## Automation Guidance

If automating glossary maintenance:

- Parse explicit `TERM-*` IDs from issue terminology blocks.
- Do not infer references by searching product words such as `Story` or `Scene`.
- Update only generated backlinks or related-issue sections.
- Do not rewrite human-maintained definitions, aliases, or notes.
