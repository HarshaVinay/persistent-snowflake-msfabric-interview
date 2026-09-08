# Project 1 — Disaster Affected Region Tracker Defence

## Verified project structure
Repository contains README, notebook, data, SQL, source and dependency/run files. fileciteturn7file0L1-L5

## Interview story
Problem → ingest disaster/region/impact CSVs → inspect and clean → standardize types → handle nulls → deduplicate → transform/merge at the correct grain → create clean analytical datasets → load relational tables → analytical SQL → visualize.

## Questions to master
- Why Pandas?
- Why MySQL?
- What cleaning rules did you apply?
- Why did you choose median for a missing numeric field?
- How did you treat missing impact values?
- How did you detect duplicates?
- What was the grain?
- Why could a region join duplicate events?
- How did you validate output?
- What would you change at 10 GB/1 TB?

## Scale-up answer
At larger scale: object storage/raw zone → Spark for distributed transformations → Bronze/Silver/Gold → Snowflake/Fabric serving layer → BI.

## Never say
“Pandas is always better.” Say it matched the supplied scale and project requirements.
