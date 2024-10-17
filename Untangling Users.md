### UNTANGLING USERS

## CHALLENGE 1: BECOMING ROOT WITH SU

- DOCUMENTATION:
In the previous level, you used the /challenge/getroot program to become the root user. Becoming root is a fairly common action that Linux users take, and your typical Linux installation obviously does not have /challenge/getroot. Instead, there are two utilities used for this purposes: su and sudo.

In this challenge, we will cover the older one, su (the switch user command). This is not typically used to elevate to root access anymore, but it is an elegant utility from a more civilized time, and we'll cover it first.

su is a setuid binary

- THOUGHT PROCESS:
This challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag

- SOLUTION:
```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{UelxKQjxusnFtvWR1SiHIK7UzYo.dVTN0UDLyMDO0czW}
```

## CHALLENGE 2: OTHER USERS WITH SU
- DOCUMENTATION:
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root

- THOUGHT PROCESS:
In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me.

- SOLUTION:
```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{w2FT4fDhvlZBUNZ7j7nAYv7_cIF.dZTN0UDLyMDO0czW}
```

- THOUGHT CCC
