# Medibot: Medical Chatbot

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Flask](https://img.shields.io/badge/Flask-2.0+-lightgrey.svg)
![LangChain](https://img.shields.io/badge/LangChain-0.1+-green.svg)
![Pinecone](https://img.shields.io/badge/Pinecone-VectorDB-orange.svg)
![Groq](https://img.shields.io/badge/Groq-LLM-purple.svg)

A Flask-based medical chatbot that leverages Retrieval-Augmented Generation (RAG) to provide accurate, context-aware answers to medical queries. The bot processes PDF documents, stores embeddings in Pinecone, and uses Groq's LLaMA model for intelligent responses.

## Features

- **Document Processing**: Loads and processes PDF files from the `data/` directory, splitting them into manageable chunks for embedding.
- **Vector Search**: Uses HuggingFace embeddings and Pinecone vector database for efficient similarity search.
- **Conversational AI**: Integrates with Groq's LLaMA model for generating concise, medically relevant answers.
- **Web Interface**: Simple, responsive chat UI built with Bootstrap and jQuery.
- **RAG Pipeline**: Combines retrieval from vector store with generative AI for high-quality Q&A.
- **Environment Management**: Secure API key handling via `.env` file.

## Technologies Used

- **Backend**: Flask (Python web framework)
- **AI/ML**: LangChain, HuggingFace Embeddings, Groq API
- **Vector Database**: Pinecone
- **Frontend**: HTML, CSS (Bootstrap), JavaScript (jQuery)
- **Data Processing**: PyPDF, RecursiveCharacterTextSplitter
- **Other**: dotenv, sentence-transformers

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/CARLOX62/Medical-chatbot.git
   cd medibot
   ```

2. **Create a Virtual Environment** (recommended):
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: env\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Setup

1. **Environment Variables**:
   - Create a `.env` file in the root directory.
   - Add your API keys:
     ```
     PINECONE_API_KEY=your_pinecone_api_key
     GROQ_API_KEY=your_groq_api_key
     ```

2. **Pinecone Index**:
   - Ensure you have a Pinecone account and API key.
   - The app uses an index named "medical-chatbot" with 384 dimensions (cosine metric).
   - Run `store_index.py` to create and populate the index with PDF data:
     ```bash
     python store_index.py
     ```

3. **Data Preparation**:
   - Place your medical PDF files in the `data/` directory (e.g., `Medical_book.pdf`).
   - The system will process and embed the content automatically.

## Usage

1. **Run the Application**:
   ```bash
   python app.py
   ```
   - The app will start on `http://0.0.0.0:5000`.

2. **Access the Chat Interface**:
   - Open your browser and go to `http://localhost:5000`.
   - Type your medical questions in the chat box and receive AI-powered answers.

3. **Testing the API**:
   - Use tools like Postman or curl to test endpoints.
   - Example: `curl -X POST http://localhost:5000/get -d "msg=What is acne?"`

## API Endpoints

- `GET /`: Renders the main chat interface (`chat.html`).
- `POST /get`: Accepts a message (`msg`) and returns the chatbot's response as a string.

## Project Structure

```
medibot/
├── app.py                 # Main Flask application
├── store_index.py         # Script to create and populate Pinecone index
├── requirements.txt       # Python dependencies
├── setup.py               # Package setup
├── .env                   # Environment variables (not committed)
├── data/                  # Directory for PDF files
│   └── Medical_book.pdf
├── src/
│   ├── helper.py          # Utility functions for PDF processing and embeddings
│   └── prompt.py          # System prompt for the LLM
├── templates/
│   └── chat.html          # Chat interface template
├── static/
│   └── style.css          # CSS styles for the UI
├── research/
│   └── trials.ipynb       # Jupyter notebook for experiments
└── README.md              # This file
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [LangChain](https://www.langchain.com/) for AI orchestration.
- Powered by [Pinecone](https://www.pinecone.io/) for vector storage.
- AI responses generated using [Groq](https://groq.com/).
- UI inspired by Bootstrap chat templates.

For any questions or issues, please open an issue on GitHub.
