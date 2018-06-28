# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > * pwd : show current working directory path
   * mkdir [dir] : create a directory
   * rmdir [dir] : remove an empty directory
   * rm -R [dir] : remove a non-empty directory and its files
   * rm [file] : delete a file
   * mv [file] [new filename] : rename a file
   * mv -v [file] [directory] : move a file to a new directory
   * ls -a : list files including hidden files
   * cp [file] [dir] : copy a file to the listed directory
   * cd [dir] : change directory
   * cd ~ : home directory
   * cd .. : move one level up 
   * man [command] : display manual page for command

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls 
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > * ls : list files in directory
    * ls -a : list files including hidden files (start with '.')
    * ls -l : list files in long format
    * ls -lh : list files with sizes w/ suffixes (Bytes, KB, GB, etc.)
    * ls -lah : list files including hidden files in the long format with sizes listed w/ suffixes (Bytes, KB, GB, etc.)
    * ls -t : list files sorted by time modified (newest first)
    * ls -Glp : list files in a long format with color enabled and directories demarcated with a '/' at the end of their names

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > 1. ls -lu : long form display of files by access time
    2. ls -S : sort files by size
    3. ls -ks : list files and file sizes in kilobytes
    4. ls -i : list file serial numbers
    5. ls -d : list only directories

:pufferfish:
---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> >  `xargs` supports building an execution pipeline from standard input

 

