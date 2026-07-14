# Usage Guide

## Getting Started

1. Open https://gopizux.github.io/AminoSeqIndex/ in a web browser
2. Paste or type your amino acid sequence into the input field (left panel)
3. The color-coded, indexed preview appears in real time
4. Select an output format from the right panel
5. Click **Export** to download as DOCX, or **Copy** to copy to clipboard

## Input Format

- Enter raw amino acid sequence using single-letter codes
- Accepted characters: A, C, D, E, F, G, H, I, K, L, M, N, P, Q, R, S, T, V, W, Y
- Case-insensitive (lowercase is converted to uppercase automatically)
- Spaces, numbers, and other characters trigger an error message and are rejected
- Sequences of any length are supported (tested up to 10,000+ residues)

## Output Formats

### Continuous
Single-line sequence with position numbers at 10-residue intervals:
```
        10        20        30
MISYAIASQM DDVIGDEDWP DVSRHWQHRL
        40        50        60
ELPRIQFPGS QRLSQVIAQA LVDKGYEVKH
```

### FASTA
Standard bioinformatics format, 60 characters per line:
```
>E. coli DHFR | MW: 17.9 kDa
MISYAIASQMDDVIGDEDWPDVSRHWQHRLELPRIQFPGSQRLSQVIAQALVDKGYEVKH
RILVRQGDEVFEDFVETRKPEAEQALLDPRIFAEIQALLGYPVIVHLAYRR
```

### Compact Grid
20 residues per row with position labels above each character:
```
 1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
 M  I  S  Y  A  I  A  S  Q  M  D  D  V  I  G  D  E  D  W  P
21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40
 D  V  S  R  H  W  Q  H  R  L  E  L  P  R  I  Q  F  P  G  S
```

### Numbered Table
Four-column layout with three-letter amino acid codes:
| Pos | AA | Pos | AA | Pos | AA | Pos | AA |
|-----|-----|-----|-----|-----|-----|-----|-----|
| 1 | Met | 2 | Ile | 3 | Ser | 4 | Tyr |
| 5 | Ala | 6 | Ile | 7 | Ala | 8 | Ser |

## DOCX Export

The exported Word document contains:
- Formatted sequence in the selected layout
- Molecular weight in kilodaltons
- Format description
- Monospace font for sequence display (Courier New or equivalent)

The document is ready for inclusion in reports, manuscripts, or lab notebooks without reformatting.

## Keyboard Shortcuts

- **Ctrl+V / Cmd+V**: Paste sequence into input field
- **Ctrl+A / Cmd+A**: Select all text in input field
- **Tab**: Move between input and format selection

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Error message "Invalid characters" | Remove spaces, numbers, or non-amino-acid characters from input |
| Sequence not appearing | Ensure the input field is not empty and contains valid amino acid codes |
| DOCX export not working | Try a different browser; ensure pop-ups are not blocked |
| Slow rendering for very long sequences | Sequences over 5,000 residues may take a few seconds to render; this is normal |
