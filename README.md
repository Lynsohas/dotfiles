# ❤ Dotfiles ❤
My current dotfiles. Could be yours as well.

## Some details
+ **OS**: Arch
+ **WM**: i3
+ **Terminal**: kitty
+ **Shell**: zsh
+ **File Manager**: Thunar for GUI, Ranger for terminal
+ **Launcher**: Rofi
+ **Bar**: Polybar (3 instances on one monitor, 2 on the other)
+ **Editor**: Vim (main) & Spacemacs

## Updated view:
![2019 Preview of Setup](https://i.imgur.com/yLiOPFK.png)

## Older picture:
![Preview of Setup](https://i.imgur.com/tewk8oJ.png)

## Instructions:
You can easily pick and choose the parts you like without having to use everything. Each folder is named after a package and contains every configuration file used by that application. The files inside the folders are relative to home (e.g. the file `vim/.vimrc` goes to `~/.vimrc`).

Since these are dotfiles they obviously require you to also install the original software you want these files to configure for you, they are after all only the configuration files.

To more quickly set things up I recomend to use GNU Stow to symlink the dotfiles.
1. Clone the repo into your home folder, e.g. `~/dotfiles`.
2. Install stow from your package manager. (or do the symlinks manualy, see: `man ln`)
4. Backup any of your original config files you want to keep around.
3. Go to the repo and run `stow vim` or similar to symlink the files asociated with that part of the setup.

## Considerations
My setup uses two monitors, one of which is an ultrawide monitor with higher than usual (1080p) resolution. If you use this on any other system you will have to manualy tweak the positioning of the polybar segments. This is not difficult, simple math should suffice. Same with the gaps/borders, they are most likely to large on for example only a single 1080p or 720p monitor.

### Addons
Many of the dotfiles require additional software/plugins or such that aren't imediately obvious, for example extra fonts, or other programs that don't require their own dotfiles, I have tried to document those in this file but I will have most likely missed one or more of them.
+ Various fonts for polybar. And Nerdfonts for Kitty.
+ ranger is using [ranger\_devicons](https://github.com/alexanderjeurissen/ranger_devicons).
+ tmux is using [powerline](https://github.com/powerline/powerline).
+ zsh is using [spaceship](https://denysdovhan.com/spaceship-prompt/).

## Custom keybinds
### i3
Mostly defauly keybindings as to not confuse other i3 users. For more information check out the i3 config file. Here are some additions:
+ `super + enter` - Launch Kitty running tmux
+ `super + Shift + enter` - Launch Kitty running ranger
+ `super + d` - Launch Rofi
+ `super + hjkl` - Move focus with vim-keys
+ `super + n` - run pywal, automatically select a new random wallpaper from `~/wallpapers/inuse`, generate new colorthemes for polybar, kitty, and much more, and automatically tell those applications to update (polybar restarts quietly). This is also done on each restart.

### vim
A lot of custom settings, mostly documented inside `.vimrc`.
+ TODO

### tmux
One of the main programs that have changed a lot from default in terms of keybindings. Default terminal copy-paste should still work as expected (`ctrl+shift+c`, mouse double, & tripple click for copy; middle mouse button, or `ctrl+shift+v` for paste).
+ Enable default vi-bindings (expect in command mode).
+ `ctrl + w` - Prefix, instead of `ctrl + b`. More vim like. Double press sends `ctrl + w` to the underlaying application.
+ `Prefix + r` - Reload tmux config.
+ `Prefix + s` & `Prefix + v` - Split horisontaly and vertically, same as vim.
+ Mouse off - Current solution to make the mouse behave as expected when doing quick copy-paste from terminal. Not perfect with vertical split panes. Try to use extrakto instead.
+ `Prefix + ctrl-c` - Copy-mode.
+ `Prefix + hjkl` - select pane.
+ `Prefix + HJKL` - resize pane, repeatable.
+ `Prefix + q` - kill pane. Same as vim close window. (default display panes moved to `Prefix + ctrl-q`)
+ `Prefix + /`, go to copy mode and search.
+ copy-mode-vi `/` & `?` - Uses incremental search (same as vim incsearch).
+ copy-mode-vi `v` - begin selection.
+ copy-mode-vi `V` - select line.
+ copy-mode-vi `ctrl+v` - begin block-selection.
+ copy-mode-vi `Home` - start of line.
+ copy-mode-vi `End` - end of line.
+ copy-mode-vi `y` - copy selection.
+ `Prefix + I` - Install plugins. Run once and forget. (`Prefix + U` update plugins)
+ `Prefix + Tab` - Start [extrakto](https://github.com/laktak/extrakto) plugin. This is magic. Requires fzf.
+ No non prefix keybindings that start with `ctrl` due to risk of colisions with applications running inside, such as vim/fzf.
+ `Alt + Arrows` - Switch panes. Leave `Alt+hjkl` for the shell or vim.
+ `Shift + Left/Right` - Switch windows.

## Wallpapers
The wallpaper is set with feh & pywal in the i3 configuration, as startup command.
+ It selects a random wallpaper from a folder (default ~/wallpapers/inuse).
+ `Super + n` - Randomly select a new wallpaper, and redo the themes on surrounding applications to match using pywal.
+ TODO more info.

## Scripts & Aliases
+ `bm` (**b**ook**m**ark) - Appends the current working directory (path) into a file in your home directory. If passed aadditional text it will append that as a comment on the line in the file. I use this to bookmark all my most commonly visited locations in the file system.
+ `cdb` (**cd** **b**ookmark) - Opens the file of bookmarks from your home directory, passes the lines to [fzf](https://github.com/junegunn/fzf), allows you to fuzzy search select a bookmark based on path or comment, and then changes your current directory to that location.
+ `fshow` - Git commit browser. `enter` for show, `Ctrl-d` for diff, \` toggles sort.
+ Various git log FZF scripts, see the `.zshrc` file for more details. , `
+ `Ctrl+r`, `Ctrl+t`, `Alt+c` - Default fzf behaviour.
+ `Ctrl+f` - fzf fuzzy search for file recursively down from current location, opens selection for editing in vim.
+ `cdd` - `cd ~/dotfiles`
+ `cdf` - cd to the directory of fzf fuzzy find filename.
+ `fkill` - fzf search all processes you have permission to kill, SIGTERM the selection.
+ `l` - `ls -lah`
+ `:e` - `vim`
+ `:q` - `exit`

## Misc software recomendations.
- CLI
    - [Zsh](https://github.com/zsh-users/zsh) - A shell similar to bash.
    - [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) - An open source, community-driven framework for managing your Zsh configuration.
    - [Bash](https://git.savannah.gnu.org/cgit/bash.git) - A Unix shell and command language.
    - [tmux](https://github.com/tmux/tmux) - A terminal multiplexer.
    - [Neovim](https://github.com/neovim/neovim) - Vim-fork focused on extensibility and usability.
    - [htop](https://github.com/hishamhm/htop) - Nicer than top.
    - [fzf](https://github.com/junegunn/fzf) - A command-line fuzzy finder. Used a lot in zshrc, vimrc, & tmux.conf.
    - [Ag](https://github.com/BurntSushi/ripgrep) - A line-oriented search tool that recursively searches directories for a regex pattern. Simiar to Grep, but faster.
    - [Nerd-Fonts](https://github.com/ryanoasis/nerd-fonts) - Patch fonts with a lot of extra symbols for use in terminal and more.
    - [fpp](https://github.com/facebook/pathpicker) - Helps picks a file path with UI from from a messy shellscript's output and pipes it into any program (mainly $EDITOR).
- GUI
    - [i3-gaps](https://github.com/Airblader/i3) - i3 fork with additional settings for spacing around/between windows.
    - [pywal](https://github.com/dylanaraps/pywal) - Generate and change color-schemes on the fly. Change the wallpaper and the theme of most applications to match.
    - [Rofi](https://github.com/DaveDavenport/rofi) - A window switcher, application launcher and dmenu replacement.
    - [Compton](https://github.com/tryone144/compton) (Fork) - A compositor for X11. Allows for transparency and blur.
    - [Arc Theme](https://github.com/NicoHood/arc-theme) (Fork) - A flat theme with transparent elements for GTK 3, GTK 2, and GNOME Shell.
    - misc tamsyn - font used in polybar
    - Wuncon Siji - font used in polybar
    - [Redshift](https://github.com/jonls/redshift) - Redshift adjusts the color temperature of your screen according to your surroundings. The lightbulb icon of the polybar lanches it and displays the current temperature.

## Contributing
I'm open to discuss suggestions, & changes. Feel free to send me a pull requests or message.
