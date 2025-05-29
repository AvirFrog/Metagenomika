# Analiza złożonego metagenomu

Na dzisiejszych zajęciach przeanalizujemy metagenom zsekwencjonowany metoda shootgun.
Wykorzystacie sekwencje złożone na poprzednich zajęciach do sortowania (binning), analizy taksonomicznej i funkcjonalnej

## Binnowanie złożenia

Złożone kontigi trzeba posortować aby otrzymać hipotetyczne genomy (MAGs) można to zrobić narzędziem SemiBin

### Instalacja narzędzia SemiBin2

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
samtools view -b -F 4 sample1.bam -o sample1.mapped.bam -@ 10
```

```bash
samtools sort -m 1000000000 sample1.mapped.bam -o sample1.mapped.sorted.bam -@ 10
```

## SemiBin2

```bash
SemiBin2 single_easy_bin -i ../assembly/hybrid_assembly.fasta -b hybrid.sorted.bam -o co-assembly_output
```
## Checkm2

```bash
checkm2 predict --threads 13 -x .fa.gz --force --input [KATALOG Z BINAMI] --output-directory [OUTPUT]
```

## Analiza taksonomiczna hipotetycznych genomów

Posirtowanym genomom można przporządkowac najbardziej prawdopodobną scieżkę taksonomiczną kożystając z  

przygotowanie danych
```bash
gtdbtk identify --genome_dir output_bins  --out_dir identyfy_out --extension gz  --cpus 19
```

alignment do bazy GTDB
```bash
gtdbtk align --identify_dir identyfy_out --out_dir align_out
```

końcowa analiza taksonomiczna
```bash
gtdbtk classify --extension gz --genome_dir ../download/output_bins --align_dir align_out --out_dir classify_out --skip_ani_screen --cpus 19
```

## Analiza funkcjonalna wybranego MAGa
Wybierz genom i przeprowadz jego adnotację funkcjomnalną
[eggNOG-mapper](http://eggnog-mapper.embl.de)

## Pyania na koniec
Prześlij na koniec zajęć odpowiedzi na pytania:<br>
* Która metoda binningu daje najlepsze rezultaty. Dlaczego tak myślisz?<br>
* Ile gatunków i rodzajów występuje w badanym metagenomie?<br>
* Znajdź geny związane z komunikacją komórkową (GO:0007154), prześlij w formie pliku tsv<br>


