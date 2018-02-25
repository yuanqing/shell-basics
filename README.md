# Unix Basics

> A quick overview of the Unix shell.

- [Introduction](#introduction)
- [Commands](#commands)
- [Paths](#paths)
- [I/O redirection](#io-redirection)
- [Shell scripts](#shell-scripts)
- [The `<Ctrl>` + `z` &ldquo;problem&rdquo;](#the-ctrl--z-problem)
- [See also](#see-also)

## Introduction

The Unix shell (or *terminal*, or *command line*) is a program that allows us to run other programs via a text interface.

### Running a program

To run a program, type its name and hit `<Enter>`. For example, the `pwd` program is for printing the path of the current directory.

```sh
$ pwd
/home/y/yuanqing
```

(In all examples shown, a command is indicated with a `$` prefix. Do not type the `$`.)

### Passing arguments to a program

Some programs accept arguments, which come after the name of the program. For example, the `cd` program is for changing the current directory:

```sh
$ cd foo
$ pwd
/home/y/yuanqing/foo
```

## Commands

Listed here are the more important command line operations that you should know.

Operation | Command
:--|:--
Show the path of the current directory | `pwd`
List all files and directories in the current directory | `ls -a`
List all files and directories in the current directory, excluding hidden files | `ls`
Change the current directory to the specified directory | `cd foo`
Change the current directory to the home directory | `cd`
Change the current directory to the parent directory | `cd ..`
Change the current directory to the previous directory | `cd -`
Show the contents of a file | `cat foo`
Print a string | `echo 'foo'`
Create an empty file | `touch foo`
Create a file containing the specified string | `echo 'foo' > bar`
Create an empty directory | `mkdir foo`
Copy a file | `cp foo bar`
Copy a file at the specified path to the current directory | `cp ~/foo/bar .`
Copy a directory | `cp -r foo bar/`
Delete a file | `rm foo`
Delete a directory | `rm -rf foo`
Move/rename a file/directory | `mv foo bar`
Compare the contents of two files | `diff foo bar`
Clear the terminal screen | `clear`
Show your command history | `history`
Open the user manual for a command | `man foo`
Write the output of a program to a file | `java HelloWorld > foo`
Write the output of a program to a file, appending to the end of the specified file | `java HelloWorld >> foo`
Use the contents of a file as the input to a program | `java Hello < input`
Use the contents of a file as the input to a program, and write its output to a file | `java Hello < input > output`
Run the shell commands listed in the specified text file | `bash foo`
Bring the most recent &ldquo;backgrounded&rdquo; program back to the foreground | `fg`

Before hitting `<Enter>`, you can:

1. Press `<Ctrl>` + `c` at any time to discard the command.
2. Use the <code>&uarr;</code> and <code>&darr;</code> arrow keys to toggle through your command history.
3. Use the `<Tab>` key to autocomplete commands.

To terminate a running program, press `<Ctrl>` + `d`. (See [the `<Ctrl>` + `z` &ldquo;problem&rdquo;](#the-ctrl--z-problem).)

## Paths

Many programs take files/directories as arguments. A file/directory path can be specified as follows:

File/directory | Path
:--|:--
The current directory | `.`
The parent directory | `..`
The directory two levels up | `../..`
The home directory | `~`
The root directory | `/`
A file/directory in the current directory | `foo` or `./foo`
A file/directory in the parent directory | `../foo`
A file/directory in the directory two levels up | `../../foo`
A file/directory in the home directory | `~/foo`
A file/directory in the root directory | `/foo`

## I/O redirection

### Redirect output

The output of a program is typically displayed on the terminal (ie. `stdout`):

```sh
$ javac HelloWorld.java
$ java HelloWorld
hello world
```

Use the `>` operator to write the program&rsquo;s output to a file:

```sh
$ java HelloWorld > foo
$ cat foo
hello world
```

If you use the `>` operator, the specified file will be *overwritten*, so be careful! To merely *append* the output to the end of the specified file, use the `>>` operator instead:

```sh
$ java HelloWorld >> bar
$ cat bar
hello world
$ java HelloWorld >> bar
$ cat bar
hello world
hello world
```

### Redirect input

Many programs accept input from the keyboard (ie. `stdin`):

```sh
$ javac Hello.java
$ java Hello
foo
hello foo
```

(Here, [Hello](https://gist.github.com/yuanqing/6bc1da264cd7ba108d8325d7b49ad2b3) is a toy Java program that accepts a string, then outputs <code>hello&nbsp;</code> followed by the string that was entered.)

We can use the contents of a file as the input to a program via the `<` operator:

```sh
$ cat input
foo
$ java Hello < input
hello foo
```

### Redirect input and output

We can redirect both input and output in a single command:

```sh
$ javac Hello.java
$ cat input
foo
$ java Hello < input > output
$ cat output
hello foo
```

## Shell scripts

A shell script is simply a sequence of commands listed in a text file.

Suppose we have a text file named `commands` containing the following:

```sh
javac Hello.java
cat input
java Hello < input > output
cat output
```

We can run the commands listed in the `commands` text file using the `bash` program:

```sh
$ bash commands
foo
hello foo
```

## The `<Ctrl>` + `z` &ldquo;problem&rdquo;

If you&rsquo;d pressed `<Ctrl>` + `z` while a program was still running, you would see something like the following:

```sh
$ javac Hello.java
$ java Hello
^Z
[1]+  Stopped                 java Hello
```

A quick fix is to run the `fg` program:

```sh
$ fg
```

This brings us back to our running program, and all is well with the world.

(Explanation: Pressing `<Ctrl>` + `z` [places the currently-running program in the background](http://en.wikibooks.org/wiki/A_Quick_Introduction_to_Unix/Job_Control#Controlling_Jobs_in_Unix). The `fg` program simply brings the most recent &ldquo;backgrounded&rdquo; program back to the foreground.)

## See also

- [Vim Basics](https://github.com/yuanqing/vim-basics/blob/master/README.md)
- [Unix Workshop](https://github.com/cyberwizardinstitute/workshops/blob/master/unix.md)
- [The Unix Philosophy](http://www.faqs.org/docs/artu/ch01s06.html)
