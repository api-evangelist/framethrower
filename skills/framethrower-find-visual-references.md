---
generated: '2026-09-25'
method: generated
name: framethrower-find-visual-references
description: Turn a scene description, colour palette or reference image into a curated set of film-still references, then refine with similar frames and pull frame detail (including the AI prompt).
api: openapi/framethrower-openapi.yml
operations: [search, searchByColor, searchByImage, findSimilar, getFrame]
source: Grounded in openapi/framethrower-openapi.yml (captured 2026-09-25 from https://framethrower.ai/api/v1/openapi.json); every operationId verified verbatim in that spec.
---

# Find visual references for a scene

1. `search` (POST /search) with a plain-language `query` ("neon-lit rainy street at night"); narrow with craft fields such as `shot_type`, `lens`, `lighting`, `time_of_day`, `era`. Or start from colour with `searchByColor` (POST /search/color) or from an image with `searchByImage` (POST /search/image, 10 credits).
2. Pick the strongest frame ids and call `findSimilar` (POST /similar) with `frameId` (or `frameIds`) to widen the set in the same visual direction.
3. For each chosen frame call `getFrame` (GET /frames?id=) to get film credits, scene metadata, palette, the composed AI `prompt`, thumbnail URLs and the deep link.

Rules: bearer token with the `ft_` prefix (authentication/framethrower-authentication.yml). Each call costs credits (2 for most reads, 10 for image search); read `X-Credits-Remaining` and stop on HTTP 402 `insufficient_credits` (errors/framethrower-problem-types.yml). Responses are references (metadata, thumbnails, deep links), never licensed image bytes; rights stay with their owners.
