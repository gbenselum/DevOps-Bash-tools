# AWS Scripts

This directory contains scripts for managing AWS resources.

---

### `aws_profile.sh`

Switches to an AWS Profile selected from a convenient interactive menu list of AWS profiles from `$AWS_CONFIG_FILE` - useful when you have lots of AWS work profiles.

---

### `aws_cli_create_credential.sh`

Creates an AWS service account user for CI/CD or CLI with Admin permissions (or other group or policy), creates an AWS Access Key, saves a credentials CSV and even prints the shell export commands and aws credentials file config to configure your environment to start using it. Useful trick to avoid CLI reauth to `aws sso login` every day.

---

### `aws_terraform_create_credential.sh`

Creates a AWS terraform service account with Administrator permissions for Terraform Cloud or other CI/CD systems to run Terraform plan and apply, since no CI/CD systems can work with AWS SSO workflows. Stores the access key as both CSV and prints shell export commands and credentials file config as above.

---

### `.envrc-aws`

Copy to `.envrc` for [direnv](https://direnv.net/) to auto-load AWS configuration settings such as AWS Profile, Compute Region, EKS cluster kubectl context etc.

---

### `aws_sso_ssh.sh`

Launches local AWS SSO authentication pop-up (if not already authenticated), then scp's the latest resultant `~/.aws/sso/cache/` file to the remote server and SSH's there so that you can use AWS CLI or kubectl to EKS remotely on that server easily, without having to copy and paste the token from remote aws sso login to your local web browser.

---

### `aws_terraform_create_s3_bucket.sh`

Creates a Terraform S3 bucket for storing the backend state, locks out public access, enables versioning, encryption, and locks out Power Users role and optionally any given user/group/role ARNs via a bucket policy for safety.

---

### `aws_terraform_create_dynamodb_table.sh`

Creates a Terraform locking table in DynamoDB for use with the S3 backend, plus custom IAM policy which can be applied to less privileged accounts.

---

### `aws_terraform_create_all.sh`

Runs all of the above, plus also applies the custom DynamoDB IAM policy to the user to ensure if the account is less privileged it can still get the Terraform lock (useful for GitHub Actions environment secret for a read only user to generate Terraform Plans in Pull Request without needing approval).

---

### `aws_terraform_iam_grant_s3_dynamodb.sh`

Creates IAM policies to access any S3 buckets and DynamoDB tables with `terraform-state` or `tf-state` in their names, and attaches them to the given user. Useful for limited permissions CI/CD accounts that run Terraform Plan eg. in GitHub Actions pull requests.

---

### `aws_account_summary.sh`

Prints AWS account summary in `key = value` pairs for easy viewing / grepping of things like `AccountMFAEnabled`, `AccountAccessKeysPresent`, useful for checking whether the root account has MFA enabled and no access keys, comparing number of users vs number of MFA devices etc. (see also `check_aws_root_account.py` in [Advanced Nagios Plugins](https://github.com/HariSekhon/Nagios-Plugins)).

---

### `aws_billing_alarm.sh`

Creates a [CloudWatch](https://aws.amazon.com/cloudwatch/) billing alarm and [SNS](https://aws.amazon.com/sns/) topic with subscription to email you when you incur charges above a given threshold. This is often the first thing you want to do on an account.

---

### `aws_budget_alarm.sh`

Creates an [AWS Budgets](https://aws.amazon.com/cloudwatch/) billing alarm and [SNS](https://aws.amazon.com/sns/) topic with subscription to email you when both when you start incurring forecasted charges of over 80% of your budget, and 90% actual usage. This is often the first thing you want to do on an account.

---

### `aws_batch_stale_jobs.sh`

Lists [AWS Batch](https://aws.amazon.com/batch/) jobs that are older than N hours in a given queue.

---

### `aws_batch_kill_stale_jobs.sh`

Finds and kills [AWS Batch](https://aws.amazon.com/batch/) jobs that are older than N hours in a given queue.

---

### `aws_cloudfront_distribution_for_origin.sh`

Returns the AWS CloudFront ARN of the distribution which serves origins containing a given substring. Useful for quickly finding the CloudFront ARN needed to give permissions to a private S3 bucket exposed via CloudFront.

---

### `aws_cloudtrails_cloudwatch.sh`

Lists [Cloud Trails](https://aws.amazon.com/cloudtrail/) and their last delivery to [CloudWatch](https://aws.amazon.com/cloudwatch/features/) Logs (should be recent).

---

### `aws_cloudtrails_event_selectors.sh`

Lists [Cloud Trails](https://aws.amazon.com/cloudtrail/) and their event selectors to check each one has at least one event selector.

---

### `aws_cloudtrails_s3_accesslogging.sh`

Lists [Cloud Trails](https://aws.amazon.com/cloudtrail/) buckets and their Access Logging prefix and target bucket. Checks [S3 access logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) is enabled.

---

### `aws_cloudtrails_s3_kms.sh`

Lists [Cloud Trails](https://aws.amazon.com/cloudtrail/) and whether their [S3](https://aws.amazon.com/s3/) buckets are [KMS](https://aws.amazon.com/kms/) secured.

---

### `aws_cloudtrails_status.sh`

Lists [Cloud Trails](https://aws.amazon.com/cloudtrail/) status - if logging, multi-region and log file validation enabled.

---

### `aws_config_all_types.sh`

Lists [AWS Config](https://aws.amazon.com/config/) recorders, checking all resource types are supported (should be true) and includes global resources (should be true).

---

### `aws_config_recording.sh`

Lists [AWS Config](https://aws.amazon.com/config/) recorders, their recording status (should be true) and their last status (should be success).

---

### `aws_csv_creds.sh`

Prints AWS credentials from a CSV file as shell export statements. Useful to quickly switch your shell to some exported credentials from a service account for testing permissions or pipe to upload to a CI/CD system via an API (eg. `jenkins_cred_add*.sh`, `github_actions_repo*_set_secret.sh`, `gitlab_*_set_env_vars.sh`, `circleci_*_set_env_vars.sh`, `bitbucket_*_set_env_vars.sh`, `terraform_cloud_*_set_vars.sh`, `kubectl_kv_to_secret.sh`). Supports new user and new access key csv file formats.

---

### `aws_codecommit_csv_creds.sh`

Prints AWS [CodeCommit](https://aws.amazon.com/codecommit/) Git credentials from a CSV file as shell export statements. Similar use case and chaining as above.

---

### `aws_ec2_instance_name_to_id.sh`

Looks up an EC2 instance ID from an instance name with extra safety checks that only a single instance ID is returned and a reverse lookup on that instance ID to re-verify it matches the name. This level of safety is important when wanting to terminate an EC2 instance by name. If an instance ID is passed, returns it as is for convenience. Used by adjacent scripts.

---

### `aws_ec2_instances.sh`

Lists AWS EC2 instances, their DNS names and States in an easy to read table output.

---

### `aws_ec2_instance_ip.sh`

Determines an EC2 instance IP address, trying first for a public IP, or failing that a private IP.

---

### `aws_ec2_instance_clone.sh`

Clones an AWS EC2 instance by creating an AMI from the original and then booting a new instance from the AMI with the same settings as the original instance. Useful to testing risky things on a separate EC2 instance, such as Server Administrator recovery of Tableau.

---

### `aws_ec2_instance_wait_for_ready.sh`

Polls an AWS EC2 instance and waits for it to finish initializing to a ready state. Used by adjacent scripts.

---

### `aws_ec2_instance_terminate_by_name.sh`

Terminate an AWS EC2 instance by name for convenience, resolves its instance ID, verifies unique and then terminates by ID.

---

### `aws_ec2_amis.sh`

List AWS EC2 AMIs belonging to your account in an easy to read table output.

---

### `aws_ec2_ami_ids.sh`

Lists AWS EC2 AMI IDs only, one per line, to be used in adjacent scripts that creating mapping tables and translate AMI IDs to names in inventory scripts `aws_info_ec2*.sh`.

---

### `aws_ec2_ami_name_to_id.sh`

Looks up an EC2 AMI ID from a name with extra safety checks that only a single AMI ID is returned and a reverse lookup on that AMI ID to re-verify it matches the name.

---

### `aws_ec2_ami_boot.sh`

Boots a personal EC2 instance of a given AMI for testing.

---

### `aws_ec2_ami_boot_ssh.sh`

Boots a personal EC2 instance of a given AMI, determines the public or private IP, and drops you into an SSH shell.

---

### `aws_ec2_ami_create_from_instance.sh`

Creates an AWS EC2 AMI from an EC2 instance and waits for it to become available for use.

---

### `aws_ec2_ami_share_to_account.sh`

Shares an AMI with another AWS account. Can specify AMI by name or id.

---

### `aws_ec2_ebs_volumes.sh`

List EC2 instances and their EBS volumes in the current region.

---

### `aws_ec2_ebs_create_snapshot_and_wait.sh`

Creates a snapshot of a given EBS volume ID and waits for it to complete with exponential backoff.

---

### `aws_ec2_ebs_resize_and_wait.sh`

Resizes an EBS volume and waits for it to complete modifying and optionally optimizing with exponential backoff.

---

### `aws_ec2_ebs_volumes_unattached.sh`

List an unattached EBS volumes in a table format.

---

### `aws_ec2_launch_templates_ami_id.sh`

For each Launch Template lists the AMI ID of the latest version. Useful to check EKS upgrades of node groups via Terragrunt have taken effect.

---

### `aws_ecr_docker_login.sh`

Authenticates Docker to AWS ECR, inferring the ECR registry from the current AWS Account ID and Region.

---

### `aws_ecr_docker_build_push.sh`

Builds a docker image and pushes it to ECR with not just the `latest` docker tag but also the current Git hashref and Git tags.

---

### `aws_ecr_list_repos.sh`

Lists ECR repos, and their docker image mutability and whether image scanning is enabled.

---

### `aws_ecr_list_tags.sh`

Lists all the tags for a given ECR docker image.

---

### `aws_ecr_newest_image_tags.sh`

Lists the tags for the given ECR docker image with the newest creation date (can use this to determine which image version to tag as `latest`).

---

### `aws_ecr_alternate_tags.sh`

Lists all the tags for a given ECR docker `image:tag` (use arg `<image>:latest` to see what version / build hashref / date tag has been tagged as `latest`).

---

### `aws_ecr_tag_image.sh`

Tags an ECR image with another tag without pulling and pushing it.

---

### `aws_ecr_tag_image_by_digest.sh`

Same as above but tags an ECR image found via digest (more accurate as reference by existing tag can be a moving target). Useful to recover images that have become untagged.

---

### `aws_ecr_tag_latest.sh`

Tags a given ECR docker `image:tag` as `latest` without pulling or pushing the docker image.

---

### `aws_ecr_tag_branch.sh`

Tags a given ECR `image:tag` with the current Git branch without pulling or pushing the docker image.

---

### `aws_ecr_tag_datetime.sh`

Tags a given ECR docker image with its creation date and UTC timestamp (when it was uploaded to ECR) without pulling or pushing the docker image.

---

### `aws_ecr_tag_newest_image_as_latest.sh`

Finds and tags the newest build of a given ECR docker image as `latest` without pulling or pushing the docker image.

---

### `aws_ecr_tags_timestamps.sh`

Lists all the tags and their timestamps for a given ECR docker image.

---

### `aws_ecr_tags_old.sh`

Lists tags older than N days for a given ECR docker image.

---

### `aws_ecr_delete_old_tags.sh`

Deletes tags older than N days for a given ECR docker image. Lists the image:tags to be deleted and prompts for confirmation safety.

---

### `aws_emr_clusters_last_steps.sh`

Shows the last N steps executed on each EMR cluster and their EndTime to find idle clusters that should be removed. Also checks CloudWatch for number of steps running within the last few months to catch directly submitted jobs such as Spark, Hive, Glue or Athena which won't show up in the native steps list.

---

### `aws_foreach_profile.sh`

Executes a templated command across all AWS named profiles configured in AWS CLIv2, replacing `{profile}` in each iteration. Combine with other scripts for powerful functionality, auditing, setup etc. eg. `aws_kube_creds.sh` to configure `kubectl` config to all EKS clusters in all environments.

---

### `aws_foreach_region.sh`

Executes a templated command against each AWS region enabled for the current account, replacing `{region}` in each iteration. Combine with AWS CLI or scripts to find resources across regions.

---

### `aws_iam_password_policy.sh`

Prints [AWS password policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html) in `key = value` pairs for easy viewing / grepping (used by `aws_harden_password_policy.sh` before and after to show the differences).

---

### `aws_iam_harden_password_policy.sh`

Strengthens [AWS password policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html) according to [CIS Foundations Benchmark](https://d1.awsstatic.com/whitepapers/compliance/AWS_CIS_Foundations_Benchmark.pdf) recommendations.

---

### `aws_iam_replace_access_key.sh`

Replaces the non-current IAM access key (Inactive, Not Used, longer time since used, or an explicitly given key), outputting the new key as shell export statements (useful for piping to the same tools listed for `aws_csv_creds.sh` above).

---

### `aws_iam_policies_attached_to_users.sh`

Finds [AWS IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html) directly attached to users (anti-best practice) instead of groups.

---

### `aws_iam_policies_granting_full_access.sh`

Finds [AWS IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html) granting full access (anti-best practice).

---

### `aws_iam_policies_unattached.sh`

Lists unattached [AWS IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage.html).

---

### `aws_iam_policy_attachments.sh`

Finds all users, groups and roles where a given IAM policy is attached, so that you can remove all these references in your Terraform code and avoid this error `Error: error deleting IAM policy arn:aws:iam::***:policy/mypolicy: DeleteConflict: Cannot delete a policy attached to entities.`.

---

### `aws_iam_policy_delete.sh`

Deletes an IAM policy, by first handling all prerequisite steps of deleting all prior versions and all detaching all users, groups and roles.

---

### `aws_iam_generate_credentials_report_wait.sh`

Generates an AWS IAM [credentials report](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_getting-report.html).

---

### `aws_iam_users.sh`

List your IAM users.

---

### `aws_iam_users_access_key_age.sh`

Prints AWS users [access key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) status and age (see also `aws_users_access_key_age.py` in [DevOps Python tools](https://github.com/HariSekhon/DevOps-Python-tools) which can filter by age and status).

---

### `aws_iam_users_access_key_age_report.sh`

Prints AWS users [access key](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) status and age using a bulk credentials report (faster for many users).

---

### `aws_iam_users_access_key_last_used.sh`

Prints AWS users [access keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) last used date.

---

### `aws_iam_users_access_key_last_used_report.sh`

Same as above using bulk credentials report (faster for many users).

---

### `aws_iam_users_last_used_report.sh`

Lists AWS users password/access keys last used dates.

---

### `aws_iam_users_mfa_active_report.sh`

Lists AWS users password enabled and [MFA](https://aws.amazon.com/iam/features/mfa/) enabled status.

---

### `aws_iam_users_without_mfa.sh`

Lists AWS users with password enabled but no MFA.

---

### `aws_iam_users_mfa_serials.sh`

Lists AWS users [MFA](https://aws.amazon.com/iam/features/mfa/) serial numbers (differentiates Virtual vs Hardware MFAs).

---

### `aws_iam_users_pw_last_used.sh`

Lists AWS users and their password last used date.

---

### `aws_ip_ranges.sh`

Get all AWS IP ranges for a given Region and/or Service using the IP range API.

---

### `aws_info_all_profiles.sh`

Calls `aws_info.sh` for all AWS profiles using `aws_foreach_profile.sh`.

---

### `aws_info.sh`

Lists AWS deployed resources in the current or specified AWS account profile.

---

### `aws_info_ec2.sh`

Lists AWS EC2 Instances resources deployed in the current AWS account.

---

### `aws_info_ec2_csv.sh`

Lists AWS EC2 Instances in quoted CSV format in the current AWS account.

---

### `aws_info_ec2_all_profiles_csv.sh`

Lists AWS EC2 Instances in quoted CSV format across all configured AWS profiles for their configured region.

---

### `aws_eks_cloudwatch_logs.sh`

Enables and fetches AWS EKS Master logs via CloudWatch.

---

### `aws_eks_ssh_dump_logs.sh`

Fetch system logs from EKS Worker Nodes EC2 VMs (eg. for support debug requests by vendors).

---

### `aws_eks_cluster_versions.sh`

Iterates EKS clusters to list each AWS EKS cluster name and version in the current account. Combine with `aws_foreach_profile.sh` and `aws_foreach_region.sh` to audit your EKS cluster versions across accounts and regions.

---

### `aws_eks_addon_versions.sh`

Lists the EKS addon versions available for the given cluster by checking its version before checking addons.

---

### `aws_eks_available_ips.sh`

Lists the number of available IP addresses in the EKS subnets for the given cluster (5 required for an EKS upgrade).

---

### `aws_eks_ami_create.sh`

Creates a custom EKS AMI quickly off the base EKS template and then running a shell script in it before saving it to a new AMI. See also [HariSekhon/Packer](https://github.com/HariSekhon/Packer) for more advanced build.

---

### `aws_kms_key_rotation_enabled.sh`

Lists [AWS KMS](https://aws.amazon.com/kms/) keys and whether they have key rotation enabled.

---

### `aws_kube_creds.sh`

Auto-loads all [AWS EKS](https://aws.amazon.com/eks/) clusters credentials in the current --profile and --region so your kubectl is ready to rock on AWS.

---

### `aws_kubectl.sh`

Runs kubectl commands safely fixed to a given [AWS EKS](https://aws.amazon.com/eks/) cluster using config isolation to avoid concurrency race conditions.

---

### `aws_logs_batch_jobs.sh`

Lists AWS Batch job submission requests and their callers.

---

### `aws_logs_ec2_spot.sh`

Lists AWS EC2 Spot fleet creation requests, their caller and first tag value for origin hint.

---

### `aws_logs_ecs_tasks.sh`

Lists AWS ECS task run requests, their callers and job definitions.

---

### `aws_meta.sh`

AWS [EC2 Metadata API](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) query shortcut. See also the official [ec2-metadata](https://aws.amazon.com/code/ec2-instance-metadata-query-tool/) shell script with more features.

---

### `aws_nat_gateways_public_ips.sh`

Lists the public IPs of all NAT gateways. Useful to give to clients to permit through firewalls for webhooks or similar calls.

---

### `aws_rds_list.sh`

List RDS instances with select fields - Name, Status, Engine, AZ, Instance Type, Storage.

---

### `aws_rds_open_port_to_my_ip.sh`

Adds a security group to an RDS DB instance to open its native database SQL port to your public IP address.

---

### `aws_rds_get_version.sh`

Quickly retrieve the version of an RDS database to know which JDBC jar version to download using `install/download_*_jdbc.sh` when setting up connections.

---

### `aws_route53_check_ns_records.sh`

Checks AWS [Route 53](https://aws.amazon.com/route53/) public hosted zones NS servers are delegated in the public DNS hierarchy and that there are no rogue NS servers delegated not matching the Route 53 zone configuration.

---

### `aws_sso_accounts.sh`

Lists all AWS SSO accounts the current SSO user has access to.

---

### `aws_sso_configs.sh`

Generates AWS SSO configs for all AWS SSO accounts the currently logged in SSO user has access to.

---

### `aws_sso_configs_save.sh`

Saves AWS SSO configs generated by `aws_sso_configs.sh` to `~/.aws/config` if they're not already found.

---

### `aws_sso_account_id_names.sh`

Parses AWS config for AWS SSO and outputs Account IDs and Profile names.

---

### `aws_sso_config_duplicate_sections.sh`

Lists duplicate AWS SSO config sections that are using the same sso_account_id. Useful to deduplicate configs containing a mix of hand crafted and automatically generated `aws_sso_configs.sh`.

---

### `aws_sso_config_duplicate_profile_names.sh`

Lists duplicate AWS SSO config profile names that are using the same sso_account_id.

---

### `aws_accounts_missing_from_config.sh`

For a list of AWS Account IDs in stdin or files, finds those missing from AWS config.

---

### `aws_sso_accounts_missing_from_list.sh`

For a list of AWS Account IDs in stdin or files, finds AWS SSO accounts in AWS config missing from the provided list.

---

### `aws_sso_env_creds.sh`

Retrieves AWS SSO session credentials in the format of environment export commands for copying to other systems like Terraform Cloud.

---

### `aws_sso_role_arn.sh`

Determines the currently authenticated AWS SSO user's base role ARN in IAM policy usable format.

---

### `aws_sso_role_arns.sh`

Prints all AWS SSO role ARNs in IAM policy usable format.

---

### `aws_profile_config_add_if_missing.sh`

Reads AWS profile config blocks from stdin and appends them to the `~/.aws/config` file if the profile section is not found.

---

### `aws_profile_generate_direnvs.sh`

Generates subdirectories containing the `config.ini` and `.envrc` for every AWS profile found in the given file or `$AWS_CONFIG_FILE` or `~/.aws/config`. Useful to take a large generated AWS `config.ini` from `aws_sso_configs.sh` and then split it into subdirectories for direnvs.

---

### `aws_s3_bucket.sh`

Creates an S3 bucket, blocks public access, enables versioning, encryption, and optionally locks out any given user/group/role ARNs via a bucket policy for safety (eg. to stop Power Users accessing a sensitive bucket like Terraform state).

---

### `aws_s3_buckets_block_public_access.sh`

Blocks public access to one or more given S3 buckets or files containing bucket names, one per line.

---

### `aws_s3_account_block_public_access.sh`

Blocks S3 public access at the AWS account level.

---

### `aws_s3_check_buckets_public_blocked.sh`

Iterates each S3 bucket and checks it has public access fully blocked via policy. Parallelized for speedup.

---

### `aws_s3_check_account_public_blocked.sh`

Checks S3 public access is blocked at the AWS account level.

---

### `aws_s3_sync.sh`

Syncs multiple AWS S3 URLs from file lists. Validates S3 URLs, source and destination list lengths matches, and optionally that path suffixes match, to prevent off-by-one human errors spraying data all over the wrong destination paths.

---

### `aws_s3_access_logging.sh`

Lists [AWS S3](https://aws.amazon.com/s3/) buckets and their [access logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html) status.

---

### `aws_s3_delete_bucket_with_versions.sh`

Deletes a bucket including all versions. Use with caution!

---

### `aws_spot_when_terminated.sh`

Executes commands when the [AWS EC2](https://aws.amazon.com/ec2/) instance running this script is notified of [Spot Termination](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html), acts as a latch mechanism that can be set any time after boot.

---

### `aws_sqs_check.sh`

Sends a test message to an [AWS SQS](https://aws.amazon.com/sqs/) queue, retrieves it to check and then deletes it via the receipt handle id.

---

### `aws_sqs_delete_message.sh`

Deletes 1-10 messages from a given [AWS SQS](https://aws.amazon.com/sqs/) queue (to help clear out test messages).

---

### `aws_ssm_put_param.sh`

Reads a value from a command line argument or non-echo prompt and saves it to AWS [Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html). Useful for uploading a password without exposing it on your screen.

---

### `aws_secret_list.sh`

Returns the list of secrets, one per line.

---

### `aws_secret_add.sh`

Reads a value from a command line argument or non-echo prompt and saves it to Secrets Manager. Useful for uploading a password without exposing it on your screen.

---

### `aws_secret_add_binary.sh`

Base64 encodes a given file's contents and saves it to Secrets Manager as a binary secret. Useful for uploading things like QR code screenshots for sharing MFA to recovery admin accounts.

---

### `aws_secret_update.sh`

Reads a value from a command line argument or non-echo prompt and updates a given Secrets Manager secret. Useful for updating a password without exposing it on your screen.

---

### `aws_secret_update_binary.sh`

Base64 encodes a given file's contents and updates a given Secrets Manager secret. Useful for updating a QR code screenshot for a root account.

---

### `aws_secret_get.sh`

Gets a secret value for a given secret from Secrets Manager, retrieving either a secure string or secure binary depending on which is available.

---

### `eksctl_cluster.sh`

Downloads [eksctl](https://eksctl.io/) and creates an [AWS EKS](https://aws.amazon.com/eks/) Kubernetes cluster.
