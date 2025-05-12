# 📄 Document Q\&A Chatbot with LangChain, Azure AI, and Gradio

This project demonstrates how to build an interactive chatbot that answers questions based on the content of a PowerPoint (`.pptx`) file. It leverages:

* **LangChain** for orchestrating the retrieval-augmented generation (RAG) pipeline.
* **Azure AI Document Intelligence** to extract structured data from documents.
* **Hugging Face Sentence Transformers** for generating embeddings.
* **Gradio** to provide a user-friendly web interface.

---

## 🚀 Features

* **Document Parsing**: Utilizes Azure AI Document Intelligence to extract text from PDF, JPEG/JPG, PNG, BMP, TIFF, HEIF, DOCX, XLSX, PPTX, and HTML files.
* **Semantic Search**: Implements an in-memory vector store for efficient similarity searches.
* **Conversational Interface**: Offers a Gradio-powered chat interface for user interaction.
* **Modular Workflow**: Employs LangGraph's `StateGraph` to manage the RAG pipeline.

---

## 🧰 Installation

Ensure you have Python 3.8 or higher installed. Then, install the required packages:

```bash
pip install --upgrade langchain-text-splitters langchain-community langgraph
pip install "langchain[google-genai]"
pip install langchain-huggingface
pip install langchain-core
pip install azure-ai-documentintelligence
pip install python-dotenv
pip install gradio
```

---

## 🔐 Environment Variables

Create a `.env` file in the project root directory and add the following variables:

```env
LANGSMITH_API_KEY=your_langsmith_api_key
GOOGLE_API_KEY=your_google_api_key
DOCUMENTAI_API_KEY=your_azure_document_intelligence_key
DOCUMENTAI_ENDPOINT=your_azure_document_intelligence_endpoint
```

Replace the placeholder values with your actual API keys and endpoints.

---

## 📂 File Structure

```
.
├── test.pptx                 # The PowerPoint file to be processed
├── .env                      # Environment variables
├── chatbot_notebook.ipynb    # Jupyter Notebook with the implementation
└── README.md                 # Project documentation
```

---

## 🧪 Usage

1. **Prepare the Document**: Place your `.pptx` file in the project directory and name it `test.pptx`.
2. **Run the Notebook**: Open `chatbot_notebook.ipynb` in Jupyter Notebook or VS Code and execute the cells sequentially.
3. **Interact with the Chatbot**: After running the notebook, a Gradio interface will launch. You can ask questions related to the content of your PowerPoint file.

---

## 🧱 Components Overview

* **Document Loader**: Uses `AzureAIDocumentIntelligenceLoader` to extract text from the PowerPoint file.
* **Text Splitter**: Employs `RecursiveCharacterTextSplitter` to divide the extracted text into manageable chunks.
* **Vector Store**: Implements `InMemoryVectorStore` with Hugging Face embeddings to store and retrieve document chunks based on similarity.
* **Prompt Template**: Retrieves a RAG prompt template from LangChain's hub.
* **LangGraph StateGraph**: Defines a two-step pipeline:

  * `retrieve`: Finds relevant document chunks based on the user's question.
  * `generate`: Uses a language model to generate an answer from the retrieved context.
* **Gradio Interface**: Provides a web-based chat interface for user interaction.

---

## 📍 License

This project is licensed under the [MIT License](LICENSE).

---

