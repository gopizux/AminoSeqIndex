# AminoSeqIndex

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21355340.svg)](https://doi.org/10.5281/zenodo.21355340)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A lightweight, browser-based bioinformatics tool for annotating protein sequences with positional indices and color-coded amino acid classification. Solves the pain point of navigating long, unindexed FASTA sequences by adding clear numerical markers and visual categorization for rapid residue identification and mutation design.

**Live tool**: https://gopizux.github.io/AminoSeqIndex/

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Use Cases](#use-cases)
- [Color-Coding System](#color-coding-system)
- [Supported Output Formats](#supported-output-formats)
- [Dependencies](#dependencies)
- [Browser Compatibility](#browser-compatibility)
- [Example Sequence Attribution](#example-sequence-attribution)
- [Citing This Software](#citing-this-software)
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
- **Zero Installation**: Runs entirely in your browser, no server required
- **Privacy-First**: All computation is client-side — sequence data never leaves your machine

## Quick Start

1. Open https://gopizux.github.io/AminoSeqIndex/ in any browser
2. Paste your amino acid sequence into the input field
3. View the color-coded, indexed preview in real time
4. Select an output format and export

No installation. No account. No server calls.

## Use Cases

| User Type | Application |
|-----------|-------------|
| **Researchers** | Identify residue positions for site-directed mutagenesis experiments |
| **Students** | Learn amino acid properties with visual color-coding |
| **Bioinformaticians** | Annotate sequences for documentation or sharing with collaborators |
| **Lab Technicians** | Prepare sequence references for experimental design |
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
| **Continuous** | Single-line sequence with positional indices at 10-residue intervals | Quick reference, copy-paste |
| **FASTA** | Standard format with annotated header, 60 chars/line | Database submission, pipeline input |
| **Compact Grid** | 20 amino acids per row with position numbering | Manual annotation, visual inspection |
| **Table** | Four-column layout with position numbers and three-letter codes | Documentation, lab notebooks |

## Dependencies

AminoSeqIndex is designed as a single-file application with minimal external dependencies:

### Runtime Dependencies (CDN-based)
- **docx@8.5.0**: Loaded from jsDelivr CDN (`https://cdn.jsdelivr.net/npm/docx@8.5.0/build/index.umd.js`) for DOCX file generation. All sequences are processed locally; the library is only used for file export.
- **Google Fonts** (optional): Space Grotesk (headings) and JetBrains Mono (monospace sequence display). These degrade gracefully if offline — the tool functions fully without them.

### Architecture
All core functionality (HTML, CSS, JavaScript) is bundled in a single `index.html` file (~37 KB) with zero build step or package manager required. No NPM dependencies are needed for development or deployment.

### Privacy & Security
- All sequence processing occurs **locally in your browser**
- Sequence data never leaves your machine
- Tool works offline after initial page load (except DOCX export requires docx library)

## Browser Compatibility

Tested and working in:
- Google Chrome 90+
- Mozilla Firefox 90+
- Apple Safari 14+
- Microsoft Edge 90+

Any modern browser with ES6 support should work.

## Example Sequence

The default example sequence in the tool is *Escherichia coli* dihydrofolate reductase (DHFR), UniProt P0A4I5. This sequence is used for demonstration purposes only and is in the public domain.

## Citing This Software

If you use AminoSeqIndex in your work, please cite:

```bibtex
@software{malagasi_aminoseqindex_2026,
  author       = {Gopi Malagasi, Ramakrishna Vadde},
  title        = {AminoSeqIndex: A Client-Side Web Tool for Color-Coded Protein Sequence Indexing and Export},
  year         = {2026},
  publisher    = {GitHub},
  url          = {https://gopizux.github.io/AminoSeqIndex/},
  repository   = {https://github.com/gopizux/AminoSeqIndex},
  version      = {1.0.1},
  doi          = {10.5281/zenodo.21355340}
}
```

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

© 2026 Gopi Malagasi

## Contact

- **Issues**: [GitHub Issues](https://github.com/gopizux/AminoSeqIndex/issues)
- **Email**: gopizux@gmail.com
