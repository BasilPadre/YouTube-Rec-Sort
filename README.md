# YouTube Rec Sort

A lightweight Chrome extension that cleans up the YouTube Home feed and sorts loaded video recommendations by view count.

## Features

- Sorts loaded Home recommendations by view count, highest first
- Optionally hides videos that are at least two years old
- Hides Shorts, promoted cards, shelves, topic chips, and other non-video blocks on the Home page
- Saves settings with Chrome sync storage
- Re-applies sorting when YouTube loads more recommendations
- Supports view-count parsing in several interface languages

## Controls

The extension adds two switches to the YouTube header:

- **Views** — enables or disables sorting by view count
- **2y** — hides videos published two or more years ago

Disabling **Views** only disables sorting. Feed cleanup remains active while the extension is enabled.

## Installation

1. Download or clone this repository.
2. Open `chrome://extensions` in Chrome or another Chromium-based browser.
3. Enable **Developer mode**.
4. Click **Load unpacked**.
5. Select the repository folder containing `manifest.json`.
6. Open or reload the YouTube Home page.

## How it works

The extension runs as a Manifest V3 content script on `youtube.com`. It reads the metadata already rendered in recommendation cards, parses view counts, and reorders the existing DOM elements. It does not use the YouTube API and does not request additional recommendations.

The extension only sorts recommendations already loaded in the browser. It does not change YouTube's recommendation algorithm.

## Permissions

- `storage` — saves the two extension settings
- `https://www.youtube.com/*` — runs the content script on YouTube

The extension does not contain analytics, external network requests, remote scripts, or a background service worker.

## Known limitations

- Sorting applies only to the YouTube Home page.
- YouTube markup changes may require selector updates.
- Age filtering currently parses English, Russian, and Ukrainian date labels.
- Some East Asian abbreviated view-count formats may be parsed incorrectly.
- Items whose view counts cannot be detected are placed after recognized videos.

## Project files

- `manifest.json` — extension manifest and permissions
- `content.js` — sorting, filtering, controls, and YouTube navigation handling
- `styles.css` — switch styling and Home feed cleanup

## Version

Current version: **0.2.1**
