# quocchungthan.github.io

Public GitHub Pages host for my local-first tools. Each UI is a static page that talks to a service on the
user's own machine (`http://localhost:<port>`) and says so when it is not running.

| Path | Tool | Source repo | Local port |
|---|---|---|---|
| `/para-bridge/` | PARA Bridge (ObserveWatching) | `quocchungthan/PARA-AI-solution` (public) | 5310 |
| `/tools-w-productioncore-aids/` | Production Core Aids (ObserveWatching) | `quocchungthan/tools-w-productioncore-aids` (private) | 5311 |
| `/tools-s-exploring-local/` | Local café explorer (SearchCollect) | `quocchungthan/tools-s-exploring-local` (private) | 5312 |
| `/tools-w-disklens/` | DiskLens (ObserveWatching) | `quocchungthan/tools-w-disklens` (private) | 5274 |

`.github/workflows/pages.yml` checks out the source repos, builds each `web/` and DiskLens's
`client/` (`npm run build:pages`), copies `landing/` to the root and deploys one artifact.
All frontends use a relative asset base to work on sub-paths.

## One-time setup

1. Create this repo as **public** with the exact name `quocchungthan.github.io` and push `main`.
2. Settings → Pages → Source = **GitHub Actions**.
3. Settings → Secrets → Actions → `TOOLS_TOKEN`: fine-grained PAT, repository access to all four source
   repos above, permission **Contents: read**.
4. Optional auto-redeploy: in each source repo add secret `PAGES_DISPATCH_TOKEN` (PAT with **Contents: write**
   on this repo). Without it, run the "Deploy all tool UIs" workflow here manually after changes.

Each source repo's README has the local-run instructions and the AFFiNE Tools-row snippet.

When adding DiskLens, grant the existing `TOOLS_TOKEN` Contents:read access to
`quocchungthan/tools-w-disklens` before running the deployment. No local service
or scan data is deployed here. The DiskLens page checks the service at
`http://localhost:5274`, shows installation/start instructions while unavailable,
and explains the browser's local-network permission. AFFiNE registration is manual.
