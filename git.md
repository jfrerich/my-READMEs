# Git

#### Git config
    ~/.gitignore_global
    ~/.gitconfig

#### goproj alias
    alias goproj 'source ~/myscripts/dev/bin/goproj.sh $!'
    goproj.sh - sets BIN_TYPE environment variable
    .cshrc - used to set path to /rel or /dev 
	     reads $BIN_TYPE set from goproj.sh
	     sets color on prompt

# Setting Up Rel and Dev Areas
#### create rel master and add first script
    mkdir myscripts/rel/lib
    mkdir myscripts/rel/bin
    cp ~/bin/Realty/cad_reader.db.pl ~/myscripts/rel/bin/Realty
    (~/myscripts/rel/) git init
    (~/myscripts/rel/bin/Realty/) git add cad_reader.db.pl
    (~/myscripts/rel/bin/Realty/) git commit cad_reader.db.pl

#### create dev area
    (~/myscripts/)% git clone rel dev
    (~/myscripts/dev/bin/)% git clone rel dev

#### add comment to cloned file and commit to cloned area
    (~/myscripts/dev/bin/Realty)% vi cad_reader.db.pl
    (~/myscripts/dev/bin/Realty)% git add cad_reader.db.pl
    (~/myscripts/dev/bin/Realty)% git commit cad_reader.db.pl

#### Release Code 
    ~/myscripts/rel/bin/Realty/
	       /rel/lib/

### Developement Code 
Cloned from /rel

    ~/myscripts/dev/bin/Realty/
	       /dev/lib/
#### Bare Dir  
Cloned from /rel

    ~/myscripts/git-bare-clone

### EXAMPLE FROM WEB (JAF MODIFIED FOR Rel and Dev areas)
http://stackoverflow.com/questions/2816369/git-push-error-remote-rejected-master-master-branch-is-currently-checked

 * myscripts/rel   (Rel Area)
 * git-bare-clone  (bare directory) Does not store files, only repository files
 * myscripts/dev   (Dev Area)
 
 
```sh
mkdir -p rel/bin/Realty
cd rel
git init
cp ../../bin/Realty/cad_reader.db.pl bin/Realty
```


```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```


```python
s = "Python syntax highlighting"
print s
```

```perl
my $variable = 'jason';
foreach my $var (@array) {
    print $var;
}
```

    #~/myscripts $ mkdir -p rel/bin/Realty
    #~/myscripts $ cd rel
    #~/myscripts/rel $ git init
    #~/myscripts/rel $ cp ../../bin/Realty/cad_reader.db.pl bin/Realty
    #~/myscripts/rel $ git bin/Realty/cad_reader.db.pl
    #~/myscripts/rel $ git commit -m 'initial import'
    #~/myscripts/rel $ git clone --bar . ../git-bare-clone
		       Cloning into bare repository '../git-bare-clone'...
    #~/myscripts/rel $ git remote add origin ../git-bare-clone
    #~/myscripts/rel $ git push --set-upstream origin master
		       Branch master set up to track remote branch master from origin.
		       Everything up-to-date
    #~/myscripts/rel $ cd ..
    #~/myscripts $ ls
		   rel  git-bare-clone
    #~/myscripts $ mkdir dev
    #~/myscripts $ cd dev
    #~/myscripts/dev $ git clone ../git-bare-clone .

## EDIT DEV and PULL INTO REL
At this point, rel/ dev/ and git-bar-clone are setup ##
editing is done in dev/. changes are added commited and pushed (to git-bare-clone)
changes are now pulled from git-bare-clone to rel/ dir

    #~/myscripts/dev $ vi bin/Realty/cad_reader.db.pl
    #~/myscripts/dev $ git add bin/Realty/cad_reader.db.pl 
    #~/myscripts/dev $ git commit -m 'added line 2'
    #~/myscripts/dev $ git push
    #~/myscripts/rel $ git pull


    #~/myscripts/rel $ cd ../dev/
    #~/myscripts/dev $ git pull   ( Shouldn't do this. Should only pull changes which have been 
    #                               pushed to git-bare-clone from dev/ )


#### QUESTIONS
how to git pull only one file
how to git diff versions ..

