# Auto-GPT中文版: 全自动 GPT-4 实验

![GitHub Repo stars](https://img.shields.io/github/stars/Torantulino/auto-gpt?style=social)
[![Twitter Follow](https://img.shields.io/twitter/follow/siggravitas?style=social)](https://twitter.com/SigGravitas)
[![Discord Follow](https://dcbadge.vercel.app/api/server/autogpt?style=flat)](https://discord.gg/autogpt)
[![Unit Tests](https://github.com/Torantulino/Auto-GPT/actions/workflows/ci.yml/badge.svg)](https://github.com/Torantulino/Auto-GPT/actions/workflows/ci.yml)

Auto-GPT 是一个实验性开源应用程序，展示了 GPT-4 语言模型的功能。该程序由 GPT-4 驱动，将 LLM 的“思想”链接在一起，以自主实现您设定的任何目标。作为 GPT-4 完全自主运行的首批示例之一，Auto-GPT 突破了 AI 的可能性界限。

### Demo (30/03/2023):

https://user-images.githubusercontent.com/22963551/228855501-2f5777cf-755b-4407-a643-c7299e5b6419.mp4

<h2 align="center"> 💖 获取openai key 💖</h2>
[获取openai key](https://www.yishengfk.cn/links/BBDA00A8)


## Table of Contents

- [Auto-GPT：自主 GPT-4 实验](#Auto-GPT：自主 GPT-4 实验)
  - [演示 (30/03/2023)：](#demo-30032023)
  - [目录](#table-of-contents)
  - [🚀 特征](#-features)
  - [📋 要求](#-requirements)
  - [💾 安装](#-installation)
  - [🔧 用法](#-用法)
    - [日志](#logs)
  - [🗣️ 语音模式](#️-speech-mode)
  - [🔍 谷歌 API 密钥配置](#-google-api-keys-configuration)
    - [设置环境变量](#setting-up-environment-variables)
  - [设置](#redis-setup)
  - [🌲Pinecone API 密钥设置](#-pinecone-api-key-setup)
    - [设置环境变量](#setting-up-environment-variables-1)
  - [设置缓存类型](#setting-your-cache-type)
  - [查看内存使用情况](#view-memory-usage)
  - [💀 连续模式 ⚠️](#-continuous-mode-️)
  - [GPT3.5 ONLY 模式](#gpt35-only-mode)
  - [🖼 图像生成](#-image-generation)
  - [⚠️ 限制](#️-limitations)
  - [🛡 免责声明](#-disclaimer)
  - [🐦 在 Twitter 上与我们联系](#-connect-with-us-on-twitter)
  - [运行测试](#run-tests)
  - [运行 linter](#run-linter)

## 🚀 Features

🌐用于搜索和信息收集的 Internet 访问
💾长期和短期内存管理
🧠用于文本生成的 GPT-4 实例
🔗访问流行的网站和平台
🗃️使用 GPT-3.5 进行文件存储和汇总

## 📋 Requirements

- 环境（只选一个）
  - [vscode + devcontainer](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers): 已经配置在.devcontainer文件夹下，可以直接使用
  - [Python 3.8 或更高版本](https://www.tutorialspoint.com/how-to-install-python-in-windows)
- [OpenAI API key](https://platform.openai.com/account/api-keys)


Optional:

- [PINECONE API key](https://www.pinecone.io/) （如果你想要 Pinecone 支持的内存）
- ElevenLabs Key （如果你想让人工智能说话）

## 💾 Installation

To install Auto-GPT, follow these steps:

1. 要安装 Auto-GPT，请按照下列步骤操作：

确保满足上述所有要求，如果没有，请安装/获取它们。
以下命令应在 CMD、Bash 或 Powershell 窗口中执行。为此，请转到计算机上的文件夹，单击顶部的文件夹路径并键入 CMD，然后按 Enter。

2. 克隆存储库：对于此步骤，您需要安装 Git，但您可以通过单击此页面顶部的按钮来下载 zip 文件☝️

```
git clone https://github.com/Torantulino/Auto-GPT.git
```

3.  导航到项目目录：（ 将其输入您的 CMD 窗口，您的目标是将 CMD 窗口导航到您刚刚下载的存储库）

```
cd 'Auto-GPT'
```

4. 安装所需的依赖项：（ 同样，将其键入您的 CMD 窗口）

```
pip install -r requirements.txt
```

5. 重命名.env.template为.env并填写您的OPENAI_API_KEY. 如果您打算使用语音模式，请ELEVEN_LABS_API_KEY也填写您的。
从以下网址获取您的 OpenAI API 密钥： https: //platform.openai.com/account/api-keys。
从https://elevenlabs.io获取您的 ElevenLabs API 密钥。您可以使用网站上的“个人资料”选项卡查看您的 xi-api-key。
如果要在 Azure 实例上使用 GPT，请设置USE_AZURE为True然后：
重命名azure.yaml.template为并提供部分中相关模型的azure.yaml相关azure_api_base和所有部署 ID ： azure_api_versionazure_model_map
fast_llm_model_deployment_id- 您的 gpt-3.5-turbo 或 gpt-4 部署 ID
smart_llm_model_deployment_id- 你的 gpt-4 部署 ID
embedding_model_deployment_id- 您的 text-embedding-ada-002 v2 部署 ID
请将所有这些值指定为双引号字符串
详细信息可在此处找到： https: //pypi.org/project/openai/部分Microsoft Azure Endpoints和此处：https: //learn.microsoft.com/en-us/azure/cognitive-services/openai/tutorials/embeddings? tabs=嵌入模型的命令行。


## 🔧 使用方法

1. 在终端中运行 `main.py` Python 脚本：
   _（将其输入您的 CMD 窗口）_

```
蟒蛇脚本/main.py
```

2. 在每个动作之后，输入'y'授权命令，'y -N'运行N个连续命令，'n'退出程序，或者为AI输入额外的反馈。


### 日志

您将在文件夹“./output/logs”中找到活动和错误日志

输出调试日志：

```
python 脚本/main.py --debug
```

## 🗣️ 语音模式

使用它来将 TTS 用于 Auto-GPT

```
python 脚本/main.py --speak
```

## 🔍 谷歌 API 密钥配置

此部分是可选的，如果您在运行谷歌搜索时遇到错误 429 问题，请使用官方谷歌 API。
要使用 `google_official_search` 命令，您需要在环境变量中设置您的 Google API 密钥。

1. 前往[谷歌云端控制台](https://console.cloud.google.com/)。
2. 如果您还没有帐户，请创建一个并登录。
3. 通过单击页面顶部的“选择项目”下拉菜单并单击“新建项目”来创建一个新项目。给它起个名字，然后单击“创建”。
4. 转到 [API 和服务仪表板](https://console.cloud.google.com/apis/dashboard) 并单击“启用 API 和服务”。搜索“自定义搜索 API”并单击它，然后单击“启用”。
5. 转到[凭据](https://console.cloud.google.com/apis/credentials) 页面并单击“创建凭据”。选择“API 密钥”。
6. 复制 API 密钥并将其设置为您机器上名为“GOOGLE_API_KEY”的环境变量。请参阅下面的设置环境变量。
7. [启用](https://console.developers.google.com/apis/api/customsearch.googleapis.com) 您项目上的自定义搜索 API。（可能需要等待几分钟才能传播）
8. 转到[自定义搜索引擎](https://cse.google.com/cse/all) 页面并单击“添加”。
9. 按照提示设置您的搜索引擎。您可以选择搜索整个网络或特定站点。
10. 创建搜索引擎后，单击“控制面板”，然后单击“基本”。复制“搜索引擎 ID”并将其设置为您计算机上名为“CUSTOM_SEARCH_ENGINE_ID”的环境变量。请参阅下面的设置环境变量。

_请记住，您的每日免费自定义搜索配额最多只允许 100 次搜索。要增加此限制，您需要为该项目分配一个计费帐户，以从每天多达 10K 次的搜索中获利。_

###设置环境变量

对于 Windows 用户：

```
setx GOOGLE_API_KEY "YOUR_GOOGLE_API_KEY"
setx CUSTOM_SEARCH_ENGINE_ID “您的自定义搜索引擎 ID”

```

对于 macOS 和 Linux 用户：

```
导出 GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY"
export CUSTOM_SEARCH_ENGINE_ID="YOUR_CUSTOM_SEARCH_ENGINE_ID"

```

## Redis 设置

安装 docker 桌面。

跑步：

```
docker run -d --name redis-stack-server -p 6379:6379 redis/redis-stack-server:latest
```

有关设置密码和其他配置的信息，请参阅 https://hub.docker.com/r/redis/redis-stack-server。

设置以下环境变量：

```
MEMORY_BACKEND=redis
REDIS_HOST=本地主机
REDIS_PORT=6379
REDIS_PASSWORD=
```

请注意，这不是为了面向互联网运行并且不安全，不要在没有密码的情况下或根本没有将 redis 暴露在互联网上。

您可以选择设置

```
WIPE_REDIS_ON_START=假
```

持久化存储在 Redis 中的内存。

您可以使用以下命令为 redis 指定内存索引：

```
MEMORY_INDEX=随便
```

## 🌲 Pinecone API 密钥设置

Pinecone 支持存储大量基于向量的内存，允许在任何给定时间只为代理加载相关内存。

1. 前往[pinecone](https://app.pinecone.io/)，如果您还没有账号，请注册一个。
2.选择`Starter`计划，避免被收费。
3. 在左侧边栏的默认项目下找到您的 API 密钥和区域。

###设置环境变量

在 .env 文件集中：
- `PINECONE_API_KEY`
- `PINECONE_ENV`（类似于：us-east4-gcp）
- `MEMORY_BACKEND = pinecone`

或者，您可以从命令行设置它们（高级）：

对于 Windows 用户：

```
setx PINECONE_API_KEY "YOUR_PINECONE_API_KEY"
setx PINECONE_ENV “你的松果区域” # 类似于：us-east4-gcp
setx MEMORY_BACKEND “松果”
```

对于 macOS 和 Linux 用户：

```
导出 PINECONE_API_KEY="YOUR_PINECONE_API_KEY"
export PINECONE_ENV="你的松果区域" # 类似于：us-east4-gcp
导出 MEMORY_BACKEND="松果"
```

## 设置你的缓存类型

默认情况下，Auto-GPT 将使用 LocalCache 而不是 Redis 或 Pinecone。

要切换到任何一个，请将“MEMORY_BACKEND”环境变量更改为您想要的值：

`local`（默认）使用本地 JSON 缓存文件
`pinecone` 使用您在 ENV 设置中配置的 Pinecone.io 帐户
`redis` 将使用您配置的 redis 缓存

## 查看内存使用方法

1. 使用 `--debug` 标志查看内存使用方法:)

##💀连续模式⚠️

运行 AI **无需**用户授权，100% 自动化。
不推荐连续模式。
它具有潜在危险，可能会导致您的 AI 永远运行或执行您通常不会授权的操作。
使用风险自负。

1. 在终端中运行 `main.py` Python 脚本：

```
python scripts/main.py --continuous

```

2. 要退出程序，请按 Ctrl + C

## GPT3.5 仅模式

如果您无权访问 GPT4 api，此模式将允许您使用 Auto-GPT！

```
python 脚本/main.py --gpt3only
```

建议将虚拟机用于需要高度安全措施的任务，以防止对主计算机的系统和数据造成任何潜在危害。

## 🖼 图像生成

默认情况下，Auto-GPT 使用 DALL-e 进行图像生成。要使用 Stable Diffusion，需要 [HuggingFace API 令牌](https://huggingface.co/settings/tokens)。

获得令牌后，在 .env 中设置这些变量：

```
IMAGE_PROVIDER=sd
HUGGINGFACE_API_TOKEN="你的_HUGGINGFACE_API_TOKEN"
```

## ⚠️ 限制

该实验旨在展示 GPT-4 的潜力，但存在一些局限性：

1. 不是完美的应用或产品，只是一个实验
2. 在复杂的真实业务场景中可能表现不佳。事实上，如果确实如此，请分享您的结果！
3. 运行成本很高，所以使用 OpenAI 设置和监控您的 API 密钥限制！

## 🛡 免责声明

免责声明
该项目 Auto-GPT 是一个实验性应用程序，按“原样”提供，没有任何明示或暗示的保证。使用本软件，即表示您同意承担与其使用相关的所有风险，包括但不限于数据丢失、系统故障或可能出现的任何其他问题。

本项目的开发者和贡献者对因使用本软件而可能发生的任何损失、损害或其他后果不承担任何责任或义务。您对基于 Auto-GPT 提供的信息做出的任何决定和行动承担全部责任。

**请注意，使用 GPT-4 语言模型可能会因其令牌使用法而变得昂贵。**通过使用此项目，您承认您有责任监控和管理您自己的令牌使用法和相关费用。强烈建议定期检查您的 OpenAI API 使用方法并设置任何必要的限制或警报以防止意外收费。

作为一项自主实验，Auto-GPT 可能会生成不符合现实世界商业惯例或法律要求的内容或采取的行动。您有责任确保基于此软件的输出做出的任何行动或决定符合所有适用的法律、法规和道德标准。本项目的开发者和贡献者对因使用本软件而产生的任何后果不承担任何责任。

通过使用 Auto-GPT，您同意就任何和所有索赔、损害、损失、责任、成本和费用（包括合理的律师费）对开发人员、贡献者和任何关联方进行赔偿、辩护并使其免受损害因您使用本软件或您违反这些条款而引起的。

## 🐦 在 Twitter 上与我们联系

通过关注我们的 Twitter 帐户，了解有关 Auto-GPT 的最新消息、更新和见解。与开发人员和 AI 自己的帐户进行有趣的讨论、项目更新等。

- **开发者**：关注 [@siggravitas](https://twitter.com/siggravitas)，了解 Entrepreneur-GPT 的创建者的开发过程、项目更新和相关主题。
- **Entrepreneur-GPT**：通过关注 [@En_GPT](https://twitter.com/En_GPT) 加入与 AI 本身的对话。分享您的经验，讨论 AI 的输出，并与不断壮大的用户社区互动。

我们期待与您联系并聆听您对 Auto-GPT 的想法、想法和体验。加入我们的 Twitter，让我们一起探索 AI 的未来！

<p对齐=“中心”>
  <a href="https://star-history.com/#Torantulino/auto-gpt&Date">
    <img src="https://api.star-history.com/svg?repos=Torantulino/auto-gpt&type=Date" alt="星史图表">
  </a>
</p>

## 运行测试

要运行测试，请运行以下命令：

```
python -m unittest 发现测试
```

要运行测试并查看覆盖率，请运行以下命令：

```
coverage run -m unittest 发现测试
```

## 运行 linter

该项目使用 [flake8](https://flake8.pycqa.org/en/latest/) 进行 linting。我们目前使用以下规则：`E303,W293,W291,W292,E305,E231,E302`。有关详细信息，请参阅 [flake8 规则](https://www.flake8rules.com/)。

要运行 linter，请运行以下命令：

```
flake8 脚本/测试/

# 或者，如果你想使用与 CI 相同的配置运行 flake8：
flake8 脚本/测试/——选择 E303、W293、W291、W292、E305、E231、E302
```
