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
```bash
grep "vista" $1 > grep-result1.txt
grep "flower" $1 > grep-result2.txt
grep "farm" $1 > grep-result3.txt
wc grep-result1.txt
wc grep-result2.txt
wc grep-result3.txt

grep -e "vista" -e "flower" -e "farm" $1 > grep-results.txt
wc grep-results.txt
```
As we can see from the output (below), the individual count sum up to the total count
![image](https://user-images.githubusercontent.com/111631103/221734097-0e581bb0-bd64-43ab-b15e-994dc5e0779d.png)

### 4. Search with Multiple Patterns from a File
given `pattern.txt`, `$ grep -f pattern.txt find-results.txt`
