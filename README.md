# MemoFlux ADVX（AdventureX 2025）参赛项目
**低成本高回报碎片化信息备忘录**

*该仓库为主仓库，在您git clone**主仓库**之后您需要执行额外的命令。*

```
git clone https://github.com/TokiyaSzk/MemoFlux.git
cd MemoFlux
git submodule update --init --recursive
```

*主仓库并不会自动更新子模块的提交，更新引用可以执行额外命令*

```
cd MemoFluxServer
git pull origin main
cd ..
cd MemoFluxIOS
git pull origin main
git add . 
git commit -m "Update server & client submodule to latest version"
git push
```

## ReMake 重新发明
从最早的信件传递到电报、电话，再到互联⽹的崛起，⼈类⼀次次通过技术迭代重塑世界。⽽今天，
我们正处于⼀个更快速变⾰的时代⸺⼈⼯智能、区块链、XR 交互、低代码开发等新兴技术正在重
构过去的系统，让我们有机会重新构想熟悉的⼀切。
「ReMake 重新创造」赛道邀请你站在科技前沿，打破固有框架，重新构想和创造那些曾经塑造世界
的经典技术、产品或体验。你可以借助 AI 赋能传统⾏业，让经典技术焕发新⽣；也可以⽤区块链颠
覆信息存储⽅式，挑战数据安全的新可能；甚⾄可以重新定义互联⽹交互，探索更具沉浸感的数字体
验.
## 赛道
- Paraflow 没有设计师
- Kimi For Vibe Coding
- 让AI真正进入生活，生活中的每个需求都能被开发者重做一次。

## 作品详细描述

### 背景
在信息爆炸的今天，核心挑战已不再是信息的获取，而是如何高效地整合、理解并利用这些来自不同渠道的碎片化信息。

### 功能
MemoFlux 提供了一套从采集到行动的完整闭环解决方案。用户可以通过系统级的快捷指令无缝捕捉屏幕任何内容。随后，MemoFlux 的 AI 引擎将立即进行意图识别和智能分析，自动整理并将其置入用户的个人知识网络中。
与传统列表式管理不同，MemoFlux 的核心是 “连接”。MemoFlux 是一个 “行动中枢”，它能根据信息内容智能生成任务建议，并无缝同步到系统原生的应用中，确保每一个有价值的想法都能被付诸行动。
- 🌊 无缝采集 (Seamless Capture)
- 🧠 AI 驱动的结构化 (AI-Powered Structuring)
- ⚡️ 一体化行动中枢 (Integrated Action Hub)
- 📊 深度洞察与回顾 (Deep Insights & Review)

### 目标用户画像
- 👨‍🎓 学生与研究人员
  - 痛点: 大量文献、课程笔记、网页资料分散各处，难以串联，写论文和备考时效率低下。
- 💼 知识工作者 (产品经理、顾问、律师等)
  - 痛点: 会议纪要、行业报告、客户邮件等信息繁杂，难以转化为有效的项目计划和决策依据。
- ✨ 生活达人
  - 痛点：保存过许多美食，生活体验，旅游等帖子，但是再次读取其中的有效信息很困难
  - 痛点：隐藏在社交的日常对话之中的日程信息经常性遗漏

## MemoFlux - 后端技术栈 (Backend Tech Stack)

以下是 MemoFlux 项目的核心后端技术栈，该组合经过精心设计，旨在构建一个高性能、可扩展、AI 驱动的现代化服务。

| 技术组件 (Component) | 核心描述 (Core Description) | 在 MemoFlux 项目中的作用 (Role in the MemoFlux Project) |
| :--- | :--- | :--- |
| **[Qdrant](https://qdrant.tech/)** | 一个高性能、开源的向量数据库。它专门用于存储、索引和搜索由 AI 模型生成的亿级高维向量，并提供高效的相似性搜索能力。 | **知识网络的核心引擎**。<br>- 实现“**关联发现**”功能，通过向量相似度依据tag归纳相关的笔记。 |
| **[Boundary](https://www.boundary.dev/)(BAML)** | 一个专为与大语言模型 (LLM) 交互而设计的创新语言和工具链。它能帮助开发者定义清晰的 AI 功能接口，并可靠地解析和验证 LLM 的输出。 | **AI 功能的管理层和翻译器**。<br>- 将“**意图识别**”、“**自动分类与标签**”、“**智能总结**”等 AI 任务定义为可靠的 BAML 函数。<br>- 替代繁琐的 Prompt 工程和不稳定的输出解析，确保从 LLM 返回的数据能直接用于业务逻辑。<br>- 统一管理对不同 LLM（如 GPT、Claude 等）的调用。 |
| **[FastAPI](https://fastapi.tiangolo.com/)** | 一个现代化、高性能的 Python Web 框架，用于构建 API。它以其出色的性能、易用性以及基于类型提示的自动 API 文档生成而闻名。 | **项目的后端服务骨架**。<br>- 构建所有面向客户端 (iOS/Web) 的 RESTful API 接口，如用户认证、笔记的增删改查、知识图谱数据获取等。<br>- 其原生的异步支持与 `asyncio` 完美结合，是承载高并发 AI 和数据库请求的理想选择。 |
| **[asyncio](https://docs.python.org/3/library/asyncio.html)** | Python 内置的、用于通过 `async/await` 语法编写并发代码的标准库。它使得在单线程中处理大量 I/O 密集型任务成为可能。 | **高并发处理的基石**。<br>- 允许应用在等待 LLM API 响应或数据库查询返回时，不阻塞整个线程，而去处理其他用户的请求。<br>- 确保了 MemoFlux 在与多个外部服务（Qdrant、LLM API、主数据库）交互时，依然能保持低延迟和高吞吐量。 |



