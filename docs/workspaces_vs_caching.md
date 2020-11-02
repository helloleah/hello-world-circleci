# Caches vs. Workspaces in CircleCI

Caches and workspaces are tools for persisting data between jobs and workflows. Both can make builds more efficient and consistent, but caches and workspaces have different features that may be more suited to one task than another.

## Data Persistence

The main difference between caches and workspaces is where the data is stored and access to the data. Caches persist data across the same job in different workflow builds, while workspaces persist data across other jobs in the same workflow. Caches are global, meaning that they can be used across different workflows and branches. CircleCI stores caches for 15 days. Conversely, workspaces are not accessible by other workflow runs. The only exception is that a workflow rerun within the 15-day limit will have access to the original run's workspace

## When to Use

The purpose of caching is to store data that would be expensive to regenerate on each build and that another job can reuse. Caching dependencies is a frequent use case because dependencies take a long time to download, and only a few dependencies may change from build to build. Workspaces are useful when dealing with data that is unique to a workflow run and when data from one job will be used as input to a downstream job. For example, a build job from a Java project may output a .jar file that is then used by the unit test, integration test, and code coverage jobs.
