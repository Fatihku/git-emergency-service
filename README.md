# Git Emergency Service

# DELETE BRANCH
### # Delete a local GIT branch:
#### - Soft
    git branch -d <branchname>
#### - Force
    git branch -D <branchname>
    - or
    git branch -d --force <branchname>
    - or
    git branch --delete --force <branchname>

### # Delete a remote GIT branch:
    git push origin --delete <branchname>
    
# PUSH BRANCH
### # Push a new local branch to a remote Git repository and track it too
    git push -u origin <branchname>
    
# RENAME BRANCH
### # Rename a Branch
    git branch -m <oldbranchname> <newbranchname>

# RECOVER
### # Recover a deleted file in local repo 
#### - If the deletion has not been committed, the command below will restore the deleted file in the working tree.
    git checkout -- <filename>
#### - You can get a list of all the deleted files in the working tree using the command below.
    git ls-files --deleted

#### - If the deletion has been committed, find the commit where it happened, then recover the file from this commit.
    git rev-list -n 1 HEAD -- <file>
    git checkout <commit>^ -- <file>

#### - In case you are looking for the path of the file to recover, the following command will display a summary of all deleted files.
    git log --diff-filter=D --summary
    
#  SOURCES    
S: https://www.quora.com/How-can-I-recover-a-file-I-deleted-in-my-local-repo-from-the-remote-repo-in-Git
S:https://www.freecodecamp.org/forum/t/push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too/13222
