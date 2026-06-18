# Rust_Projects  - Bioinformatics

This repository is a small initiation of Rust projects in Bioinformatics.

It is fully developed, maintained and provided with the goal of useful and production grade effective binary tools for parallel computing.

## mapq_counter

A Terminal binary rust tool developed for effective mapq distributions calculation on BAM file.

The tool use BAM file as priamry input with BED File for targeted screening and selected threshold based mapq read count calculations.

mapq values are highly effective and needs to be monitored in WES analysis, hence short read tech and genome complexity increases the chance of false positives.

mapq values also can be used to track the read count dynamics in highly homology regions and repetitve regions or phenotype known gene familys.

## offtarget_counter

offtarget_counter is the binary tool developed using Rust Program to calculate off target regions aligned reads from the given BAM and BED file.

offtarget_counter tool supports multi-threading option and works on linux platform with no requirement of additional tool or package installation.

offtarget calculation will helps to explore the efficiency of library preparation steps, especially the captured and sequenced reads came from pcr or target or not. Higher the offtarget region reads lower than depth of final variants.

