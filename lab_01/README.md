# 🚧 DOKUMENT W PRZYGOTOWANIU 🚧

```Ostateczna wersja w dniu zajęć może różnić się od obecnej.```

# Rekonstrukcja i klasyfikacja genomów bakteryjnych

Dane do zajęć znajdziesz w ```/home/database/metgen26```, każdy ma do pobrania pliki z konkretnego dnia (Day1/2/3/4)

```bash
cp -r {ścieżka} ./
```

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

DODAĆ LISTE NARZĘDZI

## Kolejne kroki...
