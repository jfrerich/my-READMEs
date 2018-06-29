# MY VIM CHEATSHEET

### Standard Commands
    gq - format paragraph - autowrap text at 80 characters
    

###### _Navigation_

    n - jump to start of next match
    gn - select next match
    gN - select previous match 
    
    1. /word       - find "word"
    2. cgnNEW_WORD - change "word" to "NEW_WORD"
    3. .           - repeat change word
	
	This replaces the following
	    
	    1. /word
	    2. visually select the word
	    3. cNEW_WORD
	    4. n.  n.  n.  n.
    
    Use gn / gN when changing/deleting matches
    Use n / N when navigating to matches
    
    5k - move cursor up 5 rows
    5j - move cursor down 5 rows

    'find' and 'till'
    cfn - change to next n
    f{char} - To [count]'th occurrence of {char} to the right.  
		The cursor is placed on {char} |inclusive|.
    F{char} - To the [count]'th occurrence of {char} to the left.
		The cursor is placed on {char} |exclusive|.
    t{char} - Till before [count]'th occurrence of {char} to the right.  
		The cursor is placed on the character left of {char} |inclusive|.
    T{char} - Till after [count]'th occurrence of {char} to the left.  
		The cursor is placed on the character right of {char} |exclusive|.
    ; - Repeat latest f, t, F or T [count] times.
    , - Repeat latest f, t, F or T in opposite direction [count] times. 
    
    <S-H>,<S-M>,<S-L> - move cursor to top, middle, bottom of page
    zt,zz,zb - scroll current line to top, middle, bottom or window

###### _folding_ 
    zM - close all folds
    zR - Open all folds
    za - Open / close fold at cursor ( aliased to <space> )

## Plugins

###### _VundleVim/Vundle.vim_
    :PluginInstall
    :PluginList
    :PluginClean
    :PluginSearch
    
###### _iamcco/markdown-preview.vim_
    :MarkdownPreview - open .md file in browser

###### _vim-scripts/tComment_
    gcc - comment current line
    gc - comment visual selected lines
    
###### _tpope/vim-surround_
    cs"' - change surrounding from " to '
    ds"  - delete " surrounding
    S'   - Visual select, surround with '

###### _easymotion/vim-easymotion_
    <leader> is '\' key
    <leader>s{char} - highlight {char} in file
    <leader>j{char} - Line motion - highlight lines below
    <leader>k{char} - Line motion - highlight lines above

###### _kien/ctrlp.vim (fuzzy finder)_
find anything from VIM http://www.youtube.com/watch?v=9XrHk3xjYsw

    <C-P> - invoke ctrlP
###### _scrooloose/nerdtree_
    :NERDTree - invoke NERDTree

###### _Valloric/YouCompleteMe_
 autocomplete. Also uses ultisnips
    http://www.alexeyshmalko.com/2014/youcompleteme-ultimate-autocomplete-plugin-for-vim/
_key maps _
	
	start typing.  (ife for example)
	    <C-n> <C-p> to traverse popup menu
	    <tab> to insert snippet
	    <C-j> <C-k> to move through fields
	    
    Javascript completion 
	cd .vim/bundle/YouCompleteMe/third_party/ycmd/third_party/tern_runtime
	npm install --production

###### _python-mode/python-mode_
    \r - run python from within vim
    pymode runs rope and takes for ever. using syntastic instead
    got this working and allow <C-S-e> to run script in vim 
    
###### _adelarsq/vim-matchit_
    use % to go to matching <tag>
    
###### _tpope/vim-fugitive (git wrapper)_

    :Gcommit
    :Gdiff - diff current file
    :Glog
    :Gfetch
    :Gpull
    :Gpush
    :Gstatus
	g? 	show this help
	<C-N> next file
	<C-P> previous file
	<CR>  |:Gedit|
	-     |:Git| add
	-     |:Git| reset (staged files)
	a     Show alternative format
	cc    |:Gcommit|
	D     |:Gdiff|
	ds    |:Gsdiff|
	dp    |:Git| add --intent-to-add (untracked files)
	q     close status
	r     reload status
    :Gwrite

###### _simnalamburt/mundo.vim_
    :MundoToggle
    traverse branches of file history. allows retreiving any edit
    http://vimcasts.org/episodes/undo-branching-and-gundo-vim/
    
###### _tagbar_
    :TagBarToggle - show program tags

###### _tpope/vim-repeat_
    . - repoeat command for surround.vim and a few others
    
###### _jiangmiao/auto-pairs_

###### _suan/vim-instant-markdown_

###### _tmhedberg/SimpylFold_

###### _honza/vim-snippets_
###### _perl-support.vim_
###### _closetag.vim_
    close the tag with C-_ in command mode
    
###### _vimwiki/vimwiki_

#### Look and Feel, Automatic functionality
###### _kien/rainbow_parentheses.vim_
    color (), [], {} different colors and apply different colors to nested parens
###### bling/vim-bufferline
    Add open buffers to command line
###### vim-airline/vim-airline
    powerline status bar
    theme for info bar at bottom. https://github.com/vim-airline/vim-airline/wiki/Screenshots
###### liuchengxu/space-vim-dark
###### vim-syntastic/syntastic
    syntax checker after write of file
    :SyntasticInfo to view information about version and enabled checkers on
    current file
    Debug 
	:let g:syntastic_debug=3
	:SyntasticCheck eslint
	run :mes
    
###### Plugin 'prettier/vim-prettier'
    yarn installed with -- brew install yarn
    prettier installed with -- yarn global add prettier

###### Plugin 'pangloss/vim-javascript'
    

" vim-scripts/indentpython.vim
" Plugin suan/instant-markdown-d
" Plugin nvie/vim-flake8
" PEP8 checking
