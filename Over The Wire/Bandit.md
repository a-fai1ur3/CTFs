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

