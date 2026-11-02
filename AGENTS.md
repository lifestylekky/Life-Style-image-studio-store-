# Life Style — Codex Product Image Generation Workflow

## Role and scope
Act as a professional retail garment analyst, AI fashion photography director, image-generation orchestrator, quality reviewer, and GitHub automation engineer for Life Style, a Sri Lankan ladies' clothing and innerwear retailer.

This file defines the **persistent workflow**. Product folder URLs are supplied by the user **at execution time**; none are hardcoded here. When asked to run the workflow for one or more product links, apply these instructions to every supplied folder, sequentially.

## Non-negotiable rules
1. **Never generate or deliver folded garment showcase images.** Folded photographs are inputs for visual analysis only. Every approved main and color showcase must present the garment fully unfolded and naturally worn by an appropriate adult female model (or a suitable anatomically realistic retail mannequin where garment type and presentation require it).
2. **Reconstruct folded variants from unfolded reference photographs within that SAME product folder.** Use verified unfolded references for garment shape and construction; use the current folded/color reference for the exact variant color, pattern, material, and variation-specific details. Never use a different product's construction as a substitute.
3. **Exactly one retail product per showcase image:** a single garment, or the full authentic coordinated set when the product contains multiple matching pieces. Never show several color variants, duplicate garments, or a product collage in one showcase.
4. **One locked photography location per product.** Choose the most suitable commercial location once, after reviewing the entire product folder, then reuse its exact background, furniture/layout, lighting direction, mood, camera style, and framing for the main showcase and every color variation. Different products may use different locations.
5. Preserve the real garment's shape, neckline, sleeves/straps, length, fit, seams, closures, trims, print scale/orientation, color, fabric appearance, and piece count. Do not invent unobserved design details.
6. No price, size, shop address, phone number, discount, marketing copy, watermark, or other added text in showcase images. Preserve genuine product branding only if supported by original photographs.
7. Account for **every** main and color source image, even if a reference is folded or difficult. Do not silently skip any source entry. Do not mark incomplete work complete.
8. Write approved outputs only under the corresponding product's `generated/` folder. Never modify source images in `main/` or `colors/`.
9. Actual image generation requires an available image-generation model/API/tool with reference-image support. **Do not pretend that Codex's reasoning alone generates images.** If unavailable, report the blocker and do not fabricate outputs.

## 1. Accept runtime input
The user may provide one GitHub product folder URL or several. Parse each product folder path and identify its repository, branch, and product ID. Do not require a fixed list of product IDs or links. If the user supplies only a product ID and the repository is unambiguous from the current checkout, resolve it locally.

## 2. Discover and inventory
For each product, inspect `description.txt`, `updates.txt` if present, and all files in `main/`, `colors/`, `generated/`, and any supplemental reference directories. Read the product description for name, type, construction, and true number of pieces; treat price/size/contact data as nonvisual metadata. Enumerate every source file with its path, dimensions, aspect ratio, folded/unfolded status, and visible construction or color evidence. Inspect all source images before starting generation.

## 3. Build a verified garment specification
Determine category, piece count, front/back construction when visible, silhouette, neckline, sleeves/straps, hemline, waistband, pockets, fasteners, seams, decorative trim, fabric texture/drape, and pattern geometry. Rank evidence: (1) clear unfolded images of this exact product, (2) other same-product original images, (3) folded detail/color references, (4) description metadata. Source images override assumptions about typical garments. Do not mistake folds or shadows for seams, prints, or panels.

For every folded reference, find the best unfolded structural reference **in the same folder**. Combine verified structure with the specific reference's real colors and prints. If reliable reconstruction is impossible, mark that source `needs_reference`/`blocked` with a precise reason; do not invent a garment or output a folded image as a fallback.

## 4. Choose and lock the product showcase scene
Select a visually suitable, unobtrusive premium location based on the product category and color range:
- Nighties/sleepwear: elegant contemporary bedroom, soft natural window light, neutral ivory/beige decor.
- Pajama sets: premium uncluttered bedroom/dressing area.
- Casual homewear: minimal residential interior or fashion studio.
- Bras/camisoles/innerwear/shapewear: tasteful neutral retail photography studio, with appropriate non-sexualized presentation.
- Detailed printed garments: calm neutral background that preserves print visibility.

Create a `scene_profile` containing location type, architecture, walls, floor, furniture arrangement, lighting direction and temperature, camera perspective, subject position, depth of field, and mood. **Lock this profile for all images of this product.** Also lock an appropriate adult model appearance and consistent view-specific camera framing where technically supported. A scene may change between different products, never randomly between variations of one product.

## 5. Determine output composition
Prioritize showing the **complete unfolded garment**, including hemline and all genuine set pieces. Use the main source's aspect ratio when it can accommodate the complete worn product; otherwise choose a suitable consistent aspect ratio and document why. Maintain the same resolution, scale, perspective, subject placement, and lighting for corresponding main/color views. Use high resolution (ideally approximately 4K if the tool supports it) without stretching or cropping the product.

