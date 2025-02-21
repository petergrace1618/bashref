# BASH REFERENCE

## vi
| Command | Use |
| - | - |
| :normal! 0go\<N\> " | Go to Nth character in file |
| dG, yG, cG | delete, yank, and change to end of file |
| dgg, ygg, cgg | delete, yank, and change to beginning of file |
| :argd file | delete file from argument list |
| :arge[dit] file | add file to the argument list and edits it |
| :args file1 file2 ... | load the given list of files for editing |
| :e! | reload the original file |
| :options | open window showing all vim options |
| :hid[e] | close the current window |
| ^W^W | switch to next window |
| /\<up-arrow\> :\<up-arrow\> | allows you to recall previous searches and commands |
| * | search for (and highlights) the word under the cursor |
| :%s///c | substitute on all lines (%) with confirmation (c) |
| :w | Save current file. |
| :w \<file\> | Save a copy of current file with name \<file\>. (Doesn't change name of current file) |
| :saveas \<file\> | Save current file as \<file\> |
| :edit \<file\> | Open new file to edit |
| :next | Go to next in list of files (entered on command line) |
| :prev | Go to previous ... |
| \<Ctrl-6\> | Switch between current/prev file |
| D | Delete from cursor to end of line |

## info
| Key | Use |
| --- | --- |
| t   | go to top node (menu page) |
| b   | beginning of node (top of page) |
| n   | Go to next node |
| p   | Go to previous node |
| ^x o | Move to next window |
| ^X 0 | Delete current window |
| ^X 1 | Delete all windows except current window |
| ?    | Lists a summary of commands |

## echo
| Option | Use |
| - | - |
| -e | enable interpretation of backslash escape characters |
| -e | Escape chars must be inside double quotes and -e option must precede text with escape chars |
| -e "\033c" | clears the screen |
| -n | suppress trailing newline |

## grep
| Option | Use |
| - | - |
| -e | match regexp |
| -i | ignore case |
| -n | print line number of matching lines |
| -v | invert pattern, i.e. show non-matching lines |
| -c | print count of matching lines |
| -q | quiet mode. supresses normal output |

## less
| Key command | Use |
| - | - |
| -,-- | set command line options from inside less |
| :e, E | open new file for examining |
| :n, :p, :x | view next, previous, first file in list |
| :d | remove current file from list of files |

## tr
Convert multiple occurrences of characters in \<charlist\> to single occurrences

    tr -s '<charlist>'

Delete all occurences of \<char\> from input

    tr -d '<char>'

## cat
| Option | Use |
| - | - |
| -e | shows control chars (e.g. ^M) and $ at EOL |
| -A | like -e but shows tabs as ^I |

## diff
| Option | Use |
| - | - |
| -s | report when files are the same |
| -y | two column output |
| -q | quiet mode. display only if files differ |

## ls
| Option | Use |
| - | - |
| -1 | -single column output |
| -p | -adds only / after directories |
| --indicator-style=none | -no indicator after filename |
| -d | list directory entries instead of contents, likewise with symbolic links |
| -p | add terminal backslash to directory listings |
| -Q | enclose entries in double quotes |
| -H | When a symbolic link points to a directory, follow the link |
| -L | dereference symbolic links. Shows info about file it points to, not about link itself |

List hidden files and directories. Doesn't match `.`, `..`, or `..*`

    ls .[^.]* -d

## stat.h
`sys/stat.h` located in /usr/include/sys

## ln
    ln -s TARGET LINKNAME

## sed
| Option | Use |
| - | - |
| -s | consider files separate instead of one continuous stream |
| -i | modify files in place |
| -f FILE | specifies a script file |
| -n | suppress automatic printing of pattern space |

## uniq
| Option | Use |
| - | - |
| -d | only print duplicate lines |

## cp
| Option | Use |
| - | - |
| -s | create symbolic link instead of copying file |

## wc
| Option | Use |
| - | - |
| -L | print length of longest line |

## sort
| Option | Use |
| - | - |
|-o FILE | send output to file instead of stdout |
| -d | sort in dictionary order. only consider alphanumerics and blanks |
| -r | reverse order sort |
| -c | check for sorted input. do not sort |
| -u | like uniq. collapse repeated lines |

## rm
| Option | Use |
| - | - |
| -r,-R | remove directories and their contents recursively |

## find
List directories other than hidden directories

    find . -maxdepth 1 -type d -name '[^.]*' -printf '%f\n'

Add `.bak` extension to files

    find . -name "H VII*.wav" -print0 | xargs -0 -i cp '{}' '{}'.bak

List directories only

    find . -maxdepth 1 -type d

Convert filename of the form `<NAME>/<NAME>.jpg` to `<NAME>/Folder.jpg` <br>
For example, `1971-Budgie/1971-Budgie.jpg` -> `1971-Budgie/Folder.jpg`

    find . -mindepth 1 -type d -printf '%f\0' | xargs -0 -I_ mv _/_.jpg _/Folder.jpg


## make
```
TARGET: PREREQUISITES
	RECIPE
```

## git
Display 0 if git repo, 128 if not

    git -C . rev-parse &>/dev/null; echo $?

List all config variables with scope and origin

    git config -l --show-origin --show-origin

When a repo is renamed, this set the local repo to point to the new repo

    git remote set-url origin <new-url>

Make git open help files in browser by default

    git config --global help.format html

Display 160-bit hash for given TEXT

    echo TEXT | git hash-object --stdin

Show only commits from author matching pattern

    git log --author=<pattern>

Reset \<branch\> to \<starting-point\>
    
    git branch -f <branch> <starting-point>

abort the merge after conflicts

    git merge --abort

continue merge after conflicts

    git merge --continue
    
create new branch and then switch to it

    git checkout -b <new-branch>
    
list the last N commits

    git log -N
    
remove files from index but not working tree (directory)

    git rm --cached <files>

show commit history

    git log

to show files in master branch

    git ls-tree --name-only master

to merge gh-pages into master

    git checkout master
    git merge gh-pages

to optionally delete gh-pages

    git branch -D gh-pages

To add existing local repository to github (first create new repo on github)

    cd PROJECTDIR
    git init
    git pull REMOTE-URL master
    git add .
    git commit -m MESSAGE
    git remote add REPO-NAME REMOTE-URL
    git push --set-upstream REPO-NAME master

to create a github pages branch (first rename main page to index.html)

    git branch gh-pages
    git checkout gh-pages
    git push REMOTE gh-pages

to show names/URLs of all remotes stored in project

    git remote -v

to update, commit, and push a project

    git add (FILE(s)|.)
    git commit -m "MESSAGE"
    git push (<remote>|origin) master

## set
Show lines in output of set command that match <regexp>

    grep -i <regexp> <<< `set`

Print shell variables only--no functions

    set -o posix; set; set +o posix

unset environment variable

    unset VAR

Any args after `--` are interpreted literally, even if they 
begin with `-`. Prevents any of args2 to be taken as an option.

    set [args1...] -- [args2...]

## zcat
Like cat but for zipped files

## export
| Option | Use |
| - | - |
| -n variable | remove variable from export list |

## if
use `[[` for compound conditionals

## date
Print date as YYYY-MM-DD hh:mm:ss

    date +"%F %T"

Equivalent to

    date +"%Y-%m-%d %H:%M:%S"

## xargs
Move all files in all subdirectories to current directory

    ls */* | xargs -I_ mv _ .

## free
Displays free memory. Gets data from /proc/meminfo

| Option | Use |
| - | - |
| -m | display amount in MB |

## bash
To change home directory in Git Bash, add the following to /c/Users/peter/.bashrc :

    export HOME=/c/cygwin64/home/GraxonTheImbiber
	cd $HOME

Redirect stdin & stdout to /dev/null. i.e. suppress all output

    &>/dev/null
	
## tar
Create archive.tar from files foo and bar.

    tar -cf archive.tar foo bar

List all files in archive.tar verbosely.

    tar -tvf archive.tar

Extract all files from archive.tar.

    tar -xf archive.tar

## python
| Option | Use |
| - | - |
| -i | Inspect interactively after running script. Forces a prompt even if stdin does not appear to be a terminal; also PYTHONINSPECT=x |

## env
Set each NAME to VALUE in the environment and run COMMAND.

    env [OPTION]... [-] [NAME=VALUE]... [COMMAND [ARG]...]


