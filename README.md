# 🚦 Indian Road Accident Analysis & Severity Prediction

> End-to-end data science project — EDA, machine learning, and interactive prediction — on a 20,000-record Indian road accident dataset.

---

## Project Overview

Road accidents remain one of the leading causes of preventable deaths in India. This project analyses a synthetic-but-realistic dataset of **20,000 road accidents** across 8 major Indian cities to uncover patterns in accident severity and build a predictive model that estimates severity from observable conditions. An interactive widget lets users explore predictions in real time inside the notebook.

---

## Dataset

| Property | Detail |
|---|---|
| **File** | `indian_roads_dataset.csv` |
| **Data Source** | https://www.kaggle.com/datasets/sehaj1104/indian-road-accident-dataset-20222025 |
| **Rows** | 20,000 |
| **Columns** | 24 |
| **Cities** | Bangalore, Chennai, Chandigarh, Delhi, Hyderabad, Kolkata, Mumbai, Pune |
| **Date range** | 2022 – 2025 |

### Key Columns

| Column | Description |
|---|---|
| `city`, `state` | Location |
| `date`, `time`, `hour`, `day_of_week` | Temporal info |
| `road_type` | `highway` / `urban` / `rural` |
| `weather` | `clear` / `fog` / `rain` |
| `visibility` | `low` / `medium` / `high` |
| `traffic_density` | `low` / `medium` / `high` |
| `lanes` | Number of lanes |
| `vehicles_involved` | Vehicles in the accident |
| `casualties` | People injured/killed |
| `is_peak_hour` | Binary flag |
| `accident_severity` | **Target** — `minor` / `major` / `fatal` |

---

## Technologies

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, manipulation |
| `numpy` | Numerical operations |
| `matplotlib` | Static charts |
| `seaborn` | Statistical visualisations & heatmaps |
| `scikit-learn` | Model training, evaluation, encoding |
| `ipywidgets` | Interactive prediction widget |
| `IPython` | Rich HTML output in Jupyter |

---

## Methodology

### 1. Data Understanding & Cleaning
- Loaded the CSV and inspected shape, dtypes, and descriptive statistics.
- Verified **zero missing values** and **zero duplicate rows**.
- Converted the `date` column from `DD-MM-YYYY` string to `datetime64`.
- Extracted `year` and `month` features for trend analysis.

### 2. Exploratory Data Analysis
Eight focused analyses were conducted:

| # | Analysis |
|---|---|
| 2.1 | Accident severity distribution (bar + pie) |
| 2.2 | Accidents by city and state |
| 2.3 | Accidents by hour of day and day of week |
| 2.4 | Peak vs non-peak hour comparison |
| 2.5 | Weather condition vs severity |
| 2.6 | Road type vs severity |
| 2.7 | Traffic density vs severity |
| 2.8 | Vehicles involved vs casualties (scatter + bar) |
| 2.9 | Monthly trend line + Hour × Day heatmap |

### 3. Severity Prediction
- **Algorithm:** Random Forest Classifier (100 trees, max_depth=10)
- **Features used:** city, weather, road_type, traffic_density, visibility, lanes, vehicles_involved, hour, is_peak_hour, is_weekend
- **Encoding:** `LabelEncoder` for categorical features
- **Split:** 80% train / 20% test (stratified)
- **Evaluation:** Classification report + confusion matrix + feature importance

### 4. Interactive Widget
Built with `ipywidgets`. The user selects:
- City, Weather, Road Type, Traffic Density
- Number of Lanes, Vehicles Involved, Hour, Visibility

And receives a **predicted severity badge** (Minor / Major / Fatal) plus class probabilities rendered as an inline bar chart.

---

## Results

| Metric | Value |
|---|---|
| Model | Random Forest (n=100, depth=10) |
| Test Accuracy | ~85–90% (varies by run) |
| Best-predicted class | `minor` (majority class) |
| Key drivers | `vehicles_involved`, `hour`, `risk_score`, `traffic_density` |

- **Fog** conditions correlate with higher fatal accident rates.
- **Highway** roads have a higher fatal proportion than urban/rural.
- **High traffic density** significantly raises major/fatal risk.
- **Peak hours** (8–10 AM, 5–7 PM) concentrate a disproportionate share of major accidents.

---

## How to Run

### Prerequisites
```bash
pip install -r requirements.txt
```

### Launch
```bash
jupyter notebook indian_roads_analysis.ipynb
```

### Steps inside the notebook
1. Run all cells top-to-bottom (`Kernel → Restart & Run All`).
2. Scroll to **Section 4 — Interactive Widget**.
3. Select your conditions and click **Predict Severity**.

> **Note:** The widget requires a live Jupyter kernel. It will not render in static viewers (nbviewer, GitHub preview).

---

## File Structure

```
Indian Road Accident Dataset/
├── indian_roads_dataset.csv                                  ← raw dataset
├── Pratham_Makhecha_Indian_Roads_Accidents_analysis.ipynb    ← main notebook
├── requirements.txt                                          ← Python dependencies
├── README.md                                                 ← this file
└── Pratham_Makhecha_Indian_road_Accidents_report.docx        ← full project report
```
