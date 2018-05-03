# Searching in vim

Every needed to search through your file for a key word or phrase you're looking for? Here's some ways to do it in vim.

### Searching forward
Type `/` (hint: make sure you not in `insert` mode) then type your word you're looking for
```vim
/searching
```

### Searching backwards
Type `?` and this will search from the bottom up from where your cursor is.
```vim
?searching
```

After doing either of these commands, you can move to the next by pressing the `n` key.
This moves you to the next one in the direction you have searched in.

But what if you want to go the other direction during your search?
Simply press `N` or `shift + n` and that will find the next one in the opposite direction your searching.

so:

`n` : move to the next in the direction your searching
`N` or `shift + n` : move to the next in the opposite direction you are searching (backwards)

<INSERT IMG>



