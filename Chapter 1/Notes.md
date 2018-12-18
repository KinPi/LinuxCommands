## Section 1

1. If the last character of prompt is a a pound sign ('#') rather than a dollar sign ('$'), that means that you are either logged in as the root user or you selected a terminal emulator that provides superuser privileges.

2. You can type "history" to see the command history. If you type "history -c", it will clear your history.

3. "date" displays date and time.

4. "df" displays amount of free space.

5. "free" displays amount of free memory. (Doesn't work for Mac)

6. "exit" to end a terminal session.


## Section 2

1. "cd -" changes the current working directory to the previous working directory.

2. "cd ~*user_name*" changes the current working directory to the home directory of *user_name*

3. '~' refers to home directory


## Section 3

1. In "-rw-r--r-- 1 root root  358374 2007-04-03 11:05 ubuntu Sax.ogg", the 1 refers to the number of hard links.

2. "file *filename*" prints a brief description of the file's type.

3. "less *filename*" displays the content of the file to you.
    1. Page Up or b - Scroll back one page
    2. Page Down or space  - Scroll forward one page
    3. Up Arrow - Scroll up one line
    4. Down Arrow - Scroll down one line
    5. G - Move to end of the text file
    6. 1G or g - Move to beginning of text file
    7. /*characters* - Search for next occurrence of *characters*
    8. n - Search for the next occurrence of the previous search
    9. h - Display help screen
    10. q - Quit **less**

4. Use **less** instead of **more**

5. Entries like "lrwxrwxrwx 1 root root   11 2007-08-11 07:34 libc.so.6 -> libc-2.6.so" are symbolic links(AKA soft link or symlink). The 'l' in the beginning and the two file names shows that it is a symbolic link. 

6. Symbolic links allow files to be referenced by multiple names. 

7. "Picture this scenario: A program requires the use of a shared resource of some kind con- tained in a file named “foo,” but “foo” has frequent version changes. It would be good to include the version number in the filename so the administrator or other interested party could see what version of “foo” is installed. This presents a problem. If we change the name of the shared resource, we have to track down every program that might use it and change it to look for a new resource name every time a new version of the resource is in- stalled. That doesn't sound like fun at all.
Here is where symbolic links save the day. Let's say we install version 2.6 of “foo,” which has the filename “foo-2.6” and then create a symbolic link simply called “foo” that points to “foo-2.6.” This means that when a program opens the file “foo”, it is actually opening the file “foo-2.6”. Now everybody is happy. The programs that rely on “foo” can find it and we can still see what actual version is installed. When it is time to upgrade to “foo-2.7,” we just add the file to our system, delete the symbolic link “foo” and create a new one that points to the new version. Not only does this solve the problem of the ver- sion upgrade, but it also allows us to keep both versions on our machine. Imagine that “foo-2.7” has a bug (damn those developers!) and we need to revert to the old version.
Again, we just delete the symbolic link pointing to the new version and create a new symbolic link pointing to the old version."

8. In "lrwxrwxrwx 1 root root   11 2007-08-11 07:34 libc.so.6 -> libc-2.6.so", "libc.so.6" is a symbolic link that point to "libc-2.6.so". That means that when programs search for "libc.so.6", they actually get "libc-2.6.so".


## Section 4

1. You should avoid character ranges (E.g. [a-z] or [A-Z]) because they might not work as you
   expect. You should use character classes instead. (e.g. [:alnum:], [:digit:])

2. Use "ln file link" to create a hard link.

3. Use "ln -s item link" to create a soft link.

4. Hard links are the original Unix way of creating links. Soft/symbolic links
   are more modern.

5. When creating a hard link, we create an additional directory entry for the file.
   Hard links have two important limitations - 1) it cannot reference a file outside of
   its own file system. 2) It cannot reference a directory.

6. A hard link is indistinguishable from the file itself. When a hard link is deleted,
   the link is removed but the content of the files itself continue to exist until
   all links to the file have been deleted.

7. When a symbolic link is deleted, only the link is deleted but not the file.
   If the file is deleted, then the link is broken and will point to nothing.

8. When thinking about hard links, you can imagine the file having two parts - data,
   part for the content and a name part. When creating hard links, we are creating
   new name parts that points to the same data part. The chain of disk block for the
   data part is called "inode". Each hard link refers to a specific inode containing
   the file's contents.

9. You can use "ls -il" to identify hard links with the same inode. The first field,
   consisting of a bunch of digits, is an inode number. If two items have the same
   inode number, then they are hard links of the same inode.

10. Soft links were created to overcome hard link's two limitations - cannot span
    physical devices and cannot reference directories, only files.

11. When creating soft links, you can use absolute or relative paths.


## Section 5

1. Commands are one of four things:
     1) an execute program (e.g. compiled binaries in C or a script)
     2) a command built into the shell (e.g. cd)                   
     3) shell function
     4) alias - commands that we can define ourselves, built from other commands

2. You can use "type *command*" is identify which of the four types your command belongs to.

3. Help offers documentation on built-in shell commands.

4. In help's documentation, square brackets means optional. A vertical line means mutually 
   exclusive.

5. apropos displays approximate commands

6. You can use "alias name='string'" to build your own commands.
   (e.g. alias foo='cd /usr; ls; cd -')   


## Section 6

1. Many programs produce two kinds of outputs:
      1) The output that the program was designed to produce
      2) status and error messages

2. Often, results from programs are sent to a special file called "standard output",
   stdout, and their status messages to another file called "standard error", stderr.

3. By default, stdout and stderr are linked to the screen and are not saved to disk.

4. There is also standard input, stdin, which is by defaulted, attached to the keyboard.

5. I/O redirection allows us to change where output goes, and where inputs come from.

6. '>' is the redirection operator. It will overwrite the existing output file if it exists.
   (e.g. ls -l /usr/bin > ls-output.txt)

7. Using the redirection operator with no command preceding it will truncate an existing file,
   or create a new empty file. (e.g. > ls-output.txt)

8. Use the ">>" redirection operator to append to a text file.
   (e.g. ls -l /usr/bin >> ls-output.txt)

9. To redirect standard error, we must refer to its file descriptor.
   The file descripter for standard input, output and error are 0, 1 and 2 respectively.
   (e.g. ls -l /bin/usr 2> ls-error.txt)

10. For more recent versions of bash, you can redirect output and error into the same
    file by using &>. (e.g. ls -l /bin/usr &> ls-output.txt)

11. Use "<" redirection operator for redirecting standard input.
    (e.g. cat < lazy_dog.txt) 

12. Use pipelines '|' to pipe the standard output of one command to the standard input
    of another command. (e.g. command1 | command2)

13. Difference between '>' and '|'. 
      1) Redirection connects a command with a file. (e.g. command1 > file1)
      2) Pipelines connect a command with another command (e.g. command1 | command2) 

14. uniq - report or omit repeated lines

15. wc (word count) - displays lines, words and bytes contained in files

16. grep - print lines matching a pattern (e.g. grep pattern [file...])

17. tee - reads standard input and copies it to both standard output and to one
    or more files. (e.g. ls /usr/bin | tee ls.txt | grep zip)


## Section 7

1. How wildcards get proceeded is called expansion.

2. ls -A prints list of hidden folders

3. Tilde expansion (eg. echo ~)

4. Arithemetic Expansion - $((expression))
   (e.g. echo $(($((5**2)) * 3)))

5. Brace Expansion - echo Number_{1..5} gives Number_1 Number_2 Number_3 Number_4 Number_5

6. Parameter Expansion - (e.g. echo $USER)

7. printenv gives you a list of variables.

8. Command Substitution - allows you to use the output of a command as an expansion
   (e.g. echo $(ls) Desktop Documents ls-output.txt Music Pictures Public Templates Videos)

9. You can use quoting to suppress expansions. 

10. In double quotes, special characters lose their meaning. This means that word-splitting,  pathname expansion, tilde expansion, and brace expansion are suppressed, but parameter expansion, arithmetic expansion, and command substitution are still carried out.

11. Use single quotes to suppress all expansions.


## Section 9

1. id - display user identity

2. chmod - change a file's mod

3. umask - set the default file permissions

4. su - run a shell as another user

5. sudo - execute a command as another user

6. chown - change a file's owner

7. chgrp - change a file's group ownership

8. passwd - change a user's password

9. User accounts are assigned a user Id (uid), and a primary group id (gid) and may belong to additional groups.

10. User accounts are defined in /etc/passwd. Groups are defined in /etc/group

11. chmod supports octal and symbolic notation.

12. Example for umask 0002; '1' means it gets unset
    ``` 
        Original file mode
        --- rw- rw- rw-
        Mask
        000 000 000 010
        Result
        --- rw- rw- r--
    ```
13. Su requires password of the user you are logging into.

14. Sudo requires your own password. Admins can set up a configuration file called "/etc/sudoers"
    and define specific commands that particular users are permitted to execute under an assumed identity.


## Section 10

1. Kernel launches init program.

2. init runs a series of shell scripts (located in /etc), called init scripts.
   Init scripts start system services. Init has pid = 1.

3. Many of the system services are implemented as daemon programs, programs that
   just sit in the background and do their thing without any user interface.

4. Programs can launch other programs is expressed as a process scheme as a parent
   process producing a child process.

5. "ps" shows the processes for the current terminal session.

6. TTY is short for "teletype", which refers to the controlling terminal for the process.

7. The presence of "?" in TTY column indicates no controlling terminal.

8. STAT column refers to the current state of the process. (R = running, S = sleeping)

9. "ps x" tells ps to show all of our processes regardless of what terminal (if any)
   they are controlled by

10. "ps aux" displays the processes belonging to every user.

11. Ctrl + C interrupts a process.

12. Ctrl + Z pauses a process.

13. kill command doesn't actually "kill" the process. It sends signals instead.

14. kill -9 pid causes the os to immediately terminate the process. The process will have no time
    to clean up.   