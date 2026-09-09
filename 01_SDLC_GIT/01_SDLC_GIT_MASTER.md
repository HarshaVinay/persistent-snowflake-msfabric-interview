# SDLC, Agile, Scrum & Git Master Notes

## SDLC
Software Development Life Cycle is the structured process used to plan, build, test, release and maintain software.

## Waterfall
Sequential model where phases largely proceed in order. Useful when requirements are stable and change is expensive.

## Agile
Iterative/incremental approach that delivers value in short cycles and adapts to changing requirements.

## Agile vs Waterfall
| Dimension | Waterfall | Agile |
|---|---|---|
| Requirements | mostly upfront | evolve |
| Delivery | larger phases | increments |
| Feedback | later | continuous |
| Change | costly | expected |

## Story points
Relative estimate of effort/complexity/uncertainty, not hours.

## Scrum ceremonies
- Sprint planning
- Daily scrum
- Sprint review
- Retrospective

## Git mental model
```text
Working tree → staging area → local repository → remote repository
```

## Common commands
```bash
git init
git status
git add .
git commit -m "message"
git branch feature-x
git switch feature-x
git merge feature-x
git pull
git push
```

## VCS / CVCS / DVCS
- VCS: version-control system in general.
- Centralized VCS: central server is the primary repository.
- Distributed VCS: every clone has repository history, supporting local commits and branching.

## Merge conflict
Occurs when changes cannot be combined automatically. Resolve the conflict deliberately, run tests, stage the resolution and commit.

## Interview project connection
For both your projects, be ready to explain branching, commits, pull/push flow, and how you would prevent accidental secrets or generated artifacts from entering the repository.
