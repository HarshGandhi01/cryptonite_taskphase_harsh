# DIGESTING DOCUMENTATION #

## CHALLENGE 1: LEARNING FROM DOCUMENATTION

- DOCUMENTATION:
  The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.
The correct usage of programs depends, in a large part, in the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

- THOUGHT PROCESS:
  We had to go through the docuemntation of the challenge, to find the flag

- SOLUTION:
  So I ran this program,
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{8rRjZJ9MdMzegJMEFg4yk-QMRfj.dRjM5QDL4ETO0czW}
```

## CHALLENGE 2 : LEARNING FROM COMPLEX USAGE

- DOCUMENTATION:
  While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...
  This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

- THOUGHT PROCESS:
  The documentation for this program has been given in the documentaiton, I have to go thoguh it to find the flag

- SOLUTION:
  SO i ran this program,
```
  Connected!                                                                        
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /challenge/DESCRIPTION.md
Correct argument! Here is the /challenge/DESCRIPTION.md file:
While using most commands is straightforward, the usage of some commands can get quite complex.
For example, the arguments to commands like `sed` and `awk`, which we're definitely not getting into right now, are entire programs in an esoteric programming language!
Somewhere on the spectrum between `cd` and `awk` are commands that take arguments to their arguments...
This sounds crazy, but you've already encountered this with the `find` level in [Basic Commands](../commands).find` has a `-name` argument, and the `-name` argument itself        takes an argument specifying the name to search for.
Many other commands are analogous.
Here is this level's documentation for `/challenge/challenge`:
> Welcome to the documentation for `/challenge/challenge`! This program allows you to print arbitrary files to the terminal, when given the `--printfile` argument. The            argument to the `--printfile` argument is the path of the flag to read. For example, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` will print out the               description of the level!
Given that documentation, go get the flag!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{8hvE0OPErS00raSzAVGNmTgkxys.dVjM5QDL4ETO0czW}
```

## CHALLENGE 3: READING MANUALS

- DOCUMENTATION:
  This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

- THOUGHT PROCESS:
  WE have to go through the man man page to understand the usage of the manual page, so thta we can find the secret command to print the flag

- SOLUTION:
```
Connected!                                                                        
man hacker@man~reading-manuals:~$ man  challenge

CHALLENGE(1)                                                                     Challenge Commands                                                                                CHALLENGE(1)

NAME
   /challenge/challenge - print the flag!

SYNOPSIS
   challenge <u style="text-decoration-style:solid">OPTION</u>

DESCRIPTION
   Output the flag when called with the right arguments.

   --fortune
          read a fortune

   --version
          output version information and exit

   --wqsbhh NUM
          print the flag if NUM is 744

AUTHOR
   Written by Zardus.

REPORTING BUGS
   The repository for this dojo: &lt;https://github.com/pwncollege/linux-luminarium/&gt;

SEE ALSO
   man(1) bash-builtins(7)

pwn.college                                                                           May 2024                                                                                     CHALLENGE(1)
hacker@man~reading-manuals:~$ /challenge/challenge --wqsbhh 744
Correct usage! Your flag: pwn.college{wqSAsLbRhhKaHowR_AkjIpdLv7f.dRTM4QDL4ETO0czW}
```

## CHALLENGE 4: SEARCHING MANUALS

- DOCUMENATION:
  You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards! Find the option that will give you the flag by reading the challenge man page.

- THOUGHT PROCESS:
  I have to go through the manual to find the secret command to pring the flag, we have to use the special synatx to print the flag

- SOLITION:

  I ran the following process,
```
hacker@man~searching-manuals:~$ /challenge/challenge --jjjzt
Initializing...
Correct usage! Your flag: pwn.college{w6jJMfHXUaLZD6XYfvSVEW5k7nC.dVTM4QDLyMDO0czW}
```

## CHALLENGE 5: SEARCHING FOR MANUALS

- DOCUMENTATION:
  This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the man pages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right man page, read the man page manpage by doing: man man!

- THOUGHT PROCESS:
  In this level we have to go through the database of all the manuak pages, to find the hidden manual for the file function.

- SOLUTION:

  To complete this challenge, iI ran the following command

