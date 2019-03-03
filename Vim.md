# MY VIM CHEATSHEET

### Windows

    <c-w> z close preview window

### Standard Commands

  gq - format paragraph - autowrap text at 80 characters
  
  delete / change commands
	iw (inner word)
	iW (inner WORD)
	
	diw - delete inner word
	diW - delete inner WORD
	dib - delete inner '(' ')' block
	dab - delete a '(' ')' block
	diB - delete inner '{' '}' block
	daB - delete a '{' '}' block

###### _Navigation_


    <C-o>, <C-i> - go through jump locations
    <C-a>, <C-x> - increment/decrement number
    
    H,M,L - jump to Top, Middle, Bottom of window
    
    Jump to errors in quickfix list (using unimpaired.vim)
  [q, ]q - :cnext, cprevious (mappings from unimpaired.vim)
  <leader>a :cclose

    Location List Navigation 
	[l, ]l - prev, next location
	[L, ]L - first, last location
    
    Buffer list navigation
	[b, ]b - prev, next buffer
	[B, ]B - first, last buffer
  <C-^> or :b# - previous buffer
    
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

###### _unimpaired.vim_
    [b, ]b jump to previous, next buffer
    [m, ]m jump to previous, next method

###### _vim-scripts/tComment_
    gcc - comment current line
    gc - comment visual selected lines
    
