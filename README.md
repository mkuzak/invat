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

Table describing matching beetween columns in original data and common format.


| field     | common | mpi  | gmi  | salk | wtchg |
|-----------|--------|------|------|------|-------|
| accession | col1   | col1 | ---- | col1 | ----- |
| position  | col2   | col3 | col2 | col3 | col2  |
| variant   | col3   | col5 | col4 | col5 | col5  |
