---
generated: '2026-09-25'
method: generated
name: framethrower-explore-a-film
description: Find a film in the FrameThrower catalogue, read its record, and page through its indexed frames.
api: openapi/framethrower-openapi.yml
operations: [suggest, listFilms, getFilm, listFilmFrames]
source: Grounded in openapi/framethrower-openapi.yml (captured 2026-09-25 from https://framethrower.ai/api/v1/openapi.json); every operationId verified verbatim in that spec.
---

# Explore a film

1. `suggest` (GET /suggest?q=) for free prefix autocompletion of a title, director or DP.
2. `listFilms` (GET /films) with `q`, `sort`, `min_frames` and `page`/`per_page` to find the film; each entry carries `slug`, `frameCount` and `framesUrl`.
3. `getFilm` (GET /films/{slug}) for the film record.
4. `listFilmFrames` (GET /films/frames?slug=) with `page`/`per_page` to walk its frames.

Rules: bearer `ft_` token; 2 credits per call except `suggest` (free); HTTP 402 when the balance is short; 404 "No such film" for an unknown slug. See conventions/framethrower-conventions.yml.
