# Voice to Blog Post

Record a voice note on WhatsApp, and the agent transcribes it into a fully formatted blog post — tech, travel, or thought.

---

## The Problem

Typing long posts on a phone is painful. You have thoughts while walking, commuting, or cooking — but by the time you sit down to write, the moment is gone.

## The Solution

Send a voice note. The agent does the rest.

```
📱 You (WhatsApp)
│
│  🎤 "Hey, so I just figured out something cool about
│      Flink watermarks. Basically the problem is late
│      arriving events in stream processing..."
│      (3 min voice note)
│
▼
🤖 Agent:
│  1. Transcribes voice → text (Whisper / Claude)
│  2. Detects content type (tech post)
│  3. Structures into sections with headings
│  4. Adds code blocks if you mention code
│  5. Generates title, tags, metadata
│
▼
📝 Draft ready:
│  "Understanding Flink Watermarks — A Deep Dive"
│
│  Agent: "Here's what I got from your voice note.
│          Want me to publish, or tweak anything?"
│
▼
✅ Published at lpatil.dev/blog/flink-watermarks
```

---

## Use Cases

### Tech Post via Voice
Talk through a concept you just learned. The agent structures it into a proper blog post with headings, code blocks, and diagrams.

### Travel Post via Voice
Narrate your day while walking around a new city. The agent extracts stops, times, food mentions, and builds the interactive timeline.

### Quick Thought via Voice
A 15-second voice note becomes a thought post. Zero friction.

---

## How It Should Work

1. **Transcription** — Convert voice to raw text (Whisper API or Claude's native audio)
2. **Cleanup** — Remove filler words (um, uh, like), fix grammar, keep the casual tone
3. **Structure** — Detect content type and organize into sections
4. **Enrich** — Add code formatting, links, emphasis where appropriate
5. **Confirm** — Send back a summary for approval before publishing
6. **Publish** — Same flow as text-based posts (markdown → git push → Cloudflare Pages)

---

## Voice-Specific Challenges

| Challenge | Solution |
|-----------|----------|
| Filler words (um, uh, like) | Strip during cleanup, keep natural tone |
| Code references ("use map dot filter") | Detect and format as inline/block code |
| Ambiguous punctuation | Use context to infer sentence breaks |
| Multiple topics in one note | Split into separate posts or ask user |
| Background noise | Rely on Whisper's noise handling |
| Long rambling notes | Summarize and ask user to confirm structure |

---

## Multi-Voice-Note Flow

Sometimes one voice note isn't enough. The agent should handle a series:

```
You: 🎤 (voice note 1 — intro to the topic)
You: 🎤 (voice note 2 — the deep dive)
You: 🎤 (voice note 3 — conclusion + takeaways)

Agent: "Got all 3 notes. Here's the combined post structure:
        1. Intro — what watermarks are
        2. Deep dive — how they handle late events
        3. Takeaways — when to use them

        Ready to publish?"
```

---

## Tech Options

| Option | Pros | Cons |
|--------|------|------|
| **Whisper API** | Best transcription quality, handles accents | Extra API cost |
| **Claude native audio** | Single tool, no extra service | Availability, quality TBD |
| **On-device (iOS Shortcuts)** | Free, private | Requires shortcut setup |

---

## Future Enhancements

- [ ] Real-time transcription — see text appear as you speak
- [ ] Speaker detection — multi-person podcast-style posts
- [ ] Tone detection — adjust writing style based on how you sound (excited, reflective, technical)
- [ ] Auto-language — detect language and post in that language
- [ ] Voice commands — "delete that last paragraph", "make the title shorter"
