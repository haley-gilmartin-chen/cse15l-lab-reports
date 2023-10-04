```
[user@sahara ~]$ cd
```
I got no output because I didn't change to any directory. The working directory was the home directory.
```
[user@sahara ~]$ cd lecture1/messages
```
The command navigated through the hierarchy, and the directory changed to the messages folder. 
```
[user@sahara ~/lecture1/messages]$ cd ar-dz.txt
bash: cd: ar-dz.txt: Not a directory
```
Since ar-dz.txt isn't a folder (or directory), the command cannot navigate into a directory and thus returns an error.
```
[user@sahara ~/lecture1/messages]$ cd ~
[user@sahara ~]$ ls
lecture1
```
I navigated back to home and then ran ls to list the items within the home directory.
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
I used ls to list the items within the lecture1 folder, with the working directory being the home directory.
```
[user@sahara ~]$ ls lecture1/Hello.java
lecture1/Hello.java
```
Working in the home directory, I used the ls command to display the items within the lecture1/Hello.java directory. Since Hello.java isn't a directory, the command printed the file's path.
```
[user@sahara ~]$ cat

^C
```
The cat command requires arguments to be passed. When I ran this command in home, nothing happened and I couldn't type in any more commands. I had to use ^C to escape the command.
```
[user@sahara ~]$ cat lecture1
cat: lecture1: Is a directory
```
The cat command cannot be used on directories, so the terminal threw an error even was working in the home directory and lecture1 is in this directory.
```
[user@sahara ~]$ cat lecture1/messages/ar-dz.txt
مرحبا بالعالم!
```
I used cat to successfully print the message in ar-dz.txt. I had to navigate through the hierarchy to the correct path to reach the file.
