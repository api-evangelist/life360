---
name: life360-explore-product-variants
description: Given a Life360/Tile product SKU, list its related colors or variants and check which are available.
api: openapi/life360-product-api-openapi.yml
operations:
- getApiCatalogProductsBySku
- getApiCatalogProductsBySkuRelatedProducts
- getApiCatalogProductsBySkuAvailable
generated: '2026-10-20'
method: generated
---
# Explore variants of a Life360 / Tile product

Base URL `https://www.life360.com`. No authentication. Read-only GETs.

1. `getApiCatalogProductsBySku` — `GET /api/catalog/products/{sku}` to confirm the starting product.
2. `getApiCatalogProductsBySkuRelatedProducts` — `GET /api/catalog/products/{sku}/related-products` for its colors and variants.
3. For each related SKU, `getApiCatalogProductsBySkuAvailable` — `GET /api/catalog/products/{sku}/available`.

Errors: `400` for an invalid SKU (do not retry), `500` server error (retry with backoff). Both use `ErrorResponse`.
