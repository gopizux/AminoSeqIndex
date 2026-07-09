# AminoSeqIndex

A lightweight, browser-based bioinformatics tool for annotating protein sequences with positional indices and color-coded amino acid classification. Solves the pain point of navigating long, unindexed FASTA sequences by adding clear numerical markers and visual categorization for rapid residue identification and mutation design.

## Table of Contents

- [Features](#features)
- [Use Cases](#use-cases)
- [Color-Coding System](#color-coding-system)
- [Supported Output Formats](#supported-output-formats)
- [Quick Start](#quick-start)
- [Browser Compatibility](#browser-compatibility)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features

- **Multiple Output Formats**: Continuous, FASTA, Compact Grid (20 residues/row), and Table view
- **Color-Coded Amino Acids**: Instant visual categorization for rapid identification
  - Nonpolar (orange): A, V, L, I, M, F, W, P, G
  - Polar (blue): S, T, N, Q, Y, C
  - Acidic (red): D, E
  - Basic (green): K, R, H
- **Intelligent Numbering**: Dynamic alignment for sequences of any length (1 to 10,000+ residues)
- **One-Click Export**: Copy annotated sequences to clipboard or export to DOCX format
- **Zero Dependencies**: Runs entirely in your browser, no installation or server required
- **Lightweight**: Single HTML file, no external libraries needed

## Use Cases

| User Type | Application |
|-----------|-------------|
| **Researchers** | Rapidly identify residue positions for site-directed mutagenesis experiments |
| **Students** | Learn amino acid properties with visual color-coding assistance |
| **Bioinformaticians** | Annotate sequences for documentation or sharing with collaborators |
| **Lab Technicians** | Prepare sequence references for experimental design and primer ordering |
| **Protein Engineers** | Navigate and plan modifications in large protein sequences |

## Color-Coding System

| Color | Category | Amino Acids | Properties |
|-------|----------|-------------|------------|
| **Orange** | Nonpolar | A, V, L, I, M, F, W, P, G | Hydrophobic, aliphatic or aromatic |
| **Blue** | Polar | S, T, N, Q, Y, C | Hydrophilic, often involved in H-bonding |
| **Red** | Acidic | D, E | Negatively charged at physiological pH |
| **Green** | Basic | K, R, H | Positively charged at physiological pH |

## Supported Output Formats

| Format | Description | Use Case |
|--------|-------------|----------|
| **Continuous** | Single-line uppercase sequence with positional indices | Quick reference, copy-paste to other tools |
| **FASTA** | Standard bioinformatics format with annotated header | Submission to databases, pipeline input |
| **Compact Grid** | 20 amino acids per row with position numbering and color-coding | Manual annotation, visual inspection |
| **Table** | Detailed position-by-position breakdown with amino acid properties | Documentation, detailed analysis |

## Contributing

Bug reports and feature requests are welcome! Please contact:

- **Primary Contact**: gopizux@gmail.com
- **Secondary Contact**: vrkrishna70@gmail.com

For collaboration inquiries, please reach out via email. Note: This project has specific licensing restrictions—please review the [LICENSE](LICENSE) file before contributing or forking.

## License

This tool is released under a custom license. All rights reserved © 2026 Gopi Malagasi.

**Key Points**:
- ✅ Allowed: Educational, research, and personal non-commercial use
- ❌ Prohibited: Commercial use, redistribution, modification for redistribution
- ❌ Prohibited: Uploading to other platforms without explicit permission

For the full license text and permission requests, see the [LICENSE](LICENSE) file.

## Contact

For permissions, collaborations, bug reports, or questions:

- **Primary**: gopizux@gmail.com
- **Secondary**: vrkrishna70@gmail.com

---

**AminoSeqIndex** - Making protein sequence navigation faster and more intuitive.
