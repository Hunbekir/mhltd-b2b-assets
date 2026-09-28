# MHLTD B2B portal — image & catalog assets

This repo holds public product imagery and the public PDF catalogs used by the MHLTD B2B wholesale portal, for use in a migration.
- Viktor/Convex-hosted files: exported 2026-09-26.
- Shopify CDN images: added 2026-09-28.

It contains **no customer, order, pricing, proposal or cost data.**

| Folder | What | Files |
|---|---|---|
| `storage/` | Uploaded product images from prod file storage, named by Convex storage id | 405 |
| `storage-dev/` | Images that prod products reference but that are stored on the dev deployment | 5 |
| `catalogs/` | Brand PDF catalogs, named by catalog slug (already public on `/pdf-catalogs`) | 8 |
| `public/` | Static images shipped with the app (`/palm-lane/*`, `/rugs/*`, catalog covers, favicon) | 60 |
| `shopify/` | Product images referenced from `cdn.shopify.com`, original files as served, named `<name>-<sha256 first 10 hex>.<ext>` | 3,006 files for 3,009 URLs (3 URLs share identical content) |

Manifests:
- `manifest.json`: one entry per file, with direct URL (`rawUrl`), type, size, sha256 (base64), the original URL(s) it
  replaces (`originalUrls`) and the products/catalogs that use it (`usedBy`).
- `image_url_manifest.json`: one entry per original image URL in the portal's product data. It includes the replacement
  URL and path, type, size, sha256 (hex + base64), product id, title, status, **display order** (index in
  `products.images`), alt text and the product's variant ids.
  - Images are product-level in the portal, so there is no per-variant image link.
- `download_failures.json`: the 73 `www.palmlane.bm/ecommerce-media/...` URLs. Every one returns HTTP 404 on palmlane.bm
  (retail site migrated to `/uploads/`), so none could be archived.

Direct URL pattern: `https://raw.githubusercontent.com/Hunbekir/mhltd-b2b-assets/main/<path>`

The live portal still uses its original URLs. These copies are for migration only.
