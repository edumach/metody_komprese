
# Analýza metod komprese souboru

**Východisko:** Komprimačních (a dekomprimačních) příkazů (programů) máme pro Linux víc. Mezi ty nejběžnější a nejpoužívanější patří programy: `tar`, `gzip`, `bzip2` nebo `zip`. Všechny jsou pochopitelně **bezeztrátové**. 

Každý, kdo pracuje se soubory pod Linuxem, by měl umět s těmito programy zacházet.

## Úkol
Vytvořte **textovou zprávu** (název `10XPrijmeniJ-komprese.docx`). Všechny požadované výstupy ukládejte do ní. **Odevzdejte ji v požadovaném termínu** podle následujících pokynů. Zpráva bude mít očekávané náležitosti jako titulní list (jednoduchý) a bude rozdělená na kapitoly dle zadání níže.

Ve vašem home adresáři na serveru TuX si vytvořte adresář `komprese` a příkazem `wget` do něj stáhněte testovací soubor z URL `https://www.edumach.cz/files/teploty.txt`:

```
$ mkdir komprese 
$ cd komprese
$ wget https://www.edumach.cz/files/teploty.txt
```

Pokud by vám z nějakého důvodu soubor nešel stáhnout, zkopírujte si ho z mého home adresáře:

```
$ cp -p /home/machac/teploty.txt ~/komprese
```

### Pro každou metodu zaznamenejte:

1. **Délku trvání komprese** (reálný čas z výstupu příkazu time):
    ```
    $ time <příkaz_k_provedení>
    ```
2. **Velikost** výsledného komprimovaného souboru (v bajtech).

### Vytvořte tabulku porovnávající:

- Metodu komprese,
- Velikost výsledného souboru (v bytech),
- Délku trvání komprese (v sekundách).  

### Vytvořte grafy:

- Sloupcový graf porovnávající velikost komprimovaných souborů.
- Sloupcový graf porovnávající časy trvání komprese.  

### Stručně okomentujte zjištěné výsledky:

- Která metoda je nejrychlejší,
- Která metoda vytvoří nejmenší soubor,
- Která metoda je nejvhodnější, pokud hledáte kompromis mezi rychlostí a efektivitou.


## Zkoumané metody komprese

Soubor `teploty.txt` postupně zkomprimujte pomocí těchto metod:

### (1) `tar` (bez komprese – pouze archiv)

```
$ tar -cvf teploty.tar teploty.txt
```
Vytvoří nekomprimovaný archiv `teploty.tar`. `c` (create), `v` (verbose – výpis průběhu), `f` (file – určení názvu souboru).



### (2) `tar` s kompresí `gzip`

```
$ tar -czvf teploty.tar.gz teploty.txt
```

Vytvoří archiv komprimovaný pomocí nástroje gzip (obvyklé přípona `.tar.gz` nebo méně často `.tgz`). `-z` pro gzip kompresi (GNU zip).


### (3) `tar` s kompresí `bzip2`

```
$ tar -cjvf teploty.tar.bz2 teploty.txt
```

- Vytvoří archiv komprimovaný pomocí silnějšího algoritmu bzip2 (`.tar.bz2`).
- `-j` pro bzip2 kompresi.


### (4) `gzip` (samostatná komprese)

```
$ gzip -k teploty.txt
```

- Komprimuje soubor na `teploty.txt.gz`.
- ⚠️ Ve výchozím stavu **nahradí** původní soubor `teploty.txt` komprimovanou verzí. K zachování i původního souboru použijte přepínač `-k` (keep):


### (5) `bzip2` (samostatná komprese)

```
$ bzip2 -k teploty.txt
```

- Komprimuje soubor na `teploty.txt.bz2` pomocí algoritmu bzip2.
- ⚠️ Stejně jako `gzip` standardně **maže** původní soubor. Pro jeho zachování použijte přepínač `-k`:


### (6) `zip` (samostatná komprese)

```
$ zip teploty.zip teploty.txt
```

- Zabalí soubor do archivu `teploty.zip`. Na rozdíl od `gzip` a `bzip2` **automaticky zachovává** původní soubor.

---

## Odevzdání




## Hodnocení
- **Výborně**: Práce bezchybně splňuje všechny body zadání včetně dílčích úkolů.
- **Chvalitebně**: Práce splňuje všechny body zadání, ale obsahuje drobné nepodstatné nedostatky a/nebo malé nepřesnosti, případně některé nepodstatné části chybí.
- **Dobře**: Práce správně splňuje většinu bodů zadání, ale obsahuje větší nepřesnosti a/nebo chybí její větší části.
- **Dostatečně**: Práce splňuje pouze některé dílčí body zadání a/nebo její podstatné části chybí.
- **Nedostatečně**: Práce nesplňuje zadání nebo je vypracována s velmi závažnými nedostatky nebo nebyla odevzdána vůbec.
