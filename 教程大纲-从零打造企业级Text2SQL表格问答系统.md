# 从零打造企业级 Text2SQL 表格问答系统：基于 LangGraph + MCP + ReActAgent 技术实现

## 📚 教程总览

**项目定位：** 一个轻量级、支持全链路的大模型数据助手应用框架

**核心技术栈：**
- **后端：** Sanic + LangChain/LangGraph + Text2SQL + MCP + Neo4j
- **前端：** Vue3 + TypeScript + Vite + Naive UI + ECharts
- **LLM：** 通义千问 / OpenAI / DeepSeek

**学习成果：**
- ✅ 掌握 LangGraph 多智能体架构设计
- ✅ 实现自然语言到 SQL 的智能转换
- ✅ 构建 MCP 多智能体协同系统
- ✅ 开发生产级全栈 AI 应用

**教程规模：**
- 总章节：20 章（分 4 个阶段）
- 预计字数：5-8 万字
- 预计代码：300-500 行（完整项目）
- 学习时长：20-30 小时

---

## 📖 章节目录

### 🟢 第一阶段：基础框架搭建（第 1-5 章）

#### 第 1 章：为什么要做 AI 数据助手？技术架构与开发环境全攻略
**副标题：** 从 Excel 到 AI 对话的革命性转变

**学习目标：**
- 理解 AI 数据助手的业务价值
- 掌握项目整体技术架构
- 使用 uv 搭建隔离开发环境

**核心内容：**
1. 什么是大模型数据助手？
   - 传统 BI 工具的痛点分析
   - AI 数据助手的价值主张
   - 典型应用场景展示

2. 为什么需要这个项目？
   - 对比其他解决方案（Dify、纯 LangChain）
   - 本项目的技术优势分析

3. 技术选型深度解析
   - **Sanic：** 为什么选择异步 Web 框架？
   - **LangGraph：** 为什么需要状态机编程？
   - **MCP：** 多智能体协议的必要性
   - **Neo4j：** 图数据库优化 SQL JOIN
   - **DuckDB：** 内存数据库处理文件查询
   - **Vue3 + TypeScript：** 现代化前端技术栈

4. 使用 uv 搭建开发环境
   - uv vs pip vs conda 对比
   - 创建虚拟环境
   - 项目目录结构规划

5. 环境准备检查清单
   - Python 3.9+
   - Node.js 18+
   - Docker Desktop
   - MySQL / Neo4j

**预计代码量：** 10-15 行（环境配置命令）

**思考题：**
- 为什么 LLM 应用需要异步框架？
- 图数据库在 Text2SQL 中的作用是什么？

---

#### 第 2 章：30 分钟上手 Sanic：你的第一个异步 Web API
**副标题：** 从 Hello World 到流式响应

**学习目标：**
- 掌握 Sanic 基础用法
- 理解异步编程原理
- 实现第一个聊天 API

**核心内容：**
1. 安装 Sanic 框架
2. 创建 serv.py 主入口
   - Sanic 应用实例化
   - 第一个路由：GET /
   - 理解 async/await 语法

3. Sanic 核心概念详解
   - 事件循环（asyncio）
   - 路由装饰器（@app.get/@app.post）
   - Request 对象结构
   - Response 响应格式

4. 添加 POST 接口
   - 接收 JSON 请求
   - 请求参数验证
   - 返回 JSON 响应

5. 使用 curl/Postman 测试

6. Sanic vs Flask/FastAPI 性能对比

**预计代码量：** 20-30 行

**完整代码汇总：** serv.py（完整版）

**思考题：**
- async def 和 def 的本质区别是什么？
- 为什么异步框架适合 IO 密集型应用？

---

#### 第 3 章：生产级配置管理：环境变量、多环境部署与日志监控
**副标题：** 让你的代码在任何地方都能运行

**学习目标：**
- 掌握 .env 配置管理
- 实现多环境配置切换
- 搭建日志监控系统

**核心内容：**
1. 为什么需要配置管理？
   - 开发/测试/生产环境差异
   - 敏感信息保护（API Key）
   - 团队协作配置共享

