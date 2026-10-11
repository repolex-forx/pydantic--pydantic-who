# Repolex Knowledge Graph of pydantic/pydantic-who

RDF knowledge graph data for [pydantic/pydantic-who](https://github.com/pydantic/pydantic-who), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download pydantic/pydantic-who
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b8e36eb767cab291d8acabbbfc2ba50f82e6c2eb
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b8e36eb767cab291d8acabbbfc2ba50f82e6c2eb
│           └── chunk-001.nq.gz
├── blob
│   ├── 0022a50cf0df175064a25a3093eef9e43a928ff7.nq.gz
│   ├── 24ee5b1be9961e38a503c8e764b7385dbb6ba124.nq.gz
│   ├── 4416e4e145978c5522007c52d53ad8cdc928a847.nq.gz
│   ├── 4a11380714834a6d112c5e0b09d7271db73a2731.nq.gz
│   ├── 505a3b1ca2716907d5b292ab90c36df043c42bb6.nq.gz
│   ├── 6456d3783b69cf2040bfd41b4342ec97708eb814.nq.gz
│   ├── cf4d0be0039cff711fa0d7c0aa5b3273f3b893e7.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f2372407a490d06ea7a13c5680569d952b2d4fd8.nq.gz
│   └── f81bdcc659fa94b200c083c74d5287dc8463ec06.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b8e36eb767cab291d8acabbbfc2ba50f82e6c2eb.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[pydantic/pydantic-who](https://github.com/pydantic/pydantic-who)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
