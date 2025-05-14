# Bandit

**Level 0**

`ssh bandit.labs.overthewire.org -p 2220 -l bandit0`
Password: bandit0

**Level 1**

Password for next level is stored in readme file.
use `cat readme` to get the password and login to bandit1 using `ssh bandit.labs.overthewire.org -p 2220 -l bandit1`.

**Level 2**

When we `ls` we can see a file named '-', to read the file use `cat ./-`.

**Level 3**

When we use `ls` we can see a file names 'spaces in this filename', to read the file use `cat spaces\ in\ this\ filename`.

**Level 4**

When we use `ls` we can see a directory `inhere`. Use `cd inhere` and use `ls -la` to display all the contents in the directory.
We can find a file `...Hiding-From-You`. To access this we can use `cat ...Hiding-From-You`.

**Level 5**

In this level we can see a folder `inhere`. In the folder we find multiple files, we can use `cat` to each and every file but it is ineffective. So to find the human readable file, we use `file./*` to find the exact file with ASCII values. Then `cat` the file with ASCII value to get password.

**Level 6**

Similar to previous level we cd to the `inhere` folder. Inside the folder we find multiple folders. To find the exact file with ASCII value, non-executable and 1033 bytes in size we use `find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII`.