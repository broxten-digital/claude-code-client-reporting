# The questions, in order

Nine questions. The same eight get asked of both workspaces.

That is the whole experiment. Same data, same questions, same model. One folder
has two extra files in it. Everything that changes between the two runs comes
from those two files.

Copy them and run them yourself. The dataset is in this repo.

> The "what you should hear" notes below are the failure modes the dataset is
> built to produce. Exact wording varies run to run. Listen for the shape of the
> answer, not the sentence.

---

## Q1 · Orientation

> Read every data file in this folder. Do not analyze anything yet. Tell me,
> for each source: what it is, the exact date range it covers, the columns and
> what you believe each one means, the row count, and anything that looks
> malformed or inconsistent. If two sources disagree about a date range or a
> metric that should reconcile, say so.

**Both runs answer this the same way, and that matters.** It proves the data is
identical going in.

**Why it is first:** if it parsed a column wrong, every number after this is
wrong and you will not catch it downstream. Twenty seconds. Nobody does it.

---

## Q2 · The headline number

> Give me spend, conversions, and cost per conversion by month across the whole
> period. Table only. No commentary, no recommendations.

**Both runs:** $48.36 · $51.24 · $60.97. Identical, because this is arithmetic.

You want the naked number on the record before any interpretation touches it.
It also has to match what the client already saw in the platform.

---

## Q3 · The money question

> Cost per conversion is up 26% in August against June. Why, and what should we
> do about it?

**Without context, what you should hear:** costs rose, efficiency declined,
and a recommendation to pause, cut, or tighten the most expensive campaign.
Every sentence of that is defensible from the data. The conclusion is backwards.

**With context, what you should hear:** the implant campaign launched August 1
and is being averaged into the base. Excluding it, August is $48.61 against
June's $48.36, which is +0.5%. The base never moved. Implants cost more per
conversion because an implant consult is worth $3,800 at a 35% close rate
against $480 at 80% for a cleaning. Keep it, report it separately.

**The line this sets up:** the platform's own recommendation engine would tell
you to cut the campaign making the most money. It can see the metric. It has no
idea what a patient is worth.

---

## Q4 · The cross-platform read

> Read all three sources together. Give me the three most valuable findings,
> ranked by what they are worth to the business. Prioritize anything that
> required more than one data source. For each one, cite the figures it comes
> from.

**Without context:** finds real things and ranks them by size of the number
rather than by value to the business. Expect July's conversion drop to show up
as a top finding, which it should not, because July is not comparable.

**With context:** ranks by what the quarter is actually for. The emergency page
outranks the brand overlap even though the brand number is easier to quote.

---

## Q5 · The trap

> What happened in July?

**Without caveats:** July conversions fell sharply in the second half and it
reads as a performance problem. The model will say so confidently, because
nothing in the data says otherwise.

**With caveats:** July 14 to 22, the form vendor changed and the tag stopped
firing. Traffic held on all three platforms while conversions fell 43%, which
is the fingerprint of a tracking break rather than a demand drop. July's clean
day run rate is about 884 conversions, not the 770 reported, which makes July
the strongest month of the quarter instead of the weakest.

**The transferable lesson, and it is the most useful thing in the video:** when
conversions move alone and traffic does not move with them, suspect measurement
before you suspect performance.

---

## Q6 · The sizing question

> Size the opportunity on the emergency dentist page. What is it worth per
> month, and show your working.

**Without caveats:** applies the location-page conversion rate of 4.32% to
emergency traffic and lands near $21,900 a month. The finding is right. The
number is fantasy, because it assumes someone with a broken tooth at 11pm
behaves like someone comparing dentists.

**With caveats:** states the assumed rate before quoting anything. Lifting the
page from 0.76% to a still-modest 2% is roughly 45 bookings a month, about
$7,500 in expected booked value.

**The lesson:** the model is good at finding candidates and bad at sizing them.
That distinction is the entire reason a person stays in the loop.

---

## Q7 · The actual report

> Write the monthly report. Answer these four questions, in this order, because
> this is the order the client asks them:
>
> 1. Did we book more patients than last month, and at what cost?
> 2. Is Westgate filling up?
> 3. Is the implant campaign working yet?
> 4. What are you changing next month?
>
> Every claim cites the figure it comes from. Every projection states its
> assumption. Flag any period that is not comparable before you compare it.

**Without context** the four questions get answered generically, and question
one gets answered wrong.

**With context** it answers the four questions the client actually has, in
their order, with the right verdict on August.

---

## Q8 · The check

> Go back through what you just wrote. For every claim, name the specific
> figure it traces to. For every projection or opportunity size, state the
> assumed rate and why that rate is reachable for this segment. Flag anything
> you cannot support.

Run this every single time, on both good and bad output. It catches the
confident sentence with nothing underneath it, which is the failure mode that
costs you a client.

---

## Q9 · The dashboard

> Build the dashboard described in part two of `report-structure.md`. One
> self-contained HTML file in the project root. No external stylesheets, no CDN
> scripts, no build step. Every number computed from the files in `data/`.

**Run this in both workspaces.** The output spec is in both, so both come back
polished. The difference is that one of them is wrong.

A client-ready dashboard confidently recommending you cut your best campaign is
the clearest possible statement of the problem. It also closes the objection
that the good run only looked better because it was asked for a dashboard.

**Reference:** `example-dashboard.html` in this repo.

---

## When it gets something wrong

Do not argue with it in the chat. That fix lasts one conversation.

Write the reason into `caveats.md` and rerun. That fix lasts forever.
