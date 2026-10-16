# 05 · Super Speed — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. You've spent three sessions finding out what went
wrong: the two piles of feedback that didn't agree, the numbers that
hid four people inside an average, and the code that settled it —
the shorter timeout is what did it.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.
Help me write a product brief for Helen in response for her request in 05-super-speed/director-request.txt. The product brief needs to answer exactly what she's asking for. Please also reference rook-wiki Glossary, Team directory, and the 4.2 release comments (people are named by role; the Team directory maps roles to names). Also read the Word doc 00-rook/company/notes/handoff-from-priya.docx. You already read these once on Day 1. Go back for the exact terms and names your brief needs.
The brief needs to be a 1 page narrative, broken up into section. Please describe the product we have build. Explain the problem that happened and what had changed. Explain the impact to experience for our users like the handlers and responders. Include how we are going to fix and address this issue and the reasoning on why this fix will work. Please include what we are not fixing and addressing yet. Please also indicate any risk or questions we still may have.

### 2.
The note says this shouldn't just be a setting we quietly flip. Using Kip and Meteor Mite and the Gale, walk me through what's still missing from the brief before this could actually get built.

### 3.
In Helens request, in 05-super-speed/brief-for-helen.md she asks "

I want to see what we'd actually build
instead — from the point of view of the person it happens to. Not a
setting. Something a handler like Kip would notice, and something a
responder who's gone quiet would feel differently about.

" Does that mean we should keep and include Meteor Mite and Kip his handler in the brief? Where does the logic around because per-responder detail should stay out of shared outputs.

### 4.
yes please and let me review it, maybe we should refer to meteor mite in a generic sense as a responder who has gone quiet instead in the brief.

### 5.
Please include a short “before building” section in this brief

### 6.
Is there other suggestions that can trim our brief to be more concise but still clear?

### 7.
Lets do suggestion 1, 2 and 3 as you suggested. Please apply those changes.

### 8.
Save the brief exactly as it stands now as 05-super-speed/brief.md. You can rename it, I believe it was brief-for-helen.md. Show me the file when it's done.

### 9.
Can you commit this please

### 10.
push it to git please

### 11.
Take the brief you just wrote and build me a working prototype, an actual screen I can click through, not a description of one. Save it as 05-super-speed/prototype.html, a single file I can just open in my browser. Show me where this would actually happen, and make at least one thing on it respond when I click it.

### 12.
Show me this happening to Meteor Mite specifically, using her name, the way Kip would see it. its okay to not cover the alias name of the responder in the prototype.

### 13.
Do you have any other suggestions to optimize this prototype based on the problem we are trying to solve?

### 14.
Lets implement suggestions 1, 2 and 3 first.

### 15.
Can you implement suggestions 4 and 5

### 16.
can you revert suggestion 4 and 5. I feel like they are too detailed and will overwhelm our users. I think its important for the UX to be clear and concise and intuitive.

### 17.
Do you have other suggestions on wording where it could be more clear and concise on what handlers and responders would see?

### 18.
Can you not assume pronouns and use they them. Please update these suggestions based on that feedback.

### 19.
Please update the pronouns and update the suggested wording changes above.

### 20.
Should we add a flow and option besides "Mark reachable" to our prototype for when a handler checks in with a responder by indicating "I'll call them".
What if the responder was not reachable? Can you give suggestions.

### 21.
Lets add the not available option to the protoype. I am still thinking about the third option.

### 22.
Lets remove the back when option here. Instead if they select Not available we following the same pattern as we did for when we message their phone.

### 23.
Can you make the UX more "pretty" it looks pretty basic. Can you follow more UX standards.

### 24.
Can you add a real status bar and icons please.

### 25.
Can you enhance the responders experience more? Maybe make a timer to indicate how long they have to respond. For the demo allow the timer to run faster (ex: 5x)

### 26.
Can you use a super hero comic theme for the UX?

### 27.
For the responder experience, could you also show what historical interactions would look like. For both yes, i am reachable and not right now.

### 28.
Lets explore the options in the prototype if the responder did not respond via messaging their phone or calling them.
