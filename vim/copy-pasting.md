# Copying and  pasting

As developers we all love a good ol copy paste. A `cmd + c` then `cmd + p`. 😉

## Copying / Yanking
To copy files simply type hit `y`.

Doing this just with your cursor will just take whatever is in that position at that time.

### Copying chunks
So what if we want to copy a whole word?

Remeber before when I went through motion characters? (check it out [here](./moving-the-cursor.md) thats what we can use in combination with `y`

- `y` followed by `e` will copy that whole word now.
- `y` followed by `$` will copy everything from where the cursor is to the end of the line.

This can then be paired with lots of different motion characters.

This can also be paired with [visual mode](./visual.md)

## Cutting
To cut things we can simple use `x`.

This has the same rules as applied above in copying☝️..

## Pasting
To paste the things we've just copied we use `p`.
Move your cursor to the new position after copying/yanking/cutting and paste where you please.

### Pasting between files
There are someways to can get vim to work with copy pasting across files in different vim windows open similtaniously. However most likely by default this may not be set up.

A way to get around that is to use the `edit` mode.

#### Edit mode
To get into edit mode we type `:e` + `FILENAME`.

e.g
```vim
:e my-file.md
```

Now you've got the file open paste your copy where you please. Then write and quit that file. `:wq`.

