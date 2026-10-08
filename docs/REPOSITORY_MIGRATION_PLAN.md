# TGPU Digital Ecosystem — Controlled GitHub Repository Migration

**Status:** Six repositories transferred; TEMAN post-transfer Azure deploy passed and owner confirmed website opens on phone, with separate CI smoke verification still failing; SATU remains on hold pending Azure investigation; Iqra smoke/mobile QA pending  
**Reviewed:** 8 October 2026  
**Source account:** [MamduhSaffin](https://github.com/MamduhSaffin)  
**Destination organisation:** [tgpu-digital-ecosystem](https://github.com/tgpu-digital-ecosystem)  
**Owner decision:** Keep application functionality and production hosting stable. No production repository is approved for transfer until its preflight is complete.

## Why migrate?

Separate the founder's personal GitHub portfolio from the TGPU Digital Ecosystem's long-term source-code ownership, access management and product governance.

An organisation does not need GitHub Enterprise for this work. Maintain existing repository visibility; **never make private repositories public as part of migration**.

## Current progress

- [x] Free GitHub organisation created.
- [x] ChatGPT Codex Connector installed for the organisation.
- [x] Official public organisation homepage established at `.github/profile/README.md`.
- [ ] Organisation avatar visually confirmed by the owner.
- [ ] Organisation security / owner recovery / team access reviewed.
- [ ] Pilot repository preflight completed.
- [x] First repository ownership transfer verified (Khalifah Kecil, GitHub repo and history).
- [x] Khalifah Kecil post-transfer Azure deployment verified (GitHub Actions attempt #3).
- [ ] Remaining repositories transferred and verified.

## Critical no-regression rules

1. **No mass transfer**. Migrate exactly one approved repository at a time.
2. Preserve existing public/private visibility, source history, tags, branches, releases, issues and pull requests wherever supported. Record the before-and-after state.
3. Record the exact current source commit SHA before moving anything.
4. Check the GitHub Actions triggers, required secret **names**, repository permissions, tokens, packages, webhooks, Pages settings, environment rules and external integrations. Do not commit secret **values**.
5. Check Azure Static Web Apps, Cloudflare Pages/Workers, DNS, GitHub repository authorisations, and any Supabase connections applicable to that repository.
6. Look for absolute repository links and owner-specific paths. Do not depend on permanent redirects, especially for CI asset downloads.
7. Preserve the existing deployment domain and confirm successful test/build and production smoke checks after the transfer.
8. Keep the project untouched and mark **BLOCKED** if permissions, credentials, integrations or verification are incomplete.
9. Never force-push, rewrite published history, disable security controls or delete a working repository to force the migration.
10. Ask for explicit authorisation before an actual ownership transfer.

## Proposed first pilot: Khalifah Kecil

**Source:** [MamduhSaffin/khalifah-kecil](https://github.com/MamduhSaffin/khalifah-kecil)  
**Target:** `tgpu-digital-ecosystem/khalifah-kecil`  
**Current status:** Transferred into TGPU GitHub organisation; post-transfer Azure deployment successful; live-domain check pending  
**Current domain:** https://khalifah.tgpu.my/  
**Primary hosting:** Azure Static Web Apps  
**Branch:** `main`  
**Current deployment workflow:** `.github/workflows/azure-static-web-apps.yml`  
**Known deployment secret:** `AZURE_STATIC_WEB_APPS_API_TOKEN`

This is a **candidate** only, not an approved transfer. The repository is comparatively small, but moving it can still interrupt deployment.

### Owner update — 8 October 2026

The owner reports that a new Azure Static Web Apps deployment secret value has been entered for the Khalifah Kecil project. **This is owner-reported and not independently verified**: the connector cannot inspect Actions secret values or confirm their presence. The most recent successful Azure deployment workflow observed in GitHub Actions completed on **6 October 2026** (run [37523198371](https://github.com/MamduhSaffin/khalifah-kecil/actions/runs/37523198371)), before this change.

**Next gate:** confirm the secret is named exactly `AZURE_STATIC_WEB_APPS_API_TOKEN` in the currently active source repository, run an authorised deployment or workflow validation, and verify `https://khalifah.tgpu.my/` is still healthy. A repository transfer remains **ON HOLD** pending destination secret / Azure deployment-source preflight and explicit transfer approval. Do not share the secret value.

### Verified Azure deployment rerun — 8 October 2026

**Confirmed through GitHub Actions:** Run [37523198371](https://github.com/MamduhSaffin/khalifah-kecil/actions/runs/37523198371), attempt **2**, was completed with **success** at 2026-10-08 03:20:30 UTC (11:20:30 MYT). The `build_and_deploy` job and `Deploy` step both succeeded. The rerun used the current repository secret configuration; secret values are not visible to the connector.

**Still pending:** Independent verification of `https://khalifah.tgpu.my/` (automated web access could not reach it); Azure Static Web App repository association / app authorisation; verification of secret availability after transfer; final owner approval for moving this production repo. **No ownership transfer performed.**

### Production confirmation & migration gate — 8 October 2026

- **Production site:** The owner confirmed `https://khalifah.tgpu.my/` was **working**, following the successful Azure GitHub Actions rerun.
- **Source repository:** `MamduhSaffin/khalifah-kecil` remains public on branch `main`, with repository admin access confirmed.
- **Target organisation:** `tgpu-digital-ecosystem` exists and does not currently have a `khalifah-kecil` repository.
- **GitHub transfer behaviour:** GitHub documentation says repository-level **secrets, webhooks and deploy keys are preserved** during a transfer, along with commit history, issues and pull requests. However, confirm permissions and workflow configuration after transfer.
- **Azure coupling:** Existing Azure Static Web App source association / GitHub app authorisation in the **destination organisation has not been verified**. This can affect future automatic builds even where the site remains accessible.
- **State:** **Ready for owner-directed transfer procedure**, subject to GitHub target acceptance and post-transfer Azure validation. **NOT TRANSFERRED**. No secret values should be shared in chat.
- **Next execution:** Owner must use source repo Settings → General → Danger Zone → Transfer ownership; target `tgpu-digital-ecosystem`, repository name `khalifah-kecil`. After completing the transfer, verify the new repo path, secret name, Actions permissions, Azure source link and production domain. Record final status only after both the GitHub and Azure checks pass.

### Manual transfer instruction prepared — 8 October 2026

- User has confirmed the live site works and instructed the assistant to proceed.
- The source repository `MamduhSaffin/khalifah-kecil` was verified to exist, remain public on `main`, and be administrable by the connected GitHub account.
- `tgpu-digital-ecosystem/khalifah-kecil` did not exist when checked. The organisation's GitHub App has `all repositories` access.
- GitHub Actions rerun [37523198371](https://github.com/MamduhSaffin/khalifah-kecil/actions/runs/37523198371) attempt #2 completed successfully; the owner separately confirmed the live website functions.
- **The connected GitHub app provides no repository-transfer operation**, and Azure Static Web App source association cannot be queried through the available integration. Owner must perform GitHub's UI transfer, then the new repository path and Azure deployment must be independently verified. Do not represent the migration as complete yet.

### Pilot preflight

- [ ] Confirm the source site's current production availability and record an independent rollback reference.
- [ ] Record source commit SHA and outstanding issues / pull requests.
- [ ] Confirm destination organisation permits the repository transfer.
- [ ] Confirm `AZURE_STATIC_WEB_APPS_API_TOKEN` is available or can be configured safely for the destination.
- [ ] Review Azure Static Web App deployment source / provider authorisation and whether the repository linkage must be reconnected.
- [ ] Confirm any custom-domain and workflow dependencies.
- [ ] Confirm the production deployment will not be replaced with an unrelated site during validation.
- [ ] Owner explicitly approves this repository's transfer.

### Pilot execution and post-transfer validation

1. Transfer the repository from GitHub's repository **Settings → General → Danger Zone → Transfer ownership**, selecting the destination organisation. This action should be initiated by the owner with the appropriate GitHub permission.
2. Recheck workflow and secret configuration in the new organisation repository before making any changes that might redeploy.
3. Confirm the full commit history, default branch, repository visibility, README and relevant GitHub settings.
4. Validate Azure integration and run the workflow only once the destination configuration is ready.
5. Verify the live domain `https://khalifah.tgpu.my/`, the expected content and relevant offline functionality.
6. Update references in the organisation README after successful validation.
7. Mark migration **COMPLETE** only after passing both GitHub and production checks.

If validation fails, stop changes and use the documented Azure/GitHub recovery procedure; do not assume a repository URL redirect or a reverse transfer is an automatic rollback.

## Subsequent batches — provisional

| Priority | Repositories | Main caution |
| --- | --- | --- |
| After pilot | `tgpu-learning-hub`, `tgpu-academy` | Cloudflare credentials, custom-domain management, Actions |
| Later | `tgpu-amal`, `tgpu-iqra` | Cloudflare Worker/Azure build and content validation |
| Coordinated together | `SATU`, `TEMAN-Haramain-by-TGPU` | TEMAN workflow downloads pinned map assets from `MamduhSaffin/SATU`; audit and preserve the dependency before either transfer |
| High-sensitivity | `tgpu-ecosystem`, `gulf-preservation-stage`, `gcc-market-preserve` | Multiple production deployments, domains, preservation and owner-specific configuration |
| Last / dedicated review | `tgpu-gcc-connect` | Cloudflare Worker, Supabase, RLS, private partner/admin operations, business data |
| Selective review only | Archived repos, `tgpu-legacy`, experiments and prototypes | Avoid clutter and duplicates; do not move everything automatically |

The ordering may change after repository-by-repository checks. Commercial TGPU Gulf Advisory code and client information require separate access and confidentiality decisions from public ecosystem projects.

## Project-specific dependency already identified

The TEMAN Haramain deployment workflow downloads two map-pack files from an owner-specific `raw.githubusercontent.com/MamduhSaffin/SATU/<pinned-commit>/...` URL. Treat this as a potential breaking dependency if SATU moves. Keep source files available and test any revised URL before making either transfer.

## Documentation and approvals

For each project record:

- **Source / destination repository**
- **Project owner / product**
- **Current visibility and branch**
- **Production domain and hosting**
- **External integrations**
- **Required secret names (never values)**
- **Source commit SHA**
- **Production baseline check**
- **Migration approval and date**
- **Transfer confirmation**
- **Post-transfer tests and deployment status**
- **Issues / rollback actions**
- **Final status**: PENDING, BLOCKED, READY, or COMPLETE

> **Update, 8 October 2026:** Khalifah Kecil has been transferred to `tgpu-digital-ecosystem`. All other production repositories in this plan remain under `MamduhSaffin` unless their status is explicitly updated.


## Transfer verification — 8 October 2026

**Verified via GitHub:** `tgpu-digital-ecosystem/khalifah-kecil` exists under the target organisation; visibility is public, default branch `main`, administrative access exists, and original repository ID `1400659385` remains intact. The prior `MamduhSaffin/khalifah-kecil` path redirects to the same repository, and existing 52 Actions runs are visible at the new URL. The current `main` commit remains `fbe1371f1cd8d6c24ae92e5bc62164bc43f71f04`. The deployment workflow file remains intact and references secret name `AZURE_STATIC_WEB_APPS_API_TOKEN`.

**NOT yet validated:** A new Azure deployment **after** the ownership transfer, including any necessary Azure source-repository authorisation. The successful run on 8 October 2026 at 03:20 UTC was completed **before** this transfer; it is not evidence of post-transfer continuous deployment. GitHub's API does not reveal Actions secret values. Current live-domain availability after transfer is also not independently established.

**Next steps:** (1) verify the moved repository has the required Actions secret name; (2) inspect Azure Static Web Apps → deployment/source provider association, reconnect to `tgpu-digital-ecosystem/khalifah-kecil` if required; (3) run a controlled Azure GitHub Actions test from the new repository; (4) confirm `https://khalifah.tgpu.my/` still works; (5) mark the pilot fully COMPLETE only after these checks. **Do not reset an Azure token or alter DNS by default**; only change a token where necessary and rotate the secret accordingly. No other production repository was transferred as part of this action.


## Post-transfer Azure deployment verification — 8 October 2026

**CONFIRMED SUCCESS:** On the owner's instruction, ChatGPT triggered a **rerun of the existing successful build_and_deploy job** in `tgpu-digital-ecosystem/khalifah-kecil` using GitHub's official Actions API, without changing application code. GitHub accepted the rerun and recorded [run 37523198371, attempt #3](https://github.com/tgpu-digital-ecosystem/khalifah-kecil/actions/runs/37523198371) as **completed / success**, updated at 2026-10-08 06:59:07 UTC (14:59:07 Malaysia time). The `Deploy` step in `build_and_deploy` also completed with **success**. Therefore the existing GitHub Actions Azure deployment token was accepted and the deployment can be invoked from the new repository owner.

**Pending / not verified:** The environment used to check `https://khalifah.tgpu.my/` could not resolve the domain, so this is **not** a claim that an independent public HTTP check passed. The owner previously confirmed the site worked **before** transfer. Confirm post-transfer public website functionality at a convenient opportunity. Azure Static Web Apps' GitHub OAuth/source link and *automatic* on-push delivery are not independently verified by this successful manual rerun; they can be checked on the next planned release. Do not change DNS, production credentials, or repository settings without evidence they require changes.

**Operational state:** GitHub ownership migration **COMPLETE**; Azure **manual deployment validation COMPLETE**; independent post-transfer domain/scheduled next push validation **PENDING**. No further production changes needed at this stage. Other repository transfers remain pending separate preflight.


## Next candidate preflight — TGPU Learning Hub, 8 October 2026

**Source:** `MamduhSaffin/tgpu-learning-hub`  
**Target:** `tgpu-digital-ecosystem/tgpu-learning-hub`  
**Transfer status:** **PENDING — owner must perform ownership transfer in GitHub UI**  
**Visibility:** Private, must remain private. 
**Default branch:** `main`.
**Production:** `https://learning.tgpu.my/`, Cloudflare Pages project `tgpu-learning-hub`.

GitHub preflight confirms the source repository exists with administrative access, the destination name is not currently occupied, and the most recent production GitHub Actions run [37523065381](https://github.com/MamduhSaffin/tgpu-learning-hub/actions/runs/37523065381) succeeded before transfer. The successful job checked Cloudflare Pages deployment, production custom domain and the approved logo asset. Source commit at preflight: `148d9c4cf35a63cc4d65b643207197b73da57ff5`.

**Workflow credential requirements:** `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` are referenced as GitHub Actions secrets. Repository-level secrets ordinarily remain associated during ownership transfer per GitHub documentation, but secret values are not inspectable and the destination should be tested with a controlled rerun. The only located `MamduhSaffin` reference was in the README repository attribution; update that reference after successful transfer, **not before**, because writes to `main` trigger production deployment.

**Risk gate:** Private repositories moving to a GitHub Free organisation may lose some paid-plan features such as protected branches or GitHub Pages. No such feature is verified as actively configured for this source repository. No private→public visibility change is permitted. Public uptime cannot be independently verified by this tool; rely on successful release smoke checks and perform live checks after transfer.

**Planned procedure:** Owner transfers via repository Settings → General → Danger Zone → Transfer ownership into `tgpu-digital-ecosystem`. Assistant then verifies repository identity, privacy and history, safely triggers the existing Cloudflare deployment job, inspects the resulting run, updates README's owner reference only after deployment proves safe, and marks the result in this log. Do not modify any other production repositories automatically.


## Learning Hub transfer & Cloudflare verification — 8 October 2026

**Transfer confirmed:** `tgpu-digital-ecosystem/tgpu-learning-hub` exists under the official TGPU organisation, remains **private**, retains `main` and original repository ID `1406945164`, and the former owner path redirects to the new repository. GitHub Actions history was retained.

**Post-transfer deployment passed:** With the owner's instruction to proceed, the assistant triggered rerun attempt **#2** of [GitHub Actions run 37523065381](https://github.com/tgpu-digital-ecosystem/tgpu-learning-hub/actions/runs/37523065381), which completed **successfully**. Every critical stage passed: checkout, required files, Cloudflare project check, Pages deployment, custom-domain attachment, DNS record check, and `learning.tgpu.my` custom-domain and logo verification. The Cloudflare credentials required no modification for this rerun.

**Documentation aligned:** The private Learning Hub repository README's GitHub repository path was updated from `MamduhSaffin/tgpu-learning-hub` to `tgpu-digital-ecosystem/tgpu-learning-hub` in commit `25a8ce2320b0f861601a218d82f8ab3cbb15f6fa`. The public TGPU organisation profile acknowledges the Learning Hub as a **private** organisation repository without revealing private code.

**Automatic deployment verification — COMPLETE:** That README commit triggered a fresh **push** workflow [run 37741285056](https://github.com/tgpu-digital-ecosystem/tgpu-learning-hub/actions/runs/37741285056) from the new owner. It completed **successfully** at 2026-10-08 07:06:21 UTC. GitHub Actions reports success for Cloudflare Pages deployment, custom-domain confirmation, DNS record check and production domain/logo verification. This establishes that the normal push-driven production deployment continues to work after the ownership transfer. Do not expose secret values or make the private repository public.

**Other projects:** Academy remains a candidate for independent preflight; no other production repository was transferred as part of Learning Hub migration.


## Academy transfer preflight — 8 October 2026

**Project:** TGPU Academy, structured learning and professional-development MVP.  
**Source:** `MamduhSaffin/tgpu-academy`  
**Target:** `tgpu-digital-ecosystem/tgpu-academy`  
**Status:** **READY FOR OWNER-INITIATED GITHUB TRANSFER** — not transferred yet.  
**Visibility:** PRIVATE — must remain private.  
**Repository ID:** `1406947238` (verify unchanged after transfer).  
**Default branch:** `main`.  
**Source commit before transfer:** `aeccf86f1c3a0a720841d5855f1e824a76e2a0b9`.

### Deployment baseline

- Hosting: Cloudflare Pages project `tgpu-academy`.
- Production domain: `https://academy.tgpu.my/`.
- Latest pre-transfer GitHub Actions run [37713897424](https://github.com/MamduhSaffin/tgpu-academy/actions/runs/37713897424), `push` on 8 October 2026: **success**.
- Workflow `.github/workflows/deploy.yml` completed all steps successfully: static output preparation, required secrets check, Cloudflare Pages project and deployment, custom-domain attachment, DNS record and live homepage/Study Malaysia verification.
- Required GitHub Actions secrets (NAMES ONLY): `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`. Do not disclose values.
- GitHub connector installation is enabled for all organisation repositories.
- The target `tgpu-digital-ecosystem/tgpu-academy` was absent before transfer; old owner appears in the source README's repository field, to be updated after transfer.

### Ownership transfer and validation procedure

1. Owner transfers the private repository through GitHub repo **Settings → General → Danger Zone → Transfer ownership**, selecting `tgpu-digital-ecosystem`; retain name `tgpu-academy` and **private** visibility. This requires action from the account owner; the connected GitHub app has no repository transfer operation.
2. Assistant verifies target owner, original repository ID, main commit SHA, private visibility, workflow file, and GitHub Actions run history.
3. Assistant triggers a controlled rerun of the existing successful deployment job from the new organisation repository and verifies Cloudflare deployment, DNS and public site checks.
4. Assistant changes only the README repository attribution to `tgpu-digital-ecosystem/tgpu-academy`; this pushes to `main` and tests automatic post-transfer deployment.
5. Assistant confirms the new push-triggered GitHub Actions run succeeds, particularly the custom-domain and Study Malaysia production checks.
6. Assistant updates the public TGPU organisation profile without exposing private source code and records the migration result here.

**Do not** disable Actions, reset Cloudflare credentials, reconfigure DNS or move another production repository unless a specific failed check requires a separate reviewed action. GitHub Free organisation private-repository settings and protections should be reviewed after transfer where relevant.


## Academy migration execution and verification — 8 October 2026

**Status: COMPLETE — verified GitHub ownership transfer and normal Cloudflare continuous deployment.**

- New repository: [`tgpu-digital-ecosystem/tgpu-academy`](https://github.com/tgpu-digital-ecosystem/tgpu-academy), **PRIVATE**.
- Original repository ID `1406947238` is unchanged; `main` branch and action history retained; old `MamduhSaffin/tgpu-academy` URL redirects to the new repository.
- First post-transfer check: [GitHub Actions run 37713897424, attempt #2](https://github.com/tgpu-digital-ecosystem/tgpu-academy/actions/runs/37713897424), manually rerun by the connected GitHub app at the owner's instruction. Job **completed successfully**, including static build, Cloudflare credentials, Cloudflare Pages deployment, custom domain, DNS and production URL verification of the Academy homepage and Study Malaysia guide.
- Updated README repository attribution in commit `68a432a61f6f5bf854a29715ec76ea71096a3567`; only the repository owner reference changed.
- Second post-transfer check: normal push-triggered [GitHub Actions run 37741843060](https://github.com/tgpu-digital-ecosystem/tgpu-academy/actions/runs/37741843060), completed **successfully** at 2026-10-08 07:11:16 UTC. Cloudflare deploy, custom domain, DNS and Academy public URL verification all passed.
- Official organisation profile updated to reflect Academy as a **private** organisation repository without exposing private code.
- No Cloudflare secrets were revealed, rotated or updated; no DNS changes were manually performed. Workflow's existing DNS consistency checks executed successfully.

**Next:** Continue to the next product only after a separate preflight. Cloudflare's successful workflow verifies the public URL at deployment time; independent review of mobile UI and product behaviour is outside this migration scope. Do not imply accreditation or LMS capabilities beyond the Academy's established status.


## AMAL migration preflight — 8 October 2026

**Status:** READY FOR OWNER-INITIATED TRANSFER (deployment baseline passed; post-transfer verification mandatory). **No transfer has been initiated by the assistant.**

- **Source:** `MamduhSaffin/tgpu-amal` (PRIVATE); **destination:** `tgpu-digital-ecosystem/tgpu-amal` (verified not present).
- **Existing GitHub repository ID:** `1406139723`; default branch: `main`; archived: false; connected GitHub account has administrator access.
- **Baseline source commit:** `5694b3ecbbf5c9857177237dac15d3a01a1bd123` at 2026-10-06 20:04 UTC.
- **IMPORTANT DEPLOYMENT CORRECTION:** Active `.github/workflows/deploy-cloudflare.yml` deploys a **Cloudflare Worker**, NOT Cloudflare Pages, using `cloudflare/wrangler-action@v4` with `command: deploy`. Active `wrangler.toml` declares `name = "tgpu-amal"`, Worker entry `src/worker.ts`, static assets `./dist`, `workers_dev = true` and custom-domain route `amal.tgpu.my`. The README and `docs/CLOUDFLARE_PAGES_SETUP.md` are **stale**, describing a Pages deployment; do not use those instructions to reconfigure or transfer the running service.
- **Required Actions secret names:** `CLOUDFLARE_API_TOKEN` only for the deployment workflow; repo secret values cannot be read with connector tools. Do not send or expose token.
- **Latest pre-transfer deployment:** [run 37523630452](https://github.com/MamduhSaffin/tgpu-amal/actions/runs/37523630452), 6 October 2026, **success**, including Node setup, npm install, production build, secret presence check, Worker deploy and smoke test for `https://tgpu-amal.moesaffin.workers.dev/`. Paired [quality run 37523630327](https://github.com/MamduhSaffin/tgpu-amal/actions/runs/37523630327) also **success**.
- **Not verified:** Independent current HTTP response for `https://amal.tgpu.my/`. The existing workflow smoke-tests the Workers.dev URL, **not** the custom domain. Do not claim custom-domain QA passed. External website fetch attempts were not available through the current environment.
- **Owner-specific references:** Code search found a `MamduhSaffin/tgpu-amal` repository reference in `docs/CLOUDFLARE_PAGES_SETUP.md`; after transfer update/replace that outdated documentation and align the README with current Worker hosting.
- **Transfer rules:** Owner transfers via repo Settings → General → Danger Zone → Transfer ownership to `tgpu-digital-ecosystem`, keeping `tgpu-amal` PRIVATE. Do not change Cloudflare DNS, Worker name, `wrangler.toml` routes, or API tokens solely to perform GitHub ownership transfer.
- **Post-transfer tests:** Verify same repo ID, private visibility, `main`, source commit, workflow and Actions history. Rerun the previous successful Worker deployment job under the organisation, confirm all steps passed. Then correct the README and stale Pages setup docs in a documentation-only commit; verify push triggers both Worker deployment and the quality gate successfully. Confirm current `amal.tgpu.my` site via a user-side browser check before marking end-to-end production validation complete. Update TGPU profile to acknowledge AMAL as private without exposing source.
- **Do-not-act-yet:** No other repository transfers, secret rotation, DNS work, Cloudflare Pages project setup, or code modifications. AMAL transfer needs an explicit action by the GitHub owner.


## AMAL post-transfer execution and verification — 8 October 2026

**Repository ownership: COMPLETE.** Verified `tgpu-digital-ecosystem/tgpu-amal` with GitHub repository ID `1406139723` unchanged, source private visibility preserved, default branch `main`, previous source URL redirecting to the organisation, workflows and run history intact. No other repository was transferred as part of AMAL's migration.

**Worker deployment after transfer: SUCCESS.** Via the connected GitHub app and owner instruction, the prior successful Worker deployment job was rerun under the TGPU organisation: [run 37523630452, attempt #2](https://github.com/tgpu-digital-ecosystem/tgpu-amal/actions/runs/37523630452), completed successfully 2026-10-08 07:17:48 UTC. All stages passed, including Node/npm install, build, API token presence check, Cloudflare Wrangler Worker deployment and smoke test of `tgpu-amal.moesaffin.workers.dev`. No secret values were exposed or rotated.

**Documentation corrected:** A single documentation-only commit `790dde019e9558472686a1ae0fa53c855ca970b3` updated the README to reflect **Cloudflare Workers** and organisation ownership; marked `docs/CLOUDFLARE_PAGES_SETUP.md` obsolete; and added `docs/CLOUDFLARE_WORKERS_SETUP.md` as a description of the active setup. Production worker sources, `wrangler.toml`, custom-domain routing and DNS configurations were not modified. The TGPU organisation profile was updated to mention AMAL as a **private** repository.

**Normal push-triggered deployment: SUCCESS.** This documentation commit automatically triggered both [Worker deploy run 37742678745](https://github.com/tgpu-digital-ecosystem/tgpu-amal/actions/runs/37742678745) and [quality-gate run 37742678767](https://github.com/tgpu-digital-ecosystem/tgpu-amal/actions/runs/37742678767). Both completed successfully. The Worker deploy workflow's `Deploy Worker` and `Smoke test Workers dev route` steps passed. Therefore the GitHub Actions integration can continue deploying the Worker from the new owner after ordinary pushes.

**Outstanding limitation:** `https://amal.tgpu.my/` is configured as a Worker custom domain, but GitHub's current workflow smoke-tests only the Workers.dev endpoint, and independent access to the custom domain through the available web tool was unsuccessful. Do not claim the custom-domain HTTP response, mobile UX, logo or end-user functionality have passed a fresh external QA check. Custom-domain browser verification is **PENDING**. The migration of GitHub ownership and CI/Worker deploy is **COMPLETE**.

**Next candidate:** TGPU Iqra requires an independent preflight, including Azure deployment token, audio assets, dependencies and live PWA behaviour before any transfer. No automatically generated or unreviewed code changes to Iqra have been authorised.


## TGPU Iqra preflight — 8 October 2026

**Migration state:** CONDITIONAL / READY FOR OWNER TRANSFER, with **pre-existing production smoke-test failures** requiring review after transfer. No repository transfer or Iqra application changes were performed during this preflight.

**Source:** `MamduhSaffin/tgpu-iqra`, PRIVATE, `main` branch; original repo ID `1392955949` (use to verify repository continuity).  
**Target:** `tgpu-digital-ecosystem/tgpu-iqra`; destination does not exist, so name is available.  
**Baseline main SHA:** `fc7054b65c0c9337d6893cca78d319b4cdb4f405`, 6 Oct 2026 at 20:10:32 UTC.  
**Hosting:** Azure Static Web Apps, domain `iqra.tgpu.my`; no hosting or DNS changes should be made during ownership transfer.

### Verified pre-transfer GitHub baseline

- Active deployment: `.github/workflows/azure-static-web-apps.yml`, triggered on `main` push or manual dispatch; uses `Azure/static-web-apps-deploy@v1` with `skip_app_build: true`; requires GitHub Actions secret name `AZURE_STATIC_WEB_APPS_API_TOKEN`. GitHub's automatically supplied `GITHUB_TOKEN` is referenced for repo token. Never share credential values.
- Pre-transfer [Azure deployment run 37524447816](https://github.com/MamduhSaffin/tgpu-iqra/actions/runs/37524447816) was **successful** on 6 Oct 2026, including Deploy step.
- [PWA integrity run 37524447935](https://github.com/MamduhSaffin/tgpu-iqra/actions/runs/37524447935) was **successful** on the same commit; checks JS syntax, JSON manifests, local resource references and service-worker shell resource existence.
- **Exception:** [production smoke workflow run 37524446148](https://github.com/MamduhSaffin/tgpu-iqra/actions/runs/37524446148) was **failure** at startup on 6 Oct 2026 with **0 jobs**. Its raw event was `push` even though `.github/workflows/post-deploy-smoke.yml` declares a `workflow_run` trigger; cause not confirmed. This is a pre-existing problem, **not** caused by the organisation migration. Diagnose separately before claiming end-to-end smoke verification. Do not blindly disable the check.
- The smoke-test source expects `tgpu-iqra-v83` in `sw.js`, but actual `sw.js` declares cache name `tgpu-iqra-v82`. The repo's release marker says `iqra-v83-trilingual-2026-10-07`. Even after workflow startup is corrected, this version expectation must be reconciled against the **approved production release**; do not silently rewrite it without validating cache/version semantics.
- `index.html` references `home-shell-v68.js?v=81`, while the smoke-test's static index checks expect `home-shell-v68.js?v=77`. This is another pre-existing version mismatch that would fail the existing smoke test. Fix the check only after grounding the correct release specification.
- `data/audio/manifest.json` contains 28 Iqra items but **zero `audioVerified: true` entries and zero production audio URLs**. Build/manifest validation therefore does **not** confirm working spoken audio. The user previously reported audio not working on mobile; this migration must not be used to claim voice is fixed. Audio recording/review and mobile playback require a separate product-quality workflow.
- `QURAN_SOURCE_REVIEW.md` describes the Quran reader as intentionally excluded from active runtime since v59, and independent human Quran text review as pending. Quran-related material must not be described as certified or fully reviewed.
- Service worker and manifest keep PWA shell and approved icon references; transferring the repository must not change official brand assets, media URLs, learner progress storage, cache identifiers or custom domains.
- Independent public HTTP verification of `https://iqra.tgpu.my/` was unavailable from the browsing environment; the app may still work, but this is not independently confirmed at preflight.

### Controlled ownership transfer gate

1. The owner, not the GitHub app, must open `https://github.com/MamduhSaffin/tgpu-iqra/settings` and use **Danger Zone → Transfer ownership** to `tgpu-digital-ecosystem`. Keep repo `tgpu-iqra` **PRIVATE**. Avoid changing Azure source connection, DNS or tokens until evidence they need updates.
2. Assistant verifies transferred repo ID, privacy, branch, source SHA and workflow history. Rerun the existing Azure deploy from the new owner and inspect `Deploy` step; verify the PWA integrity workflow (either triggered by a controlled docs commit, if safe, or via existing Actions UI where no API dispatch is available).
3. Review pre-existing broken `post-deploy-smoke.yml` startup and version mismatches before editing a production smoke test. Any CI-only change must be narrow and justified, and its push-triggered deployment checked.
4. Confirm `https://iqra.tgpu.my/` still works, preferably via an independent browser visit. Do not claim mobile audio, academic review or cache freshness are passed solely because CI deployed.
5. Update organisation profile and migration record, keeping repository private; do not move other repositories until Iqra transfer checks conclude.

**Do-not-act-yet:** Do not modify or replace the approved Iqra logo, author new recorded audio, enable Quran reader, set `audioVerified` or `published` without review, rotate Azure token, reset browser progress, or reconfigure production DNS solely for a GitHub transfer.


## TGPU Iqra transfer and deployment verification — 8 October 2026

**GitHub ownership transfer: VERIFIED.** `tgpu-digital-ecosystem/tgpu-iqra` is owned by the TGPU organisation; repository ID `1392955949`, private visibility, default `main`, existing workflows and prior GitHub Actions history are preserved. GitHub's former `MamduhSaffin/tgpu-iqra` endpoint redirects to the same repository. The baseline source commit remains `fc7054b65c0c9337d6893cca78d319b4cdb4f405`. The migration did **not** modify Iqra source code, production audio, reviewed learning content, approved logo, custom domain, Azure token or service worker.

**Post-transfer Azure deployment: SUCCESS.** Using the connected GitHub app, reran the existing successful Azure deployment job under the TGPU organisation. [GitHub Actions run 37524447816, attempt #2](https://github.com/tgpu-digital-ecosystem/tgpu-iqra/actions/runs/37524447816) completed successfully at 2026-10-08 07:26:16 UTC. The `Deploy TGPU Iqra to Azure Static Web Apps` step also passed. This confirms deployment via the repository's existing Azure token works under the new owner.

**Post-transfer PWA integrity validation: SUCCESS.** [GitHub Actions run 37524447935, attempt #2](https://github.com/tgpu-digital-ecosystem/tgpu-iqra/actions/runs/37524447935) completed with success at 2026-10-08 07:25:06 UTC. Syntax, JSON, local references, approved manifest icons and service-worker shell consistency checked as configured. This **does not** prove Android audio playback, offline operation under network loss or cache freshness by device testing.

**Known CI exception, pending separate investigation:** The existing `.github/workflows/post-deploy-smoke.yml` still produces immediate failures with zero jobs. At least two new unsuccessful runs appeared when the Azure and PWA job reruns began ([37743278389](https://github.com/tgpu-digital-ecosystem/tgpu-iqra/actions/runs/37743278389) and [37743273627](https://github.com/tgpu-digital-ecosystem/tgpu-iqra/actions/runs/37743273627)); each reports event `push` although the workflow YAML declares `workflow_run`. The exact validation/parse/startup failure has not been established. Existing smoke expectations are inconsistent with current source: a `tgpu-iqra-v83` service-worker cache is expected while the file declares `tgpu-iqra-v82`, and the expected home-shell version query `v=77` differs from the `index.html` reference `v=81`. **Do not mark post-deploy production smoke QA successful and do not silently change PWA cache semantics.**

**Audio disclosure:** `data/audio/manifest.json` has 28 Iqra entries with no entries marked `audioVerified: true` and no production audio URL values at this baseline. Confirm voice assets, rights/approval and mobile playback separately before describing spoken pronunciation as working. Quran browser remains out of active runtime; Quran human review remains pending per source docs.

**Operational state:** GitHub ownership migration and Azure deployment test **COMPLETE**; configured PWA CI validation **COMPLETE**; live domain, mobile/audio user acceptance and broken smoke workflow **PENDING**. The organisation's public README was updated to acknowledge Iqra as a private TGPU repository without exposing its contents. A normal new push-triggered Azure deployment has **not** been separately tested after transfer; the successful rerun validates deployment capability under the new owner, not all future event triggers. No other repository was moved in this step.


## SATU and TEMAN Haramain paired preflight — 8 October 2026

**Migration state:** REVIEWED, NOT TRANSFERRED. **Safer order:** (1) TEMAN Haramain while SATU remains at old path, (2) stabilise SATU Azure deploy and migrate SATU, (3) repoint TEMAN's pinned offline-map file download URLs to the new SATU organisation path, verify pinned SHA unchanged and both downloads valid. No production app code, Azure settings, secrets or DNS were changed during this preflight.

### Current repositories and baselines

| Attribute | SATU | TEMAN Haramain |
| --- | --- | --- |
| Source | `MamduhSaffin/SATU` | `MamduhSaffin/TEMAN-Haramain-by-TGPU` |
| Planned target | `tgpu-digital-ecosystem/SATU` | `tgpu-digital-ecosystem/TEMAN-Haramain-by-TGPU` |
| Repository ID | `1390665990` | `1396888337` |
| Visibility | **PUBLIC — preserve** | **PUBLIC — preserve** |
| Default branch | `main` | `main` |
| Source commit at preflight | `19249761746edc9a374b87b1836d96595785da3c` | `a1ea524b8cffe2dc3c4fba9d30e3d6d16cdd13a5` |
| Production domain | `https://satu.tgpu.my/` | `https://teman.tgpu.my/` |
| Hosting | Azure Static Web Apps, Vite frontend + API | Azure Static Web Apps, Vite frontend + API, pinned PMTiles map packs |
| Required GitHub Actions secrets | `AZURE_STATIC_WEB_APPS_API_TOKEN` (plus auto-supplied `GITHUB_TOKEN`) | `AZURE_STATIC_WEB_APPS_API_TOKEN` (plus auto-supplied `GITHUB_TOKEN`) |

### Pre-existing continuous-deployment exceptions

- **SATU latest deployment failed before transfer:** [run 37523177957](https://github.com/MamduhSaffin/SATU/actions/runs/37523177957), despite installation/build and approved asset staging passing. The Azure action's log ends: `The content server has rejected the request with: BadRequest`; `Reason: No matching Static Web App environment was found.` The previous [run 37523167038](https://github.com/MamduhSaffin/SATU/actions/runs/37523167038) deployed successfully with production-domain verification, but refers to an earlier commit and overlapping runs may have interacted. **Do not assert the cause is an invalid token** without Azure verification. `Verify SATU` [run 37523177974](https://github.com/MamduhSaffin/SATU/actions/runs/37523177974) succeeded for the latest SHA. **SATU transfer is ON HOLD until source deployment configuration is validated or the owner authorises proceeding with a documented broken deployment baseline.**
- **TEMAN latest deployment workflow failed final verification before transfer:** [run 37519757279](https://github.com/MamduhSaffin/TEMAN-Haramain-by-TGPU/actions/runs/37519757279). Regression tests, app build, the pinned PMTiles download and Azure upload all completed successfully; only `Verify live production domain` failed (exit 1). The repo's `public/release.html` declares `teman-v10-feedback-mobile-2026-10-07`, and its `public/sw.js` still declares cache `teman-shell-v9` while its smoke workflow expects `teman-shell-v10`. This is a grounded source/workflow mismatch and potential source of the verification failure, **but not proven to be the exact live-domain failure cause**. The prior [run 37517570592](https://github.com/MamduhSaffin/TEMAN-Haramain-by-TGPU/actions/runs/37517570592) succeeded at an earlier SHA. Do not alter service-worker cache naming without confirming release/cache semantics.
- Both sites' independent live HTTP reachability could not be established from the assistant's web environment at preflight. Avoid ungrounded uptime claims.

### Cross-repository offline-map dependency (must preserve)

TEMAN's `.github/workflows/azure-static-web-apps.yml` downloads from `raw.githubusercontent.com/MamduhSaffin/SATU/59ca2c8535b83b77e6f41ab80584e29cd5c05794/public/maps/`:

- `makkah.pmtiles` — **2,412,635 bytes**, blob SHA `727608744a56fe089341c77fcf32ef714a0be32c`.
- `madinah.pmtiles` — **2,242,253 bytes**, blob SHA `fbc38de46c5a3c73205870639b11d633b3b48cb7`.

Both files were verified in the pinned SATU commit and on the present SATU main branch. TEMAN's latest failed workflow **successfully downloaded both** before its Azure deploy and final smoke step. SATU also contains the feature branch `teman-street-map-v0.5` map-pack-building workflow; keep Git branches and assets intact. Avoid renaming/deleting SATU or making it private. Raw.githubusercontent.com old-owner redirects after transfer must **not** be assumed to work indefinitely. When SATU moves, update TEMAN's download URLs to `tgpu-digital-ecosystem/SATU/<same SHA>/...` and verify download hashes and deployment, without regenerating packs or changing coordinates.

### Controlled migration sequence

1. **TEMAN first:** the owner transfers `MamduhSaffin/TEMAN-Haramain-by-TGPU` → `tgpu-digital-ecosystem/TEMAN-Haramain-by-TGPU`, remaining **PUBLIC**. SATU remains at original owner path during this step, so the pinned map downloads are preserved. After transfer verify same repo ID, main SHA, public visibility, workflows and Azure token availability; perform controlled test/build/deploy, carefully distinguish existing production smoke-test failure from new errors. If deployment is blocked, stop and record it; do not falsely declare complete. Also check live site via owner if external checks remain unavailable.
2. **SATU after deployment issue investigation:** investigate Azure's `No matching Static Web App environment` response, confirm the intended Azure SWA resource/environment and deployment token without exposing its value. Avoid parallel overlapping production deploy runs. Once a clean deployment baseline is available, the owner transfers SATU to TGPU and tests Azure deployment and domain.
3. **Retarget pinned TEMAN map source:** change only the GitHub repository owner component of TEMAN's two PMTiles URLs to `tgpu-digital-ecosystem/SATU`, keeping commit `59ca2c8535b83b77e6f41ab80584e29cd5c05794` and paths/contents unchanged. Verify map assets are accessible and tests/deployment still work. Keep public source licences/attributions.

**Do not-act-yet:** No mass transfers, no DNS or token rotations without evidence, no PWA/mobile app feature changes during ownership migration, no regenerated or replaced Protomaps map data, no deletion of SATU's embedded historical TEMAN code or map branch, and no statements guaranteeing safety functionality before fresh testing.


## TEMAN ownership transfer — 8 October 2026

**Verified:** `tgpu-digital-ecosystem/TEMAN-Haramain-by-TGPU` is now owned by the official TGPU organisation and remains **PUBLIC**, with repository ID `1396888337`, default `main`, and GitHub Actions history preserved. The former URL redirects to the transferred repo. `MamduhSaffin/SATU` remains **PUBLIC** under the founder, so the existing TEMAN pinned offline-map URL source is unchanged. Current TEMAN workflow still references SATU commit `59ca2c8535b83b77e6f41ab80584e29cd5c05794` with both original paths.

**Post-transfer test concluded:** The controlled rerun of [GitHub Actions run 37519757279, attempt #2](https://github.com/tgpu-digital-ecosystem/TEMAN-Haramain-by-TGPU/actions/runs/37519757279) has **overall conclusion: FAILURE**, but the following steps passed: pinned Makkah and Madinah PMTiles downloads; Azure Static Web Apps build/upload/deployment (Azure logs explicitly report `Deployment Complete :)`, target `https://gray-island-074750b00.3.azurestaticapps.net`); prior regression tests and app build. The **`Verify live production domain` step failed with exit code 1**, repeating the pre-transfer failure. The verification script runs multiple assertions with `set -euo pipefail` and presently logs no individual assertion identifier on failure; the exact failing assertion is not proven. Source check confirms `public/sw.js` defines `teman-shell-v9` while workflow expects `teman-shell-v10`. A different release.html or public domain mismatch may also contribute. The app source, map packs, DNS and service worker were not changed by this migration. **Do not mark end-to-end smoke QA successful.**

**Known baseline discrepancies:** `public/release.html` declares `teman-v10-feedback-mobile-2026-10-07`, but `public/sw.js` still declares `teman-shell-v9`, whereas the current live verification step expects `teman-shell-v10`. Do not blindly change service-worker cache names during transfer; determine the intended release version and actual live HTTP response first. The GitHub profile URL for TEMAN was updated to its organisation-owned address.

**SATU hold remains in force.** Its latest Azure upload failed with `No matching Static Web App environment was found`. Diagnose/validate the SATU Azure environment and token before transferring SATU or changing TEMAN's pinned download URLs. No SATU transfer has occurred.


**TEMAN decision gate (updated with owner phone check):** The GitHub transfer and ability to deploy to Azure from the organisation are verified. On **8 October 2026**, the owner confirmed in chat that `https://teman.tgpu.my/` opens and appears normal on their phone (reply: “All good”). This is an **owner-reported live-site accessibility check**, not an independent HTTP verification of all routes, offline maps, SOS/Family Link features, or security controls. The GitHub workflow's `Verify live production domain` step still fails; the automated smoke-test defect is **UNRESOLVED**. Safest next steps are a narrow diagnostic improvement to the smoke-test workflow and review of intended v9/v10 cache policy. Do **not** reset tokens, modify offline maps, or automatically transfer SATU while its Azure failure remains unresolved.
