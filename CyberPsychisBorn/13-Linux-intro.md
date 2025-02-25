# Linux Intro - Lesson 1: Basic Commands


The Linux command line (also known as the terminal or shell) allows users to interact with the system using text-based commands. Mastering basic commands is the first step toward becoming proficient in Linux.

### Basic Navigation Commands

### a) pwd – Print Working Directory

The pwd command displays the current directory you are in.

Useful when navigating through the Linux file system to avoid getting lost.

Example:

input example
```
pwd
```

Output Example:
```
/home/user/Documents
```
### Ls - listing files and directories 

ls shows what's inside the current folder. It lists files and subfolders.

Why it’s useful:

Lets you see what files and folders exist.

Helps you find the file or folder you want to work with.

More options:

ls -l → Show detailed info (permissions, size, etc.).

ls -a → Show hidden files (files that start with .).

input example 

```
ls
```

output example 

```
file1.txt  file2.txt  Pictures  Downloads
```

### 3. cd – Change Directory

What it does:

cd lets you move between folders.

```
cd foldername
```
Moves into foldername.

```
cd Pictures
pwd
```

output 
```
home/user/pictures
```

cd goes into the pictures directory and then pwd prints the working directory to show you the location of the file. 

.. means go uo to the parent folder 

input

```
cd ..
pwd
```

output 
```
home/user
```

you can also go straight to a specific folder using cd

```
cd /home/user/downloads
```

### 4. cat – View File Contents

What it does:

cat lets you see what’s inside a file. It prints the file’s content directly in the terminal.

input 
```
cat file1.txt
```
output (if file1.txt contanins text 

```
Hello, this is a test file.
```

💡 Now you can read the file’s content without opening an editor.

📌 Why cat is useful:

Quickly check what’s inside a file.

Combine multiple files into one (cat file1 file2 > merged.txt).

## Using Find 

The find command is fantastic in a way that it can be used both very simply or rather complex depeonding on what it is you want to do exactly. 

lets start simple and assume we already know the name of the file we are looking for but cant remember where it is, in this case we are looking for passwords.txt

if we remember the filename, then we can simply use 

```
find -name passwords.txt
```
where the command will look through every folder in our current directory for that specific file 

output 
```
./folder1/passwords.txt
```
lets say we do not know the name of the dile, or want to search for every file that has an extension such as ".txt. - find lets us do that too 

we simply use what is known as a wildcard (*) to search for anything that has the .txt at the end. in this case, we want to find every .txt file that is in our current directory. We will construct a command 

```
find -name *.txt.
```
find has been able to find every .txt file and has then given us the location of each one 

output 

```
find -name *.txt
./folder1/passwords.txt
./documents/todo.txt
```
find has managed to find passwords.txt in Folder1

find has managed to find todo.txt in documents

## Using Grep 

The grep command allows us to search the contents of files for specific values that we are looking for. 

for example, the access log of a web server, in this case, the access.log of a web server has 244 entries 

```
wc -l access.log
244 access.log
```

using a command like cat would not cut it here. lets say if we wanted to search this log file to see the things that a certain user/IP address visited? looking through 244 entries isnt all that efficient considering that we want to find a specific value 

we can use grep to search the entire contents of this file for any entries of the claue that we are searching for. going with the example 

