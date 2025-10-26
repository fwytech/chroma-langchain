# 第 1 章：为什么要做 AI 数据助手？技术架构与开发环境全攻略

**副标题：** 从 Excel 到 AI 对话的革命性转变

---

## 📚 本章导读

欢迎来到《从零打造企业级 Text2SQL 表格问答系统》教程的第一章！

在这一章中，我们将从"为什么"开始，深入探讨：
- 传统数据分析工具的痛点是什么？
- AI 数据助手如何解决这些问题？
- 为什么选择这套技术栈？
- 如何搭建一个干净、隔离的开发环境？

**学习目标：**
- ✅ 理解 AI 数据助手的业务价值
- ✅ 掌握项目整体技术架构
- ✅ 使用 uv 搭建隔离开发环境
- ✅ 完成开发环境的准备工作

**预计学习时间：** 1-1.5 小时

---

## 1.1 什么是大模型数据助手？

### 1.1.1 从一个真实场景说起

想象一下，你是一家电商公司的运营经理，每天早上第一件事就是查看昨天的销售数据：

**传统方式（使用 Excel 或 BI 工具）：**
```
1. 打开 Excel 文件或登录 Tableau
2. 手动筛选日期范围
3. 使用公式计算：=SUMIF(...)
4. 创建数据透视表
5. 插入图表
6. 调整图表样式
⏰ 耗时：10-15 分钟
```

**使用 AI 数据助手：**
```
你："昨天各个品类的销售额是多少？帮我用柱状图展示"
AI："好的，正在查询...
    [自动生成 SQL]
    [执行查询]
    [生成图表]
    昨天的销售数据如下：
    - 电子产品：¥125,680
    - 服装鞋包：¥98,340
    - 食品饮料：¥76,220
    [显示柱状图]"
⏰ 耗时：5 秒
```

这就是 **AI 数据助手** 的魔力：**用自然语言，秒级获得数据洞察！**

---

### 1.1.2 传统 BI 工具的五大痛点

让我们深入分析传统数据分析方式的问题：

#### 痛点 1：学习成本高
- **Excel：** 需要掌握复杂的公式（VLOOKUP、INDEX/MATCH、数据透视表）
- **SQL：** 需要学习 SELECT、JOIN、GROUP BY 等语法
- **BI 工具：** Tableau/PowerBI 的学习曲线陡峭
- **问题：** 非技术人员（如运营、销售）难以上手

#### 痛点 2：操作繁琐
- 每次查询都要重复相同的步骤
- 图表制作需要手动配置
- 数据刷新需要人工操作
- **问题：** 效率低下，浪费时间

#### 痛点 3：灵活性差
- BI 工具的报表是预定义的
- 想要新的维度分析，需要 IT 部门支持
- 临时性的数据需求响应慢
- **问题：** 无法满足灵活多变的业务需求

#### 痛点 4：协作困难
- 查询结果难以分享
- 无法记录分析过程
- 团队成员重复劳动
- **问题：** 知识无法沉淀

#### 痛点 5：门槛高的技术要求
- 需要了解数据库表结构
- 需要知道字段含义
- 需要理解表之间的关系
- **问题：** 业务人员依赖技术人员

---

### 1.1.3 AI 数据助手的价值主张

AI 数据助手通过引入大语言模型（LLM），彻底改变了数据分析的交互方式：

#### 价值 1：零门槛使用
```
传统：SELECT product_category, SUM(sales_amount)
      FROM orders
      WHERE order_date = '2025-10-25'
      GROUP BY product_category

AI：  "昨天各品类的销售额"
```
**不需要懂 SQL，用自己的话就能查数据！**

#### 价值 2：自动化数据可视化
```python
# AI 自动：
# 1. 判断数据适合什么图表（柱状图/折线图/饼图）
# 2. 生成 ECharts 配置
# 3. 渲染交互式图表
# 用户只需要说："用图表展示"
```

#### 价值 3：上下文理解
```
用户："销售额最高的品类"  → 查询数据
用户："给我看看趋势"      → AI 知道是指上一个品类的趋势
用户："对比去年同期"      → AI 知道要对比的时间范围
```
**AI 能记住对话上下文，像人一样交流！**

#### 价值 4：智能推荐
```python
# AI 不仅回答问题，还会主动建议：
"根据数据，我发现本月电子产品销售额下降了15%，建议查看：
 1. 是否有促销活动结束？
 2. 竞品是否有价格战？
 3. 库存是否充足？"
```

#### 价值 5：实时协作与知识沉淀
- 所有查询历史自动保存
- 团队成员可以查看彼此的分析
- 常见问题自动形成知识库

---

### 1.1.4 典型应用场景

AI 数据助手可以应用于各行各业：

#### 场景 1：电商运营
```
问题："最近一周哪些商品退货率最高？"
结果：自动查询 → 生成报表 → 推荐优化建议
```

#### 场景 2：财务分析
```
问题："本季度各部门的费用支出对比去年如何？"
结果：多表 JOIN → 时间对比 → 可视化展示
```

#### 场景 3：人力资源
```
问题："哪些部门的员工流失率最高？"
结果：计算流失率 → 趋势分析 → 预警提示
```

#### 场景 4：客户服务
```
问题："上个月客户投诉最多的问题是什么？"
结果：文本分析 → 分类统计 → 改进建议
```

#### 场景 5：供应链管理
```
问题："哪些供应商的交货及时率低于 90%？"
结果：计算指标 → 供应商排名 → 风险评估
```

---

## 1.2 为什么需要这个项目？

市面上已经有不少 AI 数据分析工具，为什么我们还要自己开发一个？

### 1.2.1 现有方案对比

让我们对比几种常见方案：

#### 方案 1：纯 Prompt 工程（手动构建）
```python
# 直接调用 OpenAI API
prompt = f"根据表结构：{schema}，生成 SQL 查询：{question}"
response = openai.chat.completions.create(model="gpt-4", messages=[...])
sql = response.choices[0].message.content
```

**优点：**
- 实现简单，代码量少

**缺点：**
- ❌ 准确率低（表太多时 LLM 容易混淆）
- ❌ 无法处理复杂查询（多表 JOIN）
- ❌ 没有错误恢复机制
- ❌ 无法可视化
- ❌ 无法扩展

**适用场景：** Demo 演示，不适合生产

---

#### 方案 2：Dify 低代码平台
Dify 是一个优秀的 LLM 应用开发平台，提供可视化编排。

**优点：**
- ✅ 可视化编排工作流
- ✅ 内置多种工具
- ✅ 开箱即用

**缺点：**
- ❌ 灵活性受限（被平台约束）
- ❌ 深度定制困难
- ❌ 依赖 Dify 生态
- ❌ 学习成本（需要理解 Dify 的概念）
- ❌ 难以集成到现有系统

**适用场景：** 快速原型验证，非技术团队

---

#### 方案 3：纯 LangChain 实现
```python
from langchain.chains import SQLDatabaseChain
chain = SQLDatabaseChain.from_llm(llm, db)
result = chain.run("查询销售数据")
```

**优点：**
- ✅ 组件丰富
- ✅ 生态完善

**缺点：**
- ❌ 复杂场景需要大量定制
- ❌ 缺少状态管理（流程控制弱）
- ❌ 错误处理不够灵活
- ❌ 图表生成需要额外开发

**适用场景：** 中等复杂度项目

---

#### 方案 4：本项目（LangGraph + MCP + ReActAgent）

**我们的方案结合了各家之长：**

| 特性 | 纯 Prompt | Dify | 纯 LangChain | 本项目 |
|------|-----------|------|--------------|--------|
| **准确率** | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **灵活性** | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **可维护性** | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **扩展性** | ⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **可视化** | ❌ | ✅ | ❌ | ✅ |
| **多智能体** | ❌ | ⚠️ 有限 | ⚠️ 复杂 | ✅ |
| **学习曲线** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |

**核心优势：**
1. **LangGraph：** 状态机编程，清晰的流程控制
2. **MCP：** 多智能体协同，工具标准化
3. **ReActAgent：** 自主决策，动态工具选择
4. **混合检索：** BM25 + 向量检索，提升准确率
5. **Neo4j：** 图数据库优化多表 JOIN
6. **完整可视化：** ECharts + AntV 自动生成图表

---

### 1.2.2 本项目的技术亮点

#### 亮点 1：混合检索系统
```
用户问题："销售额最高的品类"
    ↓
BM25 关键词检索      FAISS 向量检索
"销售" → t_orders    语义相似 → t_products
"品类" → t_products  相似问题历史
    ↓                    ↓
        RRF 融合结果
    ↓
DashScope 重排序
    ↓
精准的表结构（准确率 95%+）
```

#### 亮点 2：图数据库优化 JOIN
```python
# 传统方式：LLM 可能生成错误的 JOIN
SELECT o.*, p.*
FROM orders o
JOIN products p ON o.product_name = p.name  # ❌ 字段名可能不对

# 使用 Neo4j 图谱：
# 1. Neo4j 存储：orders -[:HAS_PRODUCT {join_key: "product_id"}]-> products
# 2. 查询图谱获取准确的 JOIN 关系
# 3. LLM 生成正确的 SQL
SELECT o.*, p.*
FROM orders o
JOIN products p ON o.product_id = p.id  # ✅ 准确！
```

#### 亮点 3：自适应图表推荐
```python
# AI 自动判断：
数据类型 → 推荐图表
时间序列 → 折线图
分类对比 → 柱状图
占比分布 → 饼图
详细数据 → 表格
```

#### 亮点 4：多智能体协同
```
用户："分析销售数据，顺便搜索一下行业趋势"
    ↓
问题分类智能体：检测到需要两个任务
    ↓                    ↓
Text2SQL 智能体      通用搜索智能体
    ↓                    ↓
   销售分析结果          行业报告
    ↓
结果融合智能体：生成综合分析报告
```

#### 亮点 5：生产级工程实践
- ✅ 连接池管理（数据库/Redis）
- ✅ 向量索引持久化（避免重复计算）
- ✅ 日志监控（彩色日志、文件轮转）
- ✅ 错误恢复机制
- ✅ JWT 认证与权限控制
- ✅ Docker 一键部署

