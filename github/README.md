# GitHub Scripts

This directory contains scripts for managing GitHub resources.

---

### `github_api.sh`

Queries the GitHub [API](https://docs.github.com/en/rest/reference). Can infer GitHub user, repo and authentication token from local checkout or environment (`$GITHUB_USER`, `$GITHUB_TOKEN`).

---

### `github_install_binary.sh`

Installs a binary from GitHub releases into $HOME/bin or /usr/local/bin.

---

### `github_foreach_repo.sh`

Executes a templated command for each non-fork GitHub repo.

---

### `github_graph_commit_times_gnuplot.sh`

Generates GNUplot graph of GitHub commit times from all public GitHub repos for a given user.

---

### `github_graph_commit_times_mermaidjs.sh`

Generates MermaidJS graph of the GitHub commit times from all public GitHub repos for a given user.

---

### `github_clone_or_pull_all_repos.sh`

Git clones or pulls all repos for a user or organization.

---

### `github_download_release_file.sh`

Downloads a file from GitHub Releases.

---

### `github_download_release_jar.sh`

Downloads a JAR file from GitHub Releases.

---

### `github_invitations.sh`

Lists / accepts repo invitations.

---

### `github_mirror_repos_to_gitlab.sh`

Creates/syncs GitHub repos to GitLab.

---

### `github_mirror_repos_to_bitbucket.sh`

Creates/syncs GitHub repos to BitBucket.

---

### `github_mirror_repos_to_aws_codecommit.sh`

Creates/syncs GitHub repos to AWS CodeCommit.

---

### `github_mirror_repos_to_gcp_source_repos.sh`

Creates/syncs GitHub repos to GCP Source Repos.

---

### `github_pull_request_create.sh`

Creates a Pull Request idempotently.

---

### `github_pull_request_preview.sh`

Opens a GitHub Pull Request preview page from the current local branch.

---

### `github_push_pr_preview.sh`

Pushes to GitHub origin, sets upstream branch, then open a Pull Request preview.

---

### `github_push_pr.sh`

Pushes to GitHub origin, sets upstream branch, then idemopotently creates a Pull Request.

---

### `github_merge_branch.sh`

Merges one branch into another branch via a Pull Request.

---

### `github_remote_set_upstream.sh`

In a forked GitHub repo's checkout, determine the origin of the fork and configure a git remote to the upstream.

---

### `github_pull_merge_trunk.sh`

Pulls the origin or fork upstream repo's trunk branch and merges it into the local branch.

---

### `github_forked_add_remote.sh`

Quickly adds a forked repo as a remote from an interactive men list of forked repos.

---

### `github_forked_checkout_branch.sh`

Quickly check out a forked repo's branch from an interactive menu lists of forked repos and their branches.

---

### `github_tag_hashref.sh`

Returns the GitHub commit hashref for a given GitHub Actions `owner/repo@tag`.

---

### `github_actions_foreach_workflow.sh`

Executes a templated command for each workflow in a given GitHub repo.

---

### `github_actions_aws_create_load_credential.sh`

Creates an AWS user with group/policy, generates and downloads access keys, and uploads them to the given repo.

---

### `github_actions_in_use.sh`

Lists GitHub Actions directly referenced in the .github/workflows in the current local repo checkout.

---

### `github_actions_in_use_repo.sh`

Lists GitHub Actions for a given repo via the API, including following imported reusable workflows.

---

### `github_actions_in_use_across_repos.sh`

Lists GitHub Actions in use across all your repos.

---

### `github_actions_repos_lockdown.sh`

Secures GitHub Actions settings across all user repos to only GitHub, verified partners and selected 3rd party actions.

---

### `github_actions_repo_set_secret.sh`

Sets a secret in the given repo from `key=value` or shell export format, as args or via stdin.

---

### `github_actions_repo_env_set_secret.sh`

Sets a secret in the given repo and environment from `key=value` or shell export format, as args or via stdin.

---

### `github_actions_repo_secrets_overriding_org.sh`

Finds any secrets for a repo that are overriding organization level secrets.

---

### `github_actions_repo_restrict_actions.sh`

Restricts GitHub Actions in the given repo to only running actions from GitHub and verfied partner companies.

---

### `github_actions_repo_actions_allow.sh`

Allows select 3rd party GitHub Actions in the given repo.

---

### `github_actions_runner.sh`

Generates a [GitHub Actions](https://github.com/features/actions) self-hosted runner token and runs a dockerized runner.

---

### `github_actions_runner_local.sh`

Downloads, configures and runs a local GitHub Actions Runner for Linux or Mac.

---

### `github_actions_runner_token.sh`

Generates a GitHub Actions runner token to register a new self-hosted runner.

---

### `github_actions_runners.sh`

Lists GitHub Actions self-hosted runners for a given Repo or Organization.

---

### `github_actions_delete_offline_runners.sh`

Deletes offline GitHub Actions self-hosted runners.

---

### `github_actions_workflows.sh`

Lists GitHub Actions workflows for a given repo.

---

### `github_actions_workflow_runs.sh`

Lists GitHub Actions workflow runs for a given workflow id or name.

---

### `github_actions_workflows_status.sh`

Lists all GitHub Actions workflows and their statuses for a given repo.

---

### `github_actions_workflows_state.sh`

Lists GitHub Actions workflows enabled/disabled states.

---

### `github_actions_workflows_disabled.sh`

Lists GitHub Actions workflows that are disabled.

---

### `github_actions_workflow_enable.sh`

Enables a given GitHub Actions workflow.

---

### `github_actions_workflows_enable_all.sh`

Enables all GitHub Actions workflows in a given repo.

---

### `github_actions_workflows_trigger_all.sh`

Triggers all workflows for the given repo.

---

### `github_actions_workflows_cancel_all_runs.sh`

Cancels all workflow runs for the given repo.

---

### `github_actions_workflows_cancel_waiting_runs.sh`

Cancels workflow runs that are in waiting state.

---

### `github_actions_log.sh`

Outputs the text log for a given GitHub Actions workflow run to the terminal.

---

### `github_actions_latest_log.sh`

Same as above, but just fetches the latest workflow run log without any prompting.

---

### `github_ssh_get_user_public_keys.sh`

Fetches a given GitHub user's public SSH keys via the API.

---

### `github_ssh_get_public_keys.sh`

Fetches the currently authenticated GitHub user's public SSH keys via the API.

---

### `github_ssh_add_public_keys.sh`

Uploads SSH keys from local files or standard input to the currently authenticated GitHub account.

---

### `github_ssh_delete_public_keys.sh`

Deletes given SSH keys from the currently authenticated GitHub account by key id or title regex match.

---

### `github_gpg_get_user_public_keys.sh`

Fetches a given GitHub user's public GPG keys via the API.

---

### `github_generate_status_page.sh`

Generates a [STATUS.md](https://harisekhon.github.io/CI-CD/) page by merging all the README.md headers for all of a user's non-forked GitHub repos or a given list of any repos etc.

---

### `github_purge_camo_cache.sh`

Send HTTP Purge requests to all camo urls (badge caches) for the current or given GitHub repo's landing/README.md page.

---

### `github_ip_ranges.sh`

Returns GitHub's IP ranges, either all by default or for a select given service such as hooks or actions.

---

### `github_sync_repo_descriptions.sh`

Syncs GitHub repo descriptions to GitLab & BitBucket repos.

---

### `github_release.sh`

Creates a GitHub Release, auto-incrementing a `.N` suffix on the year/month/day date format if no exact version given.

---

### `github_repo_check_pat_token.sh`

Checks the given PAT token can access the given GitHub repo.

---

### `github_repo_description.sh`

Fetches the given repo's description.

---

### `github_repo_find_files.sh`

Finds files matching a regex in the current or given GitHub repo via the GitHub API.

---

### `github_repo_latest_release.sh`

Returns the latest release tag for a given GitHub repo via the GitHub API.

---

### `github_repo_latest_release_filter.sh`

Returns the latest release tag matching a given regex filter for a given GitHub repo via the GitHub API.

---

### `github_repo_stars.sh`

Fetches the stars, forks and watcher counts for a given repo.

---

### `github_repo_teams.sh`

Fetches the GitHub Enterprise teams and their role permisions for a given repo.

---

### `github_repo_collaborators.sh`

Fetches a repo's granted users and outside invited collaborators as well as their role permisions for a given repo.

---

### `github_repo_protect_branches.sh`

Enables branch protections on the given repo.

---

### `github_repos_find_files.sh`

Finds files matching a regex across all repos in the current GitHub organization or user account.

---

### `github_repo_fork_sync.sh`

Sync's current or given fork, then runs `github_repo_fork_update.sh` to cascade changes to major branches via Pull Requests for auditability.

---

### `github_repo_fork_update.sh`

Updates a forked repo by creating pull requests for full audit tracking and auto-merges PRs for non-production branches.

---

### `github_repos_public.sh`

Lists public repos for a user or organization.

---

### `github_repos_disable_wiki.sh`

Disables the Wiki on one or more given repos.

---

### `github_repos_with_few_users.sh`

Finds repos with few or no users.

---

### `github_repos_with_few_teams.sh`

Finds repos with few or no teams.

---

### `github_repos_without_branch_protections.sh`

Finds repos without any branch protection rules.

---

### `github_repos_not_in_terraform.sh`

Finds all non-fork repos for current or given user/organization which are not found in `$PWD/*.tf` Terraform code.

---

### `github_teams_not_in_terraform.sh`

Finds all teams for given organization which are not found in `$PWD/*.tf` Terraform code.

---

### `github_repos_sync_status.sh`

Determines whether each GitHub repo's mirrors on GitLab / BitBucket / Azure DevOps are up to date with the latest commits.

---

### `github_teams_not_idp_synced.sh`

Finds GitHub teams that aren't sync'd from an IdP like Azure AD.

---

### `github_user_repos_stars.sh`

Fetches the total number of stars for all original source public repos for a given user.

---

### `github_user_repos_forks.sh`

Fetches the total number of forks for all original source public repos for a given user.

---

### `github_user_repos_count.sh`

Fetches the total number of original source public repos for a given username.

---

### `github_user_followers.sh`

Fetches the number of followers for a given username.

---

### `github_url_clipboard.sh`

Copies a GitHub URL file's contents to the clipboard, converting the URL to a raw GitHub content URL where necessary.
