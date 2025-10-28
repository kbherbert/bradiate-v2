---
title: My terminal setup
publishDate: 28 Oct 2025
description: Achieving terminal velocity 😆
---

I spend most of my day in the terminal, so I've invested time in building a setup that's both powerful and pleasant to use.

My shell runs in [Ghostty](https://ghostty.org/), a GPU-accelerated terminal emulator that's fast and responsive. Inside, I use [Neovim](https://neovim.io/) as my editor, paired with [fzf](https://github.com/junegunn/fzf) for fuzzy file searching. My prompt is styled with [Starship](https://starship.rs/), which gives me useful information at a glance without cluttering the line. Everything is themed with [Catppuccin](https://catppuccin.com/), a beautifully soothing color scheme I use across all my tools.

All of my configuration files are version-controlled on a my private GitHub repo, and configured using [GNU Stow](https://www.gnu.org/software/stow/) to manage symlinks. This makes it trivial to set up a new machine or sync changes across systems.

For deeper dives into this ecosystem, I'd recommend checking out [Josean Martinez](https://www.josean.com) and [ThePrimeagen](https://github.com/ThePrimeagen)—they've both created excellent content on building a productive terminal environment.