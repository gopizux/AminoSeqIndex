# Refactoring Guide: Splitting into src/ Directory

This document describes an optional refactoring to improve code reviewability and maintainability by splitting the monolithic `index.html` into separate source files.

## Current Architecture

- **Single File**: `index.html` (~37 KB) containing all HTML, CSS, and JavaScript
- **Pros**: No build step, no dependencies, easy deployment to GitHub Pages
- **Cons**: Large single file, harder to review and maintain

## Proposed Architecture (Optional)

### File Structure

```
src/
├── index.html          # HTML structure only
├── style.css           # All CSS styles
└── app.js              # All JavaScript logic

build/
└── build.sh            # Build script to concatenate files

index.html              # Generated production file (git-ignored)
```

### Implementation Steps

#### Step 1: Extract HTML
Create `src/index.html` with structure only (no inline CSS/JS):
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AminoSeqIndex</title>
    <!-- CSS will be injected during build -->
</head>
<body>
    <!-- HTML structure -->
</body>
</html>
```

#### Step 2: Extract CSS
Create `src/style.css` with all stylesheet rules.

#### Step 3: Extract JavaScript
Create `src/app.js` with all JavaScript code.

#### Step 4: Create Build Script
Create `build/build.sh`:
```bash
#!/bin/bash

# Extract head section from HTML
HEAD=$(sed -n '/<head>/,/<\/head>/p' src/index.html | sed '/<\/head>/d')

# Start concatenating
echo '<!DOCTYPE html>' > index.html
echo '<html lang="en">' >> index.html
echo '<head>' >> index.html

# Include CSS inline
echo '<style>' >> index.html
cat src/style.css >> index.html
echo '</style>' >> index.html

# Include body and rest of HTML
sed -n '/<body>/,$p' src/index.html >> index.html

# Include JavaScript inline
echo '<script>' >> index.html
cat src/app.js >> index.html
echo '</script>' >> index.html

echo "Build complete! Generated index.html ($(wc -c < index.html) bytes)"
```

#### Step 5: Update Workflow
Modify `.github/workflows/ci.yml` to run build script before validation.

## Benefits

1. **Improved Reviewability**: Separate concerns make code easier to review in PRs
2. **Easier Maintenance**: Changes to CSS/JS don't require editing a massive HTML file
3. **Better Version Control**: Diffs are more meaningful when files are separated
4. **No Build Tool Overhead**: Simple shell script, no Node.js or npm required

## Drawbacks

1. **Extra Build Step**: Users must run build script before deployment
2. **Documentation Maintenance**: Need to document build process
3. **Complexity**: Slightly more complex project structure

## Alternative: PostCSS/Rollup (Not Recommended)

While tools like Rollup or PostCSS could automate the build, they would introduce:
- npm dependency
- Node.js requirement
- CI/CD complexity
- Harder onboarding for contributors

The simple shell script approach maintains the philosophy of minimal dependencies.

## Decision

This refactoring is **optional** and can be deferred:

- ✅ **If pursuing refactoring**: Implement simple shell build script, update CI/CD
- ⏸️ **If deferring**: Current single-file architecture is acceptable for now

The project was designed to be a "no build step" tool, so this remains an optional improvement rather than a necessity.

## References

- Current: `index.html` (monolithic)
- GitHub Pages compatible: ✅ (if deploying src/ directory or building before push)
- ZIP distribution: Can include both src/ and pre-built index.html
