# 🎃 Tidy Tuesday Horror Movies 🎬
**Author:** Jabir Ghaffar  
**Date:** November 1, 2022

Welcome to my exploration of horror movie data! This project analyzes the popularity, revenue, and genres of horror films. If you're a fan of horror movies or data analysis, this might pique your interest!

The data is sourced from the [TidyTuesday project](https://github.com/rfordatascience/tidytuesday/tree/master/data/2022/2022-11-01).

---

## 📊 Data Overview

The dataset provides insights into horror movies, their genres, and their financial performance. As a horror fan looking to find interesting films, I used this dataset to analyze which movies are both financially successful and popular among viewers.

### Key Variables:
- **Title:** Name of the movie
- **Revenue:** Total earnings
- **Popularity:** A metric of how well-liked the movie is
- **Genres:** Categories of horror (e.g., thriller, supernatural, etc.)

---

## 🛠️ Packages Used

- **tidyverse:** For data wrangling and visualization
- **janitor:** For cleaning the dataset

```r
# Load necessary packages
library(tidyverse)
library(janitor)
library(thematic)
```

---

## 🔎 Explorations & Visualizations

### 1. 💵 Which Movie Made the Most Money?

Initial exploration showed that **"IT"** grossed the highest revenue. However, after filtering strictly for horror movies, **"The Exorcist"** emerged as the top horror film in terms of revenue.

```r
# Top 6 Horror Movies by Revenue
horrordf |> 
  select(title, revenue, genre_names) |> 
  filter(genre_names %in% c("Horror")) |> 
  arrange(desc(revenue)) |> 
  head() |> 
  ggplot(aes(x = title, y = revenue)) +
  geom_bar(stat = "identity", fill = "#104E8B") +
  labs(title = "Top 6 Horror Movies", subtitle = "In The Horror Genre") +
  theme_dark()
```

### 2. 🔥 Most Popular Horror Movies

Popularity doesn't always correlate with revenue. Movies that gross highly aren't necessarily the most popular according to this dataset.

```r
# Scatterplot comparing revenue and popularity
horrordf |> 
  ggplot(aes(x = revenue, y = popularity)) +
  geom_point() +
  labs(title = "Revenue vs Popularity", x = "Revenue", y = "Popularity")
```

### 3. 🏗️ Do Large Budgets Equal Large Revenues?

I explored whether high-budget films tend to make more money. Surprisingly, lower-budget films like **"IT"** managed to outperform higher-budget films like **"World War Z."**

```r
# Relationship between budget and revenue
horrordf |> 
  select(title, budget, revenue) |> 
  arrange(desc(revenue)) |> 
  top_n(20) |> 
  ggplot(aes(x = title, y = revenue, color = budget)) +
  geom_point() +
  theme(axis.text.x = element_text(angle = 45, vjust = 1, hjust = 1)) +
  labs(title = "Top 20 Movies by Revenue & Budget")
```

---

## 📚 Key Findings

1. **Revenue ≠ Popularity:** High-grossing films aren't always the most popular.
2. **Budget isn't everything:** Some lower-budget films outperform in revenue.
3. **Genre insights:** Certain genres (like thrillers) blur the lines between horror and other categories.

---

## 🚀 Conclusion

This project helped me explore the trends and characteristics of horror movies in terms of financial success and popularity. It also solidified my understanding of R, especially in terms of data visualization and wrangling using the `tidyverse` package. I'm excited to continue using this knowledge to explore more datasets!

---

### 📂 Repository Structure
- `horror_movies.csv`: Dataset file
- `horror_movies_analysis.Rmd`: R Markdown document containing the full analysis
- `README.md`: This file

---

### 👻 Next Steps
I plan to dive deeper into specific horror subgenres and further investigate what makes a horror movie truly successful at the box office.

Feel free to clone the repository and explore the data yourself! 😱
