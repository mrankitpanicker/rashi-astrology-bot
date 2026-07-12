# Rashi Astrology Bot

Fully local, automated video generation for astrology (rashi) and devotional content. Script generation, narration, subtitling, and rendering all run on local hardware through a deterministic pipeline — no servers, no external data transmission. Finished videos are uploaded to publishing platforms as the final step.

## Repository layout

| Directory | Purpose |
|---|---|
| `Astro/` | Astrology (rashi) video pipeline — content generation → render → upload |
| `Dharmik/` | Devotional-content variant of the same pipeline |

Both pipelines share the same module structure:

- `main.py` — entry point and orchestration
- `config.py` — pipeline configuration (paths, models, output settings)
- `datamodel.py` — content/job data models
- `generator.py` — script and content generation
- `videopipeline.py` — narration, subtitles, and FFmpeg rendering
- `upload.py` (Astro only) — publishing/upload step
- `utils.py` — shared helpers

## Design

```
Client Inputs → Local Processing Engine → Local Output Files → Publishing Platforms
```

- All computation on the local machine; no data stored or transmitted remotely
- Deterministic outputs — same inputs produce the same video
- Delivered as an offline production tool, not a hosted service

See `Astro/SYSTEM DESIGN.txt` for the full architecture notes.

## Running

```bash
# configure config.py in the pipeline you want, then:
python Astro/main.py     # astrology pipeline
python Dharmik/main.py   # devotional pipeline
```

---

Part of a family of local media-generation tools — see [apex-ai-shortz](https://github.com/mrankitpanicker/apex-ai-shortz) for the current maintained pipeline and [apex-portfolio](https://github.com/mrankitpanicker/apex-portfolio) for the full project ecosystem.
