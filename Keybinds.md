# Default Keybinds

You can access the Neovim documentation with :help.

1. **Basic Commands:**

   - `:q` or `:quit`: Quit Neovim.
   - `:w` or `:write`: Write (save) the current file.
   - `:wq` or `:x` or `:writequit`: Write and quit.
   - `:e <filename>` or `:edit <filename>`: Open a file.
   - `:bd` or `:bdelete`: Close the current buffer.
   - `:bn` or `:bnext`: Move to the next buffer.
   - `:bp` or `:bprev`: Move to the previous buffer.

2. **Navigation Commands:**

   - `:e .`: Open the file explorer.
   - `:cd <directory>`: Change the current working directory.
   - `:vsp <filename>` or `:vsplit <filename>`: Open a file in a vertical split.
   - `:sp <filename>` or `:split <filename>`: Open a file in a horizontal split.
   - `:tabe <filename>` or `:tabedit <filename>`: Open a file in a new tab.
   - `:tabn` or `:tabnext`: Move to the next tab.
   - `:tabp` or `:tabprev`: Move to the previous tab.

3. **Search and Replace:**

   - `:/{pattern}`: Search forward for a pattern.
   - `:/{pattern}/g`: Search globally for a pattern.
   - `:s/{pattern}/{replacement}/g`: Substitute globally.
   - `:noh` or `:nohlsearch`: Turn off search highlighting.
   - `:set hlsearch`: Enable search highlighting.

4. **Undo and Redo:**

   - `:u` or `:undo`: Undo the last change.
   - `:Ctrl+r` or `:redo`: Redo the last undone change.

5. **Marks:**

   - `:marks`: List all the marks.
   - `:'a`: Move the cursor to the line of mark 'a'.
   - `:delmarks a b c`: Delete marks 'a', 'b', and 'c'.

6. **Windows and Tabs:**

   - `:qall` or `:qa`: Quit all windows and tabs.
   - `:sp` or `:split`: Split the window horizontally.
   - `:vsp` or `:vsplit`: Split the window vertically.
   - `:tabnew`: Open a new tab.
   - `:tabclose`: Close the current tab.

7. **File Operations:**

   - `:Explore` or `:E`: Open the file explorer.
   - `:Files` or `:F`: Fuzzy find files using Telescope (if configured).

8. **NERDTree (if installed):**
   - `:NERDTree`: Open the NERDTree file explorer.
   - `:Bookmark <name>`: Create a bookmark in NERDTree.
