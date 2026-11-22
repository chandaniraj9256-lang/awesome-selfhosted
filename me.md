# My Claude Code Toolkit: Skills, Tools and Credit-Saving Notes

Project goal: **YouTube GTA mission tutorial videos.** First a 30-second Short with a voiceover, captions and motion text. If I like it, a long video comes next.

---

## 1. Skills (call with `/skill-name`)

| Skill | What it does | Useful for my videos? |
|---|---|---|
| `motion-reel:motion-reel` | Motion videos made from code: animated text, captions, music, sound effects, voiceover, vertical 9:16 and square 1:1 cuts | ✅ **Main one.** Use it to make the Short |
| `dataviz` | Charts and graphs | Only for stats videos |
| `artifact-design` | Design rules for web pages and artifacts | Thumbnail or landing-page mockups |
| `artifact-diagramming` | Diagrams | Mission step diagrams |
| `artifact-capabilities` | Interactive page features | Rarely |
| `anthropic-skills:deep-research` | Researches a topic across many sources and writes a report | Mission guides, trending topics (uses a lot of credits) |
| `anthropic-skills:docs` | Editable shareable documents | Scripts, video plans |
| `anthropic-skills:docx` / `pdf` / `pptx` / `xlsx` | Word, PDF, PowerPoint and Excel files | Scripts and content calendars |
| `anthropic-skills:google-workspace` | Edit Google Docs, Sheets and Slides | Content tracker in Sheets |
| `anthropic-skills:built-in-browser` / `chrome-browser` | Control a browser | Looking at reference videos |
| `anthropic-skills:computer-use` | Control your desktop apps | Opening editors on your PC |
| `anthropic-skills:skill-creator` | Make your own custom skill | ✅ Could make a "GTA Short" skill to reuse |
| `loop` | Repeat a task on a timer | Rarely |
| `run` | Launch an app | Rarely |
| `code-review`, `simplify`, `security-review`, `init` | Coding helpers | Not for videos |
| `update-config`, `keybindings-help`, `fewer-permission-prompts` | Claude Code settings | ✅ `fewer-permission-prompts` saves time |
| `claude-api` | Claude API reference | Only if building an app |
| `session-start-hook`, `plugin-authoring` | Advanced setup | No |

> ⚠️ **There is no "yt-dlp" skill.** yt-dlp is a separate program (see section 3).

---

## 2. Tools Claude uses

**Files and commands**
- `Bash`: runs commands such as ffmpeg and Python
- `Read`, `Write`, `Edit`: open, create and change files
- `Glob`, `Grep`: find files and text

**Video and audio (in the cloud machine)**
- `ffmpeg` ✅ installed: cuts, joins, adds captions, mixes audio, exports MP4
- `Playwright` / Chromium ✅ installed: renders motion graphics into frames
- `yt-dlp` ❌ not installed, and YouTube is **blocked** on this cloud network
- A voice engine ❌ not installed here. **Google Text-to-Speech API is reachable**, so a Google API key will work

**Sharing and output**
- `SendUserFile`: sends you the finished video
- `Artifact`: publishes a web page (previews, plans)

**Other**
- `WebSearch`, `web-fetch`: look things up online
- `Agent`: helper agents (⚠️ uses many credits)
- `AskUserQuestion`: asks you to choose an option
- GitHub tools: save work to your repo

---

## 3. yt-dlp (video downloader)

Free program that downloads video and audio from YouTube and more than 1,000 other sites.

**Install (on YOUR computer):**
```bash
pip install yt-dlp
# also needs ffmpeg: https://ffmpeg.org
```

**Useful commands:**
```bash
yt-dlp "URL"                                         # download a video
yt-dlp -f "bestvideo[height<=1080]+bestaudio" "URL"  # 1080p max
yt-dlp -x --audio-format mp3 "URL"                   # audio only
yt-dlp --download-sections "*1:00-1:30" "URL"        # only 1:00–1:30
yt-dlp --write-subs --sub-langs en "URL"             # with subtitles
yt-dlp -F "URL"                                      # list available qualities
```

**Why it can't run in the Claude cloud session:** the network blocks youtube.com.
**Workaround:** download or record the clip on your PC, then upload it to the chat.

⚠️ **Copyright:** re-uploading another creator's video can get a **copyright strike** or a Content ID claim. Record your **own gameplay**. Rockstar generally allows that.

---

## 4. Voice options

| Option | Cost | Status |
|---|---|---|
| Google Cloud Text-to-Speech (your API key) | Free tier, then paid | ✅ Works here. Give the key through the secure form, **never paste it in chat** |
| Record your own voice and upload it | Free | ✅ Best for building a channel identity |
| Free voices (gTTS, edge-tts, Piper) | Free | ❌ Blocked on this cloud network. Fine on your PC |

---

## 5. How to save credits 💰

1. **Write clear, complete requests.** Include the game, the mission, the length, the voice and the style in one message. Fewer back-and-forths means fewer credits.
2. **Upload your own clip.** Claude won't waste credits searching or failing downloads.
3. **Short first, long later.** That's the plan already, and it's smart.
4. **Avoid `deep-research` and `Agent`** unless needed. They use the most credits.
5. **Reuse what works.** Once you like a Short, turn the steps into a custom skill with `skill-creator` so the next one costs less.
6. **Use `/fewer-permission-prompts`** to cut approval clicks.
7. **Do heavy downloads on your PC** with yt-dlp and ffmpeg. They cost nothing there.
8. **Start a new session for a new project.** A long chat history costs more per message.
9. **Save files to GitHub.** Cloud sessions get deleted, so commit what you want to keep.

---

## 6. Workflow for the GTA Short (30 seconds)

1. Record a GTA first-mission clip on your PC (OBS, Xbox Game Bar or PS Share button).
2. Upload it to the chat and say which game and mission.
3. Claude writes a 30-second script with the steps for the mission.
4. Voice: Google TTS (key through the secure form) or your own recording.
5. `motion-reel` and `ffmpeg` add captions, motion text and arrows, and export a **9:16 vertical MP4**.
6. You review it. If it's good, make the long video the same way.
