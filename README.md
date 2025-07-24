# 🧠 Retrieval Augmented Generation (RAG) with LangChain & IBM Granite

This project demonstrates how to build a **Retrieval-Augmented Generation (RAG)** pipeline using [LangChain](https://www.langchain.com/), IBM Granite models, and Milvus as the vector database. The RAG architecture enhances language models by providing relevant retrieved context from a knowledge base before generating a response.

---

## 📌 Use Cases

- 🧾 **Customer Support**: Answer FAQs from product manuals
- 💼 **Domain-Specific QA**: Legal, financial, or scientific document exploration
- 📰 **News Chat**: Chat about current events using updated articles

---

## 🧰 Tech Stack

- 🧠 LLM: `ibm-granite` models (via Replicate)
- 📚 Embeddings: `granite-embedding-30m-english`
- 🗂️ Vector DB: `Milvus`
- 🧱 Framework: `LangChain`
- 📦 Environment: Python 3.10+ (preferably in a virtual environment)

---

## ⚙️ Setup Instructions

### 1. ✅ Prerequisites

- Python 3.10, 3.11, or 3.12
- [Replicate](https://replicate.com/) API key
- Git, pip

### 2. 📦 Install Dependencies

```bash
pip install git+https://github.com/ibm-granite-community/utils \
    transformers \
    langchain_community \
    'langchain_huggingface[full]' \
    langchain_milvus \
    replicate \
    wget
```

---

## 🚀 Running the Notebook

1. Clone this repo or open `RAG_with_Langchain.ipynb` in Colab/Jupyter.
2. Ensure your Python version is correct:
   ```python
   import sys
   assert sys.version_info >= (3, 10) and sys.version_info < (3, 13)
   ```
3. Install required packages (see above).
4. Set your Replicate API key:
   ```bash
   export REPLICATE_API_TOKEN=your_token_here
   ```
5. Choose your models:
   - **Embeddings**: `ibm-granite/granite-embedding-30m-english`
   - **LLM**: `ibm-granite/granite-3.3-8b-instruct`
6. Use `state_of_the_union.txt` or any other document for indexing of your own.
7. Run the entire notebook to:
   - Load & chunk documents
   - Embed chunks and populate Milvus
   - Build a LangChain RAG pipeline
   - Query with semantic retrieval and get LLM responses

---

## 🧪 Example Query

```python
query = "What did the president say about Ketanji Brown Jackson?"
output = rag_chain.invoke({"input": query})
print(output['answer'])
```

**Output:**
> The president nominated Circuit Court of Appeals Judge Ketanji Brown Jackson to the Supreme Court, praising her legal expertise and bipartisan support.

---

## 🗂️ File Structure

```
.
├── RAG_with_Langchain.ipynb   # Main notebook
├── state_of_the_union.txt     # Example document
└── README.md                  # Project instructions
```

---

## ✅ Tips

- Replace Milvus with any other LangChain-supported vector store (e.g., FAISS, Chroma).
- Replace Replicate + Granite with OpenAI, Cohere, etc., by swapping out the LLM component.
- Add document upload support to dynamically build knowledge bases.

---

## 📄 License

This project is licensed under the MIT License.
