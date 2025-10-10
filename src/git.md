# Git tricks

- gitk


Pull all submodules accordign to .gitmodules branch
```
git submodule update --remote --recursive
```

Pull all submodules according to commit
```
git submodule update  --recursive
```

reset hard all submodules
```
git submodule foreach --recursive git reset --hard
```

Search history of one file (or submodule)
```
git log -p -- <file>
```

Check history of checkouts
```
git reflog | grep checkout
```

# TIG

Commit history tree
```
tig
```

Help
```
esc + h
```

Options
```
Option toggling:
    shift + D :toggle date
    shift + A :toggle author
    shift + X :toggle id
    shift + G :toggle commit-title-graph
```




Jump to specific commit
```
:goto <commit-hash>
```

Controls:
```
arrow up,down = prev, next commit
INS and DEL = scrolling in selected commit by one line
PGUP PGDN = scrolling in selected commit

```