```
hacker@man~searching-for-manuals:~$ man man
MAN(1)                                                                                 Manual pager utils                                                                                 MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is  the  system's manual pager.  Each page argument given to man is normally the name of a program, utility or function.  The manual page associated with each of these arguments is
       then found and displayed.  A section, if provided, will direct man to look only in that section of the manual.  The default action is to search in all of the available sections  follow‐
       ing a pre-defined order (see DEFAULTS), and to show only the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional  section names include NAME, SYNOPSIS, CONFIGURATION, DESCRIPTION, OPTIONS, EXIT STATUS, RETURN VALUE, ERRORS, ENVIRONMENT, FILES, VERSIONS, CONFORMING TO, NOTES, BUGS, EX‐
       AMPLE, AUTHORS, and SEE ALSO.

       The following conventions apply to the SYNOPSIS section and can be used as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.

       Exact rendering may vary depending on the output device.  For instance, man will usually not be able to render italics when running in a terminal, and will typically use  underlined  or
       coloured text instead.

       The  command  or function illustration is a pattern that should match all possible invocations.  In some cases it is advisable to illustrate several exclusive invocations as is shown in
       the SYNOPSIS section of this manual page.

EXAMPLES
       man ls
           Display the manual page for the item (program) ls.

       man man.7
           Display the manual page for macro package man from section 7.  (This is an alternative spelling of "man 7 man".)

       man 'man(7)'
           Display the manual page for macro package man from section 7.  (This is another alternative spelling of "man 7 man".  It may be more convenient when copying and pasting cross-refer‐
           ences to manual pages.  Note that the parentheses must normally be quoted to protect them from the shell.)

       man -a intro
           Display, in succession, all of the available intro manual pages contained within the manual.  It is possible to quit between successive displays or skip any of them.

       man -t bash | lpr -Pps
           Format  the  manual page for bash into the default troff or groff format and pipe it to the printer named ps.  The default output for groff is usually PostScript.  man --help should
           advise as to which processor is bound to the -t option.

       man -l -Tdvi ./foo.1x.gz > ./foo.1x.dvi
           This command will decompress and format the nroff source manual page ./foo.1x.gz into a device independent (dvi) file.  The redirection is necessary as the -T flag causes output  to
           be directed to stdout with no pager.  The output could be viewed with a program such as xdvi or further processed into PostScript using a program such as dvips.

       man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular expression.  Print out any matches.  Equivalent to apropos printf.

       man -f smail
           Lookup the manual pages referenced by smail and print out the short descriptions of any found.  Equivalent to whatis smail.

OVERVIEW
       Many  options  are available to man in order to give as much flexibility as possible to the user.  Changes can be made to the search path, section order, output processor, and other be‐
       haviours and operations detailed below.

       If set, various environment variables are interrogated to determine the operation of man.  It is possible to set the "catch-all" variable $MANOPT to any string in command  line  format,
       with  the exception that any spaces used as part of an option's argument must be escaped (preceded by a backslash).  man will parse $MANOPT prior to parsing its own command line.  Those
       options requiring an argument will be overridden by the same options found on the command line.  To reset all of the options set in $MANOPT, -D can be specified as the  initial  command
       line option.  This will allow man to "forget" about the options specified in $MANOPT, although they must still have been valid.

       Manual  pages  are  normally stored in nroff(1) format under a directory such as /usr/share/man.  In some installations, there may also be preformatted cat pages to improve performance.
       See manpath(5) for details of where these files are stored.

       This package supports manual pages in multiple languages, controlled by your locale.  If your system did not set this up for you automatically, then you may need  to  set  $LC_MESSAGES,
       $LANG, or another system-dependent environment variable to indicate your preferred locale, usually specified in the POSIX format:

       <language>[_<territory>[.<character-set>[,<version>]]]

       If the desired page is available in your locale, it will be displayed in lieu of the standard (usually American English) page.

       If you find that the translations supplied with this package are not available in your native language and you would like to supply them, please contact the maintainer who will be coor‐
       dinating such activity.

       Individual manual pages are normally written and maintained by the maintainers of the program, function, or other topic that they document, and are not included with this  package.   If
       you find that a manual page is missing or inadequate, please report that to the maintainers of the package in question.

       For information regarding other features and extensions available with this manual pager, please read the documents supplied with the package.

DEFAULTS
       The order of sections to search may be overridden by the environment variable $MANSECT or by the SECTION directive in /etc/manpath.config.  By default it is as follows:

              1 n l 8 3 2 3posix 3pm 3perl 3am 5 4 9 6 7

       The formatted manual page is displayed using a pager.  This can be specified in a number of ways, or else will fall back to a default (see option -P for details).

       The  filters  are  deciphered by a number of means.  Firstly, the command line option -p or the environment variable $MANROFFSEQ is interrogated.  If -p was not used and the environment
       variable was not set, the initial line of the nroff file is parsed for a preprocessor string.  To contain a valid preprocessor string, the first line must resemble

       '\" <string>

       where string can be any combination of letters described by option -p below.

       If none of the above methods provide any filter information, a default set is used.

       A formatting pipeline is formed from the filters and the primary formatter (nroff or [tg]roff with -t) and executed.  Alternatively, if an executable program mandb_nfmt  (or  mandb_tfmt
       with -t) exists in the man tree root, it is executed instead.  It gets passed the manual source file, the preprocessor string, and optionally the device specified with -T or -E as argu‐
       ments.

OPTIONS
       Non-argument options that are duplicated either on the command line, in $MANOPT, or both, are not harmful.  For options that require an argument, each duplication will override the pre‐
       vious argument value.

   General options
       -C file, --config-file=file
              Use this user configuration file rather than the default of ~/.manpath.

       -d, --debug
              Print debugging information.

       -D, --default
              This  option is normally issued as the very first option and resets man's behaviour to its default.  Its use is to reset those options that may have been set in $MANOPT.  Any op‐
              tions that follow -D will have their usual effect.

       --warnings[=warnings]
              Enable warnings from groff.  This may be used to perform sanity checks on the source text of manual pages.  warnings is a comma-separated list of warning names; if it is not sup‐
              plied, the default is "mac".  See the “Warnings” node in info groff for a list of available warning names.

   Main modes of operation
       -f, --whatis
              Equivalent to whatis.  Display a short description from the manual page, if available.  See whatis(1) for details.

       -k, --apropos
              Equivalent to apropos.  Search the short manual page descriptions for keywords and display any matches.  See apropos(1) for details.

       -K, --global-apropos
              Search  for  text in all manual pages.  This is a brute-force search, and is likely to take some time; if you can, you should specify a section to reduce the number of pages that
              need to be searched.  Search terms may be simple strings (the default), or regular expressions if the --regex option is used.

              Note that this searches the sources of the manual pages, not the rendered text, and so may include false positives due to things like comments in  source  files.   Searching  the
              rendered text would be much slower.

       -l, --local-file
              Activate  "local"  mode.   Format and display local manual files instead of searching through the system's manual collection.  Each manual page argument will be interpreted as an
              nroff source file in the correct format.  No cat file is produced.  If '-' is listed as one of the arguments, input will be taken from stdin.  When this option is not  used,  and
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ flag -k
bash: flag: command not found
hacker@man~searching-for-manuals:~$ -k flag
bash: -k: command not found
hacker@man~searching-for-manuals:~$ challenge --apropos
bash: challenge: command not found
hacker@man~searching-for-manuals:~$ /challenge/run --apropos
bash: /challenge/run: No such file or directory
hacker@man~searching-for-manuals:~$ /challenge/challenge --apropos
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:~$ /challenge/challenge -k
Incorrect usage! Please read the challenge man page!
hacker@man~searching-for-manuals:~$ man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
lscnlrxnid (1)       - print the flag!
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour of validity checking and error displaying
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
hacker@man~searching-for-manuals:~$ man lscnlrxnid

CHALLENGE(1)                                                                           Challenge Commands                                                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --lscnlr NUM
              print the flag if NUM is 424

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

hacker@man~searching-for-manuals:~$ /challenge/challenge --lscnlr 424
Correct usage! Your flag: pwn.college{4lLsc2n4lXVrGxNYDRnXi_RXL_Q.dZTM4QDLyMDO0czW}
```

## CHALLENGE 6: HELPFUL PROGRAMS
- DOCUMENTAION:
  Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /?

- THOUGHT PROCESS:
  We have to use the --help arguemnt on /challenge/challenge program to get the documentaion of the function and from there we have to find the correct argument to get the flag

- SOLUTIONS:
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 87
hacker@man~helpful-programs:~$ /challenge/challenge -g 87
Correct usage! Your flag: pwn.college{0Fgef8r71CSuJsITpYE2v6nv98W.ddjM4QDLyMDO0czW}
```

## CHALLGNE 7: HELP FOR BULLETINS

- DOCUMENTATION:
  Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:

- THOUGHT PROCESS:
In this challenge, we have to use the help shell function on the program challenge, to find the hidden value as argument to pass to the program,to get the flag

- SOLUTIONS:
  I ran the following program
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "gid2kYRJ".
hacker@man~help-for-builtins:~$ challenge --secret gid2kYRJ
Correct! Here is your flag!
pwn.college{gid2kYRJ-jmyNRkv9zxvymHNePw.dRTM5QDLyMDO0czW}

```
