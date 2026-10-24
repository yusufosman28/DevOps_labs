Linux

A summary of the Linux fundamentals I have covered and used hands-on, followed by real problems I hit at the terminal and how I resolved them.

Environment: Ubuntu on WSL 2 (Windows), bash.

What Linux is

Linux is an operating system used on most servers, cloud infrastructure and containers. In DevOps, most work on a Linux machine is done through the terminal rather than a graphical interface, so being comfortable at the command line is essential.

How a command runs

When I type a command, the shell (bash) interprets it and passes it to the kernel, which carries out the work on the hardware.

You → Shell → Kernel → Hardware

The shell finds the program for a command by searching the folders listed in PATH.

which ls - Shows where the ls program is stored.

echo $PATH - Shows the folders the shell searches.

A command is made up of three parts:

ls  -a  /etc
│   │   └─ argument
│   └───── option
└───────── command
ls - the command
-a - an option, which changes how the command behaves (starts with -)
/etc - the argument, what the command acts on

Commands, options and file names are case-sensitive. man <command> opens the manual for any command, which is the reliable way to check an option rather than guessing.

Navigating the filesystem

pwd - Shows the current directory.

cd <folder> - Moves into a directory.

cd .. - Moves up one level.

cd - - Returns to the previous directory.

ls -a - Lists files, including hidden files (names starting with .).

ls -l - Long listing showing permissions, owner, size and date.

An absolute path starts with / and works from anywhere (/etc/hosts). A relative path starts from the current directory (etc/hosts). ~ is the current user's home directory.

Key directories: /etc (configuration), /var/log (logs), /home (user folders), /bin (common programs), /tmp (temporary files).

Files and directories

touch - Creates an empty file.

mkdir -p a/b/c - Creates nested directories in one step.

cp -r - Copies a directory and everything inside it.

mv - Moves or renames a file.

rm / rm -r - Removes a file / a directory and its contents.

rmdir - Removes a directory only if it is empty, which acts as a safety check.

Note: ls -r reverses the sort order, while ls -R lists recursively. The same letter has different meanings in different case.

Reading files and filtering output

cat - Displays a file.

head -n 5 / tail -n 20 - Shows the first or last lines. tail is useful for checking the most recent entries in a log.

grep -i <word> - Shows only matching lines, ignoring case.

grep -E "a|b" - Matches any of several patterns.

Redirection and pipes

Every command has three streams: standard input (0), standard output (1) and standard error (2).

Symbol	Purpose
>	Write output to a file, overwriting it
>>	Append output to a file
2>	Write errors to a file
&>	Write all output to a file
2>&1	Send errors to the same place as standard output
|	Pass one command's output into the next

/dev/null discards output, for example ls missing 2> /dev/null hides the error message.

I used this to find the cause of a failed Docker build in a long log:

bash
docker build -t hello-flask-mysql . 2>&1 | grep -i -E "pkg-config|mysql_config|not found"

2>&1 sends the build errors into the pipe so grep can search them.

Permissions and ownership

ls -l shows permissions as ten characters, for example -rwxr-xr-x: the file type, then read/write/execute for the user, group and others.

Each permission has a value: read = 4, write = 2, execute = 1. Adding them per group gives the octal form:

Octal	Permissions	Typical use
644	rw-r--r--	Standard file
755	rwxr-xr-x	Script or program
600	rw-------	Private file
400	r--------	SSH private key
bash
chmod u+x deploy.sh               # add execute for the owner only
chmod 750 deploy.sh               # set all permissions at once
sudo chown priya:devops file.txt  # change owner and group
sudo chown -R priya:devops app/   # apply to a directory and its contents

chmod +x without u grants execute to everyone. When ownership is transferred, the previous owner falls into the "others" category, so their access depends on the last three permission bits.

Users, groups and sudo

sudo runs a single command with root privileges. It asks for the user's own password and every use is logged in /var/log/auth.log.

sudo adduser <user> - Creates a user.

su - <user> - Switches to another user.

sudo usermod -aG <group> <user> - Adds a user to a group. The -a (append) flag is essential: without it, the user's existing groups are replaced.

sudo apt update refreshes the package list and sudo apt install <package> installs software. Installing without updating first can fail with "package cannot be located".

Vim

Vim is a terminal text editor with modes: in command mode, keys act as commands; i enters insert mode to type; Esc returns to command mode.

:w save · :q quit · :wq save and quit · :q! quit without saving · /word search · dd delete a line · u undo · Ctrl+R redo

What broke and how I fixed it
1. sudo did not fix "permission denied"

Problem: Redirecting output to a file failed, and adding sudo gave the same error.

$ sudo ls missingfile1.txt /etc &> everything1.txt
zsh: permission denied: everything1.txt

Cause: The shell creates the output file before sudo runs, and the shell runs as my normal user. sudo only applied to ls. I was also in /, a directory I do not own.

Fix: Moved back to a directory I own. To write to a protected location, sudo tee is the correct approach because the elevated command writes the file.

What I learned: sudo elevates one command, not the redirection around it.

2. A series of unrelated-looking errors

Problem: After one mistyped command, files appeared to be missing and writes were refused.

Cause: Typing a bare /etc moved me into /etc, and cd .. then took me to /. Every following command ran in the wrong directory.

Fix: pwd showed the real location, and I returned to my home directory.

What I learned: When several commands fail in ways that do not make sense, check the current directory first. The same issue came up later when cd /docker-learning/hello_flask failed because the leading / skipped /home/yusuf; the correct path was ~/docker-learning/hello_flask.

3. Errors caused by spacing

Problem: chown sarah : admins, greeting = "hello" and cd.. all failed.

Cause: The shell uses spaces to separate a command from its arguments. Extra spaces split one value into several; a missing space joins two into one.

Fix: chown sarah:admins, greeting="hello" and cd ...

What I learned: Spacing in shell commands is part of the syntax, not formatting.

4. Vim commands saved as text

Problem: wq, q! and setnumber ended up as lines inside the file.

Cause: I was in insert mode and typed the commands without a colon.

Fix: Esc to return to command mode, then :q! to discard the changes.

What I learned: Check for -- INSERT -- in the bottom-left corner before typing commands.
