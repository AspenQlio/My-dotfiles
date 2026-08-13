# My-dotfiles

My Arch Linux dotfiles — HyDE (Hyprland) desktop configuration, shell setup, and app configs.

## Structure

The repo mirrors the home directory layout so it can be symlinked or copied directly:

```
.
├── .zshrc / .zshenv / .bashrc / .profile ...   # shell configs (root)
├── .gitconfig                                   # git identity + credential helper
├── .fonts / .icons / .themes                    # theme assets
└── .config/                                     # app configurations
    ├── hypr/            # Hyprland (window manager, hyprlock, hyprpaper)
    ├── hyde/            # HyDE config (wallbash) — theme cache excluded
    ├── waybar/          # status bar
    ├── rofi/            # launcher
    ├── kitty/           # terminal
    ├── nvim/            # Neovim
    ├── zsh/             # ZDOTDIR config (plugins, prompt, user.zsh)
    ├── fastfetch/       # system fetch
    ├── starship/        # prompt (if used)
    ├── btop/ cava/ dunst/ fish/ ...             # utilities
    └── ...
```

## What's excluded

- `~/.config/cfg_backups/` — HyDE theme-switch backups
- `~/.config/hyde/themes/` — wallpaper/theme cache (~300 MB)
- caches, history, and session data (`.zcompdump`, `.zsh_history`, etc.)
- credentials (`.git-credentials`, `~/.config/gh/hosts.yml`)

## Restore

Symlink-based restore (recommended):

```bash
git clone https://github.com/AspenQlio/My-dotfiles.git ~/dotfiles
cd ~/dotfiles

# shell + git config
ln -sf ~/dotfiles/.zshrc ~/.zshrc
ln -sf ~/dotfiles/.zshenv ~/.zshenv
ln -sf ~/dotfiles/.gitconfig ~/.gitconfig

# app configs
for d in .config/*/; do
  ln -sfn ~/dotfiles/$d ~/$d
done
```

Or copy directly:

```bash
cd ~/dotfiles && cp -r .zshrc .zshenv .gitconfig .config ~/
```
