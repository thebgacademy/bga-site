
# Hello :wave:

and welcome to the TreeVal Curation workshop :clap:

We have put alot of work into TreeVal so hopefully you'll find it incredibly helpful for your own project. Keep in mind that this course does run with the hope you attend the workshop by GRIT on manual-curation, who will show you how this data is used and how to manually curate your genome.

## The Tutorial

1, We will be using GitPod for this tutorial so [**SEND ME TO GITPOD!**](https://gitpod.io/#https://github.com/BGAcademy23/treeval-curation).

2, The Nextflow command:

```
nextflow run treeval/main.nf \
-profile singularity \
--input treeval/assets/local_testing/nxOscDF5033-BGA.yaml \
--outdir OscDF5033-TEST \
-entry RAPID
```

3, Uploading to JBrowse

```bash
cd jbrowse2

jbrowse add-assembly /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/ilTolViri5_1.fa -a ilTor --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/ilTolViri5_1_ancestral.bigBed -a ilTor -n ancestral_busco --category Busco --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/ilTolViri5_1_buscogene.bigBed -a ilTor -n standard_busco --category Busco --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/ilTolViri5_1_selfcomp.bigBed -a ilTor -n selfcomp --category selfcomp --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/telo_ilTolViri5_1.bed.gz -a ilTor -n telomere --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/gap_ilTolViri5_1.bed.gz -a ilTor -n gap --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/BSPQI.bigBed -a ilTor -n BSPQI --category Enzymes_Digest --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/BSSSI.bigBed -a ilTor -n BSSSI --category Enzymes_Digest --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/DLE1.bigBed -a ilTor -n DLE1 --category Enzymes_Digest --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/hic_files/ilTolViri5_1.hic -a ilTor -n HIC --category Mapping --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/DanausPlexippus.Dpv3_pep.gff.gz -a ilTor -n DanPlexPeptide --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/DanausPlexippus.Dpv3_cdna.bigBed -a ilTor -n DanPlexCDNA --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/DanausPlexippus.Dpv3_cds.bigBed -a ilTor -n DanPlexCDS --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/DanausPlexippus.Dpv3_rna.bigBed -a ilTor -n DanPlexRNA --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/MelitaeaCinxia.ilMelCinx1_pep.gff.gz -a ilTor -n MelCinPEP --category Alignments --load copy

jbrowse add-track /workspace/treeval-curation/ilTorViri5-BGA/treeval_upload/HeliconiusMelpomene.ASM31383v2_cdna.bigBed -a ilTor -n HelMelPEP --category Alignments --load copy

cd ../
```
  - You'll notice that the HiC and punchlist files, aren't listed here. This is because they were rather difficult to get working on the GitPod.

4, Uploading to Higlass

You will have to close any current higlass tabs you have open, navigate to the gitpod window, ports and open a new higlass window.

```
cd /workspace/treeval-curation/ilTorViri5-BGA/hic_files/

cp {ilTolViri5_1.mcool,../treeval_upload/ilTolViri5_1.genome,ilTolViri5_1_coverage.bigWig,ilTolViri5_1_repeat_density.bigWig,ilTolViri5_1_gap.bed,ilTolViri5_1_telomere.bed} /tmp/higlass-docker/

cd ../../

higlass-manage ingest /tmp/higlass-docker/ilTolViri5_1.mcool --assembly ilTorViri5_1 --project-name TreeVal-test

higlass-manage ingest --filetype chromsizes-tsv --datatype chromsizes --assembly ilTorViri5_1 /tmp/higlass-docker/ilTolViri5_1.genome --project-name TreeVal-test

higlass-manage ingest /tmp/higlass-docker/ilTolViri5_1_coverage.bigWig --assembly ilTorViri5_1 --project-name TreeVal-test

higlass-manage ingest /tmp/higlass-docker/ilTolViri5_1_repeat_density.bigWig --assembly ilTorViri5_1 --project-name TreeVal-test

clodius aggregate bedfile --chromsizes-filename /tmp/higlass-docker/ilTolViri5_1.genome /tmp/higlass-docker/ilTolViri5_1_gap.bed 

higlass-manage ingest /tmp/higlass-docker/ilTolViri5_1_gap.bed.beddb --datatype bedlike --filetype beddb --assembly ilTorViri5_1 --project-name TreeVal-test

clodius aggregate bedfile --chromsizes-filename /tmp/higlass-docker/ilTolViri5_1.genome /tmp/higlass-docker/ilTolViri5_1_telomere.bed

higlass-manage ingest /tmp/higlass-docker/ilTolViri5_1_telomere.bed.beddb --datatype bedlike --filetype beddb --assembly ilTorViri5_1 --project-name TreeVal-test
```

5, CurationPretext

This pipeline can be run like such:

```
nextflow run curationpretext/main.nf -profile singularity --input /workspace/treeval-curation/Oscheius_DF5033/genomic_data/Oscheius_DF5033.fa --pacbio /workspace/treeval-curation/Oscheius_DF5033/pacbio/ --cram /workspace/treeval-curation/Oscheius_DF5033/hic-arima2/ --outdir pretext_full -entry ALL_FILES
```

```
nextflow run curationpretext/main.nf -profile singularity --input /workspace/treeval-curation/Oscheius_DF5033/genomic_data/Oscheius_DF5033.fa --cram /workspace/treeval-curation/Oscheius_DF5033/hic-arima2 --outdir pretext_maps -entry MAPS_ONLY
```
