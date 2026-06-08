# Applied Data Science Capstone: SpaceX Falcon 9 Landing Prediction

## Project Overview

This repository contains the final project for the **Applied Data Science Capstone** course. The project analyzes SpaceX Falcon 9 launch data to understand the factors that influence first-stage landing success. The analysis includes data collection, data wrangling, exploratory data analysis, SQL analysis, interactive visualization, dashboard development, and machine learning prediction.

The main objective of this project is to predict whether the Falcon 9 first stage will land successfully. This is important because reusable first-stage boosters can reduce launch costs and provide insight into launch performance patterns.

## Business Problem

SpaceX advertises Falcon 9 launches at a lower cost compared with many traditional providers because the first stage can be reused. However, the cost advantage depends heavily on whether the first stage lands successfully. Therefore, this project investigates historical launch data and builds a machine learning model to predict landing success.

## Project Questions

This project answers the following questions:

1. Which launch site has the highest number of successful launches?
2. Which launch site has the highest launch success rate?
3. What payload ranges are associated with higher or lower success rates?
4. Which orbit types are associated with better landing outcomes?
5. Which booster versions perform best?
6. Can machine learning models predict Falcon 9 first-stage landing success?

## Repository Structure

| File/Folder | Description |
|---|---|
| `README.md` | Main project documentation. |
| `requirements.txt` | Python libraries required to run the notebooks and dashboard. |
| `Applied_Data_Science_Capstone_SpaceX_Presentation.pptx` | Final presentation slide deck for submission. |
| `completed_spacex_data_collection_api_FAST_OFFLINE.ipynb` | Data collection notebook. This version uses local/offline data to avoid repeated SpaceX API timeout issues while preserving the required output structure. |
| `jupyter-labs-webscraping_COMPLETED_FIXED.ipynb` | Web scraping notebook used to collect Falcon 9 launch table data from a web source. |
| `labs-jupyter-spacex-Data_wrangling_COMPLETED_FIXED.ipynb` | Data wrangling notebook used to clean data, handle missing values, create landing outcome labels, and generate `dataset_part_2.csv`. |
| `jupyter-labs-eda-dataviz_COMPLETED_FIXED.ipynb` | Exploratory data analysis notebook using Python visualizations such as scatter plots, bar charts, and line charts. |
| `jupyter-labs-eda-sql-coursera_sqllite_COMPLETED_FIXED.ipynb` | Exploratory data analysis using SQL queries with SQLite. |
| `lab-jupyter-launch-site-location_COMPLETED_FIXED.ipynb` | Folium map notebook used to visualize launch site locations and launch outcomes geographically. |
| `SpaceX-Machine-Learning-Prediction_COMPLETED_FIXED.ipynb` | Predictive analysis notebook using classification models such as Logistic Regression, SVM, Decision Tree, and KNN. |
| `spacex_dash_app_FIXED_DASH3.py` | Plotly Dash dashboard application compatible with newer Dash versions. |
| `spacex_dash_app.py` | Original Plotly Dash dashboard application. |
| `spacex_launch_dash.csv` | Dataset used by the Plotly Dash dashboard. |
| `dataset_part_1.csv` | Output from the data collection stage. |
| `dataset_part_2.csv` | Output from the data wrangling stage. |
| `dataset_part_3.csv` | Final cleaned dataset used for machine learning. |
| `Spacex.csv` | Dataset used for SQL analysis. |
| `spacex_launch_geo.csv` | Dataset used for Folium launch site mapping. |
| `model_results.csv` | Summary of machine learning model performance. |
| `assets/` | Folder for dashboard screenshots, Folium screenshots, EDA figures, and machine learning result screenshots. |

## Workflow Summary

### 1. Data Collection from SpaceX API

The first stage collects launch-related data such as flight number, date, rocket version, payload mass, orbit, launch site, landing outcome, and booster information. A fixed offline version is included to avoid API timeout problems during local execution.

Main output:

```text
dataset_part_1.csv
```

### 2. Data Collection by Web Scraping

The web scraping notebook extracts Falcon 9 launch records from an HTML table. The scraped data supports additional analysis and comparison with API-based data.

Main output:

```text
spacex_web_scraped.csv
```

### 3. Data Wrangling

The data wrangling step cleans the dataset and prepares it for analysis. It includes checking missing values, filtering records, analyzing landing outcomes, and creating a binary `Class` variable:

- `1` = successful landing
- `0` = unsuccessful landing

Main output:

```text
dataset_part_2.csv
```

### 4. Exploratory Data Analysis with Visualization

The EDA visualization notebook explores relationships between launch features and landing success. It includes analysis of:

- Flight number vs. launch site
- Payload mass vs. launch site
- Orbit type vs. success rate
- Flight number vs. orbit type
- Payload mass vs. orbit type
- Launch success trend by year

Main output:

```text
dataset_part_3.csv
```

