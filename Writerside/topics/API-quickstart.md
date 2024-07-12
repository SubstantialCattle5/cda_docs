# Cli Command Reference 

## check 

Automates the Image Drill process. 

```Shell
cda export <pool_name> <vm_snapshot_name>
cda export-diff <pool_name> <vm_snapshot_name> 
```

### Description 

Saves a timestamp and checksum to the inbuilt log file of an `ceph_image` which can be later used for validation checks.

1. `export/export-diff` signifies which `rbd` command to perform. 
2. `<pool_name>` signifies the pool name where the snapshot is stored. 
3. `<vm_snapshot_name>` the snapshot which reqds the checksum operation 


## verify 
Verifies the integrity of a snapshot by comparing its current checksum with the saved checksum from DC and DR log files.
```Shell
cda verify <export/export-diff> <dc_log_file> <dr_log_file> <pool_name> <image_name>
```

### Description
Verifies the integrity of the given snapshot by comparing the current checksum with the ones stored in the DC and DR log files. This ensures the snapshot has not been altered since the last recorded checksum.

1. `<export/export-diff>` specifies whether to use export or export-diff.
2. `<dc_log_file>` specifies the path to the DC log file.
3. `<dr_log_file>` specifies the path to the DR log file.
4. `<pool_name>` signifies the pool name where the snapshot is stored.
5. `<image_name>` the snapshot to verify.

Example : 
```Shell
cda verify export /path/to/dc/logfile /path/to/dr/logfile mypool mysnapshot
```

## completion
Generates the autocompletion script for the specified shell.

```Shell
cda completion [shell]
```

### Description

Generates a script that enables autocompletion for the cda commands in the specified shell.

1.  `[shell]` is the optional argument to specify the shell type (e.g., bash, zsh). If not specified, it will generate for the default shell.
Example
```Shell
    cda completion zsh
    cda completion bash
```

## help
Displays help information about cda commands.
```Shell
cda help <command>
```

### Description

Provides detailed help and usage information for any specific cda command.

1. `<command>` is the command for which help is required.
Example

```Shell
cda help check
cda help verify
```
