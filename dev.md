This is a collection of some relatively unorganized notes for people interested in developing on this extension.

## Future Features
- automatically update deprecated references
  - possibly allow for updating a single file rather than a pack. This would require changes to pks to support update-deprecations working correctly on a single file.
- click to open public API where constant lives

## Releasing a new version

Publishing is automated by `.github/workflows/release.yml`, which runs on every push to `main`.

To cut a release:
1. Bump `version` in `package.json` to a **new** value (one that has never been released).
2. Merge to `main`.

On push to `main` the workflow compiles, runs tests, then:
- If tag `v<version>` does **not** exist → packages the `.vsix`, publishes to Open VSX, and creates a GitHub release `v<version>`.
- If the version was **not** changed in the push → skips publishing (normal for docs-only merges).
- If the version **was** changed but `v<version>` already exists → **fails the build** (guards against bumping to an already-published version, which would otherwise silently skip publishing while the job still reports success).

Notes:
- Open VSX takes a minute or two to serve the new version after publish. Verify the *artifact*, not just the version string returned by the API — download it and confirm the change is present.
- Publishing uses the `OPEN_VSX_REGISRY_TOKEN` repo secret.

## Future work items
- Add buildkite CI support and add proper testing

Improve screenshot gif

improve PNG logo for extension
