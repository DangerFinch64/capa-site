# CAPA Resolve — Public Website

Static public website for [caparesolve.com](https://caparesolve.com), deployed on Cloudflare Pages.

Built with plain HTML and CSS — no framework, no build step, no JavaScript.

---

## File structure

```
capa-site/
├── index.html              → /
├── about/index.html        → /about
├── contact/index.html      → /contact
├── privacy/index.html      → /privacy
├── terms/index.html        → /terms
├── security/index.html     → /security
├── hipaa/index.html        → /hipaa
├── compliance/index.html   → /compliance
├── cookies/index.html      → /cookies
├── acceptable-use/         → /acceptable-use
│   └── index.html
├── data-requests/          → /data-requests
│   └── index.html
├── subprocessors/          → /subprocessors
│   └── index.html
├── status/index.html       → /status
├── faq/index.html          → /faq
├── styles.css              (shared stylesheet)
├── _headers                (Cloudflare Pages security headers)
└── README.md
```

Each route uses a folder with an `index.html` so that Cloudflare Pages (and any static host) serves clean URLs without `.html` extensions — e.g. `/about` not `/about.html`.

---

## Local preview

No build step is required. Any static file server works.

**Option 1 — Python (built-in, no install needed):**
```bash
cd capa-site
python3 -m http.server 8080
# Open http://localhost:8080
```

**Option 2 — Node (npx serve):**
```bash
cd capa-site
npx serve .
# Open the URL shown in the terminal
```

**Option 3 — VS Code Live Server extension:**
Right-click `index.html` → Open with Live Server.

Note: The `_headers` file only takes effect on Cloudflare Pages, not local servers.

---

## Deploying to Cloudflare Pages

### First deploy (via dashboard)

1. Push this repository to GitHub (or GitLab).
2. Go to [Cloudflare Pages](https://pages.cloudflare.com) → Create a project.
3. Connect your repository.
4. Set the following build settings:
   - **Framework preset:** None
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/` (root of the repository, or the folder name if this is a subfolder)
5. Click **Save and Deploy**.

### Publish directory

Set the publish directory to the root of this folder (`.` or the folder path if nested in a monorepo).

Cloudflare Pages will automatically pick up `_headers` and apply security headers globally.

### Custom domain

After the first deploy:
1. Go to your project → Custom domains → Add domain.
2. Enter `caparesolve.com`.
3. Follow the DNS instructions (typically add a CNAME or use Cloudflare's nameservers if the domain is already on Cloudflare).

### Subsequent deploys

Push to your connected branch (e.g. `main`). Cloudflare Pages automatically deploys on every push.

---

## Updating content

- **Shared styles:** edit `styles.css`.
- **Security headers:** edit `_headers`.
- **Any page:** edit the corresponding `index.html` in its folder.
- **Header/footer/nav:** currently duplicated across pages — update all files when changing shared elements. A future pass could template these with a build tool if needed.

---

## Legal review note

The Privacy Policy, Terms of Use, HIPAA, Compliance, Cookies, Acceptable Use, Data Requests, and Subprocessors pages are professional drafts suitable for a pre-launch website. They should be reviewed by qualified legal counsel before the platform moves into full production or begins handling real user data or healthcare workflows.
