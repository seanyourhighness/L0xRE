# L0xRE release ledger

The canonical model name is **L0xRE-27b-Low**. The runtime is **L0xRE BeeLLama**.

## Current destinations

- [Runtime installation, downloads and tests](https://github.com/seanyourhighness/L0xRE-BeeLLama-Low#readme)
- [Model card and files](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low)
- [Separate prediction-block checkpoint](https://huggingface.co/YourHighnessLA/L0xRE-27b-Low-MTP)
- [EXLLAMA Offload runtime](https://github.com/seanyourhighness/L0xRE-EXLLAMA-Offload)

## Universal runtime milestone

The release provides one Linux/WSL archive and one Windows ZIP with SM86/SM89/SM120 architecture coverage, targeting12GB GPU VRAM. Source commit `be302741801080a4fa2ea713fdf9409e2ef599d5` contains the recent SM86 and Windows changes. Model weights are unchanged.

Four CPU regression tests,11 Linux and9 Windows launcher cases passed. The Windows package passed70 PE-file and4,835 local-import checks. Archive hashes, clean extraction and GitHub asset digests were verified. The canonical runtime page links exact manifests and receipts.

Windows GPU inference and the current SM120 model path still await hardware qualification. Published Linux measurements apply to their specific model/runtime/GPU configurations. The universal runtime remains a release candidate.

## Public naming and model-card update

The model card explains the main model, optional drafter, download sizes, required runtime, installation, measured GPU configurations and qualification limits. Public model descriptions consistently use L0xRE-27b-Low. Technical provenance follows exact file hashes.
