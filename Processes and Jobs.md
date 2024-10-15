# Processes and Jobs 

## CHALLENGE 1: LISTING PROCESSES
- DOCUMENTATION:  
  This challenge talks about the usability of the "ps" command, which is used to list all the functions that are currently running in the terminal.
  It also introduced 2 arguments -ef and aux which are used to get the "full" output of this function
- THOUGHT PROCESS:  
  We had to use these arguments to find the /challenge/run folder as it hase been renamed to something else.
- SOLUTION:  
I ran this code,
```
hacker@processes~listing-processes:~$ ps -ef
```
and I recieved this output,
```
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 11:51 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 11:51 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 11:51 ?        00:00:00 /challenge/26501-run-31752
root          72      68  0 11:51 ?        00:00:00 sleep 6h
hacker        81       1  1 11:52 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/o
hacker       102      81  7 11:52 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/o
hacker       143     102  4 11:52 ?        00:00:03 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code
hacker       161     102  1 11:52 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/l
hacker       221     161  0 11:52 pts/1    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/out/vs/workbench/contrib/te
hacker       572     221  0 11:53 pts/1    00:00:00 ps -ef
```
IN this output, the PID 68 stood out, as it had the /challenge directory opened,

so then i ran this,
```
hacker@processes~listing-processes:~$ /challenge/26501-run-31752
```
and recieved the flag
```
Yahaha, you found me! Here is your flag:
pwn.college{AlERRHNv9qhTXbwj9l0DB27NYG-.dhzM4QDLyMDO0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
## CHALLENGE 2: KILLING PROCESSES
- DOCUMENTATION:
  You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of seconds specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:
- THOUGHT PROCESS:
  WE had to kill the dont_run program which was working in the background so that we can run /challnge/run,
- SOLUTION:
  I ran this program,
```
hacker@processes~killing-processes:~$ ps -ef | grep dont_run
hacker        73      71  0 13:37 ?        00:00:00 /challenge/dont_run
hacker      1249     229  0 13:42 pts/1    00:00:00 grep --color=auto dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{AnTQmSRWoEeCAbixdcOrivxXELN.dJDN4QDLyMDO0czW}
```
## CHALLENGE 3:  
- DOCUMENTATION:
  You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

- THOUGHT PROCESS:
  /challenge/run will refuse to give you the flag until you interrupt it
- SOLUTION:
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{c4mks0XQnDaw3NB5B3V_XVT2s9k.dNDN4QDLyMDO0czW}
hacker@processes~interrupting-processes:~$ 
```

## CHALLENGE 4:  
- DOCUMENTATION:
  You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes
- THOUGHT PROCESS:
  Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended
- SOLUTION:
```
  hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         298     213  0 14:05 pts/1    00:00:00 bash /challenge/run
root         300     298  0 14:05 pts/1    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         298     213  0 14:05 pts/1    00:00:00 bash /challenge/run
root         355     213  0 14:05 pts/1    00:00:00 bash /challenge/run
root         357     355  0 14:05 pts/1    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{AthjeWYt0OauasgTb1tr46pcBEa.dVDN4QDLyMDO0czW}
```

## CHALLENGE 5:  
- DOCUMENTATION:
  Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal
- THOUGHT PROCESS:
   This challenge's run needs you to suspend it, then resume it
- SOLUTION:
```bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg 
/challenge/run
I'm back! Here's your flag:
pwn.college{kjXNWz1ZMcxxrfmszhzFp4vcgUX.dZDN4QDLyMDO0czW}
Don't forget to press Enter to quit me!

Goodbye!
```
## CHALLENGE 6: BACKGROUNDING PROCESSES
- DOCUMENTATION:
You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime

- THOUGHT PROCESS:
Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background

- SOLUTION:
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         318 S+   bash /challenge/run
root         320 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         318 S    bash /challenge/run
root         388 S    sleep 6h
root         474 S+   bash /challenge/run
root         476 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sjgE-Iu758Ay8vui_qLxassmUkh.ddDN4QDLyMDO0czW}
```

## CHALLENGE 7: FOREGROUNDING PROCESSES
- DOCUMENTATION:
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that

- SOLUTION:
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{Q1J5_EkwBm-TRKfTjDRblrlUfr3.dhDN4QDLyMDO0czW}
```

## CHALLENGE 8: STARTING BACKGROUNDED PROCESSES
- DOCUMENTATION:
Of course, you don't have to suspend processes to background them: you can start the backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so

- THOUGHT PROCESS:
  Launch /challenge/run backgrounded for the flag

- SOLUTION:
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 435



hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{QyKLcM_UIj43naXABel6KI6DpHL.dlDN4QDLyMDO0czW}
```
  
## CHALLENGE 9: PROCESS EXIT CODES
- DOCUMENTATION:
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates, This can be used by the shell, or the user of the shell (that's you!) to check if the process succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the first place).

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!)
- THOUGHT PROCESS:
  In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument
- SOLUTION:
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
120
hacker@processes~process-exit-codes:~$ /challenge/submit-code 120
CORRECT! Here is your flag:
pwn.college{gTNC-i1PX3GjLZGsEYYsXlbzoH8.dljN4UDLyMDO0czW}
hacker@processes~process-exit-codes:~$
```
