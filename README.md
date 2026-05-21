# YOU DECIDE — Album Rollout Voting Site

A trap-style voting site for your rollout. Fans vote, results glitch, then the override hits.

## Setup

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project → Import your GitHub repo
3. Deploy (zero config needed — it's pure static HTML)

## Customization

Open `index.html` and find these sections:

### Your name
Search for `ARTIST NAME` — replace with your actual name/alias (appears in header + footer).

### Vote options
Find the 4 `vote-block` divs and edit the `data-val` and button text:
- Block 0 = Release date options
- Block 1 = Lead single names (currently "REDACTED" — hover to reveal effect)
- Block 2 = Cover art styles
- Block 3 = Feature options

### Countdown timer
Find this line and set your real end date:
```js
const endDate = new Date(Date.now() + 3 * 24 * 60 * 60 * 1000);
```
Replace with a real date like:
```js
const endDate = new Date('2025-08-01T00:00:00');
```

### Fake vote counts
Edit `baseCounts` array — these are the fake tallies shown after someone votes.

### The "wrong" numbers shown in glitch phase
Edit `wrongCounts` — these appear crossed out with red ERROR/???/REDACTED values during the twist reveal.

### Secret zone
The invisible clickable area is in the bottom-right corner (12x12px). 
Triple-click it to trigger the secret toast message.
Uncomment `window.location.href = '/secret'` to send them to a secret page.

## The Twist Flow

1. Fan votes on all 4 questions
2. Clicks "SUBMIT VOTES"  
3. Brief "RECORDING..." animation  
4. Screen glitches → Phase 2 overlay appears
5. Results show with corrupted/wrong numbers crossed out in red
6. Final message: **"THIS WAS NEVER YOUR CHOICE"**

## Want to add a real backend?

For real vote storage, plug in any of these:
- [Supabase](https://supabase.com) (free tier, 5min setup)
- [Vercel KV](https://vercel.com/storage/kv) (built into Vercel)
- A simple `/api/vote` serverless function

The fake counts are intentionally designed to look real — that's part of the bit.
