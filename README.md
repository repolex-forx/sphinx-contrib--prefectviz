# Repolex Knowledge Graph of sphinx-contrib/prefectviz

RDF knowledge graph data for [sphinx-contrib/prefectviz](https://github.com/sphinx-contrib/prefectviz), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/prefectviz
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5b1dad0788c4d51d9a3a61a0f9981abc77967c18
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5b1dad0788c4d51d9a3a61a0f9981abc77967c18
│           └── chunk-001.nq.gz
├── blob
│   ├── 11e5c83221dca57de2c1dfffc21e757302fcaf68.nq.gz
│   ├── 22290e0443b011bb0027cb9ba1a94b77f7787697.nq.gz
│   ├── 2a5245386b937ac9260a9728f1c734e1b0f35ab0.nq.gz
│   ├── 3a604e3aabd2d0c81414f2045df2ee20336f7fab.nq.gz
│   ├── 55ff9de50d6ca483766e6c2f6c04990de5eb12df.nq.gz
│   ├── 74c66f5d851577725991910cebabf911f3e9720f.nq.gz
│   ├── 75f703e26044ba4c6b1be9e9b010231c7c11554f.nq.gz
│   ├── 846beca58cb84c697131f8910da55635db42b0d0.nq.gz
│   ├── 8c2b983a93b3d19b4290b89aa860362358663166.nq.gz
│   ├── 9da98fa4710a7397c51d42e00785ad0d686d1854.nq.gz
│   ├── a9f2ec2f519ee3e67970e3e0ba0d2f4eb5808177.nq.gz
│   ├── b4a9d28213a3cadda30af021d11e2664f92f05c8.nq.gz
│   ├── e1095ce6e088a91932b1fab6e53a0f1801a767e1.nq.gz
│   ├── e6a325a58b41da6f6a084b0e19dc80587aae4ecc.nq.gz
│   ├── f288702d2fa16d3cdf0035b15a9fcbc552cd88e7.nq.gz
│   └── fe28f4b545c2a4159f6cdb5543a6f162aa8316f8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5b1dad0788c4d51d9a3a61a0f9981abc77967c18.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
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

[sphinx-contrib/prefectviz](https://github.com/sphinx-contrib/prefectviz)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
