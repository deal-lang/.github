<div align="center">

<a href="https://deal-lang.org">
  <img src="https://deal-lang.org/og.png" alt="DEAL — Digital Engineering Authoring Language" width="680">
</a>

### A text-first language for model-based systems engineering

Author requirements, architecture, interfaces, calculations, and verification as **plain text** that lives in Git — readable, diffable, and fast — with a 100% mapping to KerML and the SysML v2 API.

[**Documentation → deal-lang.org**](https://deal-lang.org) · [Get started](https://deal-lang.org/getting-started/installation/) · [Language reference](https://deal-lang.org/reference/definitions/)

</div>

---

## Why DEAL

Digital engineering promises a single source of truth, but today's graphical, binary, GUI-bound MBSE tools fight you for it:

- **Sync is fragile** — requirements in DOORS, architecture in Cameo, interfaces in spreadsheets, verification in test tools, all drifting apart.
- **Versioning is an afterthought** — binary model files don't diff, don't merge, and don't fit the workflows software solved decades ago.
- **GUIs don't scale** — what takes a line of text takes a dozen clicks, and none of it is scriptable.

DEAL treats the system model as **code**: plain-text `.deal` / `.dealx` / `.dealview` files that compile to SysML v2 JSON and ReqIF, live in Git, diff cleanly, and run through CI. It isn't a replacement for SysML v2 — it's the authoring surface for it.

## What works today

The compiler and CLI are real and exercised by the test suite:

```
deal parse      tokenize + parse .deal/.dealx → AST JSON
deal check      semantic + dimensional analysis (+ --verify against evidence)
deal fmt        format in place
deal build      generate SysML v2 JSON or a ReqIF archive
deal init       scaffold a new project
deal install    resolve deal.toml dependencies → deal.lock
deal simulate   run simulations registered in deal.sims.toml
deal evidence   capture and manage verification evidence
```

This includes the **behavioral surface** — actions and state machines
(succession flows, decisions, fork/join, loops, send/accept/assign, transitions,
entry/do/exit) parse, type-check, format, and emit as OMG-schema-valid SysML v2.

## Repositories

| Repository | What it is | License |
|------------|-----------|---------|
| [**deal**](https://github.com/deal-lang/deal) | Core compiler — a Zig engine (`libdeal.a`) with a Rust CLI and LSP server | Apache-2.0 |
| [**spec**](https://github.com/deal-lang/spec) | Language specification, EBNF grammar, and the showcase corpus | MIT |
| [**deal-stdlib**](https://github.com/deal-lang/deal-stdlib) | Standard library — units, base types, and math | — |
| [**deal-lang.org**](https://github.com/deal-lang/deal-lang.org) | Documentation site, [deal-lang.org](https://deal-lang.org) | Apache-2.0 |

## Status

The parser, semantic analyzer, formatter, IR, SysML v2 / ReqIF backends, the
`calc` / `constraint` surface, project and dependency tooling, and the
simulation-evidence pipeline are implemented and gated by the test suite. The
**behavioral surface** (actions + state machines) is complete through SysML v2
emission. Next up: the editor-first platform — a desktop editor, import
pipelines, and documentation generation.

DEAL is pre-release and built from source today (Zig 0.16 + Rust). See the [installation guide](https://deal-lang.org/getting-started/installation/) to get going.

## License

Each repository is licensed individually (see the badges above). The core compiler and documentation site are Apache-2.0; the specification is MIT.
