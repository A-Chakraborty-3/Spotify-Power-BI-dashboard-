# Spotify-Power-BI-dashboard-
his project presents an interactive Power BI dashboard built using the Spotify Top 50 Global dataset. It visualizes key insights from popular tracks worldwide — including artist performance, song popularity, release trends, and more.
# 🎵 Spotify Top 50 World Dashboard

## 📊 Project Overview
This Power BI dashboard visualizes the **Top 50 Global Spotify Songs**, providing insights into artist performance, song popularity, album trends, and release patterns.  
The dataset includes various song attributes such as popularity, duration, album type, explicit content, and release date.

![Spotify Dashboard Preview](./Screenshot_2025-10-22_203044.png)

---

## 🧾 Dataset Information

**Dataset Name:** `spotify-top-50-world`  
**Columns Used:**
- `date` — The date of chart record
- `position` — Rank of the song on the chart
- `song` — Song title
- `artist` — Artist or band name
- `popularity` — Spotify popularity index (0–100)
- `duration_ms` — Song duration in milliseconds
- `album_type` — Type of album (single, album, compilation)
- `total_tracks` — Total tracks in the album
- `release_date` — Official release date
- `is_explicit` — Explicit content flag (True/False)
- `album_cover_url` — URL of album cover image

---

## 🎯 Key Insights

- **Top 10 Songs Average Popularity:** 92.32  
- **Artist Count:** 342 unique artists  
- **Average Song Duration:** 3.28 minutes  
- **Most Popular Artists:** Taylor Swift, Billie Eilish, Sabrina Carpenter  
- **Explicit vs Non-Explicit Split:** 48.75% Explicit, 51.25% Non-Explicit  
- **Top Release Year:** 2023  
- **Monthly Popularity Trend:** Popularity dips mid-year and peaks again in November–December  

---

## 📈 Dashboard Features

| Section | Visualization | Description |
|----------|----------------|-------------|
| **Song by Artist** | Image card list | Displays songs with artist images |
| **Popularity by Song** | Bar Chart | Compares popularity scores |
| **Songs per Artist** | Horizontal bar chart | Shows artist contribution count |
| **Popularity by Album Type** | Donut chart | Shows average popularity across album types |
| **Explicit vs Non-Explicit** | Donut chart | Distribution of explicit content |
| **Songs by Year** | Pie chart | Distribution of songs based on release year |
| **Average Popularity by Month** | Area chart | Trend of popularity through months |
| **Top 10 Songs Popularity Avg by Month** | Bar chart | Monthly comparison of top 10 averages |

---

## 🧮 Power BI Measures (Key DAX)
Some core measures used:
```DAX
Total Songs = COUNTROWS('spotify-top-50-world')

Unique Artists = DISTINCTCOUNT('spotify-top-50-world'[artist])

Average Popularity = AVERAGE('spotify-top-50-world'[popularity])

Explicit Songs % = 
DIVIDE(
    CALCULATE(COUNTROWS('spotify-top-50-world'), 'spotify-top-50-world'[is_explicit] = TRUE()),
    [Total Songs],
    0
)

Average Duration (min) = AVERAGE('spotify-top-50-world'[duration_ms]) / 60000
