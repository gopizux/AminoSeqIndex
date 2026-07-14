# Version Management

This document outlines versioning practices and known version-specific issues for AminoSeqIndex.

## Current Versions

### v1.0.1 (Latest)
- **Status**: Current production release
- **Date Released**: 2026-07-14
- **Git Tag**: `v1.0.1`
- **DOI**: [10.5281/zenodo.21355340](https://doi.org/10.5281/zenodo.21355340)

### v1.0.0
- **Status**: Initial stable release
- **Git Tag**: `v1.0.0`

## Known Issues

### v1.0.1 Release Artifacts

The v1.0.1 release zip file available on GitHub Releases may be missing the `google-site-verification` meta tag that is present in the current `main` branch. This occurs when release artifacts are created before code updates are finalized.

**Status**: To be fixed in next release
**Workaround**: Use the latest `main` branch for the most up-to-date version with all meta tags

### Version Consistency

When updating version numbers:
1. Update `CITATION.cff` with new version and date
2. Update `README.md` if release notes are needed
3. Create a git annotated tag: `git tag -a v1.x.x -m "Release v1.x.x - Description"`
4. Push tag to GitHub: `git push origin v1.x.x`
5. Create a release on GitHub with updated artifacts

## Semantic Versioning

AminoSeqIndex follows [Semantic Versioning](https://semver.org/):

- **MAJOR** (1.0.0): Breaking changes or major new features
- **MINOR** (1.1.0): New features, backward compatible
- **PATCH** (1.0.1): Bug fixes and patches

## Release Process

### Before Release

- [ ] Update version in `CITATION.cff`
- [ ] Update date in `CITATION.cff` to current date
- [ ] Update DOI if registering new Zenodo release
- [ ] Test across all supported browsers
- [ ] Run CI/CD validation

### Creating Release

```bash
# Create annotated tag
git tag -a v1.x.x -m "Release v1.x.x - Description of changes"

# Push tag to GitHub
git push origin v1.x.x

# Create release on GitHub with downloadable artifacts
```

### Zenodo Registration

When registering a new release on Zenodo:
1. Upload the `index.html` file
2. Fill in metadata matching `CITATION.cff`
3. Obtain DOI
4. Update `CITATION.cff` with new DOI
5. Commit and push update

## Citation

For consistent citation, refer to `CITATION.cff` which provides metadata for automatic citation generation in various formats.

Example BibTeX citation:

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
