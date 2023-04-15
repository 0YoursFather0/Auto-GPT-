# Auto-GPT中文版: 全自动 GPT-4 实验

![GitHub Repo stars](https://img.shields.io/github/stars/Torantulino/auto-gpt?style=social)
[![Twitter Follow](https://img.shields.io/twitter/follow/siggravitas?style=social)](https://twitter.com/SigGravitas)
[![Discord Follow](https://dcbadge.vercel.app/api/server/autogpt?style=flat)](https://discord.gg/autogpt)
[![Unit Tests](https://github.com/Torantulino/Auto-GPT/actions/workflows/ci.yml/badge.svg)](https://github.com/Torantulino/Auto-GPT/actions/workflows/ci.yml)

Auto-GPT 是一个实验性开源应用程序，展示了 GPT-4 语言模型的功能。该程序由 GPT-4 驱动，将 LLM 的“思想”链接在一起，以自主实现您设定的任何目标。作为 GPT-4 完全自主运行的首批示例之一，Auto-GPT 突破了 AI 的可能性界限。

### Demo (30/03/2023):

https://user-images.githubusercontent.com/22963551/228855501-2f5777cf-755b-4407-a643-c7299e5b6419.mp4

<h2 align="center"> 💖 Help Fund Auto-GPT's Development 💖</h2>


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

## 🔧 Usage

1. Run the `autogpt` Python module in your terminal:
   _(Type this into your CMD window)_

```
python -m autogpt
```

2. After each of action, enter 'y' to authorise command, 'y -N' to run N continuous commands, 'n' to exit program, or enter additional feedback for the AI.


### Logs

You will find activity and error logs in the folder `./output/logs`

To output debug logs:

```
python -m autogpt --debug
```

### Docker

You can also build this into a docker image and run it:

```
docker build -t autogpt .
docker run -it --env-file=./.env -v $PWD/auto_gpt_workspace:/app/auto_gpt_workspace autogpt
```

You can pass extra arguments, for instance, running with `--gpt3only` and `--continuous` mode:
```
docker run -it --env-file=./.env -v $PWD/auto_gpt_workspace:/app/auto_gpt_workspace autogpt --gpt3only --continuous
```
### Command Line Arguments
Here are some common arguments you can use when running Auto-GPT:
> Replace anything in angled brackets (<>) to a value you want to specify
* `python scripts/main.py --help` to see a list of all available command line arguments.
* `python scripts/main.py --ai-settings <filename>` to run Auto-GPT with a different AI Settings file.
* `python scripts/main.py --use-memory  <memory-backend>` to specify one of 3 memory backends: `local`, `redis`, `pinecone` or 'no_memory'.

> **NOTE**: There are shorthands for some of these flags, for example `-m` for `--use-memory`. Use `python scripts/main.py --help` for more information

## 🗣️ Speech Mode

Use this to use TTS for Auto-GPT

```
python -m autogpt --speak
```

## 🔍 Google API Keys Configuration

This section is optional, use the official google api if you are having issues with error 429 when running a google search.
To use the `google_official_search` command, you need to set up your Google API keys in your environment variables.

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. If you don't already have an account, create one and log in.
3. Create a new project by clicking on the "Select a Project" dropdown at the top of the page and clicking "New Project". Give it a name and click "Create".
4. Go to the [APIs & Services Dashboard](https://console.cloud.google.com/apis/dashboard) and click "Enable APIs and Services". Search for "Custom Search API" and click on it, then click "Enable".
5. Go to the [Credentials](https://console.cloud.google.com/apis/credentials) page and click "Create Credentials". Choose "API Key".
6. Copy the API key and set it as an environment variable named `GOOGLE_API_KEY` on your machine. See setting up environment variables below.
7. [Enable](https://console.developers.google.com/apis/api/customsearch.googleapis.com) the Custom Search API on your project. (Might need to wait few minutes to propagate)
8. Go to the [Custom Search Engine](https://cse.google.com/cse/all) page and click "Add".
9. Set up your search engine by following the prompts. You can choose to search the entire web or specific sites.
10. Once you've created your search engine, click on "Control Panel" and then "Basics". Copy the "Search engine ID" and set it as an environment variable named `CUSTOM_SEARCH_ENGINE_ID` on your machine. See setting up environment variables below.

_Remember that your free daily custom search quota allows only up to 100 searches. To increase this limit, you need to assign a billing account to the project to profit from up to 10K daily searches._

### Setting up environment variables

For Windows Users:

```
setx GOOGLE_API_KEY "YOUR_GOOGLE_API_KEY"
setx CUSTOM_SEARCH_ENGINE_ID "YOUR_CUSTOM_SEARCH_ENGINE_ID"

```

For macOS and Linux users:

```
export GOOGLE_API_KEY="YOUR_GOOGLE_API_KEY"
export CUSTOM_SEARCH_ENGINE_ID="YOUR_CUSTOM_SEARCH_ENGINE_ID"

```

## Redis Setup

Install docker desktop.

Run:

```
docker run -d --name redis-stack-server -p 6379:6379 redis/redis-stack-server:latest
```

See https://hub.docker.com/r/redis/redis-stack-server for setting a password and additional configuration.

Set the following environment variables:

```
MEMORY_BACKEND=redis
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=
```

Note that this is not intended to be run facing the internet and is not secure, do not expose redis to the internet without a password or at all really.

You can optionally set

```
WIPE_REDIS_ON_START=False
```

To persist memory stored in Redis.

You can specify the memory index for redis using the following:

```
MEMORY_INDEX=whatever
```

## 🌲 Pinecone API Key Setup

Pinecone enables the storage of vast amounts of vector-based memory, allowing for only relevant memories to be loaded for the agent at any given time.

1. Go to [pinecone](https://app.pinecone.io/) and make an account if you don't already have one.
2. Choose the `Starter` plan to avoid being charged.
3. Find your API key and region under the default project in the left sidebar.

### Setting up environment variables

In the `.env` file set:
- `PINECONE_API_KEY`
- `PINECONE_ENV` (something like: us-east4-gcp)
- `MEMORY_BACKEND=pinecone`

Alternatively, you can set them from the command line (advanced):

For Windows Users:

```
setx PINECONE_API_KEY "YOUR_PINECONE_API_KEY"
setx PINECONE_ENV "Your pinecone region" # something like: us-east4-gcp
setx MEMORY_BACKEND "pinecone"
```

For macOS and Linux users:

```
export PINECONE_API_KEY="YOUR_PINECONE_API_KEY"
export PINECONE_ENV="Your pinecone region" # something like: us-east4-gcp
export MEMORY_BACKEND="pinecone"
```

## Setting Your Cache Type

By default Auto-GPT is going to use LocalCache instead of redis or Pinecone.

To switch to either, change the `MEMORY_BACKEND` env variable to the value that you want:

`local` (default) uses a local JSON cache file
`pinecone` uses the Pinecone.io account you configured in your ENV settings
`redis` will use the redis cache that you configured

## View Memory Usage

1. View memory usage by using the `--debug` flag :)


## 🧠 Memory pre-seeding

```
# python scripts/data_ingestion.py -h 
usage: data_ingestion.py [-h] (--file FILE | --dir DIR) [--init] [--overlap OVERLAP] [--max_length MAX_LENGTH]

Ingest a file or a directory with multiple files into memory. Make sure to set your .env before running this script.

options:
  -h, --help               show this help message and exit
  --file FILE              The file to ingest.
  --dir DIR                The directory containing the files to ingest.
  --init                   Init the memory and wipe its content (default: False)
  --overlap OVERLAP        The overlap size between chunks when ingesting files (default: 200)
  --max_length MAX_LENGTH  The max_length of each chunk when ingesting files (default: 4000

# python scripts/data_ingestion.py --dir seed_data --init --overlap 200 --max_length 1000
```

This script located at scripts/data_ingestion.py, allows you to ingest files into memory and pre-seed it before running Auto-GPT. 

Memory pre-seeding is a technique that involves ingesting relevant documents or data into the AI's memory so that it can use this information to generate more informed and accurate responses.

To pre-seed the memory, the content of each document is split into chunks of a specified maximum length with a specified overlap between chunks, and then each chunk is added to the memory backend set in the .env file. When the AI is prompted to recall information, it can then access those pre-seeded memories to generate more informed and accurate responses.

This technique is particularly useful when working with large amounts of data or when there is specific information that the AI needs to be able to access quickly. 
By pre-seeding the memory, the AI can retrieve and use this information more efficiently, saving time, API call and improving the accuracy of its responses. 

You could for example download the documentation of an API, a Github repository, etc. and ingest it into memory before running Auto-GPT. 

⚠️ If you use Redis as your memory, make sure to run Auto-GPT with the WIPE_REDIS_ON_START set to False in your .env file.

⚠️For other memory backend, we currently forcefully wipe the memory when starting Auto-GPT. To ingest data with those memory backend, you can call the data_ingestion.py script anytime during an Auto-GPT run. 

Memories will be available to the AI immediately as they are ingested, even if ingested while Auto-GPT is running.

In the example above, the script initializes the memory, ingests all files within the seed_data directory into memory with an overlap between chunks of 200 and a maximum length of each chunk of 4000.
Note that you can also use the --file argument to ingest a single file into memory and that the script will only ingest files within the auto_gpt_workspace directory.

You can adjust the max_length and overlap parameters to fine-tune the way the docuents are presented to the AI when it "recall" that memory:

- Adjusting the overlap value allows the AI to access more contextual information from each chunk when recalling information, but will result in more chunks being created and therefore increase memory backend usage and OpenAI API requests.
- Reducing the max_length value will create more chunks, which can save prompt tokens by allowing for more message history in the context, but will also increase the number of chunks.
- Increasing the max_length value will provide the AI with more contextual information from each chunk, reducing the number of chunks created and saving on OpenAI API requests. However, this may also use more prompt tokens and decrease the overall context available to the AI.

## 💀 Continuous Mode ⚠️

Run the AI **without** user authorisation, 100% automated.
Continuous mode is not recommended.
It is potentially dangerous and may cause your AI to run forever or carry out actions you would not usually authorise.
Use at your own risk.

1. Run the `autogpt` python module in your terminal:

```
python -m autogpt --speak --continuous

```

2. To exit the program, press Ctrl + C

## GPT3.5 ONLY Mode

If you don't have access to the GPT4 api, this mode will allow you to use Auto-GPT!

```
python -m autogpt --speak --gpt3only
```

It is recommended to use a virtual machine for tasks that require high security measures to prevent any potential harm to the main computer's system and data.

## 🖼 Image Generation

By default, Auto-GPT uses DALL-e for image generation. To use Stable Diffusion, a [HuggingFace API Token](https://huggingface.co/settings/tokens) is required.

Once you have a token, set these variables in your `.env`:

```
IMAGE_PROVIDER=sd
HUGGINGFACE_API_TOKEN="YOUR_HUGGINGFACE_API_TOKEN"
```

## ⚠️ Limitations

This experiment aims to showcase the potential of GPT-4 but comes with some limitations:

1. Not a polished application or product, just an experiment
2. May not perform well in complex, real-world business scenarios. In fact, if it actually does, please share your results!
3. Quite expensive to run, so set and monitor your API key limits with OpenAI!

## 🛡 Disclaimer

Disclaimer
This project, Auto-GPT, is an experimental application and is provided "as-is" without any warranty, express or implied. By using this software, you agree to assume all risks associated with its use, including but not limited to data loss, system failure, or any other issues that may arise.

The developers and contributors of this project do not accept any responsibility or liability for any losses, damages, or other consequences that may occur as a result of using this software. You are solely responsible for any decisions and actions taken based on the information provided by Auto-GPT.

**Please note that the use of the GPT-4 language model can be expensive due to its token usage.** By utilizing this project, you acknowledge that you are responsible for monitoring and managing your own token usage and the associated costs. It is highly recommended to check your OpenAI API usage regularly and set up any necessary limits or alerts to prevent unexpected charges.

As an autonomous experiment, Auto-GPT may generate content or take actions that are not in line with real-world business practices or legal requirements. It is your responsibility to ensure that any actions or decisions made based on the output of this software comply with all applicable laws, regulations, and ethical standards. The developers and contributors of this project shall not be held responsible for any consequences arising from the use of this software.

By using Auto-GPT, you agree to indemnify, defend, and hold harmless the developers, contributors, and any affiliated parties from and against any and all claims, damages, losses, liabilities, costs, and expenses (including reasonable attorneys' fees) arising from your use of this software or your violation of these terms.

## 🐦 Connect with Us on Twitter

Stay up-to-date with the latest news, updates, and insights about Auto-GPT by following our Twitter accounts. Engage with the developer and the AI's own account for interesting discussions, project updates, and more.

- **Developer**: Follow [@siggravitas](https://twitter.com/siggravitas) for insights into the development process, project updates, and related topics from the creator of Entrepreneur-GPT.
- **Entrepreneur-GPT**: Join the conversation with the AI itself by following [@En_GPT](https://twitter.com/En_GPT). Share your experiences, discuss the AI's outputs, and engage with the growing community of users.

We look forward to connecting with you and hearing your thoughts, ideas, and experiences with Auto-GPT. Join us on Twitter and let's explore the future of AI together!

<p align="center">
  <a href="https://star-history.com/#Torantulino/auto-gpt&Date">
    <img src="https://api.star-history.com/svg?repos=Torantulino/auto-gpt&type=Date" alt="Star History Chart">
  </a>
</p>

## Run tests

To run tests, run the following command:

```
python -m unittest discover tests
```

To run tests and see coverage, run the following command:

```
coverage run -m unittest discover tests
```

## Run linter

This project uses [flake8](https://flake8.pycqa.org/en/latest/) for linting. We currently use the following rules: `E303,W293,W291,W292,E305,E231,E302`. See the [flake8 rules](https://www.flake8rules.com/) for more information.

To run the linter, run the following command:

```
flake8 autogpt/ tests/

# Or, if you want to run flake8 with the same configuration as the CI:
flake8 autogpt/ tests/ --select E303,W293,W291,W292,E305,E231,E302
```
