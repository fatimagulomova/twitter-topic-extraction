# 🧠 Topic Modelling on Twitter: U.S. 2024 Election Insights using BERTopic and LDA

This project explores prevalent themes in Twitter discussions related to the 2024 U.S. Presidential Election. Two topic modeling techniques — the traditional Latent Dirichlet Allocation (LDA) and the transformer-based BERTopic — are implemented and compared in terms of performance, coherence, and interpretability.

---

## 📁 Dataset

- **Source**: [Kaggle Dataset – 2024 US Presidential Elections Twitter Data](https://www.kaggle.com/datasets/rohanroy1/2024-us-presidential-elections-twitter-data)
- **Size**: 25,652 tweets
- **Format**: CSV
- **Language**: Filtered to English using `langdetect`

> 📝 *Note: The Twitter API was not used due to scraping limitations. Instead, a publicly available dataset was selected to allow in-depth topic exploration.*

---

## ⚙️ Project Workflow

### 1. Data Preprocessing
- Removal of HTML tags, URLs, mentions, hashtags
- Lowercasing, tokenisation, and lemmatisation (for LDA)
- Stopword filtering (for LDA) and light cleaning (for BERTopic)
- Language filtering to retain only English tweets

### 2. Entity Analysis
- Top **hashtags** and **mentions** extracted and visualized
- Most **active users** and **frequent words** analyzed
- Provided context before deeper semantic modelling

### 3. Topic Modeling
#### BERTopic
- Embedding Model: `all-MiniLM-L6-v2`
- UMAP: 40 components, `min_dist=0.01`, `n_neighbors=20`
- HDBSCAN: `min_cluster_size=90`, `min_samples=50`
- Topic Reduction: Reduced to 15 final topics
- Keyword Extraction: c-TF-IDF with `bm25_weighting=True`
- Output: Representative tweets and topic summaries

#### LDA
- Vectorisation: Bag-of-Words using Gensim
- Number of Topics: 15
- Training: `passes=40`, `alpha='auto'`, `eta='auto'`
- Output: Top 10 keywords per topic, topic distribution plots

---

## 📊 Evaluation

To evaluate topic modeling performance, I compared the two approaches — BERTopic and LDA — using both **coherence scores** and **interpretability**.

### 🔹 Coherence Score

| Model     | Coherence Score | Interpretation |
|-----------|------------------|----------------|
| **BERTopic** | 0.516 ✅ | High coherence — clear, semantically rich topics |
| **LDA**       | 0.420 ✅ | Good — impressive performance for short-form text |

> Coherence scores were calculated using the `c_v` metric from Gensim’s `CoherenceModel`, which evaluates how frequently top topic words appear together in the dataset.

### 🔹 Interpretability and Topic Clarity

- **BERTopic** produced **more specific, focused** clusters using contextual embeddings and clustering algorithms. Example topics included RFK Jr. support, border policy, and religious political discourse.
- **LDA** served as a **strong baseline**, producing broader themes around major figures like Trump, Biden, Kamala Harris, and economic issues. It was less granular but still insightful.

### 🔹 Visualizations

- **BERTopic**: Used UMAP and HDBSCAN to visualise topic distances and top keywords via bar charts.
- **LDA**: Explored via word clouds, topic-word tables, and topic frequency plots.

### ✅ Conclusion

BERTopic emerged as the superior technique for this project, achieving a higher coherence score and generating more nuanced topics. LDA, with a score of 0.42, performed well given the brevity and noise in tweet data and served as a valuable benchmark for validation.

