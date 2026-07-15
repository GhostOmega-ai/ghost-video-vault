# Ghost Video Vault

Ghost Video Vault is the dedicated video module for the Ghost privacy suite. It stores videos locally, organises them into albums, separates private content, generates lightweight thumbnails and provides an immersive mobile player.

## Version

**v1.1 Clean-Room Refactor**

This release rebuilds and consolidates the internal code while preserving the exact appearance, saved data and user-facing behaviour of the production Video Vault.

## What the clean-room refactor changes

- One authoritative JavaScript application file
- One authoritative consolidated stylesheet
- Related functions grouped by responsibility
- One gesture engine for tap, double-tap, swipe and pinch
- One player visibility controller
- One fullscreen and orientation controller
- One cleanup path for timers, Blob URLs, zoom and fullscreen
- Stacked CSS patches removed
- Duplicate and obsolete fullscreen rules removed
- Existing IndexedDB database and schema preserved

## Features

### Library and albums

- Import one or more local video files
- Automatic thumbnail generation
- Automatic duration and resolution detection
- Search videos by name
- Sort A–Z, Z–A, Newest or Oldest
- Long-press to enter Select mode
- Move or permanently delete selected videos
- Permanent Library and Favourites albums
- Permanent PIN-protected Private Vault
- Create and reorder custom albums
- Library and Favourites remain first
- Private Vault remains last

### Private Vault

- Default development PIN: `1234`
- Private videos are excluded from Library and Favourites
- Moving a video into Private removes its Favourite state
- Favourite becomes Pin inside Private
- Pinned videos stay at the top of Private
- Private Vault uses its permanent fixed cover

### Album covers

- Custom albums use one selected video thumbnail
- Library and Favourites support:
  - 1 selected video: full cover
  - 2 selected videos: equal split
  - 3 selected videos: one image above two
  - 4 selected videos: 2 × 2 collage

### Player controls

- Centred Play/Pause button
- Full-width progress bar
- Current time and total duration
- Modern Mute and Fullscreen icons
- Controls remain visible while paused
- Single tap on empty video space shows or hides controls
- Controls fade after playback begins
- Double-tap left: rewind 10 seconds
- Double-tap right: forward 10 seconds
- Double-tap centre: play or pause
- Swipe left/right: previous or next video
- Pinch zoom works while paused or playing
- Double-tap while zoomed: return to normal size
- Swipe and ±10-second seeking are disabled while zoomed

### Fullscreen

- Video always begins fitted using `object-fit: contain`
- Landscape is requested only for clearly wide videos
- Portrait and near-square videos are not forced into landscape
- Pinch zoom remains available in fullscreen
- Fullscreen controls stay visible while rotation and viewport resizing settle
- Rotation and fullscreen events do not repeatedly fight the fade timer
- Controls fade once after the fullscreen layout is stable
- Leaving fullscreen or closing the player unlocks orientation

### HD video support

- Original HD and 4K files are stored without recompression
- The original video quality is preserved
- Thumbnails are reduced to a practical preview size
- Playback smoothness depends on the device, browser, codec and available memory
- Large files remain subject to the browser storage quota

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

## Required asset filenames

```text
video-vault.png
private-vault-cover.png
delete-warning.png
home-nav.png
hide-nav.png
settings-nav.png
```

## Updating on GitHub mobile

Replace these full files:

```text
index.html
README.md
css/video.css
js/video.js
```

Open each file, tap the pencil icon, select all existing contents, paste the replacement and commit. Do not delete the file itself.

The `README.md` files inside `css/` and `js/` keep those folders visible if a code file is temporarily removed.

## Storage and compatibility

- Database name: `ghost-video-vault`
- Database version: `1`
- Video store: `videos`
- Settings store: `settings`
- Existing videos, albums, covers, favourites, pins and settings remain compatible
- Updating the website files does not normally delete IndexedDB data
- Clearing browser site data can remove locally stored videos
- This development build is not encrypted yet

## Version history

### v1.1 Clean-Room Refactor

- Rebuilt and formatted the complete application logic
- Consolidated all player state and cleanup
- Consolidated fullscreen fitting, rotation and orientation unlocking
- Fixed glitchy fullscreen controls with one settling controller
- Removed stacked fullscreen and gesture CSS patches
- Preserved the exact production behaviour and stored-data compatibility

### v1.0.1 Production

- Restored pinch zoom in fullscreen
- Preserved fitted fullscreen sizing

### v1.0 Production

- Locked the working feature set
- Added safer Blob URL cleanup
- Added reduced-motion support

### Earlier development releases

Earlier releases introduced the cinema player, adaptive covers, swipe navigation, private pinning, pinch zoom and gesture controls.

## Status

Ghost Video Vault v1.1 Clean-Room Refactor is the locked production foundation for integration into the main Ghost dashboard.
