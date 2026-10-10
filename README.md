# Multi-Objective Scheduler for 5G NR (5G-LENA / ns-3)

Advanced Computer Networks (IT365) course project.
Team: Aditi Pandey (231IT003), Ayushi Bajaj (231IT013), Sakshi (231IT057)

A configurable multi-objective MAC scheduler for 5G NR. It scores each active UE
using channel quality, fairness, delay urgency and QoS priority, with weights
tuned through ns-3 simulations. It is compared against Round Robin and
Proportional Fair.

## Pinned versions

| Component | Version |
|---|---|
| ns-3 | `<ns-3 tag, e.g. ns-3.46>` |
| 5G-LENA (nr) | `<nr tag>` |

Do not change these mid-project. Scheduler internals differ between releases.

## Repository layout

```
build/             # ns-3 + nr checkouts (git-ignored, created by setup)
nr-extensions/     # our scheduler source files (.h/.cc) and CMake patch
scenarios/         # our ns-3 scenario programs
scripts/           # sweep and analysis scripts
results/           # summary CSVs and plots
report/            # LaTeX report
```

## Setup

Requires Linux or WSL with `g++`, `cmake`, `python3`, `git`, `ninja-build`.

```bash
mkdir build && cd build
git clone https://gitlab.com/nsnam/ns-3-dev.git
cd ns-3-dev
git checkout <ns-3 tag>
git clone https://gitlab.com/cttc-lena/nr.git contrib/nr
cd contrib/nr && git checkout <nr tag> && cd ../..
./ns3 configure --enable-examples --enable-modules=nr -d debug
./ns3 build
./ns3 run cttc-nr-demo      # sanity check
```

Use `-d optimized` instead of `-d debug` for large simulation sweeps.

## Status

- [x] ns-3 and nr pinned and building
- [ ] Baseline scenario (RR vs PF) with metric collection
- [ ] Scheduler cloned and registered (behaves identically to the original)
- [ ] Multi-objective score implemented, corner cases checked
- [ ] Weight sweep and analysis
- [ ] Final comparison and report# acn-multiobjective
