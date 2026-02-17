## `Shell Scripting`

A shell scripting is a text file that contains a sequence of commands for a UNIX-based operating system. It is called a shell script because it combines a sequence of commands, that would otherwise have to be typed into the keyboard one at a time, into a single script. A shell script is usually created for command sequences in which a user has a need to use repeatedly in order to save time.

### `Linux Kernel`

It is an interface between hardware and software.

A kernel is a program that is stored inside your operating system. It is like a program or a command that keeps running. It takes commands from the shell, and the shell can be anything like a GUI in Windows or Linux, or a terminal that runs Bash, shell, or c-shell.

Shell and kernel together, built as one package, are called an operating system. That operating system can be any OS like Linux, Unix, Mac, or Windows. Every operating system has that little program that actually talks to your hardware, and the shell, which is written in the C programming language as well, is the software application. So this is what the real kernel means. We really need a kernel in any operating system to talk to our hardware.

```bash
User
  ↓
Applications
  ↓
Operating System
    ├── Shell
    └── Kernel
  ↓
Hardware
```
### `Layered architecture of an operating system`

Hardware is the physical part of the computer, such as the CPU, memory, hard disk, and network devices. On top of the hardware runs the kernel, which is the core part of the operating system and directly communicates with the hardware to manage resources like CPU, memory, processes, and devices. The operating system includes the kernel along with the shell and system libraries, and it acts as a bridge between hardware and software. The shell is an interface that allows users to interact with the operating system, either through a command-line interface like Bash or a graphical user interface. Applications run on top of the operating system and use its services to perform tasks. Finally, the user interacts with the applications or the shell to perform operations on the computer.

## `Shell`

A shell is an interface between the user and the kernel or operating system. It acts like a container that allows users to communicate with the system. The shell accepts commands from the user and passes them to the kernel for execution. It can be a command-line interface (CLI) such as sh or bash, or a graphical user interface (GUI) like Windows GUI or Linux KDE.

`Types of linux shells` -

1. Gnome - GUI
2. KDE - GUI
3. sh - borne shell
4. Bash - borne again shell
5. csh and tcsh
6. ksh - corn shell

To know the shells installed - `cat /etc/shells`

### `To automate tasks`

A shell script is an executable file containing multiple shell commands that are executed in a sequential order. The file can contain -

```bash
shell (#!/bin/bash)
comments (#)
commands (echo, cp, grep, etc.)
statements (if, while, for, etc.)
```
A script is nothing but an empty file. Of course, everything in Linux is just a file until we change it to an executable, a link, or keep it as a regular file. Shell scripts should have executable permissions (-rwxr-xr-x). A shell script has to be called using its absolute path (for example, /home/userid/script.bash). If it is called from the current location, then it should be executed as ./script.bash.

### `Symbols and its meaning - Special/positional parameters`

```bash
## Shell Special Variables

$0 --> The filename of the current script.
$n --> These variables correspond to the arguments with which a script was invoked. Here n is a positive decimal number corresponding to the position of an argument (the first argument is $1, the second argument is $2, and so on).
$# --> The number of arguments supplied to a script.
$* --> All the arguments are double quoted. If a script receives two arguments, "$*" is equivalent to "$1 $2".
$@ --> All the arguments are individually double quoted. If a script receives two arguments, "$@" is equivalent to "$1" "$2".
$? --> The exit status of the last command executed.
$$ --> The process number of the current shell. For shell scripts, this is the process ID under which they are executing.
$! --> The process number of the last background command.
```
## `Basics of shell scripting`

Shell scripting allows us to automate daily Linux tasks. Many commands that we run manually—such as creating files or directories, checking user IDs, redirecting output to a file using >, or using text processors like cut, awk, grep, sort, uniq, and wc—can be combined into a script to get the desired result automatically.

We can print output to the screen using the echo command. In Linux, if we want a group of words to be considered as a single word (for example, Linux class), we use single quotes like 'Linux class'.

