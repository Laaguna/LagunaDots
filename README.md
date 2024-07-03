# LagunaDots Nvim :)

## Descripción

Este repositorio tiene configuraciones personalizadas para el desarrollo en un entorno de nvim, incluye plugins y keymaps especifimos para mejorar la productividad. Usa [LazyVim](https://github.com/LazyVim/LazyVim) como pre-configuración con un set de plugins para simplificar el uso de Nvim.
## Primeros pasos

### Instalar Iosevka Term Nerd Font o Nerd Font que más te guste [NerdFonts](https://www.nerd-fonts.com/fonts-downloads)

`https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/IosevkaTerm.zip`

### Instalar WezTerm

```bash
https://wezfurlong.org/wezterm/installation.html
```

### Configuration Transfer

#### Crea una carpeta de configuración para Wezterm si estás en MAC / LINUX

```bash
cd ~/.config
mkdir wezterm
cd wezterm
mkdir wezterm.lua
```

#### Transfer

```bash
git clone https://github.com/Laaguna/LagunaDots

Mac / Linux
cp -r LagunaDots/.wezterm.lua ~/.config/wezterm

Windows
RUN ON POWESHELL
cp -r LagunaDots/.wezterm.lua %userprofile%


Uncomment the lines under -- activate ONLY if windows --

-- config.default_domain = 'WSL:Ubuntu'
-- config.front_end = "WebGpu"
-- config.max_fps = 120
-- for _, gpu in ipairs(wezterm.gui.enumerate_gpus()) do
-- if gpu.backend == "Vulkan" then
--   config.webgpu_preferred_adapter = gpu
--   break
--  end
-- end

```

## Archivo `.wezterm.lua`

Configuración con los colores y ajustes para usar Wezterm como tu terminal por defecto.



### Instalar WSL (`https://learn.microsoft.com/en-us/windows/wsl/install`)

```bash
wsl --install
wsl --set-default-version 2
```



### Instalar HomeBrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

// Si no funciona, intenta usar
set install_script (curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)
```

#### Incluir HomeBrew en el Path

```bash
Cambia 'TuUsuario' con el nombre de usuario tuyo.

(echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/TuUsuario/.bashrc
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

### Instalar build-essencials para LINUX

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

### Instalar NVIM

```bash
brew install nvim
```

### Instalar NODE & NPM

```bash
brew install node
brew install npm
```

### Instalar GIT

```bash
brew install git
```



## Carpeta `LagunaFish`

### Instalación de Fish

#### HomeBrew (Recomendado)

Instalar HomeBrew: `https://brew.sh/`

`brew install fish`

#### Ubuntu/Debian

```
sudo apt-get update
sudo apt-get install fish
```

#### Fedora

`sudo dnf install fish`

### Instalación de Oh My Fish 

`curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish`

### Copiar toda la configuración de LagunaFish a tu "./config"

```bash
git clone https://github.com/Laaguna/LagunaDots
cp -r LagunaDots/LagunaFish/* ~/.config
```

### Configuración de PJ plugin en Oh My Fish

Corre `omf install pj`

Ve al archivo `~/.config/fish/fish_variables` y cambia la siguiente variable a la ruta de tus proyectos:

`SETUVAR --export PROJECT_PATHS: /TuRutaDeProyectos`

Mas información: `https://github.com/oh-my-fish/plugin-pj`


### Escoge el tema Everforest para fish

Corre: `fish_config theme save Everforest`




### Instalar las siguientes dependecias 

```bash
brew install gcc
brew install fzf
brew install fd
brew install ripgrep
```



## Carpeta `LagunaZellij`

Contiene la configuración de Zellij. Para instlar y usar, sigue estos pasos: 

### Instalación de Zellij

#### HomeBrew (Recommended)

`brew install zellij`

### Copiar toda la configuración de LagunaZellij a tu "./config"

```bash
git clone https://github.com/Laaguna/LagunaDots
cp -r LagunaDots/LagunaZellij/* ~/.config
```

### Explicación del plugin

#### zellij_forgot.wasm

¿Olvidaste tus atajos? Solo presiona `Alt + y` y podrás buscar el comando que necesitas.

#### zjstatus.wasm

Barra de status usada en esta configuración, puedes verla en `zellij/layouts/work.kdl`




## Caperta `LagunaNvim`

### Copiar toda la configuración de LagunaNvim a tu "./config"

```bash
git clone https://github.com/Laaguna/LagunaDots
cp -r LagunaDots/LagunaNvim/* ~/.config
```

Reinicia Nvim para aplicar los cambios.

### Importante

Algunas personas, tiene problemas al ejecutar Nvim después de hacer el script de transferencia, la forma de solucionarlo es eliminar ```harpoon.lua```, abrir nvim, y luego agregar el plugin de nuevo.

### Carpeta `plugins`

#### Archivo `codeium.lua`

This file configures the [codeium.vim](https://github.com/Exafunction/codeium.vim) plugin, providing keyboard shortcuts for accepting, completing, and clearing suggestions.

```lua
return {
  "Exafunction/codeium.vim",
  config = function()
    vim.keymap.set("i", "<C-g>", function()
      return vim.fn["codeium#Accept"]()
    end, { expr = true })

    vim.keymap.set("i", "<C-l>", function()
      return vim.fn["codeium#CycleCompletions"](1)
    end, { expr = true })

    vim.keymap.set("i", "<C-M>", function()
      return vim.fn["codeium#Complete"]()
    end, { expr = true })

    vim.keymap.set("i", "<C-x>", function()
      return vim.fn["codeium#Clear"]()
    end, { expr = true })
  end,
}
```

#### File `vim-tmux-navigation.lua`

This file configures the [nvim-tmux-navigation.vim](https://github.com/alexghergh/nvim-tmux-navigation) plugin, providing keyboard shortcuts for navigating between tmux and nvim in an optimal way.

```lua
return {
  "alexghergh/nvim-tmux-navigation",
}
```

#### File `typescript-tools.lua`

This file configures the [typescript-tools.nvim](https://github.com/pmizio/typescript-tools.nvim) plugin, providing native Tsserver communication protocol with pure lua.

```lua
return {
  "pmizio/typescript-tools.nvim",
  dependencies = { "nvim-lua/plenary.nvim", "neovim/nvim-lspconfig" },
  opts = {},
}
```

#### File `markdown-preview.lua`

This file configures the plugin [markdown-preview](https://github.com/iamcco/markdown-preview.nvim). To preview a mkd file, do `:MarkdownPreview`.

```lua
return {
  "iamcco/markdown-preview.nvim",
  cmd = { "MarkdownPreviewToggle", "MarkdownPreview", "MarkdownPreviewStop" },
  ft = { "markdown" },
  build = function()
    vim.fn["mkdp#util#install"]()
  end,
}
```

#### File `fugitive.lua`

This file configures the plugin [vim-fugitive](https://github.com/tpope/vim-fugitive) for git management without leaving NVIM.

```lua
return {
  "https://github.com/tpope/vim-fugitive",
}
```

#### File `colorscheme.lua`

This file configures the color scheme using the [nvim](https://github.com/catppuccin/nvim) plugin. The "everforest" theme with specific options is chosen. You can also choose catppucin or modus by changing the property `colorscheme = "everforest"`. If you want a transparent background, use `:TransparentEnable`, and NVIM will have extra opacity according to your terminal settings.

```lua
return {
  {
    "catppuccin/nvim",
    name = "catppuccin",
    lazy = false,
    opts = {
      transparent_background = true,
      flavour = "mocha",
    },
    integrations = {
      cmp = true,
      gitsigns = true,
      nvimtree = true,
      treesitter = true,
      notify = false,
      mini = {
        enabled = true,
        indentscope_color = "",
      },
      -- For more plugins integrations please scroll down (https://github.com/catppuccin/nvim#integrations)
    },
  },
  {
    "miikanissi/modus-themes.nvim",
    name = "modus",
    priority = 1000,
  },
  {
    "rebelot/kanagawa.nvim",
    name = "kanagawa",
    priority = 1000,
    opts = {
      overrides = function(colors)
        local theme = colors.theme
        return {
          NormalFloat = { bg = "none" },
          FloatBorder = { bg = "none" },
          FloatTitle = { bg = "none" },

          NormalDark = { fg = theme.ui.fg_dim, bg = theme.ui.bg_m3 },

          LazyNormal = { bg = theme.ui.bg_m3, fg = theme.ui.fg_dim },
          MasonNormal = { bg = theme.ui.bg_m3, fg = theme.ui.fg_dim },

          TelescopeTitle = { fg = theme.ui.special, bold = true },
          TelescopePromptNormal = { bg = theme.ui.bg_p1 },
          TelescopePromptBorder = { fg = theme.ui.bg_p1, bg = theme.ui.bg_p1 },
          TelescopeResultsNormal = { fg = theme.ui.fg_dim, bg = theme.ui.bg_m1 },
          TelescopeResultsBorder = { fg = theme.ui.bg_m1, bg = theme.ui.bg_m1 },
          TelescopePreviewNormal = { bg = theme.ui.bg_dim },
          TelescopePreviewBorder = { bg = theme.ui.bg_dim, fg = theme.ui.bg_dim },

          Pmenu = { fg = theme.ui.shade0, bg = theme.ui.bg_p1 }, -- add `blend = vim.o.pumblend` to enable transparency
          PmenuSel = { fg = "NONE", bg = theme.ui.bg_p2 },
          PmenuSbar = { bg = theme.ui.bg_m1 },
          PmenuThumb = { bg = theme.ui.bg_p2 },
        }
      end,
    },
  },
  { "rose-pine/neovim", name = "rose-pine" },
  { "nyoom-engineering/oxocarbon.nvim", name = "oxocarbon" },
  { "rktjmp/lush.nvim", dependencies = { "mcchrish/zenbones.nvim" } },
  {
    "scottmckendry/cyberdream.nvim",
    lazy = false,
    priority = 1000,
  },
  { "NTBBloodbath/doom-one.nvim", name = "doom-one" },
  { "AhmedAbdulrahman/aylin.vim", name = "aylin" },
  {
    "xiyaowong/transparent.nvim",
  },
  {
    "neanias/everforest-nvim",
    version = false,
    lazy = false,
    priority = 1000, -- make sure to load this before all the other start plugins
    -- Optional; default configuration will be used if setup isn't called.
    config = function()
      require("everforest").setup({
        -- Your config here
      })
    end,
  },
  {
    "LazyVim/LazyVim",
    opts = {
      colorscheme = "everforest",
    },
  },
}
```

#### File `editor.lua`

This file configures various plugins to enhance the editing experience, such as highlighting patterns in Markdown files and advanced search tools with Telescope.

```lua
1. **mini.hipatterns**:
   - Plugin: `echasnovski/mini.hipatterns`
   - Event: `BufReadPre`
   - Configuration:
     - Configures a highlighter for HSL colors. HSL colors in the code will be highlighted with a background color corresponding to the HSL color.

2. **git.nvim**:
   - Plugin: `dinhhuy258/git.nvim`
   - Event: `BufReadPre`
   - Configuration:
     - Configures keyboard shortcuts to open a blame window (`<Leader>gb`) and to open a file or folder in the Git repository (`<Leader>go`).

3. **telescope.nvim**:
   - Plugin: `telescope.nvim`
   - Dependencies: `nvim-telescope/telescope-fzf-native.nvim` and `nvim-telescope/telescope-file-browser.nvim`
   - Configuration:
     - Configures a series of keyboard shortcuts for various functionalities, such as searching for files, searching for a string in the current directory, listing open buffers, listing help tags, and resuming the previous telescope picker.
     - Also configured to open a file browser with the path of the current buffer with `<Leader>sf`.
   - Additional Configuration:
     - Configures results to wrap, layout strategy to be horizontal, prompt position at the top, and sorting strategy to be ascending.
     - Configures the diagnostics selector to have the "ivy" theme, initial mode to be "normal", and preview cutoff to be 9999.
     - Configures the file browser to have the "dropdown" theme, hijack netrw and use it instead, and have its own mappings.
```

#### File `harpoon.lua`

This file configures the [harpoon](https://github.com/ThePrimeagen/harpoon) plugin to facilitate navigation between marked files.

```lua
return {
  "ThePrimeagen/harpoon",
  lazy = false,
  dependencies = {
    "nvim-lua/plenary.nvim",
  },
  branch = "harpoon2",
  config = true,
}
```

#### File `oil.lua`

A vim-vinegar like file explorer that lets you edit your filesystem like a normal Neovim buffer.

```lua
return {
  "stevearc/oil.nvim",
  opts = {},
  -- Optional dependencies
  dependencies = { "nvim-tree/nvim-web-devicons" },
}

-- to use press "-"
```

#### File `telescope.lua`

This file configures the [Telescope](https://github.com/nvim-telescope/telescope.nvim) plugin for advanced searches in files and other resources.
It also includes the "telescope-life-grep-args" plugin which adds the possibility of adding arguments to live grep ";r"

```lua
return {
  "nvim-telescope/telescope.nvim",
  opts = {
    defaults = {
      layout_strategy = "vertical",
      layout_config = { preview_cutoff = 6 },
    },
  },
  dependencies = {
    {
      "nvim-telescope/telescope-live-grep-args.nvim",
      -- This will not install any breaking changes.
      -- For major updates, this must be adjusted manually.
      version = "^1.0.0",
    },
  },
  config = function()
    require("telescope").load_extension("live_grep_args")
  end,
}
```

#### File `ui.lua`

This file configures various plugins to enhance the user interface, including notifications, animations, buffer lines, and status lines.

```lua
1. **Noice.nvim**:
   - Plugin: `folke/noice.nvim`
   - Configuration:


     - Adds a path to the noice configuration to filter notification messages with the text "No information available". These messages will be skipped.
     - Sets autocmds to detect when the Neovim window gains or loses focus. This is used to determine if the interface is focused or not.
     - Adds an additional path to display system notifications when Neovim loses focus.

2. **Nvim-notify**:
   - Plugin: `rcarriga/nvim-notify`
   - Configuration:
     - Sets the background color and timeout for notifications.

3. **Mini.animate**:
   - Plugin: `echasnovski/mini.animate`
   - Configuration:
     - Disables the scroll animation (`scroll`).

4. **Bufferline.nvim**:
   - Plugin: `akinsho/bufferline.nvim`
   - Configuration:
     - Defines keyboard shortcuts to switch between tabs.
     - Configures options to show icons and close tabs.

5. **Lualine.nvim**:
   - Plugin: `nvim-lualine/lualine.nvim`
   - Configuration:
     - Configures the "catppuccin" theme for the status line.

6. **Incline.nvim**:
   - Plugin: `b0o/incline.nvim`
   - Configuration:
     - Configures colors and visual options for highlighting file names in the status line.

7. **Zen-mode.nvim**:
   - Plugin: `folke/zen-mode.nvim`
   - Configuration:
     - Configures keyboard shortcuts to activate "Zen Mode," which hides UI elements to focus on text editing.

8. **Dashboard-nvim**:
   - Plugin: `nvimdev/dashboard-nvim`
   - Configuration:
     - Sets a custom logo for the Neovim startup dashboard.
```

#### File `keymaps.lua`

This file defines some custom keymaps to improve navigation, text manipulation in insert mode and plugin shortcuts.

```lua
-- Keymaps are automatically loaded on the VeryLazy event
-- Default keymaps that are always set: https://github.com/LazyVim/LazyVim/blob/main/lua/lazyvim/config/keymaps.lua Add any additional keymaps here

vim.keymap.set("i", "<C-d>", "<C-d>zz")
vim.keymap.set("i", "<C-u>", "<C-u>zz")
vim.keymap.set("i", "<C-b>", "<C-o>de")

----- Tmux Navigation ------
local nvim_tmux_nav = require("nvim-tmux-navigation")

vim.keymap.set("n", "<C-h>", nvim_tmux_nav.NvimTmuxNavigateLeft)
vim.keymap.set("n", "<C-j>", nvim_tmux_nav.NvimTmuxNavigateDown)
vim.keymap.set("n", "<C-k>", nvim_tmux_nav.NvimTmuxNavigateUp)
vim.keymap.set("n", "<C-l>", nvim_tmux_nav.NvimTmuxNavigateRight)
vim.keymap.set("n", "<C-\\>", nvim_tmux_nav.NvimTmuxNavigateLastActive)
vim.keymap.set("n", "<C-Space>", nvim_tmux_nav.NvimTmuxNavigateNext)

-- REQUIRED
local harpoon = require("harpoon")
local oil = require("oil")
harpoon:setup()
oil.setup()
-- REQUIRED

-----  OIL -----
vim.keymap.set("n", "-", "<CMD>Oil<CR>", { desc = "Open parent directory" })

-- Delete all buffers but the current one --
vim.keymap.set(
  "n",
  "<leader>bq",
  '<Esc>:%bdelete|edit #|normal`"<Return>',
  { desc = "Delete other buffers but the current one" }
)

----- HARPOON 2 -----
vim.keymap.set("n", "<leader>a", function()
  harpoon:list():append()
end, { desc = "Add harpoon mark" })

vim.keymap.set("n", "<C-e>", function()
  harpoon.ui:toggle_quick_menu(harpoon:list())
end)

vim.keymap.set("n", "<C-M-h>", function()
  harpoon:list():select(1)
end)

vim.keymap.set("n", "<C-M-j>", function()
  harpoon:list():select(2)
end)

vim.keymap.set("n", "<C-M-k>", function()
  harpoon:list():select(3)
end)

vim.keymap.set("n", "<C-M-l>", function()
  harpoon:list():select(4)
end)

-- Disable key mappings in insert mode
vim.api.nvim_set_keymap("i", "<A-j>", "<Nop>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("i", "<A-k>", "<Nop>", { noremap = true, silent = true })

-- Disable key mappings in normal mode
vim.api.nvim_set_keymap("n", "<A-j>", "<Nop>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("n", "<A-k>", "<Nop>", { noremap = true, silent = true })

-- Disable key mappings in visual block mode
vim.api.nvim_set_keymap("x", "<A-j>", "<Nop>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("x", "<A-k>", "<Nop>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("x", "J", "<Nop>", { noremap = true, silent = true })
vim.api.nvim_set_keymap("x", "K", "<Nop>", { noremap = true, silent = true })
```







