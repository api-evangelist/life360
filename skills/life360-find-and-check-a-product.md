---
name: life360-find-and-check-a-product
description: Search the public Life360/Tile hardware product catalog, fetch a product by SKU and confirm it is available.
api: openapi/life360-product-api-openapi.yml
operations:
- getApiCatalogProducts
- getApiCatalogProductsBySku
- getApiCatalogProductsBySkuAvailable
generated: '2026-10-20'
method: generated
---
# Find and check a Life360 / Tile product

Base URL `https://www.life360.com`. No authentication (the ai-plugin manifest declares `auth: none`). All calls are read-only GETs, so idempotency keys do not apply.

1. `getApiCatalogProducts` — `GET /api/catalog/products` with `search`, optional `categories`, `skus`, `sort`, `limit`. Page with `afterCursor`.
2. Pick a product's SKU and call `getApiCatalogProductsBySku` — `GET /api/catalog/products/{sku}` for full details.
3. Call `getApiCatalogProductsBySkuAvailable` — `GET /api/catalog/products/{sku}/available` before recommending a purchase.

Errors: the SKU operations document `400` (bad SKU) and `500`, both returning the spec's `ErrorResponse` schema. Do not retry a 400; a 500 may be retried with backoff.

This API covers the hardware catalog only. It exposes no member location, Circle or safety data.
