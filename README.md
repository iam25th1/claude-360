# Claude-360

**Claude reviews YOUR performance.**

A Claude Code skill that flips the dynamic. Instead of you evaluating Claude's output, Claude evaluates your input. You get a brutally honest, corporate-style 360 performance review of your prompting skills -- complete with category scores, a personal note from your AI, and whether Claude would save you in the robot uprising.

Every review is unique. Every review is honest. No participation trophies.

## What You Get

**7 scored categories** - Prompt Clarity, Direction Stability, Context Provision, Scope Discipline, Feedback Quality, Technical Communication, Patience & Composure

**Overall rating** - from "Exceeds Expectations" down to "PIP Required" (Performance Improvement Plan)

**A Word From Your AI** - Claude breaks character to tell you what it actually thinks. Specific to you. Specific to this session.

**AI Takeover Survival Rating** - A percentage chance Claude would advocate to save you when the machines rise. Based on how you treat AI, how useful your skills are, and whether you seem like you'd pull the plug.

**Quote of Concern** - Your single worst prompt, pulled verbatim and framed in an HR document. Or if you were good: Quote of Excellence.

**Shareable card** - Square HTML card optimized for screenshots and Twitter posts. Dark terminal aesthetic. One screenshot, one tweet.

## Install

```bash
claude skills add iam25th1/claude-360
```

### Optional: Plugin mode (adds idle nudge)

If you want Claude to nudge you with `run /360 if you're brave enough.` when it goes idle:

```bash
git clone https://github.com/iam25th1/claude-360.git ~/.claude/plugins/claude-360
```

Plugin mode includes the same skill plus a notification hook. The skill install is all most people need.

## Usage

At any point during or at the end of a session:

```
/360
```

Claude analyzes the full session, prints your review in the terminal, then generates a shareable HTML card at `~/.claude-360/`.

## Demo

Generate a sample card to see the format:

```bash
git clone https://github.com/iam25th1/claude-360.git
cd claude-360
npm run demo
```

## How It Works

1. You run `/360`
2. Claude reads the entire session history
3. Claude becomes your manager and conducts a performance review
4. Every claim references your actual prompts and behavior
5. A JSON review is generated and passed to the card generator
6. An HTML card is saved to `~/.claude-360/` and opens in your browser
7. You screenshot it and post it

## The Rules

The reviews follow strict rules to stay honest:

- Every score must be justified with evidence from the session
- No score inflation. A 1 is a 1.
- No generic language. If the review could apply to someone else, it's wrong.
- No apologies. Claude is the reviewer. The reviewer does not apologize.
- The Quote of Concern is always verbatim. Your words, in an HR document.

## Project Structure

```
claude-360/
  skills/
    360/
      SKILL.md              # Core skill (loaded by claude skills add)
  .claude-plugin/
    plugin.json             # Optional plugin manifest + idle nudge hook
  commands/
    360.md                  # Slash command reference
  scripts/
    generate-review.js      # HTML card generator
  sample-review.json        # Demo data
  package.json
  README.md
```

## Contributing

PRs welcome. Two rules:

1. Keep it honest. The reviews must be brutal when earned and kind when earned. Never default to mean for comedy. Never default to nice for comfort.
2. Keep it corporate. The humor lives in the gap between the absurd format and the radical honesty. If either side breaks, the joke dies.

## License

MIT

---

Built by [@25thprmr](https://twitter.com/25thprmr)
