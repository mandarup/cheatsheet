Cheatsheet


# Shell

## File Transfer
```
   # copy from remote to local
   # -r Recursively copy entire directories
   $ scp -r user@your.server.example.com:/path/to/foo /home/user/Desktop/
```

## Run program in background, detached from shell

  - Existing process

``` 
    #suspend
    $control + z  
    
    #send to background —> 
    $bg
    
    #disown —>  
    $disown -h [job-spec]    (like %1)
```    

  - Start a new processes in background and detached


```
    $nohup yourprocess & tail -f nohup.out
```

## Select Kill Multiple Processes
```
    $ps uax | grep  <username-string> 
    
    #Select all process pids 
    $kill -9 <pid1> .. <pidN>
    
    # kill all process from specific script, e.g. `some_script.py`
    $ kill -9 `ps aux | grep  some_script.py | grep -v grep | awk '{print $2}'`
```    
    
## Diff two files - side by side
```
    $vimdiff file1 file2
 ```
 
 
## copy files local to remote

http://unix.stackexchange.com/questions/70581/scp-and-compress-at-the-same-time-no-intermediate-save

```
    $rsync  -z  file/to/copy  username@atlas1:/home/username/path/to/destination
```


# Git


## Git Graph

```
    $git log --graph --date-order -C -M --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"
    #Or 
    #With timestamp without sorting
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"
    #Or 
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"
    
    #Best
    git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

## Misc Git Commands


```
    #Git merge append message with log of all commits being merge
    $git merge <branch> --log --no-ff
    # remove file from git without deleting it
    $git rm -r --cached <your directory>
    # Rename folder
    $git mv <old name> <new name>
    
    # Remove file from entire git history 
    # Note: this deletes the file from disk
    $git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch .gmail/gmail_credentials.yml' \ 
     --prune-empty --tag-name-filter cat -- --all
```    
    
## Procedure for pushing to github

```
    $git fetch upstream
    $git checkout master
    $git merge upstream/master
    $git fetch origin
    $git merge origin/master
    $git push origin master
    # log on to github, create pull request, and merge pull request
    # then back to console
    
    # pushing all tags
    $git push origin --tags
    $git push upstream --tags
```

## python virtualenv


http://docs.python-guide.org/en/latest/dev/virtualenvs/


## creating python package

https://github.com/aiquest/python-starter-package

# above uses following refs
http://python-packaging.readthedocs.io/en/latest/everything.html
https://gehrcke.de/2014/02/distributing-a-python-command-line-application/


# sphinx docs


http://gisellezeno.com/tutorials/sphinx-for-python-documentation.html

```
    $cd /path/to/project/docs/dir/
    $sphinx-apidoc -f -o source/ ../srcdir/
    
    
    # make html
    $make html
    
    #make tex-pdf
    $make latexpdf
    
    #or
    $make tex
```

# GPU


```
    $watch -n 1 nvidia-smi
```

# Download entire website


```
    $wget -r --no-parent http://site.com/songs/
```

# Docker


```
    # get docker container id using
    $docker ps
    
    # use that container id
    $sudo docker ps <container-id>
    $sudo docker commit --message "update pandas, tensorflow version, cuda paths" <container_id> <REPOSITORY>:<TAG>
    
    # check the images (optional)
    $sudo docker images {rhel7 shows the new image ID as the image has been updated}    
 ```
