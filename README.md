# 🎬 Netflix Catalog Exploration

An end-to-end **Data Analytics project** exploring the Netflix content catalog using **Python, Pandas, and Power BI**.

The project focuses on data cleaning, exploratory data analysis (EDA), feature engineering, and interactive dashboard development to understand Netflix's movies and TV shows across **content types, release years, genres, countries, ratings, durations, and content trends**.

---

## 📊 Project Overview

The Netflix catalog contains thousands of movies and TV shows released across different countries, genres, and time periods.

The objective of this project is to transform the raw Netflix catalog into meaningful analytical insights and present them through an interactive **Power BI dashboard**.

### Key Questions

This project explores questions such as:

* How many movies and TV shows are available?
* What proportion of the catalog consists of movies vs. TV shows?
* How has Netflix content changed over the years?
* Which genres appear most frequently?
* Which countries contribute the most content?
* What are the most common content ratings?
* What is the average movie duration?
* How many seasons do TV shows typically have?
* How has the type of content released changed over time?
* How old is content when it is added to Netflix?

---

## 🎯 Project Objectives

* Clean and preprocess the Netflix dataset using Python.
* Handle missing values and inconsistent data.
* Perform exploratory data analysis using Pandas.
* Create useful analytical features.
* Analyze movies and TV shows separately.
* Analyze genres and countries with multi-value fields.
* Build an interactive Power BI dashboard.
* Present meaningful insights through data visualizations.
* Create a reusable analytics workflow suitable for portfolio and GitHub presentation.

---

## 🗂️ Dataset

The project uses the **Netflix Titles dataset** containing information about movies and TV shows available on Netflix.

### Dataset Size

* **Rows:** 8,807
* **Columns:** 12

### Original Columns

| Column         | Description                                 |
| -------------- | ------------------------------------------- |
| `show_id`      | Unique identifier for each title            |
| `type`         | Movie or TV Show                            |
| `title`        | Title name                                  |
| `director`     | Director of the title                       |
| `cast`         | Cast members                                |
| `country`      | Country/countries associated with the title |
| `date_added`   | Date the title was added to Netflix         |
| `release_year` | Original release year                       |
| `rating`       | Content rating                              |
| `duration`     | Movie duration or number of TV seasons      |
| `listed_in`    | Genres/categories                           |
| `description`  | Title description                           |

---

# 🛠️ Tools & Technologies

### Python

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

### Business Intelligence

* Microsoft Power BI
* Power Query
* DAX

### Development & Version Control

* Git
* GitHub

---

# 🔄 Project Workflow

```text
Raw Netflix Dataset
        ↓
Data Cleaning
        ↓
Missing Value Handling
        ↓
Data Transformation
        ↓
Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
Power BI Data Modeling
        ↓
Interactive Dashboard
        ↓
Business Insights
```

---

# 🧹 Data Cleaning & Preprocessing

The raw dataset was processed using **Python and Pandas**.

### Cleaning Steps

* Checked dataset dimensions and data types.
* Checked for duplicate records.
* Removed exact duplicate rows where applicable.
* Standardized text columns by removing unnecessary whitespace.
* Handled missing values.
* Converted `date_added` into a proper date format.
* Extracted year and month information from `date_added`.
* Extracted numerical duration values.
* Identified whether a title was a movie or TV show.
* Prepared the dataset for Power BI analysis.

### Missing Values

The raw dataset contained missing values in several fields, particularly:

* Director
* Cast
* Country
* Date Added
* Rating
* Duration

Missing categorical values were handled using:

```text
Not Available
```

This prevents unnecessary row deletion while keeping missing information identifiable.

---

# ⚙️ Feature Engineering

Additional analytical columns were created from the original dataset.

### Created Features

| Feature          | Description                         |
| ---------------- | ----------------------------------- |
| `year_added`     | Year the title was added to Netflix |
| `month_added`    | Month the title was added           |
| `month_number`   | Numeric month value                 |
| `duration_value` | Numeric duration/seasons            |
| `duration_unit`  | Minutes or Seasons                  |
| `is_movie`       | Binary indicator for movies         |
| `is_tv_show`     | Binary indicator for TV shows       |

These features make the dataset easier to analyze and visualize.

---

# 🔍 Exploratory Data Analysis

The Python notebook contains several levels of analysis.

## 1. Content Type Distribution

Movies and TV shows were compared to understand the overall composition of the Netflix catalog.

The dataset contains:

* **6,131 Movies**
* **2,676 TV Shows**
* **8,807 Total Titles**

Movies therefore represent the larger share of the catalog.

---

## 2. Titles by Release Year

The number of Netflix titles was analyzed across release years to understand how the catalog evolved over time.

This analysis helps identify periods with higher concentrations of Netflix catalog content.

---

## 3. Top Genres

The `listed_in` column contains multiple genres for some titles.

The genre information was separated into individual genre records to analyze the frequency of different genres.

This allows the project to identify the most frequently represented genres in the catalog.

---

## 4. Country Analysis

