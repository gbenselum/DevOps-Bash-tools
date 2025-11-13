# GCP Scripts

This directory contains scripts for managing Google Cloud Platform resources.

---

### `.envrc-gcp`

Copy to `.envrc` for [direnv](https://direnv.net/) to auto-load GCP configuration settings such as Project, Region, Zone, GKE cluster kubectl context or any other GCloud SDK settings to shorten `gcloud` commands. Applies to the local shell environment only to avoid race conditions caused by naively changing the global gcloud config at `~/.config/gcloud/active_config`.

---

### `gcp_terraform_create_credential.sh`

Creates a service account for [Terraform](https://www.terraform.io/) with full permissions, creates and downloads a credential key json and even prints the `export GOOGLE_CREDENTIALS` command to configure your environment to start using Terraform immediately. Run once for each project and combine with [direnv](https://direnv.net/) for fast easy management of multiple GCP projects.

---

### `gcp_ansible_create_credential.sh`

Creates an [Ansible](https://www.ansible.com/) service account with permissions on the current project, creates and downloads a credential key json and prints the environment variable to immediately use it.

---

### `gcp_cli_create_credential.sh`

Creates a GCloud SDK CLI service account with full owner permissions to all projects, creates and downloads a credential key json and even prints the `export GOOGLE_CREDENTIALS` command to configure your environment to start using it. Avoids having to reauth to `gcloud auth login` every day.

---

### `gcp_spinnaker_create_credential.sh`

Creates a [Spinnaker](https://spinnaker.io/) service account with permissions on the current project, creates and downloads a credential key json and even prints the Halyard CLI configuration commands to use it.

---

### `gcp_info.sh`

Huge [Google Cloud](https://cloud.google.com/) inventory of deployed resources within the current project.

---

### `gcp_info_all_projects.sh`

Same as above but for all detected projects.

---

### `gcp_foreach_project.sh`

Executes a templated command across all GCP projects, replacing `{project_id}` and `{project_name}` in each iteration.

---

### `gcp_find_orphaned_disks.sh`

Lists orphaned disks across one or more GCP projects (not attached to any compute instance).

---

### `gcp_secret_add.sh`

Reads a value from a command line argument or non-echo prompt and saves it to GCP Secrets Manager. Useful for uploading a password without exposing it on your screen.

---

### `gcp_secret_add_binary.sh`

Uploads a binary file to GCP Secrets Manager by base64 encoding it first. Useful for uploading QR code screenshots. Useful for uploading things like QR code screenshots for sharing MFA to recovery admin accounts.

---

### `gcp_secret_update.sh`

Reads a value from a command line argument or non-echo prompt and updates a given GCP Secrets Manager secret. Useful for uploading a password without exposing it on your screen.

---

### `gcp_secret_get.sh`

Finds the latest version of a given GCP Secret Manager secret and returns its value. Used by adjacent scripts.

---

### `gcp_secret_label_k8s.sh`

Labels a given existing GCP secret with the current kubectl cluster name and namespace for later use by `gcp_secrets_to_kubernetes.sh`.

---

### `gcp_secrets_to_kubernetes.sh`

Loads GCP secrets to Kubernetes secrets in a 1-to-1 mapping.

---

### `gcp_secrets_to_kubernetes_multipart.sh`

Creates a Kubernetes secret from multiple GCP secrets.

---

### `gcp_secrets_labels.sh`

Lists GCP Secrets and their labels, one per line suitable for quick views or shell pipelines.

---

### `gcp_secrets_update_lable.sh`

Updates all GCP secrets in current project matching label key=value with a new label value.

---

### `gcp_service_account_credential_to_secret.sh`

Creates GCP service account and exports a credential key to GCP Secret Manager.

---

### `gke_kube_creds.sh`

Auto-loads all GKE clusters credentials in the current / given / all projects so your kubectl is ready to rock on GCP.

---

### `gke_kubectl.sh`

Runs kubectl commands safely fixed to a given GKE cluster using config isolation to avoid concurrency race conditions.

---

### `gke_firewall_rule_cert_manager.sh`

Creates a GCP firewall rule for a given GKE cluster's masters to access [Cert Manager](https://cert-manager.io/) admission webhook.

---

### `gke_firewall_rule_kubeseal.sh`

Creates a GCP firewall rule for a given GKE cluster's masters to access [Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets) controller for `kubeseal` to work.

---

### `gke_nodepool_nodes.sh`

Lists all nodes in a given nodepool on the current GKE cluster via kubectl labels (fast).

---

### `gke_nodepool_nodes2.sh`

Same as above via GCloud SDK (slow, iterates instance groups).

---

### `gke_nodepool_taint.sh`

Taints/untaints all nodes in a given GKE nodepool on the current cluster.

---

### `gke_nodepool_drain.sh`

Drains all nodes in a given nodepool.

---

### `gke_persistent_volumes_disk_mappings.sh`

Lists GKE kubernetes persistent volumes to GCP persistent disk names, along with PVC and namespace.

---

### `gcr_list_tags.sh`

Lists all the tags for a given GCR docker image.

---

### `gcr_newest_image_tags.sh`

Lists the tags for the given GCR docker image with the newest creation date.

---

### `gcr_alternate_tags.sh`

Lists all the tags for a given GCR docker `image:tag`.

---

### `gcr_tag_latest.sh`

Tags a given GCR docker `image:tag` as `latest` without pulling or pushing the docker image.

---

### `gcr_tag_branch.sh`

Tags a given GCR docker `image:tag` with the current Git branch without pulling or pushing the docker image.

---

### `gcr_tag_datetime.sh`

Tags a given GCR docker image with its creation date and UTC timestamp.

---

### `gcr_tag_newest_image_as_latest.sh`

Finds and tags the newest build of a given GCR docker image as `latest` without pulling or pushing the docker image.

---

### `gcr_tags_timestamps.sh`

Lists all the tags and their timestamps for a given GCR docker image.

---

### `gcr_tags_old.sh`

Lists tags older than N days for a given GCR docker image.

---

### `gcr_delete_old_tags.sh`

Deletes tags older than N days for a given GCR docker image.

---

### `gcp_ci_build.sh`

Script template for CI/CD to trigger Google Cloud Build to build docker container image with extra datetime and latest tagging.

---

### `gcp_ci_deploy_k8s.sh`

Script template for CI/CD to deploy GCR docker image to GKE Kubernetes using Kustomize.

---

### `gce_foreach_vm.sh`

Run a command for each GCP VM instance matching the given name/ip regex in the current GCP project.

---

### `gce_host_ips.sh`

Prints the IPs and hostnames of all or a regex match of GCE VMs for use in /etc/hosts.

---

### `gce_ssh.sh`

Runs `gcloud compute ssh` to a VM while auto-determining its zone first to override any inherited zone config and make it easier to script iterating through VMs.

---

### `gcs_ssh_keyscan.sh`

SSH keyscans all the GCE VMs returned from the above `gce_host_ips.sh` script and adds them to `~/.ssh/known_hosts`.

---

### `gce_meta.sh`

Simple script to query the GCE metadata API from within Virtual Machines.

---

### `gce_when_preempted.sh`

GCE VM preemption latch script - can be executed any time to set one or more commands to execute upon preemption.

---

### `gce_is_preempted.sh`

GCE VM return true/false if preempted, callable from other scripts.

---

### `gce_instance_service_accounts.sh`

Lists GCE VM instance names and their service accounts.

---

### `gcp_firewall_disable_default_rules.sh`

Disables those lax GCP default network "allow all" firewall rules.

---

### `gcp_firewall_risky_rules.sh`

Lists risky GCP firewall rules that are enabled and allow traffic from 0.0.0.0/0.

---

### `gcp_sql_backup.sh`

Creates Cloud SQL backups.

---

### `gcp_sql_export.sh`

Creates Cloud SQL exports to [GCS](https://cloud.google.com/storage).

---

### `gcp_sql_enable_automated_backups.sh`

Enable automated daily Cloud SQL backups.

---

### `gcp_sql_enable_point_in_time_recovery.sh`

Enable point-in-time recovery with write-ahead logs.

---

### `gcp_sql_proxy.sh`

Boots a [Cloud SQL Proxy](https://cloud.google.com/sql/docs/postgres/sql-proxy) to all Cloud SQL instances for fast convenient direct `psql` / `mysql` access via local sockets. Installs Cloud SQL Proxy if necessary.

---

### `gcp_sql_running_primaries.sh`

Lists primary running Cloud SQL instances.

---

### `gcp_sql_service_accounts.sh`

Lists Cloud SQL instance service accounts.

---

### `gcp_sql_create_readonly_service_account.sh`

Creates a service account with read-only permissions to Cloud SQL.

---

### `gcp_sql_grant_instances_gcs_object_creator.sh`

Grants minimal GCS objectCreator permission on a bucket to primary Cloud SQL instances for exports.

---

### `gcp_cloud_schedule_sql_exports.sh`

Creates Google [Cloud Scheduler](https://cloud.google.com/scheduler) jobs to trigger a [Cloud Function](https://cloud.google.com/functions) via [PubSub](https://cloud.google.com/pubsub) to run [Cloud SQL](https://cloud.google.com/sql) exports to [GCS](https://cloud.google.com/storage) for all [Cloud SQL](https://cloud.google.com/sql) instances in the current GCP project.

---

### `bigquery_list_datasets.sh`

Lists BigQuery datasets in the current GCP project.

---

### `bigquery_list_tables.sh`

Lists BigQuery tables in a given dataset.

---

### `bigquery_list_tables_all_datasets.sh`

Lists tables for all datasets in the current GCP project.

---

### `bigquery_foreach_dataset.sh`

Executes a templated command for each dataset.

---

### `bigquery_foreach_table.sh`

Executes a templated command for each table in a given dataset.

---

### `bigquery_foreach_table_all_datasets.sh`

Executes a templated command for each table in each dataset in the current GCP project.

---

### `bigquery_table_row_count.sh`

Gets the row count for a given table.

---

### `bigquery_tables_row_counts.sh`

Gets the row counts for all tables in a given dataset.

---

### `bigquery_tables_row_counts_all_datasets.sh`

Gets the row counts for all tables in all datasets in the current GCP project.

---

### `bigquery_generate_query_biggest_tables_across_datasets_by_row_count.sh`

Generates a BigQuery SQL query to find the top 10 biggest tables by row count.

---

### `bigquery_generate_query_biggest_tables_across_datasets_by_size.sh`

Generates a BigQuery SQL query to find the top 10 biggest tables by size.

---

### `gcp_iam_roles_in_use.sh`

Lists GCP IAM roles in use in the current or all projects.

---

### `gcp_iam_identities_in_use.sh`

Lists GCP IAM identities (users/groups/serviceAccounts) in use in the current or all projects.

---

### `gcp_iam_roles_granted_to_identity.sh`

Lists GCP IAM roles granted to identities matching the regex (users/groups/serviceAccounts) in the current or all projects.

---

### `gcp_iam_roles_granted_too_widely.sh`

Lists GCP IAM roles which have been granted to allAuthenticatedUsers or even worse allUsers (unauthenticated) in one or all projects.

---

### `gcp_iam_roles_with_direct_user_grants.sh`

Lists GCP IAM roles which have been granted directly to users in violation of best-practice group-based management.

---

### `gcp_iam_serviceaccount_members.sh`

Lists members with permissions to use each GCP service account.

---

### `gcp_iam_serviceaccounts_without_permissions.sh`

Finds service accounts without IAM permissionns, useful to detect obsolete service accounts after a 90 day unused permissions clean out.

---

### `gcp_iam_workload_identities.sh`

Lists GKE Workload Identity integrations, uses `gcp_iam_serviceaccount_members.sh`.

---

### `gcp_iam_users_granted_directly.sh`

Lists GCP IAM users which have been granted roles directly in violation of best-practice group-based management.

---

### `gcs_bucket_project.sh`

Finds the GCP project that a given bucket belongs to using the GCP Storage API.

---

### `gcs_curl_file.sh`

Retrieves a GCS file's contents from a given bucket and path using the GCP Storage API.

---

### `firebase_foreach_project.sh`

Executes a templated command across all Firebase projects, replacing `{project_id}`, `{project_number}` and `{project_name}` in each iteration.
