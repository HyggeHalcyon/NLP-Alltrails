# NLP-Alltrails

This project delivers a full-fledged sentiment analysis pipeline on Google Play Store reviews of the AllTrails: Hike, Bike & Run app. The goal is to uncover meaningful user insights, analyze sentiment dynamics over time, and provide actionable, data-driven recommendations for product improvement and enhanced user experience.

---

## Project Structure

```bash
.
├── 01-scrap-reviews.ipynb          # Scrapes user reviews from Google Play
├── 02-eda.ipynb                    # Performs exploratory data analysis
├── 03-preprocess.ipynb             # Preprocesses review text for sentiment modeling
├── 04-textblob-sentiment.ipynb     # Sentiment analysis using TextBlob
├── 04-vader-sentiment.ipynb        # Baseline sentiment classification using VADER
```

---
## Tools and Libraries Used

- Python (Jupyter Notebooks)  
- `google-play-scraper` / `play-scraper`  
- `pandas`, `numpy`  
- `matplotlib`, `seaborn`  
- `nltk`, `spaCy`, `contractions`  
- `wordcloud`  
- `vaderSentiment` (baseline sentiment model)  
---

## Workflow

### `01-scrap-reviews.ipynb` - Review Scraping
- Collects user reviews of the AllTrails app from Google Play Store
- Extracts fields includes `reviewId`, `userName`, `content`, `score`, `at`, `appVersion`, etc.  
- Saves the raw dataset in CSV format for subsequent analysis.

### `02-eda.ipynb` - Exploratory Data Analysis (EDA)
- Analyzes review distributions by rating, submission date, and time of day. 
- Visualizes key metrics such as review volume and sentiment trends across versions or updates. 

### `03-preprocess.ipynb` - Sentiment-Aware Text Preprocessing
- Applies sentiment-aware cleaning techniques:
  - Converts to lowercase, removes punctuation, expands contractions
  - Uses `spaCy` for tokenization and lemmatization 
  - Implements negation tagging (e.g., transforming `not good` → `not_good`) 
  - Filters out non-informative stopwords to retain emotive content
- Outputs a `cleaned_content` column for input to sentiment classifiers.

### `04-*sentiment.ipynb` - Sentiment Classification
- TextBlob notebook:
  - Applies TextBlob's polarity and subjectivity scores to each cleaned review
  - Classifies sentiment into positive, neutral, or negative based on polarity thresholds
- VADER notebook:
  - Uses the VADER (Valence Aware Dictionary for sEntiment Reasoning) model for rule-based sentiment scoring
  - Assigns sentiment labels based on VADER’s compound score
---

## Key Insights from Sentiment Analysis

### Positive Sentiment
Across both models, positive reviews consistently highlight the following strengths of the AllTrails app:
- Ease of use: Frequent mentions of “easy”, “navigate”, “use”, and “search” suggest a user-friendly interface.
- Map and route quality: Words like “map”, “route”, “track”, and “accurate” indicate that users appreciate the detailed and reliable trail mapping.
- Outdoor activity support: Terms such as “hike”, “walk”, “explore”, “adventure”, and “travel” point to strong alignment with outdoor enthusiasts’ needs.
- Helpful features: “Information”, “location”, “show”, “list”, “helpful”, and “save” reflect satisfaction with search tools, trail data, and filtering capabilities.

### Negative Sentiment
Negative reviews from both sentiment models converge on a few recurring pain points:
- Paywall frustration: Words like “pay”, “subscription”, “pro version”, “charge”, and “cancel” dominate, indicating strong dissatisfaction with locked features and monetization.
- Offline limitations: Frequent mentions of “offline”, “download”, “without internet”, and “lose” suggest users are frustrated by limited offline functionality.
- Navigation and functionality issues: Terms like “useless”, “issue”, “fail”, “zoom”, “glitch”, “slow”, “freeze”, and “crash” highlight technical or UX problems.
- Account and refund complaints: Mentions of “email”, “support”, “refund”, “cancel”, “uninstall”, and “not work” reflect friction with customer support and cancellation processes.

---
