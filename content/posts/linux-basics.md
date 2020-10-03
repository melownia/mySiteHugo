---
title: Basic Linux Commands
date: 2020-01-23T19:06:46-04:00
tags: [linux]
categories: [tech doc]
draft: false
---

### 1. du -- display disk usage statistics


```bash
du -d 1 -h Documents # -d:depth -h:"human-readable"
du -d 0 -h Documents
```

### 2. grep -- file pattern searcher

grep stands for “global regular expression print”. It searches files for lines that match a pattern and returns the results. It is case sensitive.

```bash
grep "Apple" fruit.txt
grep -i "Apple" fruit.txt #-i:case insensitive
grep -R "Apple" ~/Documents/fruit # -R: recursive

```


#### Using Grep \+ Regex

[] Matches any one of a set(a rang with a hyphen) characters

^: The pattern following it must occur at the beginning of each line.

$: The pattern preceding it must occur at the end of each line.

\*: zero or more occurrences of the previous character

.(dot): Matches any <font color=red>one</font> character

(dot).\*: Nothing or any number of character

```bash
ls -l|grep ".*.py$"  # end of the line
grep "^apple" /home/wang/test.c #begin of the line
grep "t[ae]mp" test.txt  #tamp or temp
grep "t[a-c]mp" test.txt # tamp,tbmp,tcmp
grep "tmp[0-9][a-z]" filename  #eg. tmp07
grep "..ock" filename
grep "tmp\.\[abc\]" filename
grep "C\.T\.Cummo" filename #C.T.Cummo
grep "C.*ook" filename # Nothing or any number of characters
```
### 3. find -- walk a file hierarchy


```bash
# find files
find . -name "_config.yml"  
find ./fruit -iname apple.txt #case insensitive e.g. apple.txt, Apple.txt
find dir1 ! -name "*.py"
find . -type f -empty # find empty files
find /home -group Developer # by group
find /home -user Lucy -iname "*.txt"
find / -mtime 50 # To find all the files which are modifed 50 days back
find / -cmin -60 # Find changed files in last 1 hour
find / -size +50M -size -100M # Size between 50MB - 100MB
find . -size +1000000c -print # file size > 1MB
find ./GFG -perm 664 #search for file with entered permission
find /etc -type l  # l:linked 
# find directories
find . -type d -name _posts
find . -type d -empty 

# find and delete
find ./fruit -name grape.txt -exec rm -i {} # find and delete a file with confirmation
find ./ -mtime +3 -print|xargs rm -f –r 
# find and grep
find ./ -type f -name "*.txt" -exec grep 'Geek'  {} \ #search text within multiple files
find . -type f| xargs grep "hostname" #用grep命令在所有的普通文件中搜索hostname这个词
```

### 4. Redirect

```bash
ls -al > listings
Mail -s "Subject" to-address < Filename
cat filename >> listings  # >> To add more content to the existing file

# ERROR Rediction
ls abc 2>errorsfile #redicting error to errorsfile
find . -name 'my*' 2>error.log
ls Documents ABC> dirlist 2>&1 #both standard output and error are re-directed to dirlis
```

### 5. Piping

```bash
ls -l -> temp
sort record.txt | uniq 
cat sample2.txt | head -7 | tail -5
ls -l | find ./ -type f -name "*.txt" -exec grep "program" {} \;
```

### 6. &&, ||, !, &, (), {}

```bash
cp ~/Desktop/1.txt ~/1.txt && rm ~/Desktop/1.txt && echo "success" # and
rm ~/Desktop/1.txt || echo "fail" # or
rm ~/Desktop/1.txt || (cd ~/Desktop/;ls -a;echo "fail") #or

rm -r !(*.html)

ping ­c5 www.tecmint.com &
apt-get update & apt-get upgrade &

echo {1..10} # print 1,2,...,10
echo {10..2..2} #print 10,8,6,..,2

A=1;echo $A;{ A=2; };echo $A #?
A=1;echo $A;( A=2; );echo $A #?
```


### 7. Special variable -, $\_ 

```bash
#\_  在此之前执行的命令或者脚本的最后一个参数
mkdir -p udacity-git-course/new-git-project && cd $_

```

### 8. tar

#### Create tar Archive File:

compress and uncompress files
c: Create a new .tar archive file
v: Verbosely show the .tar file progress
f: File name type of the archive file (?)

```bash
tar -cvf all-fruit-06-26-20.tar  dir1/dir2
```
#### Create tar.gz tar.bz2 Archive File:

To create a compressed gzip archive file we use the option as<font color=red>z</font>.  


```bash
# Note : tar.gz and tgz both are similar
tar -cvzf all-fruit-06-26-20.tar.gz dir1/dir2
tar -cvzf all-fruit-06-26-20.tar.tgz dir1/dir2

# Note: tar.bz2 tar.tbz tar.tb2 are similar
tar -cvzf all-fruit-06-26-20.tar.bz2 dir1/dir2
```
#### Untar tar Archive File:

To untar or extract a tar file, just issue following command using option<font color=red>x</font> (extract).

If you want to untar in a different directory then use option as<font color=red>-C</font>(specified directory).

```bash
# Untar files in Current Directory
tar -xvf all-fruit-06-26-20.tar

# Untar files in specified Directory
tar -xvf all-fruit-06-26-20.tar -C ~/Documents/fruit

# Untar files in tar.gz
tar -xvf all-fruit-06-26-20.tar.gz

# Untar files in tar.bz2
tar -xvf all-fruit-06-26-20.tar.bz2
```

#### List Content of tar Archive File:

To list the contents of tar archive file, just run the following command with option <font color=red>t</font> (list content). 

```bash
tar -tvf all-fruit-06-26-20.tar
tar -tvf all-fruit-06-26-20.tar.gz
tar -tvf all-fruit-06-26-20.tar.bz2
```

#### zip and unzip
zip: to compress files into a zip archive
unzip: to extract files from a zip archive.

```bash
# compress
zip -r fruit.zip /dir1/dir2 #-r: Travel the directory structure recursively
zip -q -r fruip.zip * # if we are in the directory

# uncompress
unzip file.zip -d destination_folder

# if the source and destination directories are the same
unzip file.zip
```

### 9. chmod -- change file modes or Access Control Lists

```bash
#sets read, write, and execute permissions for user, and sets read permission for Group and Others
chmod 744 myCV.txt 
```
7(111):rwx  user

5(101):r-x  group

4(100):r--  Other


### References:
[Learn basic commands for Linux, a free and open-source operating system that you can make changes to and redistribute.](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners)

[Learn important and helpful commands and programs often executed by intermediate Linux users.](https://maker.pro/linux/tutorial/intermediate-linux-commands)
[18 Tar Command Examples in Linux](https://www.tecmint.com/18-tar-command-examples-in-linux/)

[linux中强大且常用命令：find、grep by 吴秦](https://www.cnblogs.com/skynet/archive/2010/12/25/1916873.html)

[error redirection](https://www.guru99.com/linux-redirection.html)





