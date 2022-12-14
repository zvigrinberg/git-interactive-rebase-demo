# git-interactive-rebase-demo
## Procedure
from main branch, Kindly run
```shell
   git init
   echo "initial commit" >> initial.out ; git add . ; git commit -m "initial commit"
   git checkout -b feature/rebaseInteractive
   ll
   echo "this is important" >> test-important.out
   git add . ; git commit -m "important commit"
   echo "this is important too but partial" >> test-important-part.out ; git add . ; git commit -m "partial commit"
   echo "this is important too and now i updated it" >> test-important-part.out ; git add . ; git commit -m "partial commit second part"
   echo "this is a totally dummy commit" >> test-dummy.out ; git add . ; git commit -m "dummy commit"
   echo "this is also important too but only part 1" >> test-in-portions.out ; git add . ; git commit -m "first part"
   echo "this is also important too but only part 2" >> test-in-portions.out ; git add . ; git commit -m "second part"
   echo "this is also important too but only part 3" >> test-in-portions.out ; git add . ; git commit -m "third part"
   ll
   cat test-in-portions.out
   echo "this is a totally dummy commit 2" >> test-dummy2.out ; git add . ; git commit -m "dummy commit 2"
   ##git log
   git branch feature/rebaseInteractive-original
   git rebase -i main
   ```
   2. git rebase interactive opened an editor with the following content, the commits on top should be with the following values on the left side:
   ```shell
   pick 5247bfc important commit
   reword 9acd1b3 first part + second part
   fixup 6067828 partial commit second part
   drop 58d9168 dummy commit
   reword a281984 first part + second part + third part
   fixup febfa00 second part
   fixup 2f5cd7a third part
   drop a8669e3 dummy commit 2

   # Rebase e49c1d7..a8669e3 onto e49c1d7 (8 commands)
   #
   # Commands:
   # p, pick <commit> = use commit
   # r, reword <commit> = use commit, but edit the commit message
   # e, edit <commit> = use commit, but stop for amending
   # s, squash <commit> = use commit, but meld into previous commit
   # f, fixup <commit> = like "squash", but discard this commit's log message
   # x, exec <command> = run command (the rest of the line) using shell
   # b, break = stop here (continue rebase later with 'git rebase --continue')
   # d, drop <commit> = remove commit
   # l, label <label> = label current HEAD with a name
   # t, reset <label> = reset HEAD to a label
   # m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
   # .       create a merge commit using the original merge commit's
   # .       message (or the oneline, if no original merge commit was
   # .       specified). Use -c <commit> to reword the commit message.
   #
   # These lines can be re-ordered; they are executed from top to bottom.
   #
   # If you remove a line here THAT COMMIT WILL BE LOST.
   #
   # However, if you remove everything, the rebase will be aborted.
   ```
   3. after editing some commit messages of the two squashes operations, run the following remaining step to merge the rebase to main branch by fast 
      forwarding HEAD
      ```shell   
         git log
         git checkout main 
         ## Generate summary of what is going to be merged into main from feature/rebaseInteractive
         git request-pull -p HEAD ./ feature/rebaseInteractive
         ## Merge          
         git merge feature/rebaseInteractive
         git log
         ll
         cat test-important.out
         cat test-important-part.out
         cat test-in-portions.out
      ```