2. 创建 .env 配置文件
   - 服务器配置
   - 数据库配置
   - LLM API 配置

3. 使用 python-dotenv 加载配置
   - config/load_env.py 模块
   - 配置验证与默认值
   - 配置读取工具函数

4. 更新 serv.py 使用配置

5. 搭建日志系统
   - **为什么需要日志？**
   - logging.conf 配置文件
   - 彩色日志输出（colorlog）
   - 日志轮转（TimedRotatingFileHandler）
   - 在代码中使用日志

6. 多环境配置管理
   - .env.dev / .env.test / .env.pro
   - 环境切换脚本

**预计代码量：** 40-50 行

**完整代码汇总：**
- config/load_env.py
- config/logging.conf
- serv.py（更新版）

**思考题：**
- 为什么不把 API Key 直接写在代码里？
- 日志轮转有什么好处？

---

#### 第 4 章：SQLAlchemy ORM 实战：从数据库连接池到模型设计
**副标题：** 告别裸写 SQL 的时代

**学习目标：**
- 掌握 SQLAlchemy ORM 使用
- 实现数据库连接池
- 设计用户数据模型

**核心内容：**
1. 为什么需要数据库？
   - 持久化用户数据
   - 存储聊天记录
   - 记录查询历史

2. Docker 快速启动 MySQL
   - docker-compose.yaml 配置
   - 数据持久化挂载

3. 安装数据库相关依赖
   - sqlalchemy
   - pymysql
   - aiomysql

4. 配置数据库连接（.env）

5. 创建数据库连接池
   - **为什么需要连接池？**
   - 单例模式实现
   - 连接池参数调优
   - model/db_connection_pool.py

6. 定义第一个数据模型
   - SQLAlchemy Base 类
   - User 用户模型
   - 字段类型与约束
   - 时间戳自动管理

7. 初始化数据库表
   - common/initialize_mysql.py
   - before_server_start 钩子

8. 测试数据库连接

**预计代码量：** 80-100 行

**完整代码汇总：**
- model/db_connection_pool.py
- model/db_models.py
- common/initialize_mysql.py
- serv.py（更新版）

**思考题：**
- 连接池的工作原理是什么？
- ORM 相比原生 SQL 的优缺点？

---

#### 第 5 章：打造企业级用户认证：JWT + 密码加密 + 权限控制
**副标题：** 让你的 API 安全如堡垒

**学习目标：**
- 实现用户注册与登录
- 掌握 JWT 认证机制
- 使用装饰器实现权限控制

**核心内容：**
1. 为什么需要用户认证？
   - 数据安全保护
   - 用户身份识别
   - 行为审计追踪

2. JWT 认证原理详解
   - 什么是 JWT（JSON Web Token）
   - JWT 结构：Header + Payload + Signature
   - 工作流程图解
   - JWT vs Session 对比

3. 安装依赖
   - pyjwt
   - bcrypt

4. 配置 JWT 密钥（.env）

5. 创建用户服务
   - services/user_service.py
   - 用户注册（密码加密）
   - 用户登录（密码验证）
   - 生成 JWT Token
   - 解析 JWT Token

6. 创建用户 API 控制器
   - controllers/user_service_api.py
   - POST /user/login
   - POST /user/register

7. JWT 认证装饰器
   - common/token_decorator.py
   - @check_token 实现
   - 从 Authorization Header 提取 Token
   - Token 过期处理

8. 保护 API 端点
   - 在需要认证的接口上使用装饰器

9. 测试完整认证流程
   - 注册新用户
   - 登录获取 Token
   - 使用 Token 访问受保护接口

**预计代码量：** 100-120 行

**完整代码汇总：**
- services/user_service.py
- controllers/user_service_api.py
- common/token_decorator.py
- model/db_models.py（更新 User 模型）

**思考题：**
- 为什么 JWT 适合分布式系统？
- 如何防止 Token 被盗用？

---

### 🔵 第二阶段：LLM 基础集成（第 6-10 章）

