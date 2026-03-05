# 🌦️ Big Data Weather Analysis with PySpark

**Course:** Cloud Computing
**Assignment:** GSOD Weather Data Analysis using Apache Spark
**Student:** Satarov Kamal (replace with your name if needed)

---

# 📂 Project Structure

```
.
├── 2015/
├── 2016/
├── 2017/
├── 2018/
├── 2019/
├── 2020/
├── 2021/
├── 2022/
├── 2023/
├── 2024/
│
├── sataromk_Spark.ipynb
├── sataromk_results.txt
├── requirements.txt
├── environment.yml
└── README.md
```

Each year folder contains weather datasets for two stations:

| Station         | Location                            |
| --------------- | ----------------------------------- |
| **72429793812** | Cincinnati Municipal Airport        |
| **99495199999** | Sebastian Inlet State Park, Florida |

---

# 🛠️ Environment Setup

### 1️⃣ Install Anaconda

Download and install:

[https://www.anaconda.com](https://www.anaconda.com)

---

### 2️⃣ Create environment

```bash
conda create -n cloudspark python=3.11 -y
conda activate cloudspark
```

---

### 3️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

Main libraries used:

```
pyspark
pandas
numpy
jupyter
```

---

### 4️⃣ Install Apache Spark

Download Spark:

[https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html)

Example used in this project:

```
Spark 4.1.1
Hadoop 3.4
```

Set environment variable:

```bash
export SPARK_HOME=/Users/your_username/spark/spark-4.1.1-bin-hadoop3
```

---

# 🚀 Running the Notebook

Launch Jupyter:

```bash
jupyter notebook
```

Open:

```
sataromk_Spark.ipynb
```

Run cells sequentially.

---

# 📊 Dataset

Data source:

**NCEI Global Surface Summary of the Day (GSOD)**

Each CSV contains daily weather measurements including:

| Column | Description              |
| ------ | ------------------------ |
| TEMP   | Average temperature      |
| MAX    | Maximum temperature      |
| MIN    | Minimum temperature      |
| PRCP   | Precipitation            |
| WDSP   | Wind speed               |
| GUST   | Wind gust                |
| FRSHTT | Weather events indicator |

---

# 🔎 Analysis Tasks

The following analyses were performed using **PySpark**.

---

## 1️⃣ Dataset Count

Count the number of rows for each dataset.

Expected:

```
19 datasets
```

---

## 2️⃣ Hottest Day Per Year

Find the hottest day (`MAX`) for each year.

Example output:

```
YEAR   DATE        MAX
2015   2015-06-12  91.9
2016   2016-07-24  93.9
...
2024   2024-08-30  100.9
```

---

## 3️⃣ Coldest March Day

Find the coldest day (`MIN`) in **March** across all years.

Result:

```
DATE: 2015-03-06
MIN: 3.2°F
```

---

## 4️⃣ Most Precipitation Year

Compute average precipitation per year for each station.

Results:

| Station    | Year | Mean PRCP |
| ---------- | ---- | --------- |
| Cincinnati | 2018 | 0.158     |
| Florida    | 2015 | 0.0       |

---

## 5️⃣ Missing Wind Gust Percentage (2024)

| Station    | Missing GUST |
| ---------- | ------------ |
| Cincinnati | 39.07%       |
| Florida    | 100%         |

---

## 6️⃣ Monthly Temperature Statistics (Cincinnati 2020)

Calculated:

* Mean
* Median
* Mode
* Standard deviation

Example:

```
MONTH  MEAN  MEDIAN  STD  MODE
1      37.95 37.7    8.35 24.7
2      36.59 36.0    7.90 25.9
...
```

---

## 7️⃣ Lowest Wind Chill Days

Wind chill formula used:

```
WC = 35.74 + 0.6215T − 35.75(V^0.16) + 0.4275T(V^0.16)
```

Top 10 lowest wind chill days in **2017** were extracted.

Example:

```
DATE        TEMP   WDSP   WIND_CHILL
2017-01-07  10.5   7.0    -0.41
```

---

## 8️⃣ Extreme Weather Events (Florida)

Decoded the `FRSHTT` column.

Results:

```
FOG: 0
RAIN: 0
SNOW: 0
HAIL: 0
THUNDER: 0
TORNADO: 0
```

---

## 9️⃣ Temperature Prediction

Predicted **maximum temperature for Nov and Dec 2024** using a simple trend model.

```
Prediction formula:
2024 = 2023 + (2023 − 2022)
```

Results:

| Month         | Prediction |
| ------------- | ---------- |
| November 2024 | 84.3°F     |
| December 2024 | 62.0°F     |

---

# ⚠️ Model Limitations

The prediction model uses only two previous years of data. This approach:

* ignores long-term climate trends
* does not capture seasonal variability
* cannot detect anomalies

More advanced models could include:

* Linear Regression
* ARIMA
* Prophet
* LSTM time-series models

---

# 🧠 Technologies Used

| Tool             | Purpose                     |
| ---------------- | --------------------------- |
| PySpark          | Distributed data processing |
| Apache Spark     | Big data engine             |
| Jupyter Notebook | Interactive analysis        |
| Python           | Data analysis               |

---

# 📎 Deliverables

```
sataromk_Spark.ipynb
sataromk_results.txt
README.md
```

---

# 🎯 Learning Outcomes

This project demonstrates:

* Big data processing using Spark
* Data cleaning and transformation
* Distributed analytics
* Basic statistical analysis
* Weather data exploration