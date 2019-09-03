# MY VIM CHEATSHEET

<c-g> brings up ctrl-P declaration.  check how and use fzf?

##### _junegunn/fzf.vim (fuzzy finder)_
  | Mapping               | Description                                     |
  | -                     | -                                               |
  | ;                     | :Buffers                                        |
  | <leader&gt;ag         | search for file under cursor in files           |
  | <leader&gt;<space&gt; | :Files                                          |
  | <leader&gt;/          | search with 'Ag'                                |
  | :Commits              | git commits                                     |
  | :BCommits             | git commits for current buffer                  |
  | :Ag                   | loads all files and file contents for searching |
  | :History:             | Command history                                 |
  | :History/             | Search history                                  |
  | :Windows              | list of open windows in vim                     |
  | :Commands             | : Commands                                      |
  | :Maps                 | key mappings                                    |
    
    start search with ' to find exact match, not fuzzy find

### Windows
|         |                      |
| -       | -                    |
| <c-w&gt; z | close preview window |

### Standard Commands
|    |                                                   |
| -  | -                                                 |
| gq | format paragraph - autowrap text at 80 characters |
    
### vimdiff Commands
|             |                                        |
| -           | -                                      |
| ]c, [c      | next/previous difference               |
| do          | diff obtain                            |
| dp          | diff put                               |
| :diffupdate | update diff if updates looks messed up |
 
### _Word Search / Modification_
|        |                                  |
| -      | -                                |
| n, N   | repeat next, previous "/" or "?" |
| gn, gN | select next, previous match      |
    
### How to edit word repeatedly through file

Use gn / gN when CHANGING/DELETING matches <br>
Use n / N when NAVIGATING to matches
    
    1. /word       - find "word"
    2. cgnNEW_WORD - change "word" to "NEW_WORD"
    3. .           - repeat change word

      Above replaces the following sequence
    
        1. /word
        2. visually select the word
        3. cNEW_WORD
        4. n.  n.  n.  n.
  
  Best option is to use 'terryma/vim-multiple-cursors'
  
###### _Text Objects_
    d, c, y -> delete, change, yank (Ex. diw)
  
|        |                                      |
| -      | -                                    |
| iw, aw | inner word, a word                   |
| iW, aW | inner WORD, a WORD                   |
| is, as | inner sentence, a sentence           |
| ip, ap | inner paragraph, a paragraph         |
| ib, ab | inner '(' ')' block, a '(' ')' block |
| iB, aB | inner '{' '}' block, a '{' '}' block |

### _Navigation_

|                                 |                   |                               |   
| -                               | -                 | -                             |   
| **Move cursor..**               | H, M, L           | Top, Middle, Bottom of Screen |   
|                                 | 5k                | up 5 rows                     |   
|                                 | 5j                | down 5 rows                   |   
| **Scroll current Line to..**    | zt,zz,zb          | top, middle, bottom of window |   
| **Move screen..**               | <C-y&gt;          | up one line                   |   
|                                 | <C-e&gt;          | down one line                 |   
| **Move cursor and screen..**    | <C-u&gt;          | up 1/2 page                   |   
|                                 | <C-d&gt;          | down 1/2 page                 |   
| **Split Window Navigation..**   | <C-H&gt;          | move to left split window     |   
|                                 | <C-J&gt;          | move to lower split window    |   
|                                 | <C-K&gt;          | move to above split window    |   
|                                 | <C-L&gt;          | move to right split window    |   
| **Go Through Jump Locations..** | <C-o&gt; <C-i&gt; |                               |   
      
###### _Quickfix and Location Windows_
    (Using unimpaired.vim)
    
      [q, ]q - :cnext, cprevious (mappings from unimpaired.vim)
      <leader>a :cclose -> close quickfix window
      :lopen -> openlocation window
      :lclose -> close location window
      
      
      Location List Navigation 
        [l, ]l - prev, next location list item
        [L, ]L - first, last location list item
    
###### _Buffers_
      Buffer list navigation
        [b, ]b - prev, next buffer
        [B, ]B - first, last buffer
        <C-^> or :b# - previous buffer
        :b <name_of_file> -> open <name_of_file>
    
    
###### _'find' and 'till'_
    
      d, c, y -> delete, change, yank (Ex. cfn -> change to next 'n')
      
      f{char} - to occurrence of {char} to the right.  Cursor is placed on {char} |inclusive|.
      F{char} - to occurrence of {char} to the left.  Cursor is placed on {char} |exclusive|.
      t{char} - Till before occurrence of {char} to the right. Cursor is placed on the character left of {char} |inclusive|.
      T{char} - Till after occurrence of {char} to the left. Cursor is placed on the character right of {char} |exclusive|.
      ; - Repeat latest f, t, F or T .
      , - Repeat latest f, t, F or T in opposite direction. 
    
    
###### _Edit in place_
    
      <C-a>, <C-x> - increment/decrement number
    

###### _folding_ 
    zM - close all folds
    zR - Open all folds
    za - Open / close fold at cursor ( aliased to <space> )

## Plugins

##### Plugin 'terryma/vim-multiple-cursors'

https://github.com/terryma/vim-multiple-cursors/wiki/Keystrokes-for-example-gifs
    
    make visual word selection
        
        <C-n> - select additional words
        c, r, i - to perform operation on selection
        <Home> - move to beginning of line
        <End> - move to end of line
        <Up/Down> - move cursors up/down
 
##### _VundleVim/Vundle.vim_
    :PluginInstall
    :PluginList
    :PluginClean
    :PluginSearch

##### _unimpaired.vim_
    [b, ]b jump to previous, next buffer
    [m, ]m jump to previous, next method

##### _vim-scripts/tComment_
    gcc - comment current line
    gc - comment visual selected lines
    
##### _tpope/vim-surround_
    cs"' - change surrounding from " to '
    ds"  - delete " surrounding
    S'   - Visual select, surround with '
    ysiw] - surround current word with [] (no spaces)
    ysiw[ - surround current word with [  ] (with spaces)

##### _tpope/vim-fugitive (git wrapper)_

    :Gcommit
    :Gdiff - diff current file
    :Glog
    :Gfetch
    :Gpull
    :Gpush
    :Gstatus
    :Gwrite
    
MAPPINGS - These mappings are available in the :Gstatus buffer and the
Fugitive object buffers

      g? 	show this help
      
  Staging and resetting mappings
      s - Stage (add) the file or hunk under the cursor
      u - Unstage (reset) the file or hunk under the cursor
      
      <C-N> skip to next file or hunk
      <C-P> skip to previous file or hunk
      
      <CR>  |:Gedit| edit file under cursor
      =     Toggle inline diff of file under cursor
      
      D, dd |:Gdiff|
      ds    |:Gsdiff| horizontal split
      dv    |:Gvdiff| vertical split
      
      a     Show alternative format
      dp    |:Git| add --intent-to-add (untracked files)
      q     close status
      P     patch 
      
  Commit Mappings 
      cc    |:Gcommit|  Create a commit
      ca    Amend the last commit and edit the message 
      ce    Amend the last commit without editing the message 
      
  Miscellaneous mappings
      gq    Close the status buffer.
      R     Reload the status buffer

##### _easymotion/vim-easymotion_
    s{char} - search {char} in file
    <leader> is '\' key
    <leader>s{char} - highlight {char} in file
    <leader>j{char} - Line motion - highlight lines below
    <leader>k{char} - Line motion - highlight lines above
    
##### _kien/ctrlp.vim (fuzzy finder)_
  Find anything from VIM http://www.youtube.com/watch?v=9XrHk3xjYsw

    Once CtrlP is open
    
    <F5> - purge cache for current dir to get new files, remove deleted files and apply new ignore
    <C-d> - switch to filename search instead of full path
    <C-P> - invoke ctrlP
    <C-F> <C-B> - switch to next, previous mode in sequence
    <C-v> <C-x> - open in Vertical or Horizontal split
    <C-j> <C-k> - navigate the result list
    <C-n> <C-p> - select next/previous string in prompt history
    <C-z> - mark/unmark multiple files. <C-o> to open files
    
##### _scrooloose/nerdtree_
    :NERDTree - invoke NERDTree

##### _iamcco/markdown-preview.vim_
    :MarkdownPreview - open .md file in browser
    
##### _Valloric/YouCompleteMe (Auto Completion)_ 
Also uses ultisnips http://www.alexeyshmalko.com/2014/youcompleteme-ultimate-autocomplete-plugin-for-vim/
	
	start typing.  (ife for example)
	    <C-n> <C-p> to traverse popup menu
	    <tab> to insert snippet
	    <C-j> <C-k> to move through fields
	    
    Javascript completion 
	cd .vim/bundle/YouCompleteMe/third_party/ycmd/third_party/tern_runtime
	npm install --production

##### _python-mode/python-mode_
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

## _fatih/vim-go_
https://www.diycode.cc/projects/fatih/vim-go
#### _Mappings_

  |                                | Shortcut           | Command            | Description                                                                                        |
  | -                              | -                  |                -   |  -                                                                                                 |
  | **quckfix navigations**        | [q, &nbsp; ]q      | :cnext, :cprevious | (mappings from unimpaired.vim)                                                                     |
  | **function navigation**        | ]], &nbsp;  [[     |                    | jump to next, previous function or method (can be used with d, v prefixes)                         |
  | **Go to Definition**           | gd                 | :GoDef             | jump to definition, locally or globally                                                            |
  |                                | <C-t&gt;           |                    | jump back to previous location                                                                     |
  |                                | \ds                | (go-def-split)     |                                                                                                    |
  |                                | \dv                | (go-def-vertical)  |                                                                                                    |
  | **Go Doc**                     | K, \gd             | :GoDoc             | Get documentation for function under cursor                                                        |
  |                                | \gv                | (go-doc-vertical)  |                                                                                                    |
  | **Go Implements (interfaces)** | \s                 | (go-implements)    | Show a list of interfaces implemented by the type under your cursor                                |
  | **Go Rename (refactoring)**    | \e                 | (go-rename)        | Rename the identifier under the cursor to a new name                                               |
  | **Commands**                   | \b                 | :GoBuild           |                                                                                                    |
  |                                | \r                 | :GoRun             | go run on whole package                                                                            |
  |                                | \R                 | :GoRun %           | go run on current file (map added to .vimrc)                                                       |
  |                                | \t                 | :GoTest            | run go test on file                                                                                |
  |                                | \c                 | :GoCoverageToggle  | toggle between GoCoverage and GoCoverageToggle                                                     |
  |                                | :A, :AV, :AS       | :GoAlternate       | alternate between <file>.go and <file>_test.go                                                     |
  | **Go Declarations**            | <C-g&gt;           | :GoDecls           | opens the current file and lists all available function declarations                               |
  |                                | \dr                | :GoDeclsDir        | is the same as :GoDecls, the only difference is it parses all Go files under the current directory |
  | **Text Objects**               | dif, cif, vif, yif |                    | detete, change, visual select, yank 'INNER FUNCTION'                                               |
  |                                | daf, caf, vaf, yaf |                    | detete, change, visual select, yank 'A FUNCTION'                                                   |
  | **Struct Split**               | gS                 |                    | Split struct expression into multiple lines                                                        |
  | **Struct Join**                | gJ                 |                    | Join struct expression into single line                                                            |
  
#### _Snippets_
  |                        |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                            |
  | -                      | -         | -                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | -                                                           |
  | **print**              | fn        | `fmt.Println()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                            |
  |                        | ff        | `fmt.Printf()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | dynamically copys the variable name into the format string |
  |                        | ln        | `log.Println()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                            |
  |                        | lf        | `log.Printf()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | dynamically copys the variable name into the format string |
  | **variables**          | :         | `v := value`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | (shorthand variable declaration)                           |
  |                        | var       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (variable declaration)                                     |
  |                        | vars      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (variables declaration)                                    |
  | **for**                | for       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (for loop)                                                 |
  |                        | fori      | `for i := 0; i < N; i++ { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | (for integer loop)                                         |
  |                        | forr      | `for k, v := range  { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | (for range loop)                                           |
  | **if, else**           | if, ife   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (if with inline err)                                       |
  |                        | else, el  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                            |
  | **field tags**         | json      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (add json field tag)                                       |
  |                        | yaml      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (add yaml field tag)                                       |
  | **interfaces**         | in        | `interface{}`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | (interface)                                                |
  |                        | inf       | `interface name { /* methods */ }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | (full interface)                                           |
  |                        | interface | `type Interface interface { /* TODO: add methods */ }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | (interface I)                                              |
  | **function**           | fun       | `func funcName() error { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | (function)                                                 |
  |                        | fum       | `func (receiver type) funcName() error { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | (method)                                                   |
  |                        | func      | `func name(params) { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
  |                        | fumh      | `func (receiver type) funcName(w http.ResponseWriter, r *http.Request) { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | (http handler function on receiver)                        |
  |                        | funch     | `func handler(w http.ResponseWriter, r *http.Request) { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | (HTTP handler)                                             |
  | **function as method** | meth      | `func (receiver type) name(params) { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | (method)                                                   |
  | **anonymous function** | anon      | `fn := func() { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | (anonymous function)                                       |
  | **Errors**             | err       | `if err != nil { log.Fatal(err) }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | (Basic error handling)                                     |
  |                        | errn      | `if err != nil { return err }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | (Error return)                                             |
  |                        | errn,     | `if err != nil { return nil, err }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | (Error multiple return)                                    |
  |                        | errp      | `if err != nil { panic() }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | (Error panic)                                              |
  |                        | errt      | `if err != nil { t.Fatal(err) }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | (Error test fatal)                                         |
  | **maps**               | make      | `make([]string, 0)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                            |
  |                        | map       | `map[string]int`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | (map[Type]Type)                                            |
  | **single words**       | rt        | `return`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                            |
  |                        | br        | `break`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                            |
  |                        | ft        | `fallthrough`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                            |
  |                        | cn        | `continue`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                            |
  | **Slices**             | ap        | `append(slice, value)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | (append)                                                   |
  |                        | ap=       | `slice = append(slice, value`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | (append assignment)                                        |
  | **Struct**             | struct    | `type Struct struct { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | (struct)                                                   |
  | **go routines**        | go        | `go funcName()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | (goroutine named function)                                 |
  |                        | gof       | `go func() { }()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | (goroutine anonymous function)                             |
  | **channels**           | ch        | `chan type`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                                            |
  |                        | select    | `select { case v1 := <-chan1 }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | select channel                                             |
  | **switch**             | sw        | `switch var {` <br>&nbsp;&nbsp;`case value1: ` <br>&nbsp;&nbsp;`case value2: ` <br>&nbsp;&nbsp;`default:`<br>` }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                            |
  |                        | switch    | `switch var { case value1: }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                            |
  | **Testing**            | test      | `func TestFunction(t *testing.T) { }`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | (test function)                                            |
  |                        | tt        | `var tests = []struct {` <br>`&nbsp;&nbsp;name string`<br> `&nbsp;&nbsp;expected string`<br> `&nbsp;&nbsp;given string`<br>` }&nbsp;{ `<br>`&nbsp;{"", "", "",}, `<br>`} `<br>`for _, tt := range tests { `<br>`&nbsp;&nbsp;tt := tt `<br>`&nbsp;&nbsp;t.Run(tt.name, func(t *testing.T){`<br>`&nbsp;&nbsp;&nbsp;&nbsp; actual := (tt.given)`<br> `&nbsp;&nbsp;&nbsp;&nbsp; if actual != tt.expected { `<br>`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;t.Errorf("(%s): expected %s, actual %s", tt.given, tt.expected, actual)`<br>`&nbsp;&nbsp;&nbsp;&nbsp; }`<br>`&nbsp;&nbsp; })`<br>` }` | (test table)                                               | 

#### _Move Between Functions (Uses Ctrl-P)_
    
  |             |                                                                                                    |
  | -           | -                                                                                                  |
  | :GoDecls    | opens the current file and lists all available function declarations                               |
  | :GoDeclsDir | is the same as :GoDecls, the only difference is it parses all Go files under the current directory |

#### _Guru (editor tool for navigating and understanding Go code)_
        
  |               |                                                                                                                                                                  |
  | -             | -                                                                                                                                                                |
  | :GoReferrers  | find references to the selected identifier, scanning all packages in the workspace. Result is location list                                                      |
  | :GoDescribe   | Like :GoInfo, but give more info show methdod set of a type, declarations of a package                                                                           |
  | :GoImplements | find the interface a type implements (shows location list)                                                                                                       |
  | :GoCallers    | Show "callees" relation for a selected package. A list of possible call targets for the type under the cursor (or selected package) is shown in a location list. |
  | :GoCallers    | Show "callers" relation for a selected function. A list of possible callers for the selected function under the cursor is shown in a location list.              |
      
#### _Refactor It_
    
  |                                  |                                                                                                                                                                      |
  | -                                | -                                                                                                                                                                    |
  | :GoRename                        | search all packages under GOPATH and renames all identifiers that depend on the identifier                                                                           |
  | :GoFreevars <br>(visual select code) | result is quickfix list of all variables that are free variables  <br> used to determine complexity of a piece of code.  See how many variables depend on this code |
      
#### _Delve Debugger_

  |        **Commands**                            |                                                                                                                                                                                                                                   |
  | -                                  | -                                                                                                                                                                                                                                 |
  | :GoDebugStart [pkg] [program-args] | (Ex :GoDebugStart ./hello)                                                                                                                                                                                                        |
  | :GoDebugStop                       | close all windows after stop                                                                                                                                                                                                      |
  | :GoDebugRestart                    | recompile code                                                                                                                                                                                                                    |
  | :GoDebugTest [pkg] [program-args]  | (same as :GoDebugStart, but debugs *_test.go file) <br> Use `-test.flag` to pass flags to `go test` when debugging a test; <br>for example `-test.v` or `-test.run TestFoo` (:GoDebugTest ./app -test.run TestStartServerSuccess) |
  | :GoDebugPrint {expr}               | (Ex. :GoDebugPrint truth == 42)                                                                                                                                                                                                   |
  | :GoDebugStepOut                    | Run all code in the current function and halt ("step out")                                                                                                                                                                        |
  | :GoDebugSet {var} {value}          | set the variable to value.  Cannot be string. limitation of delve                                                                                                                                                                 |

  |   **Mappings**                                   |                                                                                                                                                                                                                                   |
  | -                                  | -                                                                                                                                                                                                                                 |
  | <F5&gt;                               | next breakpoint (:GoDebugContinue)                                                                                                                                                                                                |
  | <F6&gt;                               | evaluate the <cword> under the cursor (:GoDebugPrint)                                                                                                                                                                             |
  | <F9&gt;                               | add breakpoint (:GoDebugBreakpoint)                                                                                                                                                                                               |
  | <F10&gt;                              | next line (:GoDebugNext) Will literally go to the line with active cursor in file!                                                                                                                                                |
  | <F11&gt;                              | step into (:GoDebugStep)                                                                                                                                                                                                          |
  | <S-F11&gt;                            | step out (:GoDebugStepOut)  Mapped in .vimrc                                                                                                                                                                                      |
      
#### _GODEBUG_OUTPUT Window_

    Struct values displayed as {...}
    array/slices as [4] -> <CR> on the variable name to expand values
      
#### _Go Test_
    
  |                |                                 |
  | -              | -                               |
  | :GoTest        | run go test on file             |
  | :GoTestFunc    | test only function under cursor |
  | :GoTestCompile | test compile without problems   |
      
#### _Go Coverage_
    
  |                   |                                                |
  | -                 | -                                              |
  | :GoCoverage       | `go test -coverprofile tempfile`               |
  | :GoCoverageClear  | clear coverage                                 |
  | :GoCoverageToggle | toggle between GoCoverage and GoCoverageToggle |
      
#### _Go Imports_
    
  |                              |                                                           |
  | -                            | -                                                         |
  | :GoImport <package>          | add package to import statement (supports tab completion) |
  | :GoImportAs <name> <package> | add package with package name (ex. str strings)           |
  | :GoDrop <package>            | remove package from imports
    
### _vim-go Tutorial_
https://github.com/fatih/vim-go-tutorial
    
    :GoRun %  - go run on current file
    :GoRun - go run on whole package
    :GoBuild - compile file instead of running it
      
###### _Add field tags (json snippet)_
        
    Place cursor at end of Message or ServerName lines.
    In insert mode, type json and hit tab.. !
  
    Convert ...
    
      type foo struct {
        Message    string
        Ports      []int
        ServerName string
      }
    
    to ...
    
      type foo struct {
        Message    string `json:"message"`
        Ports      []int
        ServerName string `json:"server_name"`
      }
        
###### _Understand It (setup with auto g: commands in .vimrc so don't have to use shortcut to use)_
    
    Identifier Resolution (what is a function accepting or returning)
    
      <leader>i -> :GoInfo 
      The following shows identifier informatino whenever move cursor
        let g:go_auto_type_info = 1
        set updatetime=100   -> set update frequency
        
    Identifier Highlighting
    
      :GoSameIds -> highlight all variables under cursor, across file
      :GoSameIdsClear -> clear highlights
      let g:go_auto_sameids = 1   -> always highlight when move cursor
        
      
##### _adelarsq/vim-matchit_
    use % to go to matching <tag>

##### _simnalamburt/mundo.vim_
    :MundoToggle
    traverse branches of file history. allows retreiving any edit
    http://vimcasts.org/episodes/undo-branching-and-gundo-vim/
    changed from gundo, because gundo no longer supports python3
    
##### _tagbar_
    :TagBarToggle - show program tags

##### _tpope/vim-repeat_
    . - repeat command for surround.vim and a few others
    
##### _jiangmiao/auto-pairs_

##### _suan/vim-instant-markdown_

##### _tmhedberg/SimpylFold_

##### _SirVer/ultisnips_

##### _honza/vim-snippets_
    snippets for ultisnips
    
##### _perl-support.vim_

    
##### _vimwiki/vimwiki_

#### Look and Feel, Automatic functionality

##### _alvan/vim-closetag.vim_
    Automatically close HTML tags
    
##### _kien/rainbow_parentheses.vim_
    color (), [], {} different colors and apply different colors to nested parens
    
##### bling/vim-bufferline
    Add open buffers to command line
    
##### vim-airline/vim-airline
    powerline status bar
    theme for info bar at bottom. https://github.com/vim-airline/vim-airline/wiki/Screenshots
    tabline extension shows active buffers at top of screen
    
##### liuchengxu/space-vim-dark

##### vim-syntastic/syntastic
    syntax checker after write of file
    :SyntasticInfo to view information about version and enabled checkers on
    current file
    Debug 
	:let g:syntastic_debug=3
	:SyntasticCheck eslint
	run :mes
    
##### Plugin 'prettier/vim-prettier'
    yarn installed with -- brew install yarn
    prettier installed with -- yarn global add prettier

##### Plugin 'pangloss/vim-javascript'

##### Plugin 'airblade/vim-gitgutter'
    show gutter with git changes
    
" vim-scripts/indentpython.vim
" Plugin suan/instant-markdown-d

" Plugin nvie/vim-flake8
" PEP8 checking
