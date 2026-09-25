# L0xRE Release Ledger

**Campaign:** L0xRE release organization and publication  
**Owner:** Sean Rotramel  
**Initialized:** September 24, 2026 — America/Los_Angeles  
**Status:** Planning artifact; agent execution has not started in this ledger.  
**Canonical destination after setup:** `seanyourhighness/L0xRE/RELEASE-LEDGER.md`

## 1. Operating rules

The coordinating agent is the only writer of this ledger. Qwen-27B on the z840 supplies two parallel worker lanes, with a maximum of two in-flight jobs. Each job receives an ID, immutable inputs, file ownership, a concrete acceptance test, and an output path. Workers return patches/reports and evidence; they do not publish, merge champions, alter shared state, or stop their own model service.

Read this snapshot and the current champion manifest before resuming. Record a task before starting and append an outcome after each experiment, test, merge, migration, or publication attempt. Preserve failed and rejected attempts. Update the current-state section without rewriting event history. Keep detailed existing experiment ledgers and link to them. Never store credentials or private prompt data here.

Before benchmarking on the z840 GPU, the external coordinator drains both lanes, frees required GPU/CPU/RAM resources, tests with exclusive ownership, restores Qwen, and health-checks the service. Do not mark a worker reachable until the actual endpoint and model identity are tested.

## 2. Owner-directed naming and scope

| Component | Canonical name / destination | State |
| --- | --- | --- |
| GitHub hub | `seanyourhighness/L0xRE` — display title **L0xRE Releases** | Planned |
| Static offload runtime | `seanyourhighness/L0xRE-EXLLAMA-Offload` | Planned rename of `0xrc-hot-experts` |
| Escha BeeLLama runtime | `seanyourhighness/L0xRE-BeeLLama-Low` | Planned separate repository |
| Runtime targets | SM89 and SM120, with separate packages and qualification | Package inventory pending |
| E3 model | `L0xRE-27b-Low` on the authorized HF namespace | Namespace and files not yet verified |
| Parallel worker | Qwen-27B on z840; two logical lanes | Endpoint and served model ID not yet tested |

These are linked sibling product repositories under a hub, not a mixed runtime monorepo. Retain working internal CLI/import/model aliases unless a compatible replacement is tested.

## 3. Initial evidence snapshot

### E-001 — Offload product identity

**Evidence class:** Observed documentation, not a new runtime test.  
The existing repository README is ExLlamaV3-focused. Its static/adaptive wording differs from the narrower `0xrc-v0.1.0` release notes, which identify static hot-expert offload as shipped and adaptive swapping as experimental/shelved. Reconcile against the frozen release; do not advertise adaptive behavior as qualified.

