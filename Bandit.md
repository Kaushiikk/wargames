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

Similar to previous level we cd to the `inhere` folder. Inside the folder we find multiple folders. To find the exact file with ASCII value, non-executable and 1033 bytes in size we use `find . -type f -size 1033c ! -executable -exec file '{}' \; | grep ASCII`. Then we cat the file found to get next level password.

**Level 7**

In this level we have to find a file with the given properties. To find the file we use `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null`. Then we cat the found file for password.

**Level 8**

To find the "millionth" word in the file data.txt we can use `cat data.txt | grep -i "millionth"`. This will provide the password from the file.

**Level 9**

To find the unique line in the data.txt file, we use the command `cat data.txt | uniq -u`. This will display the next level password.

**Level 10**

To find the human readable line with multiple "=", we can use `strings data.txt | grep ==` to display the password.

**Level 11**

When we `cat` the data.txt file, we can see a base64 encrypted text. We can decode it by `cat data.txt | base64 -d`.

**Level 12**

When we `cat` the data.txt file we get a cypher text. To deocde the text we can use cyberchef to rotate the letters back to original text.

**Level 13**

We are given a hexdump in data.txt file. To work with the file we copy the file to a temporary directory in `/tmp` directory. Then when we use `file data.txt` we can see the type of file it is. We get it as to be gz(gzip), bz2(bzip2), tar(tar). So, we change the extension to match the exact type of file it is and unzip the file. When we repeat this for a certain amount of time we get a ASCII text file which will have the password. Use `mv <original name> <new name>` to change the extension respectively.
Use `gzip -d <file name>` to unzip gz files, use `tar -xf <file name>` to unzip tar files, use `bzip2 -d <file name>` to unzip bz2 extension.

**Level 14**

Since we are provided with the ssh private key we can directly connect to the next level without passowrd using the command `ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`.

**Level 15**

Now we can get the password for bandit14 using `cat /etc/bandit_pass/bandit14`. Then we can connect to the port 30000 and send the current user password using `nc localhost 30000`. When we send the current user's passowrd we can get the next user's password.

**Level 16**

Now to send the current level password to port 30001 using ssl/tsl encryption, we can use the command `openssl s_client -connect localhost:30001` and send the current level password.

**Level 17**

To find the open and listening ports within the range, we can use nmap and the command `nmap -sV localhost -p31000-32000`. This will show all the active ports. Then we can find the specific ports that require ssl/tsl. We send the connection to these server `openssl s_client -connect localhost:31790 -quiet` and try to get the next level user's key. Once we get the private key we can store it to a file and use the command `ssh -i <file name> bandit17@bandit.labs.overthewire.org -p 2220` to access next level.

**Level 18**

We can use `diff` to find the difference between password.new and passowrd.old files. We can use `diff password.new password.old` to get the next user's password in the first line.

**Level 19**

As mentioned in the level description, the .bashrc is modified to exit when we connect. This means that ssh is executed when we try to login, thus we can use the command `ssh bandit.labs.overthewire.org -p 2220 -l bandit18 cat readme` to get the password for the next level.

**Level 20**

When we `ls` we can see a file with setuid preference which allows the file to be executed as the owner of the file. Thus when we try to access the password file of bandit20 we get back the password. The command used is `./bandit20-do cat /etc/bandit_pass/bandit20`.

**Level 21**

Since we have to send the current level password to the server we can create a one time server in any port using `echo -n '<current password>' | nc -l -p <port number> &`. Then we execute the file using the same port number which will read the next level's password.

**Level 22**

When we visit the `/etc/cron.d`, we can find a file named bandit22. When we `cat` the file, we can find the cron job, When we `cat` the cron job we can find that it stores the password for next level in `/tmp` file. Thus we got the password for the next level.

**Level 23**

Similar to the last level, we find the cron job which stores the password of bandit23 in the tmp directory and the name of the file is `echo I am user bandit23 | md5sum | cut -d ' ' -f 1`. This returnes a value which is the file name in /tmp folder which stores the password.