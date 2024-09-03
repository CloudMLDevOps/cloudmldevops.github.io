# Linux Questions and Answers

{::options parse_block_html="true" /}

<details><summary markdown="span"><b>Give some examples of Linux distribution. What is your favorite distro and why?</b></summary>

- Red Hat Enterprise Linux
- Fedora
- CentOS
- Debian
- Ubuntu
- Mint
- SUSE Linux Enterprise Server (SLES)
- SUSE Linux Enterprise Desktop (SLED)
- Slackware
- Arch
- Kali
- Backbox

My favorite Linux distribution:

- **Arch Linux**, which offers a nice minimalist base system on which one can build a custom operating system. The beauty of it too is that it has the Arch User Repository (AUR), which when combined with its official binary repositories allows it to probably have the largest repositories of any distribution. Its packaging process is also very simple, which means if one wants a package not in its official repositories or the AUR, it should be easy to make it for oneself.
- **Linux Mint**, which is also built from Ubuntu LTS releases, but features editions featuring a few different desktop environments, including Cinnamon, MATE and Xfce. Mint is quite polished and its aesthetics are rather appealing, I especially like its new icon theme, although I do quite dislike its GTK+ theme (too bland to my taste). I’ve also found a bug in its latest release Mint 19, that is getting quite irritating as I asked for with it over a fortnight ago on their forums and I have received no replies so far and it is a bug that makes my life on it more difficult.
- **Kali Linux**, is a Debian-based Linux distribution aimed at advanced Penetration Testing and Security Auditing. Kali contains several hundred tools which are geared towards various information security tasks, such as Penetration Testing, Security research, Computer Forensics and Reverse Engineering.

Useful resources:

