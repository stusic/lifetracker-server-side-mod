# Changelog

All notable changes to the LifeTracker server-side mod are documented here.
Versions follow [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`.

- **MAJOR** — breaking config changes or key updates requiring a server wipe or manual config rewrite.
- **MINOR** — new features, added backward compatibly.
- **PATCH** — bug fixes and minor adjustments.

## [1.0.0] — 2026-11-02

First public release. Deployed live on a real DayZ server
(indifferentbroccoli.com) and published to the Steam Workshop.

### Server Admin Notes

- Requires `verifySignatures=2` in your server config.
- Install `LifeTracker.bikey` into your server's `keys/` folder.
- Requires a `LifeTracker/config.json` in the server's profile directory —
  see `config.example.json` and the README for the exact fields
  (`apiBaseUrl`, `webBaseUrl`, `serverCredential`). The mod will not start
  without a valid server credential.
- Add `-serverMod=@LifeTrackerServer` to your launch parameters.
- No prior version existed, so no config migration is needed for this
  release.

### New Features

- Life tracking from spawn to death, with route sampling uploaded to the
  LifeTracker service.
- Death-cause classification (`infected`, `fall`, `self`, `unknown`).
- In-game push notification on death with a short code the player can type
  into the LifeTracker website to retrieve their public life record and
  share link.

### Known Limitations

- Death-cause detection does not yet distinguish starvation/dehydration
  from other self-inflicted deaths, and does not detect PvP kills as a
  distinct cause — both report as `self` or `unknown` for now.
- Chat-based opt-out is not implemented; opt-out currently requires
  server-owner/operator action.
