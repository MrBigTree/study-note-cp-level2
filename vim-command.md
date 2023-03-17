# Vim Command

## Fundamental Command

- ESC: normal mode
- i: insert mode

### deal with changes
- u: undo
- U: To undo all the changes on a line
- ctrl+r: redo
- exit Vim type: 
  - <ESC> :q! <ENTER> to trash all changes.
  - <ESC> :wq <ENTER> to save the changes.

### moving cursor around
- hjkl: left, down, up, right
- w: next word
- b: backward word
- gg: file top
- G: file end
- 0 Move cursor to start of a line
- $ Move cursor to end of a line

### jump to a word
- /word (find word, use n/N to go to next or prev result)
- `*` (move to next appreance of the current word)
- `#` (move to pre appreance of the current word)

### copy and cut
- copy
  - yy: copy a line
  - nyy: copy multiple lines
  - yiw (copy the word cursor in)
- cut
  - dd: cut a line
  - ndd: cut n lines
  - diw: cut the word cursor in
  - dw: cut from the cursor up to the next word type
  - dtx: cut till x
  - dfx: cut till on x
  - d$/D: cut from cursor to the end of a line
  - x cut a character at the cursor

### paste at
- after the cursor or below the line: p
- before the cursor or above the line: P 

### insert at
- left: i
- right: a
- start of a line: I
- end of a line: A
- replace the character under the cursor, type r and then the character you want to have there

### add a blank line:
- below: o
- above: O


## Advanced Command
The format for a change command is: 
operator [number] motion
where:
- operator - is what to do, such as d for delete
- [number] - is an optional count to repeat the motion
- motion - moves over the text to operate on, such as w (word), $ (to the end of line), etc.

- D/C CUT TO END/INSERT
- y$/0 cope to end/start of the line
- fx move cursor on next x
  - use ;/, to move to the next or prev one
  - use Fx to move backwards
- tx move cursor before x
  - use ;/, to move to the next or prev one
  - use Tx to move backwards
- % between pairing () [] {}
- ~: change case

## creating tags (NOT VIM)
- tag with children
  `tag>child*7` Tab

- with class
  `tag.class*4` Tab

- omit div when creating div tag
  `.class*4` Tab -> <div>

- with id
  `tag#*3` Tab
  `#*3` Tab -> <div>

`tag*2>child*3`

- example: `ul*2>li*3`

`ul>li.item${$}*24` Tab

- can only omit the first div
  `#*2>div*3`

- d/y/c/v are inter-changeable
