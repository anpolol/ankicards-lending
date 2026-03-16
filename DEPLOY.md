# GitHub Pages deploy

## 1. Push the repository

```bash
git add .
git commit -m "Add GitHub Pages deployment"
git push origin main
```

## 2. Enable GitHub Pages

In GitHub repository settings:

1. Open `Settings -> Pages`
2. In `Build and deployment`, choose `GitHub Actions`

After that, each push to `main` will redeploy the site.

## 3. Connect a custom domain

Create a file named `CNAME` in the project root with one line:

```text
yourdomain.com
```

If you want `www`, use:

```text
www.yourdomain.com
```

Then update these tags in `index.html` to the final site URL:

- `og:url`
- `link rel="canonical"`
- JSON-LD field `url`

## 4. DNS records at your registrar

For apex domain (`yourdomain.com`):

```text
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
```

For `www.yourdomain.com`:

```text
CNAME www   anpolol.github.io
```

Recommended setup:

- set `www.yourdomain.com` as the custom domain in GitHub Pages
- redirect apex (`yourdomain.com`) to `www` through your registrar or DNS provider if they support URL forwarding / ALIAS / ANAME

## 5. HTTPS

After DNS starts resolving and GitHub Pages sees the domain:

1. Open `Settings -> Pages`
2. Wait until the domain is verified
3. Enable `Enforce HTTPS`
