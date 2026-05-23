# ✈️ Flight Delay Prediction & Airline Operations Analytics
## Predicting Delays & Uncovering Operational Patterns — Airlines Dataset

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python) ![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas) ![XGBoost](https://img.shields.io/badge/XGBoost-Classification-orange) ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?logo=scikit-learn) ![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualisation-11557c)

---

> *Flight delays cost the US aviation industry over $33 billion annually — in direct costs, crew overtime, fuel burn, and lost passenger goodwill. The ability to predict which flights will be delayed before they happen is not just operationally valuable — it is a competitive advantage. This project builds a data-driven delay prediction system and delivers the operational intelligence that airlines, airports, and travel platforms need to reduce delay exposure and improve passenger experience.*

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Analysis Sections](#-analysis-sections)
- [Key Findings](#-key-findings)
- [Model Performance](#-model-performance)
- [Business Applications](#-business-applications)
- [Tools & Libraries](#-tools--libraries)
- [How to Run](#-how-to-run)

---

## 🎯 Overview

Few experiences frustrate travellers more than a delayed flight. And few operational problems frustrate airline executives more than the cascading consequences of a delay — missed connections, crew repositioning costs, gate conflicts, and the reputational damage of persistent on-time performance failures. Yet in most organisations, delay management is still largely reactive: passengers are notified after the delay has already occurred, and recovery actions are improvised rather than planned.

This project takes a proactive, data-driven approach. Using 539,383 US domestic flight records across 18 airlines and 293 airports, it delivers four things: a **comprehensive operational profile** of delay patterns across airlines, airports, routes, days, and times; an **airline performance scorecard** that benchmarks every carrier against the portfolio average; a **predictive model** that scores individual flights for delay risk before departure; and an **operational intelligence layer** that identifies the highest-risk time-route-airline combinations for targeted intervention.

The analytical frameworks applied here are the same ones used by **airline operations research teams, airport capacity planners, and travel technology companies** building intelligent rebooking and disruption management systems.

---

## 📊 Dataset

| Attribute | Details |
|-----------|---------|
| **Source** | [Airlines Dataset to Predict a Delay — Kaggle](https://www.kaggle.com/datasets/jimschacko/airlines-dataset-to-predict-a-delay) |
| **Records** | 539,383 flights |
| **Features** | 9 columns (zero nulls) |
| **Airlines** | 18 US domestic carriers |
| **Airports** | 293 origin/destination airports |
| **Target Variable** | `Delay` — binary (1 = Delayed, 0 = On Time) |
| **Overall Delay Rate** | 44.5% |
| **Key Features** | Airline · Flight number · Origin airport · Destination airport · Day of week · Departure time · Flight length |

---

## 🗂️ Project Structure

```
flight-delay-prediction/
│
├── flight_delay_prediction.ipynb       # Fully executed analysis notebook
├── Airlines.csv                        # Flight delay dataset
│
├── charts/
│   ├── eda_overview.png                # Exploratory operations overview
│   ├── delay_patterns.png              # Delay pattern deep-dive
│   ├── airline_performance.png         # Airline performance scorecard
│   ├── model_evaluation.png            # Prediction model evaluation
│   └── operational_insights.png       # Operational intelligence dashboard
│
└── README.md
```

---

## 🔍 Analysis Sections

### 1️⃣ Exploratory Data Analysis
A comprehensive operational baseline — overall delay distribution (44.5% delayed), airline delay rate ranking from best to worst performer, delay rate by day of week identifying Friday as the highest-risk day, delay rate by departure time band showing evening flights as the riskiest, flight length distribution by delay status, and the top 15 busiest routes by volume.

### 2️⃣ Delay Pattern Deep-Dive
A granular investigation of delay patterns across every operational dimension — a day-of-week × hour-of-day delay heatmap revealing the precise risk landscape across the full weekly schedule, delay rate by flight duration band, the top 15 worst-performing origin airports, the top 15 best-performing origin airports, highest delay rate routes, and an airline volume vs delay rate bubble chart mapping carrier size against operational performance.

### 3️⃣ Airline Performance Dashboard
A comprehensive carrier benchmarking system — on-time performance ranking across all 18 airlines, flight volume by carrier, average flight length comparison, a delay rate heatmap by airline × day of week, a delay rate heatmap by airline × time band, and an AM versus PM performance comparison showing which carriers degrade the most as the day progresses.

### 4️⃣ Feature Engineering & Predictive Modelling
Engineered features include route-level historical delay rate, airline-level historical delay rate, peak hour indicator (17:00–20:00), and high-risk day indicator (Thursday/Friday). Four classifiers are trained and benchmarked — Logistic Regression, Random Forest, Gradient Boosting, and XGBoost — using a stratified 100K sample for computational efficiency.

### 5️⃣ Model Evaluation & Feature Interpretation
ROC curves and AUC comparison for all four models, confusion matrix for the best performer, XGBoost feature importance ranking, Precision-Recall curves, and predicted delay probability distributions showing the separation between on-time and delayed flight populations.

### 6️⃣ Operational Intelligence Dashboard
A delay risk matrix (time band × day of week) for scheduling decisions, most delayed and most on-time routes side by side, model-scored predicted risk by hour of day, stacked on-time vs delayed volume by airline, and predicted delay risk as a function of flight length.

---

## 💡 Key Findings

### 🔴 Southwest Airlines Has a Systemic Delay Problem
> With a delay rate approaching **70%** — nearly double the dataset average — Southwest Airlines is the worst performer by a significant margin. As the highest-volume carrier in the dataset, this represents not just a brand problem but a massive operational cost centre. The combination of high frequency, short-haul routes, and point-to-point network design creates compounding delay cascades throughout the day.

### 🌙 Evening Flights Are the Riskiest — By a Wide Margin
The 17:00–20:00 time band consistently produces the highest delay rates across virtually every airline and route combination. This is the compounding delay effect in action — disruptions from earlier in the day accumulate across the network, and evening flights inherit the consequences. **The single most effective passenger-level delay avoidance strategy is booking morning departures.**

### 📅 Friday is Consistently the Worst Day for On-Time Performance
The combination of peak leisure and business travel demand on Fridays creates a perfect storm for network congestion. Gate conflicts, crew positioning challenges, and above-capacity terminal throughput all converge on Friday afternoons and evenings. Thursday also shows elevated risk, suggesting the pre-weekend travel surge begins on Thursday evening.

### 🛫 Route History is the Strongest Predictive Feature
The historical delay rate of a specific route is more predictive of future delay than the airline identity, day of week, or departure time in isolation. This finding confirms that **infrastructure constraints — runway capacity, gate availability, ATC workload at specific airports — are more deterministic of delay than carrier-level operational quality alone.** Routes serving chronically congested airports (ORD, JFK, LGA, ATX) carry structural delay risk that no airline can fully overcome.

### 🏆 Hawaiian and Mesa Airlines Are the Standout Performers
Hawaiian Airlines (HA) and Mesa Airlines (YV) significantly outperform the field with the lowest delay rates in the dataset. While both operate lower-traffic routes with less congestion exposure, their performance confirms that **operational discipline and route selection strategy meaningfully reduce delay rates** independent of network size.

### ✈️ Short Flights Are Surprisingly Delay-Prone
Flights under one hour show higher delay rates than medium-length flights (1–3 hours). This counterintuitive finding reflects the operational reality of short-haul flying: tight turnaround schedules, high frequency at congested regional airports, and less buffer time in the rotation leave short-haul operations with minimal recovery capacity when disruptions occur.

### 📊 The Day × Hour Risk Matrix is the Operational Planner's Most Valuable Tool
The delay risk heatmap combining day of week and hour of departure reveals that **Friday evenings are 20+ percentage points higher risk than Monday mornings** — a difference with direct, quantifiable implications for schedule construction, crew rostering, and gate allocation planning.

---

## 🤖 Model Performance

| Model | AUC-ROC | Avg Precision | CV AUC (3-fold) |
|-------|---------|--------------|----------------|
| Logistic Regression | ~0.68 | ~0.63 | ~0.68 |
| Random Forest | ~0.72 | ~0.68 | ~0.71 |
| Gradient Boosting | ~0.73 | ~0.69 | ~0.72 |
| **XGBoost** | **~0.73** | **~0.69** | **~0.72** |

**Best performing model: XGBoost**

**Top predictive features (XGBoost importance ranking):**
1. 🛣️ Route Historical Delay Rate
2. ✈️ Airline Historical Delay Rate
3. ⏰ Departure Hour
4. 📏 Flight Length
5. 📅 Day of Week
6. 🏢 Origin Airport (encoded)
7. 🏢 Destination Airport (encoded)
8. 🔢 Airline (encoded)

> **Note on model performance:** An AUC of ~0.73 reflects the inherent difficulty of delay prediction from schedule-level features alone. Flight delays are heavily influenced by real-time factors — weather, mechanical issues, ATC ground stops, crew availability — that are not captured in pre-departure schedule data. Incorporating live weather feeds, NOTAMs, and aircraft rotation tracking as features would materially improve predictive performance.

---

## 💼 Business Applications

**1. 🚦 Pre-Departure Risk Scoring**
Score all departing flights 2–4 hours before scheduled departure using the trained model. Flag flights with predicted delay probability > 0.60 for proactive passenger communication, crew pre-positioning, and gate buffer allocation.

**2. 📅 Intelligent Schedule Construction**
Use the day × hour delay risk matrix to inform seasonal schedule builds — scheduling lower-priority routes in high-risk time windows and protecting premium routes with morning departure slots where possible.

**3. 🔄 Proactive Passenger Rebooking**
For passengers with connections, score inbound flights for delay risk at time of booking. Flag itineraries where the inbound flight has predicted delay probability > 0.55 and the connection window is under 90 minutes — automatically offering alternative connections at booking.

**4. 🏢 Airport Capacity Planning**
Use airport-level delay rate analysis to identify the chronically worst-performing origin airports and target infrastructure investment — additional ground crew, improved gate turnaround procedures, or expanded terminal capacity — at the highest-impact locations.

**5. 📊 Carrier Performance Management**
Deploy the airline × time band heatmap as a standing operational KPI dashboard, enabling operations leadership to monitor day-over-day and week-over-week changes in carrier performance and identify deterioration trends before they become systemic.

---

## 🛠️ Tools & Libraries

| Library | Application |
|---------|------------|
| **Pandas** | Data ingestion, feature engineering, route/airline aggregation across 539K flights |
| **NumPy** | Numerical operations, array manipulations |
| **Matplotlib / Seaborn** | 30+ visualisations across 5 chart panels including heatmaps, ROC curves, bubble charts, and stacked bars |
| **Scikit-learn** | LabelEncoder · StandardScaler · LogisticRegression · RandomForestClassifier · GradientBoostingClassifier · ROC-AUC · Precision-Recall · Confusion Matrix · Cross-Validation |
| **XGBoost** | Gradient boosted tree classifier for delay risk scoring |

---

## ▶️ How to Run

1. Clone the repository and navigate to the project folder
2. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```
3. Place `Airlines.csv` in the same directory as the notebook
4. Open and run the notebook:
```bash
jupyter notebook flight_delay_prediction.ipynb
```

> ✅ All cells are pre-executed with embedded outputs. You can review the complete analysis without re-running a single cell.

---

*Part of a 15-project data analytics portfolio spanning HR analytics, financial forecasting, NLP, e-commerce, supply chain intelligence, public health, real estate prediction, credit risk modelling, and aviation operations.*
