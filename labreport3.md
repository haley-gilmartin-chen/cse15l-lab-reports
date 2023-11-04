# Lab Report 3
## Part 1 - Bugs in `ArrayExamples.java`
---

For Part 1 of this report, we will be examining the following method:
```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

### Failure-inducing Input JUnit Test
```
@Test
public void testReversedFailure(){
    int[] inputArr = {1, 2, 3};
    int[] reversed = ArrayExamples.reversed(inputArr);
    int[] expected = {3, 2, 1};

    assertArrayEquals(expected, inputArr);
}
```

### Non-Failure-inducing Input JUnit Test
```
@Test
public void testReversedSuccess(){
    int[] inputArr = {0, 0, 0};
    int[] reversed = ArrayExamples.reversed(inputArr);
    int[] expected = {0, 0, 0};

    assertArrayEquals(expected, inputArr);
}
```

### Symptom
![image](https://github.com/haley-gilmartin-chen/cse15l-lab-reports/assets/147003402/871b8875-63d9-4745-8e5b-3b18db338826)

## Fixing the Bug
Before:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
With adjustment:
```
public static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i++) {
        newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
}
```

In the original code, the method created a new array called `newArray` with the same length as `arr`. However, while attempting to copy `arr` in the reversed order to `newArray`, the method copies the values of `newArray` (which are all 0's --the default values) to `arr`, thus making all values of `arr` `0`. The method then returns `arr` (the original array) instead of `newArray`, which is supposed to be the copy. The adjusted version rectifies this simple mistake by switching the places of `arr` and `newArray` as needed to yield the desired result.

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

Example 1:
(Within a file called `check_hello.sh`)
```
if grep -q "hello" myfile.txt; then
  echo "'hello' is in the file."
else
  echo "'hello' is not in the file."
fi
```
After running `bash check_hello.sh`, `'hello' is in the file.` is outputted. `grep -q` is useful for checking if something is in a file without producing a huge output. The bash script is used to implement this.

Example 2:
(Within a file called `check_word.sh`)
```
if grep -q "word" myscript.java; then
  echo "'word' is in the script."
else
  echo "'word' is not in the script."
fi
```
After running `bash check_word.sh`, `'word' is not in the script.` is outputted. `grep -q` is useful for checking if something is in a file without producing a lengthy output. In addition to `.txt` files, `grep` can also be used on `.java` files.

The information used in Part 2 was found from the following webiste: https://git-scm.com/docs/git-grep 