### 5. Exploratory Data Analysis with SQL

The SQL notebook uses SQLite queries to summarize the launch dataset. It answers questions such as:

- Number of launches by launch site
- Payload mass statistics
- Successful landing outcomes
- Launch records by date
- Booster and mission outcome patterns

Dataset used:

```text
Spacex.csv
```

### 6. Launch Site Mapping with Folium

The Folium notebook visualizes SpaceX launch sites on an interactive map. It marks launch sites and uses map markers to show successful and unsuccessful launches. This step helps identify geographical launch site patterns.

Dataset used:

```text
spacex_launch_geo.csv
```

### 7. Interactive Dashboard with Plotly Dash

The Plotly Dash application provides interactive visual analytics for launch records. The dashboard includes:

- A launch site dropdown menu
- A pie chart showing success distribution
- A payload mass range slider
- A scatter plot showing the relationship between payload and launch outcome

Run file:

```text
spacex_dash_app_FIXED_DASH3.py
```

Dataset used:

```text
spacex_launch_dash.csv
```

### 8. Predictive Analysis with Machine Learning

The machine learning notebook builds classification models to predict Falcon 9 first-stage landing success. The models tested include:

- Logistic Regression
- Support Vector Machine
- Decision Tree
- K-Nearest Neighbors

Based on the saved model summary, Logistic Regression and SVM achieved the highest test accuracy.

| Model | Test Accuracy |
|---|---:|
| Logistic Regression | 0.8333 |
| SVM | 0.8333 |
| Decision Tree | 0.7778 |
| KNN | 0.6111 |

## Main Findings

The analysis shows that launch success is influenced by launch site, payload mass, orbit type, and booster version. Some launch sites and booster versions show stronger success patterns than others. Payload mass also appears to have a relationship with mission outcome, especially when analyzed using the interactive dashboard.

From the model comparison, Logistic Regression and SVM provided the best overall test accuracy among the tested classification models.

## How to Run This Project

### 1. Install Requirements

Open terminal or PowerShell in the project folder, then run:

```bash
pip install -r requirements.txt
```

If that does not work, install the main libraries manually:

```bash
pip install pandas numpy matplotlib seaborn plotly dash folium beautifulsoup4 requests scikit-learn sqlalchemy ipython-sql
```

### 2. Run the Notebooks in Order

Open Jupyter Notebook or JupyterLab and run the notebooks in this order:

```text
1. completed_spacex_data_collection_api_FAST_OFFLINE.ipynb
2. jupyter-labs-webscraping_COMPLETED_FIXED.ipynb
3. labs-jupyter-spacex-Data_wrangling_COMPLETED_FIXED.ipynb
4. jupyter-labs-eda-dataviz_COMPLETED_FIXED.ipynb
5. jupyter-labs-eda-sql-coursera_sqllite_COMPLETED_FIXED.ipynb
6. lab-jupyter-launch-site-location_COMPLETED_FIXED.ipynb
7. SpaceX-Machine-Learning-Prediction_COMPLETED_FIXED.ipynb
```

In each notebook, use:

```text
Kernel > Restart & Run All
```

Then save the notebook after it finishes running.

### 3. Run the Plotly Dash Dashboard

Make sure these two files are in the same folder:

```text
spacex_dash_app_FIXED_DASH3.py
spacex_launch_dash.csv
```

Run the dashboard:

```bash
python spacex_dash_app_FIXED_DASH3.py
```

Or on Windows PowerShell:

```powershell
py .\spacex_dash_app_FIXED_DASH3.py
```

Open the dashboard in the browser:

```text
http://127.0.0.1:8050/
```

## Dashboard Demo Guide

When demonstrating the dashboard:

1. Open the dashboard at `http://127.0.0.1:8050/`.
2. Show the dropdown menu and select `All Sites`.
3. Explain that the pie chart shows the distribution of successful launches by site.
4. Select one specific site, such as `CCAFS SLC 40` or `KSC LC 39A`.
5. Explain that the pie chart changes to show success vs. failure for that selected site.
6. Move the payload slider, for example from `2000` to `6000` kg.
7. Explain that the scatter plot updates to show payload mass, launch outcome, and booster version category.
8. Conclude that the dashboard helps identify launch site, payload, and booster patterns interactively.

## Suggested Screenshots for Submission

Save screenshots in the `assets/` folder:

```text
assets/dashboard_all_sites.png
assets/dashboard_selected_site.png
assets/dashboard_payload_slider.png
assets/folium_map.png
assets/eda_visualization.png
assets/machine_learning_result.png
```

## Final Deliverables

The final submission includes:

1. GitHub repository URL
2. Completed notebooks
3. Plotly Dash dashboard file
4. Final presentation slide deck
5. Dashboard and analysis screenshots
6. Machine learning results

## Author

Created for the Applied Data Science Capstone project.
