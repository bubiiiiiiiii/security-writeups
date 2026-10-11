# OverTheWire Bandit: Levels 0 to 10

## Level 0
Goal: log in and find the password in a file
Commands: ssh, ls, cat
Mistake: forgot bandit0@ in the ssh command, so SSH used my Windows username
Lesson: ssh needs username@host

## Level 1
Goal: read a file named "-"
Commands: cat ./-
Mistake: ran "cat ./" which means "the current folder", not the file
Lesson: a lone - means "read from keyboard", so ./ makes it a real file path

## Level 2
Goal: read a file with spaces in the name (and dashes at the start)
Commands: cat ./"--spaces in this filename--"
Lesson: spaces split a command into pieces; quotes keep them together

## Level 3
Goal: find a hidden file
Commands: ls -la
Lesson: hidden files start with a dot and don't show up with plain ls  
