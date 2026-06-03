# offtarget-merge

## offtarget-merge - Cross-sample off-target genomic region consensus finder

## development and testing

The tool is developed in Rust, hence untill the basic 3 conditions are satisfied, it can used in wider range.

3 conditions

* glibc version - Should be in same version or higher version, but not lower than build version
* CPU design/architecture - Should be in same type
* Linux/Mac/Windows - OS type - Should be in same type


```
ldd --version  ## to check glibc version
uname -a  ## to check CPU architecture and OS type and version
```

> Developed/Build version details - x86_64 CPU type, Ubuntu 20.04 version and glibc 2.31 version


## usage condition

- This tool can be used to handle the output files of offtarget_counter binary tool
- This should be considered as a supportive tool to handle the large file and filter the proper window region with certain conditions
- As a Rust tool, handling large dataset with multithread options and effective memory handling will be done in ease.
