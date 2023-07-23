# Tmux config plus zsh themeing 

Nice tmux config :)


## Usage

Install tpm
```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Copy the tmux.conf into "~/.tmux.conf" save and reload your termainal. 
```bash
# Richard Jones, 22/07/2023 - Custom Tmux config
## General Settings

set -g default-terminal "xterm-256color"
set -g history-limit 5000
setw -g xterm-keys on
set -s escape-time 10                     # faster command sequences
set -sg repeat-time 600                   # increase repeat timeout
set -s focus-events on

## Change the default key binding from Ctrl+b to Ctrl+a
unbind C-b
set -g prefix C-a

## mouse support 
set -g mouse on

## Hot reload Ctrl+r
bind-key r source-file ~/.tmux.conf \; display-message "~/.tmux.conf reloaded"

## Change split panes to v,h
bind h split-window -h
bind v split-window -v
unbind '"'
unbind %

## Display

set -g base-index 1           # start windows numbering at 1
setw -g pane-base-index 1     # make pane numbering consistent with windows
setw -g automatic-rename on   # rename window to reflect current program
set -g renumber-windows on    # renumber windows when a window is closed
set -g set-titles on          # set terminal title

## Activity
set -g monitor-activity on
set -g visual-activity off


# Dracula theme
set -g @plugin 'dracula/tmux'

set -g @dracula-show-battery true
set -g @dracula-show-powerline false
set -g @dracula-plugins "cpu-usage ram-usage time battery"
set -g @dracula-battery-label ""
set -g @dracula-military-time true
set -g @dracula-day-month true
set -g @dracula-show-timezone false
set -g @dracula-refresh-rate 10

# enable if powerline 10k installled
#set -g @dracula-show-powerline true

# Set tpm
set -g @plugin 'tmux-plugins/tpm'

# copy to xsel
bind -y run -b 'tmux save-buffer - | xsel -i -b'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

Install Dracula Theme
```
https://draculatheme.com/tmux
```

![image](https://github.com/AssassinUKG/tmux_config/assets/5285547/0f9dd969-6726-4b14-bcf5-5c2c67e875f8)

## Custom keys

Prefix
: `Ctrl + a`

>Windows  
split verticle : `prefix + v`  
split horizontal : `prefix + h`

>Others  
Hot tmux config reload
: `reload = prefix + r`

## Cheatsheet (Normal tmux)
### Toggle pane zoom
`prefix + z`

### Convert pane into a window
`prefix + !`


## Config 

- **Click and drag** with the **Left Mouse Button** to select some text and copy it into the primary selection
- **Double-click** the **Left Mouse Butto**n on a word to select the word and copy it into the primary selection
- **Triple-click** the **Left Mouse Butto**n on a line to select the whole line and copy it into the primary selection
- Click the **Middle Mouse Button** to paste from the primary selection
- **Ctrl + Shift + c** to copy the selection into the clipboard
- **Ctrl + Shift + v** to paste from the clipboard  


## Screenshots

![image](https://user-images.githubusercontent.com/5285547/204093029-cc8b3b01-d03f-4a77-b3a3-01acda40bea5.png)

![image](https://user-images.githubusercontent.com/5285547/204093045-5fc6c4ca-f8a9-4368-9464-29cfd238c4f2.png)


## Cheatsheet

![image](https://user-images.githubusercontent.com/5285547/204092916-96acdb42-8eca-486a-8048-3de37bc8bcbd.png)

![image](https://user-images.githubusercontent.com/5285547/204092927-303cc96d-9a4f-4862-bf80-2b75094f0927.png)

![image](https://user-images.githubusercontent.com/5285547/204092941-84e22638-7879-486e-8c82-7df7a4612f53.png)

![image](https://user-images.githubusercontent.com/5285547/204092964-89683a1b-2437-4516-8787-fe1a29d7464a.png)

![image](https://user-images.githubusercontent.com/5285547/204092988-e7cf5599-2da2-4652-95c3-4bf795dce198.png)

---

## Bonus 

### Install Ohmyzsh

[OhMyZsh](https://github.com/ohmyzsh/ohmyzsh)

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Set default shell

```bash
chsh -s $(which zsh)
```

### Add some plugins

```bash
cd ~/.oh-my-zsh/custom/plugins
git clone https://github.com/zsh-users/zsh-autosuggestions.git
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```

Now, edit your ~/.zshrc file to include them.

```plain
plugins=(
    git
    zsh-autosuggestions
    zsh-syntax-highlighting
)
```

Restart your Zsh with source ~/.zshrc.

### Powerlevel10k theme

Install

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Add correct font


[MesloLGS NF Regular.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)  
[MesloLGS NF Bold.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)  
[MesloLGS NF Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)  
[MesloLGS NF Bold Italic.ttf](https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

```
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf
wget https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf
```

cli install

```
make folder in ~/.local/share/fonts
cp the fonts to the location and refresh the font cache. 

$ fc-cache -f -v
```


Then, add powerlevel10k to ~/.zshrc

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Configure

```
$ p10k configure
```



