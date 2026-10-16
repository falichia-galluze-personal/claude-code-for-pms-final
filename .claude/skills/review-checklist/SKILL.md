---
name: review-checklist
description: Reviews a product brief against the student's four-point check before it goes any further. Use when the student says "review this brief", "run the review checklist", "check this before I send it", or points at a brief or one-pager and asks for the usual check. Checks that the brief names an owner, says how we'll know it worked, ends with the scope it started with, and explains the problem before proposing a fix.
---

# Review checklist

The student reviews every brief the same four ways before it goes further. Run those four checks on the brief they point at, and report the same way every time. Don't ask them to explain the checks again.

If they don't say which brief, ask one short question: "Which brief should I check?" Read the whole file first. This skill only reads and reports: don't edit the brief unless they ask.

## The four checks

### 1. It names who owns it
- Look for a named person (or a clearly named role) who owns the work, and for who owns each open question or dependency.
- Pass: one accountable owner is named, and the open items each have a name next to them.
- Fix: "the team", "engineering", a blank, or an owner who hasn't seen the brief yet. Say who is missing and where.

### 2. It says how we'll know it worked
- Look for a measure, a target or a "fixed means" statement, plus how and when it will be checked.
- Pass: at least one concrete, checkable result (a number, a before/after, a named signal). A date or a way to measure it is a bonus.
- Fix: "improve", "reduce", "better" with nothing to measure, or a stated intent to define success later. Quote the line and say what's missing. Also say if the data to measure it doesn't exist yet.

### 3. The scope at the end matches the scope at the start
- Write down what the brief says it covers near the top (title, summary, first paragraphs). Write down what it asks for at the end (the build list, the decision, the next steps).
- Pass: the end asks for the same thing the start promised, and anything left out is named as "not now".
- Fix: the end adds something the start never mentioned, drops something it promised, or quietly grows or shrinks. List each mismatch as "Start says X, end says Y".

### 4. It explains the problem before it proposes a fix
- Check the order. The problem, who it happens to and the evidence should come before the first proposal.
- Pass: the problem and its cause come first, and each proposed item traces back to it.
- Fix: a solution shows up before the problem is explained, or a proposed item answers a problem the brief never described. Quote the first fix and say what came before it.

## What to report

Keep it short and plain. For each check give a status (Pass, Fix, or Can't tell), one line of why, and a quote or section name as proof. Then end with the full list of fixes in the order they should be done, and one sentence on whether it's ready to go further.

Use this layout:

```
1. Owner: Pass / Fix / Can't tell. Why, with a quote.
2. How we'll know: ...
3. Scope matches: ...
4. Problem before fix: ...

Fix before it goes further:
- ...

Ready? One sentence.
```

Be honest about gaps. Don't pass a check because the section exists; pass it only when the content does the job. If a brief doesn't have a section for a check (say, it has no owner anywhere), say that plainly rather than guessing.

## A brief that worked

`05-super-speed/brief.md` is the example of the format. Use it to see what good looks like, not as a template to force on others. In it:
- The header names who it's for and who it's from, and the closing section names owners (Wen, Marcus, Sofia, Ravi) next to each gap.
- "Say what 'fixed' means" sets the targets to agree before building.
- "Not now" lists what's out, so the closing "Decision for you" matches the opening promise.
- "What happened" and "What it feels like today" come before "What we'd build".

Other briefs don't need the same headings. Judge them on the four checks, not on whether they look like this one.
