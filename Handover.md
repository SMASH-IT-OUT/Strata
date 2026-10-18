# Strata handover

Written 18 October 2026. Read this first if you are a new AI session picking up Strata. Check GitHub for anything newer.

## What Strata is

Strata runs the Qwen3.8-Flash-Next mixture-of-experts model (and its Coder, Swift 1.5 and Unsloth variants) on a normal PC with one NVIDIA or AMD graphics card plus system RAM, on Windows or Linux.

It has three parts:
- a C++/CUDA/HIP engine (`src/`, `include/`),
- a Python server with an OpenAI- and Anthropic-compatible API and a web app (`serve/`),
- a one-click installer (`setup.py`, started by `START-HERE.bat` or `setup.sh`).

## Where it runs for Smash

- Strata runs on **Blackbox** (GT ID Q1), the second PC with the GPU. It does **not** run on the MainPC (Smash's development laptop).
- The Strata server listens on port **8080**. It was moved to 8081 on 11 Oct 2026 and moved back on 12 Oct 2026, because 8080 is what is running.
- BuildBot, also on Blackbox, sends routine coding tasks to the local model. It reaches the models through llama-swap at `127.0.0.1:8090`.

## The models Smash uses

| Nickname | Model |
|---|---|
| qs1 (default) | qwen3.8-flash-next-iq3_xxs |
| qs2 | Swift-1.5-Qwen3.8-27B-GSQ-RCO-IQ2_XS-mtp.gguf (Strata Swift 1.5) |

## Where the docs are

- Installing for a user: `docs/AI_SETUP.md`. MCP server with the same steps as tools: `docs/MCP_SERVER.md`.
- How the engine works, measured numbers, API and settings: `docs/DETAILS.md` and `docs/paper/Strata-Paper.pdf`.
- AMD build: `docs/AMD_HIP.md`. More than one GPU: `docs/MULTI_GPU.md`.
- Setup tests run without a GPU or downloads: `python tools/test_setup_<name>.py`.

## Recent changes

- 12 Oct 2026: default port back to 8080.
- 12 Oct 2026: each `[strata]` console line starts with an HH:MM:SS time. `STRATA_NO_TIMESTAMPS=1` turns it off.

## Open items

- PR #4 adds the plain-language rule (ISO 24495-1) to `AGENTS.md`. Waiting for merge.

## Rules for AI working here

- Never expose the server beyond `127.0.0.1` without `--api-key`.
- Keep the docs' style: plain words, measured numbers with what they were measured on, no claims without a measurement.
- Write for people in plain language (ISO 24495-1:2023).
