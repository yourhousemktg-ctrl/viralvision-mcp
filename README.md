# ViralVision MCP

**Give Claude eyes on any social video — YouTube, Instagram, TikTok, Twitter/X, Facebook, and more.**

Built by [Marc Illy](https://www.marcillyaiplaybook.it.com) · Free forever · MIT License

---

## What it does

Paste any social video URL into Claude Code. Claude downloads it, extracts frames, and can now see and analyze every second of the video — all from inside your Claude Code chat.

**No API keys needed beyond your Anthropic subscription.**

```
You: vv_watch https://www.tiktok.com/@garyvee/video/123456789

Claude: [watches 47 frames across the 52-second video]

"This TikTok opens with a question hook at 0:02:
'Do you know what the #1 skill for 2026 is?'

The middle section (0:15-0:35) shows B-roll of the office + cuts to
face cam. The CTA at 0:48 is 'link in bio' pointing to a course..."
```

---

## Tools included

| Tool | What it does | Speed |
|---|---|---|
| `vv_watch` | Download + extract frames from any URL. Claude sees every frame. | 10-30s |
| `vv_info` | Get video metadata without downloading (title, views, hashtags, creator) | 2-3s |
| `vv_transcript` | Extract captions/transcript without downloading the video | 3-5s |
| `vv_setup` | Check your installation and see supported platforms | Instant |

---

## Install in 3 steps

### Step 1 — Install dependencies

**macOS:**
```bash
brew install yt-dlp ffmpeg
```

**Windows:**
```bash
winget install yt-dlp.yt-dlp && winget install Gyan.FFmpeg
```

**Linux:**
```bash
sudo apt install ffmpeg && pip install yt-dlp
```

### Step 2 — Install the MCP server

```bash
git clone https://github.com/yourhousemktg-ctrl/viralvision-mcp
cd viralvision-mcp
npm install && npm run build
```

### Step 3 — Add to Claude Code

Run this command to add it to your Claude Code config:

```bash
claude mcp add viralvision-mcp node /path/to/viralvision-mcp/dist/index.js
```

Or add manually to `~/.claude/claude.json`:

```json
{
  "mcpServers": {
    "viralvision-mcp": {
      "command": "node",
      "args": ["/path/to/viralvision-mcp/dist/index.js"]
    }
  }
}
```

Restart Claude Code. Type `vv_setup` to verify it's working.

---

## Usage examples

### Analyze a competitor's TikTok
```
vv_watch https://www.tiktok.com/@[username]/video/[id]
```
→ Claude describes the hook, pacing, B-roll usage, CTA, and hashtag strategy

### Get a YouTube video summary without watching it
```
vv_transcript https://www.youtube.com/watch?v=dQw4w9WgXcQ
```
→ Full transcript with timestamps in seconds

### Reverse-engineer a viral Instagram Reel
```
vv_watch https://www.instagram.com/reel/[id]/
```
→ Claude spots every cut, text overlay, and transition

### Research without watching
```
vv_info https://www.youtube.com/watch?v=[id]
```
→ Title, creator, views, likes, hashtags, description — in 2 seconds

---

## Supported platforms

| Platform | Video type | Notes |
|---|---|---|
| YouTube | All videos, Shorts | Auto-captions extracted automatically |
| Instagram | Reels, posts | Public only |
| TikTok | All videos | Watermark-free extraction |
| Twitter / X | Video tweets | Public posts |
| Facebook | Public videos | Public posts only |
| Reddit | v.redd.it | Gallery support too |
| Local files | MP4, MOV, AVI, MKV, WebM | Full local file support |

---

## License

MIT — use it, fork it, ship it. Credit appreciated but not required.

---

*Built by Marc Illy · [AI Playbook 2026](https://www.marcillyaiplaybook.it.com) — the exact workflows I use to run my business with AI.*
