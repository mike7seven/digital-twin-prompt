# Use Your Digital Twin With an AI Agent

The interview gives you a system prompt (Part B). This guide shows how to turn it into a digital twin inside an AI agent app.

Each app has a ready-made template in the [agents](agents/) folder. You copy the template to the right place on your computer, paste your system prompt into it, and start the app.

**Keep your filled-in file private.** It contains personal details. Save it only on your own computer, in the locations below. Never add it to a public project.

## Before you start

1. Finish the interview in [interview-prompt.md](interview-prompt.md) and copy **Part B** (your digital twin profile).
2. Pick your app below.
3. In the template, replace the line that starts with `<!--` with your Part B text. Leave everything above it as it is.

### Why the templates turn things off

These apps were built for programming, so by default they can run commands, change files, and browse the web. A digital twin should only talk. Each template turns those abilities off and adds a short note telling the AI it's a twin, not a coding assistant.

## Claude Code

Claude Code runs your twin as a **subagent**: a separate AI with its own instructions and limits.

1. Copy [agents/claude-code/digital-twin.md](agents/claude-code/digital-twin.md) to:
   ```
   ~/.claude/agents/digital-twin.md
   ```
   (`~` means your home folder.)
2. Open the file and paste in your Part B text.
3. Start Claude Code as your twin:
   ```
   claude --agent digital-twin
   ```
   The whole conversation is now your twin. In a normal Claude Code session, you can also type `@agent-digital-twin` followed by a message to hand that message to your twin.

**What the template sets:** `tools: Read` means your twin can only read files, not change them or run anything. `omitClaudeMd: true` keeps your other Claude Code project notes out of your twin's head.

## OpenCode

OpenCode runs your twin as a **primary agent**, which you can switch to at any time.

1. Copy [agents/opencode/digital-twin.md](agents/opencode/digital-twin.md) to:
   ```
   ~/.config/opencode/agents/digital-twin.md
   ```
2. Open the file and paste in your Part B text.
3. Start OpenCode and press **Tab** until the agent at the bottom says `digital-twin`.

**What the template sets:** `edit: deny`, `shell: deny`, and `webfetch: deny` mean your twin can't change files, run commands, or browse the web.

## Google Antigravity (agy)

Antigravity CLI (`agy`) is Google's successor to Gemini CLI. It supports **custom agents** that you can pick as your main agent.

1. Copy [agents/antigravity/digital-twin.md](agents/antigravity/digital-twin.md) to:
   ```
   ~/.gemini/config/agents/digital-twin.md
   ```
2. Open the file and paste in your Part B text.
3. Start `agy`, open the `/agents` panel, and choose `digital-twin`.

**What the template sets:** `tools: view_file` means your twin can only read files. `commandExecutionPolicy: "off"` blocks commands. `subagent: false` stops other agents from calling your twin in the background.

**Don't use `AGENTS.md` or `GEMINI.md` for your twin.** Antigravity reads those files in every session as project rules, so your twin's personality would leak into all your other work.

**Still on the old Gemini CLI?** Save your Part B text as `.gemini/system.md` in a folder of its own, then start it from that folder with `GEMINI_SYSTEM_MD=1 gemini`. This replaces Gemini CLI's built-in instructions completely, so the template's "you talk; you don't act" note should go at the top of that file too.

## Meta Muse

Muse is an app, not a tool you set up with files. There's no template for it, and as of October 2026 Meta doesn't document a custom-instructions feature.

**What you can do:**

1. In Muse's settings, give it a name, pick an avatar, and set how it communicates. Use the name and emoji from **Part A**.
2. Start a chat and paste your Part B text with this note in front:
   ```
   Please remember the profile below. Use it when you talk about me, and follow its rules, especially "Hand off to me when..." and "Never".
   ```

**Before you use Muse as a twin, know this:**

- **It acts, not just talks.** Muse can send emails and invitations, book travel, and make purchases for you. That goes further than the "mirror, not actor" idea behind this project, and your profile's rules are requests Muse may not always follow.
- **Privacy.** Muse learns from your conversations and keeps what it learns. Meta has said it plans to offer encryption but hasn't released it yet. Only share what you'd be comfortable with Meta keeping.

If you want strict limits, use Claude Code, OpenCode, or Antigravity, where the templates actually switch the risky abilities off.

## Sources

- [Claude Code subagents](https://code.claude.com/docs/en/sub-agents)
- [OpenCode agents](https://opencode.ai/docs/agents/)
- [Antigravity subagents (CLI)](https://antigravity.google/docs/subagents?tab=cli), [rules](https://antigravity.google/docs/rules/), and [Gemini CLI migration](https://antigravity.google/docs/cli/gcli-migration/)
- [Gemini CLI system prompt override](https://geminicli.com/docs/cli/system-prompt/)
- [TechCrunch: Meta debuts its Muse AI agent](https://techcrunch.com/2026/09/08/meta-debuts-its-muse-ai-agent-will-consumers-trust-it/) and [TIME: Meta's Muse AI agent and privacy](https://time.com/article/2026/10/06/meta-muse-ai-agent-privacy/)
