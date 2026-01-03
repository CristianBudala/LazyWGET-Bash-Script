```
 _                  __        ______ _____ _____ 
| |    __ _ _____   \ \      / / ___| ____|_   _|
| |   / _` |_  / | | \ \ /\ / / |  _|  _|   | |  
| |__| (_| |/ /| |_| |\ V  V /| |_| | |___  | |  
|_____\__,_/___|\__, | \_/\_/  \____|_____| |_|  
                |___/                            
```

# LazyWGET
LazyWGET is a Bash script that performs a Breadth-First Search (BFS) traversal of a tree whose root is the first URL entered by the user, while the nodes represent references (HREFs) from the previous level. The script downloads the references (promises) one depth level at a time, stopping execution after each level.

The script is designed to be:

- **Sequential:** It does not automatically execute the entire tree recursively. It waits for the user's input before moving to depth \(N + 1\).
- **Programmatic:** It preserves the state of the processing queue as a database of URLs (promises).
- **Efficient:** It prevents circular loops by checking the browsing history before adding new URLs to the queue.

## ⬇️ Installation
1. Clone the repository
2. 





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

2. How it works

On the first run, the script downloads only the root HTML file specified by the user. It then parses the file to extract all HTTP/HTTPS links and saves them as "promises" (URLs that will be downloaded later). These promises are stored in a metadata file along with their depth level (level 1). The current recursion level is incremented and saved.
On the second run, the script reads the promises marked for level 1, downloads each of those files, and extracts links from them. These new links become level 2 promises. The process continues with each subsequent execution, advancing one level deeper into the link hierarchy.

=== RO ===
1. Structura fișierelor

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

2. Cum funcționează?

La prima execuție, scriptul descarcă doar fișierul rădăcină HTML specificat de utilizator, apoi îl analizează pentru a extrage toate linkurile HTTP/HTTPS și le salvează ca "promisiuni" (URL-uri care vor fi descărcate ulterior). Aceste promisiuni sunt stocate într-un fișier de metadate împreună cu nivelul lor de adâncime (nivelul 1). Nivelul curent de recursiune este incrementat și salvat. La a doua rulare, scriptul citește promisiunile marcate pentru nivelul 1, descarcă fișierele respective și extrage linkuri noi din ele. Aceste linkuri devin promisiuni de nivel 2. Procesul continuă cu fiecare execuție ulterioară, avansând în adâncime în ierarhia linkurilor.
