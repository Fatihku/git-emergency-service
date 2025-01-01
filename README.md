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

# RESET
### # To revert changes made to the index (i.e., that you have added), do this. Warning this will reset all of your unpushed commits to master!:
    git reset
    git reset --hard

### # To revert a change that you have committed:
    git revert <commit 1> <commit 2>
    
### # To remove untracked files (e.g., new files, generated files):
    git clean -f
    
### # Or untracked directories (e.g., new or automatically generated directories):
    git clean -fd

### # Re-clone
    GIT=$(git rev-parse --show-toplevel)
    cd $GIT/..
    rm -rf $GIT
    git clone ...
    ✅ Deletes local, non-pushed commits
    ✅ Reverts changes you made to tracked files
    ✅ Restores tracked files you deleted
    ✅ Deletes files/dirs listed in .gitignore (like build files)
    ✅ Deletes files/dirs that are not tracked and not in .gitignore
    😀 You won't forget this approach
    😔 Wastes bandwidth

### # Clean and reset
    git clean --force -d -x
    git reset --hard
    ❌ Deletes local, non-pushed commits
    ✅ Reverts changes you made to tracked files
    ✅ Restores tracked files you deleted
    ✅ Deletes files/dirs listed in .gitignore (like build files)
    ✅ Deletes files/dirs that are not tracked and not in .gitignore

### # Clean
    git clean --force -d -x
    ❌ Deletes local, non-pushed commits
    ❌ Reverts changes you made to tracked files
    ❌ Restores tracked files you deleted
    ✅ Deletes files/dirs listed in .gitignore (like build files)
    ✅ Deletes files/dirs that are not tracked and not in .gitignore

### # Reset
    git reset --hard
    ❌ Deletes local, non-pushed commits
    ✅ Reverts changes you made to tracked files
    ✅ Restores tracked files you deleted
    ❌ Deletes files/dirs listed in .gitignore (like build files)
    ❌ Deletes files/dirs that are not tracked and not in .gitignore
    
#  SOURCES    
S: https://www.quora.com/How-can-I-recover-a-file-I-deleted-in-my-local-repo-from-the-remote-repo-in-Git
S: https://www.freecodecamp.org/forum/t/push-a-new-local-branch-to-a-remote-git-repository-and-track-it-too/13222
S: https://stackoverflow.com/questions/1146973/how-do-i-revert-all-local-changes-in-git-managed-project-to-previous-state
