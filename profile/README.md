Embed interactive learning activities and documents on a website without installing any package or application.

**Embed My** creates an iframe snippet that teachers, instructional designers, and website owners can paste into a page they already manage.
The only supported format for now is **H5P** (`.h5p`) packages. PDF embedding is planned.

You do **not** need to install Moodle, WordPress, an H5P server, or a JavaScript package on the site where you paste the iframe. Use it for a teaching portfolio, a school, course or department website, a public resource page, a blog or documentation site, or any CMS page that accepts an iframe but cannot install an H5P plugin.

## Quick start

You need:

1. An H5P package (`.h5p`) that you are entitled to share.
2. A public **HTTPS** URL for that file that allows cross-origin requests (**CORS**), for example `https://embed-my.github.io/samples/quiz.h5p`.
3. A page served over **HTTPS** where you can paste HTML iframe markup.

Then:

1. Open [Embed My](https://embed-my.org/) and choose **H5P package**.
2. Paste the direct URL ending in `.h5p` and preview the activity.
3. Choose display options, copy the generated snippet, and paste it into your site's HTML/embed block.

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

Use the exact code Embed My generates, and open the published page in a private window to check it before sharing.

## Guides

| Guide | What it covers |
|---|---|
| [Embedding an activity](https://embed-my.org/docs/embedding) | Display options, the resizer script, browser support, sites that restrict iframes, and a pre-publish checklist |
| [Preparing and hosting packages](https://embed-my.org/docs/hosting-packages) | Where to put the `.h5p` file, CORS and Range headers, packages without libraries, slow video |
| [Privacy and security](https://embed-my.org/docs/privacy-and-security) | What the iframe isolates, what is saved, cookies, and what you still need to protect |
| [Results, xAPI and grades](https://embed-my.org/docs/results-and-xapi) | Why scores do not reach a gradebook, and how a page can receive xAPI statements |
| [Accessibility](https://embed-my.org/docs/accessibility) | What Embed My provides and what activity authors must check |
| [Troubleshooting](https://embed-my.org/docs/troubleshooting) | Common problems and how to report one |

## Open source and licences

The H5P player behind Embed My is [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player), an open-source, browser-only H5P player: it reads the `.h5p` archive in the browser through a Service Worker, with no server-side extraction. Its repository documents the player in depth.

The player's own code is MIT. The H5P core runtime it loads inside the frame is [h5p-php-library](https://github.com/h5p/h5p-php-library), GPL-3.0, as vendored by [h5p-standalone](https://github.com/tunapanda/h5p-standalone) and published as [`@missing-elements/h5p-runtime`](https://www.npmjs.com/package/@missing-elements/h5p-runtime); its licence and notices are served beside it at [runtime-LICENSE.txt](https://embed-my.github.io/assets/runtime-LICENSE.txt) and [runtime-NOTICE.txt](https://embed-my.github.io/assets/runtime-NOTICE.txt). The player's [NOTICE.md](https://github.com/missing-elements/h5p-offline-player/blob/main/packages/player/NOTICE.md) gives the full account, including zip.js's BSD notice. The content types inside a package carry their own licences, which the **Rights of use** button shows when the toolbar is enabled.

The project is independent and is not affiliated with or endorsed by H5P Group. “H5P” is a trademark of H5P Group.

## Get help

For bug reports and feature requests, open an issue where the problem lives: the activity not playing or playing wrong is the player, [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player/issues); the snippet, the preview, the page or the guides are the [website](https://github.com/embed-my/website/issues); the frame itself (`/h5p` on embed-my.github.io) or the sizing script is the [player origin](https://github.com/embed-my/embed-my.github.io/issues).
The [troubleshooting guide](https://embed-my.org/docs/troubleshooting#reporting-a-problem) lists what to include.
