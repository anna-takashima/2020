# BioProject内のfastqを一括してダウンロードする方法

2021-01-07


以下の BioProject内のfastqを一括してダウンロードしたい。
https://www.ncbi.nlm.nih.gov/sra?LinkName=bioproject_sra_all&from_uid=494853

各サンプルを見て、SRA／SRRから始まるidを調べる

fastq-dump というツールでダウンロードする。
`conda install -c bioconda sra-tools`

使い方
https://rnakato.hatenablog.jp/entry/2017/07/06/110926

```
sra_list=({7969880..7970008})

for sra_id in ${sra_list[@]}
do
 fastq-dump --split-files SRR$sra_id
done
```
