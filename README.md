# L0xRE Releases

Curated runtimes and models for running large quantized LLMs on consumer GPUs.
One family, three products, every claim traceable to a measured artifact.

## Choose your release

| Product | Best for | Model / format | Tested hardware | Status | Quickstart |
| --- | --- | --- | --- | --- | --- |
| [**L0xRE-EXLLAMA-Offload**](https://github.com/seanyourhighness/L0xRE-EXLLAMA-Offload) | Large routed-MoE EXL3 checkpoints that need static expert CPU/GPU offload | EXL3 (ExLlamaV3 fork, Python `exllamav3`) | RTX 5090, RTX 4090 (Linux/WSL2) — qualified; RTX 4070 Ti Windows in progress | Pre-release | [Install](https://github.com/seanyourhighness/L0xRE-EXLLAMA-Offload#install) |
| [**L0xRE-BeeLLama-Low**](https://github.com/seanyourhighness/L0xRE-BeeLLama-Low) · SM120 | Escha E3/W2 + stock GGUF on RTX 5090, incl. DFlash2 spec decode | GGUF (BeeLlama/llama.cpp fork) | RTX 5090 (SM120), Ubuntu 24.04 WSL, driver 616.56 — qualified one-slot 8K/32K | Stable (v0.4.7-r9) | [Quickstart](https://github.com/seanyourhighness/L0xRE-BeeLLama-Low#quickstart) |
| [**L0xRE-BeeLLama-Low**](https://github.com/seanyourhighness/L0xRE-BeeLLama-Low) · SM89 | Same runtime on RTX 4090-class GPUs | GGUF | RTX 4090 (SM89) — 12 GiB/80K + 16 GiB/256K + full-32K configs certified | Release `beellama-sm89-v0.4.7-r1` | [Release](https://github.com/seanyourhighness/L0xRE-BeeLLama-Low/releases/tag/beellama-sm89-v0.4.7-r1) |
| [**L0xRE-27b-Low**](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low) | Smaller-footprint 27B hybrid (formerly Escha E3) with measured native-GGUF parity | GGUF (requires L0xRE-BeeLLama-Low; **not** stock llama.cpp/Ollama/LM Studio) | Served via L0xRE-BeeLLama-Low SM120 (qualified) / SM89 (115.4 / 116.3 tok/s code decode, certified configs) | Published ([non-MTP](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low) · [MTP variant](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low-MTP)) | [Quickstart](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low#quickstart-sm89-rtx-4090-class--certified-12-gib-config) |

## Status legend

- **Stable** — qualified gates published with receipts; safe default.
- **Pre-release** — works on qualified hardware; qualification incomplete (see release notes).
- **Unqualified / pending** — exists, not packaged or not yet measured; do not deploy.

## Benchmarks & evidence

Every performance statement links to a receipt naming the exact artifact, host, and protocol.

- SM120 v0.4.7-r9 parity (E3/W2 vs matched native GGUF, ≥0.95 all rows): see the release's
  `PARITY.md` and `docs/escha-v047-sm120-parity-ledger.md`.
- EXL3 offload (5090: 64.04 tok/s; 4090: 26.53 tok/s static+MTP3): `benchmarks/` in the
  offload repo.
- SM89 v0.4.7-r1 (RTX 4090): 12 GiB 115.4 ± 2.4 · 16 GiB 116.3 ± 2.9 · full-32K 139.5 ± 7.5 tok/s
  code decode; prefill 2578 ± 78. Receipts in the release archive (`receipts/`).
- N/150 quality: 124–126 / 150 pass@1 (three passes, thinking on) vs 117 native baseline —
  published on the [L0xRE-27b-Low model card](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low#quality).
  Internal suite, directional; broader runs pending.

## Migration map

| Old location | New canonical | Redirect |
| --- | --- | --- |
| `seanyourhighness/0xrc-hot-experts` | `seanyourhighness/L0xRE-EXLLAMA-Offload` | GitHub 301 (repo rename) |
| BeeLLama SM120 r9 release (misplaced in 0xrc-hot-experts) | `L0xRE-BeeLLama-Low` release `beellama-sm120-v0.4.7-r9` | Legacy release notes link forward; old assets retained |
| Escha E3 (`escha-e3-with-mtp.gguf`) | `YourHighnessLA/L0xRE-27b-Low` on HF | Name map + SHA-256 identity preserved |

## Campaign record

The full release ledger (decisions, receipts, failures, rollback pointers) lives at
[`RELEASE-LEDGER.md`](RELEASE-LEDGER.md) in this repository.