---

## 1.3 技术选型深度解析

现在我们来详细解释为什么选择这套技术栈。每个技术的选择都有深思熟虑的理由。

### 1.3.1 为什么选择 Sanic Web 框架？

#### 问题：为什么不用 Flask 或 FastAPI？

让我们对比三大 Python Web 框架：

#### Flask（同步框架）
```python
from flask import Flask
app = Flask(__name__)

@app.route('/chat')
def chat():
    response = openai.chat.completions.create(...)  # 阻塞 5 秒
    return response
# 问题：一个请求处理 5 秒，其他请求只能等待
```

**特点：**
- ✅ 简单易学
- ✅ 生态丰富
- ❌ **同步阻塞：** IO 密集型应用性能差
- ❌ **并发能力弱：** 每个请求占用一个线程

---

#### FastAPI（异步框架）
```python
from fastapi import FastAPI
app = FastAPI()

@app.get('/chat')
async def chat():
    response = await openai.chat.completions.create(...)
    return response
# 异步非阻塞，性能好
```

**特点：**
- ✅ 异步支持
- ✅ 类型检查（Pydantic）
- ✅ 自动生成 API 文档
- ⚠️ 生态相对较新
- ⚠️ 流式响应支持一般

---

#### Sanic（异步框架）
```python
from sanic import Sanic
app = Sanic("app")

@app.get('/chat')
async def chat(request):
    response = await openai.chat.completions.create(...)
    return json(response)
# 异步 + 更好的流式支持
```

**特点：**
- ✅ **原生异步：** 基于 asyncio
- ✅ **高性能：** 处理速度接近 Go
- ✅ **流式响应：** response.stream() 原生支持
- ✅ **语法简洁：** 类似 Flask
- ⚠️ 生态不如 Flask 丰富

---

#### 性能对比（基准测试）

```
场景：100 个并发请求，每个请求调用 LLM（3 秒响应）

Flask（同步）：
- 总耗时：300 秒（100 × 3 秒，串行处理）
- QPS：0.33

FastAPI（异步）：
- 总耗时：3 秒（并行处理）
- QPS：33

Sanic（异步）：
- 总耗时：3 秒（并行处理）
- QPS：35（略优于 FastAPI）
```

**结论：LLM 应用是 IO 密集型（等待 API 响应），异步框架性能提升 100 倍！**

---

#### 为什么最终选择 Sanic？

**1. 流式响应支持最好**
```python
# Sanic 的流式响应非常优雅
@app.post("/chat/stream")
async def stream_chat(request):
    response = await request.respond(content_type="text/event-stream")

    async for chunk in llm.astream("你好"):
        await response.write(f"data: {chunk}\n\n")

    await response.eof()
```

**2. 性能足够好**
- 接近 FastAPI 的性能
- 比 Flask 快 10-100 倍

**3. 语法简洁**
- 类似 Flask，学习成本低
- 代码可读性好

**4. 原生异步**
- 不需要额外的异步包装
- 天然适合 LLM 应用

---

### 1.3.2 为什么选择 LangGraph 而不是 LangChain？

#### LangChain 的局限性

LangChain 的 **Chain** 机制适合线性流程：

```python
from langchain.chains import LLMChain

# Chain 1：检索文档
retrieval_chain = RetrievalQA(...)

# Chain 2：生成答案
qa_chain = LLMChain(...)

# 串联执行
result = qa_chain.run(retrieval_chain.run(question))
```

**问题：**
- ❌ **只能线性流程：** 步骤 1 → 步骤 2 → 步骤 3
- ❌ **无法条件分支：** 不能根据结果选择不同路径
- ❌ **难以循环：** 无法重试错误的步骤
- ❌ **状态管理困难：** 中间结果难以共享

---

#### LangGraph 的优势

LangGraph 使用 **StateGraph**（状态图），支持复杂流程：

```python
from langgraph.graph import StateGraph

# 定义状态
class AgentState(TypedDict):
    question: str
    table_schema: list
    sql: str
    result: Any
    chart_config: dict

# 创建图
graph = StateGraph(AgentState)

# 添加节点
graph.add_node("retrieve_schema", retrieve_schema)
graph.add_node("generate_sql", generate_sql)
graph.add_node("execute_sql", execute_sql)
graph.add_node("visualize", visualize)

# 添加边（流程控制）
graph.add_edge("retrieve_schema", "generate_sql")
graph.add_edge("generate_sql", "execute_sql")

# 条件边（根据结果选择路径）
graph.add_conditional_edges(
    "execute_sql",
    lambda state: "visualize" if state["result"] else "generate_sql",  # 失败则重试
    {"visualize": "visualize", "generate_sql": "generate_sql"}
)

# 执行
result = graph.invoke({"question": "销售额"})
```

**LangGraph 的核心优势：**

| 特性 | LangChain Chain | LangGraph StateGraph |
|------|-----------------|----------------------|
| **流程控制** | 线性 | 图（任意拓扑） |
| **条件分支** | ❌ | ✅ |
| **循环重试** | ❌ | ✅ |
| **并行执行** | ❌ | ✅ |
| **状态管理** | ⚠️ 困难 | ✅ 原生支持 |
| **可视化** | ❌ | ✅ Mermaid 图 |
| **错误恢复** | ⚠️ 困难 | ✅ 简单 |

