# TGPU Digital Ecosystem — Controlled GitHub Repository Migration

**Status:** Khalifah Kecil and Learning Hub ownership transfers and post-transfer deployments verified; next repository pending preflight  
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
