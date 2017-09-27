As a note, if you have not downloaded [Sublime Text](https://www.sublimetext.com/) now is a great time to do so!

##  What is a GUI (pronounced gooey)?

We frequently interact with computers via a Graphical User Interface (GUI). This means using a mouse and keyboard to navigate through the computer, to open and use programs, and to operate things generally. 

However, we can also go through the computer using the Command Line Interface (CLI). When we're doing things this way, we use just the keyboard to operate things. **However**, we can still do (almost) everything that the mouse and keyboard together would let us do! We can still:

- Open and close folders
- Read files
- Run programs
- Change information
- Delete files

A [**shell**](https://en.wikipedia.org/wiki/Unix_shell) is the user interface to interact with the computer system. We will primarily be using a Unix shell in this section, which is a CLI that interprets a user's commands and executes them on the operating system. 

##### Opening and closing the terminal

Spotlight in OSX is the easiest and fastest way to open the terminal:

- ⌘ (Command) + Space
- "Terminal"
- Enter

**Note**: iTerm 2.0 is a (completely optional) replacement for Terminal.

Notice that you can actually hit enter as soon as the field autocompletes. *Get used to taking shortcuts* – don't type the whole word out if you don't have to and avoid using your mouse if you can open or use an app with just keyboard shortcuts. It may seem harder now, but when you get used to it, it will save you literally hours of cumulative time. 

##### Getting comfortable in the CLI

1. For many programs, you can open multiple tabs by pressing **⌘-T**.
  - Try it in your terminal!
2. You can close the current tab or window with **⌘-W**. This goes for most applications on a Mac.
  - Try _that_ in your terminal!
3. If you have a process running, you can quit it by pressing **Ctrl-C**. Let's try that now.

  - At the command line, type `ping 127.0.0.1`. This basically sends a message to your own computer asking if it's awake.
  - Notice that it will keep pinging, even if you type something.
  - To stop the currently-running script, press **Ctrl-C**.

4. To quit the command line altogether, you can press **⌘-Q**.

**Check** Try pinging google.com in the terminal. How do you stop pinging google?

[Here](http://ss64.com/nt/syntax-keyboard.html) are some equivalent Windows shortcuts.

———

## Paths - Demo

Every file or folder in a file system can be read, written, and deleted by referencing its position inside the filesystem.

When we talk about the position of a file or a folder in a file system, we refer to its "path". There are a couple of different kinds of paths we can use to refer to a file: the **absolute path** and the **relative path**.

**Directory** is an important term that's used interchangeably with **folder**. Though they are not exactly the same thing, when we say "navigate to your project directory" think of this as "navigate to your project folder".

##### Important Directory Locations

- `/` -- this is known as the root directory. It is the top most level of your computer and it contains all of your files. If you were on a Windows machine, this would be equivalent to `C:/`
    - _Note_: If you **are** on a Windows machine, GitBash still uses the typical Unix notation, so your root directory will also be `/`
    - _Note_: If you begin any directory that you are looking for with `/`, it will try to find that folder _directly in your root directory_ -- try to avoid this unless you know that it is there!
- Home -- Where this folder lives will ultimately depend on whether you are on OS X, Linux, or Windows, but you should consider this your default folder. 
    - _Note_: `~` is a handy shortcut for this
    - _Note_: Typing `cd` with no destination afterwards will move you to your home folder
- `.` -- this is a shortcut for the **current folder that you are in**
- `..` -- this is a shortcut for the **folder above your current one**

If I were at `/Users/richardharris`, what folder would I be looking at if I were looking at the `.` folder? What about the `..` folder?

##### What is an absolute path?

An absolute path is defined as the specific location of a file or folder from the root directory, typically shown as `/`. 

##### Working with unix commands and file paths

Typing `cd` - a command for "change directory" with no parameters takes us to our home directory.

```bash
cd
```

If we type in `pwd` - a command for "print working directory" from that folder, we can see where we are in relation to the root directory. The `pwd` command will always give you the absolute path of your current location.

An example of absolute path:

```bash
open /Users/Lucy/desktop/a/b/c/file.txt
```

Notice, this path starts from `/` directory which is a root directory for every Linux/Unix machines.

##### What is a relative path?

A relative path is a reference to a file or folder **relative** to the current position, or the present working directory(pwd). If we are in the folder `/a/b/` and we want to open the file that has the absolute path `/a/b/c/file.txt`, we can just type:

```bash
open c/file.txt
```

or

```bash
open ./c/file.txt
```

At any time, we can also use the absolute path, by adding a slash to the beginning of the path. The absolute path is the same for a file or a folder regardless of the current working directory, but relative paths are different, depending on what directory we are in.  Directory structures are laid out like `directory/subdirectory/subsubdirectory`.

**Check:**  What is the difference between an absolute path and a relative path?

#### Navigating using the command prompt

The tilde `~` character is an alias to your home directory. Use it to quickly return home.

```bash
cd ~\
```

Or even more simply, you can just type:

```bash
cd
```

The tilde `~` character is useful to shorten paths that would otherwise be
absolute paths. For example, to navigate to your Desktop you can type:

```bash
cd ~/Desktop
```

The `ls` command lists files and directories in the current folder.
```bash
ls
```

It can also be used to list files located in any directory. For example to list your applications you can type:
```bash
ls /Applications
```

To make a new directory.
```bash
mkdir folder
```

To create a new file.
```bash
touch file1
```

##### Warning -- Destructive Commands Ahead!

To remove a file.
```bash
rm file1
```

To remove a directory/folder, we need to add a **flag** to the rm command.
```bash
rm -r folder/
```

What is the **-r** flag? It stands for "recursive". It's not important to get into the technicalities of this right now, but essentially it is telling the remove command to get rid of the folder and anything within the folder at any "depth". Even if a folder is empty, the OS requires the recursive flag for deleting it.

##### Using wildcards in the command prompt

The wildcard symbol `*` is useful for using commands to operate on multiple
files. To give an example first create a folder on your Desktop and add some
files.
```bash
mkdir ~/Desktop/example_folder
cd ~/Desktop/example_folder
touch cat.txt
touch dog.txt
touch bird.txt
touch fish.txt
```

You can use the wildcard `*` to then operate on subsets of files. List any
file with "i" in the filename, for example:
```bash
ls *i*
```

Or remove any file with "d":
```bash
rm *d*
ls
```

**Check:** What's a quick way to get back to your home directory?

**Check:** What are the natural language equivalents of the following commands? (The first is done for you)
- `cd` (**C**hange **D**irectory)
- `pwd`
- `rm`
- `touch`
- `ls`

## Editing and Examining Files

---

At times it's helpful to edit files in a pinch. We can use the terminal editor `nano` to accomplish this.

Editing files from the terminal with `nano` can be accomplished with the following syntax:

`nano [filename]`

These hotkeys are available:

* **ctrl-w**: Search within file.
* **ctrl-o**: Save file as [filename].
* **ctrl-x**: Exit editor.

*The bottom of the editor contains the most common operations.*

### Echo file content to the terminal

Sometimes it's nice to view the contents of files as text. There are a variety of ways to do this. The commands `cat`, `head`, and `tail` will allow us to view the entire or partial contents of a target file.

```
cat /etc/passwd
```

*Traditionally, the /etc/passwd file is used to keep track of every registered user with access to a system.*

**Only the first few lines of a file**

This command is useful when looking at files that might be too large to open in a traditional editor such as Sublime or Atom.
```
head /etc/passwd
```

**Only the last few lines of a file**
```
tail /etc/passwd
```

*You can also pass the paramter -n to `head` and `tail` to control the amount of output that is displayed*

### Searching inside files: grep

The wonderful `grep` command will search within files and traverse within subdirectories.

**Find all files containing the word "the"**
```
grep -r "the" *
```

*Omitting -r will cause `grep` to only look within the current subdirectory.*
*Using -i will make `grep` ignore the casing of characters, but at the expense of efficiency.*

## Finding files

---

By far, the most useful operation from the terminal is finding files. `locate` finds files all over your file system.  The `find` command will find files relative to the current working directory but needs to be used in conjunction with a pipe operation.

### Find all notebook files within subdirectories of the current working directory
`find . | grep ipynb`

### Find specific file(s) within the entire system
`locate nanorc`

### Find specific file(s) with a substring match
`locate log`

### Misc trick:  Counting the number of lines in a file

At times, you may not want to load an entire file in memory. Using a combination of `head`, `tail`, `cat`, and a new command — `wc` — you can quickly assess the various size characteristics of any file.

#### Find the number of lines in a file
```bash
cat /etc/passwd | wc -l
```

#### Find the number of words in a file
```bash
cat /etc/test.txt | wc -w
```

### You probably have questions about "piping"...
Here's some optional (but highly recommended) reading about pipe and I/O redirection on the command line:

* [I/O redirection](http://linuxcommand.org/lts0060.php)
* [Good examples of piping commands together](http://unix.stackexchange.com/questions/30759/whats-a-good-example-of-piping-commands-together)

## Moving Files

The command line offers two different ways to move files around back and forth!

#### Copy a file using `cp`

```bash
cp path/to/file path/to/destination
```

Use `cp` to take a file at the location in the first argument and make a copy of it at the second argument. The file will now exist in both places!

#### Move a file using `mv`

```bash
mv path/to/file path/to/destination
```

Use `mv` to take a file at the location in the first argument and **move** it to the second argument. The file now only exists in one place (the second argument!)

_Note_: This is also how you rename files on the command line! If I wanted to rename `readme.md` to `readthis.md`, I would do the following:

```bash
mv readme.md readthis.md
```

#### I'm stuck!

Here are some tips for getting through the command line:

1. If the CLI doesn't seem to be responding to your input, try pressing `Ctrl+c` (control and c together) -- that will stop anything actively running on the command line 
2. Especially starting out, make liberal use of `pwd` and `ls` -- the quicker that you can build a map in your head of your system, the more skillfully you'll be able to navigate it!
3. Be very careful about using `rm` 
4. Don't type everything out! Type as much as you need to and use `<tab>` to autocomplete. If you hit tab and nothing comes up, hit tab twice in rapid succession and it will show you all the possibilities it could autocomplete at that point. Type until you've uniquely identified the file or folder you're pointing at and then use tab.

## Independent Practice: Try it Out! 

(Some exercises taken from [Learn Enough Command Line to Be Dangerous](https://www.learnenough.com/command-line-tutorial))

1. Starting in your home directory, execute commands to make a directory `foo`, change into it, create a file `bar` containing the string `baz`, print out `bar`’s contents, and then change directory back to the directory you came from. 
2. Delete the `foo` directory and try the previous step, but this time write it so that it executes it all in one line. 
  - _Hint_: You may need to google the `&&` symbol on the command line to make this work. Get used to googling things that you do not know yet! It is the best tool we data scientists have.
3. Without deleting the `foo` directory, what happens when you run the previous command again? How many of the commands executed? Why?
4. With a partner in the room, work together on each person's machine to show examples of the following commands. Note that some of these commands we have not discussed / these commands may not be on your machines currently! Again, making use of Google is the best thing you can do.
  - `mkdir`
  - `touch`
  - `echo`
  - `cd`
  - `pwd`
  - `ls`
  - `rm` **Do not run this unless you know what you are doing!**
  - `cp`
  - `mv`
  - `sleep`
  - `man`
  - `grep`
  - `open`
  - `cat`
  - `cowsay`
5. **Mini-lab**: Challenge yourself to get through the [Lion King CLI Lab](./lion_king.md)!

## Conclusion
Today we learned about the CLI commands mkdir, touch, cd, pwd, and ls. We also discussed absolute and relative paths.
Take a breather and then keep practicing. The more you practice, the more comfortable you'll get!