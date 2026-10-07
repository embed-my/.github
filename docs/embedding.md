# Embedding an activity

How to create an Embed My snippet for an H5P package, what the snippet contains, and how to check it before you share the page.

Before you start, you need a public HTTPS URL for the `.h5p` file. See [Preparing and hosting packages](hosting-packages.md).

## Create the embed

1. Open [Embed My](https://embed-my.org/).
2. Choose **H5P package**.
3. Paste the direct public URL ending in `.h5p`.
4. Preview the activity.
5. Choose display options:
   - a **title** for the frame, which screen readers announce;
   - H5P's own **toolbar** under the activity, with a **Rights of use** button that shows the licences recorded in the package and its media, and a **Reuse** button that lets visitors download the package.
6. Copy the generated snippet.
7. Paste it into the HTML/embed block of your website and publish the page.

## What the snippet contains

```html
<iframe
  src="https://embed-my.org/h5p?src=https%3A%2F%2Fcourses.example.edu%2Factivities%2Fweek-1-quiz.h5p"
  title="Week 1 knowledge check"
  loading="lazy"
  allow="fullscreen"
  style="width: 100%; min-height: 540px; border: 0"
></iframe>
<script src="https://embed-my.org/resizer.js"></script>
```

Use the exact code Embed My generates. It may include additional parameters for a display option you selected.

### The resizer script

The script line lets the frame grow and shrink with the activity: the frame reports its height, and the script, included once per page, applies it. It is served by Embed My, so your page sends nothing to a third party.

- **Without it**, the frame stays at the height in the `style` attribute and anything taller scrolls inside it.
- **If your site strips scripts** from pasted HTML, keep the iframe and give it a height that fits the activity.
- **If the page already includes h5p.org's `h5p-resizer.js`** for its h5p.org embeds, you need no second script: it uses the same protocol.

## Example: a portfolio page

If your package is at:

```text
https://portfolio.example/learning/windows-shortcuts.h5p
```

create an embed for that URL and paste the snippet into your portfolio's HTML/embed block. Visitors can complete the activity without an LMS account.

## Browser support

The activity runs inside the Embed My frame with its own Service Worker. That works in current Chrome, Edge, Firefox and Safari, on desktop and on Android, and on iOS from version 26. Older iOS versions have not been tested.

- **The page containing the iframe must be served over HTTPS** (or `localhost` during development). On a plain `http://` page the frame has no Service Worker and nothing plays.
- **In-app browsers** inside social and messaging apps sometimes give a frame no Service Worker at all. The frame then shows a link that opens the activity on its own Embed My page. Offer that link wherever an iframe cannot be used.

## Sites that restrict iframes

Some sites have a Content Security Policy that restricts frames. The embedding site must allow:

```text
frame-src https://embed-my.org
```

If the site cannot allow an iframe, link to the activity's Embed My page instead.

## Test before sharing

Open the published page in a private/incognito window and check that:

1. The activity loads and is not stuck on a blank frame.
2. Its interactions, media, and fullscreen button work.
3. The iframe expands far enough to show the entire activity.
4. A large video starts in an acceptable time on a normal connection.
5. The activity works for a visitor who is not signed in to your authoring system.

To check the package itself before publishing, run the open-source verifier:

```bash
npx @missing-elements/h5p-verify course.h5p
```

It opens the package in a real browser runtime and reports missing libraries, startup errors, and a screenshot. See the player's [verify guide](https://github.com/missing-elements/h5p-offline-player/blob/main/docs/verify.md) for details.

If something does not work, see [Troubleshooting](troubleshooting.md).
