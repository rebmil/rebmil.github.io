claude code context for working on this repo. Read before making changes.

Stack and hosting

Repo: rebmil/rebmil.github.io, branch main
Host: GitHub Pages, deploy from main / root
Domain: rebeccagmiller.com, registered at Cloudflare
DNS: Cloudflare, four A records on apex → 185.199.108–111.153, all set to DNS only (grey cloud, NOT proxied)

No build step. Plain HTML + one CSS file. No framework, no bundler, no package.json, no npm. Do not introduce one.

Cloudflare proxying (orange cloud) breaks GitHub's TLS cert issuance. Records must stay DNS-only.

Do not add a Cloudflare Workers project. Cloudflare is registrar + DNS only; GitHub Pages is the host.

The CNAME file in the repo root contains rebeccagmiller.com. Clearing the custom domain field in GitHub settings deletes this file. Don't remove it.

File structure

index.html      landing page + work log
about.html
styles.css      all styling for every page
work/*.html     one file per memo
CNAME           rebeccagmiller.com

Every HTML file links the stylesheet as /styles.css — absolute path with a leading slash. Relative paths break for anything in work/, which looks for /work/styles.css and silently renders unstyled. Same rule for all internal links: /about.html, not about.html.

Defined in styles.css as CSS custom properties. Change colors there, never inline.

The work log on index.html is a run log, not a card grid. Each entry carries a mono status field showing real state: Published, Drafting, Outlined, Data logged, unwritten. Honest gaps are the point — they read as a person with a pipeline and a standard. Never pad the log with filler entries to make it look fuller, and keep statuses accurate.