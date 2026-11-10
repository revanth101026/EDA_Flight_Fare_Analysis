# ✈️ Flight Fare Analysis using Exploratory Data Analysis

An end-to-end EDA project that scrapes live flight fare data from IRCTC Air and
analyzes what drives ticket prices across Indian domestic routes.

## 📌 Business Problem
Flight prices on the same route can vary a lot by airline, day of travel,
duration, and departure time. This project uses EDA and statistical testing to
help travelers understand these patterns and find the best-value options.

## 🎯 Objectives
- Scrape flight fare data from IRCTC Air
- Compare ticket prices across airlines on the same route
- Examine weekend vs weekday fare differences
- Analyze the relationship between flight duration and fare
- Study price variation across departure hours
- Identify value carriers and optimal fare windows

## 🗂️ Dataset
- **Source:** IRCTC Air (scraped with Selenium)
- **Size:** 2,500+ rows across routes such as Hyderabad → Mumbai and Hyderabad → Goa
- **Features:** Airline, From, To, Date, Departure Time, Arrival Time, Duration, Price
- **Airlines:** Air India, IndiGo, Air India Express, SpiceJet, Alliance Air, Star Air

## 🧹 Data Cleaning & Feature Engineering
- Removed rows with missing values (<1%)
- Stripped the ₹ symbol and converted price to numeric
- Converted duration from hours/minutes to total minutes
- Created a `Route` column and extracted departure/arrival hours
- Added `Type_of_Day` (weekday/weekend) and `Price_Segment` (Budget / Standard / Premium / Luxury)

## 📊 Analysis Performed
- **Univariate:** airline count plot, price KDE, duration histogram, price segment pie chart
- **Bivariate:** price by airline, duration by airline, weekday vs weekend boxplots,
  duration vs price scatter, price vs departure hour
- **Outlier analysis:** IQR method (~4.7% outliers, skewness 1.56, kurtosis 3.02)
  and the decision to retain them as genuine market behavior

## 🧪 Hypothesis Testing
| Test | Question | Result |
|------|----------|--------|
| Welch's t-test | Are weekend fares different from weekday fares? | Reject H0 |
| One-way ANOVA | Do airlines charge different average prices? | Reject H0 |
| Two-way ANOVA | Do airline and duration jointly (and interactively) affect price? | Reject H0 |

## 🔑 Key Findings
- IndiGo and Air India dominate flight volume; smaller carriers have limited presence
- About half of all flights fall in the "Standard" price segment
- Airlines follow distinct pricing strategies, even on the same route
- Duration affects price, but the relationship is weak and not proportional
- Weekday and weekend fares differ significantly
- Price outliers reflect real demand spikes and premium fares, not noise

## 🛠️ Tech Stack
Python · Selenium · Pandas · NumPy · Matplotlib · Seaborn · SciPy · Statsmodels
