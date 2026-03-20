# Exploratory Data Analysis (EDA) Notebook

## Overview

This notebook provides a comprehensive guide to **Exploratory Data Analysis (EDA)** — a foundational step in any data science workflow. EDA involves summarizing, visualizing, and understanding the key characteristics of a dataset before building models or drawing conclusions. The notebook walks through the EDA process on two real-world datasets, demonstrating practical techniques for handling messy data.

---

## Datasets Used

### 1. Titanic Dataset
- **Source:** [datasciencedojo/datasets on GitHub](https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv)
- **Description:** Passenger records from the Titanic disaster, including demographic and ticket information. A classic dataset known for missing values and mixed feature types.

### 2. California Housing Prices Dataset
- **Source:** [ageron/handson-ml2 on GitHub](https://raw.githubusercontent.com/ageron/handson-ml2/master/datasets/housing/housing.csv)
- **Description:** Residential housing data from California, featuring geographic, demographic, and property-level attributes.

---

## EDA Steps Covered

Both datasets follow the same structured EDA pipeline:

1. **Loading the Data** — Reading CSV files into pandas DataFrames
2. **Initial Data Inspection** — Reviewing shape, data types, and basic structure with `.info()`
3. **Summary Statistics** — Generating descriptive stats for both numerical and categorical features using `.describe()`
4. **Missing Values Analysis** — Identifying null values and visualizing them with a heatmap
5. **Data Cleaning** — Imputing missing values (median for numerical, mode for categorical) and dropping high-null columns
6. **Data Visualization** — Creating multiple chart types to reveal patterns and relationships

---

## Visualizations Included

### Titanic Dataset
- Count plot: Passenger survival distribution
- Bar chart: Passenger class distribution
- Histogram: Age distribution with KDE
- Bar plots: Survival rate by passenger class and by sex
- Side-by-side count plots: Male vs. female survival counts
- Class-level survival breakdown: Separate plots per class (1st, 2nd, 3rd)
- Box plots: Age and fare distributions by class and survival status
- Correlation heatmap: Relationships among numerical features

### California Housing Dataset
- Count plot: Ocean proximity categories
- Box plot: Median house value by ocean proximity
- Scatter plot: Population vs. total bedrooms
- Bar plots: Housing median age, total bedrooms, and population by ocean proximity
- Engineered feature: Total rooms per household by ocean proximity
- Correlation heatmap: Relationships among all numerical features

---

## Libraries & Dependencies

```python
pandas
numpy
matplotlib
seaborn
```

Install with:
```bash
pip install pandas numpy matplotlib seaborn
```

---

## How to Run

1. Open the notebook in [Google Colab](https://colab.research.google.com/) or Jupyter Notebook.
2. Run all cells from top to bottom.
3. Datasets are loaded directly from public GitHub URLs — no manual download required.

---

## Key Concepts Demonstrated

- Handling missing data through imputation and column removal
- Understanding distributions using histograms, box plots, and KDE curves
- Comparing groups with count plots and bar charts
- Exploring feature relationships with scatter plots and correlation heatmaps
- Feature engineering (e.g., total rooms per household)

---

## Author

**Viena Atieno Ouma**
BSc Software Engineering, Murang'a University of Technology
GitHub: [cybertech-lakewood](https://github.com/cybertech-lakewood) | LinkedIn: [viena-ouma](https://www.linkedin.com/in/viena-ouma)
