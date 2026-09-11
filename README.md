# MekongNet Lucky Draw

A self-contained web app for running **Facebook giveaway draws**. Paste the comments from a giveaway post, set the rules for who qualifies, review and adjust the list by hand, then draw winners on a full-screen, brand-styled reveal with confetti and fireworks.

Everything runs in the browser. **No login, no server, no Facebook API, nothing uploaded.**

---

## Quick start

**Option A — just open it**
Download the repo and double-click `index.html`. It opens with sample data so you can try it immediately.

**Option B — host it for the team (recommended)**
Turn on **GitHub Pages** (see [Deploy](#deploy-to-github-pages)) and share the link. Anyone with the link can run a draw.

---

## How to run a draw

1. **Get the comments.** On your Facebook post, copy the comments. Paste them into the box, **one per line**, formatted:
   ```
   Name: their comment text
   ```
2. Click **Review comments**. The app splits everyone into **Qualified** and **Not qualified**, showing *why* each person failed (e.g. "only 2 tags").
3. **Adjust if needed.** Click **move** on any card to override the rules — you always have the final say.
4. Set **Winners** (default 5) and click **🎉 Draw winners (full screen)**.
5. The winners reveal one-by-one on the branded screen. Use **↻ Remove & redraw** on any card, or **Draw again** to re-roll. Press **Esc** or **✕** to exit.

> **Tip:** For the cleanest screen-recording, click Draw — it triggers true browser full-screen (hides tabs/toolbar).

---

## Set the challenge rules (⚙ Settings → Challenge rules)

Each campaign is different, so the qualifying mechanic is fully configurable. Turn any rule on/off and set its value. A comment qualifies only when **all enabled rules pass**.

| Rule | What it checks |
| --- | --- |
| **Must include numbers** | At least N numbers. Counts Arabic (`1 2 3`) **and** Khmer (`១ ២ ៣`) numerals. |
| **Must tag friends** | At least N friend tags. Detects `@mentions` and typed names (choose sensitivity: `@` only / `@ + names` / `@ + any Capitalized word`). |
| **Must contain a word / hashtag** | The comment must contain a required word or hashtag, e.g. `#MekongNet` (case-insensitive). |
| **Minimum comment length** | Filters out one-word or empty entries. |
| **One entry per person** | Merges repeat commenters by name (recommended). |

Turn everything off and everyone qualifies.

---

## Customize / upload a different winner screen (⚙ Settings → Winner screen)

Campaigns change, so the reveal screen is editable and swappable:

- **Accent color** — recolors buttons, badges, and name bars.
- **Eyebrow, headline, subtitle, prize pill, thank-you** text. In the headline, `{n}` = winner count and `{kh}` = the count as a Khmer numeral (e.g. `អ្នកឈ្នះទាំង {kh}នាក់` → `អ្នកឈ្នះទាំង ៥នាក់`).
- **Logo**, **prize image**, and an optional **full background poster** — upload your own for each campaign.
- **Presets** — save several winner screens and switch between them anytime (stored in your browser).
- **Export / Import config** — download the whole setup (rules + screen + images) as a JSON file to share with the team or commit to this repo. Import to apply it.

### Sharing a campaign setup with the team
One person sets up the rules + winner screen, clicks **Export config**, and either:
- sends the JSON file to teammates (they **Import config**), **or**
- replaces `config.json` in this repo with it and commits — everyone who opens the hosted page then gets that setup by default.

---

## `config.json`

The app loads settings in this order (later wins): built-in defaults → `config.json` (this repo) → your in-browser edits. So `config.json` is the **team default**; local tweaks never overwrite it for others. Editing settings in the app and clicking **Export config** produces a new `config.json` you can commit.

> Opening `index.html` directly from disk (`file://`) can't read `config.json` (browser security). It still works — it falls back to the defaults baked into `index.html`. When hosted on GitHub Pages, `config.json` loads normally.

---

## Deploy to GitHub Pages

1. Push this repo to GitHub (see the repo's setup notes).
2. Repo **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → **Save**.
3. Wait ~1 minute. Your tool is live at `https://<your-org>.github.io/<repo-name>/`.
4. Share that link with the team.

---

## Getting comments out of Facebook

Facebook blocks apps from reading comments directly, so **paste** is the input method. To copy comments: open the post, expand "View more comments" to load them, select the comment area, and copy. Then paste into the app.

(If you run this with Claude + the browser tools, Claude can auto-extract the comments from a post link into the paste box — Facebook still requires a human to scroll the comments to load them all.)

---

## Privacy

The app never sends data anywhere. Pasted names and any images you upload stay in your browser (and in a `config.json` only if you choose to commit one). Don't commit real entrant names to a public repo.

## License

MIT — see [LICENSE](LICENSE).
