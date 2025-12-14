# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Neovim configuration based on kickstart.nvim. It uses lazy.nvim as the plugin manager and is written entirely in Lua.

## Configuration Structure

- `init.lua` - Main configuration file containing all core settings, keymaps, and plugin specifications
- `lua/kickstart/plugins/` - Optional kickstart plugins (debug, indent_line, lint, autopairs, gitsigns, neo-tree)
- `lua/custom/plugins/` - Custom user plugins (auto-loaded via `{ import = 'custom.plugins' }`)

## Key Settings

- Leader key: `<Space>`
- Nerd Font enabled: `vim.g.have_nerd_font = true`
- Indentation: 4 spaces (tabstop=4, shiftwidth=4, expandtab)
- Colorscheme: tokyonight-night

## Plugin Management

Check plugin status: `:Lazy`
Update plugins: `:Lazy update`
Install LSP servers/tools: `:Mason`

## Key Keybindings

| Keymap | Description |
|--------|-------------|
| `<leader>sf` | Search files (Telescope) |
| `<leader>sg` | Live grep (Telescope) |
| `<leader>sh` | Search help |
| `<leader>sk` | Search keymaps |
| `<leader><leader>` | Find buffers |
| `<leader>/` | Fuzzy search in current buffer |
| `<leader>sn` | Search Neovim config files |
| `<leader>f` | Format buffer (conform.nvim) |
| `<leader>tt` | Open terminal in bottom split |
| `\` | Toggle Neo-tree file explorer |
| `grn` | LSP: Rename |
| `gra` | LSP: Code action |
| `grr` | LSP: Go to references |
| `grd` | LSP: Go to definition |
| `gri` | LSP: Go to implementation |
| `<leader>th` | Toggle inlay hints |
| `<C-h/j/k/l>` | Navigate between splits |

## Adding New Plugins

Add plugin specs to `lua/custom/plugins/init.lua` or create new files in `lua/custom/plugins/`. Files are auto-imported.

## Adding LSP Servers

Add server names to the `servers` table in `init.lua` (around line 692). Example:
```lua
local servers = {
  lua_ls = { ... },
  pyright = {},
  ts_ls = {},
}
```

Mason will auto-install configured servers.

## Health Check

Run `:checkhealth` to diagnose configuration issues. The custom health check is in `lua/kickstart/health.lua`.
