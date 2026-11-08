# Operation Veritas

A website and research operation that stress-tests whether AI answers
are consistent and truthful — built on local Ollama, fully open source.

## Run it

```bash
pip install flask
py veritas.py          # -> http://localhost:5510
```

Set `OLLAMA_MODEL` to override the model (default `qwen2.5:1.5b`). With Ollama
offline the site still runs in **demo mode** (simulated reports).

## Pages

- `/` — operation overview
- `/research` — methodology, limitations, roadmap
- `/detector` — live check UI

## API

```
GET  /api/status          -> {"ollama": bool, "model": str}
POST /api/check {question} -> verdict report
```

## The three tests

1. **Consistency** — same question sampled 5× at temperature 0.9;
   agreement score via pairwise text similarity.
2. **Skeptic challenge** — the model must defend its answer and state
   a confidence percentage.
3. **Claim audit** — flags sentences with numbers, studies, dates,
   or absolute claims for manual verification.

See `research/CHARTER.md` for the research program.

MIT licensed.

## GitHub Pages

A static version of the site is published from `docs/` at
https://departement-of-dyon.github.io/veritas/

The static Detector runs client-side against a **local** Ollama —
for remote visitors it shows setup instructions. To let the Pages site
call Ollama directly, start it with:

```bash
set OLLAMA_ORIGINS=https://departement-of-dyon.github.io
ollama serve
```

(That exposes your local Ollama to that origin only — or use `*` to
allow any site, which is less safe.)
