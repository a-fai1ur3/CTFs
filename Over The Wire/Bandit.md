# OverTheWire - [Bandit](https://overthewire.org/wargames/bandit/) | Format - Q/A

### Level 0
The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

    * SSH bandit0@bandit.labs.overthewire.org -p 2220 | Password - bandit0

### Level 0 -> 1
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

    * ls
      cat readme
### Level 1 -> 2 
The password for the next level is stored in a file called - located in the home directory

    * ls
      cat ./

### Level 2 -> 3 
The password for the next level is stored in a file called spaces in this filename located in the home directory

    * ls
      cat spaces\ in\ this\ filename

### Level 3 -> 4 
The password for the next level is stored in a hidden file in the inhere directory.

    * ls
      cd inhere
      ls - al
      cat .hidden

### Level 4 -> 5
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

    * ls
      cd inhere
      ls
      cd ..
      file ./inhere/*
      cat ./inhere/-file07

### Level 5 -> 6 
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
human-readable | 1033 bytes in size | not executable

     * ls
       cd inhere
       ls
       find . -type f -size 1033c ! -executable
       cat ./maybehere07/.file2

### Level 6 -> 7 
The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7 | owned by group bandit6 | 33 bytes in size

     * ls
       find / -type f -user bandit7 -greoup bandit6 -size 33c
       cat /var/lib/dpkg/info/bandit7.password

### Level 7 -> 8
The password for the next level is stored in the file data.txt next to the word millionth

     * ls
       cat data.txt
       cat data.txt | grep "millionth"

### Level 8 -> 9 
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

     * ls
       sort data.txt
       cat data.txt | sort | uniq -c

### Level 9 -> 10
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

     * ls
       cat data.txt
       string data.txt | grep "="

### Level 10 -> 11
The password for the next level is stored in the file data.txt, which contains base64 encoded data

     * ls
       cat data.txt
       cat data.txt | base64 -d

### Level 11 -> 12
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

     * ls 
       cat data.txt
       and use ROT13.com to solve this level

### Level 12 -> 13
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

     * ls
       cat data.txt
       mkdir /tmp/nothing
       cp data.txt /tmp/nothing
       cd /tmp/nothing
       ls
       xxd -r data.txt > c1
       ls -> file c1
       mv c1 c1.gz
       gzip -d c1.gz
       ls -> file *
       mv c1 c1.bz2
       bzip2 -d c1.bz2
       ls -> file *
       mv c1 c1.gz
       gzip -d c1.gz
       ls -> file *
       mv c1 c1.tar
       tar -xf c1.tar
       ls -> fle *
       tar -xf data5.bin
       ls -> file *
       bzip2 -d data6.bin
       ls -> file *
       tar -xf data6.bin.out
       ls -> file *
       mv data8.bin data8.gz
       gzip -d data8.gz
       ls -> file *
       cat data8

### Level 13 -> 14
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on
