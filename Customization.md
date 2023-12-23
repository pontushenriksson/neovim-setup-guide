# How to customize Neovim and add more plugins

## 1. Create an init.lua file:

1. Visit `C:\Users\<USER>\AppData\Local` and check for a folder called `nvim`. If it doesn't exist, create a new folder called `nvim`.
2. Open the nvim folder and create a new file called `init.lua` inside that folder.

## 2. Edit the `init.lua` file to add new configurations and plugins:

1. Open the `init.lua` file.

### Add custom spacing configuration:

1. Edit the `init.lua` file to add this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
```

At this stage the total `init.lua` file content should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
```

2. Save the changes.

### Install `Lazy.vim` package manager:

_[github.com/folke/lazy.nvim](https://github.com/folke/lazy.nvim)_

1. Edit the `init.lua` file to add this:

```vim
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

local plugins = {}
local opts = {}

require("lazy").setup(plugins, opts)
```

2. Save the changes and then open the file in Neovim. You open it by opening opening cmd in the `C:\Users\<USER>\AppData\Local\nvim` folder and then writing `nvim init.lua` in that window.

3. Press `esc` and then write `:source %` in the command line.

4. You can now test that Lazy is installed by entering `:Lazy` in the command line.

At this stage the total `init.lua` file content should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")

local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

local plugins = {}
local opts = {}

require("lazy").setup(plugins, opts)
```

### Install the color scheme `Catppuccin`:

_[github.com/catppuccin/nvim](https://github.com/catppuccin/nvim)_

1. Edit the `init.lua` file to add this:

```vim
{ "catppuccin/nvim", name = "catppuccin", priority = 1000 }
```

and

```vim
require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```

that part should look like this:

```vim
local plugins = {
    { "catppuccin/nvim", name = "catppuccin", priority = 1000 }
}
local opts = {}

require("lazy").setup(plugins, opts)

require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```

2. Save the changes in the `init.lua` file and restart nvim and open the file again.

At this stage the total `init.lua` file content should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")

local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

local plugins = {
    { "catppuccin/nvim", name = "catppuccin", priority = 1000 }
}
local opts = {}

require("lazy").setup(plugins, opts)

require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```

### Install the plugin `telescope` and `plenary`:

_[github.com/nvim-telescope/telescope.nvim](https://github.com/nvim-telescope/telescope.nvim)_

1. Edit the `init.lua` file to add this:

```vim
    vim.g.mapleader = ""
```

```vim
    {
      'nvim-telescope/telescope.nvim', tag = '0.1.5',
      dependencies = { 'nvim-lua/plenary.nvim' }
    }
```

and

```vim
    local builtin = require("telescope.builtin")
    vim.keymap.set('n', '<C-p>', builtin.find_files, {})
    vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})
```

that part should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
vim.g.mapleader = ""
```

```vim
local plugins = {
    { "catppuccin/nvim", name = "catppuccin", priority = 1000 },
    {
      'nvim-telescope/telescope.nvim', tag = '0.1.5',
      dependencies = { 'nvim-lua/plenary.nvim' }
    }
}
local opts = {}

require("lazy").setup(plugins, opts)

local builtin = require("telescope.builtin")
vim.keymap.set('n', '<C-p>', builtin.find_files, {})
vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})

require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```

2. Save the changes in the `init.lua` file, enter `source %` in the command line and restart nvim and open the file again.

At this stage the total `init.lua` file content should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
vim.g.mapleader = ""

local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)

local plugins = {
    { "catppuccin/nvim", name = "catppuccin", priority = 1000 },
    {
      'nvim-telescope/telescope.nvim', tag = '0.1.5',
      dependencies = { 'nvim-lua/plenary.nvim' }
    }
}
local opts = {}

require("lazy").setup(plugins, opts)

local builtin = require("telescope.builtin")
vim.keymap.set('n', '<C-p>', builtin.find_files, {})
vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})

require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```

## The complete `init.lua` file should look like this:

```vim

```
