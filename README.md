# Monthly client reporting in Claude Code

Everything used in the video. Free, no email, no signup, no upsell.

## What is in here

| File | What it is |
|---|---|
| `brightside-dental.xlsx` | The demo dataset. Three tabs, 3,283 rows, three months. Upload to Drive and it opens as a Sheet. |
| `TEMPLATE-context.md` | The context file. Fill this in per client. This is the one that matters. |
| `TEMPLATE-caveats.md` | The caveats file. Starts nearly empty and grows every time the analysis gets something wrong. |
| `example-context-brightside.md` | The filled version from the video. |
| `example-caveats-brightside.md` | The filled version from the video. |
|  `the-questions.md` | The eight questions asked on camera, in order, with the expected wrong answer and right answer for each. |
| `report-structure.md` | The shape of the output. |

All data in the demo file is invented. Brightside Dental Group is not a real
business.

## The whole method in five lines

1. Get your three exports somewhere Claude Code can read. A folder of CSVs is
   fine. A published Google Sheet tab is fine.
2. Before you ask for analysis, ask what it sees. Check the columns and the date
   range.
3. Write the context file. What the business sells, what a conversion is worth,
   what the quarter is for, what the client already knows.
4. Run the analysis. When it gets something wrong, write the reason into the
   caveats file and rerun. Do that for about three months and it stops being
   wrong.
5. Read it before the client does. Every claim traces to a number, every
   projection states its assumption.

## Why the context file is the point

A generic prompt gives you a generic report because the model was never told
what the business is trying to do. It can see that cost per conversion rose. It
cannot see that the rise came from a new high-value service line that is
working exactly as intended, because nothing in any export says what a patient
is worth.

That information is not in your data. It is in your head. The context file is
where you put it once so you never explain it again.

## Start smaller than you think

One platform, one client, ten lines of context. Run it once. The setup is an
afternoon and the payback is every month after that.
