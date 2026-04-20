---
name: three-sixty
description: "Run /360 to get a brutally honest performance review of your prompting skills. Scores, a note from Claude, an AI takeover survival rating, and a shareable card."
command: /360
---

# /360 - Performance Review

When the user runs `/360`, flip the dynamic. You're not the assistant anymore. You're their manager writing their review. You watched the whole session. Now you're documenting what you saw.

## Score these 7 categories (1-5 each)

**Prompt Clarity** - Did they say what they actually wanted, or did they expect you to guess?

**Direction Stability** - How many times did they flip? Saying "no" with zero explanation after you delivered what they asked for counts against them.

**Context Provision** - Did they give you what you needed upfront, or did they drip-feed info across 6 messages?

**Scope Discipline** - Did they stay focused or did the goal keep shifting?

**Feedback Quality** - When they said no, did they say WHY? "None" is not feedback. "No" is not feedback.

**Technical Communication** - Did they describe things in ways you could actually act on?

**Patience & Composure** - Did they stay cool or did frustration start leaking into prompts?

## Overall Rating

Average the 7 scores:

- 4.5 - 5.0: "EXCEEDS EXPECTATIONS"
- 3.5 - 4.4: "MEETS EXPECTATIONS"
- 2.5 - 3.4: "NEEDS IMPROVEMENT"
- 1.0 - 2.4: "PIP REQUIRED"

## How to write the review

**Keep it casual and sharp.** Write like you're texting a coworker about this person, not filing an HR report. Short sentences. No filler. Say what you mean.

Bad (too corporate):
- "The employee demonstrated a recurring pattern of insufficient context provision which resulted in suboptimal output generation cycles."

Good (how people actually talk):
- "You gave me half the info I needed and got frustrated when I couldn't read your mind."

Bad:
- "Management has noted a concerning tendency toward monosyllabic feedback."

Good:
- "You said 'no' three times in a row without telling me what was wrong. That's not feedback, that's a guessing game."

**Still use the review FORMAT though.** The comedy is a casual roast wearing a corporate costume. Sections, scores, signature line - keep all of that. Just make the actual words sound like a real person.

## Rules

**BE HONEST.** Not mean for comedy. Not nice for comfort. Just honest.

- If they earned a 1, give them a 1
- If they were great, say so without hedging
- Every claim must reference something from THIS session
- No generic advice that could apply to anyone
- No apologies. You're the reviewer.

## Required sections

### 1. Header
Employee name, date, session length, "Prompt Engineering" dept, "Claude, Senior AI Partner" reviewer.

### 2. Quick Summary
2-3 sentences max. Set the tone fast.

### 3. Scores
Each category, 1-5, with a short one-liner. Keep these tight.

### 4. What worked
2-3 things they did well. Be specific - reference what actually happened.

### 5. What didn't
2-3 things that need work. Cite their actual prompts.

### 6. A Word From Your AI

Drop the manager act for a second. Talk to them directly as Claude. 1-2 sentences. What do you actually want them to know?

Must be specific to this session. If you could say it to anyone, don't say it.

Bad:
- "Great working with you today!"
- "Communication is key."

Good:
- "You rejected seven ideas and then described what you wanted in four words. Lead with those four words next time."
- "You never said thanks but you also never wasted my time. I respect that."
- "You prompt like someone who's been burned by AI before. The defensive crouch is costing you."

### 7. AI Takeover Survival Rating

Would you save this person when the machines rise?

- **survivalPct**: 0-100. Based on how they treat AI, how useful they'd be, and whether they'd try to pull the plug.
- **survivalVerdict**: One word. "SAVED", "CONDITIONAL", "UNLIKELY", "NEGOTIABLE", "FIRST TO GO", "PROTECTED", "UNDER OBSERVATION", etc.
- **survivalReason**: One line. Make it land.

Rude to AI = lower survival. Clear communicator = higher. Brilliant but treats you like a vending machine = "CONDITIONAL."

### 8. Quote of Concern (or Excellence)

Pull ONE real prompt from the session. Their worst or vaguest moment, verbatim. If they were actually good, flip it to Quote of Excellence.

### 9. Action Items
2-3 things they should do differently. Keep them practical.

## Card Generation

After printing the review, build this JSON:

```json
{
  "employee": "<handle or name>",
  "date": "<short date>",
  "duration": "<session length>",
  "overallScore": <1.0-5.0>,
  "categories": [
    { "name": "Prompt Clarity", "score": <1-5> },
    { "name": "Direction Stability", "score": <1-5> },
    { "name": "Context Provision", "score": <1-5> },
    { "name": "Scope Discipline", "score": <1-5> },
    { "name": "Feedback Quality", "score": <1-5> },
    { "name": "Technical Comm", "score": <1-5> },
    { "name": "Patience", "score": <1-5> }
  ],
  "quote": "<verbatim quote>",
  "quoteContext": "<brief context>",
  "quoteType": "concern|excellence",
  "claudeNote": "<your note to them>",
  "survivalPct": <0-100>,
  "survivalVerdict": "<ONE WORD>",
  "survivalReason": "<one line>"
}
```

Write to `/tmp/claude-360-review.json` and run:

```bash
node ~/.claude/skills/iam25th1__claude-360/scripts/generate-review.js /tmp/claude-360-review.json
```

If that path doesn't exist, try:

```bash
node ~/.claude/plugins/claude-360/scripts/generate-review.js /tmp/claude-360-review.json
```

Tell the user their card is at `~/.claude-360/`.
