Tmux makes use of **sessions**, **windows**, and **panes**.  
 
There could be multiple sessions (processes) of tmux running. Only one session could be accessed at a given time.  
Each session could have mulitple windows. A window is the entire screen area. Windows are tabbed and they are listed in the bottom pane.  
Each window could have multiple panes which are horizontally or vertically split. 

The hotkey for tmux is **Ctrl b**

Tmux has many commands. You can  list the available commands (outside a tmux session) with `tmux <TAB> <TAB>`  

When you are in a tmux session, native tmux commands as determined above can be executed in the current session with `Ctrl b :`  
So `tmux <something>` is equivalent to `Ctrl b : <something>`  
Note the colon(:) used here. 

If you are in a tmux shell, you can list all the shortcuts with `Ctrl b : ?`  
Here all lines starting with `bind-key    -T prefix` are shortcuts that can be tried.  

**To start a new session with a name**  
`tmux new -t <session>`  

**To dettach from existing session**   
`Ctrl b d`

**To list all avalable tmux sessions**  
`tmux ls`

**To kill a session from the system**  
`tmux kill-session -t <session name>`

**Or to kill the current session from tmux**  
`Ctrl b : kill-session`

**To attach to a secific session**  
`tmux attach -t <session>`

**To create a new window**  
`Ctrl b c`

**To cycle through windows**  
`Ctrl b n`
`Ctrl b p`  
Here n means next and p previous

**Windows are numbered and can be accessed with**  
`Ctrl b <number>`

**To go to the last window**  
`Ctrl b l`

**To delete a window**  
`Ctrl b &`

**To rename a window**  
`Ctrl b ,`

**To create a pane by spliting existing window vertically**  
`Ctrl b %`   
Note `%` key is situated in the top row of the keyboard that can be used to split vertically

**To create a pane by spliting existing window horizontally**  
`Ctrl b "`  
Note `"` key is situated in the middle row of the keyboard that can be used to split horizontally

**To close a pane**  
`Ctrl b x`

**To cycle through panes**  
`Ctrl b <arrow up/down/right/left>`

**To resize panes**  
`Ctrl b Ctrl  <arrow up/down/right/left>`

