# JAZZY free cloud test deployment

This package contains the original Android project and server, plus a Render Blueprint (`render.yaml`).

## Important: free Render is for disposable testing only

JAZZY stores account changes, device pairing, and encrypted events in a SQLite database at `/app/data/jazzy.sqlite`. Render's free web instances do not have a persistent disk. A restart, replacement, or redeployment may erase the database. Free instances also spin down when idle. **Do not rely on this deployment for private conversations or irreplaceable photos.** For reliable use, choose a host with persistent storage and backups.

## Steps

1. Create a **private** GitHub repository and upload the contents of this `JAZZY` folder (not the outer ZIP). Do not upload `.env`, signing keys, or private secrets.
2. Sign in to https://dashboard.render.com and select **New → Blueprint**. Connect the private repository and select the repository's `render.yaml`.
3. Review the service: `jazzy-relay`, Docker, free plan. Deploy. Render generates `JAZZY_SETUP_TOKEN` as a secret environment variable.
4. After deployment, visit `https://YOUR-SERVICE.onrender.com/health`. It should respond `{"ok":true,"app":"JAZZY","protocol":1}`.
5. In Render dashboard → your service → Environment, reveal or copy `JAZZY_SETUP_TOKEN` securely. Never paste it into a public chat or repository.
6. On each Android phone, open JAZZY → Log in, enter the full `https://YOUR-SERVICE.onrender.com` URL (no `/health`). Follow `docs/SETUP.md` for the two preconfigured account logins and private invite pairing.

**Before production use:** move the SQLite file to a persistent volume on a suitable host; configure backups and ensure TLS. Do not change the initial account seed file after a database has been initialized and expect existing accounts to change.

## Troubleshooting

- Check Render service logs if `/health` fails.
- Free instances may take time to wake after idle periods.
- A redeployment may reset the pair because SQLite is on an ephemeral filesystem.
- If the APK was configured with a different server address, use the in-app server address field as described in `docs/SETUP.md`.
