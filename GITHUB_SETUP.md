# GitHub Pages deployment — www.sepehrta.com

## Files
- `index.html`: website (HTML/CSS/JS in one file)
- `CNAME`: selected custom domain `www.sepehrta.com`
- `.nojekyll`: disables Jekyll processing
- `sitemap.xml`, `robots.txt`: search-engine hints

**Before publishing:** add your portrait `sepehr.jpg` and your current CV named `Sepehr_Tabrizchi_CV.pdf` to this same root directory. These are referenced by the HTML but not bundled.

## Publish
1. Log in to GitHub as `SepehrTa`.
2. Create a **public** repository called `SepehrTa.github.io` (case-insensitive match to GitHub username), or use another repository if you already have a personal Pages site.
3. Use Add file > Upload files to upload all files from this folder (including hidden `.nojekyll` if possible). Do not upload the ZIP itself or an enclosing folder.
4. In the repo, go to Settings > Pages > Build and deployment, choose **Deploy from a branch**, branch `main`, folder `/(root)` and click **Save**.
5. Confirm the site works at `https://sepehrta.github.io/` before pointing the custom domain. If the root `CNAME` already activates the custom domain/redirects and interferes with preview, temporarily remove it until domain setup is ready.
6. In Settings > Pages > Custom domain enter `www.sepehrta.com`, then Save.
7. In Cloudflare DNS, set `www` CNAME to `sepehrta.github.io` and set `@` to all four GitHub Pages A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`. DNS only (gray cloud) initially. Remove conflicting records for `@` and `www`, not email MX/TXT or unrelated records.
8. Disable/remove any old Cloudflare Worker custom-domain binding or route on `www.sepehrta.com` and `sepehrta.com` so it does not intercept traffic.
9. After DNS resolves and HTTPS becomes available, enable Enforce HTTPS in GitHub Settings > Pages.

Official docs: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

The custom domain and repo name should match the actual GitHub account that will host the site. If you use a different owner/organization, replace `sepehrta.github.io` with that owner's exact Pages default host.
