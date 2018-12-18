## Section 14

1. Linux distros use different packaging systems and as a general rule, a package intended for one
distro is not compatible with another distro.

2. Most distros fall into one of two camps - Debian ".deb" and Red Hat ".rpm". There are exceptions such as Gentoo, Slackware and Arch.

3. The basic unit of software in a packaging system is the package file, which is a compressed collection of files and data files that supports the program. In addition to the files to be installed, the package file also has metadata about the package, and pre- and post-installation scripts that perform configuration tasks.

4. Package files are created by a person known as package maintainer. The package maintainer gets the software in source code from the upstream provider (the author of the program), compiles it, and creates the package metadata and any necessary installation scripts.

5. Packages are made available in central repositories that may contain thousands of packages.

6. A distro may have multiple repos (e.g. testing, development)

7. Package management system usually consist of two types of tools: low-level tools which handle taks such as installing and removing packages (e.g. dpkg and rpm) and high-level tools that perform metadata searching and dependency resolution (e.g. apt-get, yum).

 
### Section 16 - Networking

1. ping - send ICMP ECHO_REQUEST to specific host

2. traceroute - displays a listing of all of the "hops" network traffic takes
to get from local system to specific host.

3. ip - multi-purpose network configuration tool; replaces "ipconfig"

4. netstat - used to examine various network settings and statistics

5. ftp - file transfer protocol; not secure because it's not encrypted. As a result,
all ftp done over the internet is done by anonymous servers (anonymous username and meaningless password)

6. lftp - better ftp

7. wget - for downloading files

8. ssh - (secure shell) authenticates remote host and encrypts communication; SSH server listens
for incoming connections on port 22, while an SSH client is used on the local system to communicate
with the remote server

9. scp - secure copy

10. sftp - secure file transfer protocol


### Section 17 - Searching For Files

1. locate - performs rapid database search of pathnames, and then outputs every file name that matches a given string. Locale database updates via a cron job once a day.

2. find - find files 

3. xargs - accepts input from standard input and convert it into an argument list for a specified command


## Section 18 - Archiving and backup

1. gzip - used to compress files. Compressed files have gz extension. (foo.txt -> foo.txt.gz)

2. gunzip - uncompresses files (foo.txt.gz -> foo.txt)

3. bzip2 - compresses files using another compression algorithm; achieves a higher level of compression at the cost of compression speed (foo.txt -> foo.txt.bz2)

4. bunzip2 - uncompresses bz2 files

5. Archiving is the process of gathering up many files and bundling them together into a single large file

6. tar - tape archive (.tar - "plain" tar achive & .tgz - gzipped archive)

7. zip - both compression tool and archiver

8. unzip - decompresses and extracts .zip files


### Section 19 -  Regular Expression

1. grep - global regular expression print

2. Metacharacters are ^ $ . [ ] { } - ? * + ( ) | \

3. '.' is the any character

4. Caret ('^') and dollar ('$') are anchors in regex. This means that they cause the match to occur
if the regex is found in the beginning ('^') or end ('$') of the line.

5. [] are used to match a single character from a set (e.g. '[bg]zip' matches bzip and gzip)
   When '^' is used in a bracket, it means negation. Likewise, dash ('-') means range.

6. There are basic and extended regex in UNIX.

7. In basic, ^ $ . [ ]* are metacharacters.

8. In extended, ( ) { } ? + | were added as metacharacters.

9. POSIX - stands for portable operating system interface (Yes, there's no X)

10. Add -E option to use extended regex
 
11. '|' is alteration (aka OR) (echo "AAA" | grep -E 'AAA|BBB|CCC' returns AAA)

12. () separates alternation. (e.g. '^(bz|gz|zip)' vs ^bz|gz|zip)

13. '?' means match an element 0 or 1 times

14. '*' means match an element 0 or more times

15. '+' means match an element 1 or more times

16. {} means match an element a specific number of times