The `country` field can contain multiple countries for a single title.

The country information was therefore normalized for analytical purposes.

This allows comparison of Netflix content across countries and regions.

---

## 5. Rating Distribution

The project analyzes the distribution of Netflix titles across content ratings such as:

* TV-MA
* TV-14
* PG-13
* R
* PG
* TV-PG
* G

This provides an overview of the types of audiences represented in the catalog.

---

## 6. Movie Duration

Movie duration was extracted as a numerical value to analyze:

* Average movie duration
* Median movie duration
* Distribution of movie lengths

---

## 7. TV Show Seasons

For TV shows, the duration field represents the number of seasons.

The project analyzes:

* Distribution of seasons
* Average number of seasons
* Comparison of TV show lengths

---

## 8. Content Added Over Time

The `date_added` field was used to analyze how Netflix content was added to the platform over the years.

The analysis also compares:

* Movies added by year
* TV shows added by year

---

## 9. Recent Content Analysis

Titles with:

```text
release_year >= 2015
```

were analyzed separately to understand the composition of more recent content.

---

## 10. Content Age at Addition

A new analytical feature was created:

```text
content_age_when_added = year_added - release_year
```

This estimates how many years after release a title was added to the Netflix catalog.

---

# 📊 Power BI Dashboard

An interactive dashboard was developed using **Microsoft Power BI**.

### Dashboard Components

The dashboard includes:

### KPI Cards

* Total Titles
* Total Movies
* Total TV Shows
* Movie Share
* Average Movie Duration

### Visualizations

* Movies vs. TV Shows
* Netflix Titles by Release Year
* Top 10 Genres
* Top Countries
* Netflix Titles by Rating
* Country-based geographic analysis

### Interactive Filters

The dashboard includes filters/slicers for:

* Content Type
* Release Year
* Rating
* Country
* Genre

These allow users to dynamically explore different parts of the Netflix catalog.

---

# 🧮 DAX Measures

The Power BI dashboard uses DAX measures for dynamic calculations.

### Total Titles

```DAX
Total Titles =
COUNTROWS(Netflix)
```

### Total Movies

```DAX
Total Movies =
CALCULATE(
    [Total Titles],
    Netflix[type] = "Movie"
)
```

### Total TV Shows

```DAX
Total TV Shows =
CALCULATE(
    [Total Titles],
    Netflix[type] = "TV Show"
)
```

### Movie Percentage

```DAX
Movie Percentage =
DIVIDE(
    [Total Movies],
    [Total Titles],
    0
)
```

### TV Show Percentage

```DAX
TV Show Percentage =
DIVIDE(
    [Total TV Shows],
    [Total Titles],
    0
)
```

### Average Movie Duration

```DAX
Average Movie Duration =
CALCULATE(
    AVERAGE(Netflix[duration_value]),
    Netflix[type] = "Movie"
)
```

### Average TV Show Seasons

```DAX
Average TV Show Seasons =
CALCULATE(
    AVERAGE(Netflix[duration_value]),
    Netflix[type] = "TV Show"
)
```

# 📌 Key Findings

The analysis identified several important characteristics of the Netflix catalog:

* The dataset contains **8,807 Netflix titles**.
* Movies form the larger portion of the catalog compared with TV shows.
* Netflix content spans a wide range of release years.
* Multiple genres can be associated with a single title.
* Multiple countries can be associated with a single title.
* The catalog contains a broad range of content ratings.
* Movie duration and TV show season counts provide useful measures for comparing content formats.
* Analyzing `year_added` alongside `release_year` provides additional insight into how old content was when it entered the catalog.

> The exact results shown in the Power BI dashboard may change when filters or slicers are applied.

---

# 💡 Analytical Skills Demonstrated

This project demonstrates practical skills in:

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis
* Feature Engineering
* Data Transformation
* Data Visualization
* Power Query
* DAX
* Power BI Dashboard Development
* Data Modeling
* Multi-value Field Normalization
* KPI Development
* Interactive Data Analysis
* GitHub Project Documentation

---

# 📈 Future Improvements

Possible extensions to this project include:

* Analyze Netflix content trends by month and season.
* Build a recommendation system.
* Perform NLP analysis on title descriptions.
* Analyze sentiment in descriptions.
* Create genre similarity analysis.
* Add more advanced DAX calculations.
* Build a predictive model for content trends.
* Add automated data refresh.
* Develop a Streamlit version of the dashboard.
* Integrate additional streaming-platform datasets for comparison.

---

# 🎓 Project Type

**Data Analytics / Business Intelligence Portfolio Project**

### Technologies

`Python` `Pandas` `NumPy` `Matplotlib` `Seaborn` `Power BI` `Power Query` `DAX` `Jupyter` `Git` `GitHub`

---

# 👩‍💻 Author

**Priyanshi Patel**

Aspiring Data Analyst interested in **Data Analytics, Business Intelligence, Python, SQL, and Power BI**.

---

## ⭐ If you found this project useful

Feel free to explore the repository, review the analysis, and provide feedback.
