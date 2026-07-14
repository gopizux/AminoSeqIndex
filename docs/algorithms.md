# Algorithm Description

## Positional Indexing

### Problem
Protein sequences are stored as continuous strings of single-letter amino acid codes. When sequences exceed ~50 residues, counting positions manually becomes error-prone. Existing tools either skip positional indexing entirely or require server-side computation.

### Approach
AminoSeqIndex calculates display width dynamically based on sequence length:

1. **Digit count**: Determine the number of digits in the largest position number (e.g., position 1234 requires 4 digits)
2. **Column padding**: Set uniform column width equal to the digit count, right-padding with spaces
3. **Interval placement**: In continuous format, insert a position label every 10 residues
4. **Grid layout**: In compact format, arrange 20 residues per row with labels above each position

### Pseudocode
```
function calculateColumnWidth(seqLength):
    maxPos = seqLength
    digits = floor(log10(maxPos)) + 1
    return digits

function formatContinuous(sequence):
    colWidth = calculateColumnWidth(sequence.length)
    header = generateIntervalLabels(colWidth, interval=10)
    lines = []
    for i = 0 to sequence.length step 60:
        chunk = sequence[i : i+60]
        numbered = addIntervalNumbers(chunk, i, colWidth)
        lines.append(numbered)
    return header + lines.join("\n")
```

### Complexity
- Time: O(n) where n is sequence length — single pass through the sequence
- Space: O(n) for the output string — no intermediate data structures larger than the input

## Amino Acid Classification

### Method
A lookup table maps each of the 20 standard amino acid single-letter codes to one of four categories:

| Category | Residues | Color | Hex |
|----------|----------|-------|-----|
| Nonpolar | A, V, L, I, M, F, W, P, G | Orange | #E67E22 |
| Polar | S, T, N, Q, Y, C | Blue | #3498DB |
| Acidic | D, E | Red | #E74C3C |
| Basic | K, R, H | Green | #27AE60 |

### Implementation
Each residue character is wrapped in a `<span>` element with a CSS class corresponding to its category:
```javascript
const CLASSIFICATION = {
  'A': 'nonpolar', 'V': 'nonpolar', 'L': 'nonpolar', ...
  'S': 'polar', 'T': 'polar', 'N': 'polar', ...
  'D': 'acidic', 'E': 'acidic',
  'K': 'basic', 'R': 'basic', 'H': 'basic'
};

function classify(aa) {
  return CLASSIFICATION[aa.toUpperCase()] || 'unknown';
}
```

CSS classes apply color without pre-rendering or canvas manipulation:
```css
.category-nonpolar { color: #E67E22; }
.category-polar    { color: #3498DB; }
.category-acidic   { color: #E74C3C; }
.category-basic    { color: #27AE60; }
```

## Molecular Weight Calculation

### Formula
```
MW = Σ(residue_mass_i) + 1.0078 + 17.0027 Da
```
Where:
- `residue_mass_i` = monoisotopic mass of residue i (from standard amino acid mass table)
- `1.0078 Da` = N-terminal hydrogen
- `17.0027 Da` = C-terminal hydroxyl group

### Standard Monoisotopic Residue Masses

| AA | Mass (Da) | AA | Mass (Da) |
|----|-----------|-----|-----------|
| A | 71.0788 | N | 114.0429 |
| C | 103.0092 | P | 97.0528 |
| D | 115.0269 | Q | 128.0586 |
| E | 129.0426 | R | 156.1011 |
| F | 147.0684 | S | 87.0320 |
| G | 57.0215 | T | 101.0477 |
| H | 137.0589 | V | 99.0684 |
| I | 113.0841 | W | 186.2132 |
| K | 128.0950 | Y | 163.0633 |
| L | 113.0841 | | |
| M | 131.0405 | | |

### Implementation
The calculation iterates through the sequence once, summing residue masses:
```javascript
function calculateMW(sequence) {
  let mw = 1.0078 + 17.0027; // N-term + C-term
  for (const aa of sequence.toUpperCase()) {
    mw += RESIDUE_MASSES[aa] || 0;
  }
  return (mw / 1000).toFixed(1); // Convert to kDa
}
```

## DOCX Export

### Method
AminoSeqIndex uses the `docx` JavaScript library (v8.5.0) loaded from jsDelivr CDN to generate Word documents client-side:

```javascript
import { Document, Packer, Paragraph, TextRun } from 'https://cdn.jsdelivr.net/npm/docx@8.5.0/+esm';

async function exportDocx(sequence, format, molecularWeight) {
  const doc = new Document({
    sections: [{
      children: [
        new Paragraph({
          children: [new TextRun({ text: `Sequence: ${sequence}`, font: 'Courier New' })]
        }),
        // ... formatted output
      ]
    }]
  });
  const blob = await Packer.toBlob(doc);
  saveAs(blob, 'AminoSeqIndex_Output.docx');
}
```

### Why CDN?
The `docx` library (~200 KB minified) is loaded from jsDelivr CDN to keep the total application size under 30 KB. If offline operation is required, the library can be bundled directly into `index.html` (increasing file size to ~230 KB).

## Performance Characteristics

| Sequence Length | Render Time | DOM Elements |
|----------------|-------------|--------------|
| 50 residues | <5 ms | ~200 |
| 300 residues | <10 ms | ~1,200 |
| 1,000 residues | ~20 ms | ~4,000 |
| 5,000 residues | ~100 ms | ~20,000 |
| 10,000 residues | ~200 ms | ~40,000 |

Measured on a mid-range laptop (Intel i5, Chrome 120). Rendering uses selective DOM updates rather than full re-renders, keeping the interface responsive even for very long sequences.
