## Section 11

1. Environment - a body of information that shell stores during your session

2. printenv - shows what is stored in environment varibles

3. set - shows both shell and environment variables

4. "alias" - shows list of alias

5. When we log on to the system, bash starts and reads a series of configuration scripts
   called startup files, which define the default environment shared for all users.
   This is followed by more startup files in your home directory that define your personal
   environment.

6. There are two types of shell - login (prompted for username and password) and non-login (
   terminal session in GUI).

7. login shell reads startup files such as "/etc/profile", "~/.bash_profile", "~/.bash_login" and
   "~/.profile".

8. Non-login shell reads "/etc/bash.bashrc" and "~/.bashrc".

9. Non-login shell also inherits the environment of their parent process, usually a login shell.

10. export command tells shell to make the contents of an environment variable available to 
    child processes of this shell.

11. You need to use the source command to activate new configuration changes because the startup files are only read during the beginning of a session.




