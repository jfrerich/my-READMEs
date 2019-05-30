# USING ZSH

### INSTALLED PLUGINS

| Plugin                       | Link / Description                                                  |
| - | - |
| git                          | aliases - https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git |
| colored-man-pages            | add color to man pages                                              |
| zsh-autosuggestions          | auto suggestions on commandline                                     |
| zsh-syntax-highlighting      | highlight command line                                              |
| zsh-history-substring-search | type substring; <esc>; then j/k to traverse through history         |
     
bindkeys setup in .zshrc

### COMMANDS 

| Command                                                         | Description                                   |
| -                                                               | -                                             |
| ls -l \*\*/*.py                                                 | recursive ls                                  |
| cd /usr/local/bin<br> cd bin share<br> pwd<br> /usr/local/share | path replacement                              |
| zmv                                                             | http://zshwiki.org/home/builtin/functions/zmv |
| take test_folder : Create folder and cd to it                   |                                               |
    

    zsh-autosuggestions
    hit -> arrow to complete autosuggestion
    

### aliases 

"alias" to see list of all aliases

| Command | Description           |
| -       | -                     |
| ~       |                       |
| ..      |                       |
| ...     |                       |
| d       | list dirs             |
| cd -3   | cd to 3rd dir in list |

### fzf

| Mapping        | Description                                                                   |
| -              | -                                                                             |
| <ctrl-r&gt;    | fzf through command HISTORY                                                   |
| <ctrl-t&gt;    | fzf through current DIRECTORY                                                 |

##### Using fzf window
| Search terms | Description                              |
| -            | -                                        |
| atom         | fuzzy search atom                        |
| 'atom        | no fuzzy. search exact match             |
| ^a  .go$     | match ^a and .go$  regex patterns        |
| !^a  !.go$   | DO NOT match ^a and .go$ regex patterns |

##### Example Completion With FZF
`COMMAND [DIRECTORY/][FUZZY_PATTERN]**<TAB>` <br> 

 Use tab on filenames to select multiple files
 
| *COMMAND*      | Description                     |
| -              | -                               |
| rm <ctrl-t&gt; | use fzf to select files for rm. |
| kill -9 <tab>  | use fzf to select PID to kill.  |


### git
    
##### git most commonly used
| Command | Description                                                                                                    |
| -       | -                                                                                                              |
| gaa     | 'git add --all'                                                                                                |
| gd      | git diff file(s) and show in terminal                                                                          |
| gdt     | git difftool file(s) and show in external vimdiff window                                                       |
| gcmsg   | 'git commit -m'                                                                                                |
| gco     | 'git checkout'                                                                                                 |
| gcount  | 'git shortlog -sn'                                                                                             |
| glod    | 'git log --graph --pretty='\''%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>%Creset'\' |
| gb      | 'git branch'                                                                                                   |
| fbr     | fzf 'git branch' -> allows selecting instead of having to type                                                 |
| gcb     | 'git checkout -b'                                                                                              |
| gcm     | 'git checkout master'                                                                                          |
  

##### INSTALLING

Follow these instructions

    http://stevelosh.com/blog/2010/02/my-extravagant-zsh-prompt/

	Install https://github.com/robbyrussell/oh-my-zsh

	    BASIC INSTALLATION
	    
	    % bash
	    % sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

##### RUNNING IN AN ENVIRONMENT

    https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-macos

    This is how to run a specific version fo python
    source Environments/my_env/bin/activate

    now python has is linked to python from my_env (which is python3)
    
    "(my_env) python --version"
    "Python 3.6.5"

##### SETUP ALIASES

    From https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/common-aliases/common-aliases.plugin.zsh
	
    placed in ~/.zshrc

##### PROMPTS 
    
    ~/.zshrc

    https://gist.github.com/kevin-smets/8568070

##### ZSH FEATURES

    https://code.joejag.com/2014/why-zsh.html

##### iTerm 

    CMD+SHIFT+H Show past history

##### DOTFILES 

    # see github README.md

##### HOMEBREW PYTHON

