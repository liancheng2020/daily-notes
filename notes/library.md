#### 0925

- agent = llm + tools + context = model + harness
- harness（运行和治理层） = 上下文管理 + 工具接口 + 约束 + 验证 + 纠错

- RAG（检索增强生成）：检索器负责从知识库里找出相关片段，生成器（通常是 LLM）拿到这些片段作为上下文来生成答案

#### 0926

- tool calling: 工具调用
- function calling: 函数调用

#### 0927

- MCP: resource-提供可读取资料，prompt-提供可复用任务模板，tool-执行带参数操作并返回结果
