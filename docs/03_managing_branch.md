# Managing branch

## Create branch

```bash
git switch -c new-branch
Switched to a new branch 'new-branch'
```

```bash
git branch
  master    
* new-branch

git log --all --oneline --graph
* ad868d6 (HEAD -> new-branch, master) Revert "Add CONTRIBUTING.md"
* 229c494 Add CONTRIBUTING.md                                      
* 1a40269 Update README.md                                         
* c6ca7bb Initial commit                                           
```

## Rename branch

```bash
git branch -m update-contribution
```

```bash
git branch
  master             
* update-contribution
```

:warning: **Do not** use this command to public branch

## Merge branch

```bash
echo "Your name" >> CONTRIBUTING.md
git add .
git commit
```

```bash
git log --all --oneline --graph
* fd896ce (HEAD -> update-contribution) Add CONTRIBUTING.md
* ad868d6 (master) Revert "Add CONTRIBUTING.md"            
* 229c494 Add CONTRIBUTING.md                              
* 1a40269 Update README.md                                 
* c6ca7bb Initial commit                                   
```

Merge master branch into update-contribution.

```bash
git switch master
git merge update-contribution
```

```bash
git log --all --oneline --graph
* fd896ce (HEAD -> master, update-contribution) Add CONTRIBUTING.md
* ad868d6 Revert "Add CONTRIBUTING.md"                             
* 229c494 Add CONTRIBUTING.md                                      
* 1a40269 Update README.md                                         
* c6ca7bb Initial commit                                           
```

## Drop branch

```bash
git branch -d update-contribution
Deleted branch update-contribution (was fd896ce).
```

```bash
git log --all --oneline --graph
* fd896ce (HEAD -> master) Add CONTRIBUTING.md
* ad868d6 Revert "Add CONTRIBUTING.md"        
* 229c494 Add CONTRIBUTING.md                 
* 1a40269 Update README.md                    
* c6ca7bb Initial commit                      
```
