---
name: xunhang-project-ops
description: Maintain the local 讯航集运 project across its UniApp H5, WeChat and Alipay mini-program builds, admin app, website, API contracts, tests, and release preparation. Use for 讯航集运 product and engineering tasks.
---

# 讯航集运项目运营

Use the project root supplied by the user or the current workspace. The main application source is `微信支付宝小程序-H5/`.

Before editing:

1. Check Git status in the affected repository and preserve unrelated changes.
2. Read the relevant README and the referenced contract or platform document.
3. Distinguish source from build output; never edit generated Alipay, WeChat, H5, `dist/`, or copied deployment files as the canonical implementation.

Use [references/project-map.md](references/project-map.md) for paths, commands, and validation routes.

## Invariants

- One UniApp/Vue source supports H5, WeChat, and Alipay. Keep platform-specific behavior explicit and avoid fixing one target by silently breaking another.
- API behavior follows `docs/openapi.yaml`; database expectations follow `docs/schema.sql`; platform login and payment setup follows `docs/platform-config.md`.
- Payment, wallet, membership, account isolation, customer numbers, and shipment state are high-risk business logic. Run the closest existing regression scripts after changes.
- Never expose or commit AppIDs, private keys, payment secrets, production tokens, customer data, or administrator credentials.
- Production deployment, payment changes, database migration, and external messaging require the user's current authorization.

## Working method

- Reuse existing scripts and tests before creating a new helper.
- Keep user-facing Chinese, Korean, and platform-specific copy consistent across targets.
- For UI changes, build the affected platform and inspect the rendered result when possible.
- For admin changes, run lint and build from `admin/`.
- Report the source changed, platforms verified, commands run, and any release step still requiring the user.
