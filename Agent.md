## LLM 
~~~
大语言模型
~~~

## Context
~~~
上下文
~~~

## Prompt
~~~
Prompt (for LLM)：提示词
~~~

## Memory
## Function Calling
~~~
1. Function Calling 指的是 AI 模型根据上下文自动执行函数的机制。
2. Function Calling 充当了 AI 模型与外部系统之间的桥梁，不同的模型有不同的 Function Calling 实现，代码集成的方式也不一样。
3. Function Calling 的缺点在于处理不好多轮对话和复杂需求，适合边界清晰、描述明确的任务。
~~~

## Agent
~~~
1. AI Agent 是一个智能系统，它可以自主运行以实现特定目标。
~~~

## RAG 
~~~
1. RAG: 检索增强生成(Retrieval Augmented Generation)
2. RAG = 检索技术 + LLM 提示
3. 向 LLM 提问一个问题, RAG 从各种数据源检索相关的信息, 并将检索到的信息和问题注入到提示词模板中, LLM 最后给出答案。
4. RAG应用流程主要包含两个阶段：
    - 数据准备阶段：数据提取——>文本分割——>向量化（embedding）——>数据入库
    - 应用阶段：用户提问——>数据检索（召回）——>注入Prompt——>LLM生成答案

~~~

## MCP
~~~
1. MCP（Model Context Protocol）
2. MCP 是一个标准协议，就像给 AI 大模型装了一个 “万能接口”，让 AI 模型能够与不同的数据源和工具进行无缝交互。
3. MCP 提供了一种标准化的方法，将 AI 模型连接到各种数据源和工具。
4. MCP 是由 Anthropic (Claude) 主导发布的一个开放的、通用的、有共识的协议标准。
5. MCP 遵循客户端 - 服务器架构。

┌─────────────────────────────────────────────────────────┐
│                        Host                             │
│              (Claude Desktop / Cursor)                  │
│                                                         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │
│  │   Client    │  │   Client    │  │   Client    │      │
│  │  (GitHub)   │  │ (Postgres)  │  │  (Sentry)   │      │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘      │
└─────────┼────────────────┼────────────────┼─────────────┘
          │                │                │
          ▼                ▼                ▼
     ┌───────────┐    ┌───────────┐    ┌───────────┐
     │MCP Server │    │MCP Server │    │MCP Server │
     │ (GitHub)  │    │(Postgres) │    │ (Sentry)  │
     └───────────┘    └───────────┘    └───────────┘
~~~

## Skills
~~~
1. Skills (for Agent) 是完成特定任务的标准化、可复用流程（固定流程做事的操作说明书）
2. 渐进式加载

3.my-skill/
    ├── SKILL.md      # 必需：指令 + 元数据
    ├── scripts/      # 可选：可执行代码
    ├── references/   # 可选：文档资料
    └── assets/       # 可选：模板、资源
    
~~~


## References
~~~
[1] https://zhuanlan.zhihu.com/p/26834797144
[2] https://guangzhengli.com/blog/zh/model-context-protocol
[3] https://www.runoob.com/vibe-coding/skills-agent.html
[4] https://zhuanlan.zhihu.com/p/1999489529032234726
[5] https://www.zhihu.com/tardis/zm/art/675509396
~~~

