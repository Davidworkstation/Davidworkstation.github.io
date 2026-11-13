---
layout: post
title: "Finding the Gift That Crossed the Threshold"
date: 2026-11-13
description: "Using SQL running totals to identify when a donor reaches a giving milestone."
tags: sql fundraising window-functions
categories: data
---

A donor has given $12,000 to your organization. That answers how much they have contributed—but what if you need to know **when they first reached $10,000?**

That small change in the question changes how we approach the data. A lifetime total can tell us who qualifies for a giving society or membership. Establishing when they qualified requires looking at how their giving accumulated over time.

This is where running totals become useful.

Imagine a donor with the following gift history:

| Gift date | Gift amount | Running total |
|---|---:|---:|
| January 15, 2025 | $2,000 | $2,000 |
| April 10, 2025 | $3,000 | $5,000 |
| September 20, 2025 | $5,000 | $10,000 |
| December 5, 2025 | $2,000 | $12,000 |

If membership begins when a donor reaches $10,000, the date we want is September 20, 2025. The December gift contributes to their current total, but they had already qualified by then.

We can find that milestone by breaking the query into three steps: calculate each donor’s running total, rank the transactions that meet the threshold, and keep the first one.

```sql
WITH gift_running_totals AS (
    SELECT
        entity_id,
        gift_id,
        gift_date,
        gift_amount,
        SUM(gift_amount) OVER (
            PARTITION BY entity_id
            ORDER BY gift_date ASC, gift_id ASC
            ROWS BETWEEN UNBOUNDED PRECEDING
                     AND CURRENT ROW
        ) AS running_total
    FROM gift_transactions
),
qualifying_gifts AS (
    SELECT
        entity_id,
        gift_id,
        gift_date,
        running_total,
        ROW_NUMBER() OVER (
            PARTITION BY entity_id
            ORDER BY gift_date ASC, gift_id ASC
        ) AS qualifying_row
    FROM gift_running_totals
    WHERE running_total >= 10000
)
SELECT
    entity_id,
    gift_id AS threshold_gift_id,
    gift_date AS threshold_date,
    running_total AS total_at_threshold
FROM qualifying_gifts
WHERE qualifying_row = 1;
```

The first step builds the giving history. `PARTITION BY entity_id` gives each donor a separate running total, while the ascending date order accumulates their gifts from oldest to newest.

The explicit `ROWS` clause adds transactions one row at a time. I also include `gift_id` as a consistent tie-breaker when multiple gifts share the same date. If the actual sequence within a day matters, use a transaction timestamp or another field that records that sequence.

The second step narrows the results to gifts where the running total is at least $10,000. Only then do we apply `ROW_NUMBER()`, numbering the qualifying transactions separately for each donor.

That order matters. We want the first transaction **among those that qualify**, so we filter before assigning the row number.

The final step keeps row one. The result is one record per qualifying donor, showing the gift and date associated with their first milestone.

A small detail here can change the answer: **reaching a threshold and exceeding it are different rules.** This example uses `>= 10000`, so a donor qualifies at exactly $10,000. If the requirement is to surpass $10,000, use `> 10000` instead. In the example above, that would move the qualifying date from September to December.

The other important consideration is what counts toward the total. Before calculating it, establish which transactions belong in the giving history. Are you counting payments, pledges, or particular types of credit? Is the milestone based on lifetime giving or a specific campaign? Those decisions determine which rows should enter the calculation.

Refunds and adjustments also deserve attention. If negative amounts are included, this query identifies the first recorded point when the donor reached the threshold—even if their total later fell below it. That answers a historical milestone question; current eligibility may require an additional check.

What I like about this approach is that it turns transaction history into something actionable. A total tells us where a donor stands. A running total helps reveal when they got there.

For membership qualification, giving society recognition, or fundraising goals, that date can be just as useful as the amount itself. By combining a running total with a ranking step, we can identify the moment a donor’s giving became a milestone.
