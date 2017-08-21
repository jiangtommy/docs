##tmux   
**notes:** `<prefix>` means prefix for tmux, default `ctrl + b`
#### basic usage
`tmux new -s myname`: create a new session   
#### basic configuration
change `tmux.conf` to `.tmux.conf` and move it to `~/`   
#### copy
`<prefix> + [`: enter copy mode   
`<space>`: start choose content   
`<Enter>`: choose content finish   
`<prefix> + ]`: paste
#### Sessions
`:new<CR>`: new session   
`:new -s <session-name>`: set session name when create new session   
`s`: list sessions   
`$`: name session 
#### Windows(tabs)
`c`: create window   
`w`: list windows   
`n`: next window   
`p`: previous window   
`f`: find window   
`,`: name window   
`&`: kill window   
#### Panes(splits)
`-`: vertical split   
`|`: horizontal split   
`o`: swap panes   
`q`: show pane numbers   
`x`: kill pane   
`{`: Move the curent pane left   
`}`: Move the current pane right   
`z`: toggle pane zome
#### Misc
`d`: detach   
`t`: big clock   
`?`: list shortcuts   