#### 第 6 章：LangChain 快速入门：5 分钟对接你的第一个大模型
**副标题：** 从 OpenAI 到通义千问的无缝切换

**学习目标：**
- 掌握 LangChain 核心概念
- 对接通义千问 API
- 实现第一个聊天接口

**核心内容：**
1. LangChain 是什么？
   - LLM 应用开发框架
   - 核心组件：LLM、Prompt、Chain、Agent
   - 为什么需要 LangChain？

2. 安装 LangChain
   - langchain
   - langchain-openai
   - dashscope（通义千问）

3. 配置 LLM API（.env）
   - MODEL_TYPE=qwen
   - MODEL_NAME=qwen-plus
   - MODEL_API_KEY
   - MODEL_BASE_URL

4. 创建 LLM 工具类
   - common/llm_util.py
   - 初始化 LLM（支持多种模型）
   - 统一接口封装

5. 实现第一个聊天 API
   - controllers/common_chat_api.py
   - POST /chat/completion
   - 调用 LLM 生成回复

6. 测试对话功能

7. 多模型切换实战
   - 通义千问 Qwen
   - OpenAI GPT
   - DeepSeek

**预计代码量：** 50-60 行

**完整代码汇总：**
- common/llm_util.py
- controllers/common_chat_api.py

**思考题：**
- LangChain 的抽象层带来了什么好处？
- 如何估算 LLM API 调用成本？

---

#### 第 7 章：流式响应实战：让 AI 对话像打字机一样优雅
**副标题：** Server-Sent Events (SSE) 完全指南

**学习目标：**
- 理解流式响应原理
- 实现 SSE 服务端推送
- 优化用户体验

**核心内容：**
1. 为什么需要流式响应？
   - LLM 生成速度慢（3-5 秒）
   - 用户体验提升（实时反馈）
   - 降低等待焦虑

2. SSE vs WebSocket vs 轮询
   - 技术对比分析
   - 为什么选择 SSE？

3. Sanic 实现 SSE
   - response.stream() 流式响应
   - await response.write() 推送数据
   - SSE 数据格式规范

4. LangChain 流式输出
   - llm.astream() 方法
   - 逐 Token 推送

5. 实现流式聊天 API
   - POST /chat/stream
   - 流式推送完整代码

6. 前端对接 SSE
   - EventSource API
   - 实时显示打字效果

7. 错误处理与重连机制

**预计代码量：** 60-70 行

**完整代码汇总：**
- controllers/common_chat_api.py（更新版）
- 前端 EventSource 示例代码

**思考题：**
- SSE 的单向通信有什么局限性？
- 如何优雅地关闭流式连接？

---

#### 第 8 章：Prompt 工程实战：如何让大模型更听话？
**副标题：** 从零基础到 Prompt 高手

**学习目标：**
- 掌握 Prompt 工程技巧
- 实现结构化输出
- 管理 Prompt 模板

**核心内容：**
1. 什么是 Prompt 工程？
   - 提示词的重要性
   - 好 Prompt vs 坏 Prompt 对比

2. Prompt 设计模式
   - **Zero-Shot：** 零样本提示
   - **Few-Shot：** 少样本学习
   - **CoT（Chain of Thought）：** 思维链
   - **ReAct：** 推理+行动

3. 结构化输出
   - 为什么需要 JSON 格式？
   - LangChain 的 StructuredOutputParser
   - Pydantic 模型约束
   - 实战：让 LLM 返回 JSON

4. Prompt 模板管理
   - PromptTemplate 类
   - 变量占位符
   - 模板复用

5. 实战：Text2SQL Prompt 设计
   - 输入：表结构 + 用户问题
   - 输出：SQL + 图表类型
   - Few-Shot 示例

**预计代码量：** 40-50 行

**完整代码汇总：**
- Prompt 模板示例
- 结构化输出代码

**思考题：**
- Few-Shot 的样本数量多少合适？
- 如何评估 Prompt 的质量？

---

#### 第 9 章：文件处理工具链：Excel、PDF、Word 一网打尽
**副标题：** MinIO 对象存储 + 多格式解析

