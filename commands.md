# Linux Command Cheat Sheet (from Bandit)

## Looking around
ls              list files in the current folder
ls -la          list everything, including hidden files (names starting with .)
cd folder       move into a folder
cd ..           go back up one folder
pwd             show where I am right now

## Reading files
cat file        print a file's content
cat ./-file     the ./ stops a dash-name from being read as an option
cat "name with spaces"     quotes keep spaces as one name
file ./*        tells me the type of every file here (ASCII text vs data)
strings file    pulls readable text out of a binary file

## Searching
find . -type f -size 1033c ! -executable
  → search from here, files only, exactly 1033 bytes, not executable
  → the 'c' = bytes. Without it, size is counted in 512-byte blocks
find / -user X -group Y -size 33c 2>/dev/null
  → search the whole server; 2>/dev/null hides "permission denied" noise
grep word file          show only lines containing a word
find only searches from where I run it, so run it from the top folder

## Combining commands
|    pipe: sends the output of one command into the next
strings data.txt | grep "=="
sort file | uniq -u     show only lines that appear exactly once
                        (uniq only works on sorted input)

## Decoding
base64 -d file          decodes base64 (encoding, not encryption)

## Other
ssh bandit5@bandit.labs.overthewire.org -p 2220
  → the username goes in front of the @, password = the one found last level
man command     opens the manual (q to quit, / to search)
reset           fixes the terminal after printing binary junk
Tab key         autocompletes file names and adds backslashes for spaces
Ctrl + C        stops a command that's stuck
