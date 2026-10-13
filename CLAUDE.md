# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

Sources: rook-wiki (About Rook, Glossary, Team directory, Releases, Q3 roadmap, Product briefs) and `00-rook/company/notes/handoff-from-priya.docx`. I am the new PM for Rook Dispatch, taking over from Priya Raghunathan (left 21 Aug 2026; 14 months as sole Dispatch PM).

### Products
- **Rook Dispatch** (mine): responder coordination. A callout comes in, Dispatch ranks available responders, pings the top one on their phone, who takes it or doesn't. Users: handlers (console, desktop-only) and responders (phone app).
- **Rook Supply**: gear provisioning (requisitions, maintenance, field failure reports). Users: handlers and quartermasters. Shares the Responder Availability Record (Dispatch writes, Supply reads).
- Company: subscription per active responder; monthly release train, point releases numbered 4.x (actual gaps have been ~2 months). Responders are independent, not employees. **Never store or try to infer cover-to-legal identity** (Security Policy 4.1; people were fired over it).

### People
| Who | Role | Notes |
|---|---|---|
| Helen Achebe | Director of Product (my boss) | Owns roadmap and commitments; gives room |
| Marcus Oyelaran | Eng Manager, Dispatch | Straight talker; first call on anything unsure |
| Wen Li | Staff Engineer, Berlin | Built the ping-ranking logic; the only real source on how it works |
| Sofia Marino | Product Designer | Console + phone app; ran the September customer interviews |
| Ravi Menon | Data Analyst, Singapore | Owns the real weekly numbers, incl. how often responders take pings |
| Nadia Hoffmann | Support Lead, Berlin | Hears handler complaints first; wants a standing 15 min |
| Priya Raghunathan | Former PM | Gone; Marcus has her number |

Wiki comments use roles, not names. Mapping: "Engineering manager" = Marcus, "Staff engineer" = Wen Li, "Product designer" = Sofia, "Support lead" = Nadia. Handlers named in briefs: Halloran (Supply), Aunt Dot, Kip, Mr. Ambrose.

### Vocabulary
- **Ping**: one callout offered to one responder. Outcomes: *taken*; *turned down* (said no); *missed* (no answer within the **ping wait**). Turned down and missed both pass it to the next responder but are recorded separately.
- **Acceptance rate** (taken ÷ pings; headline metric) and **time-to-accept** (median seconds, ping to taken).
- **Coverage gap**: no available responder had the needed **capability tags** (flight, structural-entry, hazmat-tolerant, cold-weather, aquatic, crowd-management, de-escalation). Different from low acceptance.
- **Routing priority**: ranking score from proximity (travel-time estimate), availability, capability match, and recent acceptance history. Turning down or missing pings lowers recent acceptance, which lowers future position.
- **Mutual aid**: cross-area cover; unsupported, on the Q4 list. **Requisition / quartermaster / field failure report / service interval**: Supply terms.

### Release history (Dispatch)
- 4.0, 7 Apr: new console nav, responder profile redesign, routing override audit log.
- 4.1, 16 Jun: travel-time proximity, bulk callout, push reliability.
- 4.2, 12 Aug: proximity weighted up vs recent acceptance; **ping wait 90s to 60s**; console filters persist; three fixes.

