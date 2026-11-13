# xp-developer-kb — releases

Public release artifacts for the **X-Plane plugin-development knowledge
corpus**. The source repository is private; this repo hosts the
installable wheel and its release notes.

## What this is

`xp-developer-kb` is one MCP server that gives any coding agent the
X-Plane plugin-development knowledge it usually gets wrong: one **KB
bundle** — curated rules and cross-platform bridges (XPPython3 first),
the `xp.*` SDK reference, the full dataref master list, and
host-language example layers — plus a **pre-embedded RAG index**, all
packaged as package data. 1173 concepts, no network or API keys needed
to serve.

Highlights:

- **Hybrid lookup** — BM25 over the bundle (primary) fused with dense
  retrieval over the shipped RAG index (secondary); tuned over a
  47-query golden suite.
- **Language heat** — naming a host language re-ranks the corpus
  toward that host's examples and away from the other host's pages.
- **Honest scores** — results present as 0–100 relevance with a
  "weak matches overall" tag when absolute signal is thin.
- **Token-anchored snippets** — previews open on the matched region
  (the `wind_now_direction_degt` row, not the table header).
- **`lint_code`** — ten XPPython3 rules distilled from the upstream
  guides (entry contract, lifecycle pairing, geometry, weather
  datarefs, …), each citing the concept that explains the rule.
- **The brief** — every session starts with the exact tool syntax and
  the plugin entry contract (`PI_<Name>.py`, `PythonInterface`,
  triple start return, Enable returns 1).

## Install

```
uv tool install https://github.com/stu-speed/xp-developer-kb-releases/releases/download/v1.0.0/xp_developer_kb-1.0.0-py3-none-any.whl
opencode mcp add xplane-kb --global -- xp-developer-kb mcp
```

(or `pip install <wheel-url>` and wire any MCP client to
`xp-developer-kb mcp` on your PATH).

## License

The package is dual-licensed: pipeline **code under Apache-2.0**, the
knowledge-corpus **content under CC-BY-4.0** (SPDX expression
`Apache-2.0 AND CC-BY-4.0`; both license texts ship in the wheel).
Third-party content inside the corpus is governed per source — the
shipped `ATTRIBUTION.md` documents each layer's basis (MIT-cleared
sources carry verbatim; Laminar's dataref list ships as facts with
attribution; the XPPython3 layers ride on the author's published-RAG
permission; unverified-license material is excluded from published
layers).

## Provenance

Built by the private source repo's deterministic pipeline
(`make package`: gate → stage → wheel; 185-test gate). The corpus
states its own vintage: `xp-developer-kb readme` and the served brief
carry the assembly date, and every concept carries `sources` links
back to its origin.
