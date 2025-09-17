# NLP Topic Modeling

A Python project implementing topic modeling using NLTK, spaCy, and Gensim packages. This repository contains code for performing NLP data preprocessing and implementing topic modeling using LDA (Latent Dirichlet Allocation) and LSA (Latent Semantic Analysis) algorithms on the ABC News Headlines dataset.

## Overview

This project demonstrates how to:
- Perform NLP data preprocessing on text datasets
- Implement topic modeling using LDA and LSA algorithms
- Visualize topic distributions and relationships
- Generate t-SNE visualizations for topic categories

## Sample Output

t-SNE visualization of topic categories for the ABC News headlines dataset:
![lda_sklearn_gif](https://user-images.githubusercontent.com/8759492/155252613-ad99fa6d-ddf5-4744-9256-2301e068eaca.gif)

## Prerequisites

- Python 3.8+
- Jupyter Notebook
- Required packages: nltk, spacy, gensim, textblob, bokeh, plotly, pyLDAvis

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd NLP_Topic_Modeling
```

2. Install required packages:
```bash
pip install nltk spacy gensim textblob bokeh plotly pyLDAvis
```

3. Download required NLTK data and spaCy models:
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')

# Download spaCy English model
python -m spacy download en_core_web_sm
```

## Usage

1. Open the Jupyter notebook:
```bash
jupyter notebook Topic_Modeling_NLTK_Gensim.ipynb
```

2. Follow the step-by-step instructions and documentation in the notebook

## Docker Instructions

To run this project using Docker:

1. Create a Dockerfile in the project root:
```dockerfile
FROM jupyter/scipy-notebook:latest

# Install additional packages
RUN pip install nltk spacy gensim textblob bokeh plotly pyLDAvis

# Download NLTK data
RUN python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords'); nltk.download('wordnet')"

# Download spaCy model
RUN python -m spacy download en_core_web_sm

# Copy notebook files
COPY *.ipynb /home/jovyan/work/

# Set working directory
WORKDIR /home/jovyan/work

# Expose Jupyter port
EXPOSE 8888

# Start Jupyter
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
```

2. Build the Docker image:
```bash
docker build -t nlp-topic-modeling .
```

3. Run the container:
```bash
docker run -p 8888:8888 nlp-topic-modeling
```

4. Access Jupyter notebook at `http://localhost:8888`

## Additional Resources

For more detailed implementation information, see the blog post: [Topic Modeling in Python](https://philippeheitzmann.com/2022/02/topic-modeling-in-python/)

## Dataset

This project uses the ABC News Headlines dataset from Kaggle. The dataset contains news headlines that are preprocessed and used for topic modeling analysis.
