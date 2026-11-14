# xp-developer-kb — releases

## What this is:

An MCP Server with a hybrid OKF/RAG knowledge base of datarefs, sdk-api, sample code and guides for XPPython3 and Xlua. This will help guide agents to write plugin code with optimal use of the sdk-api's and not hallucinate datarefs.

Support for XPPython3 and Lua but only fully built out and tested for XPPython3.

## On the agent app rooftop

> **Neo:** Can you code that thing?
> **Trinity:** Not yet.
> *(Trinity calls up Huggingface)*
> **Tank:** Operator.
> **Trinity:** Tank. I need a OKF/RAG for Xppython3. Hurry.
> *(Tank uploads the MCP, and Opencode's screen flutters as it absorbs the knowledge)*
> **Trinity:** Let's go.

## Highlights:

- **Hybrid lookup** — BM25 over the bundle (primary) fused with dense retrieval over the shipped RAG index (secondary); custom tuned to the dataset.
- **Language heat** — naming a host language re-ranks the corpus toward that host's examples and away from the other host's pages.
- **`lint_code`** — twelve XPPython3 rules distilled from the upstream guides (entry contract, lifecycle pairing, geometry, flight-loop return semantics, weather datarefs, …), each citing the concept that explains the rule. When serving with the corpus, it also validates usage against the dataset itself: an invented `xp.*` API name or a dataref path that isn't in the master list is an error before the plugin ever loads.
- **The brief** — every session starts with the exact tool syntax and the plugin entry contract (`PI_<Name>.py`, `PythonInterface`, triple start return, Enable returns 1).

## Install:

Easiest way is to prompt your agent: *"Install MCP xp_developer_kb-1.0.0-py3-none-any.whl"*

```sh
uv tool install https://github.com/stu-speed/xp-developer-kb-releases/releases/download/v1.0.0/xp_developer_kb-1.0.0-py3-none-any.whl
opencode mcp add xplane-kb --global -- xp-developer-kb mcp
```

## Dataset:

### SOURCES

- Laminar's dataref master list (developer.x-plane.com): the complete datarefs layer, parsed row-for-row, no LLM.
- XPPython3 v4 (xppython3.readthedocs.io / pbuckner/x-plane_plugins): the full prose docs (verbatim, @pbuckner permission), the complete `xp.*` bindings reference, and 80 demo plugins carried verbatim (MIT).
- X-Friese/FlyWithLua (GitHub): the repo's documentation, and 117 example scripts cited by pinned link (no Lua text shipped).
- X-Plane/XLua (GitHub, MIT): XLua's full SDK documentation.
- developer.x-plane.com SDK technical articles (14): link-only cards — title, canonical URL, corpus cross-references; the unlicensed article prose stays at the source.
- Hand-written curated layer: human-verified, CC-BY-4.0.
- Not shipped: Laminar's C SDK reference (740 API entities) and technical article prose — unlicensed; the C-facing knowledge reaches consumers only distilled inside the bridges.

### COUNTS (Guns. Lots of guns.)

- Datarefs: 6,216 master-list rows (6,188 unique paths) in 119 namespace tables — name, type, access, units, first version, platform, accessor note for every row.
- API methods: 589 `xp.*` binding pages (every documented function, constant, and type, full signature) plus 27 module guides.
- Doc guides: 202 — 120 XPPython3 prose pages (author-granted, verbatim), 68 XLua SDK pages (MIT), 14 Laminar article link cards.
- Examples: 197 working plugins — 80 XPPython3 demos verbatim (MIT), 117 FlyWithLua scripts by pinned link — each cross-linked to every API and dataref its code uses.
- Curated: 37 concepts (17 patterns, 7 cross-host bridges, 13 canonical definitions).
- Total: 1,187 shipped concepts; 200-test gate.

## License:

Pipeline code **Apache-2.0**; knowledge-corpus content **CC-BY-4.0** (both texts ship in the wheel). Third-party content rides on per-source clearance, documented in the shipped `ATTRIBUTION.md`.
