# Składanie Metagenomu Bakterii

Ścieżka do plików 

```bash
cp -r /home/jbarylski/metagenomika/ ./
```

##  Instalacja Condy i Mamby

Pobieranie miniforge

```bash
wget https://github.com/conda-forge/miniforge/releases/download/24.9.2-0/Mambaforge-24.9.2-0-Linux-x86_64.sh
```

```bash
chmod +x Mambaforge-24.9.2-0-Linux-x86_64.sh
```

```bash
./Mambaforge-24.9.2-0-Linux-x86_64.sh
```

Teraz należy się przelogować

```bash
conda config --add channels bioconda
```
## Tworzenie wirtualnych środowisk

--> `Dobrą praktyką (i bezpieczną) jest tworzenie osobnego środowiska do każdego narzędzia, ale jest to wymagane tylko dla niektórych programów.` <--

Tworzenie witrualnego środowiska
```bash
mamba create -n env_name
```

Aktywowanie utworzonego wirtualnego środowiska
```bash
mamba activate NAZWA_SRODOWISKA
```
Sprawdzenie jakie środowiska są już utworzone
```bash
mamba env list
```

## Narzędzia do instalacji

- Nanopore
- porechop
- filtlong
- nanoplot
- (meta)FLye
- metaquast

## Jak składać genom

### Illumina
- Sprawdzanie jakości przed filtracją (fastp)
- Filtracja (fastp)
- Sprawdzenie jakości po filtracji (fastp)
- Składanie (metaSpades/megahit)
- Sprawdzenie jakosci złożenia (metaQuast)

### Nanopore
- Sprawdzanie jakości przed filtracją (nanoplot)
- Filtracja (porechop & filtlong)
- Sprawdzenie jakości po filtracji (nanoplot)
- Składanie (metaFlye)
- Sprawdzenie jakosci złożenia (metaQuast)
