# Lab Report 3 - Four Interesting Ways to use the `GREP` Command

### 1. Output File Names containing Pattern
Instead of the output as the lines which matches the pattern...`$ grep -1 "vista" *`
```bash
$ grep -l "vista" written_2/travel_guides/berlitz1/*.txt > grep-results.txt
```
![image](https://user-images.githubusercontent.com/111631103/221728956-8e7933c4-8ffd-4235-91bf-89dffc0dd742.png)

### 2. The Search for the Pattern as a _whole word_ 
Instead of as a Substring...`$ grep -w "vista" *`

Without `-w`, notice that grep output vista as a substring such as _vistas_
![image](https://user-images.githubusercontent.com/111631103/221729781-9608e041-ea5d-4fd4-935a-d321f1b4c574.png)

Here's grep with `-w`:
![image](https://user-images.githubusercontent.com/111631103/221729597-00f78546-6ee3-4492-8b2f-82f4ac7cfac8.png)

### 3. Search with Multiple Patterns
- `$ grep -e "vista" -e "vitsa" -e "VISTA" find-results.txt`
```count-txts.sh
grep "vista" $1 > grep-result1.txt
grep "flower" $1 > grep-result2.txt
grep "farm" $1 > grep-result3.txt
wc grep-result1.txt grep-result2.txt grep-result3.txt

grep -e "vista" -e "flower" -e "farm" $1 > grep-results.txt
wc grep-results.txt
```

`$ bash count-txts.sh written_2/travel_guides/berlitz1/*.txt`

As we can see from the output (below), the individual counts from grep-result1.txt, grep-result2.txt, and grep-result2.txt doesn't quite count sum up to the expected total count (grep-results.txt).
![image](https://user-images.githubusercontent.com/111631103/221747234-96bdbbda-9619-4c4a-b4ff-447c58f601fc.png)

If a single line in the input file matches multiple search patterns, grep will output that line multiple times, once for each match. This means that the words in that line will be counted multiple times by wc. So, we have to use the -o option with grep to output each match on a separate line, so that each line is counted only once by wc.

```bash
grep -o "vista" $1 > grep-result1.txt
grep -o "flower" $1 > grep-result2.txt
grep -o "farm" $1 > grep-result3.txt
wc grep-result1.txt grep-result2.txt grep-result3.txt

grep -o -e "vista" -e "flower" -e "farm" $1 > grep-results.txt
wc grep-results.txt
```

`$ bash count-txts.sh written_2/travel_guides/berlitz1/*.txt`

We see that the output is now as expected (below):
![image](https://user-images.githubusercontent.com/111631103/221747040-4e9534f7-df3a-4bcb-a9ce-5ff1e61a190a.png)

### 4. Search with Multiple Patterns from a File
given `pattern.txt`, `$ grep -f pattern.txt find-results.txt`

```
vista
flower
farm
```

`$ grep -o -f pattern.txt written_2/travel_guides/berlitz1/*.txt | w`
![image](https://user-images.githubusercontent.com/111631103/221749091-afd8d741-fd05-49c3-b52a-88be7f493909.png)

