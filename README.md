<div align="center">

```
 ██████╗ ███████╗████████╗███████╗██████╗  ██████╗██████╗
 ██╔══██╗██╔════╝╚══██╔══╝██╔════╝██╔══██╗██╔════╝╚════██╗
 ██████╔╝█████╗     ██║   █████╗  ██████╔╝██║      █████╔╝
 ██╔═══╝ ██╔══╝     ██║   ██╔══╝  ██╔══██╗██║      ╚═══██╗
 ██║     ███████╗   ██║   ███████╗██║  ██║╚██████╗██████╔╝
 ╚═╝     ╚══════╝   ╚═╝   ╚══════╝╚═╝  ╚═╝ ╚═════╝╚═════╝
```

**Building open-source ML tooling for AMD APUs. Squeezing every FLOP out of hardware the industry forgot about.**

</div>

---

I found 3 bugs blocking ML on AMD's newest GPU architecture (gfx1150/RDNA 3.5), built a public PyTorch wheel for it, and root-caused an NPU driver bug on Strix Point ([amd/xdna-driver #1257](https://github.com/amd/xdna-driver/issues/1257)).

Currently prototyping a routing system for CPU + GPU inference on AMD APUs (+ NPU when runtime support lands), using hyperdimensional computing. HDC routing showed 21% throughput improvement in Phase 1 benchmarks.

**Rust · Python · Kotlin · JavaScript · C++ · Shell**
**CachyOS · Docker · Chrome Extension API · Vulkan**

**CEH in Training · HackerOne Researcher · Building [AgentSpyBoo](https://github.com/Peterc3-dev/agentspyboo) Phase 3**

---

### Bugs I Found

- [amd/xdna-driver #1257](https://github.com/amd/xdna-driver/issues/1257) — NPU driver fails on cold boot for Strix Point (PCI ID `17f0`)
- [CachyOS-PKGBUILDS #1311](https://github.com/CachyOS-PKGBUILDS/issues/1311) — Firmware symlink inversion in `linux-firmware-other`
- [MIOpen gfx1150](https://github.com/Peterc3-dev/miopen-gfx1150) — 3 bugs: architecture whitelist, CK crash, workspace=0

### Things I Shipped

- Chrome extensions · 5 published ([Claude Wide Chat](https://github.com/Peterc3-dev/claude-wide-chat) · [Phosphor Green Stylus](https://github.com/Peterc3-dev/phosphor-green-stylus) · [CRT Magnifier Lens](https://github.com/Peterc3-dev/crt-magnifier-lens) · [Gentle Reader](https://github.com/Peterc3-dev/gentle-reader) · [Claude Voice Reader](https://github.com/Peterc3-dev/claude-voice-reader))
- Android apps · 4 shipped ([Retune432](https://github.com/Peterc3-dev/retune432-android) · [D-Board](https://github.com/Peterc3-dev/d-board) · [PlateAuth](https://github.com/Peterc3-dev/PlateAuth) · [HingeAxis](https://github.com/Peterc3-dev/HingeAxis))
- [PyTorch for gfx1150](https://github.com/Peterc3-dev/pytorch-gfx1150) — built from source for RDNA 3.5
- [R.A.G-Race-Router](https://github.com/Peterc3-dev/recursive-routing-racer) — CPU+iGPU inference routing with NPU path wired
- [AgentSpyBoo](https://github.com/Peterc3-dev/agentspyboo) — Rust AI red team agent
- [Learning Forge](https://github.com/Peterc3-dev/learning-forge) — applied security learning archive

---

<div align="center">

*Former ATP Training Partner (Federer/Djokovic). Yes, really.*

</div>