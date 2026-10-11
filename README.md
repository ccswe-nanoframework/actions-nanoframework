# actions-nanoframework (archived)

**Moved to [ccswe-apps/actions](https://github.com/ccswe-apps/actions).** This repo is archived and gets no fixes. Existing `@master` references keep working as frozen code because archived repos stay readable.

| Old | New |
|---|---|
| `.github/workflows/nanoframework-build-publish.yml` with `publish-nuget: true` | `ccswe-apps/actions/.github/workflows/nanoframework-build-library.yml` |
| `.github/workflows/nanoframework-build-publish.yml` without `publish-nuget` | `ccswe-apps/actions/.github/workflows/nanoframework-build-app.yml` |
| `.github/workflows/nanoframework-update-dependencies.yml` | `ccswe-apps/actions/.github/workflows/nanoframework-update-dependencies.yml` (same inputs) |
| `.github/actions/setup-nanoframework`, `build-nanoframework` | `ccswe-apps/actions/.github/actions/setup-nanoframework`, `build-nanoframework` |

Changes when switching:

- The library workflow's nuget.org secret is `NUGET_API_KEY` (was `NUGET_ORG_API_KEY`), e.g. `NUGET_API_KEY: ${{ secrets.NUGET_ORG_API_KEY }}`.
- It publishes only when `src`, `version.json`, `Directory.Build.props` or `nuget.config` change.
- `dependents` still works; `discover-dependents` scans listed accounts for listeners that call `ccswe-apps/actions/.github/workflows/nanoframework-update-dependencies.yml`.
- `AUTOMATION_APP_ID` / `AUTOMATION_APP_KEY` are required (they run the shared Dependabot merge jobs).
- Check names are unchanged: `pipeline / build`, `pipeline / package-lock`, `pipeline / packages-updated`.

See the ccswe-apps/actions README for caller shapes.
