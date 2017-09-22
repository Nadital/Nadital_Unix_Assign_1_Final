# Codes used for file creation:

$ grep-E "(ZMMIL|ZMMLR|ZMMMR)" fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/maize_genotypes_no_head

$ grep -E "(ZMPBA|ZMPIL|ZMPJA)" fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/teosinte_genotypes_no_head

$ head -m 1 fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/fang_genotypes_header

$ cat fang_genotypes_header maize_genotypes_no_head > maize_genotypes_w_header

$ cat fang_genotypes_header teosinte_genotypes_no_head > teosinte_genotypes_w_header

$ mv transpose.awk Nadital_Unix_Assign_1/

$ awk -f transpose.awk teosinte_genotypes_w_header > transposed_teosinte_genotypes

$ awk -f transpose.awk maize_genotypes_w_header > transposed_maize_genotypes

$ sort -k1n snp_position.txt > Nadital_Unix_Assign_1/sorted_snp_position

$ cut -f 1-4 sorted_snp_position | column -t | head

$ sort -k1n  transposed_maize_genotypes > sorted_maize_genotypes

$ cut -f 1-4 sorted_maize_genotypes| column -t | head

$ sort -k1n transposed_teosinte_genotypes > sorted_teosinte_genotypes

$ join -t $'\t' -1 1 -2 1 sorted_snp_position sorted_maize_genotypes > joined_maize_data

$ join -t $'\t' -1 1 -2 1 sorted_snp_position sorted_teosinte_genotypes > joined_teosinte_data

$ cut -f 1,3,4,16-1588 joined_maize_data > cut_maize_data

$ cut -f 1,3,4,16-990 joined_teosinte_data > cut_teosinte_data

$ cut -f 1-4 cut_maize_data | column -t | head

$ for i in {1..10}; do awk '$2 == '$i'' cut_maize_data > chr"$i"_maize_data; done

$ cut -f 1-4 chr10_maize_data | column -t | head

$ for i in {1..10}; do sort -k3n chr"$i"_maize_data > chr"$i"_maize_inc_nt_final; done

$ cut -f 1-4 chr10_maize_inc_nt_final | column -t | head

$ for i in {1..10}; do sort -k3nr chr"$i"_maize_data > chr"$i"_maize_dec_nt; done

$ for i in {1..10}; do sed 's/?/-/g' chr"$i"_maize_dec_nt > chr"$i"_maize_dec_nt_final; done

$ cut -f 1-4 chr10_maize_dec_nt_final | column -t | head

$ for i in {1..10}; do awk '$2 == '$i'' cut_teosinte_data > chr"$i"_teosinte_data; done

$ for i in {1..10}; do sort -k3n chr"$i"_teosinte_data > chr"$i"_teosinte_inc_nt_final; done

$ for i in {1..10}; do sort -k3nr chr"$i"_teosinte_data > chr"$i"_teosinte_dec_nt; done

$ for i in {1..10}; do sed 's/?/-/g' chr"$i"_teosinte_dec_nt > chr"$i"_teosinte_dec_nt_final; done

$ mv *final Nadital_Unix_Assign_1_Final

$ awk '$2 ~ /unknown/' cut_maize_data > Nadital_Unix_Assign_1_Final/maize_snp_unknown_pos_final

$ cut -f 1-4 maize_snp_unknown_pos_final | column -t | head

$ awk  '$2 ~ /multiple/' cut_maize_data > Nadital_Unix_Assign_1_Final/maize_snp_multiple_pos_final

$ cut -f 1-4 maize_snp_multiple_pos_final | column -t | head

$ awk '$2 ~ /unknown/' cut_teosinte_data > Nadital_Unix_Assign_1_Final/teosinte_snp_unknown_pos_final

$ awk '$2 ~ /multiple/' cut_teosinte_data > Nadital_Unix_Assign_1_Final/teosinte_snp_multiple_pos_final

$ git add .

$ git status

$ git commit -m "(remarks and updates as made)"

$ git push origin master
