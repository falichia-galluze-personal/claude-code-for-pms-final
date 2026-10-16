# Quiet responders: what we'd build instead of changing a number

**To:** Helen Achebe, Director of Product · **From:** PM, Rook Dispatch · **Date:** 16 Oct 2026 · **Status:** draft, internal, for Helen only (please don't forward). Data runs to 6 Sep (see Before building).

## What we built
Rook Dispatch gets the right responder to the right callout. A handler enters it in the console. Dispatch ranks available responders by **routing priority** (proximity, availability, capability match, **recent acceptance history**) and **pings** the top one's phone. The responder takes it, turns it down, or it is **missed** when the **ping wait** runs out. Turned down and missed both pass it to the next responder. Our headline metric is **acceptance rate**, reported in aggregate.

## What happened
4.2 (12 Aug) changed three things at once: proximity weight up, **ping wait cut from 90s to 60s**, and console filters now persist. In the code, a missed ping costs a responder the same as a turn-down, and a score never recovers on its own. That is the 2019 note Wen Li left, and nobody came back to it. Responders who answer in 60 to 90 seconds started missing pings, each miss pushed them down the order, and fewer pings meant more misses. **Four of our 16 responders went from about 49 pings a week to 3.** Before 4.2 they took 75%, the same as everyone else. Acceptance "recovered" to 73% only because busy responders carry the average, so the average hid it. It isn't seasonal: their areas' callouts fell 13-20%, their pings fell about 70%.

## What it feels like today
- **Handler (Kip):** Kip handles two responders in the same area. One has gone quiet, dropping from about 11 pings a week to 1, and the other is picking up the slack (13 to 21). The console says nothing about either. Kip filed no tickets, so the only way to find out would be to notice, and then to ask. Across the team the 32 "quiet" tickets are all still open, and some affected handlers filed none, so tickets undercount.
- **The responder who has gone quiet:** the phone stops going off with no explanation and no way back. The only route to a better position is to be pinged, and that has stopped. Before 4.2 this responder took pings at the same rate as everyone else.
- **Everyone else:** 13 "gone before I could answer" tickets, which the 60s wait explains.

## What we'd build
1. **Handler: a "gone quiet" notice on the responder's card.** It appears when pings drop by more than half against their own norm. It says why in plain words ("last 7 pings timed out") and offers one click to check in with them. It goes to their own handler only. For Kip it would have fired in the first week, on the quiet responder's card, and would also show that Kip's other responder is carrying the extra load.
2. **Responder: a way back, without asking for it.** Misses stop counting as turn-downs. Standing eases back toward neutral over time. The four get a one-time reset. The phone says "you missed 3 pings, still reachable?" and offers an undo for an accidental tap (one ticket asked for this).
3. **Both: we can see it next time.** We log answer time, rank and delivery, and alert on a per-responder drop.

**Why it should work:** my replay of the scoring (a reconstruction, not stored scores) has the four falling to 0.00 by early September when misses count as turn-downs, and holding at 0.76-0.84 when they are neutral. Nothing in the code lets a score recover, so "wait until September" has no mechanism behind it. The notice shortens detection from weeks of ticket lag to about a week, and no longer depends on a handler filing a ticket.

**Not now:** reverting the 4.2 proximity change (long requested, doesn't explain the lock-out on its own), changing the 60s wait (needs real answer times first, then one change per release), shared cover (Q4 exploration, collides with cover identity), and unrelated roadmap items.

## Before building: gaps and questions
- **Cover the overloaded side too.** The notice only flags the quiet responder. A handler like Kip also needs to see when their other responder is carrying the extra load.
- **Define "check in."** Does Rook message the responder, or does the handler call? Without delivery receipts and answer times, the handler can't tell a dead phone from a slow answer, and if it is push failure the score fix won't help.
- **Test the threshold.** "Pings down more than half" needs trying against ordinary dips (leave weeks, quiet spells) before it goes live, or handlers will learn to ignore it.
- **Plan for relapse.** If a reset responder is a 60-90s answerer, neutral scoring puts them back in the order and they miss again at 60s, wasting a first-ping slot on a live callout. We need a small miss penalty with decay, or a stopgap, sized by Wen.
- **Say what "fixed" means.** Set targets for the quiet responder's pings and take rate and for the busy one's load. We can't compute time-to-accept yet, and with four affected responders there is no clean control group.
- **Missing data.** The database ends 6 Sep, so I need per-responder weekly pings through today from Ravi Menon. I also need the stored scores (do they reset at deploy?) and handler override data from Marcus Oyelaran or Wen. Supply may read quiet responders as low load when scheduling maintenance and needs to be told.
- **Phone message and owners.** Sofia Marino designs the copy and we test it, interviewing a quiet responder only with consent. Wen, Marcus and Sofia haven't seen this, and "ship this afternoon" covers the score change only. The notice, phone message and logging are real builds with no estimate yet.
- **Privacy.** Alerts stay with the responder's own handler. Shared reporting stays aggregated, with no household detail.
- **Decision for you:** ship the score fix this week (Marcus has to be told before any `config.py` change), and build the notice and phone message after it, each measured on its own?
