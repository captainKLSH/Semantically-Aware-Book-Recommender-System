# Semantically-Aware-Book-Recommender-System

Building a book recommender often suffers from the "Long Tail Problem"—thousands of niche categories have sparse data, and metadata often has missing tags. Furthermore, standard recommenders match topics but fail to match the emotional tone (e.g., "dark and gritty" vs. "light and hopeful").

I engineered a multi-stage NLP pipeline to build a content-rich recommendation dashboard:

1. Rigorous EDA & Data Imputation:

- Utilized Seaborn heatmaps and correlation matrices to diagnose patterns of missing data.

- Addressed the "Long Tail" category distribution by pruning low-information features (word length < 25) and dropping low-variance columns.

2. Vector Search Architecture (The "Brain"):

- Implemented LangChain to orchestrate the text processing pipeline.

- Used Text Splitters to chunk book descriptions and converted them into high-dimensional Word Embeddings.

- Built a Vector Database (Hugging Face) to enable semantic search, allowing users to find books based on conceptual similarity rather than just keyword matching.

3. AI-Powered Metadata Enrichment:

- Zero-Shot Classification: To solve the missing category problem, I deployed the bart-large-mnli model. This allowed me to predict and fill in missing genre tags for the original dataset without needing a labeled training set.

- Sentiment Analysis: Integrated the distilroberta model to analyze the emotional tone of book descriptions, adding a "Vibe Filter" to the dashboard so users can filter recommendations based on mood.

**Tech Stack:** Python, LangChain, Hugging Face (Transformers), Seaborn, Vector DBs, Streamlit