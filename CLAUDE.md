# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a collection of single-file HTML tools—standalone applications combining HTML, JavaScript, and CSS that require no build steps, no servers, and no frameworks.

## Tool Creation Guidelines

### Structure

Every tool must be a **single HTML file** with inline CSS and JavaScript:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tool Name</title>
    <style>
        /* All CSS inline */
    </style>
</head>
<body>
    <!-- UI here -->
    <script>
        // All JavaScript inline
    </script>
</body>
</html>
```

### Rules

1. **No React, Vue, or build-step frameworks** - Use vanilla JS or lightweight libraries loaded from CDNs
2. **No npm, no bundlers, no compilation** - Tools must work by opening the HTML file directly
3. **External libraries via CDN only** - Use unpkg, cdnjs, or esm.sh
4. **Keep it small** - Aim for a few hundred lines max; complexity defeats the purpose
5. **Mobile-friendly** - Include viewport meta tag, use responsive CSS

### Recommended Patterns

**State persistence:**
- Use URL query parameters for shareable/bookmarkable state
- Use `localStorage` for API keys and user preferences
- Never send secrets to servers

**Common features:**
- Copy-to-clipboard buttons for output
- Drag-and-drop file upload where applicable
- Download results as files when useful
- Clear visual feedback for actions

**Libraries worth using (via CDN):**
- [Pico CSS](https://picocss.com/) - Minimal classless CSS
- [DOMPurify](https://github.com/cure53/DOMPurify) - HTML sanitization
- [Marked](https://marked.js.org/) - Markdown parsing
- [Pyodide](https://pyodide.org/) - Python in browser (for computation-heavy tools)

### File Naming

Use kebab-case descriptive names: `json-formatter.html`, `base64-encoder.html`, `color-picker.html`

### Testing

Open the HTML file directly in a browser. No build step means no test runner—manual verification is expected.

## Development Workflow

1. Describe what the tool should do
2. Claude creates the single HTML file
3. Open in browser to test
4. Iterate until complete
5. Commit with descriptive message

## Deployment

Tools can be hosted on GitHub Pages. Once pushed to main, they're accessible at:
`https://{username}.github.io/tools/{tool-name}.html`
