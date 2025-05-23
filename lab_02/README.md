
**Wersja Testowa zajęć nr. 2**

zawartość tego pliku może się zmienić przed wtorkowymi zajęciami ;) 


# Adnotacja metagenomów

{TEKST}

## Binnowanie złożenia

{TEKST}

### Instalacja narzędzia SemiBin

Nowe środowisko:
```bash
mamba create -n SemiBin
```

Aktywacja środowiska:
```bash
mamba activate SemiBin
```

Instalacja SemiBin:
```bash
mamba install -c conda-forge -c bioconda semibin
```

Sprawdzenie czy wszystko jest zainstalowane poprawnie:
```bash
SemiBin2 check_install
```
Oczekiwany output:
```text
Looking for dependencies...
        bedtools        : /home/[wasze_konto]/mambaforge/envs/SemiBin/bin/bedtools
        hmmsearch       : /home/[wasze_konto]/mambaforge/envs/SemiBin/bin/hmmsearch
        prodigal        : /home/[wasze_konto]/mambaforge/envs/SemiBin/bin/prodigal
        mmseqs          : /home/[wasze_konto]/mambaforge/envs/SemiBin/bin/mmseqs
```
Jeśli jakiegoś programu brakuje to należy go ręcznie doinstalować w środowisku, w którym zainstalowany jest `SemiBin`.

### Instalacja pozostałych narzędzi

Instalacja BWA-MEM2:
```bash
mamba install bioconda::bwa-mem2
```

bwa-mem2 index hybrid_assembly.fasta
bwa-mem2 mem -t 10 hybrid_assembly.fasta ../illumina/illumina_R1.fasta ../illumina/illumina_R2.fasta > illumina.sam 

minimap2 -d hybrid_assembly.mmi hybrid_assembly.fasta
minimap2 -ax map-ont -t 10 hybrid_assembly.mmi ../nanopore/nanopore.fastq -o nanopore.sam

samtools sort -@ 8 -o illumina.bam illumina.sam
samtools sort -@ 8 -o nanopore.bam nanopore.sam
samtools merge -@ 38 hybrid.bam illumina.bam nanopore.bam



Instalacja minimap2:
```bash
mamba install bioconda::minimap2
```

