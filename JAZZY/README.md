# JAZZY

A light-blue, Instagram-inspired private Android app for **Hyu Suk** and **Jazzy** (Jasmin). Two accounts. Two cities. One shared space.

Included: a photo/video feed, likes/comments, local bookmarks, 24-hour story visibility, a Reel-link collection and short personal videos, profiles, password login, editable names/usernames/passwords, and encrypted text/media/file chat. Pairing uses a private invitation; the self-hosted Node 24/SQLite relay admits only two devices.

- [Install, deploy, and pair the phones](docs/SETUP.md)
- [Build the Android APK](docs/BUILD.md)
- [Encryption design and limitations](docs/SECURITY.md)
- [Verification status](docs/VERIFICATION.md)

The relay must be deployed before the two phones can share. An offline preview uses clearly labeled sample illustrations and messages. JAZZY is independent of Instagram/Meta. Instagram Reel links open externally; the app does not recreate Instagram's personalized feed. Calls, livestreaming, filters, music catalogs, background push notifications, and account recovery are outside this first version.

Encryption uses Web Crypto HKDF-SHA-256/AES-256-GCM and Android Keystore protection at rest. It has **not** been independently audited and has no forward secrecy. Read the security document before treating it as a high-assurance messenger.

No server has been provisioned as part of this source delivery. The included Compose configuration and setup guide deploy the relay to your own HTTPS domain.

## Project layout

```text
app/src/main/java/      Android host, secure storage, share/file handling
app/src/main/assets/    Bundled light-blue UI and encryption client
app/src/main/res/       Android theme and JAZZY icon
server/                SQLite relay, Docker Compose, Caddy TLS config
scripts/               Build-tool setup, APK build, local preview
tests/                 Crypto, relay, model, browser workflow checks
docs/                  Setup, build, security, and verification notes
```

## Quick checks

```sh
npm test
npm run preview
```

The browser preview is for interface development. Use the APK for durable Android key storage.
