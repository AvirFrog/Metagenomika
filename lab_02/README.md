
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

Instalacja minimap2:
```bash
mamba install bioconda::minimap2
```

## Mapowanie BWA-MEM2 & Minimap2

### BWA-MEM2
Indeksowanie:
```bash
bwa-mem2 index hybrid_assembly.fasta
```
Mapowanie:
```bash
bwa-mem2 mem -t 10 hybrid_assembly.fasta ../illumina/illumina_R1.fasta ../illumina/illumina_R2.fasta > illumina.sam
```
### Minimap2

Indeksowanie:
```bash
minimap2 -d hybrid_assembly.mmi hybrid_assembly.fasta
```
Mapowanie:
```bash
minimap2 -ax map-ont -t 10 hybrid_assembly.mmi ../nanopore/nanopore.fastq -o nanopore.sam
```

## Tworzenie plików BAM

Sposób ich przygotowania pochodzi z samouczka do narzedzia SemiBin

Tworzymy pliki BAM
```bash
samtools view -h -b sample1.sam -o sample1.bam -@ 10
```

```bash
samtools view -h -b sample2.sam -o sample2.bam -@ 10
```

samtools view -b -F 4 sample1.bam -o sample1.mapped.bam -@ 10
samtools view -b -F 4 sample2.bam -o sample2.mapped.bam -@ 10

samtools sort -m 1000000000 sample1.mapped.bam -o sample1.mapped.sorted.bam -@ 10
samtools sort -m 1000000000 sample2.mapped.bam -o sample2.mapped.sorted.bam -@ 10

samtools merge merged.bam sample1.mapped.sorted.bam sample2.mapped.sorted.bam -@ 10

samtools sort -o merged.sorted.bam merged.bam

samtools index merged.sorted.bam

SemiBin2 single_easy_bin -i ../assembly/hybrid_assembly.fasta -b hybrid.sorted.bam -o co-assembly_output
