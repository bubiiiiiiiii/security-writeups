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

## Level 4
Goal: find the one human-readable file among 10 mostly-binary files
Commands: file ./*
Mistake: opening files with cat showed garbage that looked like a password
Lesson: check the file type first; file tells you which one is ASCII text

## Level 5
Goal: find a file by size and properties (1033 bytes, not executable) across 20 folders
Commands: find . -type f -size 1033c ! -executable
Mistake: ran find after cd-ing into one folder, so it only searched that folder
Lesson: find searches from where you run it; the c in -size means bytes

## Level 6
Goal: find a file by owner, group and size anywhere on the server
Commands: find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
Mistake: used made-up user and group names instead of the real ones from the page
Lesson: start from / to search everything, and 2>/dev/null hides the errors

## Level 7
Goal: find the password next to a specific word in a large file
Commands: grep word data.txt
Lesson: grep filters lines instead of reading everything by eye

## Level 8
Goal: find the one line that appears only once
Commands: sort data.txt | uniq -u
Lesson: uniq only compares neighbouring lines, so sort first; pipes chain commands

## Level 9
Goal: find the readable string in a mostly-binary file
Commands: strings data.txt | grep "=="
Lesson: strings extracts readable text, then grep narrows it down

## Level 10
Goal: decode a base64-encoded file
Commands: base64 -d data.txt
Mistake: typed -d on its own, so the terminal said "command not found"
Lesson: options go after a command name; base64 is encoding, not encryption, with no key

## Bandit Level 11 → 12

**Goal:** The password is in `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13).

**Command:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

**Explanation:**
- `cat` prints the file contents
- `tr` translates characters from one set to another
- `'A-Za-z'` → `'N-ZA-Mn-za-m'` shifts every letter 13 places, which decodes ROT13

**What I learned:** ROT13 is a simple substitution cipher and is its own inverse, so applying it twice gives back the original text. It's trivial to break and gives no real security.
