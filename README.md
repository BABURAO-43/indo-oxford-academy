# Indo Oxford Academy — Deploy-ready Site

This folder contains a ready-to-deploy static website for **Indo Oxford Academy**.

## Contents
- `index.html` — full single-file responsive site (landing + portal + teacher profile).
- `README.md` — this file.
- `CNAME` — optional file to set custom domain (create this file and add your domain inside before publishing).

---

## Option A — Publish on **GitHub Pages** (recommended)

1. Create a new GitHub repository (public) — e.g. `indo-oxford-academy`.
2. In your local machine, initialize git and push these files:
   ```bash
   git init
   git add .
   git commit -m "Initial site: Indo Oxford Academy"
   git branch -M main
   git remote add origin https://github.com/<your-username>/indo-oxford-academy.git
   git push -u origin main
   ```
3. On GitHub, go to **Settings > Pages** (or **Settings > Pages & deployments**).
   - Under "Build and deployment" choose **Deploy from a branch** → `main` branch → `/ (root)` folder.
   - Save. GitHub will publish the site at `https://<your-username>.github.io/indo-oxford-academy/` within a minute.

4. If you want the site at the root of your GitHub Pages user site (i.e., `https://<your-username>.github.io/`), name the repository exactly `<your-username>.github.io` and push the same files there.

5. To use a custom domain (e.g., `indooxfordacademy.in`) see Cloudflare steps below. Alternatively, create a file named `CNAME` (no extension) containing _only_ your custom domain (one line) and add it to the repo root — GitHub Pages will pick it up.

---
## Option B — Connect a custom domain via **Cloudflare** (recommended: free plan)

1. Buy/own the domain from any registrar (Namecheap, GoDaddy, BigRock, Google Domains, etc.).
2. Create an account on Cloudflare and add your domain. Cloudflare will ask you to change the registrar's nameservers to Cloudflare's nameservers (this is done at the registrar panel).
3. On Cloudflare DNS, add records to point your domain to GitHub Pages:
   - For an **apex/root domain** (e.g., `indooxfordacademy.in`):
     - Add **A** records for the following IPv4 addresses (GitHub Pages): `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
     - Proxy status should be **Disabled** (click the orange cloud to make it gray) — GitHub Pages requires DNS-only records.
   - For a **www** subdomain (`www.indooxfordacademy.in`):
     - Add a **CNAME** record: `www` → `<your-username>.github.io.` (note the trailing dot is optional).
     - Proxy status: **Disabled** (DNS-only).
4. In your GitHub Pages repository **Settings > Pages**, set the custom domain to your domain (e.g., `indooxfordacademy.in`). GitHub will provision HTTPS (via Let's Encrypt) after DNS is set correctly.
5. In Cloudflare **SSL/TLS** set the mode to **Full** (or **Full (strict)** if you have a valid certificate on origin). Ensure Always Use HTTPS is enabled in Cloudflare to redirect HTTP → HTTPS.
6. Wait for DNS propagation (usually minutes; sometimes up to 24 hours). Your site should be live and secured with HTTPS.

> Important: When using Cloudflare in front of GitHub Pages, keep the DNS entries as **DNS only (not proxied)** to allow GitHub's certificate and GitHub Pages to serve content properly. If you enable Cloudflare proxy (orange cloud), GitHub Pages SSL may fail.

---
## Quick checklist before publish
- Replace contact phone/email placeholders in `index.html` with real values.
- If you want the site to serve from the root domain, create a `CNAME` file (containing your custom domain) and add to the repo root.
- To host at `https://<your-username>.github.io/`, name the repo `<your-username>.github.io`.
- To use Cloudflare, follow steps above and ensure records are DNS-only.

---
## Need help?
If you want, I can:
- Create the GitHub repo and push the files (you'd need to share GitHub access or create a repo and invite me). **I cannot access your accounts**, but I can provide exact commands and files ready to paste.
- Make a version with local images embedded (100% offline-ready).
- Customize branding (logo, colors, text) before you publish.

Good luck — launch karte hi link bhej dena, main check kar dungi and suggest micro-fixes.
