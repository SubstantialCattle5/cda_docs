# Ceph Drill Automation


## Introduction

Automate the process of verifying data integrity during disaster recovery drills in a Ceph storage cluster by using checksums and hashing. This ensures the integrity of RBD images transferred from the primary data center (DC) to the disaster recovery (DR) site without the need to launch a version of the image.

## Installation
**Note** : In this guide we describe using installation using .tar file. You can also clone it from [github](https://github.com/substantialcattle5/)
Install the file using 
```Shell
   wget localhost.com 
```
Then unzip the file 
```Shell
tar -xvzf <reqd_release>.tar.gz
```
Then provide enough permissions tfo execute 
```Shell
chmod a+x cda.sh
```


## Basic workflow
Once installed, you can invoke CLI commands directly from your OS command line through the `cephautomationdrill` executable. 
See the available commands by entering the following:
```Shell
cda --help
```
Get help on an individual command using the following construct. 
Substitute any command, like verify, check, etc., where you see generate in the example below to get detailed help 
on that command:
```Shell
cda verify --help 
```
To run a basic drill check, go to the ceph center and run the following command ,
replacing the names with your own: 
```Shell
cda check <pool-name> <image-name> 
```
The results would get stored in `checksum` directory,the structure is as follows : 
```Shell
checksums/
├── export
│        └── <poolname>_<imagename>.log
│        └── <poolname>_<imagename>.log
│        └── <poolname>_<imagename>.log
├── export-diff
│        └── <poolname>_<imagename>.log
└── verify
        └── <poolname>_<imagename>.log
```

## CLI command syntax

All `cda` commands follow the same format:
```Shell
cda commandOrAlias requiredArg [optionalArg] [options]
```

For example:
```Shell
cda check pool1 vm_state1 
```


### Command Overview 

Run `cephautomationdrill <command> --help` for any of the following commands to see command-specific options
See usage for detailed descriptions for each command.

| Command    | Alias | Description                              |
|------------|-------|------------------------------------------|
| check      | c     | This command generates a hash of the given snapshot and saves it in a log file. |
| completion |       | Generates and/or modifies files based on a schematic. |
| verify     |       |  Generate the autocompletion script for the specified shell                     |
| help       | h     |  Help about any command. |

<seealso>

<!--List any additional resources, such as tutorials or guides, that can help users understand and use the API effectively.-->

</seealso>
