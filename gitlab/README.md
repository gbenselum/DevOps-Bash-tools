# GitLab Scripts

This directory contains scripts for managing GitLab resources.

---

### `gitlab_api.sh`

Queries the GitLab [API](https://docs.gitlab.com/ee/api/api_resources.html). Can infer GitLab user, repo and authentication token from local checkout or environment (`$GITLAB_USER`, `$GITLAB_TOKEN`).

---

### `gitlab_install_binary.sh`

Installs a binary from GitLab releases into $HOME/bin or /usr/local/bin. Auto-determines the latest release if no version specified, detects and unpacks any tarball or zip files.

---

### `gitlab_push_mr_preview.sh`

Pushes to GitLab origin, sets upstream branch, then open a Merge Request preview from current to default branch.

---

### `gitlab_push_mr.sh`

Pushes to GitLab origin, sets upstream branch, then idemopotently creates a Merge Request from current branch to the given or default trunk branch and opens the generated MR in your browser for review.

---

### `gitlab_foreach_repo.sh`

Executes a templated command for each GitLab project/repo, replacing the `{user}` and `{project}` in each iteration.

---

### `gitlab_project_latest_release.sh`

Returns the latest release tag for a given GitLab project (repo) via the GitLab API.

---

### `gitlab_project_set_description.sh`

Sets the description for one or more projects using the GitLab API.

---

### `gitlab_project_set_env_vars.sh`

Adds / updates GitLab project-level environment variable(s) via the API from `key=value` or shell export format, as args or via stdin.

---

### `gitlab_group_set_env_vars.sh`

Adds / updates GitLab group-level environment variable(s) via the API from `key=value` or shell export format, as args or via stdin.

---

### `gitlab_project_create_import.sh`

Creates a GitLab repo as an import from a given URL, and mirrors if on GitLab Premium.

---

### `gitlab_project_protect_branches.sh`

Enables branch protections on the given project.

---

### `gitlab_project_mirrors.sh`

Lists each GitLab repo and whether it is a mirror or not.

---

### `gitlab_pull_mirror.sh`

Trigger a GitLab pull mirroring for a given project's repo.

---

### `gitlab_ssh_get_user_public_keys.sh`

Fetches a given GitLab user's public SSH keys via the API.

---

### `gitlab_ssh_get_public_keys.sh`

Fetches the currently authenticated GitLab user's public SSH keys via the API.

---

### `gitlab_ssh_add_public_keys.sh`

Uploads SSH keys from local files or standard input to the currently authenticated GitLab account.

---

### `gitlab_ssh_delete_public_keys.sh`

Deletes given SSH keys from the currently authenticated GitLab account by key id or title regex match.

---

### `gitlab_validate_ci_yaml.sh`

Validates a `.gitlab-ci.yml` file via the GitLab API.
