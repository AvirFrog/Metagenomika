# Analiza taksonomiczna hipotetycznych genomów

Do tego wykorzystamy bazę GTDB ale najpierw sprawdzmy czy mamy poprawną ścieżkę: 

```bash
echo $GTDBTK_DATA_PATH
```
Wynik powinien być taki:
```bash
$ /home/database/miniforge3/envs/gtdbtk-2.7.2/share/gtdbtk-2.7.2/db
```

Jeśli ścieżka jest inna skorzystaj z:
```bash
export GTDBTK_DATA_PATH=/home/database/miniforge3/envs/gtdbtk-2.7.2/share/gtdbtk-2.7.2/db
```

Następnie uruchamiamy klasyfikacje: 
```bash
gtdbtk classify_wf --genome_dir [PATH] --out_dir [OUTPUT_PATH] --cpus 38 --extension fa
```

## Analiza funkcjonalna wybranego MAGa

Po instalacji bakty należy ją uruchomić, pobieranie bazy danych nie jest koniecznie ponieważ znajduje sie w `/home/database/bakta_db`

```bash
bakta --db /home/database/bakta_db --verbose --output results_bakta/ --prefix assembly --threads 8 [WYBRANY_MAG]
```

## Identyfikacja profagów

Będziemy potrzebować pliku w formacie `GenBank`, znajdziesz go w folderze z plikami wyjściowymi z programu `bakta` z rozszerzeniem `.gbff`

```bash
PhiSpy.py TWÓJ_PLIK_GENBANK -o NAZWA_KATALOGU_WYJSCIOWEGO --threads 8 --output_choice 7
```

## Skrypt do napisania

Następnie napisz skrypt, który sprawdzi czy zidentyfikoane profagi pokrywają się z bakteriofagami wykrytymi przez geNomad
