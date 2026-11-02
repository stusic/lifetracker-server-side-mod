# LifeTracker — server-side mod (DayZ), packaged build

Ready-to-run build of the LifeTracker server-side mod. This is the signed
mod package, not source — drop this folder onto the server as-is.

## Install

1. Copy this entire `@LifeTrackerServer` folder to the server's mods
   location (e.g. your host's server-mods SFTP folder).
2. Copy `LifeTracker.bikey` into the server's `keys/` folder, and make sure
   `verifySignatures=2` is set in the server config.
3. Copy `config.example.json` to `$profile:LifeTracker/config.json` on the
   server (its own writable profile directory) and fill in your real
   values:

   ```json
   {
     "apiBaseUrl": "https://dayz-life-tracker-api.onrender.com",
     "webBaseUrl": "https://dayz-life-tracker-api.onrender.com",
     "serverCredential": "dzlt_live_...your real issued credential..."
   }
   ```

   If this file is missing or `apiBaseUrl`/`serverCredential` is empty, the
   mod logs a fatal error at boot and does nothing for the rest of that
   session — it does not fall back to any default.

4. Add `-serverMod=@LifeTrackerServer` to the server's launch parameters.

## Contents

- `addons/scripts.pbo` — the signed mod PBO.
- `addons/scripts.pbo.LifeTracker.bisign` — its signature.
- `LifeTracker.bikey` — public key to install in the server's `keys/`
  folder (verifies the signature above; not sensitive).
- `config.example.json` — template for the server's own
  `LifeTracker/config.json`.
