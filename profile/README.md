Check that an H5P file plays, right in your browser.

**Embed My** plays an H5P package (`.h5p`) from a link, with nothing to install, and says what the player found: the content type and licence, whether the libraries were in the file, and whether the host serves it in a way browsers can use. It is for authors, teachers and developers who want to know a package works before they upload it to an LMS or share it.

As a free extra, it also writes an iframe snippet to show the activity on a public page. That comes with no guarantees: see [What it is not](#what-it-is-not).

## What you need

1. **An `.h5p` package.** Exports from H5P.com and h5p.org usually leave the libraries out; Embed My adds them from the H5P hub's library set as the activity loads, so those play too. See [Preparing and hosting packages](https://embed-my.org/docs/hosting-packages#packages-and-library-files).
2. **A public `https://` link to it.** Embed My keeps no copy, so the `.h5p` has to sit on a web host that serves it to browsers on other sites (a header called CORS). Google Drive and OneDrive share links do not; the free hosts below do, and the [hosting guide](https://embed-my.org/docs/hosting-packages#free-places-to-put-the-file) has the steps for each.

For the optional snippet you also need a page served over `https://` where you can paste HTML.

### Free places to put the file

Checked on 9 October 2026; the [guide](https://embed-my.org/docs/hosting-packages#free-places-to-put-the-file) has the steps for each. Google Drive and OneDrive share links do not work.

| Host | Free allowance | You upload with | Starts before the download ends | Largest file |
|---|---|---|---|---|
| **Dropbox** Basic, with one edit to the link | 2 GB; 20 GB of link traffic a day | the Dropbox website or app | yes | no stated limit |
| **GitHub** public repository | 1 GB per repository | the GitHub website | yes | 25 MB from the browser |
| **Zenodo** | 50 GB per record | the Zenodo website | yes | no stated limit |
| **Backblaze B2** | 10 GB | the Backblaze website, after one CORS setting | yes | no stated limit |

## Quick start

1. Open [embed-my.org](https://embed-my.org/), paste the direct link to your `.h5p` file and press **Check**.
2. Watch it play, and read what the player found under the preview. A package that plays here will very likely play in an LMS too; an LMS can run older libraries or changes of its own, so try it there before a lesson.
3. Optionally, set a title and the display options, copy the snippet, paste it into a public page's HTML block, and open the page in a private window to check it.

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

Use the exact code Embed My generates. The snippet points at `embed-my.github.io`, not at `embed-my.org`, so an embed does not depend on that domain.

## What it is not

- **Not a service with guarantees.** It is a free tool kept by one person, with no service agreement. Embeds are meant to keep working, but nothing promises it.
- **Not ready for a data-protection review.** A snippet makes each visitor's browser contact GitHub and keeps the player's files on the device; there is no data-processing agreement to sign. Many schools and companies cannot accept that under their data-protection rules. For their pages, run [the player](https://github.com/missing-elements/h5p-offline-player) on a host they control. See [Privacy and security](https://embed-my.org/docs/privacy-and-security#data-protection).
- **Not file hosting.** Your package stays on your host; Embed My only points at it.
- **Not a gradebook.** No learner records, and scores reach no LMS.
- **Not saved progress.** Reloading the page starts the activity over.
- **Not for private material.** The package link is visible in your page's HTML, so treat the file as public.

## Repositories

| Repository | What it is |
|---|---|
| [website](https://github.com/embed-my/website) | [embed-my.org](https://embed-my.org/): the page that checks a package and writes the optional snippet, and the guides under `/docs` |
| [embed-my.github.io](https://github.com/embed-my/embed-my.github.io) | The player origin the snippet points at: the `/h5p` frame, `h5p-resizer.js` and the sample packages |
| [.github](https://github.com/embed-my/.github) | This profile and the organisation's settings |

All three are MIT. The player inside the frame is [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player), an open-source, browser-only H5P player by the same author: it reads the `.h5p` archive in the browser through a Service Worker, with no server-side extraction.

## Guides

| Guide | What it covers |
|---|---|
| [Preparing and hosting packages](https://embed-my.org/docs/hosting-packages) | Where to put the `.h5p` file, CORS and Range headers, packages without libraries, slow video |
| [Privacy and security](https://embed-my.org/docs/privacy-and-security) | What the iframe isolates, what is saved, cookies, data protection, and what you still need to protect |
| [Troubleshooting](https://embed-my.org/docs/troubleshooting) | Common problems and how to report one |

## With an AI assistant

The player's repository ships [agent skills](https://www.skills.sh/missing-elements/h5p-offline-player) for Claude Code, Cursor, Copilot, Codex and the rest. `h5p-verify` plays a package in a real H5P runtime in a headless browser and reports start-up, errors, missing libraries and a screenshot: the same check as embed-my.org, without a link. The others make a package's video start at once (`h5p-normalize`) and put the player on a site of your own (`h5p-player-setup`).

```bash
npx skills add missing-elements/h5p-offline-player --skill h5p-verify   # the check
npx skills add missing-elements/h5p-offline-player                      # all three
```

## Licences

The player is MIT. The H5P core runtime it loads inside the frame comes from [h5p-php-library](https://github.com/h5p/h5p-php-library) and is GPL-3.0, published as [`@missing-elements/h5p-runtime`](https://www.npmjs.com/package/@missing-elements/h5p-runtime); its [licence](https://embed-my.github.io/assets/runtime-LICENSE.txt) and [notices](https://embed-my.github.io/assets/runtime-NOTICE.txt) are served beside it, and the player's [NOTICE.md](https://github.com/missing-elements/h5p-offline-player/blob/main/packages/player/NOTICE.md) gives the full account. The content inside a package carries its own licence, which the **Rights of use** button shows when the toolbar is on.

Embed My is independent and is not affiliated with or endorsed by H5P Group. “H5P” is a trademark of H5P Group.

## Get help and support

Open an issue where the problem lives: the activity not playing or playing wrong is the player, [h5p-offline-player](https://github.com/missing-elements/h5p-offline-player/issues); the snippet, the preview, the page or the guides are the [website](https://github.com/embed-my/website/issues); the frame itself or the sizing script is the [player origin](https://github.com/embed-my/embed-my.github.io/issues). Not sure? Pick the website. The [troubleshooting guide](https://embed-my.org/docs/troubleshooting#reporting-a-problem) lists what to include.
