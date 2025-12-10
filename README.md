# repo2prompt

Convert any GitHub repository into LLM-ready context. No API keys, no rate limits, no dependencies.

## What it does

Paste a GitHub URL, get optimized output ready to paste into Claude, GPT, Gemini, or any other LLM. Smart filtering removes junk files, token counting shows compatibility with different models.

## Features

- **Zero setup** - Single HTML file, runs in browser
- **No API key needed** - Direct fetch from raw.githubusercontent.com
- **No rate limits** - Works unlimited times
- **Smart filtering** - Auto-excludes node_modules, lock files, build output, binaries
- **Gitignore support** - Respects .gitignore patterns
- **Multiple formats** - XML (Claude), Markdown (GPT), JSON, LLM-ready
- **Token counting** - Estimates tokens with model compatibility check
- **12 LLM models** - Context window comparison for Dec 2025 models
- **File browser** - Select/deselect individual files
- **Language stats** - Breakdown by programming language
- **Local history** - Recent repos saved in browser
- **URL sharing** - Share configurations via URL
- **Keyboard shortcuts** - Ctrl+Enter, Ctrl+C, Ctrl+S
- **Drag & drop** - Drop GitHub URLs directly

## Usage

1. Open `index.html` in browser
2. Paste GitHub URL or `owner/repo`
3. Click Convert
4. Copy output to your LLM

Or use the hosted version: [repo2prompt.vercel.app](https://repo2prompt.vercel.app)

## Filters

| Filter | Excludes |
|--------|----------|
| Dependencies | node_modules, vendor, .venv, __pycache__ |
| Lock files | package-lock.json, yarn.lock, pnpm-lock.yaml |
| Build output | dist, build, .next, target, coverage |
| Binary files | images, fonts, media, archives, executables |
| Test files | *.test.*, *.spec.*, __tests__ |
| Documentation | *.md, /docs |

Custom patterns supported. Whitelist mode available.

## Output Formats

**XML** - Optimized for Claude
```xml
<repository name="repo" owner="owner" branch="main">
  <file path="src/index.ts">
    // code here
  </file>
</repository>
```

**Markdown** - Works great with GPT, Gemini
```markdown
# owner/repo
## src/index.ts
\`\`\`ts
// code here
\`\`\`
```

**JSON** - Structured data
```json
{
  "repository": { "owner": "owner", "name": "repo" },
  "files": [{ "path": "src/index.ts", "content": "..." }]
}
```

**LLM** - Ready to paste prompt format

## Supported Models (Dec 2025)

| Model | Context |
|-------|---------|
| Gemini 2.5 Pro | 1M |
| Claude Sonnet 4.5 (1M) | 1M |
| Llama 4 Maverick | 1M |
| GPT-5 | 400K |
| Qwen3-Max | 256K |
| Claude Opus 4.5 | 200K |
| Claude Sonnet 4.5 | 200K |
| DeepSeek V3 | 128K |
| GPT-4o | 128K |
| Mistral Large 2 | 128K |

## Advanced Options

- **Subpath** - Target specific directories (`/src`, `/packages/core`)
- **Max file size** - Skip large files (default 100KB)
- **Max files** - Limit total files (default 200)
- **Target tokens** - Cap output at token limit
- **Line numbers** - Add line numbers to code
- **Compress** - Remove extra whitespace
- **Prioritize** - Important files first (README, package.json, index.*)

## Deploy

Single HTML file. Deploy anywhere:

**Vercel**
1. Push to GitHub
2. Import in Vercel
3. Set Output Directory to `.`
4. Deploy

**Netlify**
1. Drag & drop index.html

**GitHub Pages**
1. Enable Pages in repo settings

## Tech

- Pure HTML/CSS/JS
- No build step
- No dependencies
- ~2000 lines single file
- Works offline (after first load)

## License

MIT

---

by [vajbratya](https://github.com/Vajbratya)
