# STBPlay v0.2 source improvements

- Xtream category mapping and series episode resolution.
- Playlist URL resolution and EXTGRP support.
- Favorites persisted locally (not provider credentials).
- Password input masked; generic errors avoid exposing credential-bearing URLs.
- Proper cancellation propagation for network jobs.
- Explicit note: EPG XMLTV and Stalker portal remain unimplemented; the code has not been built on an Android SDK in this environment.

## Important security limitation
Many IPTV providers require plain HTTP. This project currently permits cleartext HTTP globally for compatibility. Only enter trusted providers; production builds should use a network security configuration and restrict unencrypted access where possible. Xtream providers commonly embed credentials in stream URLs. Avoid sharing those URLs.
