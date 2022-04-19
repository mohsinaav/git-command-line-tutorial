# Git-command-line-tutorial
A tutorial on how to perform various operations on git, using command line terminal instead of GUI.

There could be different scenarios where we can use git. We will handle them separately and list the commands here. 

### Scenario 1: You have a remote project and want to keep track of it

1. Initialize git on the local folder. 
        
        git init
    
    In case if you want to remove the git folder from the directory, use:
        
        rmdir .git
     
    Or if there are subfolders, you can use:
      
        rmdir /s .git
      
2. To check the status of the current folder, use:
        
        git status

3. Once the folder is ready and you have made all the necessary changes, we need to put all changes to the staging area from the current working directory. 
    
        git add -A
        
    ** command '-A' will add all files to the staging area. In case, if we need to stage each file
    one by one, replace '-A' with the filename.     
    To remove files from staging are:
    
        git reset <file name>

4. Next phase involves commit. All the staged changes are commited locally. Consider it as taking a snapshit of the project in its current status. 
      
        git commit -m "message"
      
     ** descriptive messages will be helpful in the later stages.

5. To get the log of all the changes done till now, we can use the following command: 
      
        git log

  
### Scenario 2: Cloning a remote repository

1. Suppose, we need to clone a remote repository say from github.

        git clone <url> <where to clone>
        
    Eg: git clone https://github.com/mohsinaav/TodoList.git .

    ** use . , if you are in the current destination directory
    
2. Some commands to get information about the remote repository includes:
    
        git remote -v    
        git branch -a
        
3. Once all the necessary changes are made to the local repository, staged and committed, now it's time to push those changes. 
        
        git diff
        
    The above command will show all the changes made recently or after the last push. Before pushing any changes, make sure to pull the recent changes from the remote repository, as there are possibilities of changes done by other contributors. 
  
        git pull origin master
        
    After making sure that the remote and local repos are in sync, other than the changes made by us, we can push it. Pushing step sends the recent commit history from the local repository up to GitHub.
        
        git push origin master
        
4. Better approach to this scenario is to create a new branch and make required changes for desired feature. Once all testing and code requirements are met, we can push and merge it to the master branch.

    To create a new branch, use:
    
         git branch <new_branch_name>
      
    Now, to start working on this branch, we need to check it out.
  
         git checkout <new_branch_name>
  
    As done earlier, once modifications are completed in the new branch, stage and commit it first. After that push it into the master
        
          git push -u origin <new_branch_name>
          
5. Till now, we have pushed the changes done in the new_branch from local to remote, next we need to merge this new branch to the master and resolve any conflicts if any.

    For this, we need to switch to the master branch.
          
          git checkout <master - branch to be merged into>
          
     As mentioned earlier, it is a best practice to always pull the changes before pushing anything.
          
          git pull origin master
  
     The following command will list all the branches that has been merged yet.
          
          git branch --merged

     Now, we can merge the `new_branch_name` to the master branch.
     
          git merge <new_branch _name>
          
     After that, push the master branch to make changes accessible everywhere.
            
          git push origin master
          
      
6. Once the feature request is completed, we can delete that branch.

          git branch -d <new_branch _name>
          
  The above command deleted the new_branch_name locally, but we should also delete it in the remote repository, once it is not necessary anymore.
          
          git push origin --delete sample_division
          
We still need to discuss about many more features like conflicts during merging, etc, which we will do it in the future post.




