# Repository Audit — 2026-09-09

## Audit scope
This audit reviews the current handbook structure, naming, navigation, evidence discipline, curriculum mapping, duplicated research snapshots, and technical freshness requirements.

## Findings

### Strengths
- The latest user-provided Persistent Snowflake_MSFabric curriculum is explicitly treated as the syllabus authority.
- The repository has separate research, master-note, coding, scenario, project, and final-interview layers.
- Persistent interview reports are separated into evidence classes A/B/C/D.
- The user's two real projects are first-class preparation sources.
- Previous Spark and Snowflake training notes are incorporated as source material.

### Issues found
1. Several older files use path names that no longer exactly match the current folder names. The canonical navigation must therefore point to verified current paths.
2. There are multiple dated Persistent research snapshots. These are useful as historical evidence but should not compete with one canonical synthesis.
3. Some older notes contain facts that can age. Vendor-specific facts must be checked against current official documentation before being used as the final answer.
4. GitHub-facing Markdown must use public URLs rather than internal citation syntax intended for the ChatGPT interface.
5. The curriculum checklist should distinguish **covered in master notes** from **interview priority** and from **personally implemented**.
6. The handbook must never imply production experience where the source only shows training or a personal project.

## Optimization decisions
- `00_MASTER` is the control plane of the repository.
- `01_PERSISTENT_RESEARCH` is the evidence plane.
- Domain folders are the learning plane.
- `15_PROJECTS`, `16_SCENARIOS`, and `17_CODING` are application/practice planes.
- `18_FINAL_INTERVIEW` is the final execution layer.
- Dated research files are historical snapshots; the source register and synthesis are canonical.

## Technical freshness corrections
### Snowflake
Current Snowflake documentation states that table data is automatically divided into micro-partitions containing approximately 50–500 MB of uncompressed data, with metadata used for pruning. Do not preserve older conflicting size figures as current facts.

### Snowflake recovery
Time Travel supports historical querying/cloning/restoration within the configured retention period; Fail-safe is a separate Snowflake-managed recovery period. Do not describe Fail-safe as an ordinary historical-query feature.

### Snowflake cloning
Zero-copy cloning is initially storage-efficient, but a clone is writable and independent; data changes create additional storage as needed. Time Travel can be combined with CLONE for historical states.

### Fabric
Current Microsoft documentation describes OneLake as Fabric's unified logical data lake. Lakehouse uses Delta/Parquet storage and supports Spark and SQL access. Direct Lake has distinct OneLake and SQL-endpoint security/behavior paths. OneLake security now explicitly covers table/folder, column-level and row-level access controls.

## Completion definition
The repository is considered **handbook-structure complete** when every curriculum family has a master note and final-review entry. It is considered **interview-content complete** only when P0 topics also have coding/scenario/project drills and the user has passed mock interviews.

## Quality gate
Before adding any new document, ask:
- Does it cover a gap?
- Does it belong in the existing canonical section?
- Is it evidence, teaching material, coding, scenario, project, or final simulation?
- Does it duplicate an existing file?
- Are product facts current?

**Audit status: STRUCTURE STABLE — CONTINUE CONTENT DEPTH, NOT RANDOM FILE GROWTH.**
