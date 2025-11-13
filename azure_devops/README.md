# Azure DevOps Scripts

This directory contains scripts for managing Azure DevOps resources.

---

### `azure_devops_api.sh`

Queries Azure DevOps's API with authentication.

---

### `azure_devops_foreach_repo.sh`

Executes a templated command for each Azure DevOps repo, replacing `{user}`, `{org}`, `{project}` and `{repo}` in each iteration.

---

### `azure_devops_to_github_migration.sh`

Migrates one or all Azure DevOps git repos to GitHub, including all branches and sets the default branch to match via the APIs to maintain the same checkout behaviour.

---

### `azure_devops_disable_repos.sh`

Disables one or more given Azure DevOps repos (to prevent further pushes to them after migration to GitHub).
