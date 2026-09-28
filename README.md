# MHLTD B2B portal — image & catalog assets

Every image and PDF the MHLTD B2B wholesale portal uses that was hosted on Viktor/Convex storage,
exported 2026-09-26 from production. Product images already on Shopify CDN / palmlane.bm are not duplicated.

| Folder | What | Files |
|---|---|---|
| `storage/` | Uploaded product images (prod file storage, named by Convex storage id) | 405 |
| `storage-dev/` | Images referenced by prod products but stored on the dev deployment | 5 |
| `catalogs/` | Brand PDF catalogs (named by catalog slug) | 8 |
| `public/` | Static images shipped with the app (`/palm-lane/*`, `/rugs/*`, catalog covers) | 60 |

`manifest.json` lists every file with its direct download URL (`rawUrl`), type, size, sha256, the old
Viktor/Convex URL(s) it replaces (`originalUrls`) and which products/catalogs use it (`usedBy`).
Direct URL pattern: `https://raw.githubusercontent.com/Hunbekir/mhltd-b2b-assets/main/<path>`
