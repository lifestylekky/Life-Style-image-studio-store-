# Missing generated-image workflow — 2026-11-04

**Overall status: PARTIAL.** Scanned 21 products; processed all 8 folders initially lacking generated image files. Saved 35 accepted images across 5 complete products. Three products remain blocked, with 14 source entries explicitly accounted for. Existing 13 nonempty products and all 49 target originals are unchanged.

| Product | ID / outputs | Main | Colors | Accepted | Status | Verified product commit |
|---|---|---:|---:|---:|---|---|
| Unidentified product — illustrated portrait references | [1bfc349a-7912-4e6b-b7ec-3aa1457de4d9](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/1bfc349a-7912-4e6b-b7ec-3aa1457de4d9/generated) | 1 | 1 | 0 | BLOCKED | [`73e1a91`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/73e1a917c1d556a29646fec59fd3c7d0584dfe38) |
| VELONA SLEEVELESS PLAIN NIGHTY | [2a01cb8f-1485-4e55-a2a1-2d926904f7f5](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/2a01cb8f-1485-4e55-a2a1-2d926904f7f5/generated) | 1 | 9 | 10 | COMPLETE | [`73e1a91`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/73e1a917c1d556a29646fec59fd3c7d0584dfe38) |
| Printed cotton-look short-sleeve cropped pajama set (descriptive name; empty product description) | [31802d53-4810-42b8-ba1a-e1bdd57dfda8](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/31802d53-4810-42b8-ba1a-e1bdd57dfda8/generated) | 1 | 10 | 11 | COMPLETE | [`73ecc5c`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/73ecc5c3ab7d548ed1ddc013ea9ff81607f370c4) |
| VELONA SHORT MODEL NIGHTY | [61b7971d-fef8-4733-aac7-8a70baf32202](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/61b7971d-fef8-4733-aac7-8a70baf32202/generated) | 1 | 9 | 0 | BLOCKED | [`86ef4da`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/86ef4daef3207dd04e4ee69a0c67812f4d1f01d7) |
| VELONA SLEEVE LESS NIGHTY — polka dot, 40 inch | [6c17c7d7-814a-4f56-99a0-df2d27dcd619](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/6c17c7d7-814a-4f56-99a0-df2d27dcd619/generated) | 1 | 9 | 10 | COMPLETE | [`86ef4da`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/86ef4daef3207dd04e4ee69a0c67812f4d1f01d7) |
| Unidentified product — illustrated portrait references | [787a930b-5fa6-42a2-a9aa-a1e7511b3ae2](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/787a930b-5fa6-42a2-a9aa-a1e7511b3ae2/generated) | 1 | 1 | 0 | BLOCKED | [`1bb760b`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/1bb760b909b5c081aa397cf66625c64cdc8616b7) |
| Sleeveless floral-yoke polka-dot satin nightdress (descriptive name) | [c5566ed5-6279-4b34-820d-23154c6e885e](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/c5566ed5-6279-4b34-820d-23154c6e885e/generated) | 1 | 1 | 2 | COMPLETE | [`1bb760b`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/1bb760b909b5c081aa397cf66625c64cdc8616b7) |
| Short-sleeve cropped pajama set (descriptive name) | [eb2bafda-eefe-433a-963f-8070749112d2](https://github.com/lifestylekky/Life-Style-image-studio-store-/tree/main/products/eb2bafda-eefe-433a-963f-8070749112d2/generated) | 1 | 1 | 2 | COMPLETE | [`1bb760b`](https://github.com/lifestylekky/Life-Style-image-studio-store-/commit/1bb760b909b5c081aa397cf66625c64cdc8616b7) |

## Blockers

- `1bfc349a-7912-4e6b-b7ec-3aa1457de4d9` and `787a930b-5fa6-42a2-a9aa-a1e7511b3ae2`: both main/color originals are illustrated male street portraits. Complete garment construction, actual fabric and hem are unverified; no product descriptions are present. Need actual product references.
- `61b7971d-fef8-4733-aac7-8a70baf32202`: image tool rejected two adult-retail main attempts and one independent folded pink/hanging-structure attempt at input with `moderation_blocked`, category `sexual`. No image returned. Request IDs: `986b6f3c-68b5-487e-b5b3-c2d401f0abf8`, `ea931d31-bf4a-4ef8-a4a5-0ec1ccdb6c88`, `1f9f13c6-7af6-482d-9fa1-a1f79ef410d8`. All 10 source entries remain explicitly blocked; 8 colors were not individually submitted after the shared product blocker.

## Delivery and verification

Approved images, source-linked filenames, manifests and individual QA reports are saved in each product’s `generated/` folder. All 35 accepted images decode and match recorded hashes; all 51 new product files were verified against fetched GitHub main blobs. Native resolutions: 1024×1536 and 1086×1448 PNG; no 4K/upscaling claim. Six inaccurate candidates were rejected/corrected before acceptance.

Each completed product uses a consistent ivory/cream bedroom, fixed furniture/window arrangement, same adult model, lighting and camera, with subtle pose variations. Exact scene profiles, construction references, source/output mappings and validation limitations are in the JSON report and per-product manifests. No folded final showcases were saved.

Remote product files verified on main at `1bb760b909b5c081aa397cf66625c64cdc8616b7`. This report's own commit is available through Git history.
