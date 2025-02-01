---
title: "LM Studio: 比Ollama更好用的大模型部署工具" 
toc: true
date: 2025-02-01 20:25:11
tags:
- LLM
- lmstudio
- 大语言模型
categories:
- LLM
description: Ollama作为当前流行的大语言模型部署工具，但其以命令行方式运行需要搭配其他UI工具使用；并且对非N卡设备并不友好，虽然针对Intel显卡有成熟的解决方案，但是使用起来仍然复杂。而LM Studio支持多种 GPU，包括 AMD 和 Intel 的显卡，这使得即使不拥有 NVIDIA 设备的用户也能充分利用其硬件资源来运行复杂的 AI 模型。
---

[Ollama](https://ollama.com/)作为当前流行的大语言模型部署工具，但其以命令行方式运行需要搭配其他UI工具使用；并且对非N卡设备并不友好，虽然针对Intel显卡有成熟的解决方案[^1][^2]，但是使用起来仍然复杂。而[LM Studio](https://lmstudio.ai/)支持多种 GPU，包括 AMD 和 Intel 的显卡，这使得即使不拥有 NVIDIA 设备的用户也能充分利用其硬件资源来运行复杂的 AI 模型。

相比 Ollama, LM Studio 的优势如下：
- 利用 vulkan 适配多种GPU
- 自带图形化界面，上手简单
- 选项功能丰富
- 支持大模型丰富，可以运行[huggingface](https://huggingface.co/)上gguf格式的LLM模型文件
## 安装
- 访问[LM Studio 官网](https://lmstudio.ai/)，下载对应版本安装文件。
![LM Studio 官网](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/lmstudio.png)

- 双击已下载的安装包，根据提示完成安装。
## 设置
安装后主界面如下，可以根据个人喜好修改设置。后续操作都在**高级用户**模式下操作，请在软件底部选择 **Power User**
![LM Studio 主界面](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/main_ui.png)

- 确认计算机是否支持GPU， 点击 右下角**设置** 选择 **Runtimes**，如果如图所示，除了 `CPU ollama.cpp` 还有其他 Runtime（如图中的 `Vulkan ollama.cpp`）则说明当前计算机可以使用 GPU加速大语言模型推理。
![LM Studio Runtime](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/llstudio_runtime.png)
- 在模型搜索中选择喜欢的模型进行下载如图所示
![LM Studio 模型下载](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/model_download.png)
- 在模型管理中个性化设置模型
![LM Studio 模型管理](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/model_manage.png)
- 将**GPU Offload**和**CPU Thread Pool Size**拉满，如果 **GPU Offload** 则无法调用 GPU。
![LM Studio 模型设置](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/model_setting.png)

## 使用
- 在顶部选择以下载的模型加载使用
![LM Studio 模型选择](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/select_model.png)

- 选择时亦可对大模型进行设置
![LM Studio 模型设置](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/model_tmp_setting.png)
- 选择后等待顶部进度条完成即模型加载完成，加载完成后即可使用，使用时可以看到LM Studion 正在使用GPU进行推理
![LM Studio 模型使用](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/run.png)
- 使用时可以在左边设置图标修改模型设置
![LM Studio 模型设置](https://francisol-blog.oss-cn-beijing.aliyuncs.com/lmstudio-batter-than-ollama/model_tmp_setting1.png)


[^1]: [在 Intel GPU 上使用 IPEX-LLM 运行 Ollama](https://github.com/intel/ipex-llm/blob/main/docs/mddocs/Quickstart/ollama_quickstart.zh-CN.md).
[^2]: [让Ollama拥抱Intel Arc显卡：一键部署大模型工具实践](https://francisol.github.io/LLM/ollama-for-intel/).