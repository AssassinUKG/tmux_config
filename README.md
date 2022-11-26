# Tmux config plus zsh themeing 

Nice tmux config :)


## Usage

Copy the tmux.conf into "~/.tmux.conf" save and reload your termainal. 


```bash
# ~/.tmux.conf
set -g mouse on

# These bindings are for X Windows only. If you're using a different
# window system you have to replace the `xsel` commands with something
# else. See https://github.com/tmux/tmux/wiki/Clipboard#available-tools
bind -T copy-mode    DoubleClick1Pane select-pane \; send -X select-word \; send -X copy-pipe-no-clear "xsel -i"
bind -T copy-mode-vi DoubleClick1Pane select-pane \; send -X select-word \; send -X copy-pipe-no-clear "xsel -i"
bind -n DoubleClick1Pane select-pane \; copy-mode -M \; send -X select-word \; send -X copy-pipe-no-clear "xsel -i"
bind -T copy-mode    TripleClick1Pane select-pane \; send -X select-line \; send -X copy-pipe-no-clear "xsel -i"
bind -T copy-mode-vi TripleClick1Pane select-pane \; send -X select-line \; send -X copy-pipe-no-clear "xsel -i"
bind -n TripleClick1Pane select-pane \; copy-mode -M \; send -X select-line \; send -X copy-pipe-no-clear "xsel -i"
bind -n MouseDown2Pane run "tmux set-buffer -b primary_selection \"$(xsel -o)\"; tmux paste-buffer -b primary_selection; tmux delete-buffer -b primary_selection"

set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-yank'
set -g @yank_action 'copy-pipe-no-clear'
bind -T copy-mode    C-c send -X copy-pipe-no-clear "xsel -i --clipboard"
bind -T copy-mode-vi C-c send -X copy-pipe-no-clear "xsel -i --clipboard"

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

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


## Cheatshhet

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

Then, add powerlevel10k to ~/.zshrc

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```



