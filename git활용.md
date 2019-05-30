### git (index - commit - push)



```
$ git init
```



```
$ git remote add git 
remote add [<options>] <name> <url>

    -f, --fetch           fetch the remote branches
    --tags                import all tags and associated objects when fetching
                          or do not fetch any tag at all (--no-tags)
    -t, --track <branch>  branch(es) to track
    -m, --master <branch>
                          master branch
    --mirror[=(push|fetch)]
                          set up remote as a mirror to push to or fetch from

```



```
$ git remote add origin <URL>
```



```
$ git remote -v
```



```
$ git pull
```

master branch pull



```
$ get add .
```

index



```
$ git status
```

On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)



```
$ git commit -m "file name"
```



```
$ git status
```

On branch master
nothing to commit, working tree clean



```
$ git push origin master
# git push --set-upstream origin master
```

fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

...

 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/pillarorigin/hello-world.git'

    $ git lfs install

Updated git hooks.
Git LFS initialized.



```
$ git lfs track "*.pdf"
```

Tracking "*.pdf"



```
$ git add . 
```



```
$ git commit -m "file name"
```



```
$ git push origin master
```

