# familiarize.com-workflows

This repository holds operational GitHub Actions for `familiarizeptyltd/familiarize.com`.

## SitePilot

Workflow: `.github/workflows/sitepilot-familiarize.com.yml`

Use it to run SitePilot from this workflows repository against the content repository:

- SitePilot repo: `familiarizeptyltd/SitePilot`
- content repo: `familiarizeptyltd/familiarize.com`
- workflow repo: `familiarizeptyltd/familiarize.com-workflows`

Manual inputs:

- `mode`: `dry` or `live`
- `section`: `docs`, `www`, or `about`
- `sitepilot_ref`: SitePilot branch/tag/SHA, default `main`
- `content_ref`: content branch/tag/SHA, default `main`
- `rebuild_semantic_index`: rebuild semantic index before the cycle

Production rule:

- Use `dry` first and inspect the uploaded report artifact.
- Use `live` only when dry output is defensible.
- `live` opens content PRs in `familiarizeptyltd/familiarize.com`; it does not auto-merge.

Required repository secrets:

- `REPO_TOKEN`
- `GOOGLE_CREDENTIALS_JSON`
- `GOOGLE_CUSTOM_SEARCH_API_KEY`
- `CUSTOM_SEARCH_ENGINE_ID`
- `TAVILY_API_KEY`
- `PROFESSIONALIZE_API_KEY`
- `PROFESSIONALIZE_BASE_URL`
- `PROFESSIONALIZE_LLM_MODEL`
- `PROFESSIONALIZE_EMBEDDING_MODEL`

Optional Google Ads secrets:

- `GOOGLE_ADS_DEVELOPER_TOKEN`
- `GOOGLE_ADS_CUSTOMER_ID`
- `GOOGLE_ADS_LOGIN_CUSTOMER_ID`
- `GOOGLE_ADS_OAUTH_CLIENT_ID`
- `GOOGLE_ADS_OAUTH_CLIENT_SECRET`
- `GOOGLE_ADS_OAUTH_REFRESH_TOKEN`
