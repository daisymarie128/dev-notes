# Moving your cursor

## Basic navigation keys
```
	^
	k
   < h	   l >
	j
	V
```

## Motion Charaters
Motion characters define a direction for a command to go in.
This can be used not only for moving around but also to delete in directions etc.

For now i'll just show you how to use them to move your cursor.
But just rmeber you can pair these with other commands!

### Positive movtions 
- `w` : to the start of the next word, EXCLUDING its first character.
- `e` : to the end of the current word, INCLUDING the last character.
- `$` : to the end of the line, INCLUDING the last character.

### Reverse motions
- `b` : to the start of PREVIOUS the word, EXCLUDING its first character. 
- `ge` : to the start of the current word, INCLUDING the last character.
- `0` : to the start of the line, INCLUDING the first character.

Typing numbers before a motion character will make it move that far the way that motion goes
Example:
`3w` : will move your cursor 3 words to right
`3b` : will move your cursor 3 words to the left

## Jumping to positions
There are many different ways to jump around in vim. So I'll seperate it out into scenarios.

### Jump to start of file
`gg` : takes you to the very first position of the first line of your file.

### Jump to end of file
`G` : takes you to the very last position of your file.

### Jump to a specific line
`:<LINE-NUBER>` : takes you to your specified line
e.g `:200`

### How to find current line number
`ctrl + g` will print out your current position
> To find out more on how to display your line numbers on the left see [this](link-here)

