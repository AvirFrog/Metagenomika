
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
