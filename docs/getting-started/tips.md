# Tips
This page contains tips that users have suggested would have been useful to know when they first started with APL. It should be read in conjunction with [Getting Started](https://www.dyalog.com/getting-started.htm).

To suggest a tip or tell us something that you wish you'd known when you first started, send an email to [tips@dyalog.com](mailto:tips@dyalog.com) for consideration for inclusion on this page.

### Getting Help

- The ]Help user command opens the online documentation.
- In the Microsoft Windows IDE or the RIDE, place the cursor on a symbol or other built-in and press **F1** to open the online documentation page for it.

### Editing

- Try the **F1** tip above for )ED to learn how to quickly create new items of various types.
- Use **Shift** + **Enter** to edit a name.
- )ED "file:///path/file.ext" lets you edit plain-text files and, on closing the Session, asks you how to use the content.
- Load APL functions/operators/objects from plain-text files with 2⎕FIX'file:///path/file.ext'.

### Saving Your Work

#### ... and picking up from where you left off.

- If you enter )OFF then your Session log is saved before APL closes, so you can simply scroll up when you're ready to continue.
- If you enter )CONTINUE then your workspace is saved with a temporary name and you can retrieve it with )LOAD continue.

### Debugging and Meta Information

- Use **Ctrl** + **Enter** to trace into a function and execute it one line at a time.
- Use **Shift** + **Enter** with the cursor on white space to edit a suspended function.
- Use **Ctrl** + **Break** to stop when an expression runs for a long time or results in long output in the session (alternatively, select **Interrupt** from the Session's **Action** menu).
- Get all the technical details of the last error or event with ⎕JSON⍠'Compact'0⊢⎕DMX.
- Enter 'tc'⎕CY'dfns' and then insert tc to the right of any function that you want to inspect

### Shortcuts

- Use **Ctrl** + **Shift** + **Backspace** and **Ctrl** + **Shift** + **Enter** to scroll backward and forwards through your input history (they can also be used as _Undo_ and _Redo_ in the **Edit** window.
- Many in-built functionalities have neither menu items nor keyboard shortcuts assigned by default. To configure keyboard short-cuts, got to **Options > Configure> Keyboard Shortcuts** in the Microsoft Windows IDE or click the keyboard icon in the RIDE.
- In the Microsoft Windows IDE, you can use the copy and paste buttons on the **Object** (not **Edit**) toolbar to copy and paste tables as matrices, documents as vectors of character vectors, and images as bitmap objects.

### Display Forms

- The settings in this section can be made permanent by saving your session:
    - In the Microsoft Windows IDE: **Session > Save**.
    - Within any Dyalog Session: 2⎕NQ⎕SE'FileWrite'.
- ]Rows on -fold=3 will let you scroll horizontally and trim large outputs so that they don't flood your screen vertically.

#### Boxing

- Turn boxing on to make the display of nested arrays more clear:
    
          ]Box on
    Was OFF
          ⍳2 3
    ┌───┬───┬───┐
    │1 1│1 2│1 3│
    ├───┼───┼───┤
    │2 1│2 2│2 3│
    └───┴───┴───┘
    
- With the trains modifier, you can display [function trains](https://apl.wiki/Tacit_programming#Trains) with a tree structure:
    
          ]Box -trains=tree
    Was -trains=box
          +⌿÷≢
      ┌─┼─┐
      ⌿ ÷ ≢
    ┌─┘    
    +
    
- With the fns modifier, nested arrays will have boxed display even if they are printed to the session from within functions:
    
          PrintShape←{⍴⎕←⍵}
          PrintShape ⍳1 3
     1 1  1 2  1 3 
    1 3
          ]Box -fns=on
    Was -fns=off
          PrintShape ⍳1 3
    ┌───┬───┬───┐
    │1 1│1 2│1 3│
    └───┴───┴───┘
    1 3
    
- With the style modifier you can get a more verbose view, including hints for axes and data types:
    
          ]Box -style=max
    ┌→─────────────┐
    │Was -style=min│
    └──────────────┘
          ⊂'APL'
    ┌───────┐
    │ ┌→──┐ │
    │ │APL│ │
    │ └───┘ │
    └∊──────┘
    
- See all the options with ]Box -??

### Quick Utilities

- ]Map displays the content and structure of your workspace.
- ]Plot <data> draws simple graphs of your data (see Plot -?? for details).
- ]Open <filename> opens a file in its default application.
- ]CD <dir> lets you change directory from inside an APL Session.
- In general, help for user commands can be found with ]<Command> -?.
- Use ⎕SE.Dyalog.Utils.repObj <myArray> to generate an expression for (almost) any given array.
- Use the workspace explorer to see a tree view of your workspace:
    - In the Microsoft Windows IDE, go to **Tools > Explorer**.
    - In the RIDE (default interface on macOS, optional interface on other platforms), go to **View > Show Workspace Explorer**.