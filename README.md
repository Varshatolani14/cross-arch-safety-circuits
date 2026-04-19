# cross-arch-safety-circuits

# 🏗️ Cross-Architecture Study of Safety Circuits

![GPT-2](https://img.shields.io/badge/GPT--2-gray?style=flat)
![Pythia](https://img.shields.io/badge/Pythia--160M-5C4EE5?style=flat)
![TinyLlama](https://img.shields.io/badge/TinyLlama--1.1B-teal?style=flat)
![AI Safety](https://img.shields.io/badge/AI%20Safety-coral?style=flat)

A comparative mechanistic interpretability study testing whether safety-relevant circuits are consistent across GPT-2-small, Pythia-160M, and TinyLlama-1.1B — examining generalizability of circuit findings across architectures and parameter scales.

---

## Overview

Building on refusal-circuit findings in GPT-2, this study asks: do safety-relevant circuits appear consistently across different model families and scales? This is a prerequisite for making confident claims about circuit-level alignment techniques.

## Models Studied

- **GPT-2-small** (117M) — baseline interpretability target
- **Pythia-160M** — same training corpus, different architecture details
- **TinyLlama-1.1B** — larger scale, grouped-query attention, RoPE embeddings

## Research Questions

- Do refusal circuits localize to similar layers across architectures?
- Is head-level ablation equally effective across model families?
- Do linear probes trained on one model transfer to another?
- How do architectural differences (GQA, RoPE, layer norm) affect circuit structure?

## Repository Structure

```
cross-arch-safety-circuits/
├── notebooks/
│   ├── 01_gpt2_baseline.ipynb
│   ├── 02_pythia_analysis.ipynb
│   ├── 03_tinyllama_analysis.ipynb
│   └── 04_cross_arch_comparison.ipynb
├── src/
│   ├── model_loader.py
│   ├── patching_utils.py
│   └── cross_arch_compare.py
├── configs/
│   ├── gpt2_config.yaml
│   ├── pythia_config.yaml
│   └── tinyllama_config.yaml
├── results/
│   └── cross_arch_summary.csv
└── README.md
```

## Setup

```bash
git clone https://github.com/Varshatolani14/cross-arch-safety-circuits
cd cross-arch-safety-circuits
pip install -r requirements.txt
```

## Usage

```bash
python src/patching_utils.py --model gpt2-small --config configs/gpt2_config.yaml
python src/patching_utils.py --model pythia-160m --config configs/pythia_config.yaml
python src/cross_arch_compare.py --output results/cross_arch_summary.csv
```

## Acknowledged Limitations

- All three models are small — findings may not transfer to frontier-scale systems
- Scaling trends and generalization gaps are ongoing work before strong claims
- Architectural differences (GQA, RoPE) make direct circuit comparisons non-trivial
- This is a work-in-progress; results should be treated as preliminary

## Citation

```bibtex
@misc{tolani2025crossarch,
  author = {Tolani, Varsha},
  title  = {Cross-Architecture Study of Safety Circuits},
  year   = {2025},
  url    = {https://github.com/Varshatolani14/cross-arch-safety-circuits}
}
```
