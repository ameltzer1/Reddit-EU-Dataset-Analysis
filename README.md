# Reddit-EU-Dataset-Analysis

## Overview

This project is submitted as part of the DS202W Spring Term Summative. It analyzes two datasets—Reddit Mental Health and EU Parliamentary Debates—to explore document similarity and apply unsupervised learning methods for deriving social insights from text data. The analysis is structured in two parts: document similarity and unsupervised learning.

## Contents

- `reddit-eu-dataset-analysis.ipynb`: Original Jupyter Notebook  
- `reddit-eu-dataset-analysis.qmd`: Quarto version of the analysis  
- `reddit-eu-dataset-analysis.html`: Rendered HTML output  
- `.gitignore`: Prevents large datasets from being tracked by Git

## Datasets Used

### Reddit Mental Health Dataset

Available at: https://www.kaggle.com/datasets/entenam/reddit-mental-health-dataset  
Source:  
Rani, Saima, Khandakar Ahmed, and Sudha Subramani. 2024. “From Posts to Knowledge: Annotating a Pandemic-Era Reddit Dataset to Navigate Mental Health Narratives.” *Applied Sciences*, 14(4). https://doi.org/10.3390/app14041547

Includes posts from five subreddits:
- r/anxiety
- r/depression
- r/mentalhealth
- r/suicidewatch
- r/lonely

Analysis focuses on a labeled subset containing psychological categories: Early Life, Personality, Trauma and Stress, Drug and Alcohol.

### EU Debates Dataset

Available at: https://huggingface.co/datasets/coastalcph/eu_debates  
Source:  
Chalkidis, Ilias, and Stephanie Brandl. 2024. “Llama Meets EU: Investigating the European Political Spectrum Through the Lens of LLMs.” *arXiv preprint*, arXiv:2403.13592. https://arxiv.org/abs/2403.13592

Contains over 87,000 speeches from the European Parliament (2009–2023). Translations are available where the original language is not English.

## Part 1: Document Similarity

### Reddit

- Goal: Explore similarity between mental health categories and subreddit discussions  
- Methods: TF-IDF vectorization, cosine similarity, hierarchical clustering  
- Insight: Shows strong intra-category similarity (e.g., posts in "Trauma and Stress" tend to cluster) and overlaps between subreddits such as r/depression and r/suicidewatch

### EU Debates

- Goal: Compare similarity of political discourse across countries and party groups  
- Methods: Text normalization, TF-IDF, cosine similarity matrices, clustering  
- Insight: Detected ideological alignment across countries and parties; higher similarity found within centrist and progressive groups

## Part 2: Unsupervised Learning

### Research Question (Reddit)

What latent thematic structures exist in Reddit posts labeled by psychological category?

- Features: Preprocessed text (lemmatization, stopword removal), TF-IDF matrix  
- Methods:
  - KMeans clustering
  - Latent Dirichlet Allocation (LDA)
  - UMAP for dimensionality reduction and visualization
- Results: Clusters reflect distinct subthemes like personal history, coping mechanisms, and emotional states

### Research Question (EU Debates)

Can political discourse be grouped based on topic trends over time, independent of party affiliation?

- Features: Speeches filtered by date and country, tokenized and vectorized  
- Methods:
  - Agglomerative clustering
  - LDA topic modeling
  - Temporal analysis by year
- Results: Found that topic clusters evolved with geopolitical events and showed clear thematic divergence over time

## Setup Instructions

Install the required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn tqdm spacy wordcloud langdetect umap-learn
python -m spacy download en_core_web_sm
```

## Converting the Notebook to Quarto

To convert the Jupyter notebook to a Quarto markdown file:

```bash
quarto convert reddit-eu-dataset-analysis.ipynb
```

Ensure the `.qmd` header includes:

```yaml
---
title: "DS202W - Spring Term Summative"
author: 4598
format: html
self-contained: true
jupyter: python3
engine: jupyter
editor:
  render-on-save: true
  preview: true
---
```

After editing, render the `.qmd` to HTML using the "Render" button in VS Code.

## Notes

- Data was sampled due to computational constraints.  
- All code is reproducible from top to bottom.  
- `.gitignore` excludes raw datasets to maintain repository size.  
- This analysis integrates both quantitative metrics and qualitative interpretation.