**学习目标：**
- 搭建 MinIO 对象存储
- 实现多格式文件解析
- 构建文件上传 API

**核心内容：**
1. 为什么需要对象存储？
   - 本地文件系统的问题
   - MinIO vs 阿里云 OSS vs AWS S3
   - MinIO 的优势

2. Docker 部署 MinIO
   - docker-compose 配置
   - 访问控制台

3. 安装文件处理依赖
   - minio
   - openpyxl（Excel）
   - pymupdf（PDF）
   - python-docx（Word）
   - pandas

4. 创建 MinIO 工具类
   - common/minio_util.py
   - 上传文件
   - 下载文件
   - 获取文件 URL

5. 文件解析工具
   - common/file_parse.py
   - Excel 解析：读取工作表、列类型推断
   - PDF 解析：文本提取、格式保留
   - Word 解析：转 Markdown

6. 文件上传 API
   - controllers/file_chat_api.py
   - POST /file/upload
   - POST /file/parse

7. 测试文件上传流程

**预计代码量：** 100-120 行

**完整代码汇总：**
- common/minio_util.py
- common/file_parse.py
- controllers/file_chat_api.py

**思考题：**
- 如何处理大文件上传（100MB+）？
- 文件安全性如何保障？

---

#### 第 10 章：DuckDB 内存数据库：在 Excel 上执行 SQL 查询
**副标题：** 不需要导入数据库的 SQL 引擎

**学习目标：**
- 掌握 DuckDB 使用
- 实现 Excel 文件 SQL 查询
- 理解内存数据库优势

**核心内容：**
1. DuckDB 是什么？
   - OLAP 分析型数据库
   - 完全运行在内存中
   - 直接查询 CSV/Parquet/Excel

2. 为什么选择 DuckDB？
   - vs SQLite：列式存储、OLAP 优化
   - vs Pandas：SQL 查询更直观
   - vs 传统数据库：无需导入数据

3. 安装 DuckDB
   ```bash
   uv pip install duckdb
   ```

4. DuckDB 基础用法
   - 创建连接
   - 注册 DataFrame 为虚拟表
   - 执行 SQL 查询

5. 实战：查询 Excel 文件
   - 读取 Excel → Pandas DataFrame
   - 注册为 DuckDB 表
   - 执行 SQL 查询
   - 返回结果

6. 集成到文件问答 API
   - services/text2_sql_service.py
   - exe_file_sql_query() 方法

7. 完整测试流程
   - 上传 Excel 文件
   - 执行 SQL 查询
   - 返回查询结果

**预计代码量：** 50-60 行

**完整代码汇总：**
- services/text2_sql_service.py
- DuckDB 查询示例代码

**思考题：**
- DuckDB 的列式存储有什么优势？
- 内存数据库的局限性是什么？

---

### 🟡 第三阶段：多智能体架构核心（第 11-15 章）

#### 第 11 章：LangGraph 入门：用状态机编排复杂工作流
**副标题：** 从 Chain 到 Graph 的思维跃迁

**学习目标：**
- 理解 LangGraph 设计理念
- 掌握状态机编程
- 实现第一个图工作流

**核心内容：**
1. 为什么 LangChain 的 Chain 不够用？
   - Chain 的局限性：线性流程
   - 复杂场景：条件分支、循环、并行

2. LangGraph 是什么？
   - 基于图的工作流编排
   - StateGraph：状态机编程
   - 受 Apache Beam 启发

3. 核心概念详解
   - **Node（节点）：** 执行单元
   - **Edge（边）：** 流转路径
   - **State（状态）：** 共享数据
   - **Conditional Edge：** 条件路由

4. 安装 LangGraph
   ```bash
   uv pip install langgraph
   ```

5. 第一个图工作流：问题分类器
   - 定义 State 类
   - 添加节点
   - 添加边
   - 编译图
   - 执行图

6. 可视化工作流
   - graph.get_graph().draw_mermaid()

7. 实战：路由不同类型的问题
   - 通用问答 → 通用智能体
   - 数据问答 → Text2SQL 智能体
   - 文件问答 → Excel 智能体

