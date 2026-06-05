# DepotTax Blog

Hugo-Blog über IBKR-Steuerthemen für österreichische Privatanleger.

**Live:** https://blog.depottax.at

## Themen

Praxis-Guides für Privatanleger, die ihr IBKR-Konto in der österreichischen Steuererklärung deklarieren müssen:

- E1kv-Beilage richtig ausfüllen (KZ 994, 892, 998, 937, 891 etc.)
- FlexQuery-Konfiguration bei IBKR / CapTrader / LYNX
- DBA-Quellensteuer-Anrechnung (USA, Irland, etc.)
- Vergleich Broker-Tarife AT-Markt
- ETF-/Fonds-Spezifika (OeKB-Meldefonds vs. NMF, ausschüttungsgleiche Erträge)

## Stack

- **Hugo** mit PaperMod-Theme
- **GitHub Pages** als Host (Actions-Workflow `gh-pages.yml`)
- **Custom Domain:** `blog.depottax.at` (Cert via GitHub-Pages Let's Encrypt)

## Lokal bauen

```bash
git clone https://github.com/heilquell/blog-ib-georgshost.git
cd blog-ib-georgshost
hugo server -D
# → http://localhost:1313
```

## Neuen Post schreiben

```bash
hugo new posts/mein-thema.md
# Front-Matter editieren, draft: false setzen
git add -A && git commit -m "post: mein thema"
git push  # GitHub Actions baut + deployed automatisch
```

## Konfiguration

- `hugo.toml` — baseURL, Menü, Theme-Settings
- `content/posts/` — Markdown-Posts mit YAML-Front-Matter
- `static/CNAME` — Custom-Domain-Konfiguration für GitHub Pages

## Verwandte Repos

- **Tool:** https://depottax.at (privates Repo, nicht öffentlich)
