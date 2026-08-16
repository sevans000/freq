# Frequency Cards

A kneeboard frequency card for the iPad. Two columns of cards, each holding an
airport or facility ident with its frequency below it. Cards are organized into
groups, so a home-field group and a cross-country group stay separate.

Tapping an ident brings up the letter keyboard; tapping a frequency brings up
the number pad. Entries save as you type, and the app runs with no signal once
it has been installed to the home screen.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app — markup, styles, and script in one file |
| `manifest.webmanifest` | Name, icons, and colors for the home screen install |
| `sw.js` | Service worker; caches the app so it opens offline |
| `icon-*.png`, `favicon.png` | Icons |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## Putting it on GitHub Pages

1. Create a new repository. Public is required unless you have a paid plan.
2. Upload every file in this folder to the root of the repo — not inside a
   subfolder. On github.com: **Add file → Upload files**, drag them all in, commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source** to
   *Deploy from a branch*, branch `main`, folder `/ (root)`. Save.
4. Wait a minute or two, then open `https://YOURNAME.github.io/YOURREPO/`.

Pages serves over HTTPS, which the service worker requires.

## Installing it on the iPad

Open the Pages URL in **Safari** — this does not work from Chrome on iOS. Tap the
Share button, then **Add to Home Screen**. It launches full screen with no
browser bar.

Install it this way rather than leaving it as a bookmark. Safari clears storage
for ordinary sites you have not opened in about a week; home screen apps keep
theirs. That is the difference between your frequencies still being there after
two weeks off and not.

## After you edit the app

Open `sw.js` and change the version:

```js
var CACHE = 'freq-cards-v2';   // was v1
```

Then commit both files. Without the bump, iPads that already have it installed
keep serving the cached copy and will not see your changes. Your saved
frequencies are untouched by this — they live in local storage, not the cache.

## Where the data lives

Entries are stored in the browser's local storage on that device. They are not
synced anywhere and are not in this repository. Deleting the home screen icon or
clearing Safari's website data removes them, so retype anything you would hate
to lose after a reset.
