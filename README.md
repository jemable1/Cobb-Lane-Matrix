[README.md](https://github.com/user-attachments/files/30108352/README.md)
# Cobb Lane Brand Matrix — Melbourne Bakeries

An interactive brand positioning chart mapping Cobb Lane against 12 competing Melbourne bakeries, plotted on two axes:

- **X axis** — Cost / Premium positioning (Budget/Accessible → Premium/Luxury)
- **Y axis** — Popularity & profile

The chart includes two views you can toggle between, plus a flag for bakeries with notable organic TikTok buzz.

**[View the live chart →](#)** *(replace this with your GitHub Pages URL once published — see below)*

---

## What's in this repo

| File | Purpose |
|---|---|
| `index.html` | The interactive chart. Self-contained — no build step, no dependencies. Open it in any browser or publish via GitHub Pages. |
| `README.md` | This file. |

---

## How to use the chart

1. **Toggle between two views** using the buttons at the top:
   - **Qualitative read** — positioning based on press coverage, reputation, and brand narrative.
   - **Data-backed (IG/FB followers)** — the Y axis is recalculated from real Instagram/Facebook follower counts (log-scaled, since follower counts range from ~2,500 to ~366,000 across the set). The X axis stays qualitative in this view, since hard pricing data wasn't collected.

2. **Hover or click any dot** to see that bakery's detail card: positioning tag, a short note, and (where available) Instagram followers, Facebook followers, and Google rating.

3. **Look for the black "♪" badge** on a dot. This flags a bakery with documented organic TikTok virality (creator content, hashtag traction) — it's shown for context only and is *not* factored into either axis score.

4. **Click any name in the strip at the bottom** as a shortcut to select that bakery instead of finding its dot on the chart.

---

## Data sources & limitations

- Instagram/Facebook follower counts and Google ratings were pulled from public profiles and review aggregators (Restaurant Guru, Tripadvisor) as of **July 2026** — a single snapshot, not a historical time series, since these platforms don't expose follower history publicly.
- **Google Trends** search-interest data could not be retrieved as numeric values and is not included.
- **TikTok** follower counts weren't consistently public per account, so TikTok presence is flagged qualitatively (the ♪ badge) rather than quantified.
- The **premium/cost (X axis)** position is a qualitative judgment based on menu language and press commentary, not verified per-item pricing — this applies in both the qualitative and data-backed views.

Treat this as a directional strategic tool, not a precision analytics dashboard.

---

## Publishing this via GitHub Pages

1. Create (or use) a GitHub repository and upload `index.html` (and this `README.md`) to it.
2. Go to **Settings → Pages**.
3. Under "Source," select your branch (usually `main`) and the root folder, then save.
4. GitHub will publish the site at a URL like:
   `https://yourusername.github.io/your-repo-name/`
5. It can take 1–2 minutes to go live after enabling Pages.

Once published, update the "View the live chart" link at the top of this README with your actual URL.

---

## Updating the data

All bakery data lives in a single `bakeries` array near the top of the `<script>` section in `index.html`. Each entry includes:

```js
{
  id, name, xQual, yQual, color, tag, note, highlight,
  instagram, facebook, googleRating, googleReviews, social,
  tiktokBuzz, tiktokNote
}
```

To add, remove, or reposition a bakery, edit that array directly — no build tools required, just save and refresh the page (or re-upload to GitHub).
