=== ENG ===


=== RO ===
1. Structura fișierelor

├── 'lwget'
├── 'lwget_cache'
│   ├── '/downloads'
│   └── '/.metadata'
│     	├── '/promises.txt'
│		└── '/current_level'
├── 'README.md'
├── 'Requirements.md'

2. Cum funcționează?

   Scriptul începe prin crearea directoarelor de lucru în mod recursiv, pornind de la 'Parent Directories'.
Inițial, verificăm dacă utilizatorul a introdus argumentul '-h' / '--help', caz în care apelăm funcția 'usage' care va printa la stdout instrucțiunile de utilizare a scriptului. Deși utilizarea comenzii 'echo' era mai intuitivă, am folosit 'cat << EOF [...] EOF' datorită libertății extinse de formatare a textului. Astfel, direcționăm către comanda 'cat' textul de la intrarea standard până la delimitatorul EOF.
De asemenea, dacă utilizatorul nu a introdus niciun argument, programul printează o eroare și se oprește din execuție cu exit code 1.

   În cazul utilizării normale a scriptului, începem prin a verifica nivelul curent de adâncime și a extrage urmatorul nivel de fișiere HTML. Pentru descărcarea fișierelor am utilizat comanda 'wget' în mod nerecursiv, cu argumentele quiet (fără output la stdout) și de scriere în fișier. Pentru extragerea link-urilor am folosit comanda 'grep' cu pipeline prin 'awk', astfel încât să preluăm doar URL-urile.
Nivelul de adâncime este inițializat cu 0 prin funcția 'init_level' și incrementat în funcția 'main'. 


