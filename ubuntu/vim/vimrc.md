### 我在ubuntu下的vim配置文件

" All system-wide defaults are set in $VIMRUNTIME/debian.vim (usually just
" /usr/share/vim/vimcurrent/debian.vim) and sourced by the call to :runtime
" you can find below.  If you wish to change any of those settings, you should
" do it in this file (/etc/vim/vimrc), since debian.vim will be overwritten
" everytime an upgrade of the vim packages is performed.  It is recommended to
" make changes after sourcing debian.vim since it alters the value of the
" 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
if has("syntax")
  syntax on
endif

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules and plugins
" according to the detected filetype.
"if has("autocmd")
"  filetype plugin indent on
"endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set smartcase		" Do smart case matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make
"set hidden             " Hide buffers when they are abandoned
"set mouse=a		" Enable mouse usage (all modes)

" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif


" This is my _vimrc under windows platform
" and it can be used on *nix too
" all the difference of them is the font setting session
" happy Viming,
" copyLeft (#) Abruzzi John

set linebreak " line break
set nocompatible " no compatible
set history=400 " history
set ruler
set number " line number
set hlsearch " highlight search
set noincsearch " no in C search
set expandtab " expand table
set t_vb= "close bell
set foldmethod=marker
set tabstop=4 " table step
set shiftwidth=4
set nobackup " don't backup
set smarttab " smart table
set smartindent " smart indent
set autoindent " auto indent
set cindent "cindent
set cursorline " hightlight cursor line 高亮光标所在行

colorscheme desert " color scheme

let Tlist_Use_Right_Window=0 " for tag_list plugin only
let Tlist_File_Fold_Auto_Close=1 " for tag_list plugin only

let g:winManagerWindowLayout="FileExplorer|TagList" " for winmanager

filetype plugin indent on " filetype setting
set completeopt=longest,menu " for code complete

" the following function is used for show the status bar on the buttom
function! CurrectDir()
let curdir = substitute(getcwd(), "", "", "g")
return curdir
endfunction
set statusline=\ [File]\ %F%m%r%h\ %w\ \ [PWD]\ %r%{CurrectDir()}%h\ \ %=[Line]\ %l,%c\ %=\ %P

" make sure that syntax always on
if exists("syntax_on")
syntax reset
else
syntax on
endif

""""""""""""""""""""""""""""""""""""""""""""""""""""""
let performance_mode=1

" set auto read when file is changed from outside
if exists("&autoread")
set autoread
endif

" set mapleader
let mapleader=","
let g:mapleader=","

"设置字符集 
set encoding=utf-8
set fileencodings=utf-8,cp936
set fileencoding=utf-8
set termencoding=utf-8

