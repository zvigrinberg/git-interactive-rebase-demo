# git-interactive-rebase-demo
## Procedure
from main branch, Kindly run
```shell
   git checkout -b feature/rebaseInteractive
   ll
   echo "this is important" >> test-important.out
   git add . ; git commit -m "important commit"
   echo "this is important too but partial" >> test-important-part.out ; git add . ; git commit -m "partial commit"
   echo "this is important too and now i updated it" >> test-important-part.out ; git add . ; git commit -m "partial commit second part"
   echo "this is a totally bullshit commit" >> test-bullshit.out ; git add . ; git commit -m "bullshit commit"
   git log
   echo "this is also important too but only part 1" >> test-in-portions.out ; git add . ; git commit -m "first part"
   echo "this is also important too but only part 2" >> test-in-portions.out ; git add . ; git commit -m "second part"
   echo "this is also important too but only part 3" >> test-in-portions.out ; git add . ; git commit -m "thid part"
   ll
   cat test-in-portions.out
   git commit --amend
   git log
   echo "this is a totally bullshit commit 2" >> test-bullshit2.out ; git add . ; git commit -m "bullshit commit 2"
   git log
   git rebase -i main
   git log
   git checkout main ; git merge feature/rebaseInteractive
   git log
   ll
   cat test-important.out
   cat test-important-part.out
   cat test-in-portions.out
```
