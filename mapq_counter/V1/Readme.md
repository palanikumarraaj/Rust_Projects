# mapq_counter Binary tool

## mapq_counter tool for calculation of targeted BED file based MAPQ-Read count distribution

Most of BAM related coverage/depth tool focus only on Read counts based Coverage and Depth alone.

The distribution of MAPQ in targeted regions are not calculated or noted.

This tool focus on tracking all available mapq based reads.

## mapq_counter tool usage

```
./mapq_counter --help
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

