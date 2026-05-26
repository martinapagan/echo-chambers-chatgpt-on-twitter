# Echo Chambers in the Online Discussions About ChatGPT: A Twitter-Based Analysis

This repository contains the complete empirical data science pipeline, source code, and methodologies developed for my **Master's Thesis** in *Analytics and Data Science for Economics and Management* at the University of Brescia (A.Y. 2024/2025).

The project implements an advanced computational framework combining **Social Network Analysis (SNA)** and **Natural Language Processing (NLP)** to detect, model, and analyze the formation of online **echo chambers** on Twitter (X) during global discussions surrounding **ChatGPT**.

---

## Project Overview & Research Objective
As digital platforms increasingly centralize public discourse, user behaviors often exhibit strong homophily biases, potentially leading to ideological isolation. This study tracks a massive dataset of Twitter interactions across a continuous observation window of **128 days** to answer a core question: *Do structural echo chambers systematically form and polarize user sentiment when discussing Generative AI?*

The analysis relies on a multi-layered network approach, evaluating interaction structures against mathematically simulated random baselines to provide robust statistical proof of echo chamber dynamics.

---

## Dataset & Structural Graph Dimensions
The social interactions are modeled as directed, weighted graphs across two distinct operational layers:

* **Retweet Network (`Tesi_retweet.ipynb`):** Captures passive information propagation, content amplification, and broadcast influence. It consists of a focused graph structure with **665 nodes** and **524 edges**.
* **Reply Network (`Tesi_reply.ipynb`):** Maps active conversational exchanges, direct discussions, and argumentative threads. This represents a highly complex, massive graph layer consisting of **41,197 nodes** and **34,618 edges**.

---

## Tech Stack & Key Python Libraries
The entire architecture was developed in **Python 3**, featuring highly parallelized text operations and advanced graph computational packages:

* **Social Network Analysis & Graph Theory:** `networkx`, `igraph`, `leidenalg` (Leiden algorithm implementation), `community` (`python-louvain` library for modularity optimization).
* **Natural Language Processing (NLP):** `spacy` (advanced linguistic pipelines), `nltk`, `contractions`, `re` (regular expressions optimized for noisy social media text tokenization and lemmatization).
* **Statistical Processing & Multi-Core Computing:** `pandas`, `numpy`, `multiprocessing` (leveraged to parallelize CPU-bound text mining tasks).
* **Data Visualization & Analytics:** `seaborn` (advanced kernel density and statistical plotting), `matplotlib`.

---

## Methodology & Computational Pipeline

### 1. Advanced Text Pre-processing
Tweets undergo an intensive NLP cleaning pipeline to remove structural noise (URLs, mentions, hashtags), expand text contractions, strip punctuation, and execute parallelized tokenization and lemmatization via `multiprocessing`.

### 2. Topological Community Detection
Unsupervised clustering algorithms (**Louvain** and **Leiden**) are executed on the directed graphs to partition users into highly cohesive topological sub-communities, exposing tightly knit clusters of interacting individuals.

### 3. Statistical Validation via Randomized Control Groups
To rigorously confirm that the detected communities represent genuine behavioral echo chambers rather than random structural artifacts, the empirical graphs are benchmarked against thousands of simulated synthetic baseline models (**Erdős–Rényi** and **Configuration Models**). Statistical distributions are computed for key network metrics:
* **Modularity ($Q$)**
* **Average Clustering Coefficient**
* **Graph Density**
* **Betweenness Centrality**

### 4. Dual-Approach Sentiment Analysis (Hybrid NLP Pipeline)
To ensure robust opinion mining, sentiment extraction is handled through a comparative dual approach:
* **Lexical Baseline (VADER):** Optimized for social media text, slang, and emojis to extract rapid, rule-based valence scores.
* **Deep Learning Transformers (BERT):** A contextual, bidirectional language model utilized to capture complex semantic patterns, shifting contexts, and subtle user perceptions regarding ChatGPT that keywords alone cannot detect.

### 5. Cross-Layer Sentiment Mapping
By combining topological community boundaries with NLP sentiment extraction scores, the pipeline evaluates the distribution and skewness of opinions across independent clusters, evaluating narrative polarization and systemic biases regarding AI technology.