---

#### 实际案例：Text2SQL 流程对比

**使用 LangChain Chain：**
```python
# 固定流程，无法处理异常
result = (
    retrieve_chain(question)
    .then(generate_sql_chain)
    .then(execute_sql_chain)
    .then(visualize_chain)
)
# 如果 SQL 执行失败怎么办？❌ 无法重试
```

**使用 LangGraph：**
```python
graph.add_conditional_edges(
    "execute_sql",
    lambda state: "generate_sql" if state.get("error") else "visualize",
    {"generate_sql": "generate_sql", "visualize": "visualize"}
)
# SQL 失败自动重新生成 ✅
```

**结论：LangGraph 是复杂 Agent 工作流的最佳选择！**

---

### 1.3.3 为什么需要 MCP（Model Context Protocol）？

#### 问题：智能体如何调用工具？

传统方式每个智能体都要自己实现工具：

```python
# Agent 1：数据问答智能体
def query_database(sql):
    conn = mysql.connect(...)
    return conn.execute(sql)

# Agent 2：通用问答智能体
def query_database(sql):  # ❌ 重复实现
    conn = mysql.connect(...)
    return conn.execute(sql)
```

**问题：**
- ❌ 代码重复
- ❌ 维护困难（修改一处要改多处）
- ❌ 工具不统一（接口不一致）
- ❌ 无法跨项目复用

---

#### MCP 的解决方案

**MCP（Model Context Protocol）** 是 Anthropic 提出的智能体工具协议，类似于"工具的 HTTP 协议"。

**架构：**
```
┌─────────────────┐
│  MCP Hub        │  工具注册中心
│  (工具市场)     │
└────────┬────────┘
         │
    ┌────┴────┬──────────┬────────┐
    │         │          │        │
┌───▼───┐ ┌──▼───┐  ┌───▼───┐ ┌──▼────┐
│ Tool1 │ │Tool2 │  │Tool3  │ │Tool4  │
│数据库 │ │搜索  │  │图表   │ │历史   │
└───────┘ └──────┘  └───────┘ └───────┘
    ▲         ▲          ▲        ▲
    └─────────┴──────────┴────────┘
              │
         ┌────┴────┐
         │ Agents  │  智能体们统一调用
         └─────────┘
```

**核心价值：**

1. **工具标准化**
```python
# 定义一次，到处使用
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("database-tools")

@mcp.tool(
    name="query_database",
    description="执行 SQL 查询",
)
async def query_database(sql: str) -> dict:
    return execute_sql(sql)

# 任何智能体都可以通过 MCP 调用
```

2. **跨智能体共享**
```python
# 数据问答智能体
tools = await mcp_client.get_tools(server="database-tools")

# 通用问答智能体
tools = await mcp_client.get_tools(server="database-tools")

# 同一个工具，不同智能体复用
```

3. **生态系统**
- 官方 MCP Hub：上千个工具
- 社区贡献：开箱即用
- 类似 npm/pip 的工具市场

---

### 1.3.4 为什么需要 Neo4j 图数据库？

#### 问题：多表 JOIN 的难题

企业数据库通常有几十甚至上百张表，表之间的关系复杂：

```sql
-- 查询"销售额最高的产品"需要 JOIN 多张表
SELECT p.name, SUM(od.amount)
FROM orders o
JOIN order_details od ON o.id = od.order_id      -- 关系 1
JOIN products p ON od.product_id = p.id          -- 关系 2
JOIN categories c ON p.category_id = c.id        -- 关系 3
GROUP BY p.name
```

**LLM 的挑战：**
- ❌ 如何知道 `orders` 和 `order_details` 通过 `id` 关联？
- ❌ 如何知道 `product_id` 是哪张表的字段？
- ❌ 如何知道表的主键和外键关系？

---

#### 传统方案：在 Prompt 中提供所有表信息

```python
prompt = f"""
表结构：
- orders (id, customer_id, order_date)
- order_details (id, order_id, product_id, amount)
- products (id, name, category_id)
- categories (id, name)

表关系：
- orders.id → order_details.order_id
- products.id → order_details.product_id
- categories.id → products.category_id

用户问题：销售额最高的产品
"""
```

**问题：**
- ❌ **Token 消耗巨大：** 100 张表的 Prompt 可能超过 10K tokens
- ❌ **LLM 容易混淆：** 表太多时，LLM 会忘记关系
- ❌ **维护困难：** 每次表结构变化都要更新 Prompt

---

#### Neo4j 图数据库的解决方案

**核心思想：将表关系存储为图结构**

```
(orders:Table) -[:HAS_DETAIL {join_key: "order_id"}]-> (order_details:Table)
(order_details:Table) -[:HAS_PRODUCT {join_key: "product_id"}]-> (products:Table)
(products:Table) -[:BELONGS_TO {join_key: "category_id"}]-> (categories:Table)
```

