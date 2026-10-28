# AGENTS.md

Strata runs the Qwen3.8-Flash-Next mixture-of-experts model (and its Coder, Swift 1.5 and Unsloth variants) on a
normal PC: one NVIDIA or AMD graphics card plus system RAM, on Windows or Linux. It has a C++/CUDA/HIP engine
(`src/`, `include/`), a Python server with an OpenAI- and Anthropic-compatible API and a web app (`serve/`), and a
one-click installer (`setup.py`, started by `START-HERE.bat` / `setup.sh`).

## Installing Strata for a user

Follow **[docs/AI_SETUP.md](docs/AI_SETUP.md)**: check the PC, pick the model by RAM, run setup non-interactively,
start and verify the server, and connect the user's apps. Never expose the server beyond `127.0.0.1` without
`--api-key`. As an alternative to shell commands, Strata's MCP server ([docs/MCP_SERVER.md](docs/MCP_SERVER.md))
offers the same steps as tools.

## Working on the code

- How the engine works, every measured number, the API and all settings: [docs/DETAILS.md](docs/DETAILS.md) and
  the [paper](docs/paper/Strata-Paper.pdf).
- AMD (HIP) build and validation: [docs/AMD_HIP.md](docs/AMD_HIP.md); multi-GPU: [docs/MULTI_GPU.md](docs/MULTI_GPU.md).
- Setup's own tests run without a GPU or downloads: `python tools/test_setup_<name>.py` (for example
  `tools/test_setup_amd.py`, `tools/test_setup_choices.py`).
- Keep the docs' style: plain words, measured numbers with what they were measured on, no claims without a
  measurement.

## Agent shortcuts: Ace and Bob (owner, 2026-10-28)

The owner hands work to two Claude agents by a short name. The three names on each line mean the same agent:

| they write | they mean | name in GT and on GitHub |
|---|---|---|
| `Ace`, `AC1` or `Claude-1` | the Claude project in the owner's first Claude account | `Claude-1` |
| `Bob`, `AC2` or `Claude-2` | the Claude project in the owner's second Claude account ("Claude 2" in GT's Usage screens) | `Claude-2` |

"Give this to Bob" means the item now belongs to Claude-2: assign its GT task to `Claude-2`, or, for a GitHub issue
with no GT task yet, add the label `agent: Claude-2`. Ace works the same way with `Claude-1`. Do not start an item
that belongs to the other agent. Full rules:
[two-claude-projects.md](https://github.com/SMASH-IT-OUT/GT/blob/main/docs/two-claude-projects.md) in GT.
