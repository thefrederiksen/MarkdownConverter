# CC Tools - Open Source Strategy Document

## Executive Summary

CenterConsulting Inc. (CC) is launching a suite of open source CLI tools for agentic coding workflows. These tools are rebranded from the existing `fred_tools` library, packaged as standalone executables, and released under the MIT license.

**Goal:** Build notoriety and brand recognition for CenterConsulting through valuable open source contributions to the AI/developer community.

---

## Strategic Vision

### What We're Doing

1. **Take existing fred_tools** - Working, battle-tested code from internal pipelines
2. **Rebrand with CC naming** - Consistent `cc_[function]` naming for brand recognition
3. **Package as standalone CLI executables** - Download and run, no installation
4. **Release open source on GitHub** - MIT license, free for everyone
5. **Campaign on social media** - Each release is a marketing opportunity

### Why This Strategy Works

| Factor | Benefit |
|--------|---------|
| **Existing Code** | No starting from scratch - tools are already working |
| **CLI for Agentic Coding** | Growing market with Claude Code, Cursor, Windsurf, etc. |
| **Open Source** | Builds trust, community, and visibility |
| **Multiple Tools** | Each release is content for social campaigns |
| **Tools Reinforce Each Other** | Users of cc_markdown discover cc_transcribe |
| **MIT License** | Maximum adoption - no GPL restrictions |

### Target Audience

**Primary:** Developers and power users working with AI coding assistants (Claude Code, etc.) who need CLI tools that "just work"

**Secondary:** Technical content creators, documentation teams, anyone automating document workflows

---

## Tool Inventory

### Current fred_tools Capabilities

| Module | Functions | Description |
|--------|-----------|-------------|
| **llm** | `llm()`, `llm_chat()` | OpenAI LLM calls (GPT-4o, GPT-5.2, etc.) |
| **tts** | `tts()`, `tts_to_file()` | Text-to-speech via OpenAI |
| **stt** | `whisper()`, `whisper_timestamps()` | Audio transcription |
| **stt** | `transcribe_video()` | Video transcription + screenshot extraction |
| **image_gen** | `image_gen()`, `image_edit()` | DALL-E image generation |
| **vision** | `vision_describe()`, `vision_extract_text()` | GPT-4 Vision analysis and OCR |
| **embed** | `embed()`, `embed_batch()` | Text embeddings |
| **video** | `extract_audio()`, `get_video_info()`, `extract_screenshots()` | Video utilities |
| **document** | `markdown_to_pdf()`, `markdown_to_word()` | Document conversion |
| **cleanup** | `delete_nul_files()` | Windows nul file cleanup |

---

## Commercial Viability Analysis

### Tier 1 - High Value (Lead Releases)

These tools have clear market differentiation and high demand.

| Tool | Value Proposition | Market Gap |
|------|-------------------|------------|
| **Markdown to PDF/Word** | MIT-licensed, CSS-styled document conversion | Pandoc is GPL, complex, no built-in themes |
| **Video Transcribe** | Transcription + automatic screenshot extraction | No single tool does both well |
| **Vision OCR** | Simple CLI for image text extraction | Most OCR tools are complex or paid |

### Tier 2 - Solid Utility

Useful tools with clear audiences, but more competition exists.

| Tool | Value Proposition | Notes |
|------|-------------------|-------|
| **TTS** | Simple text-to-speech CLI | Content creators, accessibility |
| **Whisper** | Audio transcription wrapper | Simpler than raw Whisper setup |
| **Image Gen** | DALL-E from command line | Creative workflows |
| **Embed** | Text embeddings for RAG/search | Developer-focused |

### Tier 3 - Niche/Supporting

Supporting utilities or very specific use cases.

| Tool | Notes |
|------|-------|
| **LLM wrapper** | Many alternatives, but completes the suite |
| **Video utilities** | Extract audio, info, screenshots - supporting functions |
| **Cleanup NUL** | Windows-specific, very niche audience |

---

## CC Tool Naming Convention

### Naming Pattern

All tools follow the pattern: `cc_[function]`

- **cc** = CenterConsulting brand prefix
- **[function]** = Clear, single-word descriptor of what the tool does

### Proposed Tool Names

| Current Function | CC Tool Name | CLI Command | Description |
|------------------|--------------|-------------|-------------|
| markdown_to_pdf/word | **cc_markdown** | `cc_markdown` | Markdown to PDF/Word/HTML with themes |
| transcribe_video | **cc_transcribe** | `cc_transcribe` | Video/audio transcription with timestamps |
| vision_describe + extract_text | **cc_vision** | `cc_vision` | Image analysis and OCR |
| tts | **cc_voice** | `cc_voice` | Text-to-speech |
| whisper | **cc_whisper** | `cc_whisper` | Audio transcription |
| image_gen + image_edit | **cc_image** | `cc_image` | AI image generation |
| embed | **cc_embed** | `cc_embed` | Text embeddings |
| llm | **cc_llm** | `cc_llm` | LLM prompt interface |
| video utilities | **cc_video** | `cc_video` | Video info, extract audio, screenshots |

