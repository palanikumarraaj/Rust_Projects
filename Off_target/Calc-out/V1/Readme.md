# Off Target Calculation and TSV output generation from BAM file

## offtarget_counter

offtarget_counter is the binary tool developed using Rust Program to calculate off target regions from the given BAM and BED file.

offtarget_counter tool supports multi-threading option and works on linux platform with no requirement of additional tool or package installation.

## Usage for a set of BAM files

- For loop based option to make TSV output files for a given BAM files

```
for f in *.bam ; do ./offtarget_counter --bed /mnt/NGS/Database/hg38_exome_comp_spikein_v2.0.2_targets_sorted.re_annotated.bed -t 20 -f /mnt/NGS/Database/resources_broad_hg38_v0_Homo_sapiens_assembly38.fasta -i $f -o $f"_off.tsv" ; done
```

- Off-target calculation is usually checked for a batch of samples


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

## usage and help option

```

$  ./offtarget_counter --help

Identifies reads in a BAM file that lie completely outside all regions defined in the provided BED file.
Output TSV columns: chr, start, end, read_id, mapq, orientation, read_length.

Usage: offtarget_counter [OPTIONS] --input <BAM> --output <OUTPUT> --bed <BED> --fasta <FASTA>

Options:
  -i, --input <BAM>
          Input BAM file (coordinate-sorted; .bai index is NOT required)

  -o, --output <OUTPUT>
          Output TSV file path

  -b, --bed <BED>
          BED file (≥3 columns: chr, start, end[, name…])

  -f, --fasta <FASTA>
          Reference FASTA file (.fai index must already exist alongside it)

  -t, --threads <THREADS>
          Number of writer threads
          
          [default: 4]

  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version
```