**预计代码量：** 60-70 行

**完整代码汇总：**
- agent/question_router.py
- State 定义示例

**思考题：**
- 图工作流相比线性 Chain 的优势？
- 如何调试复杂的图结构？

---

#### 第 12 章：Text2SQL 智能体（上）：从自然语言到 SQL 语句
**副标题：** 混合检索 + LLM 生成 SQL

**学习目标：**
- 理解 Text2SQL 核心挑战
- 实现混合检索系统
- 构建 SQL 生成节点

**核心内容：**
1. Text2SQL 的核心挑战
   - 挑战 1：如何选择相关表？（表太多）
   - 挑战 2：如何理解表结构？（列注释、类型）
   - 挑战 3：如何处理多表 JOIN？
   - 挑战 4：如何保证 SQL 正确性？

2. 混合检索系统设计
   - **BM25 关键词检索：** 精确匹配
   - **FAISS 向量检索：** 语义相似
   - **RRF 融合：** 结合两者优势
   - **重排序：** DashScope Rerank 优化

3. 安装依赖
   ```bash
   uv pip install jieba rank-bm25 pyfaiss-cpu dashscope
   ```

4. 实现 Schema Inspector 节点
   - agent/text2sql/database/db_service.py
   - get_table_schema() 方法
   - BM25 检索实现
   - FAISS 向量索引构建
   - 混合检索融合

5. 向量索引持久化
   - 索引保存与加载
   - 避免重复构建

6. Neo4j 表关系查询
   - 为什么需要图数据库？
   - 安装 Neo4j（Docker）
   - 存储表关系图谱
   - agent/text2sql/database/neo4j_search.py

7. SQL 生成节点
   - agent/text2sql/sql/generator.py
   - Prompt 设计
   - Few-Shot 示例
   - 图表类型推荐

**预计代码量：** 150-180 行（分多个文件）

**完整代码汇总：**
- agent/text2sql/database/db_service.py
- agent/text2sql/database/neo4j_search.py
- agent/text2sql/sql/generator.py

**思考题：**
- 为什么混合检索比单一方法好？
- 如何评估 SQL 生成的准确率？

---

#### 第 13 章：Text2SQL 智能体（下）：执行 SQL + 数据可视化
**副标题：** 从查询结果到 ECharts 图表

**学习目标：**
- 实现 SQL 执行节点
- 构建数据摘要生成
- 集成 ECharts 可视化

**核心内容：**
1. SQL 执行节点
   - agent/text2sql/database/db_service.py
   - execute_sql() 方法
   - SQL 注入防护
   - 错误处理

2. 数据摘要节点
   - agent/text2sql/analysis/llm_summarizer.py
   - 输入：SQL 结果 + 用户问题
   - 输出：自然语言摘要
   - Prompt 设计

3. 图表类型选择逻辑
   - 柱状图：对比、排名
   - 折线图：趋势、时间序列
   - 饼图：占比、分布
   - 表格：详细数据

4. ECharts 表格渲染
   - agent/text2sql/analysis/data_render_apache.py
   - 生成 ECharts 配置
   - JSON 格式输出

5. MCP 工具调用（高级图表）
   - agent/text2sql/analysis/data_render_antv.py
   - 连接 MCP Hub
   - 调用图表生成工具
   - 返回图表配置

6. 完整工作流图
   - agent/text2sql/analysis/graph.py
   - 定义 StateGraph
   - 添加所有节点
   - 条件路由：选择渲染方式

7. Text2SQL Agent 主类
   - agent/text2sql/text2_sql_agent.py
   - run_agent() 方法
   - 流式输出每个步骤

**预计代码量：** 120-150 行

**完整代码汇总：**
- agent/text2sql/analysis/llm_summarizer.py
- agent/text2sql/analysis/data_render_apache.py
- agent/text2sql/analysis/graph.py
- agent/text2sql/text2_sql_agent.py

**思考题：**
- 如何处理 SQL 执行超时？
- 图表推荐的准确性如何提升？

---

