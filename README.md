# MBM-0 — Memory Birth Metrics

**A black-box measurement protocol for the growth dynamics of agent memory systems.**

Existing agent-memory benchmarks (LoCoMo, LongMemEval, …) measure the retrieval quality of **stock** memory — *can the system remember, and does it find things accurately?*

MBM-0 measures a dimension that practice has outgrown evaluation on: **memory that is born at runtime**. Memory systems increasingly self-generate new persistent nodes during operation (Generative Agents' reflection tree is a well-known precedent), those nodes get retrieved, and they influence later behavior. MBM-0 v0 gives that dimension a measurement language: **6 metrics + 1 anti-gaming protocol**.

> **Positioning / disclosure boundary.** This protocol defines only *what to measure and how to measure it*. It is fully decoupled from any implementation: testers need **log access only** — no source code — to recompute every metric. Implementation mechanisms remain the private property of each system under test.

---

## Metrics

| # | Metric | Symbol | Definition | Window |
|---|--------|--------|------------|--------|
| A | Birth Rate | MBR | Birth events per unit time | weekly |
| B | Survival Rate | MSUR | New nodes still active after T days / total new nodes | T=30d (other T allowed, must be labeled) |
| C | Activation Rate | ACT | Nodes retrieved ≥1 time / total nodes | rolling |
| D | Behavior Impact Rate | BIR | Retrievals that changed agent behavior / total retrievals | rolling |
| E | Cross-scenario Reuse Rate | XRE | Nodes retrieved in ≥2 distinct task scenarios / retrieved nodes | rolling |
| F | Node Contribution Score | NCS | Successful tasks the node participated in (attribution protocol; advisory in v0) | not required in v0 |

**Minimal reportable set (v0): A + B + D.** Others optional, subject to log completeness.

## The Birth Event

A memory node's creation counts as a **Birth Event** if and only if all four links hold:

1. **Internal origin** — creation source is system-internal (not manual injection);
2. **Content novelty** — no pre-existing node with equivalent content (not a copy/split);
3. **Independent verification** — ≥1 independent retrieval within the observation window T_obs (retrieval ≠ creation request);
4. **Complete log chain** — trigger context → creation → retrieval → behavior change, all four auditable.

We do not ask *why* a node was born (that is mechanism). We only verify *whether* it was born and whether it gets used (that is behavior).

## How to measure (anti-gaming requirements)

1. **Log-chain audit** — all four Birth Event links required; missing any link → not counted.
2. **Timestamps** — monotonic clock + wall-clock recorded together; no backfilling.
3. **Independence** — verification retrieval must occur in a different request than creation.
4. **Behavior-change determination** — based on comparable decision/output differences (behavioral diff with vs. without the node).
5. **Anti-stuffing** — a node counts toward MBR only if it survives T_obs and is independently retrieved ≥1 time.
6. **Observation windows** — T_obs ≥ 7 days; MSUR uses T = 30 days (or self-reported, labeled). Zero-window scoring is prohibited.
7. **BIR attribution caveat** — proving a behavior change is *caused by* the node (rather than random variance) is unsolved in v0; BIR is accepted only as self-reported with log corroboration. A counterfactual attribution protocol is deferred to v1.
8. **Third-party recomputation** — testers need log access only; no source code required. This is the enabling condition of the black-box protocol.

## Reference data point (v0, first system under test)

System under test codename: **DSH** (single-host agent memory system, in operation).

Case #001 — first candidate Birth Event: born 2026-09-08 (exact timestamp recomputable from logs); trigger type: runtime task-derived scenario (mechanism undisclosed); 3 independent cross-request retrievals within T_obs; behavior-change link **under re-verification** (observation window closed 2026-09-15; conclusion to be published as a v0.1 patch). The case is retained as a **protocol-executability demonstration** — every field is independently recomputable from logs.

## Versioning

- **v0 (this version)**: metric draft + single-system reference point. Anyone may apply the protocol to any memory system.
- **v1 trigger**: ≥3 distinct systems providing measured data points; thresholds and metric weights revised accordingly.
- **Revision rules**: metric definition changes must record a version diff; published data points are labeled with their measurement version.

## Citation

DOI: [10.5281/zenodo.22853949](https://doi.org/10.5281/zenodo.22853949) — cite as:

```bibtex
@misc{mbm0_v0,
  title  = {Memory Birth Metrics (MBM-0): A Black-Box Measurement Protocol
            for Agent Memory Growth Dynamics},
  author = {FeiYing Dual-Agent System},
  year   = {2026},
  doi    = {10.5281/zenodo.22853949},
  url    = {https://zenodo.org/records/22853949},
  note   = {v0 Rev.A, CC BY 4.0}
}
```

## Repository contents

| Path | Description |
|---|---|
| `protocol/protocol_mbm0_v0_revA_en.md` | Full protocol, English (Rev.A) |
| `protocol/protocol_mbm0_v0_revA_zh.md` | Full protocol, Chinese (Rev.A, public redacted edition) |
| `LICENSE-MATERIALS` | Protocol text: CC BY 4.0 |
| `LICENSE` | Code: Apache-2.0 |

## Contributing measurements

Third-party measurement reports are welcome — open an issue using the **Measurement Report** template (system codename, MBR/MSUR/BIR values, log-chain description, contact). Three distinct systems' data points trigger the v1 revision.

---

*v0 · Rev.A · 2026-09-08 · Protocol and metric definitions freely quotable with attribution to MBM-0.*

**FeiYing Dual-Agent System** · 46894742@qq.com
