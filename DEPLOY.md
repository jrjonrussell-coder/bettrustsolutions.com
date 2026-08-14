# StraightForecast site: deployment

## Files in this set

| File | Purpose |
|---|---|
| index.html | Homepage |
| blog.html | Writing index |
| blog-template.html | Template for new posts, placeholders in double braces |
| 404.html | Not found page |
| site.css | Shared stylesheet for every page |
| CNAME | Tells GitHub Pages the custom domain |
| favicon.ico, icon-32/180/192/512.png | Icons |
| mark-primary.svg, mark-reversed.svg | Mark, for use in documents and elsewhere |

The existing blog-1.html and any later posts are not included. They carry the
old inline styles. To convert one, replace everything between `<head>` and
`</head>` with the head block from blog-template.html, wrap the article body
in the same structure, and delete its inline `<style>` block so it picks up
site.css.

## Step 1: put the files in the repository

Repository `jrjonrussell-coder/bettrustsolutions.com`, branch `main`.
Keep the repository name. Renaming it breaks the commit history and every
API URL in the publisher skill for no benefit.

Replace index.html, blog.html and CNAME. Add site.css, 404.html,
blog-template.html and the icon files. Keep the old blog-N.html posts in place
until they are converted.

## Step 2: point the domain at GitHub Pages

In Porkbun DNS for straightforecast.gg, add four A records with host left
blank, pointing at:

    185.199.108.153
    185.199.109.153
    185.199.110.153
    185.199.111.153

Add a CNAME record with host `www` pointing to `jrjonrussell-coder.github.io`.

Do not remove the MX or TXT records that the email hosting created.

## Step 3: set the custom domain in GitHub

Repository Settings, Pages, Custom domain: enter `straightforecast.gg` and
save. Wait for the certificate to issue, then tick Enforce HTTPS. This can
take up to an hour.

## Step 4: redirect the old domain

Keep bettrustsolutions.com registered and keep its mail forwarding. The two
CFTC filings carry that address on a public docket permanently.

Point it at the holding page (bettrust-holding-page.html), or redirect the
whole domain to straightforecast.gg at the registrar.

## Step 5: update the publisher skill

`/mnt/skills/user/bettrustsolutions-blog-publisher/SKILL.md` hardcodes the old
domain in three places: the description, the header block, and the Step 7
verification URL. Change those to straightforecast.gg. Leave the API URLs
alone, since the repository name is unchanged. Replace the template in
`references/blog-template.html` with the new blog-template.html.

## Check before announcing

- straightforecast.gg loads over HTTPS
- www redirects to the apex
- The mark renders in the header on both pages
- A test email to and from JR@straightforecast.gg passes SPF, DKIM and DMARC