#### 第 14 章：ReAct Agent 实战：让 AI 自己决定调用哪些工具
**副标题：** Reason + Act = 自主智能体

**学习目标：**
- 理解 ReAct 模式原理
- 使用 LangChain 构建 ReAct Agent
- 实现工具自动选择

**核心内容：**
1. 什么是 ReAct？
   - Reason（推理）：思考下一步做什么
   - Act（行动）：调用工具
   - Observe（观察）：查看工具结果
   - 循环迭代直到完成任务

2. ReAct vs Chain
   - Chain：固定流程
   - ReAct：动态决策

3. LangChain 的 create_react_agent
   - 源码分析
   - 工作原理

4. 定义工具（Tools）
   - @tool 装饰器
   - 工具名称与描述
   - 参数定义

5. 实战：构建通用问答 Agent
   - 工具 1：搜索引擎（Bing/Tavily）
   - 工具 2：计算器
   - 工具 3：查询历史记录
   - agent/common_react_agent.py

6. 集成到聊天 API
   - controllers/common_chat_api.py
   - 流式输出 Agent 思考过程

7. 测试 Agent 自主决策
   - 问题 1：需要搜索
   - 问题 2：需要计算
   - 问题 3：多步骤推理

**预计代码量：** 80-100 行

**完整代码汇总：**
- agent/common_react_agent.py
- 工具定义示例

**思考题：**
- ReAct 的循环次数如何控制？
- 如何防止 Agent 陷入死循环？

---

#### 第 15 章：MCP 多智能体协议：让多个 AI 协同工作
**副标题：** Model Context Protocol 完全指南

**学习目标：**
- 理解 MCP 协议设计
- 搭建 MCP Hub 服务
- 实现多智能体协同

**核心内容：**
1. MCP 是什么？
   - Model Context Protocol（模型上下文协议）
   - Anthropic 提出的标准
   - 解决什么问题？

2. 为什么需要智能体协议？
   - 工具标准化
   - 智能体互操作
   - 生态系统构建

3. MCP 架构详解
   - MCP Server：提供工具
   - MCP Client：调用工具
   - MCP Hub：工具集管理

4. 安装 MCP
   ```bash
   uv pip install mcp langchain-mcp-adapters
   ```

5. 编写 MCP Server
   - agent/mcp/query_qa_history_mcp.py
   - 使用 FastMCP 框架
   - 定义工具：查询历史记录
   - 启动服务

6. 搭建 MCP Hub
   - 使用 Claude 官方 Hub
   - 或自建 Hub
   - 配置工具集分组

7. MCP Client 使用
   - common/mcp_client.py
   - 连接 MCP Hub
   - 获取工具列表
   - 调用远程工具

8. 多智能体协同示例
   - 通用问答智能体 + 数据问答智能体
   - 工具共享与调用

**预计代码量：** 70-90 行

**完整代码汇总：**
- agent/mcp/query_qa_history_mcp.py
- common/mcp_client.py
- MCP Hub 配置

**思考题：**
- MCP 与 OpenAI Function Calling 的区别？
- 如何保证 MCP 工具的安全性？

---

### 🟠 第四阶段：完整项目实现（第 16-20 章）

#### 第 16 章：Excel 表格问答智能体：上传文件即可对话
**副标题：** DuckDB + LangGraph 完整实现

**学习目标：**
- 实现 Excel 智能体完整流程
- 处理文件上传与解析
- 构建端到端对话

**核心内容：**
1. Excel 智能体架构设计
2. Excel 解析节点
   - agent/excel/excel_mapping_node.py
   - 读取工作表
   - 推断列类型
   - 生成表结构描述

3. SQL 生成节点
   - agent/excel/excel_sql_node.py
   - 基于文件结构生成 SQL

4. SQL 执行节点
   - agent/excel/excel_excute_sql.py
   - 使用 DuckDB 查询

5. 数据摘要与可视化
   - 复用 Text2SQL 的节点

6. ExcelAgent 主类
   - agent/excel/excel_agent.py
   - 状态定义
   - 图编排
   - 流式执行

