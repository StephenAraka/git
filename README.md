# git
## git techniques and shortcuts 

### add and commit
git config --global alias.ac "commit -am"__
git ac "message"

### amend prev
CHANGE MESSAGE
git commit --amend -m "new message"

CHANGE STAGED BUT NOT MESSAGE 
git add .
git commit --amend --no-edit

### revert changes made to origin
git revert <commit_no> - note: doesnt remove original commit from history

### STASH
ADD TO STASH
git stash

REMOVE FROM STASH
git stash pop

SAVE STASH WITH NAME
git stash save <name>

SHOW LIST
git stash list

APPLY FROM LIST
git stash apply <index> - starts at 0
  
### RENAME BRANCH
git branch -M <new_name>
  

### LOGGING
SEE MORE READABLE BREAKDOWN AND BRANCHES
git log --graph --oneline --decorate
  
  
### BISECT
TO FIND BAD COMMIT
git bisect start
git bisect bad
git bisect good <commit_id>
git bisect bad
  
### SQUASHING COMMITS
SQUASH
git rebase master --interactive
  // git will pullup a file with feature commits, change pick to squash, close file
  // git will pull up another file with default squashed messages, update commit message, close file
  
FIXUP
git commit --fixup <commit_id>
git rebase -i --autosquash
  
### HOOKS
contains scripts that can be configured to run when different events in git happen
for js, husky is a package that makes it easier to configure git hooks
  
e.g. 
  npm i husky -D
  npm set-script prepare "husky install"
  npm run prepare
  
  Add a hook:
  npx husky add .husky/pre-commit "npm test"
  git add .husky/pre-commit
  
  Make a commit:
  git commit -m "Keep calm and commit" // `npm test` will run everytime you commit
  
  
### DESTRUCTION / DELETING
  Replace everything local with remote:
  git fetch origin
  git reset --hard origin/master
  git clean -df     // remove more random untracked files and build artifacts
  
### SICK OF IT ALL?
  rm -rf .git       // delete git folder
