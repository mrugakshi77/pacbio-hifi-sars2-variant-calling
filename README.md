# PacBio SARS-CoV-2 HiFi Variant Calling Pipeline

## Overview

A complete, production-quality bioinformatics pipeline for analyzing **real PacBio HiFi sequencing data** of SARS-CoV-2 to detect and characterize viral variants from clinical surveillance samples.

## Key Features

- Supports **single-sample real data analysis** for high-coverage PacBio HiFi viral amplicons.
- Reference genome alignment (**minimap2**, asm20 preset)
- QC and visualizations includes read length distributions, cumulative sequencing depth, and coverage calculation.
- Uses **Longshot** for PacBio-aware SNP calling on haploid viral genomes.    
- Variant comparison against PacBio reference VCFs, with metrics:
  - Total variants  
  - SNP/indel breakdown  
  - Concordance with PacBio calls  
- Fully reproducible with **pixi**
  
---

## Example Figures

- **pacbio_analysis_summary.png** – QC and pipeline summary for simulated reads  
- **pacbio_hifi_real_summary.png** – QC and pipeline summary for real sample  
- **variant_positions_comparison.png** – Longshot vs PacBio reference variant positions along the genome  
- **snp_density_comparison.png** – SNP density comparison (Longshot vs PacBio)  

---

## Data Source

**PacBio Official HiFiViral Dataset** (Jan 2022).
To download the full PacBio HiFiViral dataset:
1. Visit: https://downloads.pacbcommunity.org/public/dataset/HiFiViral/Jan_2022/
2. Download `samples.hifi_reads.fastq.zip`
3. Extract to `reads/hifi_samples/`

## Quick Start

### Prerequisites
- pixi (package manager)
- Jupyter notebook
- ~2 GB disk space (for full dataset)

### Installation
```bash
git clone https://github.com/mrugakshi77/pacbio-hifi-sars2-variant-calling.git
cd pacbio-hifi-sars2-variant-calling
pixi install
pixi shell
jupyter notebook
```

### Run the Pipeline

Open either notebook:
1. `01_pacbio_viral_variant_calling.ipynb` - Simulated SARS-CoV-2 workflow
2. `02_pacbio_real_data_analysis.ipynb` - Real PacBio HiFi data analysis

## Pipeline Steps

### 1. Data Preparation
- Download reference genome (NC_045512.2)
- Obtain PacBio HiFi reads from FASTQ files
- Quality filtering

### 2. Alignment
- Align with minimap2 (asm20 preset for PacBio HiFi)
- Generate sorted, indexed BAM files
- Coverage statistics

### 3. Variant Calling
- Call variants using bcftools
- Alternative: Longshot (long-read optimized)
- Generate VCF files

### 4. Analysis & Visualization
- Variant statistics and quality metrics
- Coverage analysis
- Multi-panel summary figures

## Key Results

### Sample: A_1055745 (Real Omicron Sample)
```
Input Data:
- 129,915 PacBio HiFi reads
- Mean length: 668 bp
- Total coverage: 2902x

Alignment:
- Reference: SARS-CoV-2 NC_045512.2
- High-confidence coverage

Variants:
- SNPs detected
- Indels characterized
- Variant annotations
```

## Project Structure
```
pacbio_project/
├── 01_pacbio_viral_variant_calling.ipynb    # Simulated data workflow
├── 02_pacbio_real_data_analysis.ipynb       # Real HiFi data analysis
├── README.md                                 # This file
├── pixi.toml                                 # Dependencies
├── reference/                                # Reference genomes
│   └── sars2_reference.fasta
├── reads/                                    # Input sequencing data
│   └── hifi_samples/                         # Real PacBio HiFi samples
├── aligned/                                  # BAM alignment files
├── variants/                                 # VCF variant calls
└── results/                                  # Analysis outputs & plots
```

## Tools Used

| Tool | Version | Purpose |
|------|---------|---------|
| minimap2 | 2.30+ | Long-read alignment |
| samtools | 1.23+ | BAM processing |
| bcftools | 1.23+ | Variant calling |
| Longshot | - | HiFi-optimized variant caller |
| Python | 3.9+ | Analysis & visualization |

## Skills Demonstrated

- PacBio long-read sequencing analysis
- Real clinical viral data processing
- NGS quality control workflows
- Variant detection & characterization
- Bioinformatics pipeline development
- Data visualization
- Reproducible research practices

## Applications

This pipeline can be applied to:
- COVID-19 variant surveillance
- Viral genome sequencing
- Structural variant detection
- Any viral long-read sequencing project

Conducted by Mrugakshi Chidrawar,

Bioinformatician | M.S. in Bioinformatics, Boston University
