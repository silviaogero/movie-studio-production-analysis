# movie-studio-production-analysis
Exploratory data analysis of movie genres, release timings, production budgets and box-office performance to provide strategic recommendations for a new movie studio looking to release their first movie.
# Group 3 Module III Project — Movie Industry Data Analysis

## Project Overview

This project analyzes historical movie industry data to help a new movie studio make evidence-based decisions about **what movies to produce, when to release them, and how to manage production investment**.

The analysis follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework and combines movie financial information with genre and IMDb audience-rating data.

## Business Problem

The new movie studio has limited experience in the movie industry. The goal of this project is to use historical movie data to identify patterns that can improve the studio's chances of commercial success.

The analysis focuses on:

- Box-office performance
- Production budgets
- Return on Investment (ROI)
- Movie genres
- Release timing
- Audience ratings

## Business Questions

The project answers three main questions:

1. **Which movie genres should the new studio consider investing in?**
   - Which genres have historically produced strong returns?
   - Which genres demonstrate higher median ROI?

2. **Which time of the year is best to release movies?**
   - Which release months have the highest average worldwide gross?
   - How does release volume vary by month?

3. **How does production budget relate to movie performance?**
   - Does a higher production budget correspond with higher worldwide gross?
   - Does production budget appear to be related to audience rating?

## Data Sources

The project uses several movie-industry datasets, including:

- **Box Office Mojo movie gross data** — domestic and worldwide gross information.
- **The Numbers movie budget data** — production budgets and release dates.
- **TMDB movie data** — movie information including genres and ratings.
- **Rotten Tomatoes movie information and reviews** — movie and review-related information.
- **IMDb SQLite database** — movie titles, genres, audience ratings, and vote counts.

The IMDb database is queried using SQL and then combined with the financial data for the genre and rating analysis.

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQLite / SQL
- Jupyter Notebook
- CRISP-DM methodology

## Data Preparation

The analysis includes several data preparation steps:

1. Loading the available CSV, TSV, and SQLite data.
2. Inspecting datasets, columns, data types, and sample records.
3. Converting release dates to datetime format.
4. Cleaning financial columns by removing currency symbols and commas.
5. Converting financial values to numeric data types.
6. Creating a `net_profit` feature:

   `Net Profit = Worldwide Gross - Production Budget`

7. Creating an ROI feature:

   `ROI (%) = (Net Profit / Production Budget) × 100`

8. Creating a `loss_or_profit` classification.
9. Joining IMDb movie basics and ratings using `movie_id`.
10. Matching the financial dataset's movie titles with IMDb `primary_title`.
11. Splitting multiple genres and using `explode()` so individual genres can be analyzed separately.

## Analysis and Key Findings

### 1. Release Month Performance

Movies were grouped by release month and compared using their **average worldwide gross**.

The analysis found that:

- **May** had the highest average worldwide gross at approximately **$162.3 million**.
- June and July also showed strong average worldwide gross.
- November and December were identified as strong release periods.
- December had the highest release volume, demonstrating that release volume and average financial performance are not necessarily the same thing.

**Business implication:** Release timing can be considered as part of the studio's launch strategy, alongside competition, marketing, audience demand, genre, and other factors.

### 2. Genre ROI

The analysis uses **median ROI by genre** to reduce the influence of unusually extreme ROI values.

The highest median ROI genres were:

| Rank | Genre | Median ROI |
|---|---|---:|
| 1 | Animation | 179.0% |
| 2 | Mystery | 151.3% |
| 3 | Adventure | 145.3% |
| 4 | Sci-Fi | 138.5% |
| 5 | Comedy | 105.1% |
| 6 | Fantasy | 103.2% |
| 7 | Action | 92.6% |
| 8 | Family | 89.2% |
| 9 | Romance | 87.7% |
| 10 | Music | 74.6% |

**Business implication:** Animation, Mystery, Adventure, and Sci-Fi show particularly strong historical median ROI. However, genre should not be used alone when deciding which projects to fund.

### 3. Production Budget and Movie Performance

