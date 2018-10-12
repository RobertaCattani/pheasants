# pheasants

cd /Users/bobbiecattani/Birds
#this tells terminal/ console where to look for the directory - it doesn't like folders that are stored on icloud (?) for some reason - so just use it on the actual laptop#

Bobbies-MacBook-Air:Birds bobbiecattani$ ls 
PHE079.R1.fastq			vcftools_0.1.13.tar
PHE079.trimmed_R2_.fastq
#this gives a list of everything that is in the folder so you can see if the file you want is in there#

/Users/bobbiecattani/Birds
#now look at the first line of code with Head. 
Bobbies-MacBook-Air:birds bobbiecattani$ head PHE079.r1.fastq
@1_1101_14596_1577
ATTGCAAAAAATTATGGTATGAAAATCACCTTCTACTCTCTCCCCAGAGTATTGGCTGGTTTCTTCATTTTTTTTAATTCCTCTTCATTTTCATTTTATAATCCCCAAGTTCCCATTAAGCATTTTGTAGAAGATCGAACTACAAAAG
+
BGGFEGGGGEEGCGFHF5DGHFHHHHHHFHHHHHHHHGHHHHHHGHEGHAGFHHHHHGGAGHHHHHHHGHHHGGGHBGHGGHGEFEGFHHHHHHHHHHHFHHFEGGHGAHHHFFDHHFGHHFHHHHB??BDGHGFHHFGFHGB2FDGH
@1_1101_15010_1581
GTGTGTAGAAGTCACAGTCAGAACACATAGGCTCTTCTGTTAATGCACCAGCACTGCATGAAGTTAAAGACACTACTCAGATGTTTCCAGCACATTACATGTACTTCTGTGTCAAGTAGTTAGCAGGTCAAATAGCCTCCAGGGATCT
+
BGFGGGGGGGGHHHHHHHHHHHHHHHHHGGHHHHHHHHHFHHHHHHHHHHHHHGHEHHHHHFFGHFHFHHHGHGGHHHGHHHHGHHHHGGGHHHHHHGHHGGHHHHHHHHHHHHHFGHHHHHHHHHHHHHHHHHHHHHHHHEE/FHEH
@1_1101_17524_1628
CTTCCTACTGCACGACACATCAGCTCCCAGGGCTGCTCCTGCAGGAGTTCCATGGGCTGCAGCCTCCTTCAAGCCACATCCACTGCTGCACCACGTGCTCCTCCACAGCTGCACATGGAGATGTGTTCCAGGTGGTGCCCATGGGCT
Bobbies-MacBook-Air:birds bobbiecattani$ 

#This opens a page at a time. You can scroll through using spacebar, and quit this view with q
less filename

#shows the last few lines of a file
tail filename





Scroll to the bottom of the first block of text and look at the last line. This should be something like (if you make the page wide enough, you should see individual name, space, sequence. The last line has some different characters):

less WPAallMerged.loci

# use spacebar to scroll through. 
#loci files shows all the locus in numbered block"




To use VCF tools: need to use whole pathfile bc otherwise won't work. 
```cp /Users/bobbiecattani/Birds/vcftools.dir/bin/vcftools
```
do filtering steps - can do all on one line. Remember to use Recode - recoded all. and out
```
Bobbies-MacBook-Air:Birds bobbiecattani$ /Users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf WPAallMerged.vcf --maf 0.05 --recode --recode-INFO-all --out test
```
where test is the name for the new file.



R: USe PCadapt - see link. first gives PCA for pop structure. 
first work out how many PCs explain data. 
in graph: when line flat then more PCs don't add anything - in example its three. 





/users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf WPAallMerged.vcf --maf 0.05 --recode --recode-INFO-all --out test
#filter the data now. 




Feature	As summary statistic	As inclusion criteria
Missingness per individual	--missing	--mind N
Missingness per marker	--missing	--geno N
#Allele frequency	--freq	--maf N#
Hardy-Weinberg equilibrium	--hardy	--hwe N
Mendel error rates	--mendel	--me N M


