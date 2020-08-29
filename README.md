# bibtex-duplicates-or-unused

When you have a .bib file and you want to remove unused entries, check out:

1. [checkcites](https://www.ctan.org/pkg/checkcites) for printing unused entries
2. [bibexport](https://ctan.org/tex-archive/biblio/bibtex/utils/bibexport/?lang=en) for automatically removing unused entries

## checkcites

Suppose your LaTeX file is `main.tex` and is stored into the current working directory (CWD).

For `checkcites`, first download it into your CWD, next to your `main.tex` file:

```
wget http://mirrors.ctan.org/support/checkcites.zip
unzip checkcites.zip

Then, build your LaTeX code, which will generate a `main.aux` file:

```
latexmk -pdf main.tex
```

Then, you can run `checkcites`:

```
chmod +x ./checkcites/checkcites.lua
./checkcites/checkcites.lua main.aux
```

This will output a list of unused references. 
But how can you automatically remove them?
See next.

## bibexport

First, download and build `bibexport`:

```
wget http://mirrors.ctan.org/biblio/bibtex/utils/bibexport.zip
unzip bibexport.zip
(cd bibexport/ && latex bibexport.ins)
```

Then, compile your project as before:

```
latexmk -pdf main.tex
```

Then, run `bibexport` on your `main.aux` and export the used references to `used.bib`:

```
chmod +x ./bibexport/bibexport.sh
./bibexport/bibexport.sh -o used.bib main.aux
```
