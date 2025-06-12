# __Conceptual Overview__

## __Overview of this Document__

This document is intended for users with basic knowledge of R or an interest in music data analysis. It provides the conceptual context needed to explore album rankings using the __MyFavoriteAlbums__ web app, including definitions, architecture, and tools.

### Audience

- __Beginners__ in R who want to explore data visualization through album ratings.
- __End-users__ who want to explore their own ratings using this app.

## __Definitions__

### Specific to this Project

>- **Album**: A set of songs released by an artist.
>- **Album Rating**: A rating assigned to an album by the dataset author.
>- **Album Ranking**: The position of an album relative to others based on its rating.
>- **Year**: The year the dataset author rated the album (not the release year).

**Note**: The default dataset provided is based on the year albums were rated by the author, not their release year.

### General Definitions

- **Web-based App**: An interactive website used for services or data analytics. In this case, the app provides music data visualizations.
- **GitHub**: A version control platform for tracking changes in code and sharing it. You can view and modify the __MyFavoriteAlbums__ source code at [__MyFavoriteAlbums__ GitHub Repository](https://github.com/UW-Example-Student/MyFavoriteAlbums).

## __Key Tools in MyFavoriteAlbums__

### Number One Albums

Select a range of years to see the top-rated album for each year.

**Example**: In 1993, "August and Everything After" was the top-rated album.

### Bands and Artists

Select a specific band or artist to view all related data, including the number of albums ranked and their average rating.

**Example**: For Admiral Fallow, the author ranked 4 albums with an average rating of 7.00.

### Top Albums by Year

View album rankings for a selected year, sorted from highest to lowest rating.

**Example**: In 2006, "The Crane Wife" was ranked number 1.

### Vinyl Records

Displays information on vinyl records owned by the user and highlights records not owned.

**Example**: The app shows "When I Was Born for the Seventh Time" by Cornershop as the top-rated album not owned by the dataset author.

### Band Comparison

Compare two artists or bands to see trends in ratings over the years.

**Example**: Comparing Radiohead and REM reveals their respective album ratings using distinct trend lines.

## Software Architecture Overview

### Goals of the Software

__MyFavoriteAlbums__ takes a dataset of album ratings stored in a CSV file and produces insightful interactive visualizations via a webpage.

### System Components

- **Front-End**: Uses Shiny for rendering, including interactive elements like sliders and dropdowns to update visualizations.
- **Back-End**: Utilizes CSV for data storage and R (with libraries like `dplyr` and `ggplot2`) for data manipulation and visualization.

View source code and logic details at the [__MyFavoriteAlbums__ GitHub Repository](https://github.com/UW-Example-Student/MyFavoriteAlbums).

### System Flow

1. The process begins with an album dataset stored as a CSV file.
2. The dataset is processed using `dplyr` and `ggplot2` for data visualization and filtering.
3. Shiny displays the visualizations with default values.
4. Users modify data by selecting filters, which are updated dynamically using Shiny.

## __Language and Dependencies__

- **R Programming**: For data manipulation, analysis, and building the Shiny interface.
- **Libraries**:
  - `dplyr`: Filters and aggregates data.
  - `shiny`: Enables web-based interactivity.
  - `ggplot2`: Generates data visualizations.
- **Data Format**: CSV (Comma-Separated Values).

