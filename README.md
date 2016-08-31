Installation


First, you need to decompress the zip file:

$ unzip CAT.zip

This will generate the folder CAT and inside it the folders bin and documentation

The folder documentation contains the databases with taxonomic information and the third-party programs used by CAT: diamond and prodigal

You need to use diamond to create the nr database by following the instructions here:

 http://ab.inf.uni-tuebingen.de/data/software/diamond/download/public/manual.pdf

inside the documentation folder do:

$diamond makedb –in nr.faa -d nr

Once you have inside this folder the nr.dmnd  file generated by the previous step, you can run CAT.

The user also needs to download the NCBI taxonomy files found in ftp://ftp.ncbi.nlm.nih.gov/pub/taxonomy/:



gi_taxid_prot.dmp
names.dmp
nodes.dmp




Running CAT

Go to the folder bin and run:

$python cat.py input_contigs_file N C

N = numeric, the number of threads you want for the diamond search

C= The bit-score cut off (numeric 0.1 - 1)




Output files:

CAT will generate the following output files:


Main files:

A file with the taxonomic classification of the predicted genes:  contigs_prodigal.m8.proteinsclassification.tab

This file contains the following columns:

Contig
Predicted protein
Taxon ID of the taxon to which it was classified
Taxon to which it was classified  (T)
Rank of the classification
The number of proteins within 90% range of the bitscore of the top hit 
Average bitscore of the proteins within 90% range of the bitscore of the top hit (B)
The amino-acid sequence of the protein




And  a file with the classification of the contigs: contigs_prodigal.m8.contigclassification.tab

This file contains the following columns:

Contig
Superkingdom
Phylum
Class
Order
Family
Genus
Species


Intermediate files:

contigs_prodigal.faa
(fasta file containing predicted genes in protein sequence)

contigs_prodigal.fna
(fasta file containing predicted genes in nucleotide)

contigs_prodigal.gff
(file mapping the predicted genes to their contigs)

contigs_prodigal.m8 
(file with diamond blast results)

and other files related to the diamond input.
