**Ubuntu Cheat Sheet**
==============================================
# What is `/bin/bash` and who cares about it?
Bash is just a shell program. A shell program is how the user interacts with the core of the OS. Another shell is `/bin/sh` (Bourne shell). 

BASH is short for Bourne Again SHell which is the "next" version of the Bourne shell.

The prompt of default BASH looks like:
```
[user@hostname ~]$
```
And when we are using the root account (not a good idea) it is:
```
[root@hostname ~]#
```


Re-synchronize the package index files from their sources. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list(5). An update should always be performed before an upgrade or dist-upgrade. 

    apt-get update
    
Used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list(5)

    apt-get upgrade
 
Change directory

    cd directory
    


Create new directory

    mkdir dirname

Rename a file

    mv test.jpg test2.jpg
    
Move all files from directory to another directory
    
    mv directory/* directory2    
    
Create empty file

    touch test.txt
    
Extract files from tar.gz to a destination folder (the folder must exits)

    tar -zxvf something.tar.gz -C destinationFolder
    
Search the whole filesystem for a DIRNAME

    find . -type d | grep DIRNAME

Search the whole filesystem for a FILENAME

    find . -type f | grep FILENAME
    
