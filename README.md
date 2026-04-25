# SubOverlap — Subreddit User Overlap Tool

A lightweight, browser-based tool that uses Reddit's free public API to analyse user behaviour across subreddits. Enter any subreddit and it returns a ranked list of related communities, scored by how likely users from that subreddit are to also post or comment there.

---

## What it does

When you search for a subreddit, the tool:

1. Samples a set of recent commenters from that subreddit
2. Fetches each user's comment history to identify which other subreddits they participate in
3. Calculates a **probability multiplier score** for each overlapping subreddit — a score of `2.00×` means users are twice as likely to post there compared to the average Reddit user

This is useful for audience research, content strategy, community discovery, and understanding the broader interests of any subreddit's user base.

---

## How to use it

1. Open `index.html` in any modern web browser (or visit the hosted version)
2. Type a subreddit name into the search field (without the `r/` prefix)
3. Adjust the **sample size** and **minimum overlap** settings if needed
4. Click **ANALYSE** and wait for results — larger sample sizes take longer due to API rate limits

---

## Settings

| Setting | Description |
|---|---|
| **Sample size** | Number of recent users to analyse (25–75). More users = more accurate results, but slower. |
| **Min overlap** | Minimum number of sampled users who must share a subreddit for it to appear in results. Increase this to reduce noise. |

---

## Understanding the scores

Scores are **probability multipliers** relative to baseline Reddit activity:

- `0.00×` — No users from this subreddit post there
- `1.00×` — Users post there at the same rate as the average Reddit user
- `2.00×` — Users are twice as likely to post there
- `5.00×+` — Strong overlap; highly characteristic of this community's audience

---

## Technical notes

- Uses Reddit's **free public JSON API** — no API key or authentication required
- Requests are rate-limited to approximately 1 per second to comply with Reddit's usage policies
- Very large, general-interest subreddits (e.g. r/AskReddit, r/worldnews) are filtered from results as their ubiquity skews scores
- Results are based on a sample of recent activity, not full historical data — directionally accurate but not exhaustive

**CORS note:** This file must be served over HTTP to function correctly. Opening it directly via `file://` in a browser will block API requests. See hosting instructions below.

---

## Limitations

- Based on sampled recent data, not full historical user activity
- Private or quarantined subreddits cannot be analysed
- Reddit API availability is subject to Reddit's terms of service and may change

---

*Built with vanilla HTML, CSS, and JavaScript. No dependencies, no tracking, no server required.*
