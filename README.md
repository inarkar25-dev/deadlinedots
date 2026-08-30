# Deadline Dots website

A static 3-page marketing, support, and privacy-policy site for the Deadline Dots iOS app.

No backend, no build step, no accounts, no analytics, no cookies, and no trackers. Just HTML and CSS.

## Files

- `index.html` — marketing / landing page
- `support.html` — App Store support URL
- `privacy.html` — App Store privacy policy URL
- `styles.css` — shared stylesheet for all three pages
- `README.md` — this file

## Preview it locally

You don't need to install anything to look at the site — you can open `index.html` directly in a browser. But some browsers restrict local file links slightly, so it's more reliable to serve it with a tiny local server:

**If you have Python installed (macOS ships with it):**

```bash
cd path/to/deadline-dots
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

**If you have Node.js installed:**

```bash
cd path/to/deadline-dots
npx serve .
```

Then open the URL it prints (usually `http://localhost:3000`).

Press `Ctrl+C` in the terminal to stop the server when you're done.

## Before you publish

Two placeholders need to be replaced:

1. **`YOUR_SUPPORT_EMAIL`** — appears in `support.html` (in the "Still need help?" section) and `privacy.html` (in the "Contact" section). Replace it with your real support email address in both files, in both the visible text and the `mailto:` link, e.g.:

   ```html
   <a href="mailto:support@yourdomain.com">support@yourdomain.com</a>
   ```

2. **The App Store link** — `index.html` has two buttons that link to Deadline Dots on the App Store. Both currently point to `#` as a placeholder:

   ```html
   <a class="btn btn-primary" href="#" ...>Download on the App Store</a>
   ```

   Once your app is live, replace `href="#"` on both buttons with your real App Store URL, e.g.:

   ```html
   <a class="btn btn-primary" href="https://apps.apple.com/app/idXXXXXXXXX" ...>Download on the App Store</a>
   ```

## Privacy and data collection

This site itself collects nothing. There is no analytics script, no cookie banner, no third-party embed, and no tracking pixel anywhere in the HTML, CSS, or hosting setup described below. The `privacy.html` page describes the app's data practices, not the website's, but both are equally free of tracking.

## Deploy for free

### Option A — GitHub Pages

1. Create a new repository on GitHub (e.g. `deadline-dots-website`). It can be public or private (GitHub Pages on a private repo requires a paid plan, so public is simplest for a free deployment).
2. On your computer, open a terminal in the `deadline-dots` folder and run:

   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/deadline-dots-website.git
   git push -u origin main
   ```

3. On GitHub, go to your repository's **Settings** tab.
4. In the left sidebar, click **Pages**.
5. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
6. Set **Branch** to `main` and the folder to `/ (root)`, then click **Save**.
7. Wait a minute or two, then refresh the page. GitHub will show your live URL, typically:

   ```
   https://YOUR_USERNAME.github.io/deadline-dots-website/
   ```

8. Your three pages will be available at:
   - `https://YOUR_USERNAME.github.io/deadline-dots-website/index.html` (also the root URL)
   - `https://YOUR_USERNAME.github.io/deadline-dots-website/support.html`
   - `https://YOUR_USERNAME.github.io/deadline-dots-website/privacy.html`

   These are the two URLs you'll paste into App Store Connect for **Support URL** and **Privacy Policy URL**.

### Option B — Netlify

**Drag-and-drop, no account needed to start:**

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop) in your browser.
2. Drag the whole `deadline-dots` folder (the one containing `index.html`) onto the page.
3. Netlify uploads the files and gives you a live URL immediately, like:

   ```
   https://random-name-123.netlify.app
   ```

4. Optional: create a free Netlify account to keep the site, rename the subdomain, and update it later instead of dragging a new folder each time.

**Alternative — connect a GitHub repository:**

1. Push the site to GitHub as described in Option A, steps 1–2.
2. Go to [app.netlify.com](https://app.netlify.com) and sign up or log in.
3. Click **Add new site → Import an existing project**.
4. Choose GitHub and select your `deadline-dots-website` repository.
5. Leave the build command empty and set the publish directory to `.` (the repository root), since this site has no build step.
6. Click **Deploy site**.

Either way, once deployed, your Support and Privacy URLs will look like:
- `https://your-site-name.netlify.app/support.html`
- `https://your-site-name.netlify.app/privacy.html`
