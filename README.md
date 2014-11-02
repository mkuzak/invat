invat
=====
Source code used to study inversion in *Arabidopsis thaliana*.

Single-nucleotide polymorphism data have been obtained from [1001 genomes website](http://1001genomes.org).

Variant calling results are stored in different formats,
depending on the data provider (laboratory/project that did the sequencing and variant calling).
All data have been integrated into single common format.

Table describing matching beetween columns in original data and common format.

Columns are indexed from 1


| field     | common | mpi  | gmi  | salk | wtchg |
|-----------|--------|------|------|------|-------|
| accession | col1   | col1 | ---- | col1 | ----- |
| position  | col2   | col3 | col2 | col3 | col2  |
| variant   | col3   | col5 | col4 | col5 | col5  |

* Indels have been ignored.
* During the parsing, the 'ref' based have been compared to base in the reference sequence (TAIR10) and expected to be the equal.
