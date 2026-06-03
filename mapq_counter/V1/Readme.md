# mapq_counter Binary tool

## mapq_counter tool for calculation of targeted BED file based MAPQ-Read count distribution

Most of BAM related coverage/depth tool focus only on Read counts based Coverage and Depth alone.

The distribution of MAPQ in targeted regions are not calculated or noted.

This tool focus on tracking all available mapq based reads.

## mapq_counter tool usage

```
$ ./mapq_counter --help

Counts reads per MAPQ score for each region in a 4-column BED file.
Requires a BAM index (.bai) file alongside the input BAM.

Output columns: chrom, start, end, name, mapq, count

Usage: mapq_counter [OPTIONS] --input <BAM> --bed <BED>

Options:
  -i, --input <BAM>
          Input BAM file (must have .bai index)

  -o, --output <FILE>
          Output file (use '-' for stdout)
          
          [default: -]

  -t, --threads <INT>
          Number of threads for parallel region processing
          
          [default: 4]

  -b, --bed <BED>
          BED file with regions (4 columns: chrom, start, end, name)

  -q, --min-mapq <INT>
          Minimum MAPQ score to include (0 = all reads)
          
          [default: 0]

      --exclude-unmapped
          Exclude unmapped reads (MAPQ = 255)

  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version
```

## usage

```
mapq_counter -i 121923_BatchEXT579_BQSR.bam -b /mnt/NGS/Database/hg38_exome_comp_spikein_v2.0.2_targets_sorted.re_annotated.bed --exclude-unmapped -t 30 -o 121923_mapq.tsv
```

The binary file can be copied and used directly for respective BAM and BED file used.

If unmapped regions are not to be used then ** --exclude-unmapped ** can be used


```
for f in *.bam ; do ./mapq_counter -i $f -b /mnt/NGS1/WES_Analysis/Database/hg38_exome_comp_spikein_v2.0.2_targets_sorted.re_annotated.bed -t 30 -o $f"_mapq.tsv" ; done
```

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