- [List of Linux distributions](https://en.wikipedia.org/wiki/List_of_Linux_distributions)
- [What is your favorite Linux distro and why?](https://www.quora.com/What-is-your-favorite-Linux-distro-and-why)

</details>

<details>
<summary markdown="span"><b>What are the differences between Unix, Linux, BSD, and GNU?</b></summary><br>

**GNU** isn't really an OS. It's more of a set of rules or philosophies that govern free software, that at the same time gave birth to a bunch of tools while trying to create an OS. So **GNU** tools are basically open versions of tools that already existed, but were reimplemented to conform to principals of open software. **GNU/Linux** is a mesh of those tools and the **Linux kernel** to form a complete OS, but there are other GNUs, e.g. **GNU/Hurd**.

**Unix** and **BSD** are "older" implementations of POSIX that are various levels of "closed source". **Unix** is usually totally closed source, but there are as many flavors of **Unix** as there are **Linux** (if not more). **BSD** is not usually considered "open", but it was considered to be very open when it was released. Its licensing also allowed for commercial use with far fewer restrictions than the more "open" licenses of the time allowed.

**Linux** is the newest of the four. Strictly speaking, it's "just a kernel"; however, in general, it's thought of as a full OS when combined with GNU Tools and several other core components.

The main governing differences between these are their ideals. **Unix**, **Linux**, and **BSD** have different ideals that they implement. They are all POSIX, and are all basically interchangeable. They do solve some of the same problems in different ways. So other then ideals and how they choose to implement POSIX standards, there is little difference.

For more info I suggest your read a brief article on the creation of **GNU**, **OSS**, **Linux**, **BSD**, and **UNIX**. They will be slanted towards their individual ideas, but those articles should give you a better idea of the differences.

Useful resources:

- [What is the difference between Unix, Linux, BSD and GNU? (original)](https://unix.stackexchange.com/questions/104714/what-is-the-difference-between-unix-linux-bsd-and-gnu)
- [The Great Debate: Is it Linux or GNU/Linux?](https://www.howtogeek.com/139287/the-great-debate-is-it-linux-or-gnulinux/)

</details>

<details>
<summary markdown="span"><b>What is a CLI? Tell me about your favorite CLI tools, tips, and hacks.</b></summary><br>

**CLI** is an acronym for Command Line Interface or Command Language Interpreter. The command line is one of the most powerful ways to control your system/computer.

In Unix like systems, **CLI** is the interface by which a user can type commands for the system to execute. The **CLI** is very powerful, but is not very error-tolerant.

The **CLI** allows you to do manipulations with your system’s internals and with code in a much more fine-tuned way. It offers greater flexibility and control than a GUI regardless of what OS is used. Many programs that you might want to use in your software that are hosted on say Github also require running some commands on the **CLI** in order to get them running.

**My favorite tools**

- `screen` - free terminal multiplexer, I can start a session and My terminals will be saved even when you connection is lost, so you can resume later or from home
- `ssh` - the most valuable over-all command to learn, I can use it to do some amazing things:
  * mount a file system over the internet with `sshfs`
  * forward commands: runs against a `rsync` server with no `rsync` deamon by starting one itself via ssh
  * run in batch files: I can redirect the output from the remote command and use it within local batch file
- `vi/vim` - is the most popular and powerful text editor, it's universal, it's work very fast, even on large files
- `bash-completion` - contains a number of predefined completion rules for shell

**Tips & Hacks**

- searches the command history with `CTRL + R`
- `popd/pushd` and other shell builtins which allow you manipulate the directory stack
- editing keyboard shortcuts like a `CTRL + U`, `CTRL + E`
- combinations will be auto-expanded:
  * `!*` - all arguments of last command
  * `!!` - the whole of last command
  * `!ssh` - last command starting with ssh

Useful resources:

- [Command Line Interface Definition](http://www.linfo.org/command_line_interface.html)
- [What is your single most favorite command-line trick using Bash?](https://stackoverflow.com/questions/68372/what-is-your-single-most-favorite-command-line-trick-using-bash/69716)
- [What are your favorite command line features or tricks?](https://unix.stackexchange.com/questions/6/what-are-your-favorite-command-line-features-or-tricks)

</details>

<details>
<summary markdown="span"><b>What is your favorite shell and why?</b></summary><br>

**BASH** is my favorite. It’s really a preferential kind of thing, where I love the syntax and it just "clicks" for me. The input/output redirection syntax (`>>`, `<< 2>&1`, `2>`, `1>`, etc) is similar to C++ which makes it easier for me to recognize.

I also like the **ZSH** shell, because is much more customizable than **BASH**. It has the Oh-My-Zsh framework, powerful context based tab completion, pattern matching/globbing on steroids, loadable modules and more.

Useful resources:

- [Comparison of command shells](https://en.wikipedia.org/wiki/Comparison_of_command_shells)

</details>

<details>
<summary markdown="span"><b>How do you get help on the command line? ***</b></summary><br>

- `man` [commandname] can be used to see a description of a command (ex.: `man less`, `man cat`)

- `-h` or `--help` some programs will implement printing instructions when passed this parameter (ex.: `python -h` and `python --help`)

</details>

<details>
<summary markdown="span"><b>Your first 5 commands on a *nix server after login.</b></summary><br>

- `w` - a lot of great information in there with the server uptime
- `top` - you can see all running processes, then order them by CPU, memory utilization and more
- `netstat` - to know on what port and IP your server is listening on and what processes are using those
- `df` - reports the amount of available disk space being used by file systems
- `history` - tell you what was previously run by the user you are currently connected to

Useful resources:

- [First 5 Commands When I Connect on a Linux Server (original)](https://www.linux.com/blog/first-5-commands-when-i-connect-linux-server)

</details>

<details>
<summary markdown="span"><b>What do the fields in <code>ls -al</code> output mean?</b></summary><br>

In the order of output:

```bash
-rwxrw-r--    1    root   root 2048    Jan 13 07:11 db.dump
```

- file permissions,
- number of links,
- owner name,
- owner group,
- file size,
- time of last modification,
- file/directory name

File permissions is displayed as following:

- first character is `-` or `l` or `d`, `d` indicates a directory, a `-` represents a file, `l` is a symlink (or soft link) - special type of file
- three sets of characters, three times, indicating permissions for owner, group and other:
  - `r` = readable
  - `w` = writable
  - `x` = executable

In your example `-rwxrw-r--`, this means the line displayed is:

- a regular file (displayed as `-`)
- readable, writable and executable by owner (`rwx`)
- readable, writable, but not executable by group (`rw-`)
- readable but not writable or executable by other (`r--`)

Useful resources:

- [What do the fields in ls -al output mean? (original)](https://unix.stackexchange.com/questions/103114/what-do-the-fields-in-ls-al-output-mean)

</details>

<details>
<summary markdown="span"><b>How do you get a list of logged-in users?</b></summary><br>

For a summary of logged-in users, including each login of a username, the terminal users are attached to, the date/time they logged in, and possibly the computer from which they are making the connection, enter:

```bash
# It uses /var/run/utmp and /var/log/wtmp files to get the details.
who
```

For extensive information, including username, terminal, IP number of the source computer, the time the login began, any idle time, process CPU cycles, job CPU cycles, and the currently running command, enter:

```bash
# It uses /var/run/utmp, and their processes /proc.
w
```

Also important for displays a list of last logged in users, enter:

```bash
# It uses /var/log/wtmp.
last
```

Useful resources:

- [4 Ways to Identify Who is Logged-In on Your Linux System](https://www.thegeekstuff.com/2009/03/4-ways-to-identify-who-is-logged-in-on-your-linux-system/)

</details>

<details>
<summary markdown="span"><b>What is the advantage of executing the running processes in the background? How can you do that?</b></summary><br>

The most significant advantage of executing the running process in the background is that you can do any other task simultaneously while other processes are running in the background. So, more processes can be completed in the background while you are working on different processes. It can be achieved by adding a special character `&` at the end of the command.

Generally applications that take too long to execute and doesn't require user interaction are sent to background so that we can continue our work in terminal.

For example if you want to download something in background, you can:

```bash
wget https://url-to-download.com/download.tar.gz &
```

When you run the above command you get the following output:

```bash
[1] 2203
```

Here 1 is the serial number of job and 2203 is PID of the job.

You can see the jobs running in background using the following command:

```bash
jobs
```

When you execute job in background it give you a PID of job, you can kill the job running in background using the following command:

```bash
kill PID
```

Replace the PID with the PID of the job. If you have only one job running you can bring it to foreground using:

```bash
fg
```

If you have multiple jobs running in background you can bring any job in foreground using:

```bash
fg %#
```

Replace the `#` with serial number of the job.

Useful resources:

- [How do I run a Unix process in the background?](https://kb.iu.edu/d/afnz)
- [Job Control Commands](http://tldp.org/LDP/abs/html/x9644.html)
- [What is/are the advantage(s) of running applications in background?](https://unix.stackexchange.com/questions/162186/what-is-are-the-advantages-of-running-applications-in-backgound)

</details>

<details>
<summary markdown="span"><b>Before you can manage processes, you must be able to identify them. Which tools will you use? ***</b></summary><br>

To be completed.

</details>

<details>
<summary markdown="span"><b>Running the command as root user. It is a good or bad practices?</b></summary><br>

Running (everything) as root is bad because:

- **Stupidity**: nothing prevents you from making a careless mistake. If you try to change the system in any potentially harmful way, you need to use sudo, which ensures a pause (while you're entering the password) to ensure that you aren't about to make a mistake.

- **Security**: harder to hack if you don't know the admin user's login account. root means you already have one half of the working set of admin credentials.

- **You don't really need it**: if you need to run several commands as root, and you're annoyed by having to enter your password several times when `sudo` has expired, all you need to do is `sudo -i` and you are now root. Want to run some commands using pipes? Then use `sudo sh -c "command1 | command2"`.

- **You can always use it in the recovery console**: the recovery console allows you to recover from a major mistake, or fix a problem caused by an app (which you still had to run as `sudo`). Ubuntu doesn't have a password for the root account in this case, but you can search online for changing that - this will make it harder for anyone that has physical access to your box to be able to do harm.

Useful resources:

- [Why is it bad to log in as root? (original)](https://askubuntu.com/questions/16178/why-is-it-bad-to-log-in-as-root)
- [What's wrong with always being root?](https://serverfault.com/questions/57962/whats-wrong-with-always-being-root)
- [Why you should avoid running applications as root](https://bencane.com/2012/02/20/why-you-should-avoid-running-applications-as-root/)

</details>

<details>
<summary markdown="span"><b>How to check memory stats and CPU stats?</b></summary><br>

You'd use `top/htop` for both. Using `free` and `vmstat` command we can display the physical and virtual memory statistics respectively. With the help of `sar` command we see the CPU utilization & other stats (but `sar` isn't even installed in most systems).

Useful resources:

- [How do I Find Out Linux CPU Utilization?](https://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)
- [16 Linux server monitoring commands you really need to know](https://www.hpe.com/us/en/insights/articles/16-linux-server-monitoring-commands-you-really-need-to-know-1703.html)

</details>

<details>
<summary markdown="span"><b>What is load average?</b></summary><br>

Linux **load averages** are **system load averages** that show the running thread (task) demand on the system as an average number of running plus waiting threads. This measures demand, which can be greater than what the system is currently processing. Most tools show three averages, for 1, 5, and 15 minutes.

These 3 numbers are not the numbers for the different CPUs. These numbers are mean values of the load number for a given period of time (of the last 1, 5 and 15 minutes).

**Load average** is usually described as "average length of run queue". So few CPU-consuming processes or threads can raise **load average** above 1. There is no problem if **load average** is less than total number of CPU cores. But if it gets higher than number of CPUs, this means some threads/processes will stay in queue, ready to run, but waiting for free CPU.

It is meant to give you an idea of the state of the system, averaged over several periods of time. Since it is averaged, it takes time for it to go back to 0 after a heavy load was placed on the system.

Some interpretations:

- if the averages are 0.0, then your system is idle
- if the 1 minute average is higher than the 5 or 15 minute averages, then load is increasing
- if the 1 minute average is lower than the 5 or 15 minute averages, then load is decreasing
- if they are higher than your CPU count, then you might have a performance problem (it depends)

Useful resources:

- [Linux Load Averages: Solving the Mystery (original)](http://www.brendangregg.com/blog/2017-08-08/linux-load-averages.html)
- [Linux load average - the definitive summary](http://blog.angulosolido.pt/2015/04/linux-load-average-definitive-summary.html)
- [How CPU load averages work (and using them to triage webserver performance!)](https://jvns.ca/blog/2016/02/07/cpu-load-averages/)

</details>

<details>
<summary markdown="span"><b>Where is my password stored on Linux/Unix?</b></summary><br>

The passwords are not stored anywhere on the system at all. What is stored in `/etc/shadow` are so called hashes of the passwords.

A hash of some text is created by performing a so called one way function on the text (password), thus creating a string to check against. By design it is "impossible" (computationally infeasible) to reverse that process.

Older Unix variants stored the encrypted passwords in `/etc/passwd` along with other information about each account.

Newer ones simply have a `*` in the relevant field in `/etc/passwd` and use `/etc/shadow` to store the password, in part to ensure nobody gets read access to the passwords when they only need the other stuff (`shadow` is usually protected more strongly than `passwd`).

For more info consult `man crypt`, `man shadow`, `man passwd`.

Useful resources:

- [Where is my password stored on Linux?](https://security.stackexchange.com/questions/37050/where-is-my-password-stored-on-linux)
- [Where are the passwords of the users located in Linux?](https://www.cyberciti.biz/faq/where-are-the-passwords-of-the-users-located-in-linux/)
- [Linux Password & Shadow File Formats](https://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html)

</details>

<details>
<summary markdown="span"><b>How to recursively change permissions for all directories except files and for all files except directories?</b></summary><br>

To change all the directories e.g. to **755** (`drwxr-xr-x`):

```bash
find /opt/data -type d -exec chmod 755 {} \;
```

To change all the files e.g. to **644** (`-rw-r--r--`):

```bash
find /opt/data -type f -exec chmod 644 {} \;
```

Useful resources:

- [How do I set chmod for a folder and all of its subfolders and files? (original)](https://stackoverflow.com/questions/3740152/how-do-i-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files?rq=1)

</details>

<details>
<summary markdown="span"><b>Every command fails with <code>command not found</code>. How to trace the source of the error and resolve it?</b></summary><br>

It looks that at one point or another are overwriting the default `PATH` environment variable. The type of errors you have, indicates that `PATH` does not contain e.g. `/bin`, where the commands (including bash) reside.

One way to begin debugging your bash script or command would be to start a subshell with the `-x` option:

```bash
bash --login -x
```

This will show you every command, and its arguments, which is executed when starting that shell.

Also very helpful is show `PATH` variable values:

```bash
echo $PATH
```

If you run this:

```bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin
```

most commands should start working - and then you can edit `~/.bash_profile` instead of `~/.bashrc` and fix whatever is resetting `PATH` there. Default `PATH` variable values for **root** and other users is in `/etc/profile` file.

Useful resource:

- [How to correctly add a path to PATH?](https://unix.stackexchange.com/questions/26047/how-to-correctly-add-a-path-to-path)

</details>

<details>
<summary markdown="span"><b>You typing <code>CTRL + C</code> but your script still running. How do you stop it? ***</b></summary><br>

To be completed.

Useful resources:

- [How to kill a script running in terminal, without closing terminal (Ctrl + C doesn't work)? (original)](https://askubuntu.com/questions/520107/how-to-kill-a-script-running-in-terminal-without-closing-terminal-ctrl-c-doe)
- [What's the difference between ^C and ^D for Unix/Mac OS X terminal?](https://superuser.com/questions/169051/whats-the-difference-between-c-and-d-for-unix-mac-os-x-terminal)

</details>

<details>
<summary markdown="span"><b>What is <code>grep</code> command? How to match multiple strings in the same line?</b></summary><br>

The `grep` utilities are a family of Unix tools, including `egrep` and `fgrep`.

`grep` searches file patterns. If you are looking for a specific pattern in the output of another command, `grep` highlights the relevant lines. Use this grep command for searching log files, specific processes, and more.

For match multiple strings:

```bash
grep -E "string1|string2" filename
```

or

```bash
grep -e "string1" -e "string2" filename
```

Useful resources:

- [What is grep, and how do I use it? (original)](https://kb.iu.edu/d/afiy)

</details>

<details>
<summary markdown="span"><b>Explain the file content commands along with the description.</b></summary><br>

- `head`: to check the starting of a file.
- `tail`: to check the ending of the file. It is the reverse of head command.
- `cat`: used to view, create, concatenate the files.
- `more`: used to display the text in the terminal window in pager form.
- `less`: used to view the text in the backward direction and also provides single line movement.

Useful resources:

- [Viewing text files from the shell prompt](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Step_by_Step_Guide/s1-viewingtext-terminal.html)

</details>

<details>
<summary markdown="span"><b>SIGHUP, SIGINT, SIGKILL, and SIGTERM POSIX signals. Explain.</b></summary><br>

- **SIGHUP** - is sent to a process when its controlling terminal is closed. It was originally designed to notify the process of a serial line drop (a hangup). Many daemons will reload their configuration files and reopen their logfiles instead of exiting when receiving this signal.
- **SIGINT** - is sent to a process by its controlling terminal when a user wishes to interrupt the process. This is typically initiated by pressing `Ctrl+C`, but on some systems, the "delete" character or "break" key can be used.
- **SIGKILL** - is sent to a process to cause it to terminate immediately (kill). In contrast to **SIGTERM** and **SIGINT**, this signal cannot be caught or ignored, and the receiving process cannot perform any clean-up upon receiving this signal.
- **SIGTERM** - is sent to a process to request its termination. Unlike the **SIGKILL** signal, it can be caught and interpreted or ignored by the process. This allows the process to perform nice termination releasing resources and saving state if appropriate. **SIGINT** is nearly identical to **SIGTERM**.

Useful resources:

- [POSIX signals](https://dsa.cs.tsinghua.edu.cn/oj/static/unix_signal.html)
- [Introduction To Unix Signals Programming](http://titania.ctie.monash.edu.au/signals/)

</details>

<details>
<summary markdown="span"><b>What does <code>kill</code> command do?</b></summary><br>

In Unix and Unix-like operating systems, `kill` is a command used to send a signal to a process. By default, the message sent is the termination signal, which requests that the process exit. But `kill` is something of a misnomer; the signal sent may have nothing to do with process killing.

Useful resources:

- [Mastering the "Kill" Command in Linux](https://www.maketecheasier.com/kill-command-in-linux/)

</details>

<details>
<summary markdown="span"><b>What is the difference between <code>rm</code> and <code>rm -rf</code>?</b></summary><br>

`rm` only deletes the named files (and not directories). With `-rf` as you say:

- `-r`, `-R`, `--recursive` recursively deletes content of a directory, including hidden files and sub directories
- `-f`, `--force` ignore nonexistent files, never prompt

Useful resources:

- [What is the difference between `rm -r` and `rm -f`?](https://superuser.com/questions/1126206/what-is-the-difference-between-rm-r-and-rm-f)

</details>

<details>
<summary markdown="span"><b>How do I <code>grep</code> recursively? Explain on several examples. ***</b></summary>

To be completed.

</details>

<details>
<summary markdown="span"><b><code>archive.tgz</code> has ~30 GB. How do you list content of it and extract only one file?</b></summary><br>

```bash
# list of content
tar tf archive.tgz

# extract file
tar xf archive.tgz filename
```

Useful resources:

- [List the contents of a tar or tar.gz file](https://www.cyberciti.biz/faq/list-the-contents-of-a-tar-or-targz-file/)
- [How to extract specific file(s) from tar.gz](https://unix.stackexchange.com/questions/61461/how-to-extract-specific-files-from-tar-gz)

</details>

<details>
<summary markdown="span"><b>Execute combine multiple shell commands in one line.</b></summary><br>

If you want to execute each command only if the previous one succeeded, then combine them using the `&&` operator:

```bash
cd /my_folder && rm *.jar && svn co path to repo && mvn compile package install
```

If one of the commands fails, then all other commands following it won't be executed.

If you want to execute all commands regardless of whether the previous ones failed or not, separate them with semicolons:

```bash
cd /my_folder; rm *.jar; svn co path to repo; mvn compile package install
```

In your case, I think you want the first case where execution of the next command depends on the success of the previous one.

You can also put all commands in a script and execute that instead:

```bash
#! /bin/sh
cd /my_folder \
&& rm *.jar \
&& svn co path to repo \
&& mvn compile package install
```

Useful resources:

- [Execute combine multiple linux commands in one line (original)](https://stackoverflow.com/questions/13077241/execute-combine-multiple-linux-commands-in-one-line)

</details>

<details>
<summary markdown="span"><b>What symbolic representation can you pass to <code>chmod</code> to give all users execute access to a file without affecting other permissions?</b></summary><br>

```bash
chmod a+x /path/to/file
```

- `a` - for all users
- `x` - for execution permission
- `r` - for read permission
- `w` - for write permission

Useful resources:
- [How to Set File Permissions Using chmod](https://www.washington.edu/computing/unix/permissions.html)
- [What does "chmod +x your_file_name" do and how do I use it?](https://askubuntu.com/questions/443789/what-does-chmod-x-filename-do-and-how-do-i-use-it)

</details>

<details>
<summary markdown="span"><b>How can I sync two local directories?</b></summary><br>

To sync the contents of **dir1** to **dir2** on the same system, type:

```bash
rsync -av --progress --delete dir1/ dir2
```

- `-a`, `--archive` - archive mode
- `--delete` - delete extraneous files from dest dirs
- `-v`, `--verbose` - verbose mode (increase verbosity)
- `--progress` - show progress during transfer

Useful resources:

- [How can I sync two local directories? (original](https://unix.stackexchange.com/questions/392536/how-can-i-sync-two-local-directories)
- [Synchronizing folders with rsync](https://www.jveweb.net/en/archives/2010/11/synchronizing-folders-with-rsync.html)

</details>

<details>
<summary markdown="span"><b>Many basic maintenance tasks require you to edit config files. Explain ways to undo the changes you make.</b></summary><br>

- manually backup of a file before editing (with brace expansion like this: `cp filename{,.orig}`)
- manual copy of the directory structure where file is stored (e.g. `cp`, `rsync` or `tar`)
- make a backup of original file in your editor (e.g. set rules in your editor configuration file)
- the best solution is to use `git` (or any other version control) to keep track of configuration files (e.g. `etckeeper` for `/etc` directory)

Useful resources:

- [Backup file with .bak before filename extension](https://unix.stackexchange.com/questions/66376/backup-file-with-bak-before-filename-extension)
- [Is it a good idea to use git for configuration file version controlling?](https://superuser.com/questions/1037211/is-it-a-good-idea-to-use-git-for-configuration-file-version-controlling)

</details>

<details>
<summary markdown="span"><b>You have to find all files larger than 20MB. How you do it?</b></summary><br>

```bash
find / -type f -size +20M
```

Useful resources:

- [How can I find files that are bigger/smaller than x bytes?](https://superuser.com/questions/204564/how-can-i-find-files-that-are-bigger-smaller-than-x-bytes)

</details>

<details>
<summary markdown="span"><b>Why do we use <code>sudo su -</code> and not just <code>sudo su</code>?</b></summary><br>

`sudo` is in most modern Linux distributions where (but not always) the root user is disabled and has no password set. Therefore you cannot switch to the root user with `su` (you can try). You have to call `sudo` with root privileges: `sudo su`.

`su` just switches the user, providing a normal shell with an environment nearly the same as with the old user.

`su -` invokes a login shell after switching the user. A login shell resets most environment variables, providing a clean base.

Useful resources:

- [su vs sudo -s vs sudo -i vs sudo bash](https://unix.stackexchange.com/questions/35338/su-vs-sudo-s-vs-sudo-i-vs-sudo-bash)
- [Why do we use su - and not just su? (original)](https://unix.stackexchange.com/questions/7013/why-do-we-use-su-and-not-just-su)

</details>

<details>
<summary markdown="span"><b>How to find files that have been modified on your system in the past 60 minutes?</b></summary><br>

```bash
find / -mmin -60 -type f
```

Useful resources:

- [Get all files modified in last 30 days in a directory (orignal)](https://stackoverflow.com/questions/23070245/get-all-files-modified-in-last-30-days-in-a-directory)

</details>

<details>
<summary markdown="span"><b>What are the main reasons for keeping old log files?</b></summary><br>

They are essential to investigate issues on the system. **Log management** is absolutely critical for IT security.

Servers, firewalls, and other IT equipment keep log files that record important events and transactions. This information can provide important clues about hostile activity affecting your network from within and without. Log data can also provide information for identifying and troubleshooting equipment problems including configuration problems and hardware failure.

It’s your server’s record of who’s come to your site, when, and exactly what they looked at. It’s incredibly detailed, showing:

- where folks came from
- what browser they were using
- exactly which files they looked at
- how long it took to load each file
- and a whole bunch of other nerdy stuff

Factors to consider:

- legal requirements for retention or destruction
- company policies for retention and destruction
- how long the logs are useful
- what questions you're hoping to answer from the logs
- how much space they take up

By collecting and analyzing logs, you can understand what transpires within your network. Each log file contains many pieces of information that can be invaluable, especially if you know how to read them and analyze them.

Useful resources:

- [How long do you keep log files?](https://serverfault.com/questions/135365/how-long-do-you-keep-log-files)

</details>

<details>
<summary markdown="span"><b>What is an incremental backup?</b></summary><br>

An incremental backup is a type of backup that only copies files that have changed since the previous backup.

Useful resources:

- [What Is Incremental Backup?](https://www.nakivo.com/blog/what-is-incremental-backup/)

</details>

<details>
<summary markdown="span"><b>What is RAID? What is RAID0, RAID1, RAID5, RAID6, RAID10? </b></summary><br>

A **RAID** (Redundant Array of Inexpensive Disks) is a technology that is used to increase the performance and/or reliability of data storage.

- **RAID0**: Also known as disk **striping**, is a technique that breaks up a file and spreads the data across all the disk drives in a RAID group. There are no safeguards against failure
- **RAID1**: A popular disk subsystem that increases safety by writing the same data on two drives. Called "**mirroring**," RAID 1 does not increase write performance, but read performance may equal up to the sum of each disks' performance. However, if one drive fails, the second drive is used, and the failed drive is manually replaced. After replacement, the RAID controller duplicates the contents of the working drive onto the new one
- **RAID5**: It is disk subsystem that increases safety by computing parity data and increasing speed by interleaving data across three or more drives (**striping**). Upon failure of a single drive, subsequent reads can be calculated from the distributed parity such that no data is lost
- **RAID6**: RAID 6 extends RAID 5 by adding another parity block. It requires a minimum of four disks and can continue to execute read and write of any two concurrent disk failures. RAID 6 does not have a performance penalty for read operations, but it does have a performance penalty on write operations because of the overhead associated with parity calculations
- **RAID10**: Also known as **RAID 1+0**, is a RAID configuration that combines disk mirroring and disk striping to protect data. It requires a minimum of four disks, and stripes data across mirrored pairs. As long as one disk in each mirrored pair is functional, data can be retrieved. If two disks in the same mirrored pair fail, all data will be lost because there is no parity in the striped sets

Useful resources:

- [RAID](https://www.prepressure.com/library/technology/raid)

</details>

<details>
<summary markdown="span"><b>How is a user’s default group determined? How would you change it? </b></summary><br>

```bash
useradd -m -g initial_group username
```

`-g/--gid`: defines the group name or number of the user's initial login group. If specified, the group name must exist; if a group number is provided, it must refer to an already existing group.

If not specified, the behaviour of useradd will depend on the `USERGROUPS_ENAB` variable contained in `/etc/login.defs`. The default behaviour (`USERGROUPS_ENAB yes`) is to create a group with the same name as the username, with **GID** equal to **UID**.

Useful resources:

- [How can I change a user's default group in Linux?](https://unix.stackexchange.com/questions/26675/how-can-i-change-a-users-default-group-in-linux)

</details>

<details>
<summary markdown="span"><b>What is your best command line text editor for daily working and scripting? ***</b></summary><br>

To be completed.

</details>

<details>
<summary markdown="span"><b>Why would you want to mount servers in a rack?</b></summary><br>

- Protecting Hardware
- Proper Cooling
- Organized Workspace
- Better Power Management
- Cleaner Environment

Useful resources:

- [5 Reasons to Rackmount Your PC](https://www.racksolutions.com/news/custom-projects/5-reasons-to-rackmount-pc/)

</details>

<details>
<summary markdown="span"><b>How to change permissions of the file in linux?</b></summary><br>

The `chmod` command is used to change permissions of files and directories. It supports two modes of operation: symbolic mode and octal mode.

1. Symbolic Mode:
   - Syntax: `chmod [options] [permissions] file(s)`

   - Examples:
     - Grant read and write permissions to the owner: `chmod u+rw file.txt`
     - Revoke execute permission from the group: `chmod g-x script.sh`
     - Add read and execute permissions to others: `chmod o+rx program`
     - Combined permissions: `chmod u=rw,go=r file.txt`

2. Octal Mode:
   - Syntax: `chmod [options] [mode] file(s)`

   - Examples:
     - Set read, write, and execute permissions for owner, group, and others: `chmod 755 script.sh`
     - Restrict permissions to the owner only: `chmod 700 private.txt`
     - Grant full permissions to everyone: `chmod 777 public_dir`

</details>

<details>
<summary markdown="span"><b>How to change owner of the file in linux?</b></summary><br>

The `chown` command is used to change the ownership of files and directories.

- Syntax: `chown [options] owner:group file(s)`

- Examples:
  - Change the owner and group of a file: `chown john:users file.txt`
  - Recursively change ownership for a directory and its contents: `chown -R alice:staff project_dir`

</details>

<details>
<summary markdown="span"><b>How to change group ownership of the file in linux?</b></summary><br>

The `chgrp` command is used to change the group ownership of files and directories.

- Syntax: `chgrp [options] group file(s)`

- Examples:
  - Change the group of a file: `chgrp developers script.sh`
  - Recursively change group ownership for a directory and its contents: `chgrp -R team project_dir`

</details>

<details>
<summary markdown="span"><b>What are the different Linux Directory Structure?</b></summary><br>

The folder structure in Ubuntu Linux follows the Filesystem Hierarchy Standard (FHS), which is a standard for organizing the files and directories on a Unix-like operating system. Here is an overview of the main directories you will typically find in Ubuntu:

- **/bin**: Contains essential command-line executable files (binaries) that are available to all users.

- **/boot**: Contains files related to the boot process, including the Linux kernel, initial ramdisk (initrd), and bootloader configuration.

- **/dev**: Contains device files that represent and allow access to various hardware devices on the system.

- **/etc**: Contains system-wide configuration files for various applications and services.

- **/home**: The home directories for individual users. Each user typically has a subdirectory here to store their personal files and settings.

- **/lib** and **/lib64**: These directories contain shared libraries needed by the system and applications. The "lib64" directory is present on 64-bit systems.

- **/media**: Mount point for removable media devices such as USB drives or optical discs.

- **/mnt**: A general-purpose mount point for temporarily mounting filesystems.

- **/opt**: Contains optional software packages installed on the system. Applications installed here are often self-contained in their own directories.

- **/proc**: A virtual filesystem that provides information about processes and system status. It is used by many system utilities to obtain runtime information.

- **/root**: The home directory for the root user, the administrative superuser.

- **/run**: A temporary filesystem that contains runtime data for various system services. It is cleared on each reboot.

- **/sbin**: Contains system binaries (executable files) that are primarily used by the root user for system administration tasks.

- **/srv**: Contains data for services provided by the system.

- **/sys**: A virtual filesystem that exposes kernel-related information and configuration.

- **/tmp**: A directory for temporary files created by applications and users. Its contents are typically cleared on each reboot.

- **/usr**: Contains user-related programs, libraries, documentation, and shared resources. It has subdirectories such as /usr/bin for user binaries, /usr/lib for libraries, and /usr/share for shared data.

- **/var**: Contains variable data that changes during the system's operation, such as logs, databases, and spool files.

This is a high-level overview of the Ubuntu Linux folder structure. Each directory serves a specific purpose in organizing the system's files and resources.

</details>