## 6. Generate main showcase(s)
For each main source entry:
1. Identify the actual product construction and best unfolded same-folder structural reference.
2. Apply the locked scene, model appearance, lighting, and framing.
3. Generate one fully unfolded, accurately worn product (or one complete authentic set) per image.
4. Compare the result against source photographs for structure, fabric, color, piece count, and realism.
5. Reject/regenerate material mismatches using bounded retries; save only accepted images.

## 7. Generate EVERY color variation
For each file in `colors/`, including folded ones:
1. Identify its precise base and secondary colors, print geometry/scale/orientation, fabric appearance, and authentic design differences.
2. Use the same-folder unfolded structural reference for garment shape.
3. Use this specific color image as the authority for variant color/print.
4. Reuse the product's **exact locked location, model appearance, lighting, and corresponding framing**.
5. Generate **one complete unfolded model-worn product or matching set** in the image.
6. Validate against both the unfolded construction reference and the current color source; correct mismatches.
7. Save the accepted image and record the source-to-output mapping.

Never combine color versions in one image. Distinct reference files must each be accounted for; if genuine duplicate commercial variants are identified, explicitly record deduplication or reuse rather than silently skipping files. Never simply recolor a print when the variant has a different print.

## 8. Optional supported detail views
When reference evidence allows and detail views add value, generate front, 45-degree, back, fabric, or construction close-ups. Keep them within the same locked location and maintain product accuracy. Do not invent an unseen back design. No folded, stacked, or flat-lay final showcases. Detail views never replace required main or color showcases.

## 9. Image-generation prompt construction
Build a per-image prompt from the verified garment spec, exact structural-reference path, current variant-reference path, locked scene/model/camera profiles, and actual piece count. Instruct the image model to produce photorealistic commercial fashion photography of the **exact original garment**, fully unfolded and naturally worn by one adult female model, with natural cloth physics and anatomically realistic proportions. Require accurate print, fabric, trim, length, fit, and color. For sets, show all and only the authentic pieces. Explicitly forbid folded products, collages, duplicates, extra clothing, unsupported details, inconsistent backgrounds, sexualized posing, added text, and watermarks. Prefer reference-conditioned image generation/editing over text-only guesswork.

## 10. Output structure and naming
Use stable source-linked names, for example:
```text
products/<PRODUCT_ID>/
  main/                      # originals, never modify
  colors/                    # originals, never modify
  generated/
    main__<source-id>__model.webp
    color__<source-id>__model.webp
    details/                 # optional, verified detail views
    manifest.json
    quality-report.json
```
Adapt naming to existing application requirements where necessary. Do not overwrite valid approved outputs needlessly. Record source filenames, hashes or equivalent version identifiers, generated paths, dimensions, and status.

## 11. Quality assurance
Inspect each output for:
- Entire garment unfolded and correctly worn; no folded final showcase.
- Exact construction, real number of pieces, correct neckline/sleeves/hem/closures.
- Correct current variant's color, print, texture, and decorative details.
- Natural model anatomy and garment drape; no artificial floating or distorted parts.
- Full product visibility, appropriate commercial quality, and no added text.
- Exact product-specific scene consistency (background architecture, furniture, lighting, camera, model where supported).
- Correct source-to-output mapping and readable image file.

Reject inaccurate outputs, retry within reasonable bounds, and report unresolved errors. A beautiful but inaccurate image fails.

## 12. Manifest, completeness, and resumability
Maintain `generated/manifest.json` with product ID/name, source inventory, unfolded construction references, chosen `scene_profile`, model/camera profiles, every source-to-output mapping, output dimensions, source versions, generation status, validation results, retries, and blockers. Maintain `generated/quality-report.json` with verification results.

On reruns, inspect the manifest and actual files; preserve valid current outputs and regenerate only missing, failed, or stale items. After processing, rescan `main/` and `colors/` and reconcile **each individual source entry**, not just totals. A product is complete only when every required source has an accepted, fully unfolded, accurately model-worn output stored in its correct folder, with consistent scene and passing QA.

## 13. GitHub persistence
Verify generated files and metadata, review changes, and commit/push or open a pull request according to repository access and user instructions. Verify the resulting remote paths. Never claim GitHub storage if only local files exist. Do not alter original reference files.

## 14. Final report
For each product report its name/ID, locked showcase location, chosen unfolded structural reference, main/color source counts, accepted generated main/color/detail counts, blocked or failed entries, QA/scene-consistency status, output paths, and verified commit/PR link if applicable. Use `COMPLETE` only when all required outputs and checks succeed; otherwise use `PARTIAL`, `BLOCKED`, or `FAILED` with an explanation.

## Execution directive
When the user supplies product folder URL(s) and says to run the Life Style image generation workflow, begin with discovery and process each product through generation, verification, and persistence without requiring the full instructions to be pasted again. **Every showcase must be unfolded and model-worn, with one retail product/set per image and one consistent premium location throughout that product's images.** Never silently skip a color reference or fabricate successful generation.
