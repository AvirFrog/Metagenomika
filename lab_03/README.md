# 🚧 DOKUMENT W PRZYGOTOWANIU 🚧

```Ostateczna wersja w dniu zajęć może różnić się od obecnej.```

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
gtdbtk classify_wf --genome_dir [PATH] --out_dir [OUTPUT_PATH --cpus 25 --extension fa --skip_ani_screen
```

## Analiza funkcjonalna wybranego MAGa
Wybierz genom i przeprowadz jego adnotację funkcjomnalną
[eggNOG-mapper](http://eggnog-mapper.embl.de)

## Pyania na koniec
Prześlij na koniec zajęć odpowiedzi na pytania:<br>
* Która metoda binningu daje najlepsze rezultaty. Dlaczego tak myślisz?<br>
* Ile gatunków i rodzajów występuje w badanym metagenomie?<br>
* Znajdź geny związane z komunikacją komórkową (GO:0007154), prześlij w formie pliku tsv<br>


końcowa analiza taksonomiczna
```bash
gtdbtk classify --extension gz --genome_dir ../download/output_bins --align_dir align_out --out_dir classify_out --skip_ani_screen --cpus 19
```
