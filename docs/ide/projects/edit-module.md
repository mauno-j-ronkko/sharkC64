# Editing a module

The source code of a module is shown in the editor view.
Each module is in its own tab.

![Editor view](../../images/project/imported-module.png)

The status row below the source code shows if the module has been changed or saved.
It also shows the location of the cursor.

Currently, the editor supports all basic editing functionalities, which
can also be accessed through Edit menu.

![Edit menu](../../images/menu/edit.png)

The editor supports undo and redo actions, as well as standard cut-copy-paste actions.


## Find action

If you select the "Find..." item from the menu, it opens the find panel below the source code.

![Find panel](../../images/editor/find-panel.png)

In the panel, you can type the text to be found. 
You can move to the next or previous instance of the text by clicking the arrow buttons
next to the text field.
You can close the entire find panel by clicking the cross button next to the arrow buttons.


## Replace action

If you select the "Replace..." item from the menu, it opens the replacement panel below the find panel.

![Find panel](../../images/editor/replacement-panel.png)

In the panel, you can type the text to be used in replacing the found text.
You can replace the highlighted instance by clicking the "one" button.
You can replace all the text instances by clicking the "all" button.
You can close the entire replacement panel by clicking the cross button next to the "all" button.


## Jumping in source code

Suppose you have cursor placed in a module source code over a term,
like `block.height`, as in the image below.

![Jump source module](../../images/editor/jump-source.png)

If you then select the menu item "Jump To...", the SharkC64 IDE
will automatically open the module `block` and locate the
first occurrence of the term `height` in it.

![Jump target module](../../images/editor/jump-target.png)

This works for all the terms, such as constants, variables, data sections, and functions.

If, however, the cursor is not over a term, and the menu item "Jump To..."
is selected, a dialog is opened, where you can type in the term 
that you wish to locate.

![Jump dialog](../../images/editor/jump-dialog.png)

It should be noted that at the moment jumping in the source code is not fully accurate.
It will locate the first occurrence of a term in a module.
This means that if the module has similarly named terms, the first one of them is located. 
That may not be the term that was looked for.
Thus, the jumping fails, for instance, if a module imports or uses another module
that has the same name as a variable that was looked for. 
Then, the module is located in the use section instead of the variable of the module. 


## Switching between modules
You can switch between the modules by clicking the tab name in the editor view.
Alternatively, you can click the module name in the Project tab to open the module
in the editor view.
You can close a module by clicking the cross button next to the tab name.


<br /><br />
:leftwards_arrow_with_hook: [Back to index](../../index.md)

