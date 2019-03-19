# USING ZSH

##### INSTALLED PLUGINS

    git                        # aliases - https://github.com/robbyrussell/oh-my-zsh/wiki/Plugin:git
    colored-man-pages          # add color to man pages
    zsh-autosuggestions        # auto suggestions on commandline
    zsh-syntax-highlighting    # highlight command line 
    zsh-history-substring-search   # type substring; <esc>; then j/k to traverse through history
				   # bindkeys setup in .zshrc


##### COMMANDS 


    ls -l **/*.py - recursive ls
    
    path replacement
	cd /usr/local/bin
	cd bin share
	pwd 
	    /usr/local/share
	
    zmv
    http://zshwiki.org/home/builtin/functions/zmv
    
    "alias" to see list of all aliases
	interesting ones
	    ~
	    ..
	    ...
	    take test_folder : Create folder and cd to it	    

    zsh-autosuggestions
	hit -> arrow to complete autosuggestion
    
    d - list dirs
    cd -3 cd to 3rd dir in list

#### aliases 

##### git
    
####### git most commonly used
    gaa='git add --all' 
    gd - git diff file(s) and show in terminal
    gdt - git difftool file(s) and show in external vimdiff window
    gcmsg='git commit -m'
    gco='git checkout'
    gcount='git shortlog -sn'
    glod='git log --graph --pretty='\''%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%ad) %C(bold blue)<%an>%Creset'\'
    
    gb='git branch'
    gcb='git checkout -b'
    gcm='git checkout master'
  

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

    Stole from https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/common-aliases/common-aliases.plugin.zsh
	
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

    # code brew reinstall python
    #==> Reinstalling python
    #Warning: Building python from source:
    #  The bottle needs the Apple Command Line Tools to be installed.
    #  You can install them, if desired, with:
    #    xcode-select --install
    #
    #==> Downloading https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tar.xz
    #Already downloaded: /Users/j_honky/Library/Caches/Homebrew/python-3.6.5.tar.xz
    #==> ./configure --prefix=/usr/local/Cellar/python/3.6.5 --enable-ipv6 --datarootdir=/usr/local/Cellar/python/3.6.5/share --datadir=/usr/local/Cellar/python/3.6.5/share --enable-framework=/usr/local/Cellar/python/3.6.5/Frameworks --enable-loadable-sqlite-extensions --wit
    #==> make
    #==> make install PYTHONAPPSDIR=/usr/local/Cellar/python/3.6.5
    #==> make frameworkinstallextras PYTHONAPPSDIR=/usr/local/Cellar/python/3.6.5/share/python
    #==> Downloading https://files.pythonhosted.org/packages/72/c2/c09362ab29338413ab687b47dab03bab4a792e2bbb727a1eb5e0a88e3b86/setuptools-39.0.1.zip
    #Already downloaded: /Users/j_honky/Library/Caches/Homebrew/python--setuptools-39.0.1.zip
    #==> Downloading https://files.pythonhosted.org/packages/ae/e8/2340d46ecadb1692a1e455f13f75e596d4eab3d11a57446f08259dee8f02/pip-10.0.1.tar.gz
    #Already downloaded: /Users/j_honky/Library/Caches/Homebrew/python--pip-10.0.1.tar.gz
    #==> Downloading https://files.pythonhosted.org/packages/5d/c1/45947333669b31bc6b4933308dd07c2aa2fedcec0a95b14eedae993bd449/wheel-0.31.0.tar.gz
    #Already downloaded: /Users/j_honky/Library/Caches/Homebrew/python--wheel-0.31.0.tar.gz
    #==> make html
    #==> /usr/local/Cellar/python/3.6.5/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.6.5/bin --install-lib=/usr/local/lib/python3.6/site-packages --single-version-externally-managed --record=installed.txt
    #==> /usr/local/Cellar/python/3.6.5/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.6.5/bin --install-lib=/usr/local/lib/python3.6/site-packages --single-version-externally-managed --record=installed.txt
    #==> /usr/local/Cellar/python/3.6.5/bin/python3 -s setup.py --no-user-cfg install --force --verbose --install-scripts=/usr/local/Cellar/python/3.6.5/bin --install-lib=/usr/local/lib/python3.6/site-packages --single-version-externally-managed --record=installed.txt
    #==> Caveats
    #Python has been installed as
    #  /usr/local/bin/python3
    #
    #Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
    #`python3`, `python3-config`, `pip3` etc., respectively, have been installed into
    #  /usr/local/opt/python/libexec/bin
    #
    #If you need Homebrew's Python 2.7 run
    #  brew install python@2
    #
    #Pip, setuptools, and wheel have been installed. To update them run
    #  pip3 install --upgrade pip setuptools wheel
    #
    #You can install Python packages with
    #  pip3 install <package>
    #They will install into the site-package directory
    #  /usr/local/lib/python3.6/site-packages
    #
    #See: https://docs.brew.sh/Homebrew-and-Python
    #
