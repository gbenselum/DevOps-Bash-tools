# Terraform Scripts

This directory contains scripts for managing Terraform resources.

---

### `terraform_cloud_api.sh`

Queries the Cloudflare API, handling authentication using `$TERRAFORM_TOKEN`.

---

### `terraform_cloud_ip_ranges.sh`

Returns the list of IP ranges for Terraform Cloud.

---

### `terraform_cloud_organizations.sh`

Lists Terraform Cloud organizations.

---

### `terraform_cloud_workspaces.sh`

Lists Terraform Cloud workspaces.

---

### `terraform_cloud_workspace_vars.sh`

Lists Terraform Cloud workspace variables.

---

### `terraform_cloud_workspace_set_vars.sh`

Adds / updates Terraform workspace-level sensitive environment/terraform variable(s) via the API from `key=value` or shell export format, as args or via stdin.

---

### `terraform_cloud_workspace_delete_vars.sh`

Deletes one or more Terraform workspace-level variables.

---

### `terraform_cloud_varsets.sh`

Lists Terraform Cloud variable sets.

---

### `terraform_cloud_varset_vars.sh`

Lists Terraform Cloud variables in on or all variables sets for the given organization.

---

### `terraform_cloud_varset_set_vars.sh`

Adds / updates Terraform sensitive environment/terraform variable(s) in a given variable set via the API from `key=value` or shell export format, as args or via stdin.

---

### `terraform_cloud_varset_delete_vars.sh`

Deletes one or more Terraform variables in a given variable set.

---

### `terraform_gcs_backend_version.sh`

Determines the Terraform state version from the tfstate file in a GCS bucket found in a local given `backend.tf`.

---

### `terraform_gitlab_download_backend_variable.sh`

Downloads backend.tf from a GitLab CI/CD variable to be able to quickly iterate plans locally.

---

### `terraform_import.sh`

Finds given resource type in `./*.tf` code or Terraform plan output that are not in Terraform state and imports them.

---

### `terraform_import_aws_iam_users.sh`

Parses Terraform plan output to import new `aws_iam_user` additions into Terraform state.

---

### `terraform_import_aws_iam_groups.sh`

Parses Terraform plan output to import new `aws_iam_group` additions into Terraform state.

---

### `terraform_import_aws_iam_policies.sh`

Parses Terraform plan output to import new `aws_iam_policies` additions, resolves their ARNs and imports them into Terraform state.

---

### `terraform_import_aws_sso_permission_sets.sh`

Finds all `aws_ssoadmin_permission_set` in `./*.tf` code, resolves the ARNs and imports them to Terraform state.

---

### `terraform_import_aws_sso_account_assignments.sh`

Parses Terraform plan output to import new `aws_ssoadmin_account_assignment` additions into Terraform state.

---

### `terraform_import_aws_sso_managed_policy_attachments.sh`

Parses Terraform plan output to import new `aws_ssoadmin_account_assignment` additions into Terraform state.

---

### `terraform_import_aws_sso_permission_set_inline_policies.sh`

Parses Terraform plan output to import new `aws_ssoadmin_permission_set_inline_policy` additions into Terraform state.

---

### `terraform_import_github_repos.sh`

Finds all `github_repository` in `./*.tf` code or Terraform plan output that are not in Terraform state and imports them.

---

### `terraform_import_github_team.sh`

Imports a given GitHub team into a given Terraform state resource, by first querying the GitHub API for the team ID needed to import into Terraform.

---

### `terraform_import_github_teams.sh`

Finds all `github_team` in `./*.tf` code or Terraform plan output that are not in Terraform state, then queries the GitHub API for their IDs and imports them.

---

### `terraform_import_github_team_repos.sh`

Finds all `github_team_repository` in Terraform plan that would be added, then queries the GitHub API for the repos and team IDs and if they both exist then imports them to Terraform state.

---

### `terraform_provider_count_sizes.sh`

Finds duplicate Terraform providers and their sizes.

---

### `terraform_resources.sh`

External program to get all resource ids and attribute for a given resource type to work around Terraform splat expression limitation.

---

### `terraform_managed_resource_types.sh`

Quick parse of what Terraform resource types are found in `*.tf` files under the current or given directory tree.

---

### `terraform_registry_url_extract.sh`

Extracts the Terraform Registry URL in either `tfr://` or `https://registry.terraform.io/` format from a given string, file or standard input.

---

### `terraform_registry_url_to_https.sh`

Converts one or more Terraform Registry URLs from `tfr://` to `https://registry.terraform.io/` format.

---

### `terraform_registry_url_open.sh`

Opens the Terraform Registry URL given as a string arg, file or standard input in either `tfr://` or `https://registry.terraform.io/` format.
