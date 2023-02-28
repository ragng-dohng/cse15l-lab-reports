# Lab Report 3 - Four Interesting Ways to use the `GREP` Command

### Way 1. Output File Names containing Pattern
We might want the file names which has matches in order to manipulate the files themselves. Instead of the output as the lines which matches the pattern, using the -1 option with grep outputs the file names whose content has the matches, e.g. `$ grep -l "vista" written_2/travel_guides/berlitz1/*.txt`.

![image](https://user-images.githubusercontent.com/111631103/221749504-0b350172-5d88-4e6b-bea2-0e436e05f007.png)

### Way 2. Search for the Pattern as a _whole word_ 
By default, grep's pattern matching includes substrings. This could prove to be useless if we are trying to find matches, for example, "he" but the default will have the results include matches to "the", in instance. In using the -w option with grep, the pattern "he" is interpreted as a single word. Note the example as follow: `$ grep -w "vista" written_2/travel_guides/berlitz1/*.txt`

Without `-w`, notice that grep output includes vista as a substring of _vistas_
![image](https://user-images.githubusercontent.com/111631103/221750282-22fdd0bc-a7b3-4d1d-90e0-a5060663e796.png)

Here's grep with `-w`:
![image](https://user-images.githubusercontent.com/111631103/221750361-433aad24-4f41-445c-bc4a-a85535d602bf.png)

### Way 3. Search with Multiple Patterns
Sometimes, you want to do searches for multiple patterns (or even variations on spelling of a word) and so we have the -e option, the expressions specifier. The comparison without -e and with -e is shown below in the bash script called via `$ bash count-txts.sh written_2/travel_guides/berlitz1/*.txt`.

```
// count-txts.sh
grep "vista" $1 > grep-result1.txt
grep "flower" $1 > grep-result2.txt
grep "farm" $1 > grep-result3.txt
wc grep-result1.txt grep-result2.txt grep-result3.txt

grep -e "vista" -e "flower" -e "farm" $1 > grep-results.txt
wc grep-results.txt
```

As we can see from the output (below), the individual counts from `grep-result1.txt`, `grep-result2.txt`, and `grep-result2.txt` doesn't quite count sum up to the expected total count from `grep-results.txt`.
![image](https://user-images.githubusercontent.com/111631103/221747234-96bdbbda-9619-4c4a-b4ff-447c58f601fc.png)

If a single line in the input file matches multiple search patterns, grep will output that line multiple times, once for each match. This means that the words in that line will be counted multiple times by wc. So, we have to use the -o option with grep to output each match on a separate line, so that each line is counted only once by wc.

The bash script `count-txts.sh` is updated as described.

```
count-txts.sh
grep -o "vista" $1 > grep-result1.txt
grep -o "flower" $1 > grep-result2.txt
grep -o "farm" $1 > grep-result3.txt
wc grep-result1.txt grep-result2.txt grep-result3.txt

grep -o -e "vista" -e "flower" -e "farm" $1 > grep-results.txt
wc grep-results.txt
```

We see that the output is now as expected (below):
![image](https://user-images.githubusercontent.com/111631103/221747040-4e9534f7-df3a-4bcb-a9ce-5ff1e61a190a.png)

### Way 4. Search with Multiple Patterns from a File
Now, the patterns to be matched could be very long and using -e option to specify for every one isn't always ideal, so we can use grep to refer to a text file which has all the pattern to be matched, e.g. given `pattern.txt`, thus `$ grep -o -f pattern.txt written_2/travel_guides/berlitz1/*.txt | w`. Note, the `|` is what is called a pipeline in which we "pipe" the resulting output into the next command (in this case, `wc`).

```
// pattern.txt
vista
flower
farm
```

We see that our output is as expected, i.e. the same as when we used the -e option in Way 3.
![image](https://user-images.githubusercontent.com/111631103/221749091-afd8d741-fd05-49c3-b52a-88be7f493909.png)

### A Few Last Notes...
The alternative to using a pipeline, as we seen in class, is to output to a text file, e.g. `$ grep ".txt" find_results.txt > grep_results.txt`, and then the `wc` command is applied likeso: `$ wc grep_results.txt`. I find the pipeline method to be more quicker and we can even combine commands, e.g. `$ grep ".txt" find_results.txt | uniq | wc`. 

*Note that `uniq` removes duplicate lines from the output of the grep command. This happens when there are multiple matches of the pattern in a single line.

Finally, these various ways of using `grep` was sourced from [Geeks For Geeks](https://www.geeksforgeeks.org/grep-command-in-unixlinux/).
