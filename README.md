Clinical Variant Interpretation & Annotation Pipeline

Genetic Disorders Analyzed:

1.Cystic Fibrosis (CFTR)

2.Marfan Syndrome (FBN1)

3.Tay-Sachs Disease (HEXA)

Project Overview

This project simulates a clinical genomics workflow for three genetic disorders. The steps include:

1.Selecting a pathogenic variant from ClinVar.

2.Extracting phenotype information from OMIM.

3.Examining variant coordinates in UCSC Genome Browser.

4.Evaluating AlphaMissense and REVEL pathogenicity scores.

5.Applying ACMG/AMP guidelines.

6.Formatting variants into a VCF file.

7.Annotating variants using SnpEff via CLI.

This workflow demonstrates how raw genomic variants are interpreted into clinically meaningful conclusions.

🧬 Variants Overview
Genetic Disorder	Variation	Gene	Type (Consequence)	Condition	Classification	Explanation	Phenotype	AlphaMissense	REVEL	ACMG/AMP
Cystic Fibrosis	NM_000492.4(CFTR):c.-9_14del (p.Met1fs)	CFTR	Deletion	Cystic fibrosis	Pathogenic	This CFTR variant deletes phenylalanine at position 508, causing misfolding and defective trafficking. Severe reduction in chloride channel activity leads to classic CF symptoms.	Chronic lung infections	No score at deletion site; AlphaMissense only scores missense variants	No REVEL score at deletion site	PVS1, PM2, PP3
Marfan Syndrome	NM_000138.5(FBN1):c.8554_8561delinsTATCAC (p.Asp2852fs)	FBN1	Deletion (frameshift)	Marfan syndrome	Pathogenic	This FBN1 missense variant replaces a conserved cysteine, disrupting disulfide bonds and fibrillin-1 stability. Loss of proper fibrillin-1 structure affects aorta, lens, skeleton.	Tall stature, long limbs	High pathogenicity scores (red) at chr15:48,411,041	High REVEL scores (red bars) at Asp2852 region	PVS1, PM2, PP1
Tay-Sachs Disease	NM_000520.6(HEXA):c.1549dup (p.Leu517fs)	HEXA	Duplication	Tay-Sachs disease	Pathogenic	This HEXA frameshift variant inserts four nucleotides, creating a premature stop codon. Loss of enzyme activity leads to GM2 ganglioside accumulation and neurodegeneration.	Progressive neurodegeneration	High pathogenicity scores (red) at chr15:72,344,107	High REVEL scores (red bars) at Leu517 region	PVS1, PM2, PP3
🧬 Gene-Phenotype Relationships
Cystic Fibrosis (CFTR)

CFTR variants are associated with Cystic Fibrosis and related disorders such as bronchiectasis, congenital absence of vas deferens, pancreatitis, and elevated sweat chloride.
Inheritance is mostly autosomal recessive, sometimes dominant depending on the phenotype.

This gene is linked to multiple conditions, demonstrating pleiotropy.

Marfan Syndrome (FBN1)

FBN1 mutations cause Marfan Syndrome, an autosomal dominant connective tissue disorder with:

Tall stature

Long limbs (arachnodactyly)

Joint hypermobility

Aortic root dilation

Ocular manifestations (ectopia lentis)

One gene (FBN1) can affect multiple connective tissue disorders.

Tay-Sachs Disease (HEXA)

HEXA mutations cause Tay-Sachs Disease, an autosomal recessive neurodegenerative disorder.

Key Features:

Progressive developmental delay

Loss of motor skills

Seizures

Vision/hearing impairment

Infantile onset, fatal by age 5

Lab Findings:

Hexosaminidase A deficiency

GM2 ganglioside accumulation

Ballooned neurons

🧬 UCSC Genome Browser Analysis

CFTR: AlphaMissense & REVEL → no scores at deletion site (frameshift, not SNV).

FBN1: High AlphaMissense & REVEL scores (red bars) at Asp2852.

HEXA: High AlphaMissense & REVEL scores (red bars) at Leu517.

🧬 VCF File Creation

VCF Header Example:

##fileformat=VCFv4.2
##SnpEffVersion="5.4a (build 2025-11-25 12:22)"
##SnpEffCmd="SnpEff GRCh38.mane.1.0.ensembl /home/hadia/ulti.vcf"
##INFO=<ID=ANN,Number=.,Type=String,Description="Functional annotations">
##INFO=<ID=LOF,Number=.,Type=String,Description="Predicted loss of function">
##INFO=<ID=NMD,Number=.,Type=String,Description="Predicted nonsense-mediated decay">
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO
7	117480086	rs397508136	CGCCCGAGAGACCATGCAGAGGTCGCC	<DEL>	.	PASS	SVTYPE=DEL;END=117480108;CLIN_SIG=Pathogenic
15	72344117	.	A	AA	.	PASS	CLIN_SIG=Pathogenic
Annotation via SnpEff (CLI)
SnpEff GRCh38.mane.1.0.ensembl ulti.vcf > annotated.vcf

Annotations Include:

ANN: Functional annotation

LOF: Predicted loss-of-function transcripts

NMD: Predicted nonsense-mediated decay

ACMG/AMP Classification Summary
Gene	Variant	Consequence	Classification
CFTR	Deletion	Frameshift	Pathogenic
FBN1	Deletion	Frameshift	Pathogenic
HEXA	Duplication	Frameshift	Pathogenic
Conclusion

This project demonstrates:

Database mining (ClinVar, OMIM)

Computational pathogenicity assessment (AlphaMissense, REVEL)

ACMG/AMP evidence-based classification

VCF formatting and annotation (SnpEff)

It reflects modern clinical genomics workflows used in precision medicine and diagnostic labs.
