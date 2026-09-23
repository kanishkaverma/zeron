# fork-release

This branch holds only the automation for this fork. `.github/workflows/fork-release.yml`
runs daily. When `zeronsh/zeron` publishes a release, it applies the `transcript-search`
commits, builds the macOS app, and publishes it as this repo's latest release (`ts-<version>`).

Those builds set `ZERON_RELEASES_URL` to this repo's latest release, so the in-app updater
installs them. When upstream includes the patch, the job publishes the stock build, which
returns the updater to the official feed.

Run it by hand from the Actions tab (`fork release`, optionally with `force`).
If it fails, the patch no longer applies to the new release; rebase `transcript-search`.
