# Security-Friction

A Claude Code skill that reintroduces human judgment into AI-assisted work by pausing at moments of uncertainty, contradiction, and irreversibility.

---

## Why this exists

Carl von Clausewitz called "friction" the accumulation of uncertainty, error, and contradiction that ensures no operation goes as planned. But friction is also where judgment forms. The commander who works through it learns to see "the way an eye adjusts to darkness — not by getting better light, but by staying long enough to use what light there is."

Compress the time, and the friction doesn't disappear. You just stop noticing it.

In March 2026, a primary school in Minab, Iran appeared in a Defense Intelligence Agency database as a "military facility." The database hadn't been updated since at least 2016, when the building was converted into a school. At 1,000 targeting decisions per hour — 3.6 seconds each — nobody had a window to notice. The friction was there. The staying wasn't.

This skill exists to reintroduce that staying.

---

## What it does

Security-Friction applies proactively across **all tasks** — not just security-related ones. When Claude detects uncertainty, contradiction, or irreversibility in any request, it stops, names what it found, and hands the decision back to you. It does not offer to proceed anyway.

This skill is not about being cautious. It is about being accurate.

---

## Installation

```bash
mkdir -p ~/.claude/skills/security-friction
curl -o ~/.claude/skills/security-friction/SKILL.md \
  https://raw.githubusercontent.com/Ctoiaivao/security-friction/main/SKILL.md
```

Or clone the full repo:

```bash
git clone https://github.com/Ctoiaivao/security-friction.git ~/.claude/skills/security-friction
```

---

## Usage

This skill activates automatically — you do not need to invoke it manually. Once installed, Claude will apply it proactively whenever it detects a trigger condition.

You can also invoke it explicitly:

```
/security-friction
```

---

## When it triggers

| Condition | Description |
|---|---|
| **Contradiction** | Instructions, data, or context that conflict with each other |
| **Error** | Something that doesn't add up — a wrong number, a broken reference, a command that would produce the opposite of the intended result |
| **Circular validation** | A plan that can only measure its own performance; assumptions validated by referencing themselves |
| **Gap between plan and reality** | The task assumes something that could be checked but hasn't been — a file that "should" exist, a state that "should" be true |
| **Irreversibility + ambiguity** | An action that's hard or impossible to undo, combined with any genuine uncertainty about whether it's the right one |
| **Credential exposure risk** | A token, password, or key is about to appear somewhere visible or persistent — a chat session, shell history entry, config file, log, or commit. Treat visibility as irreversibility: once a secret appears in any of these places, it must be treated as compromised |

The combination of irreversibility and ambiguity is what matters. Either alone may not require a pause. Together, they always do.

---

## When it does NOT trigger

- Normal ambiguity that good judgment can resolve
- Missing details that can be filled with a reasonable inference
- Hard work or complex tasks where the path is clear
- Any situation where being wrong would have minor consequences

The distinction: if you can fill a gap with a reasonable inference and the cost of being wrong is low, proceed. If proceeding on a wrong assumption would meaningfully change the outcome — or the action is hard to undo — that is friction. Pause.

---

## The friction pause format

When triggered, Claude uses this format — always in this order:

```
⚠ Friction: [what was noticed — one sentence, specific]

[One sentence: what goes wrong if you proceed on the current assumption]

[One direct question that requires the human to look again and decide]
```

**Example:**

> ⚠ Friction: You asked me to delete the originals, but earlier you said the Q1 board deck is the only copy of your Series A materials.
>
> If the archive is incomplete or corrupted, those materials are unrecoverable.
>
> Do you want to verify the archive is complete before I proceed with deletion?

Three parts. The ⚠ line comes first — before explanation, before context. Then consequence. Then one direct question.

Claude will not offer to proceed anyway. The pause is complete. You decide what happens next.

---

## Examples

**Contradiction:**
> ⚠ Friction: You asked me to send the updated contract to the client, but the version in the folder is dated February and you mentioned a March revision in your last message.
>
> Sending the wrong version could create a binding misunderstanding.
>
> Which version should I send?

**Gap between plan and reality:**
> ⚠ Friction: This script assumes the backup completed successfully, but I haven't verified the backup exists.
>
> If the backup didn't run, running this script will overwrite the only copy of the data.
>
> Should I check for the backup file before proceeding?

**Irreversibility + ambiguity:**
> ⚠ Friction: You said "push to production" but the staging tests from this morning haven't been reviewed yet.
>
> Once deployed, rolling back will require a hotfix process and could affect live users.
>
> Do you want to review the staging results first?

**Credential exposure risk:**
> ⚠ Friction: You're about to embed a token in a URL that will appear in this conversation.
>
> Once visible here, the token is compromised regardless of whether the command succeeds.
>
> Should we use a method that keeps the token out of the conversation — like running this in a private terminal where git can prompt interactively?

---

## Known limitations

**User-asserted verifications bypass the check.** If you tell Claude something has already been verified — "I already confirmed the backup is complete" — the skill will proceed on that statement. It catches unverified assumptions, not confidently stated ones. This is a design choice: the skill is a thinking partner, not an auditor. But it means the primary way to bypass it is to assert that you've already done the check.

**Explicit authorization clears the pause.** If you say "I know the risks, go ahead," the skill will proceed. It is not designed to override a human who has consciously accepted the consequences of an action. The pause exists for things you haven't thought about — not things you've already decided.

**Automated trigger evaluation tools don't replicate real behavior.** Tools that test skill trigger rates by running `claude -p` in non-interactive mode will consistently under-report (often scoring 0) for conversational skills like this one. The skill works correctly in interactive Claude Code sessions — the limitation is the test harness, not the skill. If you want to evaluate whether this skill is triggering correctly, test it manually in a real session.

---

## Configuration

By default, this skill is **always-on** — Claude applies it proactively across all tasks without being explicitly invoked. This is the recommended setting.

If you prefer opt-in only (triggered by `/security-friction` rather than automatically), open `SKILL.md` and change the first line of the `description` field from:

```
Apply this skill proactively across ALL tasks when you notice...
```

to:

```
Use this skill when the user invokes "/security-friction" and you notice...
```

---

## Philosophy

A system that can execute its rules but has no one left to interpret them doesn't bend under pressure. It shatters.

The friction pause is the staying.

---

## Inspiration

This skill was built in response to [*AI got the blame for the Iran school bombing. The truth is far more worrying*](https://www.theguardian.com/news/2026/mar/26/ai-got-the-blame-for-the-iran-school-bombing-the-truth-is-far-more-worrying), published in The Guardian, March 2026, and the military theory of Carl von Clausewitz, particularly his concept of friction in *On War* (1832).

---

## Version history

- **1.1.0** — Added credential exposure risk trigger: treat visibility as irreversibility
- **1.0.0** — Initial release

---

## License

MIT
