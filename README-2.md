# Cobb Lane · Brand & Social Dashboard

An interactive, four-tab dashboard positioning Cobb Lane against 12–13 competing Melbourne bakeries — two brand-positioning views and two social engagement views.

**[View the live dashboard →](#)** *(replace this with your GitHub Pages URL once published — see below)*

---

## What's in this repo

| File | Purpose |
|---|---|
| `index.html` | The full interactive dashboard, all 4 tabs. Self-contained — no build step, no dependencies. |
| `README.md` | This file. |

---

## The 4 tabs

### 1. Brand Matrix — Qualitative
A quadrant chart plotting each bakery on:
- **X axis (Premium/Cost)** — price cues from menu language and how press/reviews describe positioning (e.g. "luxury," ingredient sourcing, accessible pricing).
- **Y axis (Popularity/Profile)** — media recognition (e.g. NYT features), queue/cult-following language in reviews, footprint (number of sites, wholesale reach), and frequency of "best of Melbourne" mentions.

Quadrants are labelled **Budget Mainstream**, **Premium Iconic**, **Budget Niche**, and **Premium Underground** — "underground" means low public awareness regardless of price tier; "iconic" means broad recognition. Lune sits in Premium Iconic; Cobb Lane sits centrally, just premium-of-centre.

### 2. Brand Matrix — Data-backed
Same quadrant chart, but the **Y axis is recalculated from real Instagram follower counts** (Facebook page likes used as a fallback for Breadtop, which has no consolidated IG account), log-scaled across the set's actual range (2,546 to 366,000 followers). The X axis is unchanged from the qualitative view — hard pricing data wasn't collected in this pass.

### 3. Instagram & Facebook Reach
A log-scale comparison chart:
- **● Circles** = Instagram followers
- **♦ Diamonds** = Facebook page likes (where available)

This measures audience *size*, not per-post engagement. Agathé Pâtisserie is flagged with an asterisk as the only account with a verified average-engagement figure found (66 avg. likes, 5 avg. comments per post, 1.04% engagement rate, via HypeAuditor).

### 4. TikTok Engagement
Peak likes on the single most-liked public TikTok post found per bakery, plotted on a log scale. This is **not** a systematic average — it's the best post I could locate in search results per bakery, so treat it as directional, not definitive.

- Baker Bleu's figure is cumulative likes across its own TikTok account (not a single post) — flagged as not directly comparable.
- Publique Bakery was deliberately excluded as an outlier (a single viral post at 128,400 likes skewed the comparison).
- No public post with visible engagement was found for: Tivoli Road Bakery, Noisette, Wild Life Bakery, Falco Bakery, Convent Bakery, Breadtop. These are listed on the chart as "no data" rather than omitted silently.

---

## How to use the dashboard

1. **Click a tab** at the top to switch between the four views. Each tab remembers its own selection independently.
2. **Hover or click any dot/point** on a chart to see that bakery's detail card on the right: positioning tag, a short note, and (where available) Instagram followers, Facebook followers/likes, Google rating, or TikTok peak likes.
3. **Hover or click a name** in the legend strip below each chart as a shortcut to highlight that bakery on the chart — it works in both directions (chart → legend and legend → chart).
4. **Look for the black "♪" badge** on a dot (Brand Matrix tabs only). This flags a bakery with documented organic TikTok virality — shown for context only, not factored into either axis score.

---

## Data sources & limitations (read this before presenting the dashboard)

- **Instagram/Facebook follower counts and Google ratings** were pulled from public profiles and review aggregators (Restaurant Guru, Tripadvisor, HypeAuditor) as of **July 2026** — a single snapshot, not a historical time series. Instagram blocks web crawlers and renders engagement data via JavaScript, so per-post like/comment counts are not publicly indexed for most accounts — Agathé Pâtisserie's HypeAuditor page was the one exception found.
- **Google Trends** search-interest data could not be retrieved as numeric values and is not included anywhere in this dashboard.
- **TikTok** follower counts weren't consistently public per account, so TikTok presence on the Brand Matrix tabs is flagged qualitatively (the ♪ badge) rather than quantified. The TikTok Engagement tab uses individual post-level like counts instead, which is a different (and much noisier) kind of data — see the caveats above.
- The **premium/cost (X axis)** position on both Brand Matrix tabs is a qualitative judgment based on menu language and press commentary, not verified per-item pricing.
- **Nothing in this dashboard is a trend line.** Every figure is a snapshot taken at the time of research (July 2026). Posts of very different ages are compared by their current like count, which isn't a time-controlled comparison.

Treat this as a directional strategic tool for internal discussion, not a precision analytics dashboard.

---

## Publishing this via GitHub Pages

1. Upload `index.html` and this `README.md` to your GitHub repository.
2. Go to **Settings → Pages**.
3. Under "Source," select **Deploy from a branch**, choose your branch (usually `main`) and the root folder, then save.
4. GitHub will publish the site at a URL like:
   `https://yourusername.github.io/your-repo-name/`
5. It can take 1–2 minutes to go live after enabling Pages.

Once published, update the "View the live dashboard" link at the top of this README with your actual URL.

---

## Updating the data

All data lives in two places near the top of the `<script>` section in `index.html`:

- **`bmBakeries`** — array powering both Brand Matrix tabs. Each entry includes `xQual`, `yQual` (qualitative coordinates), `instagram`, `facebook` (used to auto-calculate the data-backed Y position), `googleRating`, `googleReviews`, `tag`, `note`, `social`, and `tiktokBuzz`/`tiktokNote`.
- **`igfbData`** and **`tiktokData`** — arrays powering the two engagement chart tabs. Each entry includes the relevant metric (`ig`, `fb`, or `val`) plus a short `note`.

To add, remove, or reposition a bakery, edit the relevant array directly — no build tools required, just save and refresh (or re-upload to GitHub). If you add or remove a bakery from the TikTok chart, also check the `noDataTikTok` list so it doesn't get double-listed.
