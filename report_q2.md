## Question 2: Which characters were the most prominent across seasons?

### Introduction

The Power Rangers franchise is often discussed online with passionate fan takes - claims like “Tommy carries the franchise” or “Rita drove the engagement” frequently appear in fan forums and videos. We wanted to explore whether these assumptions hold up under data scrutiny. Specifically, we asked: **Which characters appear most frequently throughout the series?** And more importantly, **do these characters appear in highly rated episodes?**

To answer this, we used the `power_rangers_episodes.csv` dataset. This file contains episode-level data including descriptions (`desc`), IMDb ratings, total votes, and air dates. We used `desc` for character extraction and combined it with rating information to assess audience reception.

---

### Approach

We applied basic **text analysis** to the `desc` field to identify character names mentioned in each episode. We then calculated:

- **Total number of mentions** for each character across all episodes (to see who appears the most).
- **Average IMDb rating** of the episodes each character appeared in (to gauge quality).
- **Most mentioned character per season**, to highlight changing popularity over time.

To visualize our findings, we used:

1. **Word Cloud** (for character mentions): Helps emphasize character prominence by frequency. Larger words = more mentions.
2. **Table of Top Mentioned Character in Each Season**: Provides a quick overview of which character stood out most per season, offering season-specific insight into character focus.
3. **Bar Plot with Color Mapping** (Top 10 characters by average IMDb rating): Useful for comparing quality scores visually, highlighting the contrast between frequency and audience appreciation.

---

### Analysis

**Word cloud of mentioned characters**
```python
from wordcloud import WordCloud
from collections import Counter
import re, nltk
nltk.download("stopwords")

# Extract capitalized words (likely names) from episode descriptions
word_counter = Counter()
for desc in episodes_df["desc"].dropna():
    words = re.findall(r'\b[A-Z][a-z]+(?:\s[A-Z][a-z]+)?\b', desc)
    word_counter.update(w.lower() for w in words)

# Remove non-character words and generate word cloud
non_chars = {"the", "power rangers", "ranger", "meanwhile"}
char_freq = {w: c for w, c in word_counter.items() if w not in non_chars}
WordCloud(width=800, height=400).generate_from_frequencies(char_freq).to_image()
```
<img width="812" alt="Screenshot 2025-04-02 at 21 06 26" src="https://github.com/user-attachments/assets/be8cfe28-9dcb-473c-9059-22a91ab08efd" />

**Top mentioned character in each season**
```python
# Get top mentioned character per season
season_top_chars = []

for season, group in episodes_df.groupby("season_title"):
    word_counter = Counter()
    for desc in group["desc"].dropna():
        words = re.findall(r'\b[A-Z][a-z]+(?:\s[A-Z][a-z]+)?\b', desc)
        filtered = [w for w in words if w not in ["The", "Power Rangers", "The Rangers", "Meanwhile", "He", "They", "When", "With"]]
        word_counter.update(filtered)
    if word_counter:
        top_char = word_counter.most_common(1)[0][0]
        season_top_chars.append((season, top_char))

season_char_df = pd.DataFrame(season_top_chars, columns=["season", "Most Common Character"])
```
<img width="401" alt="Screenshot 2025-04-02 at 21 07 36" src="https://github.com/user-attachments/assets/f4bc17c4-f8de-4e99-a3c2-9b737a1c49a1" />


**Top popular characters based on IMDB rating**
```python
# Merge most common characters with season IMDb ratings
merged_df = seasons_df.merge(season_char_df, on="season_title")
character_ratings = merged_df.groupby("Most Common Character")["IMDB_rating"].mean().reset_index()

# Bar chart: Top characters by average IMDb rating
sns.barplot(data=character_ratings.sort_values("IMDB_rating", ascending=False).head(10),
            x="Average IMDb Rating", y="Character", palette="viridis")
plt.title("Top 10 Most Popular Characters Based on Season IMDb Ratings")
plt.show()
```
<img width="922" alt="Screenshot 2025-04-02 at 21 07 48" src="https://github.com/user-attachments/assets/1a7495d9-09b7-4a01-bd03-f1c4089b0153" />


### Discussion
The **word cloud** highlights frequently mentioned characters such as **Tommy**, **Rita**, and **Wes**, reflecting their strong presence in the *Power Rangers* universe. Notably, **Tommy** appears in around **4–5 seasons**, far more than most other characters, which explains his prominence in overall mentions. His recurring role across multiple eras has made him a foundational figure in the franchise’s legacy.

When looking at the **most mentioned character per season**, however, the data shows a different focus. Generic mentions like **“Rangers”** dominate many seasons, especially those with strong ensemble casts. But unique names such as **Andros** (*In Space*), **Wes** (*Time Force*), and **Evox** (*Beast Morphers*) indicate seasons where individual characters were more central to the narrative. The **IMDb rating-based character chart** reveals yet another angle. Characters like **Andros**, **Wes**, and **Terra Venture** are associated with the **highest-rated seasons**, despite not being the most frequently mentioned. This implies that critical acclaim is more closely tied to compelling storytelling and character arcs than to mere frequency of appearance.

In summary, while **Tommy’s** recurring presence across multiple seasons solidifies his iconic status—earning him the reputation as the *"carrier"* of the franchise - other characters make a lasting impact through **strong, single-season arcs** that resonate with audiences and critics alike. These insights highlight that while **visibility and nostalgia fuel popularity**, it is **compelling storytelling and character depth** that often lead to **critical acclaim**.
