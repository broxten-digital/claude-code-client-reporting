# Report structure

Two halves. **What the report says**, then **what it looks like**.

Read this after `context.md` and `caveats.md`. Those two decide the conclusions.
This one decides the shape they arrive in.

---

# Part one: the written report

Adjust the section names to your client, keep the order.

The order is not stylistic. It answers the client's questions in the sequence
they actually ask them, so nobody has to hunt for the part they care about.

## 1. The answer, in four lines

Did we produce more than last period, and at what cost. Whether that is good.
The single biggest thing that changed. What you are doing next.

Written so someone who reads nothing else has still been told the truth.

## 2. What moved and whether it was good

The headline metrics, each paired with a verdict rather than a direction.
"Cost per conversion rose 26%" is not a finding. It is a fact waiting for one.

Segmented the way the context file says to segment, never blended.

## 3. Findings

Ranked by what they are worth, not by which platform they came from. Lead with
anything that required two or more sources, because that is the part the client
could not have gotten from a dashboard.

Each finding: what the data shows, which figures it comes from, what it means
for the business, and what you would do about it.

## 4. What is not comparable this period

Every caveat that applies, stated before anyone can be misled by a comparison.
Tracking breaks, promotions, launches, seasonality.

Putting this in the report rather than in a footnote is a trust move. It is
also the section that stops a client discovering a distortion on their own and
wondering what else you missed.

## 5. Next period

Three or four actions, each tied to a finding above and to a goal in the
context file. Anything you cannot trace back to both does not belong here.

## 6. Assumptions

Every projection and every opportunity size, with the rate it assumed and why
that rate is reachable.

Nobody reads this section. It is there so that when someone does, the number
survives.

---

# Part two: the dashboard

**Output:** one `dashboard.html` in the project root. No external stylesheets,
no CDN scripts, no font imports, no build step. It has to open by
double-clicking it and it has to survive being emailed to a client.

**Every number on the page is computed from the files in `data/`.** Nothing is
typed in by hand. If a figure cannot be derived from a row in an export, it does
not go on the page.

## Blocks, in this order

Same logic as part one. Do not rearrange it to put the prettiest chart first.

1. **Header.** Client name, the period, and one line naming the sources and the
   total row count. The row count is a credibility signal, so show it.
2. **The answer.** Four stat tiles, mirroring section 1 above. Each carries its
   comparison and a verdict color.
3. **The headline callout.** One paragraph resolving whatever looks alarming in
   the tiles, with the numbers inline. The single most important block on the
   page.
4. **Chart one.** The metric the client leads with, over time, split the way the
   context file says to split it.
5. **Chart two.** The measurement story. If a caveat window exists, draw it.
6. **Findings.** Three cards, ranked by value to the business rather than by the
   size of the number. Label each with the sources it required, because
   "GSC + GA4" is the whole argument for doing it this way.
7. **Not comparable this period.** Section 4 above, rendered in the page rather
   than in a footnote.
8. **Segment table.** By whatever the context file says to segment by first.
9. **Assumptions footer.** Section 6 above.

## Charts

**Two charts. Not five.** A dashboard with nine charts is a dashboard nobody
reads. Pick the two that carry the argument and put everything else in a table.

- **Pick the form from the data's job.** Comparing a few discrete periods is
  grouped bars. A continuous series where the shape matters is a line. A single
  headline number is a stat tile and not a chart at all.
- **Bars start at zero. Always.** A truncated axis to make a change look bigger
  is the oldest lie in reporting.
- **One y-axis per chart. Never two.** Two measures of different scale become
  two charts.
- **Smooth noisy daily data** with a trailing 7-day average and say in the
  caption that you did.
- **Draw the caveat windows on the chart.** A shaded band with a short label
  over a tracking outage explains more than a paragraph does.
- **Direct-label the values** on bars. Never put a number on every point of a
  line.
- **Two series get a legend and a caption** explaining why they differ. If two
  series are identical for part of the range, say why in the caption instead of
  letting it look like a rendering bug.
- **Every mark gets a `<title>`** so hovering gives the exact value.
- Grid lines and axis labels recede. The data is the only thing at full
  contrast.

## Color

Validated for color-blind separation and for contrast on the dark surface. Use
these and do not substitute.

| Role | Hex |
|---|---|
| Surface | `#0B1220` |
| Card | `#111B2E` |
| Border | `#22304a` |
| Text | `#E6EDF7` |
| Muted text | `#8FA3C0` |
| Series 1 | `#3987e5` |
| Series 2 | `#d95926` |
| Good | `#0ca30c` |
| Warning | `#fab219` |
| Serious | `#ec835a` |
| Critical | `#d03b3b` |

- **Series colors mean the entity, never the rank.** If a filter changes which
  series show, the survivors keep their color.
- **Status colors are reserved** for verdicts and never reused as a third
  series.
- **Never color alone.** A verdict carries a word, not just a hue.
- **Text stays in text colors.** A number never wears its series color.

## The one that gets missed

**A metric moving is not a finding, and an arrow is not a verdict.** A cost
increase drawn as a green up-arrow reads backwards no matter how correct the
underlying judgment is. Anything inside plus or minus one percent is "flat."
Everything else states whether the movement was good in words.
