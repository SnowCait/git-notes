# Git Commands

## ブランチ削除
```
$ git branch --merged | grep -v \* | xargs git branch -d
```
