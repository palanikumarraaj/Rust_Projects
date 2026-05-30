# Off Target Calculation and TSV output generation from BAM file

## offtarget_counter

offtarget_counter is the binary tool developed using Rust Program to calculate off target regions from the given BAM and BED file.

offtarget_counter tool supports multi-threading option and works on linux platform with no requirement of additional tool or package installation.

## Usage for a set of BAM files

- For loop based option to make TSV output files for a given BAM files

> for f in *.bam ; do ./offtarget_counter --bed /mnt/NGS/Database/hg38_exome_comp_spikein_v2.0.2_targets_sorted.re_annotated.bed -t 20 -f /mnt/NGS/Database/resources_broad_hg38_v0_Homo_sapiens_assembly38.fasta -i $f -o $f"_off.tsv" ; done


- Off-target calculation is usually checked for a batch of samples
