# quocchungthan.github.io

Public GitHub Pages host for my local-first tools. Each UI is a static page that talks to a service on the
user's own machine (`http://localhost:<port>`) and says so when it is not running.

| Path | Tool | Source repo | Local port |
|---|---|---|---|
| `/para-bridge/` | PARA Bridge (ObserveWatching) | `quocchungthan/PARA-AI-solution` (public) | 5310 |
| `/tools-w-productioncore-aids/` | Production Core Aids (ObserveWatching) | `quocchungthan/tools-w-productioncore-aids` (private) | 5311 |
| `/tools-s-exploring-local/` | Local café explorer (SearchCollect) | `quocchungthan/tools-s-exploring-local` (private) | 5312 |
| `/tools-w-disklens/` | DiskLens (ObserveWatching) | `quocchungthan/tools-w-disklens` (private) | 5274 |

`.github/workflows/pages.yml` keeps `landing/` and the original PARA Bridge build.
The other three UIs come from the verified **single-ui-apps** artifact in
`quocchungthan/EMFc-experiments`. No local backend or private scan data is deployed.
Their public paths and local API ports above are unchanged; the bundles use a
relative asset base. CarResearch/car search is not built or linked.

## One-time setup

1. Create this repo as **public** with the exact name `quocchungthan.github.io` and push `main`.
2. Settings → Pages → Source = **GitHub Actions**.
3. Keep `TOOLS_TOKEN` with **Contents: read** on PARA-AI-solution. Add
   `SINGLE_UI_TOKEN` with **Contents: read** and **Actions: read** on
   EMFc-experiments. Secrets may be in the existing `github-pages` environment.
   For compatibility, the importer can use `TOOLS_TOKEN` if `SINGLE_UI_TOKEN`
   is absent and that existing token already has the required producer access.
4. Set repository variables `SINGLE_UI_RUN_ID` and `SINGLE_UI_REVISION` to a
   successful main-branch **SingleUI apps and skins** run and its full commit SHA.
   The importer rejects failed/PR runs, mismatched revisions and damaged files.
   Artifacts expire after 90 days: retain a verified operator copy and refresh
   the pin before the next deployment. Expired/missing artifacts fail the build,
   leaving the currently deployed site intact.
5. Optional auto-redeploy: in each source repo add secret `PAGES_DISPATCH_TOKEN` (PAT with **Contents: write**
   on this repo). Without it, run the "Deploy all tool UIs" workflow here manually after changes.

Each source repo's README has the local-run instructions and the AFFiNE Tools-row snippet.

Update both SingleUI variables together to upgrade or roll back the three apps.
The importer is loaded from that exact revision. Never use "latest" or a PR run.
The previous Pages deployment remains the rollback for the landing/Bridge build.
See EMFc's `SingleUI/docs/bundle-installation.md` for manual download instructions.
Local service startup and browser local-network permission guidance remain in the
apps. Labeled samples are not live service results. AFFiNE registration is manual.
