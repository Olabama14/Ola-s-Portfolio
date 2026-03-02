# Maternal Health Risk Analysis
## Executive Summary

This project analyzes maternal health data to understand how vital signs relate to pregnancy risk levels. Using Python and Power BI, I explored patterns in blood pressure, blood sugar, age, temperature, and heart rate across 1,014 maternal records. The analysis highlights strong predictors of high‑risk cases, especially elevated blood pressure and blood sugar. Correlation patterns reveal an Age–BP–BS triad that can support early risk stratification. The project provides clinically grounded insights and a foundation for data‑driven maternal health monitoring.

## Maternal Health Risk Project Overview

This analysis explores maternal health indicators; Age, Blood Pressure, Blood Sugar, Body Temperature, and Heart Rate, to understand how these vitals relate to RiskLevel (low, mid, high). The goal is to identify patterns that may support early detection of high‑risk cases.

## Data Overview

Rows: 1014

Columns: 7

### Parameters: 

Age: Maternal age (years)

SystolicBP: Systolic blood pressure (mmHg)

DiastolicBP: Diastolic blood pressure(mmHg)

BS: Blood sugar level (mg/dL)

BodyTemp: Body temperature (°F)

HeartRate: Beats per minute

RiskLevel: Categorical risk label (low risk, mid risk, high risk)

## Univariate Analysis

| Feature            | Mean   | Std Dev | Min  | Max  |
|--------------------|--------|---------|------|------|
| Age                | 29.87  | 13.47   | 10.0 | 70.0 |
| SystolicBP (mmHg)  | 113.19 | 18.40   | 70.0 | 160.0|
| DiastolicBP (mmHg) | 76.46  | 13.88   | 49.0 | 100.0|
| BS (mg/dL)         | 8.72   | 3.29    | 6.0  | 19.0 |
| BodyTemp (°F)      | 98.66  | 1.37    | 98.0 | 103.0|
| HeartRate (bpm)    | 74.30  | 8.08    | 7.0  | 90.0 |

### RiskLevel Distribution

| RiskLevel | Proportion | Count |
|-----------|------------|-------|
| High      | 40%        | 406   |
| Mid       | 35%        | 355   |
| Low       | 25%        | 253   |

## Key Observations
Central tendencies place most vitals within expected ranges, with clinically relevant upper tails for SystolicBP and BS.

HeartRate distribution clusters around 70–80 bpm, with evidence of subgroups.

## Age Distribution
Most mothers fall between 20–35 years, with fewer cases at the extremes (10–60+).

High‑risk cases appear across all ages, showing that age alone is not a strong predictor.

![Distribution of Maternal Age](images/Distribution_of_Maternal_Age.png)

## Blood Pressure Patterns
Blood pressure is one of the strongest differentiators of risk.

- High risk: SystolicBP ≥ 140 and DiastolicBP ≥ 90

- Low risk: Typically 100–120 / 60–80

- Mid risk: Transitional zone with moderate elevation

This aligns with clinical expectations around hypertension in pregnancy.

![Box plot of Systolic BP by Risk Level](images/Box_plot_of_Systolic_BP_by_Risk_Level.png)

## Blood Sugar (BS)
Blood sugar shows a clear separation across risk levels:

- High risk: BS often > 10

- Mid risk: BS between 7–9

- Low risk: BS between 6–8

This makes BS a strong independent predictor of risk.

![Scatter plot of blood sugar by risk level](images/Scatter_plot_of_blood_sugar_by_risk_level.png)

## Heart Rate
Heart rate generally ranges between 60–90 bpm.

- High‑risk cases show more variability and more elevated values (≥ 85 bpm).

- Low‑risk cases cluster around 70–80 bpm.

![Distribution of Heart Rate](images/Distribution_of_Heart_rate.png)

## Bivariate Analysis
### SystolicBP by RiskLevel: 

High risk group exhibits elevated median and greater spread; mid risk overlaps low risk but has wider variance.

### Blood Sugar vs Age by RiskLevel: 

Positive trend between age and BS. High risk individuals show higher BS across the age range.

### HeartRate distribution:

Multimodal patterns suggest distinct subpopulations (e.g., resting versus stressed/activity states).

### Actionable  Insight

Age stratification meaningfully separates glucose and blood pressure risk profiles and should be included in risk stratification logic.

## Correlation Analysis

Provided variable correlations and interpretations.

### Age & DiastolicBP = 0.40 

Moderate positive correlation; diastolic pressure tends to increase with age. Use age as a covariate in BP risk models.

### SystolicBP & DiastolicBP = 0.79

Strong positive relationship; both move together and reflect overall BP status. Both can be retained for clinical completeness.

### Age & BS = 0.47 

Moderate positive correlation; older patients trend toward higher blood sugar. Prioritize glucose screening for older maternal age groups.

### BodyTemp & BS ≈ -0.10 

Very weak negative relationship; temperature is not a useful predictor of blood sugar here.

### HeartRate correlations < 0.15 with other vitals 

Heart rate shows weak associations and likely reflects contextual factors. Treat HR as dynamic and evaluate with time-context data where possible.

![Correlation Matrix of Maternal Health Indicators](images/Correlation_Matrix_of_Maternal_Health_Indicators.png)

### Multivariate Implication

Age, BP, and BS form a correlated triad suitable for composite risk scoring.

BodyTemp and HeartRate are weaker predictors and are better treated as supplementary signals.

## Outlier Detection and Clinical Flags

Primary outliers are elevated SystolicBP (>140 mmHg) and high BS values in the high risk group.

### Recommendation for flagged records: 

- Measurement validation.

- Review medication and comorbidities.

- Follow-up monitoring or intervention.

## Recommendations

Build a composite risk score using Age SystolicBP DiastolicBP and BS with weighting informed by correlation strengths.

Implement age-stratified screening protocols for glucose and blood pressure.

Use BodyTemp to flag systemic stress or infection but not as a primary metabolic predictor.

Model HeartRate separately with time-series or context features when available.

Add interactive correlation-weighting widgets in Power BI to let clinicians explore variable importance and patient-level flags.

