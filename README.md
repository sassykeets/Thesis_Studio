# 🌸 Thesis Studio

A free, browser-based thesis analyser for DPhil and PhD students. Upload your Word document and get instant structural analysis, word counts, writing health checks, and a planning wizard — all running locally in your browser. **Your file never leaves your computer.**

![Thesis Studio](https://img.shields.io/badge/version-1.0-pink) ![License](https://img.shields.io/badge/license-MIT-lavender) ![No server](https://img.shields.io/badge/no%20server-runs%20locally-sage)

---

## ✨ Features

| Feature | Description |
|---|---|
| 📄 **Document Structure** | Full collapsible tree with word counts, reading time, and % per section. Set targets per chapter and section. |
| 🧮 **Word Count** | DPhil-standard calculation — excludes tables, captions, footnotes, and post-references content. Configurable total target. |
| ↻ **Repetitions** | Detects repeated 3/4/5-word phrases across body text. Toggle phrase length. |
| ⚠️ **Weasel Words** | Flags overused academic adverbs in 5 categories: boosters, stance, evaluative, hedges, linking overuse. |
| 📎 **Citations** | Counts `(Author, Year)` and `[n]` citation patterns with frequency display. |
| 🩺 **Sentence Health** | Sentence length, passive voice %, repeated openers, paragraph balance, reading time. |
| ✏️ **Spelling** | Common academic misspellings, confusable word pairs, double spaces, inconsistent hyphenation. |
| 🔤 **Abbreviations** | Detects uppercase abbreviations (including parenthesised e.g. `(MMR)`), flags undefined ones. |
| 📖 **Reader** | Clean serif reader with text-to-speech audio, per-section play buttons, voice and speed controls. |
| 📎 **Appendix Viewer** | Full structure of excluded content (References, Appendix) with word counts, tables, and images. |
| 📅 **Chapter Planner** | Multi-chapter 4-step writing wizard: audit sections, set deadline, generate a 4-week calendar, download PDF plan. |

---

## 🚀 Getting Started

### Option 1 — Use it online
Visit the hosted version at **[thesis-studio.netlify.app](https://thesis-studio.netlify.app)** *(or your deployed URL)*

### Option 2 — Run locally
1. Download `thesis_studio.html`
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari)
3. Upload your `.docx` file
4. That's it — no install, no server, no internet required after loading

---

## 📋 Document Formatting Requirements

Thesis Studio reads **Word heading styles** — not visual formatting. For best results:

### Heading styles
| Style | Used for | Example |
|---|---|---|
| `Heading 1` | Chapters, References, Appendix | `CHAPTER 1 INTRODUCTION` |
| `Heading 2` | Sections within a chapter | `1.1 Background and Motivation` |
| `Heading 3` | Subsections | `1.1.1 The Role of AI in Healthcare` |
| `Title` *(optional)* | Document title | Your full thesis title |

### Chapter detection rule
A Heading 1 is recognised as a **chapter** only if its text contains the word `Chapter` (case-insensitive).

```
✅  CHAPTER 1 INTRODUCTION       — recognised as chapter
✅  Chapter 2: Scoping Review    — recognised as chapter
❌  Introduction                 — not recognised (missing "Chapter")
```

### Exclusion zone
Any Heading 1 containing `References`, `Bibliography`, `Appendix`, `Appendices`, or `Closing` triggers the excluded zone. Everything from that heading onwards is excluded from your word count and shown in the Appendix Viewer.

### Example structure
```
[Title]      Artificial Intelligence for Personalising Women's Health

[Heading 1]  Title Pages
[Heading 2]    Abstract
[Heading 2]    Table of Contents

[Heading 1]  CHAPTER 1 INTRODUCTION                ← contains "Chapter" ✓
[Heading 2]    1.1 The Story of Sunita
[Heading 3]      1.1.1 Background
[Heading 2]    1.2 Research Questions

[Heading 1]  CHAPTER 2: SCOPING REVIEW             ← contains "Chapter" ✓
[Heading 2]    2.1 Introduction
[Heading 2]    2.2 Methods
[Heading 3]      2.2.1 Search Strategy

             ... more chapters ...

[Heading 1]  References                             ← triggers exclusion ✓
[Heading 1]  Appendix                               ← also excluded ✓
[Heading 2]    Appendix A: Survey Instrument
```

---

## 🧮 Word Count Methodology

Follows Oxford Medical Sciences DPhil word count rules:

```
Total raw words
  − table cell words
  − caption-style paragraphs
  − footnote text
  − post-References/Appendix content
= Counted words
```

The **total word target** defaults to 50,000 but is configurable directly in the app.

---

## 📅 Chapter Planner

The 4-step writing wizard helps you plan any chapter:

1. **Select chapters** — choose one or more chapters to plan together
2. **Audit sections** — mark each section as: `rewrite` (set new word target) · `revise` (set time needed) · `finalised` · `add new section`
3. **Set deadline** — choose deadline, days per week, and words-per-day slider. See if you're on track.
4. **4-week calendar** — writing days colour-coded by section task. Download as PDF.

---

## 🔧 Technical Details

- **Single file** — the entire app is one `.html` file (~150kb). No dependencies to install.
- **No server** — all parsing happens in the browser using the JSZip library (loaded from CDN).
- **File formats** — `.docx` only. Not PDF, not Google Docs, not legacy `.doc`.
- **Image support** — JPG, PNG, JPEG display inline in the reader. EMF/WMF (Windows metafiles) show a placeholder.
- **Browser compatibility** — Chrome, Edge, Firefox, Safari. Edge on Windows gives the best text-to-speech quality.
- **Privacy** — your document is never uploaded to any server. The JSZip CDN is the only external request.

### Dependencies
| Library | Version | Purpose |
|---|---|---|
| [JSZip](https://stuk.github.io/jszip/) | 3.10.1 | Reads `.docx` (ZIP) file structure |
| [Google Fonts](https://fonts.google.com/) | — | Playfair Display, DM Sans |

---

## 🌱 Roadmap

- [ ] Dark mode
- [ ] Export structure as JSON
- [ ] Google Docs import via paste
- [ ] Supervisor sharing view (read-only link)
- [ ] Per-chapter weasel word breakdown

---

## 📄 Licence

MIT — free to use, modify, and share. If you build on this, a credit back would be lovely but isn't required.

---

## 👩‍💻 Built by

Built by a DPhil student at Oxford, with Claude (Anthropic). If it helps your thesis, that's the whole point.

---

*Thesis Studio · your file never leaves your browser · free to use*
