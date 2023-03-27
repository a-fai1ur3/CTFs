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

      * ls
        ssh bandit14@localhost -i sshkey.private -p 2220

### Level 14 -> 15
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

      * cat /etc/bandit_pass/bandit14
        nc local host 30000
        and submit the above password

### Level 15 -> 16
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

      * openssl s_client -connect localhost:30001
        and submit the current level password

### Level 16 -> 17
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

      * nmap -A localhost -p 31000-32000
        openssl s_client -connect localhost:31790
        and submit the current level password
        after submitting you will get the ssh key for next level
        then paste the key into a file, in a directory into /tmp | chmod 600 of the ssh key

### Level 17 -> 18
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new | NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

      * ssh bandit17@localhost -i (ssh.key) -p 2220
        cat /etc/bandit_pass/bandit17
        diff passwords.old passwords.new
        and now with the new password ssh into next level

### Level 18 -> 19
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

      * ssh bandit18@localhost -p 2220 ls
        ssh bandit18@localhost -p 2220 cat readme

### Level 19 -> 20
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

      * ls
        ./bandit20-do id
        whoami
        ./bandit20-do whoami
        ./bandit20-do cat /etc/bandit_pass/bandit20

### Level 20 -> 21
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21). | NOTE: Try connecting to your own network daemon to see if it works as you think

      * ls
        ./suconect
        cat /etc/bandit_pass/bandit20
        Now make a new tab and again ssh into level 20 in the seperate tab M1 | M2
        M1 - nc -lvnp 1234
        M2 - ./suconnect 1234
        M1 - Paste the current level password and it will return the next level password

### Level 21 -> 22
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

      * ls -al /etc/cron.d/
        cat /etc/cron.d/cronjob_bandit22
        cat /usr/bin/cronjob_bandit22.sh
        cat /tmp/(name of the file which is in temp)

### Level 22 -> 23
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. | NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

      * cat /etc/cron.d/cronjob_bandit23
        cat /usr/bin/cronjob_bandit23.sh
        use the command from the script  echo I am user $myname | md5sum | cut -d ' ' -f 1
        echo I am user bandit23 | md5sum | cut -d ' ' -f 1
        cat /tmp/paste here what we get after execuring the last command

### Level 23 -> 24
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. | NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level! | NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

      * cat /etc/cron.d/cronjob_bandit24
        cat /usr/bin/cronjob_bandit24.sh
        mkdir /tmp/(hacker) -> and cd tmp
        vim test.sh -> #!/bin/bash
                       cat /etc/bandit_pass/bandit24 > /tmp/(hacker)/(file)
        touch (file)
        chmod 777 test.sh
        chmod 777 (file)
        cp test.sh /var/spool/bandit24
        ls -al
        cat (file)

### Level 24 -> 25
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time

      * mkdir /tmp/hacker
        cd /tmp/hacker
        vim brf.sh -> #! /bin/bash
                      pass=(paste the password of the current directory)
                      for pin in {0000..9999}; do
                      echo "$pass $pin"
                      done
        chmod 777 brf.sh
        ./brf.sh
        ./brf.sh | nc localhost 30002

### Level 25 -> 26
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

      * ls
        cat bandit26.sshkey
        cat /etc/passwd | grep bandit25
        cat /etc/passwd | grep bandit26
        cat /usr/bin/showtext
        ssh bandit26@localhosty -i bandit26.sshkey
        set shell=/bin/bash
        shell
        cat etc/bandit_pass/bandit26

### Level 26 -> 27
Good job getting a shell! Now hurry and grab the password for bandit27!

      * ls
        ./bandit27-do id
        ./bandit27-do cat /etc/bandit_pass/bandit7

### Level 27 -> 28
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user bandit27-git is the same as for the user bandit27. | Clone the repository and find the password for the next level.

      * mkdir /tmp/hacker
        cd /tmp/hacker
        git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
        and paste the same password of the current level
        ls
        cd repo
        ls
        cat readme

### Level 28 -> 29
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28. | Clone the repository and find the password for the next level.

      * mkdir /tmp/hacker
        cd /tmp/hacker
        git clone ssh://bandit28-git@localhost/home/bandit28-git/repo
        and paste the same password of the current level
        ls
        cd repo 
        ls
        cat readme.md
        git show

### Level 29 -> 30
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo. The password for the user bandit29-git is the same as for the user bandit29. | Clone the repository and find the password for the next level.

      * mkdir /tmp/hacker
        cd /tmp/hacker
        git clone ssh://bandit29-git@localhost/home/bandit29-git/repo
        and paste the same password of the current level
        ls
        cd repo
        ls
        cat readme.md
        git show
        git branch -a
        git checkout remotes/origin/dev
        ls
        cat readme.md

### Level 30 -> 31


