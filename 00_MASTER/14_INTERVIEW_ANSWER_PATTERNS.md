# Interview Answer Patterns

## 1. Concept question
**Definition → mechanism → example → when to use → limitation**

Example: What is partition pruning?

> Partition pruning is the process of skipping storage partitions that cannot satisfy a filter. In Snowflake, micro-partition metadata can be used to eliminate irrelevant micro-partitions, reducing data scanned. It is especially useful for large tables with selective predicates.

## 2. Comparison question
Use the same dimensions for both choices.

**Definition → key difference → performance → cost → operational impact → selection rule.**

## 3. Coding question
**Clarify → state assumptions → write clean solution → test edge cases → explain complexity → mention alternative only when useful.**

## 4. Troubleshooting question
**Observe → isolate → root cause → fix → validate → prevent recurrence.**

## 5. Architecture question
**Requirements → volume → latency/SLA → source → ingestion → raw/bronze → transformation → silver → serving/gold → orchestration → quality → security → observability → recovery → cost.**

## 6. Project question
Answer in this order:
1. Problem
2. Input/source
3. Architecture
4. Your exact contribution
5. Data cleaning/transformation
6. Storage/model
7. Analytics/output
8. Challenge
9. How you solved it
10. What you would change at scale

## 7. Experience honesty
Use these phrases accurately:
- “I implemented…” for code you actually wrote.
- “During training, I practiced…” for curriculum labs.
- “My design would be…” for proposed production architecture.

Never convert a study topic into claimed production experience.
