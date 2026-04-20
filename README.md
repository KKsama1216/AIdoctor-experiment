# AI Doctor: Medical Assistant with RAG and Knowledge Graph

## Project Overview
AI Doctor is an intelligent medical assistant system that integrates Retrieval-Augmented Generation (RAG) with Knowledge Graph reasoning to provide accurate, evidence-based medical information. The system features a hybrid architecture that combines unstructured medical literature retrieval with structured knowledge graph querying, supporting both text and voice interactions through a multimodal interface.

## Key Features
- **Hybrid Knowledge Retrieval**: Combines dense vector search (RAG) with structured knowledge graph querying
- **Multi-modal Interface**: Supports both text and voice input/output
- **Medical Domain Specialization**: Optimized for healthcare applications with medical knowledge graphs
- **Real-time Response**: Average response time of 2.8 seconds
- **High Accuracy**: Achieves 0.9165 F1-Score on MedQA benchmark

## Repository Structure

AIdoctor-experiment/
├── .git/ # Version control
├── pycache/ # Python cache files
├── audio/ # Audio processing modules (STT/TTS)
│ ├── audio_extract.py # Speech-to-text implementation
│ └── audio_generate.py # Text-to-speech implementation
├── client/ # LLM client abstractions
│ ├── init.py
│ ├── clientfactory.py # Factory for LLM clients
│ └── openai_client.py # OpenAI API client
├── config/ # Configuration files
├── data/ # Data storage
├── experiment/ # Experiment scripts and evaluations
├── Internet/ # Web-related modules
├── kg/ # Knowledge graph operations
│ ├── init.py
│ ├── Graph.py # Neo4j graph operations
│ └── queries/ # Cypher query templates
├── knowledge-base/ # Knowledge base files
├── model/ # Machine learning models
│ ├── init.py
│ ├── embedding.py # Text embedding models
│ └── RAG/ # Vector database operations
├── ppt_docx/ # Documentation and presentations
├── qa/ # Question answering modules
│ ├── init.py
│ └── answer_generate.py # Answer generation logic
├── rag/ # RAG implementation
│ ├── init.py
│ ├── rag_chain.py # Main orchestration chain
│ ├── retrieve/ # Document retrieval
│ └── process/ # Query processing
├── rag_eval_env/ # RAG evaluation environment
├── resource/ # Resource files
│
├── .env # Environment variables
├── .env.example # Environment template
├── .gitignore # Git ignore file
├── init.py # Package initialization
├── app.py # Main application entry point
├── env.py # Environment configuration
├── LICENSE # License file
└── requirements.txt # Python dependencies
## Installation

### Prerequisites
- Python 3.9+
- Neo4j Database (for knowledge graph)
- OpenAI API key or other LLM provider credentials

### Setup Instructions

1. **Clone the repository:**
bash
git clone https://github.com/KKsama1216/AIdoctor-experiment.git
cd AIdoctor-experiment
2. **Create and activate virtual environment:**
bash
python -m venv venv
source venv/bin/activate # On Windows: venv\Scripts\activate
3. **Install dependencies:**
bash
pip install -r requirements.txt
4. **Configure environment variables:**
bash
cp .env.example .env
Edit .env with your configuration
5. **Set up Neo4j database:**
- Install and start Neo4j
- Create medical knowledge graph using scripts in `kg/` directory
- Update connection details in `.env`

6. **Set up vector database:**
- Configure your vector database (e.g., FAISS, ChromaDB)
- Populate with medical documents

## Usage

### Running the Application

1. **Start the web interface:**
bash
python app.py
2. **Access the application:**
- Open browser and navigate to `http://localhost:7860`
- Use the Gradio interface for text or voice interactions

### Running Experiments

1. **Evaluate retrieval strategies:**
bash
cd experiment
python evaluate_retrieval.py
2. **Run model comparisons:**
bash
python evaluate_models.py
## Configuration

### Environment Variables
- `NEO4J_URI`: Neo4j database connection URI
- `NEO4J_USER`: Neo4j username
- `NEO4J_PASSWORD`: Neo4j password
- `OPENAI_API_KEY`: OpenAI API key
- `VECTOR_DB_PATH`: Path to vector database
- `MODEL_NAME`: Default LLM model name

### Model Configuration
- LLM providers: OpenAI, ZhipuAI (configured via `client/`)
- Embedding models: Sentence transformers
- Speech models: Whisper (STT), Edge-TTS (TTS)

## Performance
The system has been evaluated on the MedQA dataset with the following results:

| Model/Strategy | Accuracy | Precision | Recall | F1-Score |
|---------------|----------|-----------|--------|----------|
| Knowledge Graph Only | 0.8531 | 0.8999 | 0.7574 | 0.8203 |
| Document RAG Only | 0.8276 | 0.8586 | 0.8822 | 0.8675 |
| **Hybrid (Ours)** | **0.9011** | **0.9212** | **0.9091** | **0.9165** |

| LLM Model | Accuracy | F1-Score |
|-----------|----------|----------|
| GLM-5.1 | 0.90 | 0.8533 |
| **DeepSeek-V3.1-Terminus** | **0.99** | **0.99** |
| Qwen3.5-397B-A17B | 0.91 | 0.91 |

## Development

### Code Style
- Follow PEP 8 guidelines
- Use type hints where possible
- Document functions and classes with docstrings

### Testing
bash
Run unit tests
pytest tests/
Run integration tests
pytest tests/integration/
### Contributing
1. Fork the repository
2. Create a feature branch
3. Commit changes with descriptive messages
4. Submit a pull request


## Acknowledgements
- MedQA dataset for evaluation
- Neo4j for graph database
- LangChain for orchestration framework
- Gradio for web interface
- All open-source libraries used in this project