7. 文件问答 API
   - controllers/file_chat_api.py
   - POST /file/process_file_llm_out

8. 完整测试流程
   - 上传销售数据 Excel
   - 提问："哪个月销售额最高？"
   - 返回：图表 + 摘要

**预计代码量：** 100-120 行

**完整代码汇总：**
- agent/excel/excel_agent.py
- agent/excel/excel_graph.py
- controllers/file_chat_api.py（完整版）

**思考题：**
- Excel 智能体与 Text2SQL 智能体的区别？
- 如何处理复杂的 Excel 文件（多工作表）？

---

#### 第 17 章：前端开发：Vue3 + TypeScript 打造现代化 UI
**副标题：** 从零搭建聊天界面

**学习目标：**
- 搭建 Vue3 项目
- 实现聊天组件
- 对接后端 API

**核心内容：**
1. 创建 Vue3 项目
   ```bash
   npm create vue@latest
   ```

2. 项目结构规划
   - web/src/
   - 组件、路由、状态管理

3. 安装依赖
   - Naive UI
   - Axios
   - Pinia

4. 配置 Vite
   - vite.config.ts
   - 代理配置

5. 创建 API 客户端
   - web/src/api/index.ts
   - Axios 实例配置
   - 请求拦截器（添加 Token）
   - 响应拦截器（错误处理）

6. 实现聊天组件
   - web/src/components/ChatBox.vue
   - 消息列表
   - 输入框
   - 发送按钮

7. 对接 SSE 流式响应
   - EventSource API
   - 实时显示 AI 回复

8. 状态管理
   - web/src/store/userStore.ts
   - 用户信息
   - Token 管理

9. 路由配置
   - web/src/router/index.ts

**预计代码量：** 150-200 行

**完整代码汇总：**
- web/src/api/index.ts
- web/src/components/ChatBox.vue
- web/src/store/userStore.ts

**思考题：**
- 为什么使用 TypeScript？
- 前端状态管理的必要性？

---

#### 第 18 章：数据可视化：ECharts 图表动态渲染
**副标题：** 从 JSON 数据到交互式图表

**学习目标：**
- 集成 ECharts
- 动态渲染图表
- 实现图表交互

**核心内容：**
1. 安装 ECharts
   ```bash
   npm install echarts
   ```

2. 创建图表组件
   - web/src/components/ChartRender.vue
   - Props 接收图表配置
   - 使用 echarts.init() 初始化

3. 支持多种图表类型
   - 柱状图
   - 折线图
   - 饼图
   - 表格

4. 动态更新图表
   - watch 监听数据变化
   - setOption() 更新配置

5. 图表交互
   - 点击事件
   - 缩放
   - 数据筛选

6. Markdown + 图表混合显示
   - web/src/components/MessageItem.vue
   - 解析消息中的图表 JSON
   - 渲染为 ECharts 图表

7. 完整对话流程
   - 用户提问
   - 后端返回：摘要 + 图表配置
   - 前端渲染：文本 + 图表

**预计代码量：** 80-100 行

**完整代码汇总：**
- web/src/components/ChartRender.vue
- web/src/components/MessageItem.vue

**思考题：**
- 如何优化大数据量图表的性能？
- ECharts vs AntV 如何选择？

---

#### 第 19 章：Docker 容器化部署：一键启动完整项目
**副标题：** Docker Compose 多容器编排

**学习目标：**
- 编写 Dockerfile
- 使用 Docker Compose 编排
- 实现一键部署

**核心内容：**
1. 为什么需要容器化？
   - 环境一致性
   - 快速部署
   - 易于扩展

2. 编写后端 Dockerfile
   - docker/Dockerfile
   - 基础镜像选择
   - 依赖安装
   - 启动脚本

3. 编写前端 Dockerfile
   - 多阶段构建
   - Nginx 部署

4. Docker Compose 编排
   - docker/docker-compose.yaml
   - 服务定义：
     - chat-web（前端）
     - chat-service（后端）
     - mysql
     - neo4j
     - minio
     - redis

5. 环境变量管理
   - docker/.env.template
   - 敏感信息处理

