# Power Rangers Analysis

The dataset for this project comes from [Kaggle's Power Rangers Dataset](https://www.kaggle.com/datasets/karetnikovn/power-rangers-dataset/data) (collected by karetnikovn)!

## 1. Dataset Description

The dataset consists of two main files:

- **power_rangers_episodes.csv**: Contains details about individual episodes, such as `episode_title`, `season_title`, `air_date`, `IMDB_rating`, `total_votes`, and `desc` (episode description).
- **power_rangers_seasons.csv**: Contains details about each season, including `season_title`, `season_num`, `number_of_episodes`, `air_date_first_ep`, `air_date_last_ep`, `producer`, and `IMDB_rating`.

This dataset provides valuable insights into the performance and reception of different seasons and episodes of the Power Rangers franchise, which has been a significant part of pop culture since 1993.

## 2. Reason for Choosing the Dataset

The Power Rangers franchise has a rich history spanning over 25 seasons and more than 830 episodes. Analyzing this dataset allows us to uncover trends in audience reception and the evolution of the show over time. By leveraging data visualization techniques, we can present engaging insights into factors influencing a season's popularity, the impact of season duration on viewer reception, and even text-based analysis to explore favorite characters. The structured nature of the dataset makes it ideal for answering these intriguing questions.

## 3. Questions to Answer

### **Question 1: What factors influence a season's popularity?**

- **Why:** Instead of merely identifying the highest-rated seasons, we aim to analyze **what contributes to a season’s popularity** beyond simple IMDb rankings.
- **Plan:**
  - Use the `power_rangers_seasons.csv` dataset.
  - Analyze IMDb ratings in relation to:
    - **Total votes** (to distinguish widely watched seasons from niche favorites).
    - **Number of episodes** (to explore whether longer seasons tend to receive higher or lower ratings).
    - **Gaps between seasons** (to examine if long breaks affect audience interest and reception).
  - Visualize insights using bar charts, scatter plots, and time-series analysis.

### **Question 2: Which characters were the most prominent across seasons?**

- **Why:** Power Rangers has a large and evolving cast. Analyzing which characters were most frequently mentioned can help identify fan favorites and trends over time.
- **Plan:**
  - Use the `power_rangers_episodes.csv` dataset.
  - Perform text analysis on **episode descriptions (`desc`)** to identify frequently mentioned characters.
  - Compare character prominence across seasons and investigate whether popular characters correlate with higher ratings.
  - Visualize character trends using word clouds and frequency plots.

### **Question 3: How does season duration impact audience reception?**

- **Why:** Some seasons run longer than others, and we want to explore whether season length correlates with audience reception.
- **Plan:**
  - Use the `power_rangers_seasons.csv` dataset.
  - Calculate season duration using the difference between `air_date_first_ep` and `air_date_last_ep`.
  - Compare season length to IMDb ratings and total votes to determine if longer seasons are generally better received.

## 4. Plan for Answering the Questions

- **Data Cleaning:**  
  Ensure proper date formats for analysis, handle missing values, and verify the distribution of IMDb ratings.

- **Exploratory Data Analysis (EDA):**  
  Generate summary statistics and initial visualizations to check for trends in ratings, episode numbers, season durations, and character mentions.

- **Data Visualization:**  
  Implement interactive and static visualizations:
  - **Dashboard with Interactive Filters:** Allow users to click on a season to view its performance metrics.
  - **Bar Charts:** Show average IMDb ratings, vote counts per season, and the most frequently mentioned characters.
  - **Scatter Plots:** Compare season duration vs. IMDb rating and total votes.
  - **Time-Series Analysis:** Examine trends in ratings over time and the effect of gaps between seasons.
  - **Word Clouds:** Extract key character mentions from episode descriptions to determine viewer favorites.

- **Insights & Conclusion:**  
Identify key findings about the most popular seasons and season longevity, and provide interpretations on viewer preferences and trends over the years.

This project will provide an engaging and insightful look into the Power Rangers franchise’s reception over the years by combining data analysis with interactive and rich visualizations. It will highlight trends in season popularity, audience preferences, and narrative elements through text-based analysis of favorite characters.

