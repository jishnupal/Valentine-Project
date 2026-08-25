# RomCom Premiere Builder

This is the public, reusable version of the original project.

It is designed so the code can live on GitHub while private photos and videos stay on the user's own device.

## Files

```text
index.html                 customer-facing builder and installer
play.html                  final interactive experience
assets/template/           safe reusable template assets only
.gitignore                 keeps private media out of GitHub
```

## How it works

1. Open `index.html`.
2. The customer edits the basics.
3. The customer edits each episode one by one.
4. The customer attaches each cover image and video using clear upload slots.
5. The customer edits finale and credits text.
6. The customer optionally adds background music.
7. The customer launches `play.html` from the Review screen.

Selected media is loaded locally with the browser's `URL.createObjectURL`. It is not uploaded to GitHub or to any server.

## What is saved

The editable text settings are saved in the browser with `localStorage`.

Private media files are saved locally in the browser with IndexedDB. They remain on the user's device and can be reused when the same browser opens the builder/player again.

## Media slots

The builder hides filenames from the customer. Internally, the player uses these slots:

```text
tile1.jpg ... tile6.jpg   episode cover images
ep1.mp4 ... ep6.mp4       episode videos
M1.jpg ... M5.jpg         credits images
bgm.mp3                   optional background music
```

Users do not need to rename files. A file named `final-cut-from-phone.mp4` can be selected for "Episode 1 video"; the builder stores it in the correct internal slot automatically.

## Template-owned media

Use `assets/template/` only for non-confidential media that is safe to ship publicly.

Current included template assets:

```text
assets/template/netflix_intro.mp4
assets/template/sparkle.mp3
assets/template/celebration.mp3
```

For a public/commercial product, replace these with assets you own or are licensed to distribute.

Do not put personal/client photos or videos in the repo.

Background music is intentionally left as a customer upload because song choice is personal and may involve licensing.

## Deployment recommendation

Deploy this as a static website using GitHub Pages, Netlify, Vercel, or similar.

This is better than asking every user to run files locally because:

- no installation is needed;
- users always get the latest template;
- private media still stays local in their browser;
- the product can be shared as a simple link.

Use a local/offline ZIP only when the client does not want to open any deployed website at all.

## GitHub upload

Upload this folder, not the original private project folder.

The `.gitignore` blocks private media formats by default while allowing safe template assets inside `assets/template/`.

## Local reset

The builder has a Reset button. It clears saved text and locally stored media from the browser.
