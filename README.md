Project Requirements:

Write a shell program (script) named lwget that uses the wget command NON-RECURSIVELY to download 
HTML documents from the internet to the local computer.


lwget downloads a SINGLE HTML file from the internet at a time using the wget command. 
It then parses the content of that file and recursively downloads the HTML resources referenced 
within the document, emulating the behavior of the wget -r command.

The difference compared to wget -r is that the recursive downloading of resources referred to 
in the HTML document is done lazily, in the sense that all HTML tags that define resources to be downloaded 
are defined as promises. These promises are only evaluated when the lwget command forces them through a new call.


Specifically, each command lwget <URL> forces the evaluation of the current level of recursion in the 
document tree:

* The first call downloads the HTML file furnished as a parameter in the command line 
(the root of the document tree).

* The second call parses this file and locally downloads the documents referred to by the HTML file.

* The third call parses all the HTML documents downloaded in the previous stage and downloads 
the HTML documents referred to by those documents, and so on.

After each stage, you can use common commands like ls or tree to check the behavior of the lwget command.
