# power-rangers-analysis
The dataset for this project comes from Kaggle's Power Rangers Dataset.

## 1. Dataset Description

The dataset for this project comes from Kaggle's Power Rangers Dataset, which includes information about the episodes and seasons of the Power Rangers franchise. The dataset consists of two main files:

- **power_rangers_episodes.csv**: Contains details about individual episodes, such as episode title, season title, air date, IMDb rating, and total votes.
- **power_rangers_seasons.csv**: Contains details about each season, including season title, season number, number of episodes, air dates, producer, and average IMDb rating.

This dataset provides valuable insights into the performance and reception of different seasons and episodes of the Power Rangers franchise—a significant part of pop culture since 1993.

## 2. Reason for Choosing the Dataset

The Power Rangers franchise has a rich history spanning over 25 seasons and more than 830 episodes. Analyzing this dataset can uncover trends in audience reception and the evolution of the show over time. By leveraging data visualization techniques, we can present engaging insights into what made certain seasons or episodes more popular than others. Additionally, the dataset is well-structured, making it ideal for answering interesting questions about viewer preferences, episode ratings, and season longevity.

## 3. Questions to Answer

### **Question 1: What were the most popular seasons based on IMDb ratings?**

- **Why:** Understanding which seasons received the highest audience appreciation can help analyze storytelling trends and overall franchise success.
- **Plan:**
  - Use the `power_rangers_seasons.csv` dataset.
  - Analyze the `IMDB_rating` variable for each season.
  - Visualize the top-rated seasons using a bar chart or ranking plot.
  - (Optional) Merge external IMDb datasets if available for additional audience review metrics.

### **Question 2: Which season lasted the longest on screen, and how does its reception compare to others?**

- **Why:** Some seasons may have had more episodes or longer air times, potentially correlating with their success.
- **Plan:**
  - Use the `power_rangers_seasons.csv` dataset.
  - Calculate the duration between `air_date_first_ep` and `air_date_last_ep`.
  - Compare season longevity with its IMDb rating and number of episodes.
  - Visualize season duration vs. audience reception using a scatter plot or line chart.

## 4. Plan for Answering the Questions

- **Data Cleaning:**  
  Ensure proper date formats for analysis, handle missing values, and verify the distribution of IMDb ratings.

- **Exploratory Data Analysis (EDA):**  
  Generate summary statistics and initial visualizations to check for trends in ratings, episode numbers, and season durations.

- **Data Visualization:**  
  Utilize various plots:
  - **Bar Charts:** To display average IMDb ratings and vote counts per season.
  - **Timeline or Horizontal Bar Charts:** To visualize the duration of each season.
  - **Scatter Plots/Line Charts:** To compare season longevity against audience reception.
  - **Word Clouds (Optional):** For text analysis of episode descriptions (e.g., to assess which ranger might be the "favorite").

- **Insights & Conclusion:**  
  Identify key findings about the most popular seasons and season longevity, and provide interpretations on viewer preferences and trends over the years.

## 5. Potential External Data Sources

- **IMDb API or External Rating Sources:**  
  To supplement user ratings and reviews.
- **Viewer Engagement Metrics:**  
  From streaming platforms (if available).
- **Merchandise Sales Data:**  
  To compare season popularity through additional cultural impact measures.

---

This project will provide an engaging and insightful look into the Power Rangers franchise's reception over the years by combining data analysis with rich visualizations. It will highlight trends in season popularity, episode performance, and even delve into narrative aspects through text analysis.

