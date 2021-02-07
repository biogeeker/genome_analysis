# Genome analysis tools

Here, I would record some tools for genome assembly, annotation, and comparative genomics analysis when I used during my projects. Also, some useful scripts would be addded into this chapter.

## Genome assembly
### Short read sequencing
- Trinity (k-mer ≤ 32)
```
# Trinity default k-mer 25, maximum 32
$ Trinity --seqType fq --left reads_1.fq --right reads_2.fq --CPU 6 --max_memory 20G 
```

- SPAdes (Metagenome)
```
# -k: max k-mer
# -l: min k-mer
# -s: step size
# --rna: this flag is required for RNA-Seq data
# --plasmid: runs plasmidSPAdes pipeline for plasmid detection
$ /bin/spades.py --rna -k 21,27,33,55,77,99,127 -1 R1.fastq -2 R2.fastq -o spades_out_dir/
```

- SOAPdenovo (The Beijing Genomics Institute)
- Velvet (de Bruijn)
```
$ velveth output 31,37,2 -shortPaired -fasta -separate left.fa right.fa
# output/ based on velveth output
$ velvetg output/ -min_contig_lgth 500 \
  -exp_cov auto -cov_cutoff auto \
  -clean yes -scaffolding yes -amos_file yes
```

### Long read sequencing
Some tools for PacBio long reads assembly:
- MECAT2 (PacBio)*
```
$ mecat.pl config ecoli_config_file.txt
$ vi ecoli_config_file.txt
$ mecat.pl correct ecoli_config_file.txt
$ mecat.pl trim ecoli_config_file.txt
$ mecat.pl assemble ecoli_config_file.txt
# Run Pillon for local bases polish
$ java -jar pilon-1.23.jar --genome reference_genome.fasta --bam mecat2_mapped_Illumina_sorted.bam --fix all --output pillon_corrected
```
- falcon (PacBio)

Some tools for Nanopore long reads assembly:
- NECAT (Nanopore)*
```
```
- Shasta (Nanopore)

## Post-assembly stage
Some tools were used for sequencing errors correction after assembly:
- Pilon (polish using short reads)
- Racon (polish using long reads)
- NextPolish (polish using short reads)
- Medaka (Nanopore polish using long reads after Racon polish at least once)

Some tools that assisted an assembly of heterozygous/polymorphic genomes (remove redundant sequence):
- 
- HaploMerger2 (untangle allelic relations between haplotype sequences in a highly-polymorphic diploid assembly, and then reconstruct and output two separated haploid sub-assemblies)

## Genome annotation


## Comparative analysis
