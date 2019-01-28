# Git Commands

## ブランチ削除

### ローカル
```
git branch --merged | grep -v \* | xargs git branch -d
```

### リモート
```
git branch -a --merged | grep remotes/origin/ | grep -v -e remotes/origin/master -e remotes/origin/HEAD | sed -e 's%remotes/origin/\(.\)%\1%g' | tr "\n" " " | xargs git push --delete origin
```
https://qiita.com/RyochanUedasan/items/99103da5b45cf85b626a
