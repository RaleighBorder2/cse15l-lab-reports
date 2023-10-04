# Commands cd, ls, and cat
__1. cd__
 - Using cd with no argument will return the console to the home directory.  This is not an error, but an intended feature of the cd command.
```
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
[user@sahara ~/lecture1/messages]$ cd
[user@sahara ~]$ pwd
/home
```
_The working directory begins in ./lecture1/messages, and moves to the home directory after the command is executed._
 - Using cd with a directory address will move the console to the specified directory, as long as the directory exists within the working directory.
```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ cd notMessages
bash: cd: notMessages: No such file or directory
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
_The working directory begins in home, and changes to ./lecture1 after the command is run successfully.  The command has no effect if the specified directory does not exist._ 
 - Using cd with a file produces an error, as its intended purpose is to change the working directory, and changing working directory to a file is nonsensical.  
```
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
[user@sahara ~/lecture1]$ cd README
bash: cd: README: Not a directory
```
_The command runs succesfully once, when used with a directory, but returns an error and has no effect when used with anything that is not a directory._

---

__2. ls__
 - Using ls with no argument will display all files present in the current working directory.
```
[user@sahara ~]$ ls
lecture1
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
```
_The working directory begins in the home directory, which contains only the lecture1 directory, as shown by ls.  After switching directories, ls shows all files and directories present in ./lecture1._
 - Using ls with a directory as an argument will display a list of all files and directories within the specified address, assuming the address is accesible.
```
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~]$ ls lecture2
ls: cannot access 'lecture2': No such file or directory
[user@sahara ~]$ ls ./lecture1/messages
en-us.txt  es-mx.txt  ko.txt  zh-cn.txt
```
_The current working directory is home, but using an address, the contents of other directories can be displayed.  Does not work with "lecture2", as the directory must exist and be accesible._
 - Using ls with a file repeats the filename.  
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ ls README
README
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
_Above, the ls command repeats the names, "README" and "Hello.java"._

---

__3. cat__
 - Using cat with no argument causes nothing to happen, as the command will continue to wait for more inputs.  This is a kind of error, as the command will not do anything but keep the console useless for as long as it is running. 

```
[user@sahara ~]$ cat


^C
```
_The command will do nothing but wait, and this state only ends when the kill signal is sent with ^C._
 - Using cat with a directory as an argument will cause an error, as this command does not do anything with directories. 
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```
_As expected, an error is displayed._
 - Using cat with one or more files will cause the contents of the specified files to be displayed together.
```
[user@sahara ~/lecture1/messages]$ cat en-us.txt
Hello World!
[user@sahara ~/lecture1/messages]$ cat en-us.txt es-mx.txt ko.txt zh-cn.txt
Hello World!
¡Hola Mundo!
안녕하세요 세상!
你好世界
```
_The contents of the txt files are displayed in the order the txt files are given to the function._


