# remote-source-manager

This script facilitates syncing code from a remote server to a local machine. It supports various commands to perform different operations:

**Downloading Code:**
To download code from the server, use the `-d down` or `--direction down` option. This will sync code from the server to the local machine.

**Uploading Code:**
To upload code to the server, use the `-d up` or `--direction up` option. This will sync code from the local machine to the server.

**Syncing Code:**
This will pull latest code from remote git repository, use the `-d sync` option.

**Downloading Binaries:**
To download binary files from the server, use the `-d bin` or `--direction bin` option.

**Dry Run:**
You can perform a dry run to check which files will be copied without actually performing the sync. Use the `-t` or `--test_run` option for this purpose.

## Changes Needed for Customization:
To customize this script for your use case, you need to update the configurations list with your specific configurations. Each configuration should include the following parameters:

- `name`: A descriptive name for the configuration.
- `source_path`: The path of the source code on the server.
- `destination_path`: The local destination path where the code will be synced.
- `remote_address`: The username and IP address (or alias) of the remote server.
- `output_file_remote_path`: The path of the output file on the server (only for binary downloads).
- `output_file_cmd`: The command to execute after downloading the binary file (optional).

## Setup Steps and Prerequisites:
Before running the script, ensure the following prerequisites are met:

- **Python 3:** Ensure Python 3 is installed on your system.
- **Dependencies:** This script has no external dependencies.
- **SSH Access:** Ensure you have SSH access to the remote server for syncing files.
- **Rsync Installed:** Ensure rsync is installed on both local and remote systems if you intend to sync files.
- **Git Installed:** If you plan to use the sync command, ensure git is installed on both local and remote systems.

## Example Configuration (Appendix):
Here's an example configuration format for the configurations list:

```python
configurations = [
    {
        "name": "ProjectName",
        "source_path": "<server-path>",
        "destination_path": "<local-path>",
        "remote_address": "user@ip",
        "output_file_remote_path": "apk path",
        "output_file_cmd": "adb root && sleep 1 && adb remount && sleep 1 && adb push <path to apk> <device path>"
    },
    # Add more configurations as needed
]
```
Replace placeholders like `<server-path>`, `<local-path>`, `user@ip`, and others with your actual paths and addresses.