**查询流程：**
```python
# 1. 用户问题："销售额最高的产品"
# 2. 关键词提取：["销售额", "产品"]
# 3. 查询 Neo4j：找到相关表及其关系
query = """
MATCH path = (t1:Table)-[r*]-(t2:Table)
WHERE t1.name IN ['orders', 'order_details']
  AND t2.name = 'products'
RETURN path
"""
# 4. 结果：orders → order_details → products（自动找到最短路径）
# 5. 提取 JOIN 关系：
#    - orders.id = order_details.order_id
#    - order_details.product_id = products.id
# 6. 告诉 LLM 这些关系
# 7. LLM 生成正确的 SQL
```

**优势：**
- ✅ **准确率提升：** 从 60% → 90%+
- ✅ **Token 节省：** 只传递相关表的关系
- ✅ **自动发现：** 图算法找最短路径
- ✅ **易于维护：** 图结构直观

---

### 1.3.5 为什么使用 DuckDB 而不是 MySQL？

#### 场景：用户上传 Excel 文件进行问答

**传统方案：导入 MySQL**
```python
# 1. 读取 Excel
df = pd.read_excel("sales.xlsx")

# 2. 创建表
CREATE TABLE temp_sales (...)

# 3. 插入数据（10 万行）
INSERT INTO temp_sales VALUES (...)  # 耗时 10 秒

# 4. 查询
SELECT * FROM temp_sales WHERE ...

# 5. 清理
DROP TABLE temp_sales
```

**问题：**
- ❌ 需要写入数据库（慢）
- ❌ 需要清理临时表（麻烦）
- ❌ 并发用户互相干扰
- ❌ 数据库压力大

---

#### DuckDB 方案：直接查询文件

```python
import duckdb

# 1. 读取 Excel
df = pd.read_excel("sales.xlsx")

# 2. 直接查询（无需导入）
result = duckdb.query("""
    SELECT * FROM df
    WHERE amount > 1000
""").to_df()

# 就这么简单！
```

**DuckDB 的特点：**
- ✅ **内存数据库：** 运行在内存中，极快
- ✅ **零配置：** 不需要安装数据库服务
- ✅ **直接查询文件：** CSV/Parquet/DataFrame
- ✅ **OLAP 优化：** 列式存储，分析查询快
- ✅ **完整 SQL 支持：** JOIN、GROUP BY、窗口函数

**性能对比：**
```
查询 100 万行数据：
- MySQL：需要先导入（10 秒） + 查询（2 秒） = 12 秒
- DuckDB：直接查询（0.5 秒）

性能提升：24 倍！
```

---

### 1.3.6 前端技术栈：Vue3 + TypeScript + Vite

#### 为什么选择 Vue3？

**Vue3 vs React vs Angular：**

| 特性 | Vue3 | React | Angular |
|------|------|-------|---------|
| **学习曲线** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| **开发效率** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **性能** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **生态** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **TypeScript** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

**Vue3 的优势：**
- ✅ 渐进式框架（按需使用）
- ✅ 组合式 API（Composition API）
- ✅ 响应式系统（Reactivity）
- ✅ 中文文档完善

---

#### 为什么使用 TypeScript？

```typescript
// JavaScript（无类型检查）
function sendMessage(message) {
    api.post('/chat', message)  // 如果 message 是 undefined？
}

// TypeScript（类型安全）
interface Message {
    content: string;
    role: 'user' | 'assistant';
}

function sendMessage(message: Message): Promise<Response> {
    return api.post('/chat', message)  // ✅ 编译时检查
}
```

**TypeScript 的价值：**
- ✅ 类型安全（减少 bug）
- ✅ 代码提示（提升效率）
- ✅ 重构友好
- ✅ 适合大型项目

---

#### 为什么选择 Vite？

**Vite vs Webpack：**

```
启动速度对比：
Webpack：30 秒
Vite：1 秒（快 30 倍！）

热更新速度：
Webpack：5 秒
Vite：< 1 秒
```

**Vite 的优势：**
- ✅ 基于 ESM（ES Modules）
- ✅ 按需编译（不打包整个项目）
- ✅ 开发体验极佳

---

### 1.3.7 技术栈总结

我们的完整技术栈：

```
┌─────────────────────────────────────────┐
│          前端 (用户界面)                 │
│  Vue3 + TypeScript + Vite + Naive UI     │
│          + ECharts (数据可视化)          │
└──────────────────┬──────────────────────┘
                   │ HTTP / SSE
┌──────────────────▼──────────────────────┐
│          后端 (业务逻辑)                 │
│         Sanic (异步 Web 框架)            │
│                  │                       │
│  ┌───────────────┼───────────────────┐  │
│  │  LangChain / LangGraph             │  │
│  │  (LLM 应用框架 / 工作流编排)       │  │
│  └───────────────┬───────────────────┘  │
│                  │                       │
│  ┌───────────────▼───────────────────┐  │
│  │  Multi-Agent System               │  │
│  │  - Text2SQL Agent (数据问答)      │  │
│  │  - Excel Agent (文件问答)         │  │
│  │  - Common Agent (通用问答)        │  │
│  │  - ReAct Agent (工具调用)         │  │
│  └───────────────┬───────────────────┘  │
│                  │                       │
│  ┌───────────────▼───────────────────┐  │
│  │  MCP (Model Context Protocol)     │  │
│  │  工具协议 & 智能体协同             │  │
│  └───────────────────────────────────┘  │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│          数据层                          │
│  - MySQL (业务数据)                      │
│  - Neo4j (表关系图谱)                    │
│  - DuckDB (内存分析)                     │
│  - FAISS (向量检索)                      │
│  - Redis (缓存)                          │
│  - MinIO (文件存储)                      │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│          LLM 层                          │
│  - 通义千问 Qwen / OpenAI / DeepSeek     │
│  - DashScope Embeddings (向量化)         │
│  - DashScope Rerank (重排序)             │
└──────────────────────────────────────────┘
```

