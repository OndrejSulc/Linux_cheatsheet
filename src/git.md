# Git tricks

- gitk


Pull all submodules accordign to .gitmodules branch
```
git submodule update --remote --recursive
```


Search history of one file (or submodule)
```
git log -p -- <file>
```

# TIG

Commit history tree
```
tig
```

Jump to specific commit
```
:goto <commit-hash>
```
