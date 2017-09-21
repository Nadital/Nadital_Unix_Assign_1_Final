# Codes used for generation of files:

$ grep-E "(ZMMIL|ZMMLR|ZMMMR)" fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/maize_genotypes_no_head

$ grep -E "(ZMPBA|ZMPIL|ZMPJA)" fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/teosinte_genotypes_no_head

$ head -m 1 fang_et_al_genotypes.txt > Nadital_Unix_Assign_1/fang_genotypes_header

$ cat fang_genotypes_header maize_genotypes_no_head > maize_genotypes_w_header

$ cat fang_genotypes_header teosinte_genotypes_no_head > teosinte_genotypes_w_header

$ mv transpose.awk Nadital_Unix_Assign_1/

$ awk -f transpose.awk teosinte_genotypes_w_header > transposed_teosinte_genotypes

$ awk -f transpose.awk maize_genotypes_w_header > transposed_maize_genotypes

$ sort -k1,1 snp_position.txt > Nadital_Unix_Assign_1/sorted_snp_position

$ sort -k1,1 transposed_maize_genotypes > sorted_maize_genotypes

$ sort -k1,1 transposed_teosinte_genotypes > sorted_teosinte_genotypes

$ join -t $'\t' -1 1 -2 1 sorted_snp_position sorted_maize_genotypes > joined_maize_data

$ join -t $'\t' -1 1 -2 1 sorted_snp_position sorted_teosinte_genotypes > joined_teosinte_data

$ cut -f 1,3,4,16-1588 joined_maize_data > cut_maize_data

$ cut -f 1,3,4,16-990 joined_teosinte_data > cut_teosinte_data

$ for i in {1..10}; do awk '$2 == '$i'' cut_maize_data > chr"$i"_maize_data; done

$ for i in {1..10}; do sort -k3,1n chr"$i"_maize_data > chr"$i"_maize_inc_nt_final; done

$ for i in {1..10}; do sort -k3,1n -r chr"$i"_maize_data > chr"$i"_maize_dec_nt; done

$ for i in {1..10}; do sed 's/?/-/g' chr"$i"_maize_dec_nt > chr"$i"_maize_dec_nt_final; done

$ for i in {1..10}; do awk '$2 == '$i'' cut_teosinte_data > chr"$i"_teosinte_data; done

$ for i in {1..10}; do sort -k3,1n chr"$i"_teosinte_data > chr"$i"_teosinte_inc_nt_final; done

$ for i in {1..10}; do sort -k3,1n -r chr"$i"_teosinte_data > chr"$i"_teosinte_dec_nt; done

$ for i in {1..10}; do sed 's/?/-/g' chr"$i"_teosinte_dec_nt > chr"$i"_teosinte_dec_nt_final; done

$ awk '$2 ~ /unknown/' cut_maize_data > Nadital_Unix_Assign_1_Final/maize_snp_unknown_pos_final

$ awk  '$2 ~ /multiple/' cut_maize_data > Nadital_Unix_Assign_1_Final/maize_snp_multiple_pos_final

$ awk '$2 ~ /unknown/' cut_teosinte_data > Nadital_Unix_Assign_1_Final/teosinte_snp_unknown_pos_final

$ awk '$2 ~ /multiple/' cut_teosinte_data > Nadital_Unix_Assign_1_Final/teosinte_snp_multiple_pos_final
