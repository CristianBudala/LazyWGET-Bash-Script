=== ENG ===
1. File structure

```
├── 'lwget'
├── 'lwget_cache'
│   ├── '/downloads'
│   └── '/assets'
│   ├── '/.metadata'
│     	├── '/promises.txt'
│		└── '/current_level'
├── 'README.md'
├── 'Requirements.md'
```

2. How it works?

The script begins by recursively creating the working directories, starting from the 'Parent Directories'.

Initially, we check if the user has provided the '-h' / '--help' argument, in which case we call the 'usage' function to print the script's usage instructions to stdout. Although using the 'echo' command might have been more intuitive, we used 'cat << EOF [...] EOF' due to the greater flexibility it offers for text formatting. Thus, we redirect the text from standard input to the 'cat' command up to the EOF delimiter. Additionally, if the user has not provided any arguments, the program prints an error and terminates execution with exit code 1.

During normal script operation, we begin by checking the current depth level and extracting the next level of HTML files. To download the files, we used the 'wget' command in non-recursive mode, using the 'quiet' argument (no output to stdout) and the file output argument. To extract links, we used the 'grep' command piped through 'awk' to retrieve only the URLs.

The depth level is initialized to 0 via the 'init' function and incremented within the 'main' function.

=== RO ===
1. Structura fișierelor

```
├── 'lwget'
├── 'lwget_cache'
│   ├── '/downloads'
│   └── '/.assets'
│   ├── '/.metadata'
│     	├── '/promises.txt'
│		└── '/current_level'
├── 'README.md'
├── 'Requirements.md'
```

2. Cum funcționează?

Scriptul începe prin crearea directoarelor de lucru în mod recursiv, pornind de la 'Parent Directories'.
Inițial, verificăm dacă utilizatorul a introdus argumentul '-h' / '--help', caz în care apelăm funcția 'usage' care va printa la stdout instrucțiunile de utilizare a scriptului. Deși utilizarea comenzii 'echo' era mai intuitivă, am folosit 'cat << EOF [...] EOF' datorită libertății extinse de formatare a textului. Astfel, direcționăm către comanda 'cat' textul de la intrarea standard până la delimitatorul EOF.
De asemenea, dacă utilizatorul nu a introdus niciun argument, programul printează o eroare și se oprește din execuție cu exit code 1.

   În cazul utilizării normale a scriptului, începem prin a verifica nivelul curent de adâncime și a extrage urmatorul nivel de fișiere HTML. Pentru descărcarea fișierelor am utilizat comanda 'wget' în mod nerecursiv, cu argumentele quiet (fără output la stdout) și de scriere în fișier. Pentru extragerea link-urilor am folosit comanda 'grep' cu pipeline prin 'awk', astfel încât să preluăm doar URL-urile.

Nivelul de adâncime este inițializat la 0 prin funcția 'init' și incrementat în funcția 'main'. 


