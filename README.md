# fasta-sequence-orf-analyzer

# Multi-FASTA Sequence & Open Reading Frame (ORF) Analyzer

A Python bioinformatics pipeline built with **Biopython**, **Pandas**, and **Matplotlib** to perform cross-species nucleotide profiling, sliding-window GC analysis, three-frame Open Reading Frame (ORF) translation, and ortholog sequence comparison on real NCBI genomic records.

## Dataset Analyzed
- ***Homo sapiens* *TP53* genomic locus** (`NC_000017.11:c7687490-7668421`, 19,070 bp)
- ***Rattus norvegicus* *Tp53* genomic locus** (`NC_086028.1:54798882-54810300`, 11,419 bp)
- ***Danio rerio* *tp53* genomic locus** (`NC_141025.1:25128576-25140154`, 11,579 bp)

## Pipeline Modules & Key Findings
1. **Multi-FASTA Ingestion (`Bio.SeqIO`):** Parses multi-record NCBI FASTA files and extracts sequence metadata and lengths.
2. **Nucleotide Composition & Sliding-Window GC Profiling (`Bio.SeqUtils`):** Identifies an evolutionary GC-content gradient across vertebrate *TP53* orthologs (**49.38%** in human, **47.34%** in rat, **36.03%** in zebrafish) and maps localised exonic GC peaks using a 500 bp sliding window.
3. **ORF Detection & Protein Translation:** Scans all three forward reading frames (`ATG` start to `TAA/TAG/TGA` stop codons, trimmed to codon boundaries), detecting **18 candidate exonic/intronic ORFs ($\ge 50\text{ aa}$)** in the unspliced human *TP53* locus.
4. **Ortholog Variant & Alignment Comparison (`Bio.Align.PairwiseAligner`):** Contrasts naive positional base indexing (8,553 unaligned mismatches due to intronic indels) against global pairwise sequence alignment (score = **978.0** over the initial 2,000 bp).

## Tech Stack
- **Language:** Python 3
- **Libraries:** Biopython, Pandas, Matplotlib, Seaborn
- **Environment:** Google Colab / Jupyter Notebook
