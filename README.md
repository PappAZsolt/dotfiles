# Linux

A dotfile of my Xfce config

# Vim Config

---

```bash
set cursorline
highlight Visual cterm=NONE ctermbg=236 ctermfg=NONE guibg=Grey40

highlight LineNr cterm=none ctermfg=240 guifg=#2b506e guibg=#000000
set clipboard=unnamedplus
syntax on 
filetype plugin indent on
set ts=2 sts=2 sw=2 et ai si nu

" Reference chart of values:
"   Ps = 0  -> blinking block.
"   Ps = 1  -> blinking block (default).
"   Ps = 2  -> steady block.
"   Ps = 3  -> blinking underline.
"   Ps = 4  -> steady underline.
"   Ps = 5  -> blinking bar (xterm).
"   Ps = 6  -> steady bar (xterm).
let &t_SI = "\e[6 q"
let &t_EI = "\e[2 q"

" /////////////////////////////////////////////////////////////////////////////
"        _             _
"  _ __ | |_   _  __ _(_)_ __  ___
" | '_ \| | | | |/ _` | | '_ \/ __|
" | |_) | | |_| | (_| | | | | \__ \
" | .__/|_|\__,_|\__, |_|_| |_|___/
" 
" |_|            |___/
" /////////////////////////////////////////////////////////////////////////////
" // All the cool kids are using these.
" /////////////////////////////////////////////////////////////////////////////

                                                                  " ╭─────────────────╮╭───────────────────────────────────────────────────────╮
call plug#begin('~/.vim/plugged')                                 " │ Pluggin         ││ Description                                           │
                                                                  " │─────────────────││───────────────────────────────────────────────────────│
" Appearance                                                      " │                 ││                                                       │
Plug 'vim-airline/vim-airline'                                    " │ Airline         ││ Lean & mean status and tabline                        │
                                                                  " │                 ││                                                       │
" Accessibility                                                   " │                 ││                                                       │
Plug 'preservim/nerdtree'                                         " │ NERDTree        ││ Tree Explorer for vim                                 │
Plug 'neoclide/coc.nvim', {'branch': 'release'}                   " │ Coc.nvim        ││ Senses for your vim, using language servers           │
Plug 'jiangmiao/auto-pairs'

call plug#end()

"     _       __             _ _
"  __| | ___ / _| __ _ _   _| | |_ ___
" / _` |/ _ \ |_ / _` | | | | | __/ __|
"| (_| |  __/  _| (_| | |_| | | |_\__ \
" \__,_|\___|_|  \__,_|\__,_|_|\__|___/
" -----------------------------------
" These are the set of "sane defaults" that people on the internet have agreed
" upon.

" Sanity
set splitbelow                          " │ Horizontal split will put the new window below the current                    │
set splitright                          " │ Vertical split will put the new window to the right                           │
set noerrorbells                        " │ Don't like any ring and dangling in my earball                                │
set autoread                            " │ Autoread the file when the file is externally modified                        │

" Appearance & feels                      ╭───────────────────────────────────────────────────────────────────────────────╮
set background=dark                     " │ Notify the nvim that background color of terminal is dark                     │
set title                               " │ Set the title of the window to titlestring                                    │
                                        " ╰───────────────────────────────────────────────────────────────────────────────╯

"use <tab> for trigger completion and navigate to the next complete item
function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1] =~ '\s'
endfunction

inoremap <silent><expr> <Tab>
\ pumvisible() ? "\<C-n>" :
\ <SID> check_back_space() ? "\Tab":
\ coc#refresh()

"set termguicolors

"  _ __ ___ _ __ ___   __ _ _ __  ___
" | '__/ _ \ '_ ` _ \ / _` | '_ \/ __|
" | | |  __/ | | | | | (_| | |_) \__ \
" |_|  \___|_| |_| |_|\__,_| .__/|___/
"                          |_|
" ------------------------------------

" Window Resizing, change the width of windows using {+, -}
nnoremap + :vertical resize +2<CR>
nnoremap - :vertical resize -2<CR>

" NERDTree configurations
map <C-b> :NERDTreeToggle<CR>
map <C-f> :NERDTreeFind<CR>

" "Tabs Navigation", Use <CTRL> + {j, k} to move backward and forward and CTRL-H
" to go at the first tab and CTRL-L to go at the last tab
map <C-J> :tabprevious<CR>
map <C-K> :tabnext<CR>
map <C-L> :tablast<CR>
map <C-H> :tabfirst<CR>
```

### !!! Make sure to install nodejs and npm for coc to work !!!

```bash
pacman -S nodejs npm
```

### Install Ranger (jump around files)

```bash
sudo pacman -S ranger
```

## If future me is stuck make sure to watch this video:

[https://www.youtube.com/watch?v=7-dfpQ5sexk](https://www.youtube.com/watch?v=7-dfpQ5sexk)

# Picom

---

- Not going to include the full config file here because it’s too long so I’m going to source the tutorial video, installation command and some screenshots.

```bash
yay -S picom-ibhagwan-git
```

[https://www.youtube.com/watch?v=39JPR691yyc&t=617s](https://www.youtube.com/watch?v=39JPR691yyc&t=617s)

![Screenshot](https://user-images.githubusercontent.com/68129312/167709532-3c0a8cab-7996-422c-bc75-84ea02b4181b.png)


# Kitty Terminal

---

## Usage

---

The commands that I use most of the time

```markdown
Ctrl+Shift+Enter - New layout
Ctrl+Shift+{ or } - Cycling between layouts
Ctrl+Shift+W - Closing the layout
Ctrl+Shfit+F or B - Moving the layout forward or backwards
Ctrl+Shift+L or M - Increase or Decrease Background opacity
```

Comand to install Kitty theme

```bash
cp theme.conf ~/.config/kitty/
echo "include theme.conf" >> ~/.config/kitty/kitty.conf
```

# Oh my Zsh

---

- Installation:

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- Install zplug :

```bash
 curl -sL --proto-redir -all,https https://raw.githubusercontent.com/zplug/installer/master/installer.zsh | zsh
```

- ZSH configuration commands:

```bash
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

if [ -f ${HOME}/.zplug/init.zsh ]; then
    source ${HOME}/.zplug/init.zsh
fi
# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

source $ZSH/oh-my-zsh.sh

#zplug "dracula/zsh",as:theme
plugins=(
          git 
          zsh-autosuggestions)

source $ZSH/oh-my-zsh.sh
# Example aliases
alias kittyconfig="vim ~/.config/kitty/kitty.conf"
alias zshconfig="vim ~/.zshrc"
alias ohmyzsh="vim ~/.oh-my-zsh"
alias c="clear"
alias update="sudo pacman -Syu"
alias open="thunar"
alias ls="lsd"
alias e="exit"
alias restart="exec terminator"
alias fish="asciiquarium"
alias norm="wmctrl -r :ACTIVE: -e 0,-1,-1,800,800"
alias fat="wmctrl -r :ACTIVE: -e 0,-1,-1,1200,850"
alias slim="wmctrl -r :ACTIVE: -e 0,-1,-1,650,800"
alias mid="wmctrl -r :ACTIVE: -e 0,550,100,-1,-1"
alias right="wmctrl -r :ACTIVE: -e 0,1200,100,-1,-1"
alias left="wmctrl -r :ACTIVE: -e 0,100,100,-1,-1"
alias untar="tar xvf"
alias files="ranger"
alias nvimconfig="cd /home/pappz/.config/nvim/"
alias picomconfig="vim ~/.config/picom/picom.conf"
source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme

# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
```

- Install zsh-autosuggestions:

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

## Powerlevel10k

---

- Installation :

```bash
yay -S --noconfirm zsh-theme-powerlevel10k-git
echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
p10k configure
```

## XFCE Configuration with theme/icon/dock

[https://www.youtube.com/watch?v=TAWwJoYWq6s&t=964s](https://www.youtube.com/watch?v=TAWwJoYWq6s&t=964s)
