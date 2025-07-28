[English](#english) | [中文](#中文)

<h1 id="english">Whisper.cpp.binary Pre-compiled Binaries</h1>

This project provides pre-compiled, ready-to-use binaries for [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp). It aims to help users quickly and easily deploy and use the Whisper ASR model on various mainstream operating systems without the need to configure a complex build environment.

## Target Audience

This project is for you if you are:

*   **Developers** who want to quickly integrate Whisper's speech recognition capabilities into their applications or services without spending time on C++ environment setup and compilation.
*   **General users** who want to run a local, offline speech-to-text service on their personal computer to protect data privacy.
*   **Tech enthusiasts** interested in AI models who want to experience the power of Whisper on their own devices.

## About whisper.cpp

[whisper.cpp](https://github.com/ggerganov/whisper.cpp) is a high-performance C++ port of OpenAI's [Whisper](https://openai.com/research/whisper) model. Whisper is a powerful general-purpose Automatic Speech Recognition (ASR) model that can accurately transcribe audio from various languages into text.

The core advantages of the `whisper.cpp` project are:

*   **Pure C/C++ Implementation**: No external dependencies, making it easy to integrate and deploy.
*   **Highly Optimized**: Supports various instruction sets like Apple Silicon (Metal), AVX, AVX2, and AVX512 for optimal performance.
*   **Cross-Platform**: Runs on various platforms including Windows, macOS, Linux, Android, and iOS.
*   **Low Resource Consumption**: Optimized for memory and processor usage, allowing it to run efficiently on resource-constrained devices.

## The Advantage of Small Models: On-Device Friendly

The Whisper model comes in various sizes, such as `tiny`, `base`, `small`, `medium`, and `large`. The `whisper.cpp` project excels at running these models efficiently on CPUs.

**Small models (like `tiny` and `small`) are ideal for on-device deployment.** Their advantages include:

*   **Extremely Low Resource Usage**: They require very little memory and CPU, so they won't burden your device.
*   **Fast Response Speed**: Suitable for real-time transcription scenarios that require immediate feedback.
*   **Completely Offline**: All computations are done locally, ensuring data privacy and security.

For most personal applications and edge integration scenarios, small models strike an excellent balance between performance, speed, and resource consumption.

## Compatibility

This project automatically builds and verifies binaries for the following platforms via CI/CD:

| Operating System | Architecture | Notes |
| --- | --- | --- |
| Linux | x86_64 (amd64) | Built on the latest Ubuntu |
| Windows | x86_64 (amd64) | Built on the latest Windows |
| macOS | x86_64 (Intel) | Built on the latest macOS |
| macOS | ARM64 (Apple Silicon) | Built with Metal support for optimal GPU acceleration |

## How to Use

### 1. Download the Binaries

Go to the download page and get the `.zip` package corresponding to your OS and architecture.

**Download URL**: [https://yaklang.oss-accelerate.aliyuncs.com/whisper.cpp/](https://yaklang.oss-accelerate.aliyuncs.com/whisper.cpp/)

Please navigate to the folder with the most recent date (e.g., `20231027/`) to download. We also provide `.sha256` files for you to verify file integrity.

### 2. Download a Model

You will need a model file in `ggml` format. You can download one from [Hugging Face](https://huggingface.co/ggerganov/whisper.cpp/tree/main).

Here is an example of downloading the `tiny` model:
```bash
# Create a directory for models
mkdir models
# Download the tiny-q5 model
curl -L -o models/ggml-tiny.bin https://huggingface.co/ggerganov/whisper.cpp/resolve/main/ggml-tiny.bin
```

### 3. Run the Server

Unzip the downloaded package and use the following command to start the `whisper-server`:

```bash
# Make the binary executable (Linux / macOS)
chmod +x ./whisper-server

# Start the server, specifying the model path with the -m flag
./whisper-server -m ./models/ggml-tiny.bin
```

The server listens on port `8080` by default.

### 4. Send an Inference Request

You can use `curl` or any HTTP client to send a `multipart/form-data` request to the `/inference` endpoint for speech recognition.

```bash
curl --request POST \
  --url http://127.0.0.1:8080/inference \
  --header 'Content-Type: multipart/form-data' \
  --form 'file=@/path/to/your/audio.mp3'
```

The server will return a JSON result containing the transcribed text.

## Disclaimer

This project only provides pre-compiled binaries for `whisper.cpp` to facilitate user access. All core code and functionality come from the official [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp) repository. For source code, feature requests, or to report core issues, please visit the official project.

---

<h1 id="中文">Whisper.cpp.binary 预编译二进制文件</h1>

本项目为 [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp) 项目提供预编译的、可直接执行的二进制文件，旨在帮助用户快速、轻松地在各种主流操作系统上部署和使用 Whisper ASR 模型，无需自行配置复杂的编译环境。

## 项目受众

如果您是以下用户之一，本项目将为您带来便利：

*   **开发者**：希望将 Whisper 的语音识别能力快速集成到自己的应用或服务中，而不想花费时间在 C++ 环境的搭建和编译上。
*   **普通用户**：希望在个人电脑上运行一个本地的、离线的语音转文字服务，以保护数据隐私。
*   **技术爱好者**：对 AI 模型感兴趣，希望在自己的设备上体验 Whisper 的强大功能。

## 关于 whisper.cpp

[whisper.cpp](https://github.com/ggerganov/whisper.cpp) 是 OpenAI [Whisper](https://openai.com/research/whisper) 模型的高性能 C++ 移植版本。Whisper 是一个强大的通用自动语音识别（ASR）模型，可以准确地将各种语言的音频转录为文字。

`whisper.cpp` 项目的核心优势在于：

*   **纯 C/C++ 实现**：无任何外部依赖，易于集成和部署。
*   **极致优化**：支持 Apple Silicon (Metal)、AVX、AVX2、AVX512 等多种指令集，以实现最佳性能。
*   **跨平台**：可在 Windows、macOS、Linux、Android、iOS 等多种平台上运行。
*   **低资源消耗**：对内存和处理器占用进行了优化，使其可以在资源受限的设备上高效运行。

## 小模型的优势：本地化与设备友好

Whisper 模型提供多种尺寸，如 `tiny`、`base`、`small`、`medium`、`large`。`whisper.cpp` 项目尤其擅长在 CPU 上高效运行这些模型。

**小模型（如 `tiny` 和 `small`）是本地设备部署的理想选择**。它们的优势在于：

*   **极低的资源占用**：运行时仅需很少的内存和 CPU，不会对您的设备造成负担。
*   **快速的响应速度**：适合需要即时反馈的实时转录场景。
*   **完全离线**：所有计算都在本地完成，确保了数据隐私和安全。

对于大多数个人应用和端侧集成场景，小模型在性能、速度和资源消耗之间取得了绝佳的平衡。

## 兼容性

本项目通过 CI/CD 自动构建并验证了以下平台的二进制文件：

| 操作系统 | 架构 | 说明 |
| --- | --- | --- |
| Linux | x86_64 (amd64) | 在 Ubuntu 最新版上构建 |
| Windows | x86_64 (amd64) | 在 Windows 最新版上构建 |
| macOS | x86_64 (Intel) | 在 macOS 最新版上构建 |
| macOS | ARM64 (Apple Silicon) | 启用 Metal 支持以获得最佳 GPU 加速性能 |

## 如何使用

### 1. 下载文件

前往下载页面，根据您的操作系统和架构下载对应的 `.zip` 压缩包。

**下载地址**: [https://yaklang.oss-accelerate.aliyuncs.com/whisper.cpp/](https://yaklang.oss-accelerate.aliyuncs.com/whisper.cpp/)

请进入最新日期的文件夹（例如 `20231027/`）进行下载。我们同时提供了 `.sha256` 文件供您校验文件完整性。

### 2. 下载模型

您需要一个 `ggml` 格式的模型文件。您可以从 [Hugging Face](https://huggingface.co/ggerganov/whisper.cpp/tree/main) 上下载。

以下是一个 `tiny` 模型的下载示例：
```bash
# 创建一个用于存放模型的文件夹
mkdir models
# 下载 tiny-q5 模型
curl -L -o models/ggml-tiny.bin https://huggingface.co/ggerganov/whisper.cpp/resolve/main/ggml-tiny.bin
```

### 3. 运行服务

解压下载的压缩包，并使用以下命令启动 `whisper-server` 服务：

```bash
# 赋予可执行权限 (Linux / macOS)
chmod +x ./whisper-server

# 启动服务，-m 参数指定模型路径
./whisper-server -m ./models/ggml-tiny.bin
```

服务默认在 `8080` 端口上监听。

### 4. 发送识别请求

您可以使用 `curl` 或任何 HTTP 客户端向 `/inference` 端点发送一个 `multipart/form-data` 请求来进行语音识别。

```bash
curl --request POST \
  --url http://127.0.0.1:8080/inference \
  --header 'Content-Type: multipart/form-data' \
  --form 'file=@/path/to/your/audio.mp3'
```

服务器将返回一个包含识别文本的 JSON 结果。

## 免责声明

本项目仅提供 `whisper.cpp` 的预编译二进制文件，以方便用户使用。所有核心代码和功能均来自 [ggerganov/whisper.cpp](https://github.com/ggerganov/whisper.cpp) 官方仓库。如需查看源码、提出功能建议或报告核心问题，请访问官方项目。 