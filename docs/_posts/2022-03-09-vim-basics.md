---
layout: post
title:  "VIM Basics"
date:   2022-03-10 00:01:21 +0530
categories: vim editor vi
---

VIM Basics:

Vim is Improved Vi editor which is powerful editor for *nix like OS.

```bash
# on command line type

vim <filename>

i - insert mode - from the curser
I - insert mode - from the beginning of the line
a - insert mode - append from the cursor
A - insert mode - append at the end of the current line
o - insert mode - with new line below from the cursor line
O - insert mode - with new line above from the cursor line

:set number - set line number
:set relativenumber - set line numbers relative to current line to the top and bottom
```

put these stuff in the `~/.vimrc` file so that it preserves the settings everytime we load `vim`

```bash
set number # shows line numbers
set relativenumber # shows line numbers relative to cursor
set tabstop=4 # set tab stuff
set shiftwidth=4 # set shift width
set autoindent
set mouse=a # enable mouse interaction inside vim
colorscheme slate # sets color scheme for vim
```
## Navigation:

```bash
k - Up
j - Down
h - Left
l - Right

# 5 Up Arrow or 5k - Move 5 lines above.

u - Undo
Ctrl + R - Redo
5u - Undo 5 times
5Ctrl+R - Redo 5 times
```

## Visual Mode:

```bash
v - enter into visual mode

# Select text with Visual Mode

d - deletes the selection
y - yanks the selection
p - pastes the yanked content below current line
P - paste the yanked content above the current line
dd - cuts the whole line
yy - yanks the whole line

cc - delete the content of the line and enter in to insert mode to write new stuff on the same line
D - deletes the rest of the line from current cursor point
C - changes the content from the cursor point to the end of the line (deletes the rest of the line and enter in to insert mode)
Y - copies the entire line from the beginning
r - replace the current character with the typed one.
```

### Navigate through:

```bash
w - jump from one word to another (delimeters between words space( ), hypen (-) ).
W - jump from one word to another forward direction (delimeter only space).
b - jump from one word to another backward direction (delimeters between words space( ), hypen (-) ).
B - jump from one word to another backward direction (delimeter only space).

d2w - delete 2 words in the forward direction
d2b - delete 2 words in the backward direction

diw - deletes the current word
ciw - changes the current word (removes the current word in the cursor and enter in to insert mode)
yiw - yanks the current word

di" - deletes the text inside the quotes
ci" - changes the text inside the quotes
yi" - yanks the text inside the quotes.

e - goes to the end of the word.
0 - goes to beginning of the line.
$ - goes to the end of the line.

d0 - deletes everything from current cursor to the beginning of the line.
d$ - deletes everything from current cursor to the end of the line.

% - jumps to the matching paranthesis { } back and forth.

t* - go to one position before the next available * in the file (forward direction).
T* - go to one position before the next available * in the file (backwards).

f* - go the next available * position.
dt* - delete the current line until the * 
dt( - delete the current line until the (

gg - goes to the beginning of the file
G  - goes to the end of the file
12G - goes to the line number 12.
:21 - goes to the line 21.
```

## Intermediate Skill:

### Indentation:
```bash
>> - indents the current line to the right
<< - indents the current line to the left
> - indents the current selection to the right
< - indents the current seletion to the left

= indents the current line
gg=G - moves to the beginning of the file and fix indentation until the end of the file.

# select something using visual mode then press =, then it indents the selection correctly.
```

## Search:

```bash
/url - searches the url in the file in forward direction
	n - finds the next occurance in forward direction
	N - finds the search term backwards.
?url - searches the url in the file in backward direction
	n - finds the next occurance in backward direction
	N - finds the next occurance in forward direction
# - on a word - searches backward direction 
* - on a word - searches forward  direction
```
## Marking Waypoint:

```bash
# Go to a certain line and press ma (to 'mark' the line with reference 'a')
# Go to different place and press  'a (to move back to the line with reference 'a')

zz - move the current line as center of the screen.
```
## Search and replace all occurances:

```bash
:%s/character/symbol/g - to find character and replace with symbol 
```

## Search and replace only selection:

```bash
:s/symbol/something/g - to find symbol and replace with something
```
## Repeat the last command:

```bash
dd - cuts the current line
. - repeats the last command

:reg - will show the vim register (list  of commands executed)
"7p - will take the line represents 7 from the register and paste
"7yy - will yank the current line to the register position 7.
"+ - represents clipboard
"+p - will paste the clipboard
```

## Macros:

```bash
qa - records a macro named 'a' - whatever you do after will be recorded. 
qa <d3wA100>q - records macro named 'a' then delete 3 words then append the line with 100
q - quits the macro recording.
@q - will execute the macro at the current line.
```

## References:

- https://www.youtube.com/watch?v=RZ4p-saaQkc
