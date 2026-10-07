# Privacy and security

## What Embed My isolates

H5P packages contain JavaScript libraries. The player runs them inside the Embed My iframe, on `embed-my.js.org`, rather than on the website where you paste the iframe. A package loaded through Embed My therefore does not run as JavaScript on your portfolio, school site, or CMS origin, and cannot read that site's cookies or storage. This is especially useful when the embedding site cannot safely host its own H5P player files.

## What it does not isolate

Browsers give the Embed My frame separate storage for each site that embeds it, so what a package does inside the frame stays with your site's embeds. Within that, every package embedded through Embed My on the same site shares one store: a package can read what other packages on that site have extracted there, which is their files and package URLs.

Embed only packages you trust, as you would any script.

## What is saved

Nothing between visits. Reloading the page starts the activity over, and answers are not kept anywhere. Embed My stores no learner records.

## Cookies and tracking

Embed My is a minimal, public player origin: it has no accounts, serves no advertising, and sets no application cookies. The embedding website controls its own privacy notice and any analytics it places around the iframe.

H5P content itself may contact services named by the package, such as YouTube, Vimeo, Google Fonts, MathJax, or an organization-hosted media service. Review a package and its third-party content before publishing it.

## What you should still protect

- **Share only packages you are allowed to publish.** An H5P package can include copyrighted media, learner-facing data, and JavaScript libraries.
- **Do not put secret package URLs in an embed.** The package URL appears in the iframe address and can be visible in browser history, page source, server logs, and referrer-related systems. A signed URL that expires keeps working only for visitors whose browser already opened it; new visitors get an error.
- **Use HTTPS.** The page containing the iframe must use HTTPS (or `localhost` during development). The player needs a secure context for its Service Worker.
- **Treat the package host as public.** Anyone who can view the page can discover and request the package URL.
- **Avoid personal data in the package.** Embed My is a player, not a learner-record store.

Do not use Embed My to embed private learner records, passwords, API keys, or confidential course material.

## Reporting a vulnerability

Vulnerabilities in the player itself are handled under the h5p-offline-player [security policy](https://github.com/missing-elements/h5p-offline-player/blob/main/SECURITY.md).
