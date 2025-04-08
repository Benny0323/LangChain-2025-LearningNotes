# 📖 Nethan's LangChain 学习笔记 2025.04

## 📚 学习笔记大纲

### 1. 简单的 QA 机器人
1. [invoke、stream 输出](1-SimpleQARobot/1-simple_demo.ipynb)
2. [Messages 类的封装使用](1-SimpleQARobot/2-messages.ipynb)

### 2. 有记忆的 QA 机器人
1. [配置前后文记忆 thread_id](./2-QARobotWithMemory/1-memory_demo.ipynb)
2. [PromptTemplate 的定义与使用](./2-QARobotWithMemory/2-templates.ipynb)
3. [结构化输出的配置与使用](./2-QARobotWithMemory/3-JSON_parser.ipynb)

### 3. 工具类的定义与集成
1. [@tool 工具注解的介绍与定义](./3-RobotWithTools/1-introduction.ipynb)
2. [LLM 如何调取工具并返回结果？](./3-RobotWithTools/2-tools_calling.ipynb)
3. [中间件 Artifacts 的获取](./3-RobotWithTools/3-tools_and_artifacts.ipynb)

### 4. 文件上传与多模态
1. [图片和文本之间的多模态输入](./4-Multimodality/1-introduction.ipynb)
2. [向量嵌入以及语义相关性](./4-Multimodality/2-embedding.ipynb)
3. [向量存储和简单的 RAG](./4-Multimodality/3-vectorstore.ipynb)
4. [文档 Loader 和 Text Splitter](./4-Multimodality/4-text_splitters.ipynb)

### 5. AI Agent 的构建
1. [LangChain 链的表达](./5-Agent/1-LCEL_usage.ipynb)


## To be accomplished...

## 什么是 LangChain？
LangChain 是一个用于构建基于 LLM 应用的 开发框架。它的核心目标是：

> 让语言模型不仅能生成文字，还能理解上下文、调用工具、访问知识库、与外部世界交互。

因此，它并不是一个模型，而是一个模型驱动的应用开发框架，帮你组织 LLM 的输入输出、记忆、工具调用等。RAG、多 agents 都需要使用到 LangChain 或者相关技术。

## ❓为什么要创建这个仓库
LangChain 库有几个已知的缺点：
* LangChain 更新频繁，且包管理混乱。一两年前的教程使用的包和方法现在都已经标记为 Deprecated，因此会有很多 Warnings 产生。
为了解决这个问题，我目前使用的版本为 2025.4，并基于官方文档来进行构建；
* 目前 LangChain 抽象十分复杂，一个方法有若干种实现形式。所以该笔记尝试统一写法，将所有的方法调用统一的接口，并尝试将其封装并可复用。
* 在工作中也会使用到 LangChain，有一个学习文档供参考可以省去很多搜索时间。

## 💻 如何运行笔记的代码
会用到 `jupyter notebook` 文件，穿插 `markdown` 格式的表述。把常用的功能实现，并且把官方链接附在上方以供查阅。

使用的时候只需要确保一下自己的 Python 库，大体上会用到以下库（可能会有疏忽）：

```shell
pip install python-dotenv
pip install langchain==0.3.23
pip install langgraph==0.3.25
pip install langchain-openai==0.3.12
```

## 🤔 如何启动
首先在当前目录创建一个 `.env` 文件，内容为 `OPENAI_API_KEY=sk-******`，即 OpenAI 的 API Key。
因此本笔记也是基于 OpenAI 的若干模型进行学习，常用的为 `gpt-4o-2024-11-20`。

```shell
$ touch .env
$ vim .env
# PRESS i
# ----- INSERT API KEY HERE -----
OPENAI_API_KEY=sk-******
# PRESS ESC -> :wq -> PRESS ENTER
```

后面如果需要用到 LangSmith，可以继续配置：
```text
LANGSMITH_TRACING=true
LANGSMITH_TRACING=******
```

在做网络爬虫和识别的时候，我们会用到比如 SerpAPI 这样的 Google API：
```text
SERPAPI_API_KEY=******
```