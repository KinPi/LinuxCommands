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