# Bin Scripts

This directory contains general purpose scripts.

---

### `login.sh`

Logs to major Cloud platforms if their credentials are found in the environment, CLIs such as AWS, GCP, Azure, GitHub... Docker registries: DockerHub, GHCR, ECR, GCR, GAR, ACR, Gitlab, Quay...

---

### `clean_caches.sh`

Cleans out OS package and programming language caches - useful to save space or reduce Docker image size.

---

### `crypto_dice_rolls.sh`

Generates 100 random dice rolls to test a new crypto hardware wallet's fidelity (do not use this for your real crypto seed as your machine could be infected with malware which steals your seed phrase).

---

### `delete_duplicate_files.sh`

Deletes duplicate files with (N) suffixes, commonly caused by web browser downloads, in the given or current directory.

---

### `download_url_file.sh`

Downloads a file from a URL using wget with no clobber and continue support, or curl with atomic replacement to avoid race conditions.

---

### `curl_auth.sh`

Shortens `curl` command by auto-loading your OAuth2 / JWT API token or username & password from environment variables or interactive starred password prompt.

---

### `find_duplicate_files*.sh`

Finds duplicate files by size and/or checksum in given directory trees.

---

### `find_broken_links.sh`

Find broken links with delays to avoid tripping defenses.

---

### `find_broken_symlinks.sh`

Find broken symlinks pointing to non-existent files/directories.

---

### `find_lock.sh`

Tries to find if a lockfile is used in the given or current working directory by taking snapshots of the file list before and after a prompt in which you should open/close an application.

---

### `foreach_path_bin.sh`

Runs each binary of the given name found in `$PATH` with the args given.

---

### `http_duplicate_urls.sh`

Find duplicate URLs in a given web page.

---

### `ldapsearch.sh`

Shortens `ldapsearch` command by inferring switches from environment variables.

---

### `ldap_user_recurse.sh` / `ldap_group_recurse.sh`

Recurse Active Directory LDAP users upwards to find all parent groups, or groups downwards to find all nested users.

---

### `linux_distro_versions.sh`

Quickly returns the list of major versions for a given Linux distro.

---

### `diff_line_threshold.sh`

Compares two files vs a line count diff threshold to determine if they are radically different.

---

### `organize_downloads.sh`

Moves files of well-known extensions in the `$HOME/Downloads` directory older than 1 week to capitalized subdirectories of their type.

---

### `copy_to_clipboard.sh`

Copies stdin or string arg to system clipboard on Linux or Mac.

---

### `paste_from_clipboard.sh`

Pastes from system clipboard to stdout on Linux or Mac.

---

### `paste_from_clipboard_upon_changes.sh`

Pastes from system clipboard to stdout on Linux or Mac whenever the clipboard changes.

---

### `paste_diff_settings.sh`

Takes snapshots of before and after clipboard changes and diffs them to show config changes.

---

### `processes_ram_sum.sh`

Sums the RAM usage of all processes matching a given regex in GB to one decimal place.

---

### `pldd.sh`

Parses `/proc` on Linux to show the runtime `.so` loaded dynamic shared libraries a program pid is using.

---

### `random_select.sh`

Selects one of given args at random.

---

### `random_number.sh`

Prints a random integer between two integer arguments (inclusive).

---

### `random_string.sh`

Prints a random alphanumeric string of a given length.

---

### `shields_embed_logo.sh`

Base64 encodes a given icon file or url and prints the `logo=...` url parameter you need to add the [shields.io](https://shields.io/) badge url.

---

### `shorten_text_selection.sh`

Shortens the selected text in the prior window.

---

### `shred_file.sh`

Overwrites a file 7 times to DoD standards before deleting it to prevent recovery of sensitive information.

---

### `shred_free_space.sh`

Overwrites free space to prevent recovery of sensitive information for files that have already been deleted.

---

### `split.sh`

Split large files into N parts (defaults to the number of your CPU cores) to parallelize operations on them.

---

### `ssl_get_cert.sh`

Gets a remote `host:port` server's SSL cert in a format you can pipe, save and use locally.

---

### `ssl_verify_cert.sh`

Verifies a remote SSL certificate.

---

### `ssl_verify_cert_by_ip.sh`

Verifies SSL certificates on specific IP addresses.

---

### `tmux_vertical.sh`

Launches tmux with N-way vertical shell split or commands given as args in equally balanced vertical panes.

---

### `tmux_horizontal.sh`

Same as above but split horizontally.

---

### `tmux_square.sh`

Same as above but with 4 panes in a square tiled view.

---

### `urlencode.sh` / `urldecode.sh`

URL encode/decode quickly on the command line, in pipes etc.

---

### `urlextract.sh`

Extracts the URLs from a given string arg, file or standard input.

---

### `url_extract_redirects.sh`

Extracts the URLs from a given string arg, file or standard input, queries each one and outputs the redirected urls instead to stdout.

---

### `url_replace_redirects.sh`

Extracts the URLs from a given string arg, file or standard input, queries each one and outputs the entire contents to stdout with the urls replaced by the redirected urls.

---

### `urlopen.sh`

Opens the URL given as an arg, or first URL found from stdin or a given file.

---

### `vagrant_hosts.sh`

Generate `/etc/hosts` output from a `Vagrantfile`.

---

### `vagrant_total_mb.sh`

Calculate the RAM committed to VMs in a `Vagrantfile`.

---

### `mac_diff_settings.sh`

Takes before and after snapshots of UI setting changes and diffs them to make it easy to find `defaults` keys to add to `setup/mac_settings.sh` to save settings.

---

### `mac_restore_file.sh`

Checks all the backup mount points for the latest backup that has a given file and then restores it.

---

### `mac_find_excluded_backup_paths.sh`

Does a deep search for excluded backup paths on file/folder attributes.

---

### `mac_iso_to_usb.sh`

Converts a given ISO file to a USB bootable image and burns it onto a given or detected inserted USB drive.
