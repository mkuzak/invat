invat
=====
Source code used to study inversion in *Arabidopsis thaliana*.

Single-nucleotide polymorphism data have been obtained from [1001 genomes website](http://1001genomes.org).

Variant calling results are stored in different formats,
depending on the data provider (laboratory/project that did the sequencing and variant calling).

Data sources:
-------------
**mpi:**  
``filtered_variant.txt``  

**gmi:**  
``<accession_name>.<accession_id.0cf>.snp``

**salk:**  
``quality_variant_filtered_<strain_name>.txt``

**wtchg**  
``<accession_name>.v7c.sdi``

Data integration:
-----------------

* All data have been integrated into single common format.
* Columns are indexed from 1
* Only first 8Mb of the chr4 sequence is taken
* Indels have been ignored.
* During the parsing, the 'ref' based have been compared to base in the reference sequence (TAIR10) and expected to be the equal.

Table describing matching between columns in original data and common format.


| field     | common | mpi  | gmi  | salk | wtchg |
|-----------|--------|------|------|------|-------|
| accession | col1   | col1 | ---- | col1 | ----- |
| position  | col2   | col3 | col2 | col3 | col2  |
| variant   | col3   | col5 | col4 | col5 | col5  |

Data analysis and visualisation:
--------------
* import SNP table generated in previous steps
* import reference sequence (TAIR10 chr4)
* for each accession generate the sequence based
on reference sequence by substituting reference base with variant base at each variant location
* use a moving window of 10 kb and shift it every 1 kb
* within each window calculate edit distance between every pair of accessions:  
distance is calculated using neditStartingAt function in Biocoductor's Biostrings package, it takes into account IUPAC codes (fixed=FALSE option) for base encoding (which are present in variant calls from some of the projects)
* put a distance value in the middle of each window
* for distance plots (not the heatmap) the distances are normalised to one, mening 0: same sequence, 1: completly different sequence ( (window_width - dist)/window_width )
* to generate the heatmap, first hierarchical clustering is done on the distances (hclust R function) (the tree represents this clustering) then the order originating from the clustering is used to order accessions in the heatmap
