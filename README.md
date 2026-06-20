# TorchVision macOS Builder

> 🔧 自动构建 TorchVision 官方发行版本的 macOS 平台兼容 `.whl` 安装包。
> 🔧 Automatically build official TorchVision release `.whl` packages for macOS

---

## 📦 项目简介 Project Introduction

[本项目](https://github.com/Morton-Li/TorchVision-MacOS-Builder) 通过 GitHub Actions 定期获取 [TorchVision 官方仓库](https://github.com/pytorch/vision) 的最新稳定版本，并自动构建适用于 **macOS** 的 Python wheel 安装包。

构建产物为 **多 Python 版本** 的 `.whl` 文件，便于在老款 Mac 上继续使用高版本 TorchVision。

[This project](https://github.com/Morton-Li/TorchVision-MacOS-Builder) uses GitHub Actions to periodically fetch the latest stable release from the [official TorchVision repository](https://github.com/pytorch/vision), and automatically builds Python wheel packages for **macOS**.

The output includes `.whl` files for **multiple Python versions**, allowing users to continue using newer versions of TorchVision on older Mac machines.

---

## 🛠 使用方式 How to Use

1. 从 [Releases 页面](../../releases) 下载你所需版本的 `.whl`：
   示例文件名：`torchvision-0.27.1-cp313-cp313-macosx_11_0_x86_64.whl`
2. 使用 `pip` 安装：

   ```bash
   pip install torchvision-0.27.1-cp313-cp313-macosx_11_0_x86_64.whl
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
