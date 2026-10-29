# TorchVision macOS Builder

> 🔧 通过 GitHub Actions 构建 TorchVision 官方发行版本的 macOS 平台兼容 `.whl` 安装包。
> 🔧 Build official TorchVision release `.whl` packages for macOS with GitHub Actions

---

## 📦 项目简介 Project Introduction

[本项目](https://github.com/Morton-Li/TorchVision-MacOS-Builder) 通过 GitHub Actions 每日缓存 [TorchVision 官方仓库](https://github.com/pytorch/vision) 最新稳定版本的源码，由维护者手动触发构建适用于 **macOS** 的 Python wheel 安装包。

构建产物为兼容 **多个 Python 版本** 的单个 `py3-none` wheel，便于在老款 Intel Mac 上继续使用高版本 TorchVision。

[This project](https://github.com/Morton-Li/TorchVision-MacOS-Builder) uses GitHub Actions to cache the source of the latest stable release from the [official TorchVision repository](https://github.com/pytorch/vision) daily. Maintainers manually trigger builds of Python wheel packages for **macOS**.

The output is a single `py3-none` wheel for **multiple Python versions**, allowing users to continue using newer versions of TorchVision on older Intel Macs.

---

## 🛠 使用方式 How to Use

当前构建目标为 **TorchVision 0.29.2 + PyTorch 2.15.0**。上游 0.29 版本引入了基于 PyTorch 2.14 的 ABI 稳定性，详见[发布说明](https://github.com/pytorch/vision/releases/tag/v0.29.2)。

The current build target is **TorchVision 0.29.2 + PyTorch 2.15.0**. Upstream 0.29 introduces ABI stability starting with PyTorch 2.14.

截至 2026-10-29，以下是 **0.29.2 的目标文件名**，本项目尚未构建或发布该版本；当前可下载版本为 0.29.1。请在新 Release 实际发布后使用示例，或按 Releases 中的真实文件名安装。

As of 2026-10-29, 0.29.2 is a build target, not a published Intel macOS wheel. The currently published version is 0.29.1; use the examples below after the new release becomes available.

1. 从 [Releases 页面](../../releases) 下载你所需版本的 `.whl`：
   示例文件名：`torchvision-0.29.2-py3-none-macosx_11_0_x86_64.whl`
   同时从 [PyTorch macOS Builder Releases](https://github.com/Morton-Li/PyTorch-MacOS-Builder/releases/tag/v2.15.0) 下载相同 Python 版本的 PyTorch wheel。
2. 使用 `pip` 安装：

   ```bash
   pip install torch-2.15.0-cp313-cp313-macosx_11_0_x86_64.whl
   pip install torchvision-0.29.2-py3-none-macosx_11_0_x86_64.whl
   ```
3. 验证是否安装成功（需确保已安装兼容的 PyTorch）：

   ```bash
   python -c "import torchvision; print(torchvision.__version__)"
   ```

---

## 🔗 构建与验证 Build and Validation

0.29.2 上游改用 `py3-none` 标签，且[源码依赖](https://github.com/pytorch/vision/blob/v0.29.2/setup.py)为 `torch>=2.14.0`。本项目使用 **Python 3.12 + PyTorch 2.15.0** 构建一次，然后在 **Python 3.11–3.14** 上安装同一个 wheel，检查版本、依赖、原生 NMS 和 JPEG 编解码；所有测试成功后，只有 `main` 上的手动运行会发布 Release。每日定时工作流只缓存源码。

Upstream 0.29.2 uses the `py3-none` tag and requires `torch>=2.14.0`. This project builds once with **Python 3.12 + PyTorch 2.15.0**, then tests that same wheel on **Python 3.11–3.14**, including native NMS and JPEG operations. Publishing requires all tests to pass and a manual run on `main`; the daily workflow only caches source.

目标为 **macOS 11.0+、x86_64**。本次修改尚未执行 macOS 构建或运行测试；最低系统版本、Python 3.15、free-threaded Python 和 MPS 运行时均未在本次验证。Python 3.15 测试需先有对应的自建 PyTorch `cp315` wheel；`py3-none` 标签本身不代表该组合已通过测试。

The target is **macOS 11.0+, x86_64**. These changes still need macOS build and runtime validation. The minimum OS version, Python 3.15, free-threaded Python and MPS have not been tested here. Testing Python 3.15 first requires a matching custom PyTorch `cp315` wheel; a `py3-none` tag alone does not establish tested compatibility.

## 💡 为什么需要这个项目 Why This Project Matters

TorchVision 是 PyTorch 图像相关功能的重要组件，但其官方安装包亦不再为 Intel 架构的 macOS 提供支持。本项目旨在填补该缺口，**延续 TorchVision 在旧款 Mac 上的使用寿命**，并确保其与非官方构建的 PyTorch 保持兼容。

TorchVision, a core library for computer vision in PyTorch, has also dropped support for Intel-based macOS in official binaries. This project fills the gap by **extending TorchVision support for Intel Macs**, ensuring continued compatibility with custom-built PyTorch packages.

---

## 🤝 鸣谢 Acknowledgements

* [PyTorch](https://github.com/pytorch/pytorch)
* [TorchVision](https://github.com/pytorch/vision)
* [GitHub Actions](https://github.com/features/actions)
