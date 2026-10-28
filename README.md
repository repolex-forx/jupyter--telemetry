# Repolex Knowledge Graph of jupyter/telemetry

RDF knowledge graph data for [jupyter/telemetry](https://github.com/jupyter/telemetry), parsed by [repolex](https://repolex.ai).

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
rlex download jupyter/telemetry
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2975fcac06cb3ffa5872258669990f488547e0c1
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2975fcac06cb3ffa5872258669990f488547e0c1
│           └── chunk-001.nq.gz
├── blob
│   ├── 08486464d5bbdb4979426070b311ee15e727c913.nq.gz
│   ├── 0a0d9379a7391ba6443afbddc5500ebf6fc58d53.nq.gz
│   ├── 0ca421800918d56fd85fa768849677ec45aa1e55.nq.gz
│   ├── 0fd2b469d52c795705e1ec26c226510329225b03.nq.gz
│   ├── 131ee184a1712948383b210ae0104444affc459a.nq.gz
│   ├── 19c7630bd5dd59e27a8ecf069ec2e208bd2a1f18.nq.gz
│   ├── 1a0409b1222acc18da60f3c6a6803a547eff7ddf.nq.gz
│   ├── 2119f51099bf37e4fdb6071dce9f451ea44c62dd.nq.gz
│   ├── 29a19480760753ea1c32d4321d995e097e5432d4.nq.gz
│   ├── 2a0e0af3e295b795c72442805e25bea9885cf8c9.nq.gz
│   ├── 5683356b34207406c9b71dbf782e6f48d5ae61c5.nq.gz
│   ├── 57bd024d55d5cad1380f221fc907a22b83124585.nq.gz
│   ├── 611d66a98ab3b366d5f89acf00938dddbf7b5092.nq.gz
│   ├── 6812b1e291aae6e17c597f1eb8bef1ca0e06a97a.nq.gz
│   ├── 709f7c08414e82efda5dabd17e084e6a46537bd7.nq.gz
│   ├── 8bf1ba938af9b4993f625db4fc6e708be9f3f3b7.nq.gz
│   ├── 8e4f4f3c92844501123fa6f2a84dbbf175462945.nq.gz
│   ├── 9138a94663da7f07c01609e75466fb87cdaeda2f.nq.gz
│   ├── 9353319fbb275719063c776d0e30d02d73df0e52.nq.gz
│   ├── 9ab153aef13bff9aa2cbea3f3535046a67d20452.nq.gz
│   ├── a32058bb206292daff2aeb42a70638b025175869.nq.gz
│   ├── a35a41767bae5a8beeb2278483d8174c3c2df796.nq.gz
│   ├── a63524839e458d60fb6f6e7c1aa6d912fc0c194d.nq.gz
│   ├── ac8628022f38c49c74437bfb5856840e12c30d0f.nq.gz
│   ├── bb3030b309b14dccdd6742f9a9250df8d36443dd.nq.gz
│   ├── bd05d25cd4c1eae757fe2a2d7ce3656194bfd680.nq.gz
│   ├── bff4986141155544dd60a5089760b660ffeec4f2.nq.gz
│   ├── c1aa89d26b1c2bb29c3ec1b89a208e280018ae34.nq.gz
│   ├── c4c8956a5633c8f5a9a2907ae576b0a44b105ff4.nq.gz
│   ├── d2bbfa0e41bfcabffa9b7e8f319397858a04551f.nq.gz
│   ├── d4bb2cbb9eddb1bb1b4f366623044af8e4830919.nq.gz
│   ├── e0ea309f2bfa9b4acac29f7a5296b99dd441a190.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e735a818ba93d6cbdc1f4e1cc60ccbc9a4254bd1.nq.gz
│   ├── e7d871acfd0fe3f1d4606d84c0dd7a49312873d5.nq.gz
│   ├── e8c8d8c3d378a28d4c720d3730618a9f1408aad9.nq.gz
│   ├── eca55196cf908b74fbb66a0e123fd618519e38ad.nq.gz
│   └── f68458af837c119a28567bf2f6a3d591b7e9df75.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2975fcac06cb3ffa5872258669990f488547e0c1.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[jupyter/telemetry](https://github.com/jupyter/telemetry)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
