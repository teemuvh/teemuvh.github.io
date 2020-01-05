---
layout: default
---

## Introduction

This is a short recap of the University of Helsinki course
<a href="https://courses.helsinki.fi/fi/KIK-LG219/129824412" target="_blank">Command Line Tools for linguists</a>,
an introductory course to UNIX and terminal tools given in fall 2019.

| Contents of the course |
| ------------- |:-------------|
| Week 1 | Introduction to Command Line Environments |
| Week 2 | Navigating UNIX System |
| Week 3 | Basic Corpus Processing |
| Week 4 | Advanced Corpus Processing |
| Week 5 | Scripting and Configuration Files |
| Week 6 | Installing and Running Programs |
| Week 7 | Version Control |
| Week 8 | Building Webpages using GitHub Pages |

### Introduction to Command Line Environments

Learning the basics of command line.  
You can navigate in your system with command line using
such commands as _ls_, _pwd_, _mv_, _cp_, and _cd_. You can create directories with _mkdir_, get files from the WWW with
_wget_, and check the files with _cat_ or _less_. You can also remove or delete files or directories
with _rm_ or _rm -r_.  
If you need instructions to the commands, use
```
man <command>
```
for example:
```
man tr
```

You can for example create a directory, save a file from the internet into that directory and read the file with commands:

```
mkdir new_directory
cd new_directory
wget url_of_some_web_page
less some_file.txt
```

For modifying the files, you can use the command line text editor _Emacs_, or some other command line text editor such as
vim, or nano.

### Navigating a UNIX System

![unix system](http://swcarpentry.github.io/shell-novice/fig/home-directories.svg "http://swcarpentry.github.io/shell-novice/02-filedir/index.html")

You can copy and move directories with _cp -r_ and _rm -r_ commands, and remove a directory
with _rmdir_ command.  

For example, you can remove a directory with:

```
rm -r some_directory
```
or
```
rmdir some_directory
```

You can compress files with _gzip_ and _tar_.  

```
tar -czvf wanted_name_of_a_zipped_directory.tgz name_of_directory_to_zip/
```

If you need to access remote servers, for example more computing power, you can
use _ssh_ and _scp_ to connect the remote servers and move files between the remote
and local hosts.

### Basic Corpus Processing

Learn about text processing tools in UNIX as well as character encodings.  
You can investigate characted encodings of a file with _file_, transform windows
end of lines to unix end of lines with _dos2unix_ and convert between different encoding systems
with _iconv_.  

Use _tr_ to replace certain characters and _sort_ and _uniq_ to form alphabetical lists
of words in a text file. Some useful commands for text files include _head_ and _tail_ for printing
lines from the beginning and the end of a file.  

Learn to use regular expressions with _egrep_ command. Useful to know: couple of different file formats, namely, _csv_ and _tsv_.  

You can replace all uppercase letters to lowercase letters and create a new file with:

```
tr 'A-Z' 'a-z' < input_file > output_file
```
or more generally:
```
tr '[:upper:]' '[:lower:]' < input_file > output_file
```

### Advanced Corpus Processing

Learn more text processing with UNIX tools. Learn to combine commands with pipeline, and transform
text files with _sed_.  

You can create a word frequency file from a text file with command line tools:  
Open a file with _cat_, set all words in their own lines with _tr_, remove punctuation with _tr_,
set words in alphabetical order with _sort_, count identical words with _uniq_, and sort the file
in reversed numerical order:
```
cat input_file | tr -s "[:space:]" "\n" | tr -d "[:punct:]" | sort | uniq -c | sort -nr > output_file
```
Now, the words in your file will be counted and sorted in a descending order. Output file can for example
look like this:  

* 4595 the
* 2556 of
* 1840 and
* 1631 to
* 1155 that
* 1035 in
* 918 a
* 720 is
* 532 will
* 521 be

### Scripting and Configuration Files

Introduction to basic scripting in UNIX terminal. Remember, you can set up a configuration
file _/.bashrc_ or _/.bash_profile_ for yourself. Also, formatting a nice shell prompt may or may not
improve your productivity.  

You can check your currently existing environment variables with _printenv_.   

More importantly, you can create the previously mentioned word frequency file in a shell scrip format.
Create a new shell script file with _touch_:
```
touch name_of_script.sh
```
Open the file in your preferred command line text editor and include the following:
```
#! /bin/bash

cat $1 |
dos2unix |
tr -s "[:space:]" "\n" |
tr -d "[:punct:]" |
sort |
uniq -c |
sort -nr > $2
```

Then run the script with:
```
./name_of_script.sh input_file output_file
```

### Installing and Running Programs

Learn to install and run programs from command line.  

Becoming a root user gives you more power. Using _brew_ makes installing software easy.
_Pip_ is your friend in installing Python packages.  

Installing Python packages is easy with _pip_. First, check installation guide for the package
from the package website and run:
```
pip3 install wanted_package_name
```
Your package will be ready to use in a short while.  

_Makefiles_ are used in almost all development projects. _Make_ is useful for example
when you need to run scripts on multiple files simultaniously.

### Version Control

Introduction to _git_.  
Set up a GitHub account, create a repository, and
learn to use _git_ for development projects as a version control system. Learn
to _add_ and _commmit_ to GitHub. Also, learn to use branches in version control.
Last, learn to _merge_ branches.  

Create a new .git directory in your working directory, add, commit and push
changes:

```
git
git add name_of_file
git commit -m "message you want to add"
git push <remote> <branch>
```

Create and change to new branch:

```
git checkout -b name_of_new_branch
```

Merge branches into master branch when ready working in one branch:

```
git checkout master
git merge name_of_branch_to_merge
```

More important _git_ commands to learn include _clone_ for cloning github repositories to your local machine,
and _reverting_ to undo changes you have made.

Workflow:
![git workflow](https://www.tutorialspoint.com/git/images/life_cycle.png "https://www.tutorialspoint.com/git/images/life_cycle.png")

### Final Assignment: Building Webpages using GitHub Pages

You can use _jekyll_ and _GitHub Pages_ to build a personal webpage.  

_Jekyll_ is a tool to view websites offline on your local machine. It is a useful tool
for checking that minor changes in your files are working on your website as you wanted
before committing and pushing to your GitHub.  

To view your website locally with _jekyll_, you need to install _jekyll_ and _bundle_ packages first.
Then run
```
bundle exec jekyll serve
```
Copy the ip address that will be printed to your browser, press enter and you'll see your website on your local machine.
If everything looks right, you are ready to push to git.  


Images from:  
http://swcarpentry.github.io/shell-novice  
https://www.tutorialspoint.com/git
