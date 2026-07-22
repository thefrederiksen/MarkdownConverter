# MarkdownConverter - Product Requirements Document

## Executive Summary

**MarkdownConverter** is an MIT-licensed CLI tool that transforms Markdown into professionally styled PDF, Word, and HTML documents. Download the executable, run a command, get a beautiful document.

### The Problem

LLMs generate excellent Markdown content daily - sales documents, pitches, reports, documentation. Users need to convert this to professional formats with consistent styling. Current solutions are either:

- **Too complex** - Pandoc is a Swiss-army knife with steep learning curve
- **Wrong license** - Pandoc is GPL (copyleft), blocking commercial and MIT-licensed projects
- **Poor styling** - CSS only works for HTML; Word requires template files

### The Solution

A focused CLI tool:
- Single executable download from GitHub
- CSS-based styling for all output formats
- 7 beautiful built-in themes
- Works perfectly with Claude Code and agentic workflows

---

## Target Audience

### Primary: Agentic/CLI Users

People using Claude Code, automation scripts, or command-line workflows who need to convert Markdown to polished documents. They want:

```bash
mdconvert report.md -o report.pdf --theme Boardroom
```

That's it. No library integration, no code, no configuration files.

### Secondary: Anyone with Markdown

Technical writers, developers, business users who have Markdown and need PDF/Word/HTML output with professional styling.

---

## Competitive Analysis

| Feature | Pandoc | MarkdownConverter |
|---------|--------|-------------------|
| License | GPL v2 (copyleft) | MIT (permissive) |
| Language | Haskell | C# |
| Learning Curve | Steep | One command |
| Word Styling | Reference doc templates | CSS |
| Built-in Themes | None | 7 themes |
| Distribution | Complex install | Single executable |

---

## Architecture

### Conversion Pipeline

```
Markdown --> HTML (with CSS) --> Output Format
                                    |
                                    +--> PDF
                                    +--> Word (.docx)
                                    +--> HTML (standalone)
```

### Why HTML as Intermediate

1. CSS is the natural styling language
2. Single styling system for all outputs
3. Well-understood rendering model

---

## Functional Requirements

### FR-1: Markdown Parsing

- CommonMark specification
- GitHub Flavored Markdown extensions:
  - Tables
  - Task lists
  - Strikethrough
  - Fenced code blocks with syntax highlighting

### FR-2: Output Formats

**PDF:**
- High-fidelity CSS rendering
- Page size: A4, Letter
- Configurable margins

**Word (.docx):**
- Valid Office Open XML
- CSS styles mapped to Word styles
- Headings, lists, tables, code blocks, images

**HTML:**
- Standalone file with embedded CSS
- Valid HTML5

### FR-3: Styling System

**Built-in themes** (7 at launch):

| Theme | Vibe |
|-------|------|
| Boardroom | Corporate, executive, serious |
| Terminal | Technical, monospace, dark-friendly |
| Paper | Minimal, clean, elegant |
| Spark | Creative, colorful, energetic |
| Thesis | Academic, scholarly, serif |
| Obsidian | Dark theme, subtle highlights |
| Blueprint | Technical documentation |

**Custom CSS:**
- Use `--css` flag to apply custom stylesheet
- CSS applies to all output formats
- Users can save custom CSS files as their own "templates"

### FR-4: CLI Interface

```bash
# Basic conversion (format detected from extension)
mdconvert input.md -o output.pdf
mdconvert input.md -o output.docx
mdconvert input.md -o output.html

# With built-in theme
mdconvert input.md -o output.pdf --theme Boardroom

# With custom CSS
mdconvert input.md -o output.pdf --css mystyle.css

# List available themes
mdconvert --themes

# Show version
mdconvert --version

# Help
mdconvert --help
```

**That's the entire interface.** Simple.

---

## Non-Functional Requirements

### NFR-1: Distribution

- **Single executable** - Download and run, no installation
- **GitHub Releases** - Precompiled binaries for Windows, Linux, macOS
- **.NET 10** - LTS release, supported until November 2028
- **Self-contained** - No .NET runtime required on target machine

### NFR-2: Performance

- Convert typical document (10-50 pages) in under 5 seconds
- No external dependencies at runtime

### NFR-3: Quality

- Unit tests for parsing and conversion
- Integration tests for each output format
- Visual spot-checks for themes

---

## Technical Decisions

### Framework
- **.NET 10** (LTS)
- Single-file publish with self-contained deployment

### Markdown Parser
- **Markdig** - MIT licensed, CommonMark + GFM support

### PDF Generation
- **Playwright** or **PuppeteerSharp** for headless Chromium
- OR **QuestPDF** for native PDF (evaluate tradeoffs)

### Word Generation
- **Open XML SDK** - Direct .docx generation

### Syntax Highlighting
- **Markdig.SyntaxHighlighting** or embed Prism.js CSS

---

## Out of Scope for V1

These are explicitly NOT in v1:

- Library/NuGet package (CLI only)
- Table of contents generation
- Cover pages
- Headers/footers with page numbers
- Custom fonts embedding
- Math/LaTeX rendering
- Mermaid diagrams
- Batch processing
- Watch mode
- More than 7 themes

These can be added in v2 based on user feedback.

---

## Deliverables

1. **GitHub Repository** - MIT licensed, open source
2. **CLI Executable** - `mdconvert` (or `mdconvert.exe` on Windows)
3. **GitHub Releases** - Precompiled binaries:
   - Windows x64
   - Linux x64
   - macOS x64
   - macOS ARM64
4. **README** - Quick start, CLI usage, theme gallery
5. **7 Theme CSS Files** - Embedded in executable

---

## Success Criteria

V1 is successful when:

1. User can download single executable from GitHub
2. User can run `mdconvert doc.md -o doc.pdf --theme Boardroom`
3. Output PDF looks professional and matches the theme
4. Same works for Word and HTML
5. Custom CSS works via `--css` flag
6. Works on Windows, Linux, macOS

---

## Open Questions

1. **PDF engine** - Playwright (high fidelity, large) vs QuestPDF (smaller, less CSS support)?
2. **Executable size** - Acceptable size for single-file distribution?
3. **Theme preview** - Should `--themes` show previews or just list names?

---

*Document Version: 2.0*
*Last Updated: 2026-02-12*
*Status: Draft - Simplified for V1*
