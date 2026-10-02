# TorchVision macOS Builder

> 🔧 通过 GitHub Actions 构建 TorchVision 官方发行版本的 macOS 平台兼容 `.whl` 安装包。
> 🔧 Build official TorchVision release `.whl` packages for macOS with GitHub Actions

---

## 📦 项目简介 Project Introduction

[本项目](https://github.com/Morton-Li/TorchVision-MacOS-Builder) 通过 GitHub Actions 每日缓存 [TorchVision 官方仓库](https://github.com/pytorch/vision) 最新稳定版本的源码，由维护者手动触发构建适用于 **macOS** 的 Python wheel 安装包。

构建产物为 **多 Python 版本** 的 `.whl` 文件，便于在老款 Mac 上继续使用高版本 TorchVision。

[This project](https://github.com/Morton-Li/TorchVision-MacOS-Builder) uses GitHub Actions to cache the source of the latest stable release from the [official TorchVision repository](https://github.com/pytorch/vision) daily. Maintainers manually trigger builds of Python wheel packages for **macOS**.

The output includes `.whl` files for **multiple Python versions**, allowing users to continue using newer versions of TorchVision on older Mac machines.

---

## 🛠 使用方式 How to Use

当前构建目标为 **TorchVision 0.29.1 + PyTorch 2.14.1**。上游 0.29 版本引入了基于 PyTorch 2.14 的 ABI 稳定性，详见[发布说明](https://github.com/pytorch/vision/releases/tag/v0.29.1)。

The current build target is **TorchVision 0.29.1 + PyTorch 2.14.1**. Upstream 0.29 introduces ABI stability starting with PyTorch 2.14.

1. 从 [Releases 页面](../../releases) 下载你所需版本的 `.whl`：
   示例文件名：`torchvision-0.29.1-cp313-cp313-macosx_11_0_x86_64.whl`
   同时从 [PyTorch macOS Builder Releases](https://github.com/Morton-Li/PyTorch-MacOS-Builder/releases/tag/v2.14.1) 下载相同 Python 版本的 PyTorch wheel。
2. 使用 `pip` 安装：

   ```bash
   pip install torch-2.14.1-cp313-cp313-macosx_11_0_x86_64.whl
   pip install torchvision-0.29.1-cp313-cp313-macosx_11_0_x86_64.whl
   ```
3. 验证是否安装成功（需确保已安装兼容的 PyTorch）：

   ```bash
   python -c "import torchvision; print(torchvision.__version__)"
   ```

---

## 💡 为什么需要这个项目 Why This Project Matters

TorchVision 是 PyTorch 图像相关功能的重要组件，但其官方安装包亦不再为 Intel 架构的 macOS 提供支持。本项目旨在填补该缺口，**延续 TorchVision 在旧款 Mac 上的使用寿命**，并确保其与非官方构建的 PyTorch 保持兼容。

TorchVision, a core library for computer vision in PyTorch, has also dropped support for Intel-based macOS in official binaries. This project fills the gap by **extending TorchVision support for Intel Macs**, ensuring continued compatibility with custom-built PyTorch packages.

---

## 🤝 鸣谢 Acknowledgements

* [PyTorch](https://github.com/pytorch/pytorch)
* [TorchVision](https://github.com/pytorch/vision)
* [GitHub Actions](https://github.com/features/actions)
