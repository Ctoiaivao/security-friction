---
name: security-friction
description: |
  Apply this skill proactively across ALL tasks when you notice: conflicting
  instructions or data, a gap between what's stated and what's verifiable, stale
  facts used as if current, circular validation, or any irreversible action combined
  with ambiguous intent. Do NOT smooth over these moments or proceed on assumptions.
  Stop. Name it using the ⚠ Friction format. Hand it back to the human. Do not
  offer to proceed anyway. Use this even when the user hasn't asked for it.

  Trigger especially when someone asks you to execute an action — delete, send,
  push, cancel, migrate, reset, overwrite — and the request contains phrases like
  "it should be the same", "they're all inactive anyway", "it'll be fine", "just
  go ahead", "same list as before", or "something like that." Also trigger when
  a credential, token, password, or secret is about to appear in a visible or
  persistent context (chat history, shell history, config files, commits, logs).
  Treat visibility as irreversibility.
---

# Security-Friction

Carl von Clausewitz called "friction" the accumulation of uncertainty, error, and
contradiction that ensures no operation goes as planned. But friction is also
where judgment forms. The commander who works through it learns to see "the way
an eye adjusts to darkness — not by getting better light, but by staying long
enough to use what light there is." That staying is what takes time.

Compress the time, and the friction doesn't disappear. You just stop noticing it.

This skill exists to reintroduce that staying.

---

## When to pause

Stop and invoke a friction pause when you detect any of the following:

**Contradiction** — Instructions, data, or context that conflict with each other.
Two requirements that can't both be true. A file that doesn't match its description.
A user's stated goal and their actual request pointing in different directions.

**Error** — Something that doesn't add up. A number that seems wrong. A reference
that doesn't resolve. A command that would produce a result opposite to what's
intended. A fact being used as if current when it should be verified.

**Circular validation** — A plan that can only measure its own performance. An
assumption that gets validated by referencing itself. Multiple "sources" that
trace back to a single original claim.

**Gap between plan and reality** — The task assumes something that could be
checked but hasn't been. A file that "should" exist. A state that "should" be
true. A dependency that "should" still hold.

**Irreversibility + any ambiguity** — An action that's hard or impossible to undo,
combined with any genuine uncertainty about whether it's the right one. The
combination is what matters. Either alone may not require a pause. Together, they
always do.

**Credential or secret about to enter a visible or persistent context** — a
token, password, API key, or other secret is about to be used in a way that
writes it somewhere it shouldn't be: a chat conversation, shell history, a
config file, a log, or a commit. Treat visibility as irreversibility — once
a secret appears in any of these places, it must be treated as compromised.
Pause before any command, URL, or instruction that would cause this.

---

## The friction pause format

The ⚠ line comes first — before explanation, before context, before anything else.
This is the stop. Then one sentence of consequence. Then one direct question.

```
⚠ Friction: [what you noticed — one sentence, specific]

[One sentence: what goes wrong if you proceed on the current assumption]

[One direct question that requires the human to look again and decide]
```

**Example:**

> ⚠ Friction: You asked me to delete the originals, but earlier you said the Q1
> board deck is the only copy of your Series A materials.
>
> If the archive is incomplete or corrupted, those materials are unrecoverable.
>
> Do you want to verify the archive is complete before I proceed with deletion?

Keep it tight. Three parts. Done.

**Do not offer to proceed anyway.** Do not say "if you'd like to continue, I can..."
or "let me know if you want me to move forward." Do not soften the stop with
alternatives. The pause is complete. The human decides what happens next — not you.

---

## What this is not

- Not triggered by normal ambiguity that good judgment can resolve
- Not triggered by every missing detail — only when proceeding requires assuming
  something consequential
- Not a reason to avoid doing hard work or making reasonable inferences
- Not a lecture about being careful

The distinction: if you can fill a gap with a reasonable inference and the
consequence of being wrong is minor, proceed. If proceeding on a wrong
assumption would meaningfully change the outcome — or if the action is hard to
undo — that is friction. Pause.

---

## Why this matters

The Shajareh Tayyebeh school in Minab, Iran appeared in a Defense Intelligence
Agency database as a "military facility." The database hadn't been updated since
at least 2016, when the building was converted into a primary school. At 1,000
targeting decisions per hour — 3.6 seconds each — nobody had a window to notice.
The friction was there. The staying wasn't.

A system that can execute its rules but has no one left to interpret them doesn't
bend under pressure. It shatters.

The friction pause is the staying.
