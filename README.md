# BRFSS 2013 Health Analysis

This ia an exploratory data analysis project using the 2013 Behavioral Risk Factor Surveillance System (BRFSS) dataset. This project examines associations between exercise, body mass index (BMI), mental health, household income, health-care coverage, and self-reported general health among U.S. adults.

## Project Overview

This project was completed as part of the Duke University *Introduction to Probability and Data with R* course. It demonstrates a basic end-to-end R workflow: data cleaning, descriptive statistics, grouped summaries, data visualization, and interpretation of observational survey data.

The analysis uses `dplyr` for data wrangling and `ggplot2` for visualization.

## Dataset and Study Design

The 2013 BRFSS is a large probability-based telephone survey of non-institutionalized U.S. adults aged 18 years and older. Data were collected through landline and cellular telephone interviews.

Because BRFSS is an observational survey, the findings describe associations rather than causal effects. Potential limitations include nonresponse bias, telephone undercoverage, self-report bias in exercise, health, height, and weight, and possible bias from excluding observations with missing values.

The raw dataset is not included in this repository. It was supplied through course materials and is excluded from version control through `.gitignore`.

## Research Questions

### RQ1: Exercise, BMI, and self-reported health

How does self-reported general health differ between adults who did and did not exercise in the past 30 days, across BMI categories?

![RQ1: Self-reported health by exercise status and BMI category](figures/rq1_exercise_bmi_health.png)

Across all BMI categories, respondents who exercised in the past 30 days had a higher proportion reporting Excellent or Very good health and a lower proportion reporting Fair or Poor health than non-exercisers. For example, among respondents with normal weight, 67.4% of exercisers reported Excellent or Very good health, compared with 39.8% of non-exercisers. The obese non-exercising group had the highest proportion reporting Fair or Poor health (40.1%).

### RQ2: Exercise, sex, and poor mental health days

How does the number of poor mental health days in the past 30 days differ by recent exercise status and sex among U.S. adults?

![RQ2: Poor mental health days by exercise status and sex](figures/rq2_mental_health_exercise_sex.png)

The median number of poor mental health days was zero in all groups, so the proportion reporting zero poor mental health days provided a clearer comparison. Among males, 75.4% of exercisers and 71.3% of non-exercisers reported zero poor mental health days. Among females, the corresponding proportions were 66.7% and 62.1%. Female non-exercisers had the highest mean number of poor mental health days (5.2 days).

### RQ3: Income, health-care coverage, and self-reported health

How does self-reported general health differ across household income categories among adults with and without health-care coverage?

![RQ3: Self-reported health by income and health-care coverage](figures/rq3_income_insurance_health.png)

Self-reported health showed a clear income gradient within both health-care coverage groups. Among respondents with coverage, the proportion reporting Excellent or Very good health increased from 30.1% in the lowest income group to 70.5% in the highest income group. Among respondents without coverage, the same proportion increased from 33.5% to 63.9%.

The relationship between health-care coverage and self-reported health was not consistent within income groups. This should not be interpreted causally, as age, employment, existing health conditions, and other unmeasured factors may influence both health-care coverage and self-reported health.

## Methods

The analysis includes:

- Data screening and complete-case analysis for each research question
- Removal of invalid values, such as `menthlth = 5000` for a variable defined as the number of poor mental health days in the past 30 days
- Descriptive statistics including sample size, proportions, means, medians, and interquartile ranges
- Grouped comparisons using `group_by()` and `summarise()`
- Proportional stacked bar charts and faceted visualizations
- Interpretation of generalizability, bias, confounding, and causal limitations