Source: [README](https://github.com/seanyourhighness/0xrc-hot-experts/blob/release/0xrc-v0.1/README.md) · [0xrc-v0.1.0 release](https://github.com/seanyourhighness/0xrc-hot-experts/releases/tag/0xrc-v0.1.0)

### E-002 — Misplaced SM120 release

**Evidence class:** Observed release metadata and reported tests, not locally reproduced.  
**Tag:** `beellama-sm120-v0.4.7-r9`  
**Reported target branch:** `release/beellama-sm120-v0.4.7`  
**Asset:** `escha-beellama-v047-sm120-r9.tar.zst`  
**Reported size:** 574,363,796 bytes  
**Reported SHA-256:** `e93f85d1593c4c6a6397cd34307d75f409fa77e322c502a23a47b2819e68a571`

The release reports ratios above 0.95 for ordinary prefill/decode and DFlash2 prose/code, plus 32/32 clean-extract integration checks. Preserve its tested one-slot profile and host limitations; do not extend the claim to untested MTP, longer contexts, or multiple slots. Download and hash-check the asset before treating metadata as a verified migration receipt.

Source: [SM120 r9 release](https://github.com/seanyourhighness/0xrc-hot-experts/releases/tag/beellama-sm120-v0.4.7-r9)

### E-003 — Inputs not yet inventoried

SM89 champion source/package/receipts; exact E3 and W2 artifact identities; N/150 suite, scorer and raw results; W2/SGLang comparison receipts; exact current 3.5-bit and 2.5-bit EXL3 model revisions; HF publishing namespace; live Qwen endpoint/model ID. Do not replace these gaps with remembered numbers or guessed paths.

## 4. Champion and publication pointers

| Product / target | Source commit | Package/model hash | Evidence receipt | Public destination | State |
| --- | --- | --- | --- | --- | --- |
| ExLlama static offload | Resolve from real champion | Resolve per checkpoint | Existing receipts to inventory | Planned canonical repo | Not inventoried |
| BeeLLama SM89 | Resolve from real champion | Resolve actual archive | SM89 receipts to locate | Planned canonical repo | Not inventoried |
| BeeLLama SM120 | Resolve immutable commit behind r9 | Metadata digest above; bytes not checked here | r9 reports; raw receipts to reconcile | Legacy release above | Migration pending |
| L0xRE-27b-Low / E3 | Resolve recipe and source revisions | Resolve actual model file(s) | N/150 and serving receipts to locate | HF namespace unresolved | Not inventoried |

## 5. Task board

| ID | Task | Owner | Dependency | Status | Acceptance / next action |
| --- | --- | --- | --- | --- | --- |
| LXR-001 | Freeze and back up champions, dirty changes, refs and release assets | Coordinator | None | DONE | Immutable identities and rollback map recorded |
| LXR-002 | Resolve Qwen endpoint/model and verify two lanes | Coordinator | None | DONE | Health/model identity and two-request test succeed |
| LXR-003 | Inventory repo/asset migration and source lineage | Lane A | 001, 002 | REVIEW | Scoped migration map with hashes and preserved aliases |
| LXR-004 | Inventory model provenance, N/150 and W2/SGLang evidence | Lane B | 001, 002 | REVIEW | Exact artifacts, protocol, scores or explicit missing cells |
| LXR-005 | Build hub catalog and product navigation drafts | Coordinator | 003 | TODO | Exact names, per-component status, canonical targets |
| LXR-006 | Prepare separate BeeLLama source and SM89/SM120 packages | Lane A; coordinator integrates | 003 | TODO | Manifests, rebuild recipes, clean-package tests |
| LXR-007 | Prepare renamed E3 files and HF model card | Lane B; coordinator integrates | 004 | TODO | Identity/provenance, runtime instructions, supported claims |
| LXR-008 | Close missing benchmark and correctness cells | Coordinator | 004, 006, 007 | TODO | Repeatable receipts; each required gate resolved |
| LXR-009 | Publish validated BeeLLama destination and migration notices | Coordinator | 006, 008 | TODO | Download hashes and legacy-to-new links verified |
| LXR-010 | Rename and publish static offload product with both model recipes | Coordinator | 003, 009 | TODO | Redirects, tuned-control tests, accurate static scope |
| LXR-011 | Publish HF model and verify a clean download/load | Coordinator | 007, required gates in 008, compatible runtime ready | TODO | Final HF revision and hashes; advertised loads succeed |
| LXR-012 | Finish hub links, acceptance audit and campaign record | Coordinator | 009, 010, 011 | TODO | All requested components publicly usable; limitations explicit |

Independent work may proceed when its own dependencies are satisfied. Do not hold a ready offload release for unrelated optional-mode work. Do not declare the full campaign complete before both BeeLLama targets and the model are delivered.

## 6. Gate contract

- **Native speed:** candidate / matched native throughput >= 0.95 for each required GPU/mode/workload row. Compare ordinary to ordinary and DFlash2 to DFlash2. Faster than native passes; no arbitrary fixed tok/s or mandatory 2x target.
- **Correctness:** use the existing validated same-artifact control and established exact/tolerance rules. Do not equate downstream quality with numerical parity or demand bitwise equality between different quantizations.
- **Claims:** publish separately measured speed, file size, serving RAM/VRAM, and N/150 results. Cross-stack SGLang comparisons require disclosed settings and limits. No unverified universal “same quality” claim.
- **Packaging:** a renamed filename may preserve bytes; a repackaged archive needs a new hash and extracted-package checks. Changed runtime/model/dependencies need affected requalification.

Gate statuses: `PASS`, `FAIL`, `NOT TESTED`, `NOT APPLICABLE`. Task statuses: `TODO`, `RUNNING`, `BLOCKED`, `REVIEW`, `DONE`, `REJECTED`. `DONE` requires a receipt, not a worker assertion.

## 7. Append-only event template

```text
ID:
Timestamp with timezone:
Product / GPU architecture / mode:
Task or hypothesis:
Owner / worker lane:
Input source commit and model hashes:
Changes and output paths:
Exact commands and environment:
Baseline metrics / candidate metrics / paired ratio:
Correctness and memory outcome:
Evidence paths / raw logs:
Verdict and reason:
Blockers and next action:
Rollback pointer:
Public release / HF revision, when applicable:
```

## 8. Event history

### INIT — September 24, 2026 (America/Los_Angeles)

Created a starter plan and ledger from the owner's requested hierarchy plus inspected repository documentation/release metadata. No repository migration, publication, model upload, worker connection, downloaded-asset verification, or hardware benchmark has been performed as part of this initialization. All execution tasks remain TODO.

### LXR-002 — 2026-09-24 (America/Los_Angeles) — DONE

- Endpoint: `http://192.168.1.159:8080/v1` (z840, llama.cpp/llama-server, health 200).
- Served model identity tested: `/home/sean/models/unsloth-qwen38-27b-q4km/Qwen3.8-27B-UD-Q4_K_M.gguf`
  (Q4_K_M, 27.3B, n_ctx 196096) — matches the `custom:z840` provider in agent config.
- Two-lane test: two concurrent chat completions with distinct prompts both returned exact
  expected replies ("LANE A ONLINE" / "LANE B ONLINE"), wall 1.3s. Two logical lanes reachable.
- Thinking disabled via `chat_template_kwargs.enable_thinking=false` for worker requests.
- No GPU benchmarking performed; no model service altered.

### LXR-003 / LXR-004 — 2026-09-24 — RUNNING

- Coordinator inventoried local evidence (repo refs/tags, release-asset SHA-256s, model dirs,
  Escha GGUF hashes, n/150 and SGLang receipt locations) and froze it into two immutable
  review packets: `~/work/l0xre/lane-A-packet.md` (LXR-003 migration map) and
  `~/work/l0xre/lane-B-packet.md` (LXR-004 provenance/gate matrix).
- Notable coordinator observations handed to lanes: `qwen38-flash-next-exl3-r0b0tlab-2.50bpw-ng5`
  shards are 74–90-byte Git-LFS pointer stubs (not weights); no n/150 suite receipts found on
  disk for E3/W2/EXL3 targets; HF namespace for L0xRE-27b-Low unresolved.
- Workers: Qwen-27B on z840, lanes A and B in parallel, review-only (no file access, no
  publication authority). Reports land in `~/work/l0xre/lane-{A,B}-report.md`.

### LXR-001 — 2026-09-24 — DONE

- Ref/tag freeze snapshot: `~/work/l0xre/freeze-refs.txt` (all heads/tags + remotes, 2026-09-24T20:48-07:00).
- Working tree of `~/code/exllamav3-champion-features` (origin=0xrc-hot-experts) is CLEAN on
  `feature/adaptive-hot-experts` @ e8e8d28 — the previously shelved adaptive work is now
  committed on that branch, not dirty. No champion work at risk of loss.
- Local release-asset SHA-256s computed (rc1/rc2 wheel/tar/bundle) and recorded in lane packets.
- SM120 r9 asset downloaded from GitHub and hash-checked:
  `e93f85d1593c4c6a6397cd34307d75f409fa77e322c502a23a47b2819e68a571` — EXACT MATCH to release
  metadata; 574,363,796 bytes. Stored at `~/work/l0xre/assets/escha-beellama-v047-sm120-r9.tar.zst`.
  This is now a verified migration receipt, not just metadata.
- Rollback pointer: nothing remote mutated; all operations read/download only.

### LXR-003 — 2026-09-24 — REVIEW (lane A report + coordinator resolution)

- Lane A report: `~/work/l0xre/lane-A-report.md` (migration map, rename-safety audit,
  reversible step plan). Coordinator resolved its open questions with live git checks:
  - `974e571` (r9) is NOT an ancestor of `release/0xrc-v0.1`; common merge-base IS `9ca0885`
    — the BeeLLama branch was cut FROM the rebrand commit. Histories are shared, so pushing
    branch+tag to a new repo preserves lineage (Lane A Scenario A/B resolved: hybrid).
  - Tag `beellama-sm120-v0.4.7-r9` is ANNOTATED (tag object must be pushed, not just commit).
  - The 3 unreleased commits (30b3cd7, 66ce79f, 145de28) are manifest/receipt/docs updates on
    `release/beellama-sm120-v0.4.7` — no runtime code changes observed in subjects.
  - CI: no `.github` file references the repo slug `0xrc-hot-experts`; `pyproject.toml`
    `name = "exllamav3"` confirmed — rename-safe per audit.
  - BeeLLama python dist name question is moot: the BeeLLama product is a C++/CMake
    llama.cpp fork (beellama-escha-native), not a Python distribution.
- Asset integrity item resolved: SM120 asset hash verified (see LXR-001).
- Remaining for coordinator before execution: GitHub auth check, hub repo creation,
  and owner approval of the rename order (BeeLLama destination FIRST, rename second, per plan §03).

### LXR-004 — 2026-09-24 — REVIEW (lane B report + coordinator notes)

- Lane B report: `~/work/l0xre/lane-B-report.md` (artifact identity table, gate matrix,
  n/150 gap protocol, SGLang claim limits, quarantine recommendation).
- Coordinator confirms the ng5 stub finding: `qwen38-flash-next-exl3-r0b0tlab-2.50bpw-ng5`
  shards are 74–90-byte LFS pointers. QUARANTINE: excluded from all publication candidates.
- Gate matrix summary (all four targets): native-speed rows NOT VERIFIED locally (r9 report
  metadata only); n/150 NOT TESTED for E3/W2/EXL3 (no suite receipts on disk); E3/W2 file
  identity PASS (hashes computed); EXL3 3.50/2.50 hashes still to be computed (large files —
  schedule with next idle window, not blocking BeeLLama work).
- HF namespace for L0xRE-27b-Low remains UNRESOLVED — requires owner decision (which HF
  account) before LXR-007 can complete.

### LXR-004 addendum / namespace resolution — 2026-09-24

- HF namespace RESOLVED from authenticated local config: `hf auth whoami` -> **YourHighnessLA**
  (differs from GitHub `seanyourhighness`; plan §05 warned against assuming equality).
- GitHub `gh` auth active as seanyourhighness with `repo` scope — migration steps are executable.
- BeeLLama SM89 champion located: `~/kernel-lab5090/4090-escha-sprint-rc-fast.{md,env}`
  (frozen sprint-RC profile: SM89 bridge pkg `~/kernel-lab5090/preview-bridge-sm89`,
  routes R248/251/253/258/260/262/264, E3 GPU-resident embeddings, KVarN3/2, MTP n2 + CPU
  q4_0 draft; ESCHA_W2_I8_HEAD and decode-gate-overlap deliberately OFF/experimental).
  Evidence dirs r113–r150 under ~/kernel-lab5090/evidence/. SM89 *package* does not exist yet
  (LXR-006 must build it); SM120 r9 component tree lives in the 0xrc repo under
  `beellama-sm120/` (BUILD.md, MANIFEST.json, MODELS.md, PARITY.md, SHA256SUMS, bridge/,
  parity ledger) — that subtree is the migration seed for L0xRE-BeeLLama-Low.
- escha-release RECEIPT.md (2026-09-19 DFlash2 E3/W2 champion) records commit-unavailable
  caveat: identity = file-hash pairs, not a git commit. Relevant to §06 identity rules.
- EXL3 3.50bpw + 2.50bpw full-file SHA-256 pass started in background ->
  `~/work/l0xre/exl3-hashes.txt` (~120 GB read; non-blocking).
- Hub README draft written: `~/work/l0xre/hub-README-draft.md` (LXR-005 draft).
