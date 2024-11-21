# RAG With Cohere

This project implements a question-answering system based on Andrew Ng's article about building a career in AI. The system uses Cohere's language models for embeddings and text generation, along with approximate nearest neighbors (Annoy) for efficient similarity search.

## Features

- Text preprocessing and cleaning
- Semantic search using embeddings
- Question answering based on context
- Configurable search and generation parameters
- Modular and extensible architecture
- Comprehensive test suite with multiple test cases
- Formatted display of results

## Project Structure

```
project_root/
│
├── config/
│   └── config.py           # Configuration parameters
│
├── src/
│   ├── preprocessing/      # Text processing modules
│   │   ├── __init__.py
│   │   └── text_processor.py
│   ├── embeddings/         # Embedding generation
│   │   ├── __init__.py
│   │   └── embedding_handler.py
│   ├── search/            # Search functionality
│   │   ├── __init__.py
│   │   └── search_engine.py
│   ├── qa/                # Question-answering system
│   │   ├── __init__.py
│   │   └── question_answerer.py
│   └── test_cases/        # Test suite
│       ├── __init__.py
│       └── test_suite.py
│
├── data/
│   └── sample_text.py     # Sample article text
│
├── utils/
│   ├── __init__.py
│   ├── env_loader.py      # Environment configuration
│   └── display_formatter.py # Result formatting
│
├── requirements.txt       # Project dependencies
├── main.py               # Main application entry
└── README.md
```

## Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- A Cohere API key (get one at [dashboard.cohere.ai](https://dashboard.cohere.ai))

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd ai-career-qa
```

2. Create and activate a virtual environment:
```bash
# On Unix/macOS
python -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the root directory:
```
COHERE_API_KEY=your_api_key_here
```

## Configuration

The system's behavior can be customized through the `config/config.py` file:

### Search Configuration
- `SEARCH_INDEX_FILENAME`: Name of the file to store the search index
- `NUM_TREES`: Number of trees in the Annoy index (higher = more accurate but slower)
- `NUM_NEIGHBORS`: Number of nearest neighbors to retrieve

### Generation Configuration
- `MAX_TOKENS`: Maximum length of generated answers
- `MODEL_NAME`: Cohere model to use for generation
- `TEMPERATURE`: Generation temperature (higher = more creative)
- `DEFAULT_NUM_GENERATIONS`: Default number of answer variations to generate

### Test Configuration
- `TEST_CONFIGS`: Specific configurations for different types of test cases
  - Technical Skills
  - Project Selection
  - Learning Path

## Components

### TextProcessor
Handles text preprocessing, including:
- Splitting text into paragraphs
- Cleaning and normalizing text

### EmbeddingHandler
Manages text embeddings:
- Generates embeddings using Cohere's API
- Builds and saves search indices

### SearchEngine
Implements semantic search:
- Uses approximate nearest neighbors for efficient similarity search
- Returns relevant context for questions

### QuestionAnswerer
Generates answers:
- Uses retrieved context to answer questions
- Configurable generation parameters
- Multiple answer generation support

### TestSuite
Provides comprehensive testing:
- Multiple test cases covering different aspects
- Configurable test parameters
- Single and multiple generation tests
- Out-of-domain question handling

### DisplayFormatter
Formats and displays results:
- Hierarchical display of test cases
- Configurable output width
- Multiple generation result formatting
- Clean separation between test cases

## Usage

1. Run the main script:
```bash
python main.py
```

2. The system will:
   - Process the input text
   - Generate embeddings
   - Build a search index
   - Run the test suite
   - Display formatted results

3. To use in your own code:
```python
from src.qa.question_answerer import QuestionAnswerer
from utils.display_formatter import DisplayFormatter

# Initialize components
qa_system = QuestionAnswerer(cohere_client, search_engine)
formatter = DisplayFormatter(width=80)

# Generate and format answers
answers = qa_system.generate_answer(
    "Your question here?",
    num_generations=1,
    max_tokens=70,
    temperature=0.5
)

# Display results
formatter.display_test_results([{
    'number': 1,
    'description': "Your Test",
    'question': "Your question here?",
    'results': answers
}])
```

## Test Cases

The system includes several predefined test cases:
1. Single Generation - Side Projects
2. Multiple Generations - Career Building
3. Out of Domain Questions
4. Technical Skills Assessment
5. Project Selection Guidance
6. Learning Path Recommendations
7. Community Impact Analysis
8. Job Search Specifics

Each test case can be configured with:
- Number of generations
- Maximum tokens
- Temperature
- Model selection
- Display options

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Based on Andrew Ng's article about AI careers
- Uses Cohere's language models
- Implements approximate nearest neighbors using Annoy