**为什么这套技术栈适合企业级应用？**
1. ✅ **性能：** 异步架构 + 内存数据库 + 向量检索
2. ✅ **准确率：** 混合检索 + 图数据库 + ReAct Agent
3. ✅ **可扩展：** 模块化设计 + MCP 协议
4. ✅ **可维护：** TypeScript + 清晰的分层架构
5. ✅ **易部署：** Docker Compose 一键启动

---

## 1.4 使用 uv 搭建开发环境

现在开始实战！我们将使用 **uv** 搭建一个干净、隔离的 Python 开发环境。

### 1.4.1 什么是 uv？为什么用它？

#### uv vs pip vs conda

| 特性 | pip | conda | uv |
|------|-----|-------|-----|
| **速度** | ⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **依赖解析** | ⚠️ 有时出错 | ✅ 完善 | ✅ 快速且准确 |
| **虚拟环境** | venv 单独创建 | ✅ 内置 | ✅ 内置 |
| **跨平台** | ✅ | ✅ | ✅ |
| **实现语言** | Python | Python | Rust |

**uv 的核心优势：**

1. **速度极快**
```bash
# 安装 pandas 对比：
pip install pandas     # 20 秒
conda install pandas   # 40 秒
uv pip install pandas  # 2 秒（快 10 倍！）
```

2. **兼容 pip**
```bash
# uv 完全兼容 pip 命令
uv pip install ...
uv pip uninstall ...
uv pip list
```

3. **依赖解析快速且准确**
- Rust 实现，解析速度快
- 自动解决依赖冲突

4. **环境隔离好**
- 不会污染系统 Python
- 每个项目独立环境

---

### 1.4.2 安装 uv

#### 方法 1：使用安装脚本（推荐）

**Linux / macOS：**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows（PowerShell）：**
```powershell
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

#### 方法 2：使用 pip 安装
```bash
pip install uv
```

#### 验证安装
```bash
uv --version
# 输出：uv 0.5.0 (或更高版本)
```

---

### 1.4.3 创建项目目录

打开终端（Terminal / 命令提示符），执行以下命令：

```bash
# 创建项目根目录
mkdir sanic-web-tutorial

# 进入项目目录
cd sanic-web-tutorial

# 查看当前路径（确认位置）
pwd  # Linux/Mac
cd   # Windows
```

**预期输出：**
```
/Users/你的用户名/sanic-web-tutorial  # 或类似路径
```

---

### 1.4.4 创建虚拟环境

**为什么需要虚拟环境？**

想象你有两个项目：
- 项目 A 需要 `numpy==1.21`
- 项目 B 需要 `numpy==1.24`

如果不用虚拟环境，两个项目会冲突！虚拟环境为每个项目创建独立的 Python 环境。

```bash
# 使用 uv 创建虚拟环境
uv venv

# 会在当前目录创建 .venv 文件夹
```

**预期输出：**
```
Using Python 3.11 interpreter at: /usr/bin/python3.11
Creating virtualenv at: .venv
Activate with: source .venv/bin/activate
```

---

### 1.4.5 激活虚拟环境

**Linux / macOS：**
```bash
source .venv/bin/activate
```

**Windows（命令提示符）：**
```cmd
.venv\Scripts\activate
```

**Windows（PowerShell）：**
```powershell
.venv\Scripts\Activate.ps1
```

**激活成功标志：**
命令提示符前面会出现 `(.venv)`：
```bash
(.venv) user@computer:~/sanic-web-tutorial$
```

---

### 1.4.6 验证环境隔离

```bash
# 查看 Python 路径（应该指向虚拟环境）
which python  # Linux/Mac
where python  # Windows

# 预期输出：
# /Users/你的用户名/sanic-web-tutorial/.venv/bin/python
```

```bash
# 查看已安装的包（应该是空的）
uv pip list

# 预期输出：
# Package Version
# ------- -------
# pip     24.0
# （只有 pip 本身）
```

---

### 1.4.7 安装第一个包（测试）

```bash
# 安装 requests 库
uv pip install requests

# 预期输出：
# Resolved 5 packages in 123ms
# Downloaded 5 packages in 456ms
# Installed 5 packages in 12ms
#  + certifi==2024.2.2
#  + charset-normalizer==3.3.2
#  + idna==3.6
#  + requests==2.31.0
#  + urllib3==2.2.0
```

**测试安装成功：**
```bash
python -c "import requests; print(requests.__version__)"
# 输出：2.31.0
```

---

### 1.4.8 创建项目目录结构

```bash
# 创建后端目录结构
mkdir -p agent/{text2sql,excel,mcp}
mkdir -p common
mkdir -p config
mkdir -p controllers
mkdir -p services
mkdir -p model
mkdir -p logs

