---
title: 让Ollama拥抱Intel Arc显卡：一键部署大模型工具实践
toc: true
date: 2025-01-31 22:58:58
tags:
- LLM
- 大语言模型
- 开源
- Rust
- Deepseek
- 英特尔
- Ollama
categories:
- LLM
description: 随着 AI 技术的飞速发展，大语言模型（LLM）如 Deepseek、GPT-4、Claude 等正逐渐改变我们的工作和生活方式。这些模型的强大能力依赖于高性能计算资源，尤其是 GPU 加速的支持。然而，在 Intel 平台上运行这些模型可能面临一些挑战。
---
随着AI技术的飞速发展，大语言模型（LLM）如 Deepseek、GPT-4、Claude等正逐渐改变我们的工作和生活方式。开源社区也涌现出许多优秀的工具和框架。其中，Ollama 作为一款轻量级且易于部署的大语言模型（LLM）服务工具，因其出色的性能和灵活性而备受关注。

然而，在实际使用过程中，我们发现 Ollama 的官方支持主要集中在 NVIDIA GPU 和 CPU 上，对于 Intel 的集成显卡（Intel(R) Arc）并未提供直接的支持。尽管 Intel 官方提供了相关工具和技术支持，但操作流程较为复杂。

针对这一问题，[olltel](https://github.com/francisol/ollatel/)被开发出来，旨在简化在 Intel GPU 上运行 Ollama 的过程。通过封装和优化 Intel 提供的官方工具链，我们的工具能够帮助用户更轻松地在 Intel(R) Arc 架构上部署和运行 Ollama 服务。


## 工具简介
olltel 封装了Intel官方提供的AI推理工具包，并将其与Ollama服务相结合。通过图形化界面，用户可以轻松完成从环境配置到模型部署的整个流程。目前该工具仅支持多种Intel Arc显卡架构（不包括B系列）。
## 安装
### 驱动更新
请确保你的 GPU 驱动程序版本不低于 31.0.101.5522。 如果版本较低，从 [Intel 官方下载页面](https://www.intel.com/content/www/us/en/download/785597/intel-arc-iris-xe-graphics-windows.html) 下载并安装最新的 GPU 驱动程序，否则可能会遇到输出乱码的问题。
### 工具安装
- 请从 [Release页](https://github.com/francisol/ollatel/releases) 查找下载文件，或点此直接下载 [zip包](https://github.com/francisol/ollatel/releases/download/v0.1.0/windows_amd64.zip)、[exe 安装包](https://github.com/francisol/ollatel/releases/download/v0.1.0/Ollama.for.Intel_0.1.0_x64-setup.exe)、[msi 安装包](https://github.com/francisol/ollatel/releases/download/v0.1.0/Ollama.for.Intel_0.1.0_x64_zh-CN.msi)。
- 双击安装文件根据指引安装软件。
## 使用
初次使用需要初始化环境，该步骤可能需要代理
![初始化环境](https://francisol-blog.oss-cn-beijing.aliyuncs.com/ollama-for-intel/init.png)

环境设置成功后跳转到Ollama 控制页面，可以在此处启动或关闭Ollama服务。如需使用 `ollama` 命令请点击 **打开CMD**或**打开powershell** 按钮。在命令行中使用。
![Ollama控制](https://francisol-blog.oss-cn-beijing.aliyuncs.com/ollama-for-intel/ollama.png)

### 后续
可以根据个人喜好搭配其他大语言模型前端工具，例如：[Lobe Chat](https://chat-preview.lobehub.com/)、[AnythingLLM](https://anythingllm.com/)、[Chatbox AI](https://chatboxai.app/zh)、[Open WebUI](https://docs.openwebui.com/)。
可参考：[五个优秀的免费 Ollama WebUI 客户端推荐](https://lobehub.com/zh/blog/5-ollama-web-ui-recommendation)。
## 意见反馈
如有问题，欢迎提交[Issues](https://github.com/francisol/ollatel/issues)。


---
参考资料：[在 Intel GPU 上使用 IPEX-LLM 运行 Ollama](https://github.com/intel/ipex-llm/blob/main/docs/mddocs/Quickstart/ollama_quickstart.zh-CN.md)


