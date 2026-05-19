# Rekonstrukcja i klasyfikacja genomów bakteryjnych

Dane do zajęć znajdziesz w ```/home/database/metgen26```, każdy ma do pobrania pliki z konkretnego dnia (Day1/2/3/4)

##  Instalacja Condy i Mamby

Pobieranie miniforge

```bash
wget https://github.com/conda-forge/miniforge/releases/download/25.9.1-0/Miniforge3-25.9.1-0-Linux-x86_64.sh
```

```bash
chmod +x Miniforge3-25.9.1-0-Linux-x86_64.sh 
```

```bash
./Miniforge3-25.9.1-0-Linux-x86_64.sh 
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

fastp
metaQuast
BWA-MEM
SemiBin2
CheckM2
Kraken2
Bracken
KronaTools

## Zadania na dziś

Surowe odczyty znajdziecie w `/home/database/metgen26/raw_reads`, każda osoba dostanie do przeanalizowania próbki z jednego dnia (3 próbki na jeden dzień). Scaffoldy znajdziecie w `/home/database/metgen26/scaffolds`

1. Sprawdzamy je za pomocą fastp
2. MetaQuastem wybieramy najlepsze złożenie
3. Do najlepszego złożenia mapujemy za pomocą BWA-MEM przefiltrowane odczyty
4. Robimy wspólnie JEDEN binning za pomocą SemiBin2
5. Sprawamy za pomocą CheckM2 jakość bininngu
6. Sprawdzamy Kraken2/Bracken/Krona

