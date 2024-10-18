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

