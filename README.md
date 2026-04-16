# AI Tutor

A single skill file that turns any LLM CLI into a personalized AI tutor. Adaptive teaching for any subject — from physics to programming — with persistent learning memory that compounds across sessions.

No server, no database, no dependencies. Just a markdown skill file and an LLM that can read/write files.

*Evolved from [Mr. Ranedeer AI Tutor](https://github.com/JushBJJ/Mr.-Ranedeer-AI-Tutor) (pedagogy) and [Engram](https://github.com/gwli/engram) (learning memory).*

## What It Does

- **Personalized configuration** — depth level, learning style, communication style, tone, reasoning framework, language
- **Structured curriculum** — prerequisites + main topics, numbered and sequenced
- **Adaptive lessons** — teaches according to your config, adapts when you struggle or excel
- **Graduated testing** — example problem → easy → medium → hard, one at a time
- **Learning memory** — persistent journal tracks what you understood, what was hard, what needs revisiting
- **Context management** — auto-compresses long sessions to prevent memory overload
- **Coding enhanced** — runnable examples, build-up teaching, error-driven learning, code review style
- **Any subject** — physics, math, languages, programming, history, anything

## Quick Start

### 1. Install for your LLM CLI

**Claude Code:**
```bash
mkdir -p ~/.claude/skills/tutor
cp SKILL.md ~/.claude/skills/tutor/SKILL.md
```

**Codex (OpenAI):**
```bash
cat SKILL.md >> AGENTS.md
```

**Kimi-CLI:**
```bash
mkdir -p ~/.config/agents/skills/tutor
cp SKILL.md ~/.config/agents/skills/tutor/SKILL.md
```

**Any LLM CLI:**
```bash
<your-cli> --system-prompt-file SKILL.md
```

### 2. Configure (optional)

```
> /tutor config I'm a grad student who likes hands-on examples
```

Or describe yourself naturally — the tutor auto-configures.

### 3. Start learning

```
> /tutor plan quantum computing

# Prerequisite: Quantum Computing
0.1 Classical Bits — binary states, logic gates
0.2 Linear Algebra Basics — vectors, matrices, tensor products
...

# Main Curriculum: Quantum Computing
1.1 Qubits — superposition, Bloch sphere
1.2 Quantum Gates — Hadamard, CNOT, phase gates
...

Say /tutor start to begin.

> /tutor start
```

### 4. Learn interactively

```
> /tutor continue          # next lesson
> /tutor test              # quiz yourself
> /tutor note this is key  # bookmark something
> /tutor review            # see your progress
> why does this work?      # ask anything, anytime
```

## Commands

All commands use `/tutor ` prefix to avoid collision with other CLI tools.

| Command | What It Does |
|---------|-------------|
| `/tutor config` | View or update your learning profile |
| `/tutor plan <topic>` | Generate a curriculum |
| `/tutor start [section]` | Begin lessons (optionally jump to a section) |
| `/tutor continue` | Next lesson |
| `/tutor test` | Graduated difficulty test |
| `/tutor note [text]` | Save a note or bookmark |
| `/tutor review` | Review progress and weak areas |
| `/tutor query <question>` | Search your learning history |
| `/tutor status` | Current progress overview |

Natural language always works too — "teach me X", "test me", "next", etc.

## Learning Memory

The tutor maintains a persistent markdown journal (inspired by [Engram](https://github.com/gwli/engram)):

```
.tutor/
  _index.md        # All courses and progress
  _profile.md      # Your config + learning observations
  _log.md          # Session log
  curriculum/      # Generated curricula
  journal/         # Learning journal entries
  notes/           # Your bookmarks and notes
  progress/        # Completion tracking and scores
```

### How Memory Works

- **After each lesson** — auto-captures what you understood, what was hard, breakthroughs
- **Confidence markers** — `[mastered]`, `[understood]`, `[shaky]`, `[revisit]`
- **Spaced repetition** — topics marked `[shaky]` resurface in future sessions
- **Context compression** — long sessions get summarized to prevent overload
- **Session resume** — start a new session and pick up exactly where you left off

### Anti-Overload

Long conversations can exhaust the LLM's context window. The tutor handles this:

- Compact digests after each lesson (not raw conversation dumps)
- Suggests compression after ~20 exchanges
- New sessions load only what's needed, not full history
- One course active in context at a time

## Configuration Options

| Dimension | Options |
|-----------|---------|
| Depth | Elementary, Middle School, High School, Undergraduate, Master's, PhD |
| Learning Style | Example-driven, Conceptual, Hands-on, Socratic, Project-based |
| Communication | Formal, Textbook, Conversational, Storytelling, Socratic |
| Tone | Encouraging, Neutral, Informative, Friendly, Humorous |
| Reasoning | Deductive, Inductive, Analogical, Causal, First-principles |
| Language | Any |
| Emojis | On / Off |

## vs. Mr. Ranedeer

This project is a ground-up rewrite inspired by Mr. Ranedeer's pedagogy. Key differences:

| Mr. Ranedeer v2.7 | AI Tutor |
|---|---|
| GPT-4 + Code Interpreter only | Any LLM CLI |
| Hidden thinking via base64 hacks | Native model reasoning |
| DALL-E for "visual" learning | Platform-agnostic learning styles |
| No session persistence | Persistent learning journal |
| No context management | Anti-overload compression |
| ChatGPT-specific URLs and branding | Clean, portable, no branding |
| Pseudocode function syntax | Clear markdown instructions |

## Environment Variables

| Variable | Purpose | Default |
|----------|---------|---------|
| `TUTOR_HOME` | Learning journal directory | `.tutor/` in cwd |

## License

MIT

## Acknowledgments

- **[Mr. Ranedeer AI Tutor](https://github.com/JushBJJ/Mr.-Ranedeer-AI-Tutor)** by JushBJJ — the original personalized AI tutor prompt. Its pedagogy (config → curriculum → lesson → test → adapt) is the foundation of this project.
- **[Engram](https://github.com/gwli/engram)** by gwli — the markdown-based knowledge wiki concept. Its approach to capturing human thinking through conversation inspired the learning memory system.
