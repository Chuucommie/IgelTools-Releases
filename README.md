# IgelTools Releases

Public release assets for the **IgelTools** suite. The source code lives in
private repositories; only build artifacts are published here, so clients can
check for and download updates without authentication.

## Applications

| App | Tag prefix | Asset prefix |
| --- | --- | --- |
| IgelServer | `igelserver-` | `IgelServer` |
| IgelNotes | `igelnotes-` | `IgelNotes` |
| IgelTVRemote | `igeltvremote-` | `IgelTVRemote` |

## Naming rules

1. **Tag**: `<app>-vMAJOR.MINOR.PATCH` — for example `igelserver-v2.1.0`.
   The version inside the tag is what each updater compares with the installed build.
2. **Assets**: `<App>-<Platform>-vMAJOR.MINOR.PATCH.<ext>` — for example
   `IgelServer-Bazzite-v2.1.0.AppImage` and `IgelServer.dmg`.
3. **Updaters must filter by prefix.** Every app ignores releases and assets that
   do not carry its own prefix, so several products can share this repository
   without ever offering the wrong build to a client.

## Publishing

Releases are built and mirrored **locally, on request**, from each app's source
repository — there is no CI here:

```bash
./ci.sh release v2.1.0          # GitHub Release on the private source repo
./ci.sh release-public v2.1.0   # mirror the assets here as igelserver-v2.1.0
```

`release-public` downloads the assets from the private release when it exists and
falls back to the local `dist/` folder otherwise. The repositories can be
overridden with `IGELTOOLS_RELEASES_REPO` and `IGELSERVER_SOURCE_REPO`.