http://vcftools.sourceforge.net/man_latest.html
--max-missing <float>

Exclude sites on the basis of the proportion of missing data (defined to be between 0 and 1, where 0 allows sites that are completely missing and 1 indicates no missing data allowed).

-minQ <float>

Includes only sites with Quality value above this threshold.


Include only sites with a Minor Allele Frequency greater than or equal to the "--maf" value and less than or equal to the "--max-maf" value. One of these options may be used without the other. Allele frequency is defined as the number of times an allele appears over all individuals at that site, divided by the total number of non-missing alleles at that site.





FILTERING
```
/users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf WPAallMerged.vcf --maf 0.05 --max-missing 0.5 --minQ 30 --recode --recode-INFO-all --out fi
CFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf WPAallMerged.vcf
	--recode-INFO-all
	--maf 0.05
	--minQ 30
	--max-missing 0.5
	--out fi
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...
After filtering, kept 0 out of a possible 184264 Sites
No data left for analysis!
Run Time = 2.00 seconds
vcftools.dir bobbiecattani$ /users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf fi.recode.vcf --missing-indv

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf fi.recode.vcf
	--missing-indv

After filtering, kept 69 out of 69 Individuals
Outputting Individual Missingness
After filtering, kept 0 out of a possible 0 Sites
File does not contain any sites
Run Time = 0.00 seconds
```
so filtering worked in code, but first one kept 0 sites? - need to address this. 



-> do it individually.
##MAF##
```
/users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf WPAallMerged.vcf --maf 0.05 --recode --recode-INFO-all --out filter1
```


VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf WPAallMerged.vcf
	--recode-INFO-all
	--maf 0.05
	--out filter1
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...
#After filtering, kept 125671 out of a possible 184264 Sites#
Run Time = 15.00 seconds
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ 



For the next one need to keep change the name 
vcftools adds the .recode.vcf extension


users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --minQ 30 --recode --recode-INFO-all --out filter2

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf filter1.recode.vcf
	--recode-INFO-all
	--minQ 30
	--out filter2
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...
After filtering, kept 0 out of a possible 125671 Sites
No data left for analysis!
Run Time = 2.00 seconds
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ 



## min Q 20 still filters everything out##
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ /users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --minQ 20 --recode --recode-INFO-all --out filter2.a

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf filter1.recode.vcf
	--recode-INFO-all
	--minQ 20
	--out filter2.a
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...
After filtering, kept 0 out of a possible 125671 Sites
No data left for analysis!
Run Time = 1.00 seconds

## minq 10 doesn't seem to do anything - all files are kept

Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ /users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --minQ 10 --recode --recode-INFO-all --out filter2b

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf filter1.recode.vcf
	--recode-INFO-all
	--minQ 10
	--out filter2b
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...
After filtering, kept 125671 out of a possible 125671 Sites
Run Time = 12.00 seconds
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ 
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ 


## min Q 15 still gets rid of everything as well, as does 14)


/users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --minQ 15 --recode --recode-INFO-all --out filter2c
-After filtering, kept 0 out of a possible 125671 Sites


but min Q 13 keeps everything  /users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --minQ 13 --recode --recode-INFO-all --out filter2c

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf filter1.recode.vcf
	--recode-INFO-all
	--minQ 13
	--out filter2c
	--recode

After filtering, kept 69 out of 69 Individuals
Outputting VCF file...


After filtering, kept 125671 out of a possible 125671 Sites



#MAX MISSING 
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ /users/bobbiecattani/Birds/vcftools/bin/vcftools --vcf filter1.recode.vcf --max-missing 0.5--recode --recode-INFO-all --out filter3

VCFtools - v0.1.13
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
	--vcf filter1.recode.vcf
	--recode-INFO-all
	--max-missing 0.5
	--out filter3

After filtering, kept 69 out of 69 Individuals
## After filtering, kept 41503 out of a possible 125671 Sites
Run Time = 3.00 seconds
Bobbies-MacBook-Air:vcftools.dir bobbiecattani$ 


