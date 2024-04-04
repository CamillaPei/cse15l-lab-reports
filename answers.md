## ls with no arguments
```
(base) Camillas-Macbook:lecture1 CosmoNil$ ls
(base) Camillas-Macbook:~ CosmoNil$ ls
=2.1                    Music                   eclipse-workspace
=3.10                   OneDrive                helloWorld.class
Applications            Pictures                helloWorld.java
Creative Cloud Files    Public                  iCloud Drive (Archive)
Desktop                 PycharmProjects         lecture1
Documents               Sites                   moefiles
Downloads               Untitled.ipynb          notes.txt
IBM                     Untitled1.ipynb         opt
Library                 dlib
Movies                  eclipse
```
The absolute path to the working directory right before the command was /home/CosmoNil$. When no arguments are given, ls lists the files and folders of the current working directory, therefore the folders and files in my laptop are printed as expected. This output is not an error.

## ls with a path to a directory
```
(base) Camillas-Macbook:~ CosmoNil$ ls lecture1
Hello.class     Hello.java      README          messages
```
The absolute path the to working directory right before the command was /home/CosmoNil$. When a path to a directory (lecture1 in this case) is given, ls lists the files in lecture1. This output is not an error.

## ls with a path to a file as an argument 
```
(base) Camillas-Macbook:~ CosmoNil$ ls lecture1/Hello.java
lecture1/Hello.java*
```
The absolute path the to working directory right before the command was /home/CosmoNil$. When a path to a file is given and if the file exists, ls displays the file. Therefore, when the path to Hello.java, which exists in lecture1, is provided, the file information is printed as an output. This output is not an error.

## cd with no arguments
```
(base) Camillas-Macbook:~ CosmoNil$ cd
(base) Camillas-Macbook:~ CosmoNil$ 
```
The absolute path to the working directory right before the command run was /home/CosmoNil$. When no argument is provided, cd takes you to the home directory, which is shown on the second line of code. This output is not an error. 

## cd with path to a directory
```
(base) Camillas-Macbook:~ CosmoNil$ cd lecture1
(base) Camillas-Macbook:lecture1 CosmoNil$ 
```
The absolute path to the working directory right before the command run was /home/CosmoNil$. When a path to a directory is provided, cd switches the current working directory to the given path. In this case, a path to lecture1 is provided therefore it is shown on the second line. This output is not an error. 

## cd with path to file
```
(base) Camillas-Macbook:lecture1 CosmoNil$ cd messages/en-us.txt
bash: cd: messages/en-us.txt: Not a directory
```
The absolute path to the working directory right before the command run was /home/CosmoNil$/lecture1. When a path to a file is provided, “Not a directory” is printed out because a file is not a directory. Cd switches the current working directory to the given path, and it doesn’t work with files. This output is an error because cd can only change the current directory, not file.

## cat with no arguments
```
(base) Camillas-Macbook:lecture1 CosmoNil$ cat
hi
hi
heyy
heyy
^C
```
The absolute path to the working directory right before the command run was lecture1. When no argument is given, it waits for the user to input then print out the input. So when I type in “hi”, it prints out “hi”; when I type in “hello”, it prints out “hello”. The output is not an error. 

## cat with a path to directory
```
(base) Camillas-Macbook:lecture1 CosmoNil$ cat messages
cat: messages: Is a directory
```
The absolute path to the working directory right before the command run was /home/CosmoNil$/lecture1. When a path to a directory is given as an argument, it prints out “cat: messages: Is a directory” because concatenate is used to print the contents of one or more files given by the path, it doesn’t work with directories. Therefore, the output is an error because cat only works with files. 

## cat with a path to file
```
(base) Camillas-Macbook:lecture1 CosmoNil$ cat messages/en-us.txt
Hello World!
(base) Camillas-Macbook:lecture1 CosmoNil$ cat messages/en-us.txt messages/zh-cn.txt
Hello World!
你好世界
```
The absolute path to the working directory right before the command run was /home/CosmoNil$/lecture1. When a path to one file is given as an argument, it prints out the content in that file. When two files are given by the path, it prints out contents in both files because concatenate is used to print contents of one or more files given by the path. The output is not an error. 
