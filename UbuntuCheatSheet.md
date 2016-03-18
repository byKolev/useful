**Ubuntu Cheat Sheet**
==============================================
_Some text._

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
    
