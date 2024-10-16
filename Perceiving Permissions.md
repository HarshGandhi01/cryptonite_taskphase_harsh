### Perceiving Permissions

## CHALLENGE 1: CHANGING FILE OWNERSHIP
- DOCUMENTATION:
  Every file in Linux is owned by a user on the system. Most often, in your day-to-day life, that user is the user you log in as every day.

On a shared system (such as in a computer lab), there might be many people with different user accounts, all with their own files in their own home directories. But even on a non-shared system (such as your personal PC), Linux still has many "service" user accounts for different tasks.

The two most important user accounts are:

Your user account! On pwn.college, this is the hacker user, regardless of what your username is.
root. This is the administrative account and, in most security situations, the ultimate prize. 
- THOUGHT PROCESS:
  I made it so that you can use chown to your heart's content as the hacker user (again, typically, this requires you to be root). Use this power wisely and chown away

- SOLUTION:
```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{Ey6yasmONAazEe_MEZejJ0WH1H5.dFTM2QDLyMDO0czW}
```

## CHALLENGE 2: GROUPS AND FILES
- DOCUMENTATION:
  Sharing is built into Linux's design. Files have both an owning user and group. A group can have multiple users in it, and a user can be a member of multiple groups.
  you can check what groups you are part of with the id command
- THOUGHT PROCESS:
  