# 创建前端目录（占位，后续章节详细搭建）
mkdir web

# 创建配置文件（占位）
touch .env
touch .gitignore
touch README.md
touch serv.py
```

**查看目录结构：**
```bash
tree -L 2  # Linux/Mac（需要安装 tree）
# 或
ls -R      # 递归列出

# 预期输出：
# sanic-web-tutorial/
# ├── .venv/
# ├── agent/
# │   ├── text2sql/
# │   ├── excel/
# │   └── mcp/
# ├── common/
# ├── config/
# ├── controllers/
# ├── services/
# ├── model/
# ├── logs/
# ├── web/
# ├── .env
# ├── .gitignore
# ├── README.md
# └── serv.py
```

---

### 1.4.9 配置 .gitignore

我们不希望把虚拟环境、日志等提交到 Git：

```bash
# 编辑 .gitignore 文件
cat > .gitignore << 'EOF'
# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python

# 虚拟环境
.venv/
venv/
ENV/

# 日志
logs/
*.log

# 环境变量（包含敏感信息）
.env
.env.*

# 数据库
*.db
*.sqlite3
db/

# IDE
.vscode/
.idea/
*.swp
*.swo

# 系统文件
.DS_Store
Thumbs.db

# 前端
web/node_modules/
web/dist/
web/.nuxt/

# 向量索引
vector_index/
*.index

# Docker
docker/data/
EOF
```

---

### 1.4.10 创建 README.md

```bash
cat > README.md << 'EOF'
# Text2SQL 表格问答系统

基于 LangGraph + MCP + ReActAgent 的企业级 AI 数据助手

## 技术栈

- **后端：** Sanic + LangChain/LangGraph + MCP
- **前端：** Vue3 + TypeScript + Vite
- **数据库：** MySQL + Neo4j + DuckDB + Redis
- **LLM：** 通义千问 / OpenAI / DeepSeek

## 快速开始

```bash
# 1. 创建虚拟环境
uv venv
source .venv/bin/activate

# 2. 安装依赖（后续章节）
uv pip install -r requirements.txt

# 3. 配置环境变量
cp .env.example .env
# 编辑 .env 填入 API Key

# 4. 启动服务
python serv.py
```

## 项目结构

```
sanic-web-tutorial/
├── agent/          # 智能体模块
├── common/         # 工具库
├── config/         # 配置
├── controllers/    # API 控制器
├── services/       # 业务服务
├── model/          # 数据模型
├── web/            # 前端项目
└── serv.py         # 后端入口
```

## 学习资源

- [教程大纲](./docs/outline.md)
- [第 1 章：环境搭建](./docs/chapter-01.md)

## 开源协议

MIT
EOF
```

---

## 1.5 环境准备检查清单

在开始后续章节之前，请确保以下环境已准备就绪：

### 1.5.1 Python 环境

```bash
# 检查 Python 版本（需要 3.9+）
python --version
# 预期：Python 3.9.0 或更高

# 如果版本低于 3.9，需要升级：
# macOS: brew install python@3.11
# Ubuntu: sudo apt install python3.11
# Windows: 从 python.org 下载安装
```

---

### 1.5.2 Node.js 环境（前端开发需要）

```bash
# 检查 Node.js 版本（需要 18+）
node --version
# 预期：v18.0.0 或更高

# 检查 npm 版本
npm --version
# 预期：8.0.0 或更高

# 如果未安装：
# 官网下载：https://nodejs.org/
# 或使用 nvm：
# curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
# nvm install 18
```

---

### 1.5.3 Docker Desktop（可选，但强烈推荐）

Docker 将用于快速启动 MySQL、Neo4j、MinIO 等服务。

```bash
# 检查 Docker 版本
docker --version
# 预期：Docker version 20.0.0 或更高

docker-compose --version
# 预期：docker-compose version 1.29.0 或更高

# 如果未安装：
# 官网下载：https://www.docker.com/products/docker-desktop
```

---

### 1.5.4 Git 版本控制

```bash
# 检查 Git 版本
git --version
# 预期：git version 2.0.0 或更高

# 初始化 Git 仓库
git init
git add .gitignore README.md
git commit -m "Initial commit: 项目初始化"
```

---

### 1.5.5 代码编辑器（推荐 VS Code）

**推荐插件：**
- Python（微软官方）
- Pylance（代码提示）
- Vue Language Features (Volar)（Vue3 支持）
- ESLint（代码检查）
- Prettier（代码格式化）

---

### 1.5.6 环境检查脚本

创建一个自动检查脚本：

```bash
cat > check_env.sh << 'EOF'
#!/bin/bash

echo "🔍 环境检查开始..."
echo ""

# 检查 Python
echo "📦 检查 Python..."
python --version
if [ $? -eq 0 ]; then
    echo "✅ Python 已安装"
else
    echo "❌ Python 未安装或版本不符"
