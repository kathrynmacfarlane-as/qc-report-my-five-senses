# How to publish this report on GitHub Pages

This folder is a complete, ready-to-publish GitHub Pages site. Follow these steps once and you'll have a permanent URL you can send to stakeholders.

---

## Option A — Web UI (easiest, no command line)

1. Go to <https://github.com/new> and create a **public** repo called `qc-report-my-five-senses`.
   - Leave "Add a README" unchecked (this folder already has one).
2. On the new empty-repo page, click **"uploading an existing file"**.
3. Drag these four files from this folder into the upload area:
   - `index.html`
   - `README.md`
   - `report.md`
   - `PUBLISH.md` (optional, for your reference)
4. Click **Commit changes**.
5. Go to the repo's **Settings → Pages** (left sidebar).
6. Under *Source*, pick **Deploy from a branch**. Under *Branch*, pick **`main`** and **`/ (root)`**. Click **Save**.
7. Wait ~30 seconds. GitHub will show a green banner with your live URL:
   ```
   https://<your-username>.github.io/qc-report-my-five-senses/
   ```
   That's the link to send to stakeholders.

---

## Option B — Command line (if you have `gh` installed and authenticated)

Open a Terminal, `cd` into this folder, then run:

```bash
# Replace <your-username> with your GitHub handle
cd "/path/to/qc-report-my-five-senses"

git init -b main
git add .
git commit -m "Add QC report for My Five Senses"

gh repo create qc-report-my-five-senses --public --source=. --push
gh api -X POST /repos/:owner/qc-report-my-five-senses/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

After a minute, your URL is:
```
https://<your-username>.github.io/qc-report-my-five-senses/
```

---

## Using an existing repo instead

If you'd rather host this under a repo you already own (e.g. `readings-a-breeze`), put this folder at a subpath like `docs/qc/my-five-senses/` and enable Pages from the `docs` folder. The URL will be:
```
https://<your-username>.github.io/readings-a-breeze/qc/my-five-senses/
```

---

## Private / stakeholder-only link

GitHub Pages from a free account **requires a public repo**. If you need the report to be private:

- **GitHub Gist (secret):** create a secret gist with `index.html` — gives you a secret URL, but the HTML won't render (only the source shows). Not recommended for this report.
- **GitHub Pro / Enterprise:** supports Pages from a private repo.
- **Drop-in alternatives:** Netlify Drop (<https://app.netlify.com/drop>) lets you drag this folder onto the page and get a private-ish `*.netlify.app` URL in 10 seconds.

---

## Updating the report later

Every time you want to edit the report, just commit a new version of `index.html` (and `report.md` if you want the markdown version to match). GitHub Pages redeploys automatically within a minute. The URL stays the same.
