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
    
# Some useful keyboard shortcuts to work with
- `CTRL L` Clear the terminal 
- `CTRL P` Previous command (just like up arrow key)
- `CTRL N` Next command (just like up arrow key) usually after you `CTRL P` a few times and miss the command you were looking for
- `CTRL O` Execute command, but don't clear the line
- `CTRL J` Execute command and clear the line (just like when you press `Enter`)
- `CTRL D` Delete character under cursor OR logout if the line is empty
- `SHIFT Page Up/Down` Go up/down the terminal
- `CTRL F` Move forward to next character (just like right arrow key)
- `CTRL B` Move backward to prev character (just like right arrow key)
- `CTRL A` Cursor to start of line
- `CTRL E` Cursor the end of line
- `ALT B` Move a word back
- `ALT F` Move a word forward
- `CTRL U` Delete left of the cursor
- `CTRL K` Delete right of the cursor
- `CTRL W` Delete word on the left
- `CTRL Y` Paste (after CTRL U,K or W)
- `TAB` auto completion of file or command
- `CTRL R` reverse search history - press `CTRL R` again to go to previous result.
- `!!` repeat last command
- `CTRL SHIFT -`  undo

# Aliases (“An alias is worth a thousand commands”).
Aliases are a very easy way to get cozy with the terminal. Aliases are defined in ~/.bashrc and are per user.

Edit the file `~/.bashrc` (create if does not exist) and type the following:

```
alias myalias="mycommand"
```

My personal favorites are:

```
alias www='cd /var/www/'
alias gits='git status'
alias gitc='git commit -m'
alias gitca='git commit -a -m'
alias phup='phing site-update'
alias dca='drush cc all'
alias tlog='sudo tail -F /var/log/httpd/something.workingpropeople.com-error_log'
```

# History (“The moment you forgot what magic you did yesterday”)
Fortunately everything is recorded. The `history` command prints out your recent commands.

Every command has a number in front of it. For example:

```
[user@hostname ~]$ history
  101  ls -la
  102  git add .
  103  drush cc all
```

If you execute `!101` it will execute the command with number 101 (`ls -la` in the above case).

As mentioned earlier `!!` executes the last command. 

Forgot to type `sudo`? No problem: `sudo !!`
 
# Commonly used commands 
 
Print working directory

    pwd

List the files and the folders in the current directory.

    ls
    ls -l
    ls -la
    ls -lh
    ls -i *.jpg

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
    
