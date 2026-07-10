# Enterprise-RAG

## 项目简介

Enterprise-RAG 是一个基于 **LangChain + Chroma + DeepSeek + FastAPI** 实现的企业知识库智能问答系统。

系统能够将企业内部文档进行向量化存储，并结合大语言模型实现 Retrieval-Augmented Generation (RAG)，为用户提供准确、高效的知识问答能力。

本项目采用模块化设计，可作为 AI Agent、企业知识库、智能客服等项目的基础组件。

---

## 项目架构

```
documents
      │
      ▼
Document Loader
      │
      ▼
Text Splitter
      │
      ▼
Embedding(BGE)
      │
      ▼
Chroma Vector Database
      │
      ▼
Similarity Search
      │
      ▼
DeepSeek LLM
      │
      ▼
Answer
```

---

## 技术栈

- Python 3.11
- LangChain
- LangChain OpenAI
- ChromaDB
- HuggingFace Embedding (BAAI/bge-small-zh-v1.5)
- DeepSeek API
- FastAPI
- Uvicorn

---

## 项目目录

```
Enterprise-RAG

├── app.py
├── api.py
├── build_db.py
├── rag.py
├── llm.py
├── config.py
├── requirements.txt
├── README.md
├── .env.example

├── documents/

├── vector_db/

├── utils/
│      loader.py
│      splitter.py
│      logger.py

└── logs/
```

---

## 功能

✅ 文档加载

✅ 文本自动切分

✅ HuggingFace Embedding

✅ Chroma 向量数据库

✅ Top-K 相似度检索

✅ DeepSeek 大模型生成回答

✅ FastAPI REST API

✅ Swagger API 文档

---

## 快速启动

### 1. 创建虚拟环境

```bash
python -m venv venv
```

Windows

```bash
venv\Scripts\activate
```

---

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

---

### 3. 配置环境变量

创建 `.env`

```
DEEPSEEK_API_KEY=你的Key

DEEPSEEK_BASE_URL=https://api.deepseek.com
```

---

### 4. 建立知识库

```bash
python build_db.py
```

---

### 5. 启动 API

```bash
uvicorn api:app --reload
```

浏览器打开：

```
http://127.0.0.1:8000/docs
```

---

## API

### POST

```
/chat
```

Request

```json
{
    "question":"公司请假制度是什么？"
}
```

Response

```json
{
    "question":"公司请假制度是什么？",
    "answer":"员工每年拥有10天带薪年假。"
}
```

---

## RAG 流程

```
User Question
      │
      ▼
Embedding
      │
      ▼
Similarity Search
      │
      ▼
Retrieve Top-K Documents
      │
      ▼
Prompt Construction
      │
      ▼
DeepSeek
      │
      ▼
Answer
```

---

## 项目亮点

- 使用 Chroma 构建企业知识库
- 基于 HuggingFace 中文 Embedding 模型
- DeepSeek API 生成最终回答
- FastAPI 提供 REST API 服务
- 模块化设计，方便扩展 Agent、MCP 等能力

---

## 后续规划

- LangGraph Agent
- MCP Tool Calling
- 多文档知识库
- Docker 部署
- 前端聊天页面

---

## License

MIT