6. 网络配置
   - 容器间通信
   - 端口映射

7. 数据持久化
   - Volume 挂载
   - 数据备份

8. 启动与测试
   ```bash
   cd docker
   docker-compose up -d
   ```

9. 日志查看与调试

**预计代码量：** 100-120 行（配置文件）

**完整代码汇总：**
- docker/Dockerfile（后端）
- docker/Dockerfile.web（前端）
- docker/docker-compose.yaml
- docker/.env.template

**思考题：**
- 容器化部署的安全性考虑？
- 如何实现容器的健康检查？

---

#### 第 20 章：生产优化与扩展：性能调优、监控与二次开发指南
**副标题：** 从 Demo 到生产级应用

**学习目标：**
- 掌握性能优化技巧
- 搭建监控系统
- 理解二次开发路径

**核心内容：**
1. 性能优化

   **1.1 向量索引优化**
   - FAISS 索引持久化
   - 避免重复构建
   - 增量更新策略

   **1.2 数据库连接池调优**
   - pool_size 参数选择
   - 连接泄漏检测
   - 慢查询优化

   **1.3 缓存策略**
   - Redis 缓存 LLM 响应
   - 表结构缓存
   - 查询结果缓存

   **1.4 异步优化**
   - 并发处理优化
   - 批量操作

2. 监控与日志

   **2.1 日志分析**
   - ELK 栈集成
   - 日志聚合

   **2.2 性能监控**
   - Prometheus + Grafana
   - 关键指标：QPS、延迟、错误率

   **2.3 告警系统**
   - 异常检测
   - 邮件/短信通知

3. 安全加固

   **3.1 API 安全**
   - Rate Limiting（限流）
   - SQL 注入防护
   - XSS 防护

   **3.2 数据安全**
   - 敏感信息脱敏
   - 数据库备份
   - 加密传输（HTTPS）

4. 二次开发指南

   **4.1 如何添加新的智能体？**
   - 定义 State 类
   - 实现节点函数
   - 编排工作流图
   - 注册到路由

   **4.2 如何支持新的 LLM？**
   - 扩展 llm_util.py
   - 适配接口差异

   **4.3 如何接入新的工具？**
   - 编写 MCP Server
   - 注册到 MCP Hub

5. 常见问题排查

   **5.1 LLM 响应慢**
   - 检查网络
   - 切换模型
   - 启用缓存

   **5.2 SQL 生成不准确**
   - 优化 Prompt
   - 增加 Few-Shot 示例
   - 改进混合检索

   **5.3 图表渲染错误**
   - 检查 ECharts 配置
   - 验证数据格式

6. 项目总结与展望
   - 技术栈回顾
   - 核心能力总结
   - 未来扩展方向

**预计代码量：** 50-80 行（优化代码示例）

**完整代码汇总：**
- 性能优化配置
- 监控脚本
- 二次开发模板

**思考题：**
- 如何评估系统的性能瓶颈？
- 生产环境还需要哪些改进？

---

## 🎓 学习路径建议

### 适合人群
- Python 中级开发者
- 对 AI 应用感兴趣的工程师
- 希望构建企业级 LLM 应用的团队

### 前置知识
- Python 基础（异步编程加分）
- 基本的 SQL 知识
- 了解 Web 开发概念
- 前端基础（HTML/CSS/JavaScript）

### 学习建议
1. **循序渐进**：按章节顺序学习，不要跳跃
2. **动手实践**：每章的代码都要亲自敲一遍
3. **理解原理**：不要只是复制代码，要理解为什么这么做
4. **主动思考**：认真思考每章的思考题
5. **扩展练习**：尝试用自己的数据测试

---

## 📞 支持与反馈

**问题反馈：**
- 教程中的错误或不清楚的地方
- 代码无法运行的问题
- 改进建议

**扩展阅读：**
- LangChain 官方文档
- LangGraph 官方文档
- Sanic 官方文档
- Vue3 官方文档

---

## 📝 版权声明

本教程为教学目的编写，代码基于 MIT 协议开源。

---

**祝学习愉快！🚀**
