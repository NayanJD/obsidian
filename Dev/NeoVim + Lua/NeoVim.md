#editor

My NeoVim config uses `NvChad/NvChad` as base.

## Highlighting 

I am using `nvim-treesitter/nvim-treesitter`. It basically adds highlighting grammar for different languages. It is based out of Treesitter which is a language parser written in Rust.

## LSPs 

Neovim supports the Language Server Protocol (LSP), which means it acts as a client to a LSP Servers and includes a Lua Framework vim.lsp for building enhaces LSP tools. Nvim provides an LSP Client, but the servers are provided by third parties.

`nvim-lspconfig` provides default client configuration for all languages. 

I am using `mason.nvim` to automatically install LSP Servers, DAP servers, linters and formatters. `mason-lspconfig` is a companion plugin to `mason.nvim` to let install different LSP server like `gopls` etc.

## Formatting

`stevearc/conform.nvim` is used to add formatters for different languages.


### Debuggers

`mfussenegger/nvim-dap` is being used as base for debugging in nvim. `leoluz/nvim-dap-go` provided useful commands to run `delve` debugger and also run debugger for specific tests.

#### Completion and Snippets

`hrsh7th/nvim-cmp` is being used with `L3MON4D3/LuaSnip` engine along with others. `rafamadriz/friendly-snippets` is used as languages' snippets source for luasnip.

#### How To add support for a new language 

Here are steps if a new language is added:

1. Find the language server from the [mason-lspconfig](https://github.com/williamboman/mason-lspconfig.nvim?tab=readme-ov-file#available-lsp-servers) repo or by running `MasonInstallAll`.
2. Add the language server in the `williamboman/mason-lspconfig.nvim` block in `lua/plugins/init.lua` file. This is for future installation. Run `MasonInstall <lsp server name>`.
3. Add the language server name in `lua/configs/lspconfig.lua` in the array in this line:
```
local servers = { "html", "cssls", "gopls" }
```
