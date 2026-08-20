```
 ██████╗ ███████╗████████╗███████╗██████╗  ██████╗██████╗
 ██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗██╔════╝╚════██╗
 ██████╔╝█████╗     ██║   █████╗  ██████╔╝██║      █████╔╝
 ██╔═══╝ ██╔══╝     ██║   ██╔══╝  ██╔══██╗██║      ╚═══██╗
 ██║     ███████╗   ██║   ███████╗██║  ██║╚██████╗██████╔╝
 ╚═╝     ╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝ ╚═════╝╚═════╝
```

Self-taught systems programmer working at the **GPU / driver / ML-runtime boundary**. From-scratch on-device NPU inference across **two vendors' silicon** — AMD (Radeon 890M iGPU + XDNA 2 NPU) and MediaTek (MDLA / APU 650). I build PyTorch backends, patch kernel drivers, drive vendor NPU compilers directly, and write the upstream bug reports for hardware the software stack hasn't caught up to yet — and I publish all of it.

Async / written-first collaborator. Comfortable in Rust and C++ down to the dispatcher, allocator, and SPIR-V level.

---

### Featured work

| Project | What it actually does |
|---------|----------------------|
| [`torch-vulkan`](https://github.com/Peterc3-dev/torch-vulkan) | From-scratch PyTorch device backend (PrivateUse1 + Vulkan compute) for the Radeon 890M iGPU. 39 hand-written SPIR-V compute shaders, custom allocator, buffer pooling, Q4 matmul. C++17 / pybind11. Functional prototype. |
| [`amdxdna-strix-fix`](https://github.com/Peterc3-dev/amdxdna-strix-fix) | Kernel driver patch — root-caused and fixed an SMU init-order bug in the in-tree `amdxdna` driver (Linux 6.14+) that left the Ryzen AI NPU dead on cold boot. Brought an otherwise-unusable NPU online. |
| [`mdla-cnn-engine`](https://github.com/Peterc3-dev/mdla-cnn-engine) | From-scratch INT8 inference engine for a **MediaTek MDLA** phone NPU (MT6886) — drives the on-device Neuron compiler directly, bypassing the gated NeuroPilot SDK. Four stock CNNs run end-to-end on the NPU through one pipeline, hardware-witnessed. Honestly scoped (CNN-only, stock models — the contribution is the path to the silicon). |
| [`recursive-routing-racer`](https://github.com/Peterc3-dev/recursive-routing-racer) | Tri-processor dispatch runtime — routes ML workloads across CPU + iGPU (Vulkan) + NPU (XDNA) on Ryzen AI 300. REINFORCE-trained scheduler, SQLite-backed state, hardware monitoring. Working prototype, ~5,100 lines Python. |
| [`kv-compressor`](https://github.com/Peterc3-dev/kv-compressor) | KV-cache compression experiment with a documented **negative result** (`FINDINGS.md`) — measured where the approach stops paying off, written up honestly rather than buried. |
| [`graphql-authz-fuzzer`](https://github.com/Peterc3-dev/graphql-authz-fuzzer) | GraphQL mutation authorization tester — schema introspection, probe generation, auth-gap classification. Standard-library only, has tests. |
| [`cube-memory`](https://github.com/Peterc3-dev/cube-memory) | Research code + the public **VSA negative-results preprint** ([`/paper`](https://github.com/Peterc3-dev/cube-memory/tree/master/paper) — 12-page PDF, LaTeX source, 6 figures). See Research below. |

### More AMD / ML systems work

| Project | What it actually does |
|---------|----------------------|
| [`recursive-routing-racer-rs`](https://github.com/Peterc3-dev/recursive-routing-racer-rs) | LLM inference engine from scratch in Rust — GGUF loading, BPE tokenizer, KV cache, Vulkan GPU dispatch, speculative decoding. Runs Phi-4 Mini at ~5.5 tok/s. Learning project. |
| [`pytorch-gfx1150`](https://github.com/Peterc3-dev/pytorch-gfx1150) | PyTorch built from source for the Radeon 890M (gfx1150) — build scripts, AOTriton workarounds, GCC 15 fixes, documented. |
| [`miopen-gfx1150`](https://github.com/Peterc3-dev/miopen-gfx1150) | MIOpen analysis for RDNA 3.5 — whitelist patch, CK VGPR analysis, solver-availability matrix; 3-bug writeup. |
| [`unified-ml`](https://github.com/Peterc3-dev/unified-ml) | HIP + Vulkan unified-memory strategy benchmarks on AMD APUs, plus a GGUF parser (712 lines, 5 quant formats + F32/F16). |

---

### Upstream bug reports (RDNA 3.5 / Strix ML-enablement gaps)

Filed reproducible upstream issues against PyTorch, ROCm, and AMD driver projects documenting where the software stack breaks on this silicon. Several **triaged by maintainers**; one closed after direct collaboration with an AMD engineer. (These are reported & triaged *issues*, not merged fixes.)

- PyTorch [#178934](https://github.com/pytorch/pytorch/issues/178934), [#178839](https://github.com/pytorch/pytorch/issues/178839) — MIOpen Gemm solvers return `workspace_size=0` on gfx1150 (**triaged**, `has-workaround`)
- ROCm/rocm-libraries [#6045](https://github.com/ROCm/rocm-libraries/issues/6045), [#6048](https://github.com/ROCm/rocm-libraries/issues/6048) — gfx1150 missing from CK whitelist; CK VGPR mismatch (in triage)
- ROCm/composable_kernel [#3724](https://github.com/ROCm/composable_kernel/issues/3724) — WMMA kernels fail on gfx1150
- amd/xdna-driver [#1257](https://github.com/amd/xdna-driver/issues/1257) — `aie2_smu_init` cold-boot precheck failure (closed after collaboration with AMD)
- amd/Triton-XDNA [#33](https://github.com/amd/Triton-XDNA/issues/33) — `detect_npu_version()` doesn't recognize RyzenAI-npu4

---

### Research / writing

**"Two Negative Results for Vector Symbolic Architectures"** — single-author 12-page preprint showing VSAs fail at FFN replacement (a rank bottleneck: VSA retrieval is rank ≤ top-k while FFN effective rank exceeds 2048) and at compositional image generation, with cross-scale validation on Qwen3-4B / 8B / 27B. **Preprint, targeting the NeurIPS Negative Results track** — not peer-reviewed.
Read it: [github.com/Peterc3-dev/cube-memory/tree/master/paper](https://github.com/Peterc3-dev/cube-memory/tree/master/paper)

---

### Certifications

**CompTIA Security+** (SY0-701) — August 2026. [Verify on Credly](https://www.credly.com/earner/)

**GitHub Certified: Agentic AI Developer** — GitHub, July 2026 (Exam GH-600). [Verify credential](https://learn.microsoft.com/api/credentials/share/en-us/PeterClemente-1378/EF8E60BA7F3BF8A9?sharingId=243EEB743D6D589F)

---

### Currently exploring

- **torch-vulkan** — expanding op coverage on the Vulkan/SPIR-V PyTorch backend
- **amdxdna NPU** — driver debugging and bring-up on XDNA 2 (Strix Point)
- Cross-arch ML enablement on RDNA 3.5 + XDNA 2 — building and reporting upstream as gaps surface

---

### Tech

`Rust` · `C++17` · `Python` · `GLSL/SPIR-V` · `Vulkan (Kompute)` · `HIP/ROCm` · `Linux kernel (driver debugging)` · `CachyOS/Arch` · `Kotlin / Android SDK` · `GraphQL` · `Tailscale`

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Peterc3-dev&show_icons=true&theme=chartreuse-dark&hide_border=true&bg_color=0a0a0a&title_color=00ff00&icon_color=33ff33&text_color=00ff00" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Peterc3-dev&layout=compact&theme=chartreuse-dark&hide_border=true&bg_color=0a0a0a&title_color=00ff00&text_color=00ff00" />
</p>
