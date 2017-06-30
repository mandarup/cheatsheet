Cheatsheet
----------


.. contents:: Table of Contents
   :depth: 2



Run program in background, detached from shell
----------------------------------------------

1. Existing process
~~~~~~~~~~~~~~~~~~~

.. code:: sh

    
    #suspend
    $control + z  
    
    #send to background —> 
    $bg
    
    #disown —>  
    $disown -h [job-spec]    (like %1)


2. Start a new processes in background and detached
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: sh

    $nohup yourprocess & tail -f nohup.out




Select Kill Multiple Processes
------------------------------
.. code:: sh

    $ps uax | grep  <username-string> 
    
    #Select all process pids 
    $kill -9 <pid1> .. <pidN>



Git
---

Git Graph
~~~~~~~~~
.. code:: sh

    $git log --graph --date-order -C -M --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"

    #Or 
    #With timestamp without sorting
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"

    #Or 
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"
    
    #Best
    git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit


Misc Git Commands
~~~~~~~~~~~~~~~~~

.. code:: sh

    #Git merge append message with log of all commits being merge
    $git merge <branch> --log --no-ff


    # remove file from git without deleting it
    $git rm -r --cached <your directory>


    # Rename folder
    $git mv <old name> <new name>
    
    



Procedure for pushing to github
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code:: sh

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



Diff two files - side by side
----------------------------
.. code:: sh

    $vimdiff file1 file2




copy files local to remote
---------------------------
http://unix.stackexchange.com/questions/70581/scp-and-compress-at-the-same-time-no-intermediate-save

.. code :: sh

    $rsync  -z  file/to/copy  username@atlas1:/home/username/path/to/destination



python virtualenv
-----------------
http://docs.python-guide.org/en/latest/dev/virtualenvs/


creating python package
-----------------------
https://github.com/aiquest/python-starter-package

# above uses following refs
http://python-packaging.readthedocs.io/en/latest/everything.html
https://gehrcke.de/2014/02/distributing-a-python-command-line-application/


sphinx docs
~~~~~~~~~~~
http://gisellezeno.com/tutorials/sphinx-for-python-documentation.html

.. code:: sh

    $cd /path/to/project/docs/dir/
    $sphinx-apidoc -f -o source/ ../srcdir/
    
    
    # make html
    $make html
    
    #make tex-pdf
    $make latexpdf
    
    #or
    $make tex



GPU
---

.. code:: sh

    $watch -n 1 nvidia-smi


Download entire website
-----------------------

.. code:: sh

    $wget -r --no-parent http://site.com/songs/



Docker
------

.. code:: sh

    # get docker container id using
    $docker ps
    
    # use that container id
    $sudo docker ps <container-id>
    $sudo docker commit --message "update pandas, tensorflow version, cuda paths" <container_id> <REPOSITORY>:<TAG>

    
    # check the images (optional)
    $sudo docker images {rhel7 shows the new image ID as the image has been updated}    
    
    