The project examines the relationship between production budget and:

- Worldwide gross
- Audience rating

The analysis shows a **positive relationship between production budget and worldwide gross**. In general, movies with larger production budgets tend to generate higher worldwide gross.

However, the relationship is not absolute. Movies with similar budgets can have very different financial outcomes.

The relationship between production budget and audience rating appears **relatively weak**, suggesting that spending more on production does not automatically result in higher audience ratings.

**Business implication:** Production budgets should be **optimized rather than simply maximized**.

## Recommendations

Based on the analysis, the project recommends:

1. **Consider stronger release windows** such as May–July and November–December when planning major releases.
2. **Give greater consideration to high-ROI genres**, particularly Animation, Mystery, Adventure, and Sci-Fi.
3. **Optimize production budgets** according to the expected potential of each movie rather than assuming that a larger budget guarantees greater box-office success.
4. Combine genre, release timing, budget, audience demand, competition, marketing, and other business factors before making investment decisions.

## CRISP-DM Workflow

The project follows this workflow:

**Business Understanding → Data Understanding → Data Preparation → Modeling / Analytical Methods → Evaluation → Recommendations**

## Interactive Dashboard & Presentation

[→ Open Interactive Tableau Dashboard](https://public.tableau.com/app/profile/yahya.osman1735/viz/MovieStudioAnalysisDashboard/Dashboard1?publish=yes)

[→ Open Presentation](https://docs.google.com/presentation/d/1fbNasbkhW25zgj8HHPxtrz-HrqZxOlkseos1WyBo648/edit?slide=id.g3f3f23a2796_2_75#slide=id.g3f3f23a2796_2_75)


## Limitations

- Historical performance does not guarantee future success.
- Audience preferences and industry conditions can change over time.
- Worldwide box-office gross is not the same as true profit because marketing, distribution, and promotional expenses are not included.
- Movies can belong to multiple genres, so a single movie may contribute to more than one genre's results.
- Release timing is only one factor affecting movie performance.
- The production-budget analysis shows an association, not a causal relationship. A larger budget does not guarantee higher revenue or ratings.

## Project Structure

A typical project structure is:

```text
movie-industry-project/
│
├── movie_studio.ipynb
├── README.md
│
└── data/
    ├── bom.movie_gross.csv/
    ├── tmdb.movies.csv/
    ├── tn.movie_budgets.csv/
    ├── rt.movie_info.tsv/
    ├── rt.reviews.tsv/
    └── im.db/
```

> **Note:** The datasets are not included in this README. The notebook expects the data files to be available under the corresponding `data/` directories.

## How to Run the Project

1. Clone or download the project repository.
2. Make sure Python and Jupyter Notebook are installed.
3. Place the required datasets in the `data/` directory using the folder structure expected by the notebook.
4. Open `movie_studio.ipynb`.
5. Run the notebook cells from top to bottom.

### Python Libraries

Install the main required libraries with:

```bash
pip install pandas numpy matplotlib seaborn
```

SQLite support is provided through Python's built-in `sqlite3` module.

## Conclusion

The analysis provides a data-driven starting point for a new movie studio. The strongest opportunities identified are to consider high-performing genres, strategically select release windows, and manage production budgets carefully.

The results should be treated as **historical evidence rather than guarantees of future success**. A final investment decision should combine these findings with current market conditions, audience research, competition, marketing strategy, franchise potential, and other relevant business information.

## Author / Project

**Group 3 — Module III Project**

Movie Industry Data Analysis

## Kanban Board link and description
Task Allocation: The group has divided the 60 project tasks equally among the 6 group members. Each member is responsible for completing 10 tasks, ensuring an equal distribution of workload and accountability. Tasks are assigned sequentially from Task 1 to Task 60. Each member moved their assigned tasks through the Kanban workflow: To Do → In Progress → Completed. Group members communicated regularly, reviewed each other's work, and supported one another where tasks are dependent on previous work.
Kanban Board link https://app.clickup.com/90152682218/v/b/2kyr9gqa-95

