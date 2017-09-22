# Nadital_Unix_Assign_1_Final

## Info on file structure and dimensions on fang et al file:
File size: 11M
- Code: $ du -h fang_et_al_genotypes.txt

File type: ASCII text, with very long lines
- Code: $ file fang_et_al_genotypes.txt

Number of columns: 986
- Code: $ awk -F "\t" '{print NF; exit}' fang_et_al_genotypes.txt

Number of lines: 2783
- Code: $ wc -l fang_et_al_genotypes.txt

<br>


## Info on file structure and dimensions on snp position file:

File size: 84 K
- Code: $ du -h snp_position.txt

File type: ASCII text
- Code: file snp_position.txt

Number of columns: 15
- Code: $ awk -F "\t" '{print NF; exit}' snp_position.txt

Number of lines: 984
- Code: $ wc -l snp_position.txt

<br>

## Codes used:

File size: $ du -h

File type: $ file

Column count: $ awk -F "\t" '{print NF;exit}'

Line count: $ wc -l

## Codes used for generation of files are in README2










