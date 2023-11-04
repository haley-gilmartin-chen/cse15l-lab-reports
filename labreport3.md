# Lab Report 3
## Part 2 - Researching `grep`
---
`-c` (or --count): Outputs the count of matching lines in each file, rather than showing the lines themselves.
Example 1:
```
$ grep -c "hi" myfile.txt
3
```
In `myfile.txt`, I'm using `grep -c` to find the number of lines where instances of the keyword `hi` appear. The output is 3, indicating there are `3` lines. This is useful for counting instances of strings within files without having all the lines printed.

Example 2:
```
$ grep -c "hi" file1.txt file2.txt
file1.txt:5
file2.txt:2
```
Here, I'm using `grep -c` on multiple files. The command prints the file name and number of lines where instances of `hi` occur for each respective file. This is useful for counting instances of strings within files without having all the lines printed.

---

`-n` (or --line-number): Outputs line numbers along with lines.
Example 1:
```
$ grep -n "error" error_messages.txt
42:This is an error message.
58:Another error occurred.
```
In `error_messages.txt`, the `grep -n` command searches for instances of the string `error`. This option allows `grep` to output first the line number, then the entire line in which the keyword is found. In `error_messages.txt`, `grep -n` found `error` in lines `42` and `58`. This is useful for finding the locations of instances of keywords within files

Example 2:
```
$ grep -n "WARNING" warnings_log.txt
3:WARNING: No ice cream!
9:WARNING: Low on caffeine.
```
In `warnings_log.txt`, the `grep -n` command searches for instances of the string `WARNING`. In `warnings_log.txt`, `grep -n` found `WARNING` in lines `3` and `9`. This is useful for finding the locations of instances of keywords within files. 

---

`-H` (or --with-filename): Outputs the file name before each line.
Example 1:
```
$ grep -H "keyword" *.txt
file1.txt:This line contains the keyword.
file2.txt:Another line with the keyword.
```
`grep -H` has found all the instances of `keyword` within the `.txt` files within the working directory. This is useful because in addition to printing the lines with instances, the command has also provided the files in where they are found.

Example 2:
```
$ grep -H "hii" /Documents/UCSD/*.txt
/Documents/UCSD/file1.txt: hii.
/Documents/UCSD/file2.txt: hii <3.
```
`grep -H` has found all the instances of the keyword `hii` within the `.txt` files within the directory path provided within the working directory. This is useful because in addition to printing the lines with instances, the command has also provided the files in where they are found.

---

`-q` (or --quiet or --silent): Suppress normal output. It's typically used when you want to check if a pattern exists without displaying the results.
