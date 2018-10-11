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



R: USe PCadapt - see link. first gives PCA for pop structure. 
first work out how many PCs explain data. 
in graph: when line flat then more PCs don't add anything - in example its three. 

