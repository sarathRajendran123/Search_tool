## Project Overview

The Smart Course Search Tool is a project aimed at helping users efficiently find educational courses using semantic search. It was developed using Python with a Gradio frontend, FAISS for similarity search, and Hugging Face's Sentence Transformers for embedding generation.

This tool utilizes the following core libraries:
- **Sentence Transformers** for generating embeddings from text.
- **FAISS (Facebook AI Similarity Search)** for efficient similarity-based searching.
- **Gradio** for an interactive, user-friendly web interface.

---

## Features

- **Semantic Search**: Users can input queries in natural language to find courses.
- **Efficient Embedding Storage**: FAISS indexing allows for fast and efficient similarity search, even with large datasets.
- **Interactive Interface**: Built with Gradio, the web app offers an easy-to-use interface for users to search courses by keyword or topic.

---

## Installation

To run this project locally, you'll need to install the following dependencies:
```bash
pip install gradio faiss-cpu sentence-transformers numpy pandas requests beautifulsoup4
```

Ensure `requirements.txt` includes:
```plaintext
gradio
faiss-cpu
sentence-transformers
numpy
pandas
requests
beautifulsoup4
```

## How It Works

1. **Data Collection and Preprocessing**: First, course data (including titles, descriptions, and topics) is collected and preprocessed. 
2. **Embedding Generation**: Using the Sentence Transformers model, embeddings are generated for each course description to capture semantic meaning.
3. **Indexing with FAISS**: The generated embeddings are indexed using FAISS, allowing for efficient similarity search.
4. **Search Functionality**: When a user enters a search query, it is transformed into an embedding, and FAISS retrieves the most similar course embeddings.
5. **Displaying Results**: The Gradio interface displays the retrieved courses, showing the most relevant ones based on the search query.

### Core Code Implementation
The main functionalities include:
- **Embedding generation** using Sentence Transformers.
- **FAISS indexing** for fast similarity searches.
- **Gradio Interface** for user interaction.

```python
from sentence_transformers import SentenceTransformer
import faiss
import numpy as np

# Model initialization
model = SentenceTransformer('all-MiniLM-L6-v2')

# Embedding generation example
def generate_embeddings(courses):
    return model.encode(courses, show_progress_bar=True)

# Index creation using FAISS
def create_faiss_index(embeddings):
    dimension = embeddings.shape[1]
    index = faiss.IndexFlatL2(dimension)
    index.add(embeddings)
    return index
```

---

## Usage

Once the app is deployed on Hugging Face Spaces, it can be accessed via the link provided above. Simply:
1. Enter your search query in the text box.
2. Click **Submit** to retrieve relevant courses.
3. View the results showing the best-matching courses.

Example queries:
- "Machine learning fundamentals"
- "Data science for beginners"
- "Advanced Python programming"

---


## Project Structure

- **app.py**: Contains the main application code, including the Gradio interface and search functionality.
- **requirements.txt**: Specifies the Python dependencies needed for the project.
- **README.md**: (This document) Provides a project overview, usage instructions, and deployment steps.

---

## Future Improvements

Potential enhancements for the Smart Course Search Tool include:
- **Enhanced filtering**: Add filters like course level, duration, and format.
- **Personalized Recommendations**: Use user data to provide personalized course recommendations.
- **Expanded Dataset**: Integrate additional courses from various platforms.

---

## Acknowledgements

- **Hugging Face Spaces** for providing an easy-to-use platform for hosting Gradio applications.
- **Facebook AI** for FAISS, enabling efficient large-scale similarity search.
- **Gradio** for making user interface development straightforward and interactive.

---

## Contact

For questions or feedback, please contact [Sarath Rajendran](mailto:sarath.rajendran.2021@gmail.com).
