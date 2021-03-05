# bashref 

A [quick reference](bashref) for various Bash shell commands.

## ar (Add reference)
A Bash script to add a reference to `bashref`. 

Usage: `ar KEYWORD`. 

If KEYWORD exists, adds a reference under the heading for KEYWORD. If KEYWORD does not exist, creates a new heading for KEYWORD and reference at end of `bashref`.

## vr (View reference)
A Bash script to view an existing reference. 

Usage: `vr [KEYWORD]`. 

If KEYWORD is specified, prints the entry for KEYWORD, otherwise prints a list of all entries in `bashref`.