Variables in shell scripting act like containers that store values. We can assign values to variables and use them later in the script.

To execute a shell script, the file must have executable permissions. We can give execute permission using:

```bash
chmod a+x filename
```
`Example` - `output to screen`

```bash
#!/bin/bash
echo hello world
```

### `To execute`
```bash
chmod a+x output-screen
./output-screen
```
`Example` - `using Variables - variable screen `

```bash
#!/bin/bash
# Example of defining variables

a=naveen
b=krishna
c=kamuju

echo "My first name is $a"
echo "My middle name is $b"
echo "My last name is $c"
```

Make it executable and run - 
```bash
chmod a+x variable-screen
./variable-screen
```

## `Input and Output of script`

In shell scripting, we can interact with the user by taking input and displaying output. The shell can wait for user input using the read command. The echo command is used to display output on the screen.

The read command pauses the script and waits for the user to enter a value. The entered value is stored in a variable (a container), which can then be used later in the script.

`Example - Taking user input`

```bash
#!/bin/bash
# Description

echo "Hello, my name is KNK"
echo
echo "What is your name?"
read namecont   # namecont is the variable to store the input value
echo
echo "Hello $namecont"
echo
```
In this example:  
  - read namecont waits for user input.  
  - The entered value is stored in the variable namecont. `$namecont` is used to display the stored value.

`Example - Storing command output in a variable`  
We can also store the output of a command inside a variable using backticks ` ` (or $( ), which is the modern method).

```bash
#!/bin/bash
# Description

a=`hostname`

echo "Hello, my name is $a"
echo
echo "What is your name?"
read b
echo
echo "Hello $b"
echo
```
`Important Note`

If you assign a simple value to a variable, you can use it normally with $variablename. However, if you want to store the output of a command inside a variable, you must use backticks:

```bash
a=`command`
```
OR the recommended modern syntax:

```bash
a=$(command)
```
`Example`

```bash
a=$(hostname)
```
This stores the system’s hostname inside variable a.

## `If-then scripts`

In shell scripting, an if-then statement is used to make decisions. 

If a condition is true → do this  
Otherwise → do that

The if statement allows us to check conditions such as whether a file exists, whether a variable is empty, or whether two values are equal.

`Common File Test Options` -

-e → Checks if a file exists  
-f → Checks if it is a regular file  
-z → Checks if a string is empty  
!= → Not equal to  

`Example: Searching for a Keyword in Files`

The following script checks files in a folder and searches for a keyword inside each file.

`If the file exists`:  

  - It searches for the keyword "spo"  
  - If the keyword is not found → prints EMPTY  
  - If found → prints FOUND!  

`If the file does not exist`:

  Prints that it is not a file.

```bash
#!/bin/bash

for myfile in *
do
    if [ -f "$myfile" ]; then
        echo "$myfile"

        grep -ni "spo" "$myfile"
        check=$(grep -ni "spo" "$myfile")

        if [ -z "$check" ]; then
            echo "EMPTY"
        else
            echo "FOUND!"
        fi
    else
        echo "$myfile is NOT a file."
        echo
    fi

    echo "----------------------------------------"
done
```

## `For script`

A `for loop` allows you to execute a script multiple times. It runs repeatedly until all items have been processed or a specified condition has been satisfied.

A for loop can run based on:

  1. A specified number of times.
      For example, if a variable is set to 10, the script will run 10 times.

  2. list of values.
      For example, if a variable contains green, blue, and red, the script will run three times — once for each color.

The for loop is a powerful statement in a scripting environment because it allows repetitive tasks to be executed again and again automatically.

For incrementing by 1 in a loop, we use:

  `((i++))`
This increases the value of i by 1 during each iteration.

## `Do-while Scripts`

Do-while scripts are very similar to for loop scripts. The while statement continually executes a block of commands as long as a particular condition is true or satisfied.

