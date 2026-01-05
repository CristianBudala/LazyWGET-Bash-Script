```
 _                  __        ______ _____ _____ 
| |    __ _ _____   \ \      / / ___| ____|_   _|
| |   / _` |_  / | | \ \ /\ / / |  _|  _|   | |            University of Bucharest
| |__| (_| |/ /| |_| |\ V  V /| |_| | |___  | |            Department of Computer Science
|_____\__,_/___|\__, | \_/\_/  \____|_____| |_|            Year 1, Sem 1: Intro to Computer Science
                |___/                                      
```



## 🔮 Overview
LazyWGET is a Bash script that performs a Breadth-First Search (BFS) traversal of a tree whose root is the first URL entered by the user, while the nodes represent references (HREFs) from the previous level. The script downloads the references (promises) one depth level at a time, stopping execution after each level.

The script is designed to be:

- **Sequential:** It does not automatically execute the entire tree recursively. It waits for the user's input before moving to depth \(N + 1\).
- **Programmatic:** It preserves the state of the processing queue as a database of URLs (promises).
- **Efficient:** It prevents circular loops by checking the browsing history before adding new URLs to the queue.

## ⬇️ Installation and Usage
1. Clone the repository
2. Dependencies:
Make sure the following standard Linux utilities are installed on your system:

- **bash** (Shell environment)
- **wget** (Network download tool)
- **grep, awk, cut** (Text-processing pipelines)

3. In action:

    | ./lwget URL |
    |---|
    | <img src="attributes/lwget-usage.gif" width="500"> |

4. Reset & Help:
   
    To clear the cache, remove downloaded files, and reset the depth counter back to 0:
    
    ```bash
    ./lwget -r
    ./lwget --reset
    ```

    To receive information on how to correctly use the script:
    
    ```bash
    ./lwget -h
    ./lwget --help
    ```

## 📁 Project structure
```
├── lwget
├── lwget_cache/
    ├── .metadata/                # Stores the internal state and metadata
         ├── current_level.txt    # Stores current level for parsing
         ├── promises.txt         # Database of promises, sorted by their depth level
    ├── downloads/                # Stores downloaded content
         ├── downloaded.html      # Most recently downloaded HTML file
         ├── assets/              # All downloaded resources
```

| Flowchart |
|---|
| <img src="attributes/LazyWGET_Flowchart.png" width="700"> |

## ❗ Limitations
- **URL Detection:**  
  The script uses `grep` to find links referenced in HTML files. These links are placed directly into the promises database queue. It strictly supports `http` and `https`.

- **Asset Detection:**  
  The script uses Regex (`grep`) to identify file extensions. Known extensions (Table 1) are treated as terminal nodes — they are downloaded but not scanned further for potential promises.

- **Duplicate Handling:**  
  The script uses `grep -Fq` to scan the promises database before updating it for the next level, ensuring uniqueness of promises.

    | Category | Extensions |
    | --- | --- |
    | Images | jpg, jpeg, png, gif, webp, bmp, ico, tiff, svg |
    | Documents | pdf, doc, docx, xls, xlsx, ppt, pptx, txt, csv |
    | Code & Data | css, js, json, xml, map |
    | Media | mp3, mp4, wav, webm, m4a |
    | Archives | zip |

## 🛠️ Troubleshooting

| Problem | Possible Cause | Solution |
| --- | --- | --- |
| `You must enter an URL!` | The script was executed without arguments at Level 0. | Provide the root URL: `./lwget <URL>` |
| `You must enter a single URL!` | More than one root URL was provided at Level 0. | Run `./lwget` with a single root URL. |

## 🎓 Academic Context
This project was developed as part of the course "Instrumente si Tehnici de Baza in Informatica" (Introduction to Computer Science) from the Faculty of Mathematics and Computer Science at the University of Bucharest.

## 👥 Students Involved
- Cristian Budala (@CristianBudala)
- Ruslan Gaitur (@Dontmindmeifido)

## 📝 License
This project is MIT licensed.
