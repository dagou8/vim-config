""""""""""""""""""""""
"      Settings      "
""""""""""""""""""""""


set number
set pastetoggle=<F2>
" set foldmethod=indent
set tabstop=4
set softtabstop=4
set shiftwidth=4
set noexpandtab
set autoindent
" set fileformats+=dos
" set nofixendofline

" Colorscheme
syntax enable
set t_Co=256
" let g:rehash256 = 1
" let g:molokai_original = 1
colorscheme gruvbox
set background=dark

" let g:indentLine_setColors = 0
let g:indentLine_color_gui = '#454545'

if exists('$VIM_TERMINAL')
  echoerr 'Do not run Vim inside a Vim terminal'
  quit
endif

if has('autocmd')
  " 为了可以重新执行 vimrc，开头先清除当前组的自动命令
  au!
endif

if has('gui_running')
  set guifont=DejaVu_Sans_Mono_for_Powerline:h16
  let do_syntax_sel_menu = 1
  let do_no_lazyload_menus = 1
endif

set enc=utf-8
" set nocompatible
source $VIMRUNTIME/vimrc_example.vim

" 启用 man 插件
source $VIMRUNTIME/ftplugin/man.vim

set fileencodings=ucs-bom,utf-8,gb18030,latin1
set formatoptions+=mM
set keywordprg=:Man
set scrolloff=1
set spelllang+=cjk
set tags=./tags;,tags,/usr/local/etc/systags
set nobackup

if has('persistent_undo')
  set undofile
  set undodir=~/.vim/undodir
  if !isdirectory(&undodir)
    call mkdir(&undodir, 'p', 0700)
  endif
endif

if has('mouse')
  if has('gui_running') || (&term =~ 'xterm' && !has('mac'))
    set mouse=a
  else
    set mouse=nvi
  endif
endif

if !has('gui_running')
  " 设置文本菜单
  if has('wildmenu')
    set wildmenu
    set cpoptions-=<
    set wildcharm=<C-Z>
    nnoremap <F10>      :emenu <C-Z>
    inoremap <F10> <C-O>:emenu <C-Z>
  endif

  " 识别终端的真彩支持
  if has('termguicolors') &&
        \($COLORTERM == 'truecolor' || $COLORTERM == '24bit')
    set termguicolors
  endif
endif

if has('eval')
	" 和 asyncrun 一起用的异步 make 命令
	command! -bang -nargs=* -complete=file Make AsyncRun -program=make @ <args>
endif

if v:version >= 800
  packadd! editexisting
endif


""""""""""""""""""""""
"      Mappings      "
""""""""""""""""""""""

let mapleader = ","
let g:mapleader = ","

" 修改光标上下键一次移动一个屏幕行
nnoremap <Up>        gk
inoremap <Up>   <C-O>gk
nnoremap <Down>      gj
inoremap <Down> <C-O>gj

" 切换窗口的键映
nnoremap <C-Tab>   <C-W>w
inoremap <C-Tab>   <C-O><C-W>w
nnoremap <C-S-Tab> <C-W>W
inoremap <C-S-Tab> <C-O><C-W>W
noremap <C-h> <C-w>h
noremap <C-j> <C-w>j
noremap <C-k> <C-w>k
noremap <C-l> <C-w>l

