# Unix Basics

> A quick introduction to the Unix command line.

## Introduction

The Unix shell is a program that allows you to run other programs via a text interface.

### Running a program

To run a program, type its name and hit `<Enter>`. For example, the `pwd` program is for printing the path of the current directory:

```
$ pwd
/home/f/foo
```

### Passing arguments to a program

Some programs accept arguments, which come after the name of the program. For example, the `cd` program is for changing the current directory:

```
$ cd bar
$ pwd
/home/f/foo/bar
```

## Commands

Listed here are the more important command line operations that you should/must know.

Operations | Command
:--|:--
Print the path of the current directory | `pwd`
List all files and directories in the current directory | `ls -a`
Change the current directory to the given directory | `cd foo`
Change the current directory to the home directory | `cd`
Change the current directory to the parent directory | `cd ..`
Print the contents of a file | `cat foo`
Create an empty file | `touch foo`
Create an empty directory | `mkdir foo`
Copy a file | `cp foo bar`
Copy a file at a given path to the current directory | `cp ~/foo/bar .`
Copy a directory | `cp -r foo bar/`
Delete a file | `rm foo`
Delete a directory | `rmdir foo`
Compare the contents of two files | `diff foo bar`
Move/rename a file/directory | `mv foo bar`
Clear the terminal screen | `clear`
Show your command history | `history`
Open the user manual for a command | `man foo`

### Tips

1. Before hitting `<Enter>`, you can press `<Ctrl>` + `c` at any time to discard the command you&rsquo;d entered.
2. Press `<Ctrl>` + `d` to terminate a running program.
3. Issue the `pwd` and `ls -a` commands to orient yourself to the current directory.
4. Use the <code>&uarr;</code> and <code>&darr;</code> arrow keys to toggle through your command history.
5. Use the `<Tab>` key to autocomplete commands.

### How paths work

Many programs accept files/directories as arguments. A file/directory can be specified as follows:

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

The output of a program will be displayed on the terminal (ie. `stdout`):

```
$ java HelloWorld
Hello, World
```

You can redirect the output to a file via the `>` operator.

```
$ java HelloWorld > foo
$ cat foo
Hello, World
```

### Redirect input

A program may accept input from the keyboard (ie. `stdin`):

```bash
$ java HelloMe
foo
Hello, foo
```

You can use the contents of a file as the input to a program via the `<` operator:

```
$ cat input
foo
$ java HelloMe < input
Hello, foo
```

### Both

You can use *both* the `<` and `>` operators in a single command:

```bash
$ java HelloMe < input > output
$ cat output
Hello, foo
```

## Further reading

- [Introduction to Unix and the Command Line](https://github.com/cyberwizardinstitute/workshops/blob/master/unix.markdown)
- [The Unix Philosophy](http://www.faqs.org/docs/artu/ch01s06.html)
