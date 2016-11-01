# frequently-used-commands






Send active program to background
---------------------------------
.. code :: sh

    #suspend
    $control + z  
    
    #send to background —> 
    $bg
    
    #disown —>  
    $disown -h [job-spec]    (like %1)






Select Kill Multiple Processes
------------------------------
.. code :: sh

    $ps uax | grep  <username-string> 
    
    #Select all process pids 
    $kill -9 <pid1> .. <pidN>



Git
---

Git Graph
~~~~~~~~~
.. code :: sh

    $git log --graph --date-order -C -M --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"

    #Or 
    #With timestamp without sorting
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"

    #Or 
    $git log --decorate --graph --oneline --all --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s"


Misc Git Commands
~~~~~~~~~~~~~~~~~

.. code :: sh

    #Git merge append message with log of all commits being merge
    $git merge <branch> --log --no-ff


    # remove file from git without deleting it
    $git rm -r --cached <your directory>


    # Rename folder
    $git mv <old name> <new name>



Procedure for pushing to github
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code :: sh

    $git fetch upstream
    $git merge upstream/master
    $git push origin master







Diff two files - side by side
----------------------------
.. code :: sh

    $vimdiff file1 file2




copy files local to remote
---------------------------
http://unix.stackexchange.com/questions/70581/scp-and-compress-at-the-same-time-no-intermediate-save

.. code :: sh

    $rsync  -z  file/to/copy  username@atlas1:/home/username/path/to/destination






# python virtualenv
http://docs.python-guide.org/en/latest/dev/virtualenvs/


# creating python package
http://python-packaging.readthedocs.io/en/latest/everything.html
https://gehrcke.de/2014/02/distributing-a-python-command-line-application/




# sphinx docs
http://gisellezeno.com/tutorials/sphinx-for-python-documentation.html


# cd to /project/docs/dir/
sphinx-apidoc -f -o source/ ../riskscore/




#------------------------------------------------------------------------------------------------------------
# github push process


git fetch upstream
Git checkout master
Git merge upstream master
Git push


# log on to github, create pull request, and merge pull request
# then back to console
git fetch upstream
Git checkout master
Git merge upstream master
Git push


#------------------------------------------------------------------------------------------------------------




# Download entire website
wget -r --no-parent http://site.com/songs/




