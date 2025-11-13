# Jenkins Scripts

This directory contains scripts for managing Jenkins CI.

The Bash scripts can execute from the git clone, but the `*.groovy` scripts needs to be pasted into the Jenkins Console at `$JENKINS_URL/script` which you can browse to:

Jenkins -> Manage Jenkins -> Script Console

---

### `jenkins.sh`

One-touch [Jenkins CI](https://jenkins.io/): launches Docker container, installs plugins, validates `Jenkinsfile`, configures job, triggers build, and tails results in terminal.

---

### `jenkins_api.sh`

Queries the Jenkins Rest API, handles authentication, pre-fetches CSFR protection token crumb, and supports many environment variables for ease of use.

---

### `jenkins_jobs.sh`

Lists Jenkins jobs (pipelines).

---

### `jenkins_foreach_job.sh`

Runs a templated command for each Jenkins job.

---

### `jenkins_jobs_download_configs.sh`

Downloads all Jenkins job configs to xml files of the same name.

---

### `jenkins_job_config.sh`

Gets or sets a Jenkins job's config.

---

### `jenkins_job_description.sh`

Gets or sets a Jenkins job's description.

---

### `jenkins_job_enable.sh`

Enables a Jenkins job by name.

---

### `jenkins_job_disable.sh`

Disables a Jenkins job by name.

---

### `jenkins_job_trigger.sh`

Triggers a Jenkins job by name.

---

### `jenkins_job_trigger_with_params.sh`

Triggers a Jenkins job with parameters.

---

### `jenkins_jobs_enable.sh`

Enables all Jenkins jobs/pipelines with names matching a given regex.

---

### `jenkins_jobs_disable.sh`

Disables all Jenkins jobs/pipelines with names matching a given regex.

---

### `jenkins_builds.sh`

Lists Jenkins latest builds for every job.

---

### `jenkins_cred_add_cert.sh`

Creates a Jenkins certificate credential from a PKCS#12 keystore.

---

### `jenkins_cred_add_kubernetes_sa.sh`

Creates a Jenkins Kubernetes service account credential.

---

### `jenkins_cred_add_secret_file.sh`

Creates a Jenkins secret file credential from a file.

---

### `jenkins_cred_add_secret_text.sh`

Creates a Jenkins secret string credential from a string or a file.

---

### `jenkins_cred_add_ssh_key.sh`

Creates a Jenkins SSH key credential from a string or an SSH private key file.

---

### `jenkins_cred_add_user_pass.sh`

Creates a Jenkins username/password credential.

---

### `jenkins_cred_delete.sh`

Deletes a given Jenkins credential by id.

---

### `jenkins_cred_list.sh`

Lists Jenkins credentials IDs and Names.

---

### `jenkins_cred_update_cert.sh`

Updates a Jenkins certificate credential from a PKCS#12 keystore.

---

### `jenkins_cred_update_kubernetes_sa.sh`

Updates a Jenkins Kubernetes service account credential.

---

### `jenkins_cred_update_secret_file.sh`

Updates a Jenkins secret file credential from a file.

---

### `jenkins_cred_update_secret_text.sh`

Updates a Jenkins secret string credential from a string or a file.

---

### `jenkins_cred_update_ssh_key.sh`

Updates a Jenkins SSH key credential from a string or an SSH private key file.

---

### `jenkins_cred_update_user_pass.sh`

Updates a Jenkins username/password credential.

---

### `jenkins_cli.sh`

Shortens `jenkins-cli.jar` command by auto-inferring basic configuations, auto-downloading the CLI if absent, and handling authentication.

---

### `jenkins_foreach_job_cli.sh`

Runs a templated command for each Jenkins job using the Jenkins CLI.

---

### `jenkins_create_job_parallel_test_runs.sh`

Creates a freestyle parameterized test sleep job and launches N parallel runs of it to test scaling and parallelization of Jenkins agents.

---

### `jenkins_create_job_check_gcp_serviceaccount.sh`

Creates a freestyle test job which runs a GCP Metadata query to determine the GCP serviceaccount the agent pod is operating under.

---

### `jenkins_jobs_download_configs_cli.sh`

Downloads all Jenkins job configs to xml files of the same name using the Jenkins CLI.

---

### `jenkins_password.sh`

Gets Jenkins admin password from local docker container.

---

### `jenkins_plugins_latest_versions.sh`

Finds the latest versions of given Jenkins plugins.

---

### `check_jenkinsfiles.sh`

Validates all `*Jenkinsfile*` files in the given directory trees using the online Jenkins validator.
