# BioProject内のfastqを一括してダウンロードする方法

2021-01-07


https://www.ncbi.nlm.nih.gov/sra?LinkName=bioproject_sra_all&from_uid=494853

```
sra_list=({7969880..7970008})

for sra_id in ${sra_list[@]}
do
 fastq-dump --split-files SRR$sra_id
done
```