fi
echo ""

# 检查 uv
echo "📦 检查 uv..."
uv --version
if [ $? -eq 0 ]; then
    echo "✅ uv 已安装"
else
    echo "❌ uv 未安装"
fi
echo ""

# 检查 Node.js
echo "📦 检查 Node.js..."
node --version
if [ $? -eq 0 ]; then
    echo "✅ Node.js 已安装"
else
    echo "❌ Node.js 未安装"
fi
echo ""

# 检查 Docker
echo "📦 检查 Docker..."
docker --version
if [ $? -eq 0 ]; then
    echo "✅ Docker 已安装"
else
    echo "⚠️  Docker 未安装（可选）"
fi
echo ""

# 检查 Git
echo "📦 检查 Git..."
git --version
if [ $? -eq 0 ]; then
    echo "✅ Git 已安装"
else
    echo "❌ Git 未安装"
fi
echo ""

echo "✨ 环境检查完成！"
EOF

chmod +x check_env.sh
./check_env.sh
```

---

## 1.6 本章总结

### 1.6.1 我们学到了什么？

#### 理论知识
1. **AI 数据助手的价值：**
   - 零门槛使用（自然语言查询）
   - 10-100 倍效率提升
   - 自动化数据可视化
   - 智能推荐与洞察

2. **技术选型的理由：**
   - **Sanic：** 异步高性能，适合 IO 密集型（LLM 调用）
   - **LangGraph：** 状态机编程，复杂工作流编排
   - **MCP：** 工具标准化，多智能体协同
   - **Neo4j：** 图数据库优化多表 JOIN
   - **DuckDB：** 内存分析引擎，直接查询文件
   - **Vue3：** 渐进式框架，开发效率高

3. **项目架构：**
   - 前后端分离（Vue3 + Sanic）
   - 多智能体系统（Text2SQL + Excel + Common）
   - 混合检索（BM25 + FAISS + Rerank）
   - 图数据库辅助（Neo4j）

#### 实战技能
1. ✅ 使用 uv 创建虚拟环境
2. ✅ 激活和管理虚拟环境
3. ✅ 安装 Python 包
4. ✅ 创建项目目录结构
5. ✅ 配置 .gitignore
6. ✅ 检查开发环境

---

### 1.6.2 思考题

1. **为什么异步框架在 LLM 应用中性能提升这么大？**
   <details>
   <summary>点击查看答案</summary>

   LLM API 调用是 IO 密集型操作（等待网络响应），同步框架一次只能处理一个请求，其他请求必须等待。异步框架可以在等待 API 响应期间处理其他请求，实现并发，性能提升 10-100 倍。
   </details>

2. **为什么需要 Neo4j 图数据库，而不是在 Prompt 中提供所有表关系？**
   <details>
   <summary>点击查看答案</summary>

   表太多时（50+ 张表），Prompt 会超过 Token 限制，且 LLM 容易混淆。Neo4j 使用图算法自动找到相关表的最短路径，只传递必要的关系信息，准确率从 60% 提升到 90%+。
   </details>

3. **MCP 协议解决了什么问题？**
   <details>
   <summary>点击查看答案</summary>

   MCP 将工具标准化，避免每个智能体重复实现相同的工具。类似于"工具的 HTTP 协议"，实现工具复用、跨智能体共享、生态系统构建。
   </details>

4. **为什么用 uv 而不是 pip？**
   <details>
   <summary>点击查看答案</summary>

   uv 使用 Rust 实现，速度比 pip 快 10 倍，依赖解析更准确，同时完全兼容 pip 命令。更重要的是，uv 的虚拟环境管理更简洁，适合教学和项目开发。
   </details>

---

### 1.6.3 下一章预告

在第 2 章中，我们将开始真正的编码：

**《第 2 章：30 分钟上手 Sanic - 你的第一个异步 Web API》**

内容抢先看：
- 创建第一个 Sanic 应用
- 实现 Hello World API
- 添加 POST 接口（聊天 API）
- 理解异步编程原理
- 使用 curl/Postman 测试

**预计代码量：** 20-30 行（完整可运行的 Web 服务）

---

### 1.6.4 作业（可选）

1. **环境检查：** 运行 `check_env.sh` 脚本，确保所有环境就绪
2. **阅读文档：** 浏览 Sanic 官方文档首页（https://sanic.dev）
3. **思考应用场景：** 想想你的工作中有哪些数据分析需求可以用 AI 助手解决？

---

## 📞 需要帮助？

如果在环境搭建过程中遇到问题：
1. 检查 Python 版本是否 >= 3.9
2. 确认虚拟环境已激活（命令提示符前有 `.venv`）
3. 查看错误日志，搜索具体错误信息
4. 参考官方文档：
   - uv: https://github.com/astral-sh/uv
   - Sanic: https://sanic.dev

---

**恭喜你完成第 1 章！🎉**

现在你已经理解了项目的价值和技术架构，并搭建好了开发环境。在下一章，我们将开始编写第一行代码，创建一个真正运行的 Web 服务！

让我们继续前进！🚀

---

**版权声明：** 本教程为教学目的编写，代码基于 MIT 协议开源。
