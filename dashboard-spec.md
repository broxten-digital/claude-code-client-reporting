# Dashboard spec

How to render the analysis as a single self-contained HTML file.

Read this after `context.md` and `caveats.md`. Those two decide what the report
says. This one decides what it looks like.

**Output:** one `dashboard.html` in the project root. No external stylesheets,
no CDN scripts, no font imports, no build step. It has to open by
double-clicking it and it has to survive being emailed to a client.

**Every number on the page is computed from the files in `data/`.** Nothing is
typed in by hand. If a figure cannot be derived from a row in an export, it does
not go on the page.

---

## Structure, in this order

The order answers the client's questions in the sequence they ask them. Do not
rearrange it to put the prettiest chart first.

1. **Header.** Client name, the period, and one line naming the sources and the
   total row count. The row count is a credibility signal, so show it.
2. **The answer.** Four stat tiles. Booked conversions, cost per conversion on
   the comparable base, cost per conversion blended, expected revenue after
   close rates. Each carries its comparison and a verdict color.
3. **The headline callout.** One paragraph resolving whatever looks alarming in
   the tiles. This is the single most important block on the page. If a metric
   moved and the movement was fine, say so here in plain language, with the
   numbers inline.
4. **Chart one.** The metric the client leads with, over time, split the way the
   context file says to split it.
5. **Chart two.** The measurement story. If a caveat window exists, draw it.
6. **Findings.** Three cards, ranked by value to the business rather than by the
   size of the number. Label each with the sources it required, because
   "GSC + GA4" is the whole argument for doing it this way.
7. **Not comparable this period.** Every applicable caveat, in the report, not
   in a footnote. This is a trust move and it is not optional.
8. **Segment table.** By whatever the context file says to segment by first.
9. **Assumptions footer.** Every close rate and assumed conversion rate used
   anywhere above.

---

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
