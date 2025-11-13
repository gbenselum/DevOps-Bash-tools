# Git Scripts

This directory contains scripts for managing Git repositories.

---

### `precommit_run_changed_files.sh`

Runs pre-commit on all files changed on the current branch vs the default branch.

---

### `git_diff_commit.sh`

Quickly commits added or updated files to Git, showing a diff and easy enter prompt for each file.

---

### `git_review_push.sh`

Shows diff of what would be pushed upstream and prompts to push.

---

### `git_branch_delete_squash_merged.sh`

Carefully detects if a squash merged branch you want to delete has no changes with the default trunk branch before deleting it.

---

### `git_tag_release.sh`

Creates a Git tag, auto-incrementing a `.N` suffix on the year/month/day date format if no exact version given.

---

### `git_foreach_branch.sh`

Executes a command on all branches.

---

### `git_foreach_repo.sh`

Executes a command against all adjacent repos from a given repolist.

---

### `git_foreach_modified.sh`

Executes a command against each file with git modified status.

---

### `git_foreach_repo_replace_readme_actions.sh`

Updates the `README.md` badges for GitHub Actions to match the local repo name.

---

### `git_foreach_repo_update_readme.sh`

Git-diff-commits the `README.md` for each Git repo checkout.

---

### `git_push_stats.sh`

Shows the Git push stats to the remote origin for the current branch.

---

### `git_origin_log_to_push.sh`

Shows the Git log in local branch that would be pushed to remote origin.

---

### `git_origin_files_to_push.sh`

Shows the Git files in local branch that would be pushed to remote origin.

---

### `git_origin_diff_to_push.sh`

Shows the Git diff of lines in local branch that would be pushed to remote origin.

---

### `git_origin_commit_count_to_push.sh`

Shows the number of Git commits in local branch that would be pushed to remote origin.

---

### `git_origin_line_count_to_push.sh`

Shows the Git number of lines changed in local branch that would be pushed to remote origin.

---

### `git_merge_all.sh` / `git_merge_master.sh` / `git_merge_master_pull.sh`

Merges updates from master branch to all other branches.

---

### `git_remotes_add_origin_providers.sh`

Auto-creates remotes for the 4 major public repositories (GitHub/GitLab/Bitbucket/Azure DevOps).

---

### `git_remotes_set_multi_origin.sh`

Sets up multi-remote origin for unified push to automatically keep the 4 major public repositories in sync.

---

### `git_remotes_set_https_to_ssh.sh`

Converts local repo's remote URLs from https to ssh.

---

### `git_remotes_set_ssh_to_https.sh`

Converts local repo's remote URLs from ssh to https.

---

### `git_remotes_set_https_creds_helpers.sh`

Adds Git credential helpers configuration to the local git repo to use http API tokens dynamically from environment variables if they're set.

---

### `git_repos_pull.sh`

Pull multiple repos based on a source file mapping list.

---

### `git_repos_update.sh`

Same as above but also runs the `make update` build to install the latest dependencies.

---

### `git_grep_env_vars.sh`

Find environment variables in the current git repo's code base in the format `SOME_VAR`.

---

### `git_log_empty_commits.sh`

Find empty commits in git history.

---

### `git_log_me.sh`

Shows only commits in the Git log done by you.

---

### `git_log_me_added.sh`

Same as above but only file addition commits.

---

### `git_graph_commit_history_gnuplot.sh`

Generates GNUplot graphs of Git commits per year and per month for the entire history of the local Git repo checkout.

---

### `git_graph_commit_history_mermaidjs.sh`

Generates MermaidJS graphs of Git commits per year and per month for the entire history of the local Git repo checkout.

---

### `git_graph_commit_times_gnuplot.sh`

Generates a GNUplot graph of Git commit times from the current Git repo checkout's `git log`.

---

### `git_graph_commit_times_mermaidjs.sh`

Generates a MermaidJS graph of Git commit times from the current Git repo checkout's `git log`.

---

### `git_graph_commit_times_gnuplot_all_repos.sh`

Generates GNUplot graph of the GitHub commit times from all local adjacent Git repo checkouts.

---

### `git_graph_commit_times_mermaidjs_all_repos.sh`

Generates MermaidJS graph of the GitHub commit times from all local adjacent Git repo checkouts.

---

### `github_public_lines_of_code.sh`

Checks out all public original source GitHub repos for the current or given user and then counts all lines of code for them.

---

### `git_revert_line.sh`

Reverts the first line that matches a given regex from the Git head commit's version of the same line number.

---

### `git_files_no_uncommitted_changes.sh`

Returns zero if given file(s) don't have uncommitted changes to Git.

---

### `git_files_in_history.sh`

Finds all filename / file paths in the git log history.

---

### `git_filter_branch_fix_author.sh`

Rewrites Git history to replace author/committer name & email references.

---

### `git_filter_repo_replace_text.sh`

Rewrites Git history to replace a given text to scrub a credential or other sensitive token from history.

---

### `git_submodules_update.sh`

Updates all submodules in the local git repo to the latest commit of their detected default trunk branch.

---

### `git_submodules_update_repos.sh`

Updates submodules for all repos given as args or saved in the `setup/repos.txt` file.

---

### `git_askpass.sh`

Credential helper script to use environment variables for git authentication.