# A LOOK INTO THE REPOSITORIES

    #~/myscripts/rel $ git remote -v
      origin	../git-bare-clone (fetch)
      origin	../git-bare-clone (push)
    #~/myscripts/rel $ git branch -r
      origin/master

    #~/myscripts/dev $ git remote -v
      origin	/Users/j_honky/myscripts/dev/../git-bare-clone (fetch)
      origin	/Users/j_honky/myscripts/dev/../git-bare-clone (push)
    #~/myscripts/dev $ git branch -r
      origin/HEAD -> origin/master
      origin/master

    #~/myscripts/git-bare-clone $ git remote -v
      origin	/Users/j_honky/myscripts/rel/. (fetch)
      origin	/Users/j_honky/myscripts/rel/. (push)
    #~/myscripts/git-bare-clone $ git branch -r

### EXAMPLE FROM WEB (JAF MODIFIED FOR Readability)

 * repo1  (Release Area)
 * repo1-bare-clone  (bare directory.  does not store files, only repository files)
 * repo1-remote (Dev Area)
 

    #~ $ cd gitdir
    /home/lylez/gitdir
    #~/gitdir $ ls
    #~/gitdir $ mkdir repo1
    #~/gitdir $ cd repo1
    #~/gitdir/repo1 $ git init
    #~/gitdir/repo1 $ echo "line 1" > afile.txt
    #~/gitdir/repo1 $ git add afile.txt
    #~/gitdir/repo1 $ git commit -m 'initial import'
    #~/gitdir/repo1 $ git clone --bar . ../repo1-bare-clone
		      Cloning into bare repository '../repo1-bare-clone'...
    #~/gitdir/repo1 $ git remote add origin ../repo1-bare-clone
    #~/gitdir/repo1 $ git push --set-upstream origin master
		      Branch master set up to track remote branch master from origin.
		      Everything up-to-date
    #~/gitdir/repo1 $ cd ..
    #~/gitdir $ ls
		repo1  repo1-bare-clone
    #~/gitdir $ mkdir repo1-remote
    #~/gitdir $ cd repo1-remote
    #~/gitdir/repo1-remote $ git clone ../repo1-bare-clone .
			     Cloning into '.'...
    #~/gitdir/repo1-remote $ ls
			     afile.txt
    #~/gitdir/repo1-remote $ cat afile.txt
			     line 1
    #~/gitdir/repo1-remote $ echo "line 2" >> afile.txt
    #~/gitdir/repo1-remote $ git add afile.txt
    #~/gitdir/repo1-remote $ git commit -m 'added line 2'
			     [master 5ad31e0] added line 2
			      1 file changed, 1 insertion(+)
    #~/gitdir/repo1-remote $ git push
			     Counting objects: 3, done.
			     Writing objects: 100% (3/3), 260 bytes | 0 bytes/s, done.
			     Total 3 (delta 0), reused 0 (delta 0)
			     To /home/lylez/gitdir/repo1-remote/../repo1-bare-clone
				f407e12..5ad31e0  master -> master
    #~/gitdir/repo1-remote $ cd ../repo1
    #~/gitdir/repo1 $ ls
		      afile.txt
    #~/gitdir/repo1 $ cat afile.txt
		      line 1
    #~/gitdir/repo1 $ git pull
		      remote: Counting objects: 3, done.
		      remote: Total 3 (delta 0), reused 0 (delta 0)
		      Unpacking objects: 100% (3/3), done.
		      From ../repo1-bare-clone
			 f407e12..5ad31e0  master     -> origin/master
		      Updating f407e12..5ad31e0
		      Fast-forward
		       afile.txt | 1 +
		       1 file changed, 1 insertion(+)
    #~/gitdir/repo1 $ cat afile.txt
		      line 1
		      line 2
    #~/gitdir/repo1 $ echo "line 3" >> afile.txt
    #~/gitdir/repo1 $ git add afile.txt
    #~/gitdir/repo1 $ git commit -m 'added line 3'
		      [master 3fa569e] added line 3
		       1 file changed, 1 insertion(+)
    #~/gitdir/repo1 $ git push
		      Counting objects: 3, done.
		      Writing objects: 100% (3/3), 265 bytes | 0 bytes/s, done.
		      Total 3 (delta 0), reused 0 (delta 0)
		      To ../repo1-bare-clone
			 5ad31e0..3fa569e  master -> master
    #~/gitdir/repo1 $ cd ../repo1-remote/
    #~/gitdir/repo1-remote $ ls
			     afile.txt
    #~/gitdir/repo1-remote $ cat afile.txt
			     line 1
			     line 2
    #~/gitdir/repo1-remote $ git pull
			     remote: Counting objects: 3, done.
			     remote: Total 3 (delta 0), reused 0 (delta 0)
			     Unpacking objects: 100% (3/3), done.
			     From /home/lylez/gitdir/repo1-remote/../repo1-bare-clone
				5ad31e0..3fa569e  master     -> origin/master
			     Updating 5ad31e0..3fa569e
			     Fast-forward
			      afile.txt | 1 +
			      1 file changed, 1 insertion(+)
    #~/gitdir/repo1-remote $ cat afile.txt
			     line 1
			     line 2
			     line 3




