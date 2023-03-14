# Lab Report 5 - Organizing my Downloads folder

### Goal: I want to categorize most of the files within my Downloads folder into their own respective directories based on their file type.

### 1. Go to relevant directory: `$ cd ~/Downloads`
### 2. What are the most reoccuring file types in my Downloads?
command: `$ find ~/Downloads -type f | awk -F "." '{print $NF}' | sort | uniq -c | sort -nr`
- `find` with `type -f` pulls up all files within the specified directory `~\Downloads`
- `awk -F` splits file names via the specified delimiter `.`
- `$NF` is a built-in variable which references the last field after `awk` splits the file name apart, specifically the file name and its file extension, e.g. "filename.txt" would become two fields which is "filename" and "txt" such that `$NF` refers to the latter
- And so `print` would display to terminal the extracted file extensions
- this first `sort` arranges the output in alphabetical order, so that the following `uniq` can remove the adjacent duplicates. 
- the addition of `-c` to `uniq` also counts the numbers of occurrences
- `sort -nr` sorts based on the number of occurences in descending order

![image](https://user-images.githubusercontent.com/111631103/224905984-f0184ab6-692b-46e4-af3f-e1ef1006f68b.png)

We can now see that the files which clutters the Downloads folder the most are those of types `pdf`,`exe`, `png`, `docx`, `txt`, and `jpg`.

### 3. Categorize files into their respective directories

Here are the directories that I will create: `PDF_DOC_TXT/`, `EXE/`, and `PIC/`
command: 
  1. `mkdir -p PDF_DOC_TXT`
  2. `mv *.pdf PDF_DOC_TXT/`
  3. `mv *.docx PDF_DOC_TXT/`
  4. `mv *.txt PDF_DOC_TXT/`
*Note that the following screenshots don't actually follow exactly this as I was indecisive about what I wanted to do. However, the way I used `mv` provides insight into how one would correct for the natural mistake.

![image](https://user-images.githubusercontent.com/111631103/224907786-1a70a599-985c-409e-84a1-524d12efe94c.png)
![image](https://user-images.githubusercontent.com/111631103/224907801-ab1b0028-1fb5-477f-a792-b651a745929c.png)

We would do similarly for the other directories.

### Future Plans
Downloaded files automatically categorize themself into the existing directories within the Downloads folder. I imagine this would require a script utilizing if-statements.

### Outside Sources
https://www.baeldung.com/linux/awk-command-nf-variable
