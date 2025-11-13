# Kubernetes Scripts

This directory contains scripts for managing Kubernetes resources.

---

### `.envrc-kubernetes`

Copy to `.envrc` for [direnv](https://direnv.net/) to auto-load the right Kubernetes `kubectl` context isolated to current shell to prevent race conditions between shells and scripts caused by otherwise naively changing the global `~/.kube/config` context.

---

### `aws/eksctl_cluster.sh`

Quickly spins up an [AWS EKS](https://aws.amazon.com/eks/) cluster using `eksctl` with some sensible defaults.

---

### `kubernetes_info.sh`

Huge [Kubernetes](https://kubernetes.io/) inventory listing of deployed resources across all namespaces in the current cluster / kube context.

---

### `kubectl.sh`

Runs kubectl commands safely fixed to a given context using config isolation to avoid concurrency race conditions.

---

### `kubectl_diff_apply.sh`

Generates a kubectl diff and prompts to apply.

---

### `kustomize_diff_apply.sh`

Runs Kustomize build, precreates any namespaces, shows a kubectl diff of the proposed changes, and prompts to apply.

---

### `kustomize_diff_branch.sh`

Runs Kustomize build against the current and target base branch for current or all given directories, then shows the diff for each directory. Useful to detect differences when refactoring, such as switching to tagged bases.

---

### `kubectl_create_namespaces.sh`

Creates any namespaces in yaml files or stdin, a prerequisite for a diff on a blank install, used by adjacent scripts for safety.

---

### `kubernetes_check_objects_namespaced.sh`

Checks Kubernetes yaml(s) for objects which aren't explicitly namespaced, which can easily result in deployments to the wrong namespace. Reads the API resources from your current Kubernetes cluster and if successful excludes cluster-wide objects.

---

### `kustomize_check_objects_namespaced.sh`

Checks Kustomize build yaml output for objects which aren't explicitly namespaced (uses above script).

---

### `kubectl_deployment_pods.sh`

Gets the pod names with their unpredictable suffixes for a given deployment by querying the deployment's selector labels and then querying pods that match those labels.

---

### `kubectl_get_all.sh`

Finds all namespaced Kubernetes objects and requests them for the current or given namespace. Useful because `kubectl get all` misses a lof of object types.

---

### `kubectl_get_annotation.sh`

Find a type of object with a given annotation.

---

### `kubectl_restart.sh`

Restarts all or filtered deployments/statefulsets in the current or given namespace. Useful when debugging or clearing application problems.

---

### `kubectl_logs.sh`

Tails all containers in all pods or filtered pods in the current or given namespace. Useful when debugging a distributed set of pods in live testing.

---

### `kubectl_kv_to_secret.sh`

Creates a Kuberbetes secret from `key=value` or shell export format, as args or via stdin (eg. piped from `aws_csv_creds.sh`).

---

### `kubectl_secret_values.sh`

Prints the keys and base64 decoded values within a given Kubernetes secret for quick debugging of Kubernetes secrets. See also: `gcp_secrets_to_kubernetes.sh`.

---

### `kubectl_secrets_download.sh`

Downloads all secrets in current or given namespace to local files of the same name, useful as a backup before migrating to Sealed Secrets.

---

### `kubernetes_secrets_compare_gcp_secret_manager.sh`

Compares each Kubernetes secret to the corresponding secret in GCP Secret Manager. Useful to safety check GCP Secret Manager values align before enabling [External Secrets](https://external-secrets.io/latest/) to replace them.

---

### `kubernetes_secret_to_external_secret.sh`

Generates an [External Secret](https://external-secrets.io/latest/) from an existing Kubernetes secret.

---

### `kubernetes_secrets_to_external_secrets.sh`

Generates [External Secrets](https://external-secrets.io/latest/) from all existing Kubernetes secrets found in the current or given namespace.

---

### `kubernetes_secret_to_sealed_secret.sh`

Generates a [Bitnami Sealed Secret](https://github.com/bitnami-labs/sealed-secrets) from an existing Kubernetes secret.

---

### `kubernetes_secrets_to_sealed_secrets.sh`

Generates [Bitnami Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets) from all existing Kubernetes secrets found in the current or given namespace.

---

### `kubectl_secrets_annotate_to_be_sealed.sh`

Annotates secrets in current or given namespace to allow being overwritten by Sealed Secrets (useful to sync ArgoCD health).

---

### `kubectl_secrets_not_sealed.sh`

Finds secrets with no SealedSecret ownerReferences.

---

### `kubectl_secrets_to_be_sealed.sh`

Finds secrets pending overwrite by Sealed Secrets with the managed annotation.

---

### `kubernetes_yaml_strip_live_fields.sh`

Strips live fields from Kubernetes yaml object dumps. Useful so you can do `kubectl diff` or `kubectl apply` without hitting annoying errors about immutable fields left in exports from `kubectl get ... -o yaml`.

---

### `kubernetes_foreach_context.sh`

Executes a command across all kubectl contexts, replacing `{context}` in each iteration (skips lab contexts `docker` / `minikube` / `minishift` to avoid hangs since they're often offline).

---

### `kubernetes_foreach_namespace.sh`

Executes a command across all kubernetes namespaces in the current cluster context, replacing `{namespace}` in each iteration.

---

### `kubernetes_api.sh`

Finds Kubernetes API and runs your curl arguments against it, auto-getting authorization token and auto-populating OAuth authentication header.

---

### `kubernetes_autoscaler_release.sh`

Finds the latest Kubernetes Autoscaler release that matches your local Kubernetes cluster version using kubectl and the GitHub API. Useful for quickly finding the image override version for `eks-cluster-autoscaler-kustomization.yaml` in the [Kubernetes configs](https://github.com/HariSekhon/Kubernetes-configs) repo.

---

### `kubernetes_etcd_backup.sh`

Creates a timestamped backup of the Kubernetes Etcd database for a kubeadm cluster.

---

### `kubernetes_delete_stuck_namespace.sh`

To forcibly delete those pesky kubernetes namespaces of 3rd party apps like Knative that get stuck and hang indefinitely on the finalizers during deletion.

---

### `kubeadm_join_cmd.sh`

Outputs `kubeadm join` command (generates new token) to join an existing Kubernetes cluster (used in [vagrant kubernetes](https://github.com/HariSekhon/DevOps-Bash-tools/tree/master/vagrant/kubernetes) provisioning scripts).

---

### `kubeadm_join_cmd2.sh`

Outputs `kubeadm join` command manually (calculates cert hash + generates new token) to join an existing Kubernetes cluster.

---

### `kubernetes_nodes_ssh_dump_logs.sh`

Fetch logs from Kubernetes nodes (eg. for support debug requests by vendors).

---

### `kubectl_exec.sh`

Finds and execs to the first Kubernetes pod matching the given name regex, optionally specifying the container name regex to exec to, and shows the full generated `kubectl exec` command line for clarity.

---

### `kubectl_exec2.sh`

Finds and execs to the first Kubernetes pod matching given pod filters, optionally specifying the container to exec to, and shows the full generated `kubectl exec` command line for clarity.

---

### `kubectl_pods_per_node.sh`

Lists number of pods per node sorted descending.

---

### `kubectl_pods_important.sh`

Lists important pods and their nodes to check on scheduling.

---

### `kubectl_pods_colocated.sh`

Lists pods from deployments/statefulsets that are colocated on the same node.

---

### `kubectl_node_labels.sh`

Lists nodes and their labels, one per line, easier to read visually or pipe in scripting.

---

### `kubectl_pods_running_with_labels.sh`

Lists running pods with labels matching key=value pair arguments.

---

### `kubectl_node_taints.sh`

Lists nodes and their taints.

---

### `kubectl_jobs_stuck.sh`

Finds Kubernetes jobs stuck for hours or days with no completions.

---

### `kubectl_jobs_delete_stuck.sh`

Prompts for confirmation to delete stuck Kubernetes jobs found by script above.

---

### `kubectl_images.sh`

Lists Kubernetes container images running on the current cluster.

---

### `kubectl_image_counts.sh`

Lists Kubernetes container images running counts sorted descending.

---

### `kubectl_image_deployments.sh`

Lists which deployments, statefulsets or daemonsets container images belong to. Useful to find which deployment, statefulset or daemonset to upgrade to replace a container image eg. when replacing deprecated the k8s.gcr.io registry with registry.k8s.io.

---

### `kubectl_pod_count.sh`

Lists Kubernetes pods total running count.

---

### `kubectl_pod_labels.sh`

Lists Kubernetes pods and their labels, one label per line for easier shell script piping for further actions.

---

### `kubectl_pod_ips.sh`

Lists Kubernetes pods and their pod IP addresses.

---

### `kubectl_container_count.sh`

Lists Kubernetes containers total running count.

---

### `kubectl_container_counts.sh`

Lists Kubernetes containers running counts by name sorted descending.

---

### `kubectl_pods_dump_stats.sh`

Dump stats from all pods matching a given regex and namespace to txt files for support debugging.

---

### `kubectl_pods_dump_logs.sh`

Dump logs from all pods matching a given regex and namespace to txt files for support debugging.

---

### `kubectl_pods_dump_jstacks.sh`

Dump Java jstacks from all pods matching a given regex and namespace to txt files for support debugging.

---

### `kubectl_pods_dump_all.sh`

Calls the above `kubectl_pods_dump_*.sh` scripts for N iterations with a given interval.

---

### `kubectl_empty_namespaces.sh`

Finds namespaces without any of the usual objects using `kubectl get all`.

---

### `kubectl_delete_empty_namespaces.sh`

Removes empty namespaces, uses `kubectl_empty_namespaces.sh`.

---

### `kubectl_alpine.sh`

Quick launch one-off pods for interactive debuggging in Kubernetes.

---

### `kubectl_busybox.sh`

Quick launch one-off pods for interactive debuggging in Kubernetes.

---

### `kubectl_curl.sh`

Quick launch one-off pods for interactive debuggging in Kubernetes.

---

### `kubectl_dnsutils.sh`

Quick launch one-off pods for interactive debuggging in Kubernetes.

---

### `kubectl_gcloud_sdk.sh`

Quick launch one-off pods for interactive debuggging in Kubernetes.

---

### `kubectl_run_sa.sh`

Launch a quick pod with the given service account to test private repo pull & other permissions.

---

### `kubectl_port_forward.sh`

Launches `kubectl port-forward` to a given pod's port with an optional label or name filter. If more than one pod is found, prompts with an interactive dialogue to choose one. Optionally automatically opens the forwarded localhost URL in the default browser.

---

### `kubectl_port_forward_spark.sh`

Does the above for Spark UI.

---

### `helm_template.sh`

Templates a Helm chart for Kustomize deployments.

---

### `kustomize_parse_helm_charts.sh`

Parses the [Helm](https://helm.sh/) charts from one or more `kustomization.yaml` files into TSV format for further shell pipe processing.

---

### `kustomize_install_helm_charts.sh`

Installs the [Helm](https://helm.sh/) charts from one or more `kustomization.yaml` files the old fashioned Helm CLI way so that tools like [Nova](https://github.com/FairwindsOps/nova) can be used to detect outdated charts (used in [Kubernetes-configs](https://github.com/HariSekhon/Kubernetes-configs) repo's [CI](https://github.com/HariSekhon/Kubernetes-configs/actions/workflows/nova.yaml)).

---

### `kustomize_update_helm_chart_versions.sh`

Updates one or more `kustomization.yaml` files to the latest versions of any charts they contain.

---

### `kustomize_materialize.sh`

Recursively materializes all `kustomization.yaml` to `kustomization.materialized.yaml` in the same directories for scanning with tools like [Pluto](https://github.com/FairwindsOps/pluto) to detect deprecated API objects inherited from embedded Helm charts. Parallelized for performance.

---

### `argocd_auto_sync.sh`

Toggle Auto-sync on/off to allow repairs and maintenance operation for a given app and also disables / re-enables the App-of-Apps base apps to stop then re-enabling the app.

---

### `argocd_apps_sync.sh`

Sync's all [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) apps matching an optional ERE regex filter on their names using the ArgoCD CLI.

---

### `argocd_apps_wait_sync.sh`

Sync's all [ArgoCD](https://argo-cd.readthedocs.io/en/stable/) apps matching an optional ERE regex filter on their names using the ArgoCD CLI's while also checking their health and operation.

---

### `argocd_generate_resource_whitelist.sh`

Generates a yaml cluster and namespace resource whitelist for ArgoCD project config. If given an existing yaml, will merge in its original whitelists, dedupe, and write them back into the file using an in-place edit. Useful because ArgoCD 2.2+ doesn't show resources that aren't explicitly allowed, such as ReplicaSets and Pods.

---

### `pluto_detect_helm_materialize.sh`

Recursively materializes all helm `Chart.yaml` and runs [Pluto](https://github.com/FairwindsOps/pluto) on each directory to work around [this issue](https://github.com/FairwindsOps/pluto/issues/444).

---

### `pluto_detect_kustomize_materialize.sh`

Recursively materializes all `kustomization.yaml` and runs [Pluto](https://github.com/FairwindsOps/pluto) on each directory to work around [this issue](https://github.com/FairwindsOps/pluto/issues/444).

---

### `pluto_detect_kubectl_dump_objects.sh`

Dumps all live Kubernetes objects to /tmp and runs [Pluto](https://github.com/FairwindsOps/pluto) to detect deprecated API objects on the cluster from any source.

---

### `rancher_api.sh`

Queries the Rancher API with authentication.

---

### `rancher_kube_creds.sh`

Downloads all Rancher clusters credentials into subdirectories matching cluster names, with `.envrc` in each, so a quick `cd` into one and your kubectl is ready to rock.