In many cases, scripts such as daemons or background processes never stop running. They continue running as long as the condition remains true. These types of processes often use while loops.

For example, you can run a script until a specific date and time, such as August 2024 at 2 PM, by setting the appropriate condition in the loop.

Basic syntax
```bash
while [ condition ]
do
   command1
   command2
   commandN
done
```
A daemon process is commonly written using a while loop so that it keeps running continuously until it is manually stopped or the condition becomes false.

## `Case statement scripts`

A case statement is used to perform different actions based on different options selected by the user.

   1. If option A is selected, do this.    
   2. If option B is selected, do this.    
   3. If option C is selected, do this.  

Most installation programs are written using case statements, where the script waits for user input and allows the user to select from multiple choices.

The if-then statement looks for a matching condition, whereas the case statement provides a list of options to choose from and executes the corresponding block of code based on the selected option.

## `Check other servers connectivity`

We can write a script to check the connectivity status of remote hosts. This is commonly done using the ping command.

To ping a host only once, use:
`ping -c1 <ip_address>`
The -c1 option means the ping command will send only one packet.

To check the result of the ping command, we use:
`$?`

The special variable $? stores the exit status of the last command executed. By default:
    0 means success
    Any non-zero value means failure

Example condition:

`if [ $? -eq 0 ]`

This checks whether the previous command was successful.

If you do not want to display the ping output on the screen, you can redirect it to /dev/null:

`ping -c1 192.168.1.1 &> /dev/null`

/dev/null is a special file in Linux. Any output redirected to this file is discarded. It is often called a null file because whatever you send to it simply disappears.

## `Aliases = Shorter name`

```bash
# Aliases
# Aliases are used to shorten lengthy and repetitive commands.

alias ls="ls -al"
alias pl="pwd; ls"
alias tell="whoami; hostname; pwd"
alias dir="ls -l | grep ^d"
alias lmar="ls -l | grep Mar"
alias wpa="chmod a+w"
alias d="df -h | awk '{print \$6}' | cut -c1-4"
```
To remove alias = `unalias "aliasname"`

## `Creating User or Global Aliases`

Aliases can be created either for a specific user or for all users on the system. A user alias applies only to a specific user profile. To create a user alias, edit the following file:

```bash
/home/user/.bashrc
```
Any alias added to this file will be available only to that particular user.

A global alias applies to all users who have an account on the system. To create a global alias, edit:

```bash
/etc/bashrc
```
Any alias added to this file will be available to everyone on the system.

After making changes, reload the file using:

```bash
source ~/.bashrc
```

## `Shell history`

All commands executed in the shell are recorded in the shell history.

When you run the history command, it displays a list of all previously executed commands, sorted by their serial numbers. If you want to run a particular command from the history, you can use its serial number.

```bash
406  pwd
```
To execute this command again, you would run:

```bash
!406
```

The file where the shell command history is stored is:

```bash
/home/yourname/.bash_history
```

To view another user's shell history, you must have root privileges. First, switch to the root user:

```bash
su -
```

Then view the history file:

```bash
cat /home/username/.bash_history
```

## `Functions`

A function is a small block of code that can be reused multiple times within a script without copying and pasting it repeatedly. Functions are useful when we need to perform the same action multiple times.

### `Example`

```bash
#!/bin/bash

mydate() {
    echo "Today is:"
    date
    echo "Have a GREAT day!"
}

hello2() {
    echo "Hello $1"
    echo "Hello also to $2"
    return 35
}

echo "Start here"
mydate
echo "-------------------------"
hello2 "Mark" "blabla"
echo "Return value of my function is $?"
```
One of the advantages of functions is that they can accept input values (arguments).

  1. $1 refers to the first input value given to the function.
  2. $2 refers to the second input value given to the function.

Just like terminal commands, functions also return a value.
By default:
  1. 0 means success
  2. A non-zero value means something went wrong

The return value of a function can be accessed using:
`$?`
We can also manually set the return value inside a function using the return statement.