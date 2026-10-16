# 06 · Sidekicks — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. You've spent five sessions on it: finding out what
went wrong, then building the fix nobody had — a working prototype,
by hand, in one sitting, for one room.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

I want to save a habit as something I can reuse as a skill. Please reference 05-super-speed/brief.md as an example of format that worked from a previous brief. When I review a brief before it goes any further, here's what I actually check for:
- It names who owns it
- It says how we'll know it worked
- The scope at the end matches the scope at the start
- It explains the problem before it proposes a fix

Turn that into a skill called review-checklist, so I can point it at any brief and get the same check every time, without me explaining it again.

### 2.

Do you have any suggestions on improvements on the skill based on the format of 5-super-speed/brief.md

### 3.

Lets test it first can you do a dry run on on 05-super-speed/brief.md and see whether it finds the gaps above. dont make any changes to the brief though.

### 4.

run /review-checklist on 05-super-speed/brief.md

### 5.

/review-checklist https://github.com/brucewyatt/claude-code-for-pms-final/blob/c629b8ee88fd49395de1c4a39bfa842aff01a5b7/05-super-speed/brief.md

### 6.

Schedule review-checklist to run every Monday morning, and let me know what it finds. Nothing needs to be ready for it to fire today. I'm setting the habit, not waiting on the result.
