```
 ██████╗ ███████╗████████╗███████╗██████╗  ██████╗██████╗
 ██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗██╔════╝╚════██╗
 ██████╔╝█████╗     ██║   █████╗  ██████╔╝██║      █████╔╝
 ██╔═══╝ ██╔══╝     ██║   ██╔══╝  ██╔══██╗██║      ╚═══██╗
 ██║     ███████╗   ██║   ███████╗██║  ██║╚██████╗██████╔╝
 ╚═╝     ╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝ ╚═════╝╚═════╝
```

Building open-source ML tooling for AMD APUs. Squeezing every FLOP out of hardware the industry forgot about.

I found 4 bugs blocking ML on AMD's newest GPU architecture (gfx1150/RDNA 3.5), built the first public PyTorch for it, patched the NPU driver, and designed a tri-processor inference engine that routes compute across CPU + GPU + NPU using hyperdimensional computing. Also do security research, Android apps, and creative coding.

---

### AMD / ML Stack

| Project | What it does |
|---------|-------------|
| [`rag-race-router`](https://github.com/Peterc3-dev/rag-race-router) | R.A.G-Race-Router [TAP] — Tri-processor inference engine. HDC cosine similarity routing across CPU+iGPU+NPU on Ryzen AI 300 |
| [`miopen-gfx1150`](https://github.com/Peterc3-dev/miopen-gfx1150) | Found 3 bugs blocking ML training on RDNA 3.5 — whitelist patch, CK VGPR analysis, solver availability matrix |
| [`pytorch-gfx1150`](https://github.com/Peterc3-dev/pytorch-gfx1150) | First public PyTorch build for AMD RDNA 3.5 (Radeon 890M) with native GPU acceleration |
| [`amdxdna-strix-fix`](https://github.com/Peterc3-dev/amdxdna-strix-fix) | NPU driver patch for Strix Point — SMU init bypass, brought XDNA 2 NPU to life on Linux |
| [`unified-ml`](https://github.com/Peterc3-dev/unified-ml) | Custom HIP + Vulkan kernels proving 60% Vulkan speedup over ROCm on consumer AMD GPUs |
| [`apu-codec`](https://github.com/Peterc3-dev/apu-codec) | Neural audio codec from scratch — NPU encoder, GPU decoder, 512x compression at 44.1kHz |

### Security / Tools

| Project | What it does |
|---------|-------------|
| [`graphql-authz-fuzzer`](https://github.com/Peterc3-dev/graphql-authz-fuzzer) | Detects GraphQL mutation authorization bypass — zero dependencies, pure Python |
| [`PlateAuth`](https://github.com/Peterc3-dev/PlateAuth) | NFC behavioral biometric authentication research prototype (Android/Kotlin) |
| [`cin-agent`](https://github.com/Peterc3-dev/cin-agent) | Telegram bot with natural language shell execution and safe command sandboxing |

### Apps / Creative

| Project | What it does |
|---------|-------------|
| [`retune432-android`](https://github.com/Peterc3-dev/retune432-android) | Batch A440→A432 Hz audio converter with metadata preservation |
| [`d-board`](https://github.com/Peterc3-dev/d-board) | Ortholinear Android keyboard — true grid layout, zero stagger |
| [`geodancer`](https://github.com/Peterc3-dev/geodancer) | Audio-reactive geometric wireframe dancer — C++, OpenGL, libaubio |
| [`crt-magnifier-lens`](https://github.com/Peterc3-dev/crt-magnifier-lens) | Chrome extension — draggable CRT magnifier with barrel distortion |

---

### Currently working on

- **Vulkan PyTorch backend** — PrivateUse1 dispatch, no ROCm needed, runs on any GPU
- **HDC routing on NPU** — Hyperdimensional Computing on XDNA 2 systolic array for sub-100us dispatch
- **Rust rewrite** — zero-GIL tri-processor coordination with PyO3 bindings
- **Upstream contributions** — MIOpen/CK/PyTorch issues filed, AMD engineers engaged

---

### Tech

`Python` · `Rust` · `C++/OpenGL` · `Kotlin` · `JavaScript` · `GLSL/SPIR-V` · `HIP/ROCm` · `Vulkan (Kompute)` · `IREE/MLIR` · `Android SDK` · `Chrome Extensions (MV3)` · `GraphQL` · `Linux (CachyOS)` · `Tailscale`

---

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Peterc3-dev&show_icons=true&theme=chartreuse-dark&hide_border=true&bg_color=0a0a0a&title_color=00ff00&icon_color=33ff33&text_color=00ff00" />
</p>

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Peterc3-dev&layout=compact&theme=chartreuse-dark&hide_border=true&bg_color=0a0a0a&title_color=00ff00&text_color=00ff00" />
</p>
