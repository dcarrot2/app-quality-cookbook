```nohighlight
sudo apt-get install git
...
$ git --version
git version 2.0.4
```
    ```nohighlight
    $ mkdir foo
    ```
    ```nohighlight
    $ cd foo
    ```
    ```nohighlight
    $ git init
    ```
```nohighlight
$ git status

On branch master

Initial commit

nothing to commit
```
        
    ```nohighlight
    $ echo "hi" > file.txt
    ```
    ```nohighlight
    $ git status
    ...
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    
      file.txt
    ````
    ```nohighlight
    $ git add file.txt
    ```
    ```nohighlight
    $ git status
    On branch master
    
    Initial commit
    
    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)
    
      new file:   file.txt
    ...
    ```
    ```nohighlight
    $ git commit
    ```
    ```nohighlight
    $ git commit
    
    *** Please tell me who you are.
    
    Run
    
      git config --global user.email "you@example.com"
      git config --global user.name "Your Name"
    ```
```nohighlight
$ git log
commit c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
Author: Erik Eldridge <erik@example.com>
Date:   Fri Mar 13 04:22:00 2015 +0000

    Add file
```
```nohighlight
$ git show c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
commit c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
Author: Erik Eldridge <erik@example.com>
Date:   Fri Mar 13 04:22:00 2015 +0000

    Add file

