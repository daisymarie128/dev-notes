# Deleting in vim

## Deleting basics
The first command to remeber when wanting to delete a character without entering `insert mode (i)` is `d`.

Pressing `d` then and arrow or navigation key of your choicell delete in that direction.

- `d` then a left or right navigation key (arrows || h,l) : will delete a single character in the left or right direction depending on your choice.

- `d` then a up or down navigation key (arrows || j,k) : will delete the current line the cursor is on plus the one above of below it.

## Mixing deleting with motion commands
`dw` : deletes from where the cursor is to the start of the next word.
`d$`: deletes from where the cursor is to the end of the line.

For more motion commands to mix with this see [motion commands](./moving-cursor.md#motion-characters)

## Undoing changes
`u` : will undo whatever edit you've just made to the file.
