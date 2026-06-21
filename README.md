# TrailMate DMV 🥾

A personal hiking app for weekend trails (3–8 mi) around Maryland, Northern Virginia, DC, and nearby — with parking, hours, drive times from home, waterfalls, dams, ruins, camping, family extras, live "where to eat" lookups, a personal hiked-tracker, and per-trail notes.

Everything runs in a single `index.html` file. Your check-offs and notes save in your browser and (once you connect GitHub) auto-save to a data file in this repo so they sync across devices.

---

## 1. Put it on GitHub (hosting)

1. Sign in to GitHub → top-right **+** → **New repository**.
2. Name it (e.g. `trailmate-dmv`). **Set it to Private** (recommended — see Security below). Click **Create repository**.
3. On the new repo page click **uploading an existing file**.
4. Drag in **`index.html`** (and this `README.md` if you like). Click **Commit changes**.

## 2. Turn on GitHub Pages (makes it a live website)

1. In the repo: **Settings** → **Pages** (left sidebar).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: **main**, folder: **/ (root)** → **Save**.
4. Wait ~1 minute, then refresh. Your live URL appears at the top, like:
   `https://<your-username>.github.io/trailmate-dmv/`
5. Open that URL on your phone/computer and bookmark it.

> Note: if the repo is **Private**, Pages requires a paid plan to publish. If you want free Pages, make the repo **Public** — but then read **Security** below carefully before connecting sync.

## 3. Connect data sync (saves your check-offs + notes into the repo)

1. Create a token: GitHub → your avatar → **Settings** → **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
   - **Resource owner:** your account
   - **Repository access:** *Only select repositories* → choose your `trailmate-dmv` repo
   - **Permissions → Repository permissions → Contents:** **Read and write**
   - Generate, then **copy the token** (starts with `github_pat_…`).
2. Open your live app → tap **⚙ Sync** (top, by the progress bar).
3. Enter:
   - **Owner:** your GitHub username
   - **Repo:** `trailmate-dmv`
   - **Branch:** `main`
   - **Data file path:** `data/trailmate-data.json`
   - **Token:** paste it
4. Tap **Connect & sync**. The status shows **Synced ✓**. From now on every check-off and note auto-commits to `data/trailmate-data.json` in your repo, and any device that opens the app pulls the latest.

---

## 🔒 Security (please read)

- The sync token lives **only in your browser's local storage** — it is never written into `index.html` or committed to the repo.
- Even so, a token in a browser on a **public** page is riskier. Best setup: **Private repo** + a **fine-grained token limited to just this one repo** with only **Contents: Read & write**. That way, worst case, the token can only edit this one hiking repo — nothing else in your account.
- Never paste the token into the code or commit it anywhere.
- You can revoke the token any time in Developer settings, then create a new one and reconnect.
- Most secure option (optional, later): put the token in a tiny serverless proxy (Cloudflare Worker / Netlify function) so it never touches the browser. Ask and this can be added.

## Updating the app later

Re-upload a new `index.html` to the repo (replace the file and commit). Your saved data lives in `data/trailmate-data.json`, so updating the app doesn't touch your check-offs or notes.