###### _tpope/vim-surround_
    cs"' - change surrounding from " to '
    ds"  - delete " surrounding
    S'   - Visual select, surround with '
    ysiw] - surround current word with [] (no spaces)
    ysiw[ - surround current word with [  ] (with spaces)

###### _easymotion/vim-easymotion_
    <leader> is '\' key
    <leader>s{char} - highlight {char} in file
    <leader>j{char} - Line motion - highlight lines below
    <leader>k{char} - Line motion - highlight lines above

###### _kien/ctrlp.vim (fuzzy finder)_
find anything from VIM http://www.youtube.com/watch?v=9XrHk3xjYsw

    <C-P> - invoke ctrlP
    <C-F> - switch to next mode in sequence
    <C-B> - switch to previous mode in sequence (line mode is default)
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
    good video - https://www.youtube.com/watch?v=67OZNp9Z0CQ
    explanation of rope functions - https://github.com/python-rope/rope/blob/master/docs/overview.rst
    
    \r - run python from within vim
    \g - goto definition
    K - show documentaion
    
    [[, ]] - Jump to prev, next class or function (normal, visual, operator modes)
    [M, ]M - Jump to prev, next class or method (normal, visual, operator modes)
    aC    Select a class. Ex: vaC, daC, yaC, caC (normal, operator modes)
    iC    Select inner class. Ex: viC, diC, yiC, ciC (normal, operator modes)
    aM    Select a function or method. Ex: vaM, daM, yaM, caM (normal, operator modes)
    iM    Select inner function or method. Ex: viM, diM, yiM, ciM (normal, operator modes)
    
    [l, ]l - Jump to prev, next location of error/warning
    
    Extract method/variable from selected lines.
    <C-c>rm - visual select first.  Extracts selection and creates new function/method
    <C-c>rl - visual select first.  Extracts selection and creates new variable
	
    <C-c>ro - organize imports
    <C-c>rr - rename method/function/class/variable under cursor
    
    got this working and allow <C-S-e> to run script in vim 

###### _fatih/vim-go_

  SHORTCUTS (Explained in detail in next sections)
    gd - goto function definition
      <C-t> go back to last location before gd command
    
    Text Objects
      af, if  ->  'a function', 'inner function'
      ac, ic  ->  'a comment', 'inner comment'
      
      works with d, c, v, y
      
      Ex. dif, cic
      
    (Unimpaired mappings)
      ]], [[ - jump to next, previous function or method
               These can be used with d, v prefixes
      [q, ]q  for :cnext, cprevious (mappings from unimpaired.vim)
    
    K - Get documentation for function under cursor
    \b - :GoBuild
    \r - :GoRun
    \t - :GoTest
    \c - :GoCoverageToggle
    
    Snippets
      errp -> panic if err ! nil
      errn -> return if err ! nil
      fn -> fmt.Println()
      ff -> fmt.Printf()
      ln -> log.Println()
      lf -> log.Printf()
      
      ff / lf dynamically copys the variable name into the format string!!!
      
      :  -> v:= value
      
      anon ->  fn := func() {
            
               }
	    ap ->  append(slice, value)
      ap= ->  slice = append(slice, value)
      br  ->  break
      interface  ->
      if  -> 
      else  -> 
      json  ->  json field tag
      yaml  ->  yaml field tag
      for  ->  for loop
      fori  ->  for integer loop
      forr  ->  for range loop
      
      ff  ->  Printf debug
      fn  ->  Println debug
      
      meth  ->   method
      
      test  ->  test function
      tt  ->  test table 
      
      var  ->  variable declaration
      vars  ->  variables declaration
      select  ->  select channel
      switch  ->  switch, case
      rt  ->  return
      
      
      
    :A, :AV, :AS - :GoAlternate - alternate to and from <file>.go and <file>_test.go 
      
    Move Between Functions (Uses Ctrl-P)
      :GoDecls opens the current file and lists all available function declarations
      :GoDeclsDir is the same as :GoDecls, the only difference is it parses all Go files under the current directory
      
    :GoReferrers -> find references to the selected identifier, scanning all
                    packages in the workspace. Result is location list
    :GoDescribe -> Like :GoInfo, but give more info 
                    - show methdod set of a type, declarations of a package
    :GoImplements -> find the interface a type implements (shows location list)
      
    Refactor It
      :GoRename -> search all packages under GOPATH and renames all identifiers
                   that depend on the identifier
      :GoFreevars (visual select code) -> result is quickfix list of all
          variables that are free variables  
          - used to determine complexity of a piece of code.  See how many
            variables depend on this code
      
    Delve Debugger   
    
      :GoDebugStart [pkg] [program-args]  (Ex :GoDebugStart ./hello)
      :GoDebugStop  -> close all windows after stop
      :GoDebugRestart  -> recompile code
      :GoDebugTest [pkg] [program-args]
          Use `-test.flag` to pass flags to `go test` when debugging a test; for
          example `-test.v` or `-test.run TestFoo`
      
      :GoDebugStepOut - Run all code in the current function and halt ("step out")
      :GoDebugSet {var} {value} -> set the variable to value. 
                                   Cannot be string. limitation of delve
      
      <F5> - continue until next breakpoint
      <F9> - add breakpoint
      <F10> - run to the next line
      <F11> - step into 
      
      NOTE : <F10> will literally go to the line active cursor in file!
    
    
    vim-go Tutorial https://github.com/fatih/vim-go-tutorial
    :GoRun %  - go run on current file
    :GoRun - go run on while package
    :GoBuild - compile file instead of running it
    :GoTest - run go test on file 
    :GoTestFunc - test only function under cursor
    :GoTestCompile - test compile without problems
    :GoCoverage - `go test -coverprofile tempfile`
    :GoCoverageClear - clear coverage
    :GoCoverageToggle - toggle between GoCoverage and GoCoverageToggle
    :GoImport <package> - add package to import statement (supports tab completion)
    :GoImportAs <name> <package> - add package with package name (ex. str strings)
    :GoDrop <package> - remove package from imports 
    :GoCallers 
        Show "callees" relation for a selected package. A list of possible call
        targets for the type under the cursor (or selected package) is shown in a
        location list.
    :GoCallers
        Show "callers" relation for a selected function. A list of possible
        callers for the selected function under the cursor is shown in a location
        list.
    
    Text Objects
      dif, cif, vif, yif - detete, change, visual select, yank 'INNER FUNCTION'
      daf, caf, vaf, yaf - detete, change, visual select, yank 'A FUNCTION'
      
    Struct Split and Join
      gS - Split struct expression into multiple lines
      gJ - Join struct expression into single line
  
    Snippets
      errp -> panic if err ! nil
      fn -> fmt.Println()
      ff -> fmt.Printf()
      ln -> log.Println()
      lf -> log.Printf()
      
      ff / lf dynamically copys the variable name into the format string!!!
      
      Add field tags
        
        Place cursor at end of Message or ServerName lines.
        In insert mode, type json and hit tab.. !
      
        Convert ...
        
          type foo struct {
            Message    string
            Ports      []int
            ServerName string
          }
        
        To ...
        
          type foo struct {
            Message    string `json:"message"`
            Ports      []int
            ServerName string `json:"server_name"`
          }
          
    Navigation
      Alternate Files
        :GoAlternate - alternate between test and not-test file
        
      Go to Definition 
        gd -> :GoDef jump to definition, locally or globally
        <C-t> -> jump back to previous location
      
      Move Between Functions (Uses Ctrl-P)
      
        :GoDecls opens the current file and lists all available function declarations
        :GoDeclsDir is the same as :GoDecls, the only difference is it parses all Go files under the current directory
        
        These can be used with d, v prefixes
        ]] - jump to next function or method
        [[ - jump to previous function or method 
        
        
    Understand It
    
      Documentation Lookup 
        K - Get documentation for function under cursor (:GoDoc)
        
      Identifier Resolution (what is a function accepting or returning)
        <leader>i -> :GoInfo 
        The following shows identifier informatino whenever move cursor
          let g:go_auto_type_info = 1
          set updatetime=100   -> set update frequency
          
      Identifier Highlighting
        :GoSameIds -> highlight all variables under cursor, across file
        :GoSameIdsClear -> clear highlights
        let g:go_auto_sameids = 1   -> always highlight when move cursor
        
    Guru (editor tool for navigating and understanding Go code)
      
      :GoReferrers -> find references to the selected identifier, scanning all
                      packages in the workspace. Result is location list
      :GoDescribe -> Like :GoInfo, but give more info 
                      - show methdod set of a type, declarations of a package
      :GoImplements -> find the interface a type implements (shows location list)
      
    Refactor It
      :GoRename -> search all packages under GOPATH and renames all identifiers
                   that depend on the identifier
      :GoFreevars (visual select code) -> result is quickfix list of all
          variables that are free variables  
          - used to determine complexity of a piece of code.  See how many
            variables depend on this code
      
      
        
      
          
      
    
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
    changed from gundo, because gundo no longer supports python3
    
###### _tagbar_
    :TagBarToggle - show program tags

###### _tpope/vim-repeat_
    . - repeat command for surround.vim and a few others
    
###### _jiangmiao/auto-pairs_

###### _suan/vim-instant-markdown_

###### _tmhedberg/SimpylFold_

###### _SirVer/ultisnips_

###### _honza/vim-snippets_
    snippets for ultisnips
    
###### _perl-support.vim_

###### _alvan/vim-closetag.vim_
    Automatically close HTML tags
    
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

###### Plugin 'airblade/vim-gitgutter'
    show gutter with git changes
    
###### Plugin 'terryma/vim-multiple-cursors'
    https://github.com/terryma/vim-multiple-cursors/wiki/Keystrokes-for-example-gifs
    - make visual word selection
    - <C-n> - select additional words
    - c, r, i - to perform operation on selection
    - <Home> - move to beginning of line
    - <End> - move to end of line
    - <Up/Down> - move cursors up/down
 
" vim-scripts/indentpython.vim
" Plugin suan/instant-markdown-d

" Plugin nvie/vim-flake8
" PEP8 checking
