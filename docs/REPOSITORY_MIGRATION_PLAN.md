# TGPU Digital Ecosystem — Controlled GitHub Repository Migration

**Status:** Planning / preflight only  
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
- [ ] First repository transferred and verified.
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
**Current status:** Public, production application  
**Current domain:** https://khalifah.tgpu.my/  
**Primary hosting:** Azure Static Web Apps  
**Branch:** `main`  
**Current deployment workflow:** `.github/workflows/azure-static-web-apps.yml`  
**Known deployment secret:** `AZURE_STATIC_WEB_APPS_API_TOKEN`

This is a **candidate** only, not an approved transfer. The repository is comparatively small, but moving it can still interrupt deployment.

### Owner update — 8 October 2026

The owner reports that a new Azure Static Web Apps deployment secret value has been entered for the Khalifah Kecil project. **This is owner-reported and not independently verified**: the connector cannot inspect Actions secret values or confirm their presence. The most recent successful Azure deployment workflow observed in GitHub Actions completed on **6 October 2026** (run [37523198371](https://github.com/MamduhSaffin/khalifah-kecil/actions/runs/37523198371)), before this change.

**Next gate:** confirm the secret is named exactly `AZURE_STATIC_WEB_APPS_API_TOKEN` in the currently active source repository, run an authorised deployment or workflow validation, and verify `https://khalifah.tgpu.my/` is still healthy. A repository transfer remains **ON HOLD** pending destination secret / Azure deployment-source preflight and explicit transfer approval. Do not share the secret value.

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

> This document records the migration plan, not an executed transfer. As of 8 October 2026, production repositories remain owned by the personal GitHub account.
