# Docker Scripts

This directory contains scripts for managing Docker resources.

---

### `dockerhub_api.sh`

Queries DockerHub API v2 with or without authentication (`$DOCKERHUB_USER` & `$DOCKERHUB_PASSWORD` / `$DOCKERHUB_TOKEN`).

---

### `docker_api.sh`

Queries a Docker Registry with optional basic authentication if `$DOCKER_USER` & `$DOCKER_PASSWORD` are set.

---

### `docker_build_hashref.sh`

Runs `docker build` and auto-generates docker image name and tag from relative Git path and commit short SHA hashref and a dirty sha suffix if git contents are modified. Useful to compare docker image sizes between your clean and modified versions of `Dockerfile` or contents.

---

### `docker_package_check.sh`

Runs package installs on major versions of a docker image to check given packages are available before adding them and breaking builds across linux distro versions.

---

### `docker_registry_list_images.sh`

Lists images in a given private Docker Registry.

---

### `docker_registry_list_tags.sh`

Lists tags for a given image in a private Docker Registry.

---

### `docker_registry_get_image_manifest.sh`

Gets a given image:tag manifest from a private Docker Registry.

---

### `docker_registry_tag_image.sh`

Tags a given image with a new tag in a private Docker Registry via the API without pulling and pushing the image data (must faster and more efficient).

---

### `dockerhub_list_tags.sh`

Lists tags for a given DockerHub repo. See also [dockerhub_show_tags.py](https://github.com/HariSekhon/DevOps-Python-tools/blob/master/dockerhub_show_tags.py) in the [DevOps Python tools](https://github.com/HariSekhon/DevOps-Python-tools) repo.

---

### `dockerhub_list_tags_by_last_updated.sh`

Lists tags for a given DockerHub repo sorted by last updated timestamp descending.

---

### `dockerhub_search.sh`

Searches with a configurable number of returned items (older docker cli was limited to 25 results).

---

### `clean_caches.sh`

Cleans out OS package and programming language caches, call near end of `Dockerfile` to reduce Docker image size.

---

### `quay_api.sh`

Queries the [Quay.io](https://quay.io/) API with OAuth2 authentication token `$QUAY_TOKEN`.