### Where things stand
- **4.2 is the live problem.** Callout tickets ~3x normal since ~12 Aug and still elevated on 26 Aug. About two thirds "phone never goes off", one third "gone before I could answer" (Nadia's tracking). The second is explained by the 60s ping wait. The first is not.
- **My hypothesis, unverified:** the 4.2 weighting applies equally to responders who turn pings down, so a drop in acceptance pushes them lower and they get pinged less (a feedback loop). Marcus asked on 14 Aug whether that was a decision or fell out of the config; Wen Li never answered. Nobody has run the numbers.
- **Priya's view:** mostly seasonal (August is soft), come back in September, don't revert 4.2 (it was a long-requested change). Treat as her opinion, not evidence; the ping wait change confounds it. Marcus and Nadia deferred the 4.2 discussion until I'd looked myself. Get Ravi's weekly acceptance and time-to-accept trend, split by before/after 12 Aug and by responders with low recent acceptance. A `rook-database` connector exists but I have not checked it.
- **Roadmap is stale** (last reviewed 30 Jun, all items Priya's). 4.2 committed: change to who gets pinged (shipped), ping timeout tuning (a 90 to 60 cut shipped; unclear if that was the whole item), **Availability Confidence (not in 4.2 notes; squeezed out, still marked Committed)**. 4.3 committed: requisition approval chains (Supply). Q4 exploring: handler phone app, shared cover between responders. Priya says the "which are still Q3 commitments" talk with Helen has not happened; I need to have it.
- **Briefs are partly out of date:** Routing Override Audit Log and Bulk Callout both shipped (4.0, 4.1) though the briefs read as pending. Requisition Approval Chains has scope creep (second approval over $2,000 plus five add-ons); phasing undecided. Handler Phone App (8 Sep) is exploration only, unstaffed.
- No written description of how pings are ranked exists. Priya asked me to write it, with Wen Li.
- Don't let 4.2 console filter persistence tickets eat time (noise).
- Not yet read: Customer interviews and Research in the wiki; the Team directory still lists Wen Li as away in August (out of date).
- **Now read and checked:** the four September customer interviews, `00-rook/code/dispatch-routing`, and `rook-database` (callouts, pings, responders, handlers, support_tickets; data only 29 Jun to 6/7 Sep). It has no answer times, rank positions, push delivery receipts or capability tags, so time-to-accept and coverage gaps can't be computed. Wiki pages returned no comment threads.
- **What the numbers show:** weekly acceptance was flat at ~75-78% until 9 Aug, 54% in the week of 10 Aug, 73% by 31 Aug. Missed pings went from 2-6 a week to 38, then 21-28. Tickets went from 5-8 a week to 20-32. Callouts dipped ~140 to 110-127 a week (some real seasonality), but four responders (Farlight, The Undertow, Meteor Mite, Vesper) lost 66-75% of their pings while busy ones gained, and 55-64% of the four's pings were missed (vs ~10-14% for others). Meteor Mite and The Gale share Eastgate and got 3.8 vs 18.6 pings a week.
- **My hypothesis needs revising:** the code cut the recent-acceptance weight in 4.2 (0.40 to 0.25) and raised proximity (0.45 to 0.60). Misses are scored as declines (-0.12 vs +0.08 credit, no decay, floor 0, a 2019 TODO). So the likelier driver is the 60s ping wait plus miss-as-decline, not the weighting. Untested: whether these four are slow answerers or hit push failure. Need from Ravi/Wen: answer times, delivery receipts, rank positions, and a replay of scoring without the miss penalty. Also unchecked: whether proximity alone sinks them (their areas vs callouts).
- **Open questions and inconsistencies:** Supply may read starved responders as "low callout load" when scheduling maintenance (inference; ask Supply). The Requisition Approval Chains brief says Halloran wants a second approval, but his interview says approvals are too slow. Priya says Marcus can pull numbers, the directory says Ravi owns them. "Shared cover" on the roadmap collides with "cover identity". The roadmap still says Q3 and 4.3 isn't in Releases. The interview transcripts carry household detail about responders and handlers: keep it out of anything I write.
- **The four are locked out, not dipping:** pings to Farlight, The Undertow, Meteor Mite and Vesper went from ~49 a week to 16, 6, then 3 (weeks of 17, 24, 31 Aug). Their last 7 pings were all missed, none taken. Before 4.2 they took 75% of pings, same as everyone else, so they were not weak responders. The company-wide acceptance "recovery" to 73% is the busy responders carrying the average. In `history.py` a score only moves when someone is offered a ping and has no decay, so a low-ranked responder can't climb back. That is my reading of the code, not confirmed against stored scores.
- **Cost to callouts:** callouts where nobody took the ping went from 5.5% (48 of 879) to 11.1% (49 of 440). Callouts needing 3+ pings went from 1.4% to 5.9%. I can't see whether handlers covered them by hand. Of 107 tickets filed since 12 Aug, 83 are still open, and all 40 earlier ones are closed (support is swamped, including open "ping moved on while reaching for the phone" tickets).
- **Worries nobody has raised:** nobody tracks per-responder activity or likely churn; handlers may be quietly overriding routing (the audit log exists but there's no override data in the database); Supply hasn't been told 4.2 changed who gets called out; any fix shipped as a bundle will be confounded again, so stage it and measure per responder; per-responder timelines could help identify masked responders, so keep shared outputs aggregated.
- **Data is stale:** `rook-database` stops on 6/7 Sep and today is 13 Oct. Next asks: Ravi for per-responder weekly numbers through today, Nadia for open "quieter than usual" tickets, Marcus/Wen for the four's stored scores, push delivery and handler overrides. Leading fix option to take to Helen and Marcus: keep the 4.2 proximity change, stop scoring misses as declines, add decay, revisit the 60s wait (Marcus must be told before any `config.py` change).
- **Support tickets (147, 29 Jun to 7 Sep, 12 handlers, each about one responder):** 32 "quiet" (all open, all after 12 Aug, only from the handlers of Farlight, The Undertow, Halfmoon and Corporal Ashgrove), 13 "gone before answering" (nine handlers, responders whose pings rose), 16 filters, 26 Supply, 40 console requests, 15 account/admin, 5 push glitches (all before 12 Aug). Volume went from ~6 a week to ~28; the non-4.2 tickets also rose ~2.5x. Meteor Mite's and Vesper's handlers filed none, so tickets undercount.
- **Correction:** Halfmoon and Corporal Ashgrove are not locked out (pings -22% and -25%, their areas' callouts -32% and -33%; Halfmoon also had a leave week and a travel time-zone ticket). Watch list only. In Uptown, Harborside and Old Town the home responder got the first ping 80% of the time before 4.2 and 17% after (other areas 80% to 72%), so proximity did not protect the four.
- **Refined hypothesis:** the 60s wait turned slower answerers (60-90s) into misses, miss-as-decline with no decay locked them out, and what they were still offered were leftover pings, so they missed more. Busy responders absorbed the load and lost some to the 60s clock ("gone before"). Priya's "seasonal" doesn't fit (the four's areas down 13-20%, their pings down ~70%) and the weighting change alone doesn't either. Untested: slow answerers vs push failure.
- **Interviews vs tickets:** only Mr. Ambrose is in both; the three handlers who never filed (Aunt Dot, Kip, Halloran) are three of the four interviewees (about 1% chance if random; ask Sofia how they were picked). 85% of tickets were filed before the 2-5 Sep interviews. Interviews alone mislead: they overweight "gone before", read like a UX backlog and make "seasonal" look plausible.
- **Open inconsistencies:** Ambrose's incident is 12 Aug in his ticket but "two weeks ago" in his interview; Halloran says maintenance scheduling improved but tickets say it booked a suit on marathon day; many ticket bodies are word-for-word identical across handlers (ask Nadia if templated).
- **Next:** Nadia first, then Linda Pruitt (Farlight), Desmond Okafor (The Undertow), one busy-responder handler (Marjorie Sung or Farid Haddad), Simone Fischer (Halfmoon), follow-ups with Kip and Aunt Dot, a quartermaster, and a starved responder only with consent. Still need answer times, delivery receipts, stored scores, a no-miss-penalty replay and per-responder weeks to today.
