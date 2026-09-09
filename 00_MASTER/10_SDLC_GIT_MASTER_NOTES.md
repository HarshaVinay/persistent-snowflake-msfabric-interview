# SDLC + Git Master Notes

## Curriculum
Waterfall, Agile, Agile vs Waterfall, story pointing, Scrum ceremonies, VCS/CVCS/DVCS, repository initialization, remote push, commit, branch, merge, push, pull and exercises.

## SDLC
SDLC is the lifecycle for planning, designing, building, testing, deploying and maintaining software.

### Waterfall
Sequential phase-oriented model. Changes late in the cycle are usually expensive.

### Agile
Iterative development in short cycles, continuous feedback and reprioritization.

### Agile vs Waterfall
```text
Waterfall → sequential, scope planned upfront
Agile     → iterative, feedback-driven
```

## Scrum
Know Product Backlog, Sprint, Sprint Planning, Daily Scrum, Review, Retrospective and story points.

Story points estimate relative effort/complexity; they are not hours.

## Git mental model
```text
Working tree → staging area → local repository → remote repository
```

Core commands:
```bash
git init
git status
git add .
git commit -m "message"
git branch
git switch -c feature/x
git merge feature/x
git remote add origin <url>
git push

git pull
```

## VCS terminology
VCS = version control system.
CVCS = centralized VCS.
DVCS = distributed VCS; Git is distributed.

## Interview questions
- Why Git?
- commit vs push.
- pull vs fetch.
- merge vs rebase at conceptual level.
- branch strategy.
- resolve a merge conflict.
- why meaningful commits?

## Practical answer
"I use branches to isolate changes, commits to create local version history, push to publish commits to the remote repository, and pull to synchronize local work with remote changes. I resolve conflicts by understanding both changes instead of blindly accepting one side."
