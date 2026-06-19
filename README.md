# llama.cpp CUDA Builds

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Build Status](https://github.com/ahizap/llama.cpp-cuda/actions/workflows/build-cuda.yml/badge.svg)](https://github.com/ahizap/llama.cpp-cuda/actions/workflows/build-cuda.yml)
[![Upstream](https://img.shields.io/badge/upstream-llama.cpp-green)](https://github.com/ggml-org/llama.cpp)

**High-performance, pre-built CUDA binaries for [llama.cpp](https://github.com/ggml-org/llama.cpp).**

Stop wasting time compiling from source. Get optimized binaries for your NVIDIA GPU, including support for the latest architectures like **Blackwell (B200/GB200)** and **Hopper (H100)**.

---

## 🚀 Quick Start

Get up and running in seconds:

1. **Download**: Go to the [Releases](../../releases) page and download the tarball for your CPU architecture (`-amd64` for x86_64, `-arm64` for aarch64).
2. **Extract**:
   ```bash
   tar -xzf llama.cpp-bXXXX-cuda-12.8-amd64.tar.gz
   cd cuda-12.8
   ```
3. **Run**:
   ```bash
   ./llama-cli -m /path/to/your/model.gguf -p "Hello, how are you?" -n 128 --n-gpu-layers 33
   ```

---

## 🛠 Supported Configurations

We provide binaries for a wide range of NVIDIA GPUs to ensure maximum compatibility and performance.

### GPU Architectures
| Compute Capability | GPU Examples |
| :--- | :--- |
| **12.0** | RTX Pro series, RTX 5000 series |
| **10.0** | Blackwell B200, GB200 |
| **9.0** | Hopper H100, H200, GH200 |
| **8.9** | Ada Lovelace RTX 4000 series, L4, L40 |
| **8.6** | Ampere RTX 3000 series |
| **8.0** | Ampere A100 |
| **7.5** | Turing RTX 2000 series, T4, Quadro RTX |
| **7.0** | Volta V100 |
| **6.1** | Pascal Titan XP, Tesla P40, GTX 10xx |

### CUDA & CPU Support
- **CUDA Versions**: 12.8, 13.0
- **Host Architectures**: 
  - `amd64` (x86_64): Most desktops, servers, and cloud VMs.
  - `arm64` (aarch64): Grace Hopper, Grace Blackwell, DGX Spark, Ampere Altra.

---

## 📖 Detailed Usage

### Choosing the Right Binary
When downloading from the releases page, look for the filename: `llama.cpp-bXXXX-cuda-<version>-<arch>.tar.gz`

- **`<version>`**: Choose based on your installed CUDA toolkit and driver. 
  - *Recommendation*: Use **CUDA 12.8+** for Blackwell GPUs.
- **`<arch>`**: 
  - `amd64` $\rightarrow$ Intel/AMD 64-bit.
  - `arm64` $\rightarrow$ ARM 64-bit.

### Essential Binaries Included
| Binary | Purpose |
| :--- | :--- |
| `llama-cli` | Main CLI for inference |
| `llama-server` | High-performance HTTP API server |
| `llama-quantize` | Quantize models to lower precision |
| `llama-bench` | Benchmark GPU performance |
| `llama-embedding` | Generate text embeddings |

---

## 💻 System Requirements

- **Operating System**: Linux (Ubuntu 24.04 compatible).
- **GPU**: NVIDIA GPU with Compute Capability 6.1+.
- **Drivers**: 
  - For CUDA 12.8+: Driver $\ge$ 570.15.
  - Ensure your NVIDIA driver is compatible with the CUDA version you download.

---

## ⚙️ How it Works (Build Process)

This repository automates the heavy lifting of building `llama.cpp` with CUDA support.

- **Automatic Tracking**: The CI checks for new `llama.cpp` releases daily.
- **Exact Versions**: We clone the exact release commit from upstream for stability.
- **Containerized Builds**: All binaries are built using official CUDA Docker images to ensure a clean, reproducible environment.
- **Multi-Arch**: We build across a matrix of CUDA versions and GPU architectures to provide the best possible performance for your specific hardware.

---

## 🤝 Contributing & Support

### Need Help?
- **Binary or Build Issues**: Open an issue in [this repository](https://github.com/ahizap/llama.cpp-cuda/issues).
- **`llama.cpp` Feature/Bug**: Open an issue in the [upstream repository](https://github.com/ggml-org/llama.cpp/issues).

### Custom Builds
Want to customize the architectures or CUDA versions?
1. Clone this repo.
2. Modify `.github/workflows/build-cuda.yml`.
3. Trigger a manual workflow run in GitHub Actions.

---

## 📜 License

The build scripts in this repository are licensed under the **MIT License**. 
The `llama.cpp` binaries themselves are subject to the [llama.cpp MIT License](https://github.com/ggml-org/llama.cpp/blob/master/LICENSE).

**Maintained with ❤️ by [ahizap](https://github.com/ahizap)**
