# __Reference Documentation__

## __Overview of this Document__

This document complements the Conceptual and Task Documentation. It addresses frequently asked questions, outlines the album data structure, describes the app’s key functions, and provides an overview of essential R files powering the application.

### Contents

- FAQ
- Data Structure Reference
- API Reference
- File Overview

---

## __FAQ__

**Q: What is the required format for album data?**  
**A:** Your album ratings must be in **CSV** format, following the exact column names and data types. See the **Data Structure Reference** section for details. You can also refer to the default file located at: `data/album-rankings.csv`.

**Q: My albums aren’t showing up in the app?**  
Check the following:
- Ensure the file name is **exactly** `album-rankings.csv`.
- Confirm that the file path is: `data/album-rankings.csv`.
- Verify that the structure and formatting of your CSV matches the required format.

**Q: How can others view my version of the app?**  
**A:** Make sure your local app is running correctly. Then publish it via Shiny using the provided steps in the Task Documentation. A unique URL will be generated:
```
https://shiny_username.shinyapps.io/MyFavoriteAlbums/
```
Example: [https://loudsandals.shinyapps.io/MyFavoriteAlbums/](https://loudsandals.shinyapps.io/MyFavoriteAlbums/)

**Q: What if I don’t have all the data?**  
**A:** You can leave any column blank. The album may not appear in certain visualizations, but it won't break the app. For example, if the **Year** is blank, the album will be excluded from time-based aggregations.

---

## __Data Structure Reference__

Your CSV file must follow this structure:

| Column Index | Column Name | Description | Type | Example |
|--------------|-------------|-------------|------|---------|
| 1 | Year | Album release year | Integer | 2011 |
| 2 | Rank | Album ranking within the year | Integer | 1 |
| 3 | Album | Name of album | String | "Nostalgia, Ultra" |
| 4 | Artist | Name of the artist or band | String | Frank Ocean |
| 5 | Rating | Album rating (0–10) | Integer | 8 |
| 6 | Vinyl | Mark with `v` if owned on vinyl | Boolean | v |
| 7 | EP | Mark with `EP` if the album is an EP | Boolean | EP |
| 8 | Live | Mark with `Live` if the album is a live recording | Boolean | Live |

> **Note:** For album or artist names containing commas, use quotation marks. E.g., `"Nostalgia, Ultra"`

> **Tip:** Ratings are subjective. Ranks should reflect rating order per year.
---

## __API Reference__

This section documents the functions across different `.R` files used to power the tabs of the app. You can reuse or extend these functions.

### File: `albums_by_band.R`

**`albums_by_bands(band.var)`**  
Pulls all albums by a specific artist.  
**Parameters:** `band.var` (string) — Artist or band name.  
**Returns:** Data frame with `Album`, `Year`, and `Rating`.  
**Example:** `albums_by_bands("Frank Ocean")`

**`band_mean_rating(band.var)`**  
Calculates and prints average rating for a given artist.  
**Parameters:** `band.var` (string)

**`band_album_count(band.var)`**  
Returns the number of albums by an artist.  
**Parameters:** `band.var` (string)

### File: `number_one_albums.R`

**`number_one_album(var.startyear, var.endyear)`**  
Lists top-ranked album for each year in the given range.  
**Parameters:**
- `var.startyear` (int)
- `var.endyear` (int)  
**Returns:** Data frame with `Year`, `Album`, and `Artist`.  
**Example:** `number_one_album(2000, 2020)`

### File: `albums_by_year.R`

**`year_albums(year.var)`**  
Shows all albums from a specific year.  
**Parameters:** `year.var` (int)  
**Returns:** Data frame with `Ranking`, `Album`, and `Artist`.  
**Example:** `year_albums(2023)`

### File: `vinyl.R`

**`missing_vinyl()`**  
Lists highly-rated albums not owned on vinyl.  
**Returns:** Data frame with `Album`, `Artist`, and `Rating`.

**`year_most_vinyl()`**  
Shows years with the most vinyl albums owned.  
**Returns:** Data frame with `Year` and count of owned albums.

### File: `compare_bands.R`

**`band_album_comparison_chart(var.artist1, var.artist2)`**  
Creates a comparison chart of two artists' ratings over time.  
**Parameters:**
- `var.artist1` (string)
- `var.artist2` (string)  
**Returns:** A `ggplot2` chart object.  
**Example:** `band_album_comparison_chart("Frank Ocean", "The Marias")`

---

## __File Overview__

| File Name | Description |
|-----------|-------------|
| `app.R` | Launches the app and connects UI to server logic. |
| `app_ui.R` | Defines the layout and user inputs (5-tab UI). |
| `app_server.R` | Runs the logic for user interaction and updates. |
| `albums_by_band.R` | Functions for artist filtering and statistics. |
| `number_one_albums.R` | Functions for listing top albums by year. |
| `vinyl.R` | Functions related to vinyl ownership insights. |
| `compare_bands.R` | Generates a visual comparison between artists. |
| `albums_by_year.R` | Displays all albums within a selected year. |

---

This reference guide should help you debug, extend, or simply understand the logic behind the MyFavoriteAlbums app. If you're feeling adventurous, dive into the code and try modifying the functions yourself!