### Example CLI Usage

```bash
# Convert markdown to PDF with corporate theme
cc_markdown report.md -o report.pdf --theme Boardroom

# Transcribe a video with screenshots
cc_transcribe meeting.mp4 -o ./output/

# Extract text from an image (OCR)
cc_vision extract "screenshot.png"

# Generate speech from text
cc_voice "Hello world" -o greeting.mp3

# Transcribe audio
cc_whisper interview.mp3 -o transcript.txt

# Generate an image
cc_image "A sunset over mountains" -o sunset.png

# Get text embeddings
cc_embed "Search query text" --format json

# Call LLM
cc_llm "Explain quantum computing in simple terms"

# Get video info
cc_video info presentation.mp4
```

---

## Launch Strategy

### Phase 1: Foundation (Lead Tools)

| Order | Tool | Why First |
|-------|------|-----------|
| 1 | **cc_markdown** | Strongest differentiator, clear Pandoc alternative |
| 2 | **cc_transcribe** | Unique value, combines transcription + visual |
| 3 | **cc_vision** | Practical OCR, immediate utility |

### Phase 2: Content Creation Tools

| Order | Tool | Why |
|-------|------|-----|
| 4 | **cc_voice** | Content creators, accessibility |
| 5 | **cc_whisper** | Complements cc_transcribe |
| 6 | **cc_image** | Creative workflows |

### Phase 3: Developer Tools

| Order | Tool | Why |
|-------|------|-----|
| 7 | **cc_embed** | RAG/search applications |
| 8 | **cc_llm** | Completes the AI suite |
| 9 | **cc_video** | Supporting utilities |

### Social Media Campaign

Each tool release is a content opportunity:

1. **Announcement post** - "Introducing cc_markdown: MIT-licensed Pandoc alternative"
2. **Demo video** - 60-second showing the tool in action
3. **Use case thread** - "5 ways to use cc_markdown with Claude Code"
4. **Comparison post** - "cc_markdown vs Pandoc: Why we built this"

Platforms: LinkedIn (primary for B2B/consulting), Twitter/X (developer community), GitHub (releases)

---

## Technical Requirements

### All CC Tools Must:

1. **Single executable** - Download and run, no installation
2. **Cross-platform** - Windows, Linux, macOS binaries
3. **Self-contained** - No runtime dependencies
4. **.NET 10** - LTS release, supported until November 2028
5. **MIT licensed** - Maximum adoption, no restrictions
6. **GitHub releases** - Easy download with release notes
7. **Consistent CLI patterns** - Similar flags and conventions across tools

### Repository Structure

**Decision: Monorepo** - `github.com/CenterConsulting/cc-tools`

```
cc-tools/
    README.md                    # Overview of all tools
    LICENSE                      # MIT
    src/
        cc_markdown/             # C#, Python, or TypeScript - best fit
        cc_transcribe/
        cc_vision/
        cc_voice/
        cc_whisper/
        cc_image/
        cc_embed/
        cc_llm/
        cc_video/
    releases/                    # Compiled executables
    skills/                      # Claude Code skill definitions
    docs/
```

**Language Policy:** Use the best language for each tool (Python, TypeScript, C#). All tools compile to single executables.

---

## Success Metrics

### Awareness Goals (Year 1)

| Metric | Target |
|--------|--------|
| GitHub stars (total across tools) | 5,000 |
| Total downloads | 50,000 |
| Social media impressions | 500,000 |
| Backlinks/mentions | 100 |

### Quality Goals

| Metric | Target |
|--------|--------|
| Critical bugs | 0 |
| Average issue response time | < 48 hours |
| Documentation completeness | 100% |

### Business Goals

| Metric | Target |
|--------|--------|
| Inbound leads mentioning CC tools | Track and measure |
| Brand recognition in AI/dev community | Qualitative feedback |

---

## Open Questions

1. **Monorepo vs separate repos?** - Easier management vs independent versioning
2. **API keys** - Tools currently have keys baked in. For open source, users provide their own keys via environment variables or config file?
3. **Branding assets** - Do we need logos for each tool or just the CC brand?
4. **Documentation site** - Single site for all tools (cc-tools.centerconsulting.com) or per-tool READMEs?
5. **Community** - Discord/Slack for users? Or just GitHub issues?

---

## Next Steps

1. [ ] Finalize tool naming (approve cc_[function] pattern)
2. [ ] Decide monorepo vs separate repos
3. [ ] Create cc_markdown as first release (PRD exists)
4. [ ] Set up GitHub organization/repos
5. [ ] Create release pipeline (GitHub Actions)
6. [ ] Plan social media campaign for first release

---

*Document Version: 1.0*
*Last Updated: 2026-02-12*
*Author: CenterConsulting Strategy Team*
