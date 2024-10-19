### PONDERING POSITIONS

## CHALLENGE 1: THE PATH VARIABLE
- DOCUEMENTAION:
It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable, called PATH,
 that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. If you blank out the variable, things go badly

- THOUGHT PROCESS:
you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command,
the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command
- SOLUTION:
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{wQ00NV105NWbzxNaP3sEfQJNGQ-.dZzNwUDLyMDO0czW}
```

## CHALLENGE 2: SETTING PATH

- DOCUMENTATION:
Let's explore how we would, for example, add a new directory of programs to our command repertoire.
Recall that PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path
- THOUGHT PROCESS:
This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory

- SOLUTION:
```
```

## CHALLENGE 3: ADDING PATH
- DOCUMENTATION:
What we see here, of course, is the hacker making the shell more useful for themselves by bringing their own commands to the party. Over time, you might amass your own elegant tools. Let's start with win

- THOUGHT PROCESS:
Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

- SOLUTION:
```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ echo $PATH
/home/hacker:/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ win
cat: /flag: Permission denied
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{wCicM4M8YS3WJIb_EJ4LNjw1Y_Z.dZzNyUDLyMDO0czW}
```

## CHALLENGE 4: HIJACKING COMMANDS
- DOCUMENTATION:
Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you

- THOUGHT PROCESS:
You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it

- SOLUTION:
```
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ chmod a+x /home/hacker/rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{UswDDVFxyCpYgEdTzE3_nrSXBcy.ddzNyUDLyMDO0czW}
```
