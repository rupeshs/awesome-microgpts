# awesome-microgpt [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of ports, variants, and extensions of Andrej Karpathy's [microgpt.py](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95) — a 200-line, dependency-free GPT in pure Python.

---

## Original

| Name | Author | Language | Description |
|------|--------|----------|-------------|
| [microgpt.py](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95) | [@karpathy](https://github.com/karpathy) | Python | The original. 200 lines, zero dependencies, complete GPT: tokenizer, autograd, transformer, Adam, training loop, inference. MIT licensed. |

---

## Language Ports

### Systems Languages

| Name | Author | Language | Speedup vs CPython | Notes |
|------|--------|----------|--------------------|-------|
| [microgpt.cpp](https://github.com/Charbel199/microgpt.cpp) | [@Charbel199](https://github.com/Charbel199) | C++ | ~219x | Single-file, single-threaded. Tape-based autograd. SoA arena allocator. Fused multiply-add. Stack KV cache. Benchmarked ~109x vs PyPy. |
| [rust-microgpt](https://github.com/mplekh/rust-microgpt) | [@mplekh](https://github.com/mplekh) | Rust | ~440x | Tape autograd with MT19937 RNG for 1:1 output parity with microgpt.py. Uses unsafe blocks for max performance. ~74x vs PyPy. |
| [EEmicroGPT](https://github.com/Entrpi/eemicrogpt) | [@Entrpi](https://github.com/Entrpi) | C | >440x | Single-file, dependency-free C. Explicit chain rule (no autograd overhead). SIMD/vectorized. Targets L1-resident weights on a single CPU core. |

### Go

| Name | Author | Language | Speedup vs CPython | Notes |
|------|--------|----------|--------------------|-------|
| [go-microgpt](https://github.com/prasad83/go-microgpt) | [@prasad83](https://github.com/prasad83) | Go | ~109x | Pure Go, no external dependencies. Clean modular layout: autograd, tokenizer, model, trainer. ~108.96x faster than original Python. |

### JavaScript / TypeScript

| Name | Author | Language | Notes |
|------|--------|----------|-------|
| [microgpt-ts](https://github.com/dubzdubz/microgpt-ts) | [@dubzdubz](https://github.com/dubzdubz) | TypeScript | Clean, fully typed code. Works in the browser. Zero dependencies. Live demo at [microgpt-ts.vercel.app](https://microgpt-ts.vercel.app/). |
| [microgptjs](https://github.com/assassindesign/microgptjs) | [@assassindesign](https://github.com/assassindesign) | JavaScript (Node.js, ES5) | Node.js port. Supports training on poetry/Chinese text. |
| [trainmyowngpt](https://github.com/jayyvk/trainmyowngpt) | [@jayyvk](https://github.com/jayyvk) | JavaScript | Browser-based visual UI. Real-time training visualization. Live demo at [trainmyowngpt.com](https://trainmyowngpt.com/). |

### Julia

| Name | Author | Language | Notes |
|------|--------|----------|-------|
| [microgpt_jl](https://github.com/ranton256/microgpt_jl) | [@ranton256](https://github.com/ranton256) | Julia (Flux.jl) | ~70x faster than Python (1.3s vs 89.2s). CUDA + Apple Metal support. Checkpoint persistence. 125 tests. Extended Shakespeare training mode. |

### OCaml

| Name | Author | Language | Notes |
|------|--------|----------|-------|
| [ocaml-microgpt](https://github.com/smimram/ocaml-microgpt) | [@smimram](https://github.com/smimram) | OCaml | ~6x faster than Python. |

---

## Python Variants & Extensions

| Name | Author | Description |
|------|--------|-------------|
| [tapegpt.py](https://gist.github.com/mplekh/3afbdfb9f063cf531cfd3d00685cfdc0) | [@mplekh](https://github.com/mplekh) | Python with Wengert tape autograd (same algorithm as microgpt.cpp/rust-microgpt). 1:1 output parity with microgpt.py. ~4x speedup over original. Good for benchmarking algorithm vs compiler. |
| [microgpt + EMA + ASCII plot](https://gist.github.com/santakd/a3645e3b58246e9b092a8633bf95659c) | [@santakd](https://github.com/santakd) | Adds argparse, rich metrics, EMA loss, ASCII loss curve (raw + EMA overlay), live progress bar with ETA. Still pure stdlib. |
| [AttoGPT](https://gist.github.com/JGalego/26d617e5c939af0c32f3c16e4e392803) | [@JGalego](https://github.com/JGalego) | Golf'd microgpt compressed to ~50 lines. A readability crime scene. |
| [microgpt (66 lines)](https://gist.github.com/karpathy/8627fe009c40f57531cb18360106ce95#gistcomment-6000490) | [@metacritical](https://github.com/metacritical) | Compressed to ~66 lines. Described as "a compression experiment and a readability crime scene." |
| [MoE microgpt](https://gist.github.com/credo92/4ba7d2db64bd6993864aaebbf13983cc) | [@credo92](https://github.com/credo92) | Adds a naive Mixture of Experts (MoE) layer to microgpt. |
| [ko-microgpt](https://github.com/woduq1414/ko-microgpt) | [@woduq1414](https://github.com/woduq1414) | Korean-language microgpt. Live demo at [ko-microgpt.vercel.app](https://ko-microgpt.vercel.app/). |
| [gpahal/microgpt](https://github.com/gpahal/microgpt) | [@gpahal](https://github.com/gpahal) | PyTorch-based micro GPT with RoPE, GQA, multi-GPU training, cosine LR, HellaSwag eval, 2-stage training with weight souping. |

---

## Ecosystem & Extensions

| Name | Author | Description |
|------|--------|-------------|
| [molequla](https://github.com/ariannamethod/molequla) | [@ariannamethod](https://github.com/ariannamethod) | Multi-organism autonomous training ecology. Go + C + Rust + JS + AML. Organisms grow architecture at runtime (ontogenesis), exchange "DNA" cross-training, reproduce via mitosis, self-regulate via SyntropyTracker. |
| [purevlm](https://github.com/sailfish009/purevlm) | [@sailfish009](https://github.com/sailfish009) | Vision-Language Model in the spirit of microgpt. Most atomic VLM. |
| [chuck-optimizer](https://github.com/ariannamethod/chuck-optimizer) | [@ariannamethod](https://github.com/ariannamethod) | Adam variant with self-awareness: self-modulates λ from loss trend, injects noise η to escape plateaus. Claims 38% faster convergence than Adam. |

---

## Benchmarks

Performance relative to CPython 3.14 (lower µs/sample = faster):

| Implementation | µs/sample | Speedup vs CPython |
|---|---|---|
| CPython 3.14 | 713,200 | 1x |
| PyPy 7.3.17 | 301,400 | 2.4x |
| microgpt.cpp | 3,260 | ~219x |
| rust-microgpt | 1,620 | ~440x |

> Go runtime: ~108.96x faster than original CPython (5:23.61 min vs 2.97s for 1,000 steps).

---

## Related Projects (Karpathy lineage)

| Name | Description |
|------|-------------|
| [micrograd](https://github.com/karpathy/micrograd) | The autograd engine microgpt's `Value` class is based on |
| [makemore](https://github.com/karpathy/makemore) | Character-level name generator; microgpt uses its names dataset |
| [nanoGPT](https://github.com/karpathy/nanoGPT) | Full-scale PyTorch GPT training; the production counterpart |
| [minGPT](https://github.com/karpathy/minGPT) | Earlier minimal PyTorch GPT re-implementation |

---

## Contributing

PRs welcome! Please include: repo URL, author, language, brief description, and speedup/benchmark if available.