diff --git a/file.txt b/file.txt
new file mode 100644
index 0000000..45b983b
--- /dev/null
+++ b/file.txt
@@ -0,0 +1 @@
+hi
```
    ```nohighlight
    $ echo "world" >> file.txt
    ```
    ```nohighlight
    $ git diff
    diff --git a/file.txt b/file.txt
    index 45b983b..3b097cd 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1,2 @@
     hi
    +world
    ```
    ```nohighlight
    $ git reset
    Unstaged changes after reset:
    M file.txt
    ```
    ```nohighlight
    $ git add file.txt
    $ git commit -m "Update file.txt"
    [master 59d700c] Update file.txt
    1 file changed, 1 insertion(+)
    $ git log
    commit 06abe628a703ed148bfcf21c45efdd2283609d40
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:27:42 2015 +0000
    
        Update file.txt
    
    commit c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:22:00 2015 +0000
    
        Add file
    ...
    ```
    ```nohighlight
    $ git revert 06abe628a703ed148bfcf21c45efdd2283609d40
    [master f7d0faa] Revert "Update file.txt"
     1 file changed, 1 deletion(-)
     ```
    ```nohighlight
    $ git log
    commit f7d0faa478b7b2ee19feba9c0d76bebfab37b061
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:32:07 2015 +0000
    
        Revert "Update file.txt"
        This reverts commit 06abe628a703ed148bfcf21c45efdd2283609d40.
    
    commit 06abe628a703ed148bfcf21c45efdd2283609d40
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:27:42 2015 +0000
    
        Update file.txt
    
    commit c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:22:00 2015 +0000
    
        Add file
    ```
    ```nohighlight
    $ git branch
    * master
    ```
    ```nohighlight
    ```
    ```nohighlight
    $ git checkout foo
    Switched to branch 'foo'
    ```
    ```nohighlight
    $ echo "a new change" >> file.txt
    $ git add file.txt
    $ git commit -m "Add a new change"
    ```
    ```nohighlight
    $ git diff master
    diff --git a/file.txt b/file.txt
    index 45b983b..0a978b3 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1,2 @@
     hi
    +a new change
    ```
    ```nohighlight
    $ git log master..foo
    commit 9c249cd4035b675df73e92861afb0c1609d2a74b
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:40:05 2015 +0000
    
        Add a new change
    ```
    ```nohighlight
    $ git checkout master
    ```
    ```nohighlight
    $ git merge foo
    Updating f7d0faa..9c249cd
    Fast-forward
     file.txt | 1 +
     1 file changed, 1 insertion(+)
    ```
    ```nohighlight
    $ git diff master..foo
    ```
    ```nohighlight
    $ echo "starting text" > file.txt
    $ git add file.txt
    $ git commit -m "Add starting text"
    ```
    ```nohighlight
    $ git branch bar
    $ git branch baz
    ```
    ```nohighlight
    $ git checkout bar
    Switched to branch 'bar'
    $ echo "bar text" > file.txt
    $ git add file.txt
    $ git commit -m "Add bar text"
    [bar 3557270] Add bar text
     1 file changed, 1 insertion(+), 1 deletion(-)
    $ git checkout baz
    Switched to branch 'baz'
    $ echo "baz text" > file.txt
    $ git add file.txt
    $ git commit -m "Add baz text"
    [baz e76619d] Add baz text
    1 file changed, 1 insertion(+), 1 deletion(-)
    ```
    ```nohighlight
    $ git checkout master
    Switched to branch 'master'
    $ git merge bar
    Updating feac207..1f2e058
    Updating 0c4320f..3557270
    Fast-forward
     file.txt | 2 +-
     1 file changed, 1 insertion(+), 1 deletion(-)
    $ git merge baz
    Auto-merging file.txt
    CONFLICT (content): Merge conflict in file.txt
    Automatic merge failed; fix conflicts and then commit the result.
    ```
    ```nohighlight
    $ git status
    On branch master
    You have unmerged paths.
      (fix conflicts and run "git commit")
    
    Unmerged paths:
      (use "git add <file>..." to mark resolution)
    
      both modified:      file.txt
    
    no changes added to commit (use "git add" and/or "git commit -a")
    $ cat file.txt 
    <<<<<<< HEAD
    bar text
    =======
    baz text
    >>>>>>> baz
    ```
    ```nohighlight
    $ vim file.txt
    $ cat file.txt 
    baz text
    ```
    ```nohighlight
    $ git log -p
    commit 7c5d054732577aa89581e505e4468928a1a88e3b
    Merge: 3557270 e76619d
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:52:41 2015 +0000
    
        Merge branch 'baz'
        Conflicts:
          file.txt
    
    commit e76619db788991b25c68a1290b37848bbc692d17
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:46:17 2015 +0000
    
        Add baz text
    
    diff --git a/file.txt b/file.txt
    index d2bc3f2..a67f6b2 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1 @@
    -starting text
    +baz text
    
    commit 355727053e3f85b758c7d3d82f9167e154067476
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:45:26 2015 +0000
    
        Add bar text
    
    diff --git a/file.txt b/file.txt
    index d2bc3f2..132d0f8 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1 @@
    -starting text
    +bar text
    
    commit 0c4320fa52e32c23bde122200737bf8b71769de5
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:43:02 2015 +0000
    
        Add starting text
    
    diff --git a/file.txt b/file.txt
    index 0a978b3..d2bc3f2 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1,2 +1 @@
    -hi
    -a new change
    +starting text
    
    commit 9c249cd4035b675df73e92861afb0c1609d2a74b
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:40:05 2015 +0000
    
        Add a new change
    
    diff --git a/file.txt b/file.txt
    index 45b983b..0a978b3 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1,2 @@
     hi
    +a new change
    
    commit f7d0faa478b7b2ee19feba9c0d76bebfab37b061
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:32:07 2015 +0000
    
        Revert "Update file.txt"
        This reverts commit 06abe628a703ed148bfcf21c45efdd2283609d40.
    
    diff --git a/file.txt b/file.txt
    index 3b097cd..45b983b 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1,2 +1 @@
     hi
    -world
    
    commit 06abe628a703ed148bfcf21c45efdd2283609d40
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:27:42 2015 +0000
    
        Update file.txt
    
    diff --git a/file.txt b/file.txt
    index 45b983b..3b097cd 100644
    --- a/file.txt
    +++ b/file.txt
    @@ -1 +1,2 @@
     hi
    +world
    
    commit c9b26e67839d1e53b017b4a02c55bb8e7f4eefec
    Author: Erik Eldridge <erik@example.com>
    Date:   Fri Mar 13 04:22:00 2015 +0000
    
        Add file
    
    diff --git a/file.txt b/file.txt
    new file mode 100644
    index 0000000..45b983b
    --- /dev/null
    +++ b/file.txt
    @@ -0,0 +1 @@
    +hi
    ```
```nohighlight
$ ssh-keygen -t rsa -C "erik@example.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/vagrant/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/vagrant/.ssh/id_rsa.
Your public key has been saved in /home/vagrant/.ssh/id_rsa.pub.
The key fingerprint is:
5a:d6:2f:b1:99:5e:c6:41:0f:e2:c1:69:81:61:8e:ca erik@example.com
The key's randomart image is:
+--[ RSA 2048]----+
|        oo.      |
|       +.. o     |
|      . . * o    |
|   . .   + + o   |
|    E   S + . .  |
|       +   B .   |
|      .   = =    |
|         . +     |
|          .      |
+-----------------+
$ eval "$(ssh-agent -s)"
Agent pid 2244
$ ssh-add ~/.ssh/id_rsa
Identity added: /home/vagrant/.ssh/id_rsa (/home/vagrant/.ssh/id_rsa)
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAKEDM4noIPCkpjk39KrfSz0y4zFJVsiP7gv0Wazi1+uAP/np0WR82ylWK8TTBY6M6LrcYESkl4T4ssLOdDpUrH6jlvLhbBVYjjwPA+omVniAb2kgXGLFwIVIDTqHjNqNtoBzXEGgN5aU4/1sXvcsuEU5kxRq/1fM9XOxJvniLgcbQ5egD/aa6VYd9zqEekNeNqalg6ehXXiw6tSe3D/lFs2NxQn56tt0DQGZwrmXc36ziFEEM7rpcZX5iPFvDhr/6mp4fU93IXikSiWrVXkIzjVHQi23JkYX17nxIEWVzpRXZT/W9A8fQrZOBILKqyK+mtF+a4BrF0sPdUC8hxvxjHT erik@example.com
```
```nohighlight
$ git remote add origin git@github.com:erikeldridge/cst-395-example.git
```
    ```nohighlight
    $ git push -u origin master
    Warning: Permanently added the RSA host key for IP address '192.30.252.131' to the list of known hosts.
    Counting objects: 20, done.
    Compressing objects: 100% (8/8), done.
    Writing objects: 100% (20/20), 1.48 KiB | 0 bytes/s, done.
    Total 20 (delta 3), reused 0 (delta 0)
    To git@github.com:erikeldridge/cst-395-example.git
     * [new branch]      master -> master
    ```
```nohighlight
$ java Generator 1 erik@example.com
[martha@example.com, alex@example.com, erik@example.com]
```
```nohighlight
$ cd ~
$ git clone https://github.com/<github username>/<repository name>.git
```
```nohighlight
$ cd <repository name>
$ javac Generator.java
$ java Generator 1 erik@example.com
[martha@example.com, alex@example.com, erik@example.com]
```
    ```nohighlight
    $ git pull origin master
    remote: Counting objects: 3, done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (3/3), done.
    From github.com:erikeldridge/cst-395-example
     * branch            master     -> FETCH_HEAD
       7c5d054..0c3e437  master     -> origin/master
    Updating 7c5d054..0c3e437
    Fast-forward
     file.txt | 1 +
     1 file changed, 1 insertion(+)
    ```
* We're using Github for this book, but [Bitbucket](https://bitbucket.org/) is a comparable product