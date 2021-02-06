# Genome analysis tools

Here, I would record some tools for genome assembly, annotation, and comparative genomics analysis when I used during my projects. Also, some useful scripts would be included in this part.

## Genome assembly
### Short read sequencing
- Trinity (K-mer ≤ 32)
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

- SOAPdenovo (BGI)
- Velvet (?)

### Long read sequencing
- MECAT2 (PacBio)
```
$ mecat.pl config ecoli_config_file.txt
$ vi ecoli_config_file.txt
$ mecat.pl correct ecoli_config_file.txt
$ mecat.pl trim ecoli_config_file.txt
$ mecat.pl assemble ecoli_config_file.txt
# Run Pillon for local correction
$ java -jar pilon-1.23.jar --genome reference_genome.fasta --bam mecat2_mapped_Illumina_sorted.bam --fix all --output pillon_corrected
```

- NECAT (Nanopore)
## Genome annotation


## Comparative analysis
