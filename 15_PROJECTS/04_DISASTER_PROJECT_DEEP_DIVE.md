# Disaster Affected Region Tracker — Interview Deep Dive

Repository: https://github.com/HarshaVinay/Disaster-Affected-Region-Tracker-Analysis

## One-minute explanation
I built a data-analysis pipeline that ingests disaster/region CSV data, cleans and validates it with Python/Pandas, derives an analytical event-level dataset, loads curated data into MySQL and runs SQL analytics to answer operational questions. The final layer produces charts for affected population, severity, monthly trends, economic loss and disaster frequency.

## Data engineering flow
```text
CSV sources
   ↓
Pandas ingestion
   ↓
Data type normalization
   ↓
Missing-value handling
   ↓
Deduplication
   ↓
Business-rule transformations
   ↓
Curated datasets
   ↓
MySQL
   ↓
SQL analytics
   ↓
Visualizations
```

## Key defense: grain
Before joins, identify the grain. If region reference data has multiple rows for the same region name, joining event data on region name can multiply rows. The safer approach is to preserve the event-region grain and avoid a join that double-counts measures.

## Missing values
Explain each business rule, not merely the code:
- missing categorical disaster type → controlled unknown category;
- invalid dates → null plus validation handling;
- missing population → statistical imputation where appropriate;
- missing affected population/economic loss → zero only when zero is a defensible business interpretation.

## Why Pandas + MySQL?
For a small supplied dataset, this is a simple and transparent architecture. At large scale, move landing data to cloud object storage and distributed processing, then serve curated data using a cloud warehouse/lakehouse.

## Likely follow-ups
- What was the grain?
- How did you validate the output?
- Why median instead of mean?
- How did you detect duplicates?
- Why MySQL?
- How would you process 1 TB?
- How would you implement SCD/CDC?
- How would you move this to Snowflake?
- How would you redesign it in Fabric?
