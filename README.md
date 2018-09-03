# vimset nocompatible
" set the runtime path to include Vundle and initialize
" set rtp+=~/.vim/bundle/Vundle.vim
" call vundle#begin()
" " alternatively, pass a path where Vundle should install plugins
" "call vundle#begin('~/some/path/here')
"
" " let Vundle manage Vundle, required
" Plugin 'VundleVim/Vundle.vim'
"
" " The following are examples of different formats supported.
" " Keep Plugin commands between vundle#begin/end.
" " plugin on GitHub repo
" Plugin 'tpope/vim-fugitive'
" " plugin from http://vim-scripts.org/vim/scripts.html
" " Plugin 'L9'
" " Git plugin not hosted on GitHub
" Plugin 'git://git.wincent.com/command-t.git'
" " git repos on your local machine (i.e. when working on your own plugin)
" Plugin 'file:///home/gmarik/path/to/plugin'
" " The sparkup vim script is in a subdirectory of this repo called vim.
" " Pass the path to set the runtimepath properly.
" Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" " Install L9 and avoid a Naming conflict if you've already installed a
" " different version somewhere else.
" " Plugin 'ascenator/L9', {'name': 'newL9'}
"
" " All of your Plugins must be added before the following line
" call vundle#end()            " required
" filetype plugin indent on    " required
" " To ignore plugin indent changes, instead use:
" "filetype plugin on
" "
" " Brief help
" " :PluginList       - lists configured plugins
" " :PluginInstall    - installs plugins; append `!` to update or just
" :PluginUpdate
" " :PluginSearch foo - searches for foo; append `!` to refresh local cache
" " :PluginClean      - confirms removal of unused plugins; append `!` to
" auto-approve removal
" "
" " see :h vundle for more details or wiki for FAQ
" " Put your non-Plugin stuff after this line
filetype on

" Load Vindle
" Type :source % (Noob)
" Type :PluginInstall (Noob)
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Plugin 'hashivim/vim-terraform'
Plugin 'stephpy/vim-yaml'
Plugin 'gmarik/Vundle.vim'
Plugin 'tmhedberg/SimpylFold'
"Plugin 'vim-scripts/indentpython.vim'
Plugin 'ntpeters/vim-better-whitespace'
Plugin 'scrooloose/nerdtree'
Plugin 'jistr/vim-nerdtree-tabs'
"Plugin 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
Plugin 'ekalinin/Dockerfile.vim'
Plugin 'scrooloose/syntastic'
Plugin 'rodjek/vim-puppet'
Bundle 'chase/vim-ansible-yaml'
Bundle 'https://github.com/m-kat/aws-vim'
Bundle "MarcWeber/vim-addon-mw-utils"
Bundle "tomtom/tlib_vim"
Bundle "garbas/vim-snipmate"
Bundle "vadv/vim-chef"
Plugin 'elzr/vim-json'
Plugin 'https://github.com/vim-scripts/groovy.vim.git'
Plugin 'Yggdroot/indentline'
Plugin 'hdima/python-syntax'
Plugin 'martinda/Jenkinsfile-vim-syntax'
Bundle 'vim-ruby/vim-ruby'
Plugin 'airblade/vim-gitgutter'
call vundle#end()
"
" Enable Syntax Highlight
syntax on
" Enable Indentation
filetype plugin indent on

" Defaults
set tabstop=2
set softtabstop=0 expandtab
set shiftwidth=2 smarttab

" Setup NerdTree Stuff
autocmd vimenter * NERDTree
autocmd vimenter * wincmd p
autocmd BufWinEnter * NERDTreeMirror
let NERDTreeShowHidden=1
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

" Setup Python Stuff
au BufNewFile,BufRead *.py
    \ set tabstop=4 |
    \ set softtabstop=4 |
    \ set shiftwidth=4 |
    \ set textwidth=79 |
    \ set expandtab |
    \ set autoindent |
    \ set fileformat=unix
set encoding=utf-8

" Setup Syntastic Stuff
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

autocmd FileType yaml setlocal ts=2 sts=2 sw=2 expandtab

autocmd BufRead,BufNewFile *.md setlocal spell
autocmd FileType gitcommit setlocal spell
let g:indentLine_enabled = 1
let g:indentLine_setColors = 0

nnoremap <F2> :set invpaste paste?<CR>
set pastetoggle=<F2>
set showmode
"set spellfile to location that is guaranteed to exist, can be symlinked to
" Dropbox or kept in Git and managed outside of thoughtbot/dotfiles using rcm.
 set spellfile=$HOME/.vim-spell-en.utf-8.add
"
" " Autocomplete with dictionary words when spell check is on
 set complete+=kspell
"
" " Always use vertical diffs
set diffopt+=vertical

" " Local config
 if filereadable($HOME . "/.vimrc.local")
   source ~/.vimrc.local
 endif
