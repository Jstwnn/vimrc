source $VIMRUNTIME/vimrc_example.vim
source $VIMRUNTIME/mswin.vim
behave mswin

set diffexpr=MyDiff()
function MyDiff()
  let opt = '-a --binary '
  if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif
  if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif
  let arg1 = v:fname_in
  if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
  let arg2 = v:fname_new
  if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
  let arg3 = v:fname_out
  if arg3 =~ ' ' | let arg3 = '"' . arg3 . '"' | endif
  if $VIMRUNTIME =~ ' '
    if &sh =~ '\<cmd'
      if empty(&shellxquote)
        let l:shxq_sav = ''
        set shellxquote&
      endif
      let cmd = '"' . $VIMRUNTIME . '\diff"'
    else
      let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
    endif
  else
    let cmd = $VIMRUNTIME . '\diff'
  endif
  silent execute '!' . cmd . ' ' . opt . arg1 . ' ' . arg2 . ' > ' . arg3
  if exists('l:shxq_sav')
    let &shellxquote=l:shxq_sav
  endif
endfunction
"""""""""""""""""""""""""""""""

"""""""""""""""""""""""""""""""
" Specify a directory for plugins (for Neovim: ~/.local/share/nvim/plugged)
call plug#begin('~/.vim/plugged')

" Make sure you use single quotes

" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

" Any valid git URL is allowed
"Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" Multiple Plug commands can be written in a single line using | separators
""Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets
Plug 'honza/vim-snippets'

" On-demand loading
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
"Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-master branch
"Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
"Plug 'fatih/vim-go', { 'tag': '*' }

" Plugin options
"Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
"Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
"Plug '~/my-prototype-plugin'

" ++++++++++++++++++++++++++++++++++++++++++++++++ "
Plug 'flazz/vim-colorschemes'
Plug 'majutsushi/tagbar'
Plug 'vim-scripts/taglist.vim'
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'kien/ctrlp.vim'
Plug 'davidhalter/jedi'
Plug 'davidhalter/jedi-vim'
Plug 'Yggdroot/indentLine'
Plug 'vim-syntastic/syntastic'
Plug 'vim-scripts/vim-gitgutter'
Plug 'yegappan/mru'
""""""""""""""""""""""""""""""""""""""""""""""""""""

" Initialize plugin system
call plug#end()
""""""""""""""""""""""""""""""""
"colorscheme torte
"colorscheme molokai
"colorscheme codeschool
"colorscheme solarized
"colorscheme atom-dark
"colorscheme Benokai
"colorscheme candyman
"colorscheme holokai
colorscheme lxvc

"set guifont=Consolas_for_Powerline:h10
"set guifont=Consolas:h11

""""""""""""""""""""""""""""""""
if has("gui_running")
au GUIEnter * simalt ~x " Max Window on starting
"set guioptions-=m " Hide Menubar
set guioptions-=T " Hide Toolbar
"set guioptions-=L " Hide Left-scroller
"set guioptions-=r " Hide Right-scroller
"set guioptions-=b " Hide Bottom-scroller
"set showtabline=0 " Hide Tab-menu
endif
""""""""""""""""""""""""""""""""


""""""""""""""""""""""""""""""""
"let mapleader='t'
let mapleader="\<Space>"

"set cuc
set cul
set fillchars+=vert:\|
hi vertsplit guifg=fg guibg=bg

" Set for 80 characters
"highlight ColorColumn ctermbg=235 guibg=#252627
"let &colorcolumn=join(range(81,999),",")
let &colorcolumn="80,".join(range(120,999),",")

"highlight OverLength ctermbg=red ctermfg=white guibg=#592929
"match OverLength /\%81v.\+/

" Indent lines
set expandtab "Use softtabstop spaces instead of tab characters for indentation
set shiftwidth=4 "Indent by 4 spaces when using >>, <<, == etc.
set softtabstop=4 "Indent by 4 spaces when pressing <TAB>
let g:indentLine_char = '¦'
let g:indentLine_concealcursor = 'inc'
let g:indentLine_conceallevel = 1


" NERDTree
"nn <silent><F2> :exec("NERDTree ".expand('%:h'))<CR>
nmap <Leader>f :NERDTreeFind<CR>
nmap <Leader>q :NERDTreeToggle<CR>
nmap <Leader><Leader> :NERDTreeToggle \|:TagbarToggle <CR>


" Tagbar
let g:tagbar_width=30
nmap <Leader>w :TagbarToggle<CR>
"nmap <Leader>g:TlistToggle<CR>


" Syntastic
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
"let g:syntastic_check_on_open = 1
let g:syntastic_check_on_open = 0
let g:syntastic_check_on_wq = 0

"let g:syntastic_python_checkers = ['pylint', 'flake8']
let g:syntastic_python_checkers = ['pylint']

let g:syntastic_error_symbol = '×' 
let g:syntastic_warning_symbol = '! ' 
"let g:syntastic_warning_symbol = '~ ' 
let g:syntastic_style_error_symbol = '×' 
let g:syntastic_style_warning_symbol = '! ' 
"let g:syntastic_style_warning_symbol = '~ ' 

let g:syntastic_loc_list_height = 5

"map  :SyntasticCheck<CR>
"nmap <Leader>s :SyntasticCheck<CR>
nmap <Leader>s :SyntasticToggleMode<CR>

" Air-line
source $VIMRUNTIME/delmenu.vim
source $VIMRUNTIME/menu.vim

"set cuc
"set cul
set t_Co=256
set termencoding=utf-8
set encoding=utf-8
set langmenu=zh_CN.UTF-8

set fileencodings=ucs-bom,utf-8,cp936,gb18030,big5,euc-jp,euc-kr,latin1
set fileencoding=utf-8

nnoremap <C-N> :bn<CR>
nnoremap <C-P> :bp<CR>

"let g:airline_theme="molokai"
"let g:airline_theme="base16"
"let g:airline_theme="solarized"
"let g:airline_theme="jellybeans"
let g:airline_theme="ubaryd"
"let g:airline_theme="understated"

set laststatus=2
let g:bufferline_echo=0

set ambiwidth=double
let g:Powerline_symbols='fancy'

set guifont=Consolas\ for\ Powerline\ FixedD:h10
let g:airline_powerline_fonts = 1
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#buffer_nr_show = 1

let g:airline#extensions#whitespace#enabled = 0
let g:airline#extensions#whitespace#symbol = '!'

if !exists('g:airline_symbols')
    let g:airline_symbols = {}
endif

" Air-line Symbols
" " unicode symbols
"let g:airline_left_sep = '»'
"let g:airline_left_sep = '>>'
"let g:airline_right_sep = '«'
"let g:airline_right_sep = '<<'
let g:airline_symbols.crypt = '⭤'
"let g:airline_symbols.linenr = '⭡'
"let g:airline_symbols.linenr = '⭡'
"let g:airline_symbols.linenr = '⭡'
"let g:airline_symbols.maxlinenr = '¶'
let g:airline_symbols.maxlinenr = ' ~ '
"let g:airline_symbols.maxlinenr = ' ♠'
"let g:airline_symbols.branch = '⭠'
let g:airline_symbols.paste = 'ρ'
"let g:airline_symbols.paste = 'Þ'
"let g:airline_symbols.paste = '∥'
let g:airline_symbols.spell = 'ξ'
let g:airline_symbols.notexists = 'θ'
let g:airline_symbols.whitespace = '-'

" " powerline symbols
"let g:airline_left_sep = '⮀'
"let g:airline_left_alt_sep = '⮁'
"let g:airline_right_sep = '⮂'
"let g:airline_right_alt_sep = '⮃'
"let g:airline_symbols.branch = '⭠'
"let g:airline_symbols.readonly = '⭤'
"let g:airline_symbols.linenr = '⭡'

" " old vim-powerline symbols
let g:airline_left_sep = '⮀'
let g:airline_left_alt_sep = '⮁'
let g:airline_right_sep = '⮂'
let g:airline_right_alt_sep = '⮃'
let g:airline_symbols.branch = '⭠'
let g:airline_symbols.readonly = '⭤'
let g:airline_symbols.linenr = '⭡'

""""""""""""""""""""""""""""""""""""
"""""""""""""  "Quickly Run """""""" 
map <F5> :call CompileRunCode()<CR>
func! CompileRunCode()
    exec "w"
    if &filetype == 'c'
        exec "!gcc % -O %<"
        exec "! .%<"
    elseif &filetype == 'cpp'
        exec "!g++ % -o %<"
        exec "! ./%<"
    elseif &filetype == 'python'
        exec "!python %"
    elseif &filetype == 'sh'
        exec "!bash %"
    elseif &filetype == 'python'
        exec "!firefox % &"
    elseif &filetype == 'go'
        exec "!go run %"
    end if 
endfunc

" Enable folding
set foldmethod=indent
set foldlevel=99

