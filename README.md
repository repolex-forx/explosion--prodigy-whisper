# Repolex Knowledge Graph of explosion/prodigy-whisper

RDF knowledge graph data for [explosion/prodigy-whisper](https://github.com/explosion/prodigy-whisper), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/prodigy-whisper
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2b6179e8c352f8af23bd5c1d33636a091e29c427
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2b6179e8c352f8af23bd5c1d33636a091e29c427
│           └── chunk-001.nq.gz
├── blob
│   ├── 2f141c115ddc6ac05b35e183d45ba5039d3d283f.nq.gz
│   ├── 3e386f564dbd27c3616ad44b64520bf7b44582ae.nq.gz
│   ├── 57d05e7cd20c0d6d98585f1e333a37e910dadddb.nq.gz
│   ├── 68bc17f9ff2104a9d7b6777058bb4c343ca72609.nq.gz
│   ├── 6dbd43fbd7f530f3f0c554c63605be7e3d220485.nq.gz
│   ├── 7f4e1d5cf3ba2fa939bde3c58fdf4ca84fbad975.nq.gz
│   ├── 94aaefb570e06d7246729cbd0a6e101a0906da7d.nq.gz
│   ├── 9bee21c389b13bc633c418c3365ed908ab9f7c85.nq.gz
│   ├── 9c61ecd6e6de43072bdd1f509f8093d1f4597c68.nq.gz
│   ├── a986e64a008811a0df0a6386386b9b7f3ed8dc0c.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2b6179e8c352f8af23bd5c1d33636a091e29c427.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 18 files
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

[explosion/prodigy-whisper](https://github.com/explosion/prodigy-whisper)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
