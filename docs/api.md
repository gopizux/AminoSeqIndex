# API Reference

AminoSeqIndex is a client-side web application. This document describes the internal JavaScript API for developers extending or embedding the tool.

## Global Functions

### `formatSequence(sequence, format)`
Formats an amino acid sequence into the specified output format.

**Parameters:**
- `sequence` (string): Raw amino acid sequence (single-letter codes)
- `format` (string): One of `'continuous'`, `'fasta'`, `'grid'`, `'table'`

**Returns:** Formatted string

### `calculateMolecularWeight(sequence)`
Calculates the molecular weight of a protein sequence.

**Parameters:**
- `sequence` (string): Raw amino acid sequence

**Returns:** Molecular weight in kilodaltons (number, 1 decimal place)

### `classifyResidue(aa)`
Returns the classification category for a single amino acid.

**Parameters:**
- `aa` (string): Single-letter amino acid code

**Returns:** One of `'nonpolar'`, `'polar'`, `'acidic'`, `'basic'`

### `validateSequence(input)`
Checks whether an input string contains only valid amino acid codes.

**Parameters:**
- `input` (string): Character string to validate

**Returns:** `{ valid: boolean, invalidChars: string[] }`

## Constants

### `RESIDUE_MASSES`
Object mapping single-letter amino acid codes to monoisotopic residue masses in Daltons.

```javascript
const RESIDUE_MASSES = {
  'A': 71.0788, 'C': 103.0092, 'D': 115.0269, 'E': 129.0426,
  'F': 147.0684, 'G': 57.0215,  'H': 137.0589, 'I': 113.0841,
  'K': 128.0950, 'L': 113.0841, 'M': 131.0405, 'N': 114.0429,
  'P': 97.0528,  'Q': 128.0586, 'R': 156.1011, 'S': 87.0320,
  'T': 101.0477, 'V': 99.0684,  'W': 186.2132, 'Y': 163.0633
};
```

### `CLASSIFICATION`
Object mapping single-letter codes to CSS class names.

```javascript
const CLASSIFICATION = {
  'A': 'nonpolar', 'V': 'nonpolar', 'L': 'nonpolar', 'I': 'nonpolar',
  'M': 'nonpolar', 'F': 'nonpolar', 'W': 'nonpolar', 'P': 'nonpolar',
  'G': 'nonpolar',
  'S': 'polar', 'T': 'polar', 'N': 'polar', 'Q': 'polar',
  'Y': 'polar', 'C': 'polar',
  'D': 'acidic', 'E': 'acidic',
  'K': 'basic', 'R': 'basic', 'H': 'basic'
};
```

## CSS Classes

The following classes are applied to residue spans for color coding:

| Class | Color | Usage |
|-------|-------|-------|
| `.category-nonpolar` | Orange (#E67E22) | Nonpolar residues |
| `.category-polar` | Blue (#3498DB) | Polar residues |
| `.category-acidic` | Red (#E74C3C) | Acidic residues |
| `.category-basic` | Green (#27AE60) | Basic residues |

## Embedding

To embed AminoSeqIndex in another page:

```html
<iframe src="https://gopizux.github.io/AminoSeqIndex/" 
        width="100%" height="600" 
        style="border: none;">
</iframe>
```

## External Dependencies

| Dependency | Version | Source | Purpose |
|-----------|---------|--------|---------|
| docx | 8.5.0 | jsDelivr CDN | DOCX file generation |
| Space Grotesk | - | Google Fonts | Heading font (optional) |
| JetBrains Mono | - | Google Fonts | Monospace font (optional) |
