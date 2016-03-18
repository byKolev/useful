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

# Quick go through some basic commands - pwd, ls, cp, mv, mkdir, cd.
- `pwd` - print working directory
- `ls` - list files - most used are `ls -l`, `ls -la`, `ls -lh`. `ls -l *.jpg` lists only .jpg files, `ll` is actually an alias of `ls -l` (we'll get back to that later)
- `cd` - change working directory - `cd` with no args and `cd ~` takes you home, `cd ..`
- `cp` - copy files - `cp file1 file2`, use `cp -r folder1 folder2` to copy folders, `cp file1 folder1` copies file1 to folder1
- `mv` - move files - the same behavior as copy but moves files 
- `mkdir` - makes a directory - `mkdir -p folder1/folder2` creates folder1 also if it does not exist and then creates folder2 in folder1.
- `rm` - remove file - `rm file1`, `rm -r folder1`, `rm -rf folder1` (don't use `-rf` too much, it can bite)

# Getting help
If you don't know what a program does or what are its options, you can see the manual with `man <COMMAND>`

```
[user@hostname ~]$ man ls
```
Will give you the documentation of the `ls` command. `man` works with every command and program that has a manual page.
You can scroll with the arrow keys or hjkl.

# `<TAB>` is your best friend`
Pressing the `TAB` key autocompletes or suggests possible completions. Works with paths and commands.

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
alias www='cd /var/www/something.workingpropeople.com/www'
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
# Process management (bg, fg, disown, ps, top).
When you run a command/program it is executed as a foreground process.
`CTRL Z` suspends the current foreground process. From there you can resume it in the foreground with `fg` or in the background with `bg`.
`jobs` lists the current background processes.
By adding an `&` at the end of the command you can execute it in background (same as `CTRL Z` + `bg`).
`ps` lists all processes currently running on the system. `ps aux` for a complete list.
However the output from `top` is nicer.
# How to dump the database and zip the source simultaneously.
We archive the files with
```
[user@hostname ~]$ tar -zcf mysite.tar.gz /var/www/mysite &
```
`tar` is now running as a background process (because of the `&` at the end). We can then enter the next command without waiting.
```
[user@hostname ~]$ mysqldump -uroot -p mydb | gzip -9 > mydb.sql.gz
```
We enter our password and we can `CTRL Z` that and then `bg` it
# Useful tools - cat, grep, head, tail, cut, <, >, pushd, popd, tree, watch, touch
In the last command we used `|` and `>`. These are special operators which can be used to chain programs and redirect input/output.
`|` is called a pipe. It passes the output from one program to another. A simple example is:
```
[user@hostname ~]$ history | less
```
This will pass the output of `history` to the `less` program.
The `<` and `>` operators redirect input and output to a file respectively.
```
[user@hostname ~]$ history > myhistory.txt
```
This will save the output of the `history` command in the file `myhistory.txtt
# tmux - Multitasking for ninja’s without ALT + TAB
Tmux is a terminal multiplexer. It acts as a 'parent' to all your terminals. The best thing is that if you lose your SSH session you don't lose your session.

 - start a tmux session
```
[user@hostname ~]$ tmux
```
 - list sessions
```
[user@hostname ~]$ tmux ls
```
 - attach to last session
```
[user@hostname ~]$ tmux a
```
All shortcuts in tmux have a prefix. The default is CTRL B.
 - `<prefix> ?` - shows you all shortcuts (exit by pressing `q`)
 - `<prefix> "` - split pane horizontally
 - `<prefix> %` - split pane vertically
 - `<prefix> <Arrow keys>` - move between panes
 - `<prefix> c` - open a new window
 - `<prefix> n` - next window
 - `<prefix> p` - previous window
 - `<prefix> !` - make a new window and move the pane you are currently at to it
 - `<prefix> x` - kill pane
 - `<prefix> d` - detach from session (you have to reattach with `tmux a` later)
# ViM - How to edit a file with no headache.
ViM is not like other editors. It has 3 modes:
 - `NORMAL` - in this mode you move around the text and perform "motions"
 - `INSERT` - in this mode you insert text
 - `VISUAL` - in this mode you select text
## Files
We can give a filename to vim upon starting it.
```
[user@hostname ~]$ vim myfile.txt
```
or we can just start it and then name the file as we save it
```
:w myfile.txt
```
We write and exit with `:wq` or for short `SHIFT Z SHIFT Z` (pressing z twice while holding Shift)
To exit vim you type `:q` or `:q!` if you don't want to save changes.
## So how do I move?
The keys `h` = left, `j` = down, `k` = up, `l` = right act as arrow keys. Arrow keys on your keyboard also work.
Others are:
 - `w` - next word
 - `b` - prev word
 - `t <char>` - move to next occurence of char
 - `CTRL u` - page up
 - `CTRL d` - page down
 - `CTRL o` - jump to the last position
## Insert mode
You go to insert mode by pressing `i` (insert text before cursor) or `a` (insert text after cursor).
'SHIFT i' enter insert mode at the start of the row, `SHIFT a` - at the end of the line
`o` enters insert mode at a new line below
`SHIFT o` - new line above
In insert mode you can only enter text and once you're done press `Esc` or `CTRL [` to get back to normal mode.
## Text manipulation (motions)
 - `d` - combine with a navigation key from above to: `dw` delete next word, `dt(` delete everything to the next '(', `dd` - delete the whole line
 - `x` - delete the char under the cursor
 - `c` - deletes and enters insert mode: `cw` change next word, `cc` change line
 - `u` - undo
 - `CTRL r` - redo
## Copy paste
 - `y` - starts a yank motion
 - `p` - paste
## Other
Pressing `.` will execute the last motion.
