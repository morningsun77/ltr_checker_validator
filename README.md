# ltr_checker_validator

**LTR_checker_validator: a quality control pipeline for intact LRT-RT validation**

## Overview

LTR_checker_validator is a comprehensive six-module validation procedure implemented into a Python pipeline that systematically evaluates structural integrity, temporal constraints, and functional features to retain only high-confidence intact LTR-RT. This Python pipeline sequentially implements: (Module 1) removal of gapped sequences, tandem repeats, and length validation; (Module 2) boundary refinement and target site duplication (TSD) verification; (Module 3) calculation of LTR divergence and filtering; (Module 4) protein domain identification and classification; (Module 5) Filtering LTR-RT with Non-LTR coding sequencescreening for overlapping transposable elements and plant protein domains; and (Module 6) Validation of nested insertion.

## Dependencies

**Python 3.9+** with the following main packages:
- PyTorch 1.11.0 (with CUDA support optional)
- Biopython 1.85+
- NumPy 1.24.3+
- Pandas 2.2.3+
- Matplotlib 3.9.4+
- Seaborn 0.13.2+
- Scikit-learn
- tqdm 4.67.1+

### External Tools

- **TRF (Tandem Repeats Finder) 4.10.0** - Tandem repeat detection
- **BLAST+ (RMBlast variant) 2.14.1+** - Sequence alignment and comparison
- **HMMER 3.4** - Protein domain annotation (hmmsearch)
- **EMBOSS 6.6.0.0** - Sequence analysis utilities
- **RepeatMasker 4.1.8** - Repeat sequence masking
- **LTR_FINDER 1.07** - LTR retrotransposon detection
- **GenomeTools 1.6.6** (includes LTR_HARVEST) - Alternative LTR retrotransposon detection
- **LtrDetector** - Additional LTR retrotransposon detection capabilities
- **MUSCLE 5.1.0**

### Database Files (Included)

- `REXdb_protein_database_viridiplantae_v3.0.hmm` - HMM profiles for plant LTR-RT protein domains
- `TEfam.hmm` - Transposable element family profiles
- `Tpases020812DNA.txt` and `Tpases020812LINE.txt` - Transposase reference sequences

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/ltr_checker_validator.git
cd ltr_checker_validator
```

### 2. Install Python Dependencies
```bash
conda create -n ltr_checker_validator python=3.9
conda activate ltr_checker_validator
pip install -r requirements.txt
```

### 3. Install External Tools

Ensure all external tools listed above are installed and accessible in your system path.

### 4. Prepare Database Files

Place the required HMM profiles and reference sequences in the `dataset/` directory.

## Usage

### Basic Command
```bash
python validator.py --genome input.fasta --output output_dir
```

### Command-Line Options
```
Required Arguments:
  --sequence SEQUENCE  input LTR-RTs sequences in fasta format [required]
  --genome GENOME      input genome in fasta format [required]
  --output OUTPUT      output directory path [required]

