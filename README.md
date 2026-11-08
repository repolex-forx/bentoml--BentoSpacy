# Repolex Knowledge Graph of bentoml/BentoSpacy

RDF knowledge graph data for [bentoml/BentoSpacy](https://github.com/bentoml/BentoSpacy), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/BentoSpacy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── b17cc50f4022efaacbb0e1821e5fa8665c1e1a26
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── b17cc50f4022efaacbb0e1821e5fa8665c1e1a26
│           └── chunk-001.nq.gz
├── blob
│   ├── 01d7f95b0ac35a34b1a842653131239e81dd3b57.nq.gz
│   ├── 213930f134449732bf1b01bf64bbbd716fa01f7d.nq.gz
│   ├── 2906a453d3ed1583e3ba3b1d491b1e4b25995c5d.nq.gz
│   ├── 2c0733315e415bfb5e5b353f9996ecd964d395b2.nq.gz
│   ├── 347b3213effbe928bc593153a99e0a1efc8ef29e.nq.gz
│   ├── 883fc7e96c644b943e0ec61219947ca87537aeb5.nq.gz
│   ├── 958df24811268559be49e80f0460eac486eace6a.nq.gz
│   ├── a1a2705d43d10b8d4904245bc5e22511e5e6ddac.nq.gz
│   ├── bf5cd35c21f3690294a149ee0b504511c90471f4.nq.gz
│   ├── ea2b9097362d424c23673c8e07e8d48725dc6a8d.nq.gz
│   └── fe7f1d70de454f793366589311538438da2949fc.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── b17cc50f4022efaacbb0e1821e5fa8665c1e1a26.nq.gz
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

[bentoml/BentoSpacy](https://github.com/bentoml/BentoSpacy)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
