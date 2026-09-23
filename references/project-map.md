# Project map

## Canonical paths

- Project root: the user-supplied project workspace
- UniApp source: `微信支付宝小程序-H5/`
- Admin source: `微信支付宝小程序-H5/admin/`
- Related website: `jikgu-pro-网站/`
- API contract: `微信支付宝小程序-H5/docs/openapi.yaml`
- Database schema: `微信支付宝小程序-H5/docs/schema.sql`
- Platform setup: `微信支付宝小程序-H5/docs/platform-config.md`

Any separately copied `xunhang-mp-alipay` directory is compiled Alipay output, not source. Rebuild it from the UniApp project instead of editing it directly.

## Local commands

From `微信支付宝小程序-H5/`:

```bash
npm run dev:h5
npm run build:h5
npm run dev:mp-weixin
npm run build:mp-weixin
npm run build:mp-weixin:review
npm run dev:mp-alipay
npm run build:mp-alipay
npm run build:mp-alipay:review
```

Build outputs:

- H5: `dist/build/h5`
- WeChat: `dist/build/mp-weixin`
- Alipay: `dist/build/mp-alipay`

The public H5 entry documented by the project is `https://www.jikgu.pro/`, with production API `https://api.daigouhanguo.com`. Verify current external state before relying on these values for a deployment.

From `admin/`:

```bash
npm run dev
npm run lint
npm run build
npm run db:generate
```

Database generation is not authorization to apply a production migration.

## Regression routing

Search `scripts/test-*.mjs` and choose tests closest to the changed domain. Existing coverage includes account isolation, cart and checkout, customer numbers, fulfillment, invitation, membership, modal locale, package status, shipping, Taobao marketplace, visa, wallet, and WeChat verification.

For release preparation, verify every affected target separately. Review builds use the explicit `:review` scripts and may intentionally differ from production builds.
