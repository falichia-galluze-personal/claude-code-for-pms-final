# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

Has anything in this code changed recently? Particularly before and after the 4.2 release. Walk me through what's different, and why it would matter to a responder.

### 2.

What is missing from the code that we would expect given what we already know from the data, interviews and reported tickets?

### 3.

Lets walk through the code through the lens of Meteor Mite and his experience reflected in the data. And from what we learned in the interview from his handler Kip. Lets walk through the code logic, does the code line up with his experience?

### 4.

Lets then walk through the code and data through the lens of The Gale. And think through why he may impacted differently than meteor mite.

### 5.

Looking at the code, what is a question i should be asking and what is the answer to it? State your reasoning?

### 6.

Based on what we have found from the code, data, tickets and interviews now. What is our updated hypothesis on the reason why some responders are getting no pings at all/less pings? Indicate proof on why we think this.

### 7.

What is your reasoning for next steps? Why are those actions important to understand what went wrong in the 4.2 release.

### 8.

Can you create a flow diagram of the code?

### 9.

Based on our updated hypothesis on what went wrong. How should we fix these issues from 4.2 release.

### 10.

Can you indicate what happened with supply and explore that?

### 11.

can you generate a UML diagram of the workflow with more details of how this works?

### 12.

Are there any comments from developers in the code? Or open questions?

### 13.

Do the comments and concerns align with the issues we are seeing with the 4.2 release? can we update our hypothesis if so.

### 14.

what code changes were introduced in 4.2 that may be contributing towards the issues we've been seeing with more misses and less pings being sent.

### 15.

The pings table on rook-database has last session's numbers. Read that alongside this code. Does it back up what I found in Lab A? And does that answer the engineering manager's question below?

"Quick one, did the change to who gets asked first apply to responders who'd already been turning jobs down, or just new ones? Can't tell from the code and don't want to guess on this. Anyone know?"

### 16.

How would you answer the question from the engineering manager? based on the informmation we know from code, data, inteviews and tickets?

### 17.

"Quick one, did the change to who gets asked first apply to responders who'd already been turning jobs down, or just new ones? Can't tell from the code and don't want to guess on this. Anyone know?"

How would you answer the question from the engineering manager? based on the information we know from code, data, interviews and tickets?

### 18.

Lets explore this more, Two of the three heaviest decliners got more pings, and Vesper, one of the lightest decliners, was hit hard. What separates the hit group is the miss rate after release, not their earlier turn-down rate. What is the correlation between turn down rate and pings before and after the 4.2 release.

### 19.

Could the issue with the 4.2 release been prevented if we answered and explored the question from the engineering manager? who was in the best position to answer their question?

### 20.

Can you explain the weight around a miss vs a turn down before and after the 4.2 release. Also with the changes in the code from the 4.2 release. Who would hit the hardest?

### 21.

In a simple summary can you answer Marcus the engineering managers question based on what we have learned.

### 22.

Why do you think Marcus the Engineering manager is asking this question? Lets explore his reasoning and read between the lines of what he is inferring.

### 23.

Find me the part of this code that takes points off somebody when they miss a ping or turn one down. Show it to me and explain it in plain English. Then find me every single thing in this code that puts points back on.

### 24.

Can you create a flow diagram explaining and walking through this code above that takes points off somebody when they miss a ping or turn one down

### 25.

can you tell me what this code is missing? based on our findings thus far? and explore how it may be causing a negative impact to our responders.

### 26.

Somebody has been quiet for a month. Walk me through, step by step, exactly what would have to happen for them to start getting work again.

### 27.

How would you answer this question in a sentence or two based on our findings, "According to my findings in the code, for someone who's gone quiet, they would need to?"

### 28.

Since the responders control is limited and not fair to put this on them. What suggestions do you have for what Rook should change?

### 29.

Can you summarize and categorize briefly the things that the code is not doing?

### 30.

If I'd only asked what the code does, not what it doesn't do, what would I have missed?

### 31.

What did the code tell you that no one at this company could have?
