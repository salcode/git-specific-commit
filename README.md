# Git Specify a Commit

Specifying a specific commit from your git history can be difficult, these are my notes about how to do it.

You can clone this repository and try these commands for yourself.

## Git Log

The log output below is made with the command

    git log --oneline --graph

See my post, [Improve Git Log](https://salferrarello.com/improve-git-log/), for more information about improving your git log output.

In our history, you can see `feature-c` was developed on a separate branch and merged as a merge commit (i.e. not a fast-forward merge).

```
xxxxxxx README.md
d27e249 D
5d632b0 feature-c
  3e93287 C2
  520118c C3
462cfcd B
55a4cb0 A
30db254 Initial Commit
```

## Example Specifications

In these examples, we are going to use
`git log --oneline --no-walk` which returns a single line of the commit that is specified.

    git log --oneline --no-walk
    README.md
    git log --oneline --no-walk HEAD
    README.md

    git log --oneline --no-walk d27e249
    D
    git log --oneline --no-walk HEAD^1
    D
    git log --oneline --no-walk HEAD^
    D
    git log --oneline --no-walk HEAD~1
    D

    git log --oneline --no-walk 5d632b0
    feature-c
    git log --oneline --no-walk HEAD^^
    feature-c
    git log --oneline --no-walk HEAD~2
    feature-c

    git log --oneline --no-walk HEAD~3
    B
    git log --oneline --no-walk HEAD^^^
    B
    git log --oneline --no-walk 462cfcd
    B

    git log --oneline --no-walk 3e93287
    C2
    git log --oneline --no-walk HEAD^^^2
    C2
    git log --oneline --no-walk HEAD~2^2
    C2

    git log --oneline --no-walk 520118c
    C3
    git log --oneline --no-walk HEAD^^^2^
    C3
    git log --oneline --no-walk HEAD~2^2^
    C3
    git log --oneline --no-walk HEAD~2^2~
    C3
    git log --oneline --no-walk HEAD~2^2~1
    C3

    git log --oneline --no-walk HEAD^^^
    B
    git log --oneline --no-walk HEAD~3
    B

    git log --oneline --no-walk 462cfcd
    B
    git log --oneline --no-walk HEAD^^^2^^
    B
    git log --oneline --no-walk HEAD~2^2^^
    B
    git log --oneline --no-walk HEAD~2^2~2
    B

    git log --oneline --no-walk HEAD^^^^
    A
    git log --oneline --no-walk HEAD~4
    A

    git log --oneline --no-walk HEAD^^^^^
    Initial commit
    git log --oneline --no-walk HEAD~5
    Initial commit

## Git Log with Commit Targets Listed

```
xxxxxxx README.md (HEAD)
d27e249 D (HEAD^1, HEAD^, HEAD~1)
5d632b0 feature-c (HEAD^^, HEAD~2)
  3e93287 C2 (HEAD^^^2, HEAD~2^2)
  520118c C3 (HEAD^^^2^, HEAD~2^2^, HEAD~2^2~, HEAD~2^2~1)
462cfcd B (HEAD^^^, HEAD~3, HEAD^^^2^^, HEAD~2^2^^, HEAD~2^2~2)
55a4cb0 A (HEAD^^^^, HEAD~4)
30db254 Initial Commit (HEAD^^^^^, HEAD~5)
```

## Author

[Sal Ferrarello](https://salferrarello.com) / [@salcode](https://twitter.com/salcode)
