# pathogenicity-llm-bench

Benchmarking large language models (LLMs) for somatic variant pathogenicity classification in cancer.

## Overview

This repository contains the evaluation pipeline, prompt templates, benchmark dataset metadata, and statistical analysis scripts accompanying the study:

> **Benchmarking large language models for classifying the pathogenicity of somatic variants in cancer**  
> Leqing Sang, Yunjin Wang, Yifeng Jiao, Sha Liu, Zhenzhen Niu, Tian Tang, Li Guo, and Ying Yu

We systematically evaluate **12 LLMs** spanning three functional categories across **840 curated somatic cancer variants** under the ClinGen/CGC/VICC standard operating procedure (SOP) framework:

- **Open-source general-purpose models**: Qwen3 series (`8B`, `14B`, `32B`, `235B`), GPT-OSS series (`20B`, `120B`), and `DeepSeek V3.2`
- **Proprietary general-purpose models**: `GPT-5.1`, `Gemini-3-pro-preview`, and `Kimi K2.5`
- **Domain-specific models**: `BioMedLM 2.7B` and `GeneGPT`
- **Rule-based benchmark**: [SVOC](https://svoc.premedkb.cn)

## Benchmark Datasets

1. **ClinGen/CGC/VICC Expert Consensus Dataset ($n = 94$)**: Expert-curated somatic variants with ground-truth evidence codes, numerical scores, and five-tier oncogenicity classifications (`Oncogenic`, `Likely Oncogenic`, `VUS`, `Likely Benign`, `Benign`).
2. **ClinVar Somatic Variant Dataset ($n = 746$)**: Real-world somatic variants annotated with clinical oncogenicity classifications extracted from `clinvar_20250217.vcf.gz`.

## Repository Structure

```text
pathogenicity-llm-bench/
├── data/                   # Input variant lists and ground-truth labels
├── prompts/                # Standardized Basic and ClinGen/CGC/VICC SOP prompt templates
├── scripts/
│   ├── inference/          # Batch inference scripts (Ollama, Hugging Face, and API clients)
│   ├── parsing/            # Output validation, evidence code extraction, and score parsing
│   └── analysis/           # R scripts for F1 metrics, correlation, and mixed-effects modeling
├── results/                # Summary tables and benchmark outputs
├── LICENSE                 # GNU General Public License v3.0 (GPLv3)
└── README.md
