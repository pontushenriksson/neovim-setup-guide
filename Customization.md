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

This is now the total `init.lua` file contents:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
```

### Install `Lazy.vim` package manager:

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

## The complete `init.lua` file should look like this:

```vim
vim.cmd("set expandtab")
vim.cmd("set tabstop=2")
vim.cmd("set softtabstop=2")
vim.cmd("set shiftwidth=2")
vim.g.mapleader = " "

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
  },
  {"nvim-treesitter/nvim-treesitter", build = ":TSUpdate"}
}
local opts = {}

require("lazy").setup(plugins, opts)

local builtin = require("telescope.builtin")
vim.keymap.set('n', '<C-p>', builtin.find_files, {})
vim.keymap.set('n', '<leader>fg', builtin.live_grep, {})

local config = require("nvim-treesitter.configs")
config.setup({
  ensure_installed = { "arduino", "bash", "c", "c_sharp", "cmake", "cpp", "css", "csv", "dockerfile", "git_config", "git_rebase", "gitattributes", "gitcommit", "gitignore", "html", "http", "java", "javascript", "json", "llvm", "lua", "make", "markdown", "markdown_inline", "nasm", "ninja", "passwd", "perl", "php", "python", "ql", "regex", "ruby", "rust", "scala", "scss", "sql", "ssh_config", "svelte", "toml", "tsv", "tsx", "typescript", "vim", "vue", "xml", "yaml", "zig" },
  highlight = { enable = true },
  indent = { enable = true }
})

require("catppuccin").setup()
vim.cmd.colorscheme "catppuccin"
```