#### EXAMPLE FROM WEB

    lylez@LJZ-DELLPC ~
    $ cd gitdir
    /home/lylez/gitdir

    lylez@LJZ-DELLPC ~/gitdir
    $ ls

    lylez@LJZ-DELLPC ~/gitdir
    $ mkdir repo1

    lylez@LJZ-DELLPC ~/gitdir
    $ cd repo1
    /home/lylez/gitdir/repo1

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git init
    Initialized empty Git repository in /home/lylez/gitdir/repo1/.git/

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ echo "line 1" > afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git add afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git commit -m 'initial import'
    [master (root-commit) f407e12] initial import
     1 file changed, 1 insertion(+)
     create mode 100644 afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git clone --bar . ../repo1-bare-clone
    Cloning into bare repository '../repo1-bare-clone'...
    done.

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git remote add origin ../repo1-bare-clone

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git push --set-upstream origin master
    Branch master set up to track remote branch master from origin.
    Everything up-to-date

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ cd ..

    lylez@LJZ-DELLPC ~/gitdir
    $ ls
    repo1  repo1-bare-clone

    lylez@LJZ-DELLPC ~/gitdir
    $ mkdir repo1-remote

    lylez@LJZ-DELLPC ~/gitdir
    $ cd repo1-remote
    /home/lylez/gitdir/repo1-remote

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git clone ../repo1-bare-clone .
    Cloning into '.'...
    done.

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ ls
    afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ cat afile.txt
    line 1

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ echo "line 2" >> afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git add afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git commit -m 'added line 2'
    [master 5ad31e0] added line 2
     1 file changed, 1 insertion(+)

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git push
    Counting objects: 3, done.
    Writing objects: 100% (3/3), 260 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To /home/lylez/gitdir/repo1-remote/../repo1-bare-clone
       f407e12..5ad31e0  master -> master

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ cd ../repo1

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ ls
    afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ cat afile.txt
    line 1

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git pull
    remote: Counting objects: 3, done.
    remote: Total 3 (delta 0), reused 0 (delta 0)
    Unpacking objects: 100% (3/3), done.
    From ../repo1-bare-clone
       f407e12..5ad31e0  master     -> origin/master
    Updating f407e12..5ad31e0
    Fast-forward
     afile.txt | 1 +
     1 file changed, 1 insertion(+)

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ cat afile.txt
    line 1
    line 2

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ echo "line 3" >> afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git add afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git commit -m 'added line 3'
    [master 3fa569e] added line 3
     1 file changed, 1 insertion(+)

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ git push
    Counting objects: 3, done.
    Writing objects: 100% (3/3), 265 bytes | 0 bytes/s, done.
    Total 3 (delta 0), reused 0 (delta 0)
    To ../repo1-bare-clone
       5ad31e0..3fa569e  master -> master

    lylez@LJZ-DELLPC ~/gitdir/repo1
    $ cd ../repo1-remote/

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ ls
    afile.txt

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ cat afile.txt
    line 1
    line 2

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git pull
    remote: Counting objects: 3, done.
    remote: Total 3 (delta 0), reused 0 (delta 0)
    Unpacking objects: 100% (3/3), done.
    From /home/lylez/gitdir/repo1-remote/../repo1-bare-clone
       5ad31e0..3fa569e  master     -> origin/master
    Updating 5ad31e0..3fa569e
    Fast-forward
     afile.txt | 1 +
     1 file changed, 1 insertion(+)

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ cat afile.txt
    line 1
    line 2
    line 3

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
    $ git --version
    git version 2.1.1

    lylez@LJZ-DELLPC ~/gitdir/repo1-remote
