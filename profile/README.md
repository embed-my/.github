Embed interactive H5P activities on a website without installing any plugin or application there.

**Embed My** turns a link to an H5P package (`.h5p`) into an iframe snippet that teachers, instructional designers and website owners paste into a page they already manage: a teaching portfolio, a school, course or department website, a public resource page, a blog, or any CMS page that accepts an iframe but cannot take an H5P plugin. H5P is the only format for now; PDF documents are planned.

## What you need

1. **A complete `.h5p` package you are allowed to share.** Exports from H5P.com and h5p.org usually leave the libraries out and will not play anywhere else; choose a complete export, or check the file in the preview first. See [Preparing and hosting packages](https://embed-my.org/docs/hosting-packages#packages-and-library-files).
2. **Somewhere to host the file.** Embed My keeps no copy, so the `.h5p` has to sit on a web host that serves it over `https://` to any site (a header called CORS). Google Drive and OneDrive share links do not; the free hosts below do, and the [hosting guide](https://embed-my.org/docs/hosting-packages#free-places-to-put-the-file) has the steps for each.
3. **A page served over `https://` where you can paste HTML**, such as an HTML, Embed or Custom HTML block.

### Free places to put the file

Checked on 9 October 2026; the [guide](https://embed-my.org/docs/hosting-packages#free-places-to-put-the-file) has the steps and what does not work.

| Host | Free allowance | You upload with | Starts before the download ends | Largest file |
|---|---|---|---|---|
| **Dropbox** Basic, with one edit to the link | 2 GB; 20 GB of link traffic a day | the Dropbox website or app | yes | no stated limit |
| **GitHub** public repository | 1 GB per repository | the GitHub website | yes | 25 MB from the browser |
| **Zenodo** | 50 GB per record | the Zenodo website | yes | no stated limit |
| **Backblaze B2** | 10 GB | the Backblaze website, after one CORS setting | yes | no stated limit |
| **Cloudflare Pages** | 500 uploads a month | drag and drop in the dashboard | no | 25 MB |

## Quick start

1. Open [embed-my.org](https://embed-my.org/) and paste the direct link to your `.h5p` file. If it plays in the preview, it will play on your page.
2. Set a title and the display options, and copy the snippet.
3. Paste it into your page's HTML block, publish, and open the page in a private window to check it.

```html
<iframe
  src="https://embed-my.github.io/h5p?src=https://embed-my.github.io/samples/quiz.h5p"
  title="Sample quiz"
  loading="lazy"
  allow="fullscreen"
  style="width: 100%; min-height: 540px; border: 0"
></iframe>
<script src="https://embed-my.github.io/h5p-resizer.js"></script>
```

Use the exact code Embed My generates. The snippet points at `embed-my.github.io`, an address the project keeps for as long as it is on GitHub, so an embed does not depend on the `embed-my.org` domain.

## What it is not

- **Not file hosting.** Your package stays on your host; Embed My only points at it.
- **Not a gradebook.** No accounts, no learner records, and scores reach no LMS. A developer can [receive xAPI statements](https://embed-my.org/docs/results-and-xapi) on the embedding page.
- **Not saved progress.** Reloading the page starts the activity over.
- **Not for private material.** The package link is visible in your page's HTML, so treat the file as public.

## Repositories

| Repository | What it is |
|---|---|
| [website](https://github.com/embed-my/website) | [embed-my.org](https://embed-my.org/): the page that writes the snippet, with the live preview, and the guides under `/docs` |
| [embed-my.github.io](https://github.com/embed-my/embed-my.github.io) | The player origin the snippet points at: the `/h5p` frame, `h5p-resizer.js` and the sample packages |
| [.github](https://github.com/embed-my/.github) | This profile and the organisation's settings |

All three are MIT. The player inside the frame is [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player), an open-source, browser-only H5P player by the same author: it reads the `.h5p` archive in the browser through a Service Worker, with no server-side extraction.

## Guides

| Guide | What it covers |
|---|---|
| [Embedding an activity](https://embed-my.org/docs/embedding) | Display options, the resizer script, browser support, sites that restrict iframes, and a pre-publish checklist |
| [Preparing and hosting packages](https://embed-my.org/docs/hosting-packages) | Where to put the `.h5p` file, CORS and Range headers, packages without libraries, slow video |
| [Privacy and security](https://embed-my.org/docs/privacy-and-security) | What the iframe isolates, what is saved, cookies, and what you still need to protect |
| [Results, xAPI and grades](https://embed-my.org/docs/results-and-xapi) | Why scores do not reach a gradebook, and how a page can receive xAPI statements |
| [Accessibility](https://embed-my.org/docs/accessibility) | What Embed My provides and what activity authors must check |
| [Troubleshooting](https://embed-my.org/docs/troubleshooting) | Common problems and how to report one |

## Licences

The player is MIT. The H5P core runtime it loads inside the frame comes from [h5p-php-library](https://github.com/h5p/h5p-php-library) and is GPL-3.0, published as [`@missing-elements/h5p-runtime`](https://www.npmjs.com/package/@missing-elements/h5p-runtime); its [licence](https://embed-my.github.io/assets/runtime-LICENSE.txt) and [notices](https://embed-my.github.io/assets/runtime-NOTICE.txt) are served beside it, and the player's [NOTICE.md](https://github.com/missing-elements/h5p-offline-player/blob/main/packages/player/NOTICE.md) gives the full account. The content inside a package carries its own licence, which the **Rights of use** button shows when the toolbar is on.

The project is independent and is not affiliated with or endorsed by H5P Group. “H5P” is a trademark of H5P Group.

## Get help and support

Open an issue where the problem lives: the activity not playing or playing wrong is the player, [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player/issues); the snippet, the preview, the page or the guides are the [website](https://github.com/embed-my/website/issues); the frame itself or the sizing script is the [player origin](https://github.com/embed-my/embed-my.github.io/issues). Not sure? Pick the website. The [troubleshooting guide](https://embed-my.org/docs/troubleshooting#reporting-a-problem) lists what to include.

Embed My is free, with no accounts and no advertising. If it saved you a plugin or a licence, the [support section](https://embed-my.org/#support) on the site lists ways to give something back.
