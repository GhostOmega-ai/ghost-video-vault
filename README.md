# Ghost Video Vault

Ghost Video Vault is the dedicated video module for the Ghost privacy suite. It provides local video storage, album organisation, private content separation, automatic thumbnails and an immersive mobile video player in the same neon Ghost design language as Photo Vault.

## Version

**v1.0 Production**

This is the first consolidated release of Video Vault. It uses one authoritative HTML file, one authoritative stylesheet and one authoritative JavaScript file.

## Features

### Library and albums

- Import multiple local videos
- Automatic thumbnail, duration and resolution detection
- Search videos by name
- Sort by A–Z, Z–A, Newest or Oldest
- Long-press to enter Select mode
- Move or permanently delete selected videos
- Permanent Library and Favourites albums
- Permanent PIN-protected Private Vault
- Custom albums with touch reordering
- Library and Favourites stay first
- Private Vault stays last

### Private Vault

- Default development PIN: `1234`
- Private videos are excluded from Library and Favourites
- Moving a video into Private removes its Favourite state
- Favourite becomes Pin inside Private
- Pinned Private videos remain at the top
- Private Vault uses a permanent fixed cover

### Album covers

- Custom albums use one selected video thumbnail
- Library and Favourites use adaptive layouts:
  - 1 selected: full cover
  - 2 selected: equal split
  - 3 selected: one image above two
  - 4 selected: 2 × 2 collage

### Cinema player

- Video always uses `object-fit: contain`
- Centred Play/Pause control
- Full-width timeline
- Current time and total duration
- Modern Mute and Fullscreen icons
- Smooth control fading
- Controls remain visible while paused, ended or seeking
- Single tap shows or hides controls
- Double-tap left third: rewind 10 seconds
- Double-tap right third: forward 10 seconds
- Swipe left/right: previous or next video
- Fullscreen hides the vault action row for more viewing space
- Landscape is requested only for clearly landscape videos where it improves the view
- Portrait and near-square videos are not forced into landscape
- Orientation is unlocked when fullscreen or the player closes

### Video information

The information panel shows album, Favourite/Pin status, name, duration, resolution, file size and date added. Videos can be renamed and selected as album covers from this panel.

## Project structure

```text
Ghost-Video-Vault/
├── index.html
├── README.md
├── css/
│   ├── README.md
│   └── video.css
├── js/
│   ├── README.md
│   └── video.js
└── assets/
    ├── video-vault.png
    ├── private-vault-cover.png
    ├── delete-warning.png
    ├── home-nav.png
    ├── hide-nav.png
    └── settings-nav.png
```

The small README files inside `css/` and `js/` keep those folders visible on GitHub if the main code file is temporarily removed.

## Required asset filenames

```text
video-vault.png
private-vault-cover.png
delete-warning.png
home-nav.png
hide-nav.png
settings-nav.png
```

## GitHub Pages installation

1. Upload `index.html` and this complete `README.md` to the repository root.
2. Upload `video.css` to `css/`.
3. Upload `video.js` to `js/`.
4. Upload the required images to `assets/`.
5. Open **Settings → Pages**.
6. Choose **Deploy from a branch**.
7. Select `main` and `/ (root)`.
8. Save and allow GitHub Pages time to redeploy.

## Safe mobile updates

Open the code file, tap the pencil icon, select all text inside the editor, replace it and commit. Do not use **Delete file** unless intentionally removing it. GitHub hides a folder when its final tracked file is deleted.

## Storage and privacy

- Database: `ghost-video-vault`
- Storage: browser IndexedDB
- Existing videos normally remain after code-file updates because the database name and schema are unchanged
- Clearing browser site data can remove stored videos
- Original HD and 4K files are stored without recompression or quality loss
- Playback smoothness depends on the phone, browser, codec and available memory
- Large imports are limited by the browser/device storage quota
- This development build is not encrypted yet

## Navigation

The Home button currently points to:

```text
../Ghost-Phoenix/
```

Hide and Settings remain placeholders until those Ghost modules are connected.

## Compatibility

Designed for modern Android browsers supporting IndexedDB, `<dialog>`, Blob URLs, Canvas, Fullscreen API and touch events. Orientation locking is browser-dependent. When it is blocked, fullscreen still works and the complete video remains fitted without cropping.

## Version history

### v1.0 Production

- Locked the current feature set as the production release
- Added safer Blob URL cleanup
- Added page-unload media cleanup
- Confirmed one active gesture engine and one player-control flow
- Added reduced-motion accessibility support
- Preserved the existing IndexedDB database and all stored-data compatibility
- No user-facing features were changed in this production polish pass

### v1.1

- Replaced the overlapping tap logic with one clean gesture state machine
- One tap reliably toggles controls in either direction
- Double-tap left and right still seeks by 10 seconds
- Double-tap centre toggles playback
- Pinch zoom and swipe navigation no longer compete with tap detection
- Removed the old scattered gesture timers and state variables
- Gesture handling now has one source of truth and one event flow

### v1.0.5

- Added a dedicated transparent gesture surface over the video
- Player taps no longer depend on the browser video element forwarding touch events
- One tap reliably hides visible controls or restores hidden controls
- Control buttons remain above the gesture surface and continue to work normally
- Swipe, pinch zoom and double-tap gestures remain supported

### v1.0.4

- Single tap now toggles controls immediately in both directions
- Tapping while controls are visible hides them straight away
- Tapping while controls are hidden restores them straight away
- Double-tap left/right still performs ±10-second seeking
- Double-tap while zoomed still resets the video to normal size

### v1.0.3

- Fixed controls failing to return after they faded during playback
- The first tap now restores hidden controls immediately
- A second tap within the double-tap window still performs ±10-second seeking
- Pinch zoom and double-tap reset remain unchanged

### v1.0.2

- Paused controls remain visible by default
- A single tap while paused can hide or restore every control
- Added pinch-to-zoom during playback or while paused
- Pinch zoom supports up to 4× magnification
- Double-tap while zoomed returns immediately to normal size
- Swipe navigation and ±10-second seeking are disabled while zoomed
- Original HD video files are stored and played without downscaling or recompression
- Thumbnail generation remains lightweight so HD uploads do not create oversized preview images

### v1.0.1

- Player controls remain visible whenever playback is paused or ended
- Controls disappear after playback resumes or when the user taps outside them
- Fullscreen video is forced to fit using `object-fit: contain`
- Added viewport refitting after fullscreen entry and orientation changes
- Prevented landscape fullscreen from appearing cropped or zoomed

### v1.0 Clean

- Consolidated the complete working Video Vault
- Removed obsolete album-cover CSS
- Smoothed control fading
- Prevented auto-hide timer jitter
- Kept controls visible during seeking
- Added aspect-ratio-aware fullscreen rotation
- Added automatic orientation unlock
- Included this complete replacement README

### v0.4 Cinema Player

- Added centred Play/Pause
- Added full-width timeline
- Added time, Mute and Fullscreen controls
- Removed the separate rotate icon

### v0.3 Immersive Gesture Player

- Added swipe navigation
- Added double-tap ±10-second seeking
- Added tap-to-show and tap-to-hide controls

### v0.2 Premium Player

- Added custom playback controls
- Added adaptive album-cover layouts

### v0.1 Clean Foundation

- Added the separate video database, albums, Private PIN, thumbnails, metadata, favourites, move and delete

## Status

Ghost Video Vault v1.0 Production is ready for main-dashboard integration and normal use. Future changes should replace complete modules cleanly rather than stacking patches.
