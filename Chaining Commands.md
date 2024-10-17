### CHAINING COMMANDS

## CHALLENGE 1: CHAINING WITH SEMI COLON

- DOCUMENTATION:
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines

- THOUGHT PROCESS:
In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon

- SOLUTION:
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{4banYDHON5XHN-w0dQbpzfB8LHQ.dVTN4QDLyMDO0czW}
```

## CHALLENGE 2: FIRST SHELL SCRIPT

- DOCUMENTATION:
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):
```
echo COLLEGE > pwn
cat pwn
```
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.

- THOUGHT PROCESS:
