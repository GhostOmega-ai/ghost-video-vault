# 👻 Ghost Video Vault

Clean standalone Video Vault module for the Ghost privacy suite.

## Version

**v0.1 Clean Foundation**

## Included

- Separate `ghost-video-vault` IndexedDB database
- Library, Favourites and PIN-protected Private Vault
- Custom albums and touch reordering
- Video upload and local browser storage
- Automatic thumbnails, duration and resolution detection
- Search, sorting, long-press selection, move and delete
- Favourites and Private pins
- Custom album covers and four-image collage covers
- Full-screen native video playback
- Video Info and rename flow
- Permanent Ghost navigation

## Required assets

Copy these into `assets/`:

```text
video-vault.png
private-vault-cover.png
delete-warning.png
home-nav.png
hide-nav.png
settings-nav.png
```

## Note

Videos are stored in IndexedDB. This development build is not encrypted, and large files remain subject to the browser storage quota.
