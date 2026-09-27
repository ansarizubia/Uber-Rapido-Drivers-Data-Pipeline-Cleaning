## Data Cleaning - Uber/Rapido Drivers Dataset 

#### Overview

A data-cleaning and validation project focused on transforming a messy 50,000-row Uber/Rapido driver dataset into a consistent, reliable, and analysis-ready file.

The project demonstrates how an analyst handles real-world data-quality problems such as duplicate records, missing IDs, inconsistent text formats, invalid values, mixed date formats, missing data, and statistical outliers.

The final output includes a cleaned CSV file and a reproducible Jupyter Notebook documenting each cleaning decision.

#### Objective

The objective was to transform a deliberately messy, real-world-style driver dataset into a clean, consistent, and analysis-ready dataset while documenting and validating every major cleaning decision.

The project focused on answering practical data-quality questions:

- How many duplicate records exist?
- Which fields contain missing or invalid values?
- Are IDs unique and usable?
- Are dates stored in consistent formats?
- Are numerical values within logical business ranges?
- Which missing values can be safely filled?
- Which values should remain blank because they cannot be reliably recovered?
- How did the dataset change after cleaning?

#### Dataset

The raw dataset contains approximately 50,000+ records related to Uber and Rapido drivers:

- Driver identifiers.
- Platform information.
- Personal and contact fields.
- Driver status.
- Ratings and performance metrics.
- Registration and onboarding dates.
- Completion and cancellation rates.
- Other operational attributes.

### Data Cleaning Process
1. **Data quality report (before)** — checked null counts, duplicate rows,
   data types, and value-range anomalies across all columns.

2. **Duplicate removal** — dropped exact duplicate rows, then ran a second
   duplicate check after standardization (which revealed additional
   duplicates hidden by inconsistent formatting).

3. **Missing primary key** — dropped rows with no `driver_id`, since a
   unique ID can't be reconstructed or guessed.

4. **Standardization** — fixed inconsistent casing/spelling in text and
   category columns (e.g. `"Uber"`/`"UBER"`/`"uber"` → `"Uber"`), converted
   Yes/No/1/0 variants to proper booleans, cleaned phone numbers and email
   addresses, and parsed 7 different date formats into a single consistent
   datetime format.

5. **Value-range validation** — converted logically impossible values
   (e.g. age of `999`, rating of `-2`, completion rate over `100%`) into
   true missing values, separate from genuine statistical outliers.

6. **Missing-data handling** — applied median imputation for numeric
   columns, mode/"Not Specified" for categorical columns, and left
   inherently unrecoverable fields (phone, email, interview/onboarding
   dates) blank rather than fabricating values.

7. **Outlier detection** — used the IQR method on all numeric columns and
   handled flagged values by capping rather than deleting rows.

8. **Data type correction** — set every column to its correct final type
   (IDs/text as string, counts as integer, rates/scores as float, dates as
   datetime, flags as boolean).

9. **Before vs. after summary** — compared row count, missing values, and
   duplicate count pre- and post-cleaning to confirm the cleaning worked.

10. **Export** — saved the cleaned dataset to a new CSV file.

### Tech Stack
- Microsoft Excel
- Python
- pandas, NumPy
- Jupyter Notebook

#### Outcome

The project transformed the raw dataset into a validated dataset suitable for further analysis.

- Cleaned 50,000 raw rows across 33 columns.
- Produced 47,602 validated rows.
- Removed more than 900 duplicate records.
- Addressed over 150,000 data-quality issues.
- Standardized inconsistent text and category values.
- Parsed seven date formats into a consistent datetime format.
- Converted invalid business values into genuine missing values.
- Applied appropriate missing-data strategies.
- Detected and capped statistical outliers.
- Delivered a clean CSV file and reproducible Python notebook.

*The data-quality issue count includes duplicate records, missing values, invalid entries, formatting inconsistencies, and other field-level corrections. These issues are not necessarily unique rows.*

#### Why This Project Matters

Poor-quality data can lead to incorrect reporting, unreliable dashboards, and misleading business decisions.

For a mobility company, clean driver data could support future analysis of:

- Driver performance.
- Platform-wise driver activity.
- Driver onboarding.
- Completion and cancellation rates.
- Ratings and service quality.
- Driver retention.
- Regional operations.
- Workforce planning.

This project demonstrates that reliable analysis begins with validated and well-documented data.

#### Important Notes

- The dataset is intended for analytical and learning purposes.
- Missing values were handled according to field type and business logic.
- Unrecoverable information was left blank rather than artificially created.
- Outliers were capped where appropriate instead of automatically deleting rows.
- The cleaned dataset should be reviewed again before use in production reporting.

## Author

**Zubia Ansari**  
Data & BI Analyst

[LinkedIn](https://www.linkedin.com/in/zubia-ansari01/) · [GitHub](https://github.com/ansarizubia)