inoremap <C-d>	<Esc>ddi
inoremap jj <Esc>`^

" sudo to write
cnoremap w!! w !sudo tee % >/dev/null
" json格式化
com! FormatJSON %!python3 -m json.tool

" 切换buffer
nnoremap <silent> [b :bprevious<CR>
nnoremap <silent> [n :bnext<CR>

" 开关 Tagbar 插件的键映射
nnoremap <leader>t :TagbarToggle<CR>
inoremap <leader>t <C-O>:TagbarToggle<CR>



""""""""""""""""""""""
"      Plugings      "
""""""""""""""""""""""

call plug#begin()
Plug 'mhinz/vim-startify'
Plug 'tpope/vim-fugitive'
Plug 'yegappan/mru'
Plug 'fatih/molokai'
Plug 'morhetz/gruvbox'
Plug 'majutsushi/tagbar'
Plug 'lfv89/vim-interestingwords'
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'Yggdroot/indentLine'
Plug 'preservim/nerdtree'
Plug 'ctrlpvim/ctrlp.vim'
Plug 'easymotion/vim-easymotion'
Plug 'tpope/vim-surround'
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'
Plug 'brooth/far.vim'
Plug 'fatih/vim-go', { 'do': ':GoUpdateBinaries' }
Plug 'python-mode/python-mode', { 'for': 'python', 'branch': 'develop' }
if has('nvim')
  Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }
else
  Plug 'Shougo/deoplete.nvim'
  Plug 'roxma/nvim-yarp'
  Plug 'roxma/vim-hug-neovim-rpc'
endif
Plug 'lvht/phpcd.vim', { 'for': '/usr/local/opt/php@7.4/bin/php', 'do': 'composer install' }
Plug 'Chiel92/vim-autoformat'
Plug 'dense-analysis/ale'
Plug 'preservim/nerdcommenter'
Plug 'mbbill/undotree'
Plug 'tpope/vim-eunuch'
Plug 'skywind3000/asyncrun.vim'
Plug 'airblade/vim-gitgutter'
Plug 'mg979/vim-visual-multi', {'branch': 'master'}
Plug 'mattn/calendar-vim'
Plug 'adah1972/vim-copy-as-rtf'
Plug 'jiangmiao/auto-pairs'
Plug 'uguu-org/vim-matrix-screensaver'
Plug 'tpope/vim-repeat'
call plug#end()


" NerdTree
nnoremap <leader>v :NERDTreeFind<CR>
nnoremap <leader>g :NERDTreeToggle<CR>
let NERDTreeShowHidden=1
let NERDTreeIgnore = [
	\ '\.git$', '\.hg$', '\.svn$', '\.stversions$', '\.pyc$',  '\.pyo$', '\.svn$', '\\.pyo$', '\.svn$', '\.swp$',
	\ '\.DS_Store$', '\.sass-cache$', '__pycache__$', '\.egg_info$', '\.ropeproject$',
	\ ]


" ctrlP
let g:ctrlp_map = '<c-p>'
let g:ctrlp_cmd = 'CtrlP'

" easymotion
nmap ss <Plug>(easymotion-s2)

" python-mode
let g:pymode_python = 'python3'
let g:pymode_trim_whitespaces = 1
let g:pymode_doc = 1
let g:pymode_doc_bind = 'K'
let g:pymode_rope_goto_definition_bind="<C-]>"
let g:pymode_lint = 1
let g:pymode_lint_checkers = ['pyflakes', 'pep8', 'mccabe', 'pylint']
let g:pymode_options_max_line_length = 120

" deoplete
let g:deoplete#enable_at_startup = 1
set completeopt-=preview

" vim-autoformat
let g:formatdef_php = '"/usr/local/bin/php-cs-fixer fix --level=psr2 -n"'
let g:formatters_php = ['php']
noremap <F3> :Autoformat<CR>

" phpcd.vim
let g:phpcd_php_cli_executable = "/usr/local/opt/php@7.4/bin/php"

" 开关撤销树的键映射
nnoremap <F6>      :UndotreeToggle<CR>
inoremap <F6> <C-O>:UndotreeToggle<CR>

" 替换光标下单词的键映射
nnoremap <Leader>v viw"0p
vnoremap <Leader>v    "0p

" 停止搜索高亮的键映射
nnoremap <silent> <F2>      :nohlsearch<CR>
inoremap <silent> <F2> <C-O>:nohlsearch<CR>

" 映射按键来快速启停构建
nnoremap <F5>  :if g:asyncrun_status != 'running'<bar>
                 \if &modifiable<bar>
                   \update<bar>
                 \endif<bar>
                 \exec 'Make'<bar>
               \else<bar>
                 \AsyncStop<bar>
               \endif<CR>


" 用于 quickfix、标签和文件跳转的键映射
if !has('mac')
nnoremap <F11>   :cn<CR>
nnoremap <F12>   :cp<CR>
elsvim-repeate
nnoremap <D-F11> :cn<CR>
nnoremap <D-F12> :cp<CR>
endif
nnoremap <M-F11> :copen<CR>
nnoremap <M-F12> :cclose<CR>
nnoremap <C-F11> :tn<CR>
nnoremap <C-F12> :tp<CR>
nnoremap <S-F11> :n<CR>
nnoremap <S-F12> :prev<CR>

if has('unix') && !has('gui_running')
  " Unix 终端下使用两下 Esc 来离开终端作业模式
  tnoremap <Esc><Esc> <C-\><C-N>
else
  " 其他环境则使用 Esc 来离开终端作业模式
  tnoremap <Esc>      <C-\><C-N>
  tnoremap <C-V><Esc> <Esc>
endif

if has('autocmd')
	function! GnuIndent()
		setlocal cinoptions=>4,n-2,{2,^-2,:2,=2,g0,h2,p5,t0,+2,(0,u0,w1,m1
		setlocal shiftwidth=2
		setlocal tabstop=8
	endfunction

	" 异步运行命令时打开 quickfix 窗口，高度为 10 行
	let g:asyncrun_open = 10

	" 用于 Airline 的设定
	let g:airline_powerline_fonts = 1  " 如没有安装合适的字体，则应置成 0
	let g:airline#extensions#tabline#enabled = 1
	let g:airline#extensions#tabline#buffer_nr_show = 1
	let g:airline#extensions#tabline#overflow_marker = '…'
	let g:airline#extensions#tabline#show_tab_nr = 0
	let g:airline_theme='bubblegum'

	" 非图形环境不使用 NERD Commenter 菜单
	if !has('gui_running')
		let g:NERDMenuMode = 0
	endif

	au BufRead /usr/include/*  call GnuIndent()
endif	

" 100豪秒
set updatetime=100
