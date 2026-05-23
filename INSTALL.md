# Installing the Game Book Playbook on iPad

Quick guide for getting The Family Game Book onto an iPad as a real home-screen app.

## What's in the zip

- `index.html` — the playbook itself
- `manifest.json` — tells iOS this is an installable app
- `sw.js` — service worker (lets the app work offline)
- `icon-192.png` and `icon-512.png` — the home-screen icon
- `INSTALL.md` — this file

## Option 1: Free hosting (recommended — 5 minutes)

The easiest path. Host the folder on a free static site and add it to the home screen.

1. Go to [netlify.com/drop](https://app.netlify.com/drop) (no signup needed).
2. Drag the **entire unzipped folder** onto the drop zone.
3. Wait ~10 seconds. You'll get a URL like `https://something-random.netlify.app`.
4. Open that URL in Safari on the iPad.
5. After about 1.5 seconds an "Install" banner will appear at the bottom.
6. Or manually: tap the Share button ⬆️, scroll down, tap "Add to Home Screen", confirm.
7. Optional: in Netlify, claim the site (free account) and rename the URL to something memorable like `alexanders-game book.netlify.app`.
8. Done! The game book icon now lives on the home screen and opens fullscreen with no Safari chrome.

The service worker caches everything, so the app works offline after the first load — perfect for the game book field with spotty wifi.

## Option 2: Local network only (no internet)

If you'd rather not host it on the web at all, you can serve it from a Mac on the local network.

1. Unzip the folder somewhere on the Mac.
2. Open Terminal, `cd` into the folder.
3. Run: `python3 -m http.server 8080`
4. On the iPad (same wifi as the Mac), open Safari and go to `http://<mac's-local-ip>:8080`.
5. Find the Mac's IP in System Settings → Network. It'll look like `192.168.1.42`.
6. Add to Home Screen the same way as Option 1.

The downside: it only works when the Mac is running and on the same wifi. For game book days when you'll be at the club, Option 1 is much better.

## Option 3: GitHub Pages

If you have a GitHub account, push the folder to a repo and enable GitHub Pages. The URL will be `https://username.github.io/repo-name`. Same Add-to-Home-Screen flow.

## After installation

- The app opens fullscreen with no Safari UI
- It works offline (videos still need internet, but the playbook itself loads instantly)
- The home-screen icon is the game book ball
- Tab switches are instant
- All the YouTube video links open in an in-app player with a "Back" button — no leaving the app
- The "Install" banner only shows once, then never again

## Troubleshooting

- **Icon doesn't update on the home screen?** iOS caches icons aggressively. Delete the app from the home screen, clear Safari's cache (Settings → Safari → Clear History), reinstall.
- **App opens in Safari instead of fullscreen?** You probably tapped the icon in Safari's bookmarks instead of the home screen. Look on the actual home screen for the game book ball icon.
- **Videos won't play?** Check the iPad's internet. The playbook is offline-capable, but YouTube videos still need wifi or cellular.
- **Want to update the app later?** Re-host the updated folder at the same URL. The service worker will pick up changes within a day, or you can delete the app and reinstall for an immediate refresh.

## Why a real PWA (not just a bookmark)

This is a proper Progressive Web App — meaning:

- It looks and behaves like a native iOS app
- It works offline
- It has its own home-screen icon
- It doesn't show Safari's address bar
- Tabs and back-buttons all work properly without leaving the app
- Future updates can ship without re-installing anything

No App Store. No developer account. No Xcode. Just web standards.
