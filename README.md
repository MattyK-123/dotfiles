# DotFiles

This repository contains my personal dotfiles (e.g., .bashrc, .vimrc) that customize the behavior of tools and programs on Unix-like systems. I manage them using a bare Git repository, an elegant method that keeps my home directory clean and allows easy synchronization across machines.

## Installing on a New System

1. Add alias to shell config (e.g., `.bashrc`):
   ```bash
   alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
   ```

2. Clone the `dotfiles` repository via Https:
   ```bash
   git clone --bare https://github.com/MattyK-123/dotfiles.git $HOME/.cfg
   ```
   or via SSH:
   ```bash
   git clone --bare git@github.com:MattyK-123/dotfiles.git $HOME/.cfg
   ```

   
4. Checkout the actual content from the bare repository to your `$HOME`:
   ```bash
   config checkout
   ```
   
5. If conflicts occur, back up existing files:
   ```bash
   mkdir -p .config-backup && config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
   ```

## Version Controlling New Files

1. Add alias to shell config (e.g., `.bashrc`):
   ```bash
   alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
   ```

2. Prefix normal git command with `config` alias:
   ```bash
   config status
   config add .vimrc
   config commit -m "Add vimrc"
   config add .bashrc
   config commit -m "Add bashrc"
   config push
   ```
