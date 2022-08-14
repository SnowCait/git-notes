# Git Commands

## ブランチ削除

### ローカル
Bash
```bash
git branch --merged | grep -v \* | grep -v master | xargs git branch -d
```

PowerShell
```powershell
git for-each-ref --format '%(refname:short)' refs/heads --merged | ForEach-Object { If("develop","master" -notcontains $_) { git branch $_ -d } }
git branch --merged | Select-String -NotMatch '\*' | % { git branch -d $_.ToString().Trim() }
```

### リモート
```bash
git branch -a --merged | grep remotes/origin/ | grep -v -e remotes/origin/master -e remotes/origin/HEAD | sed -e 's%remotes/origin/\(.\)%\1%g' | tr "\n" " " | xargs git push --delete origin
```
https://qiita.com/RyochanUedasan/items/99103da5b45cf85b626a

## 含まれているか

```bash
git branch --merged | grep <branch>
git branch --contains <sha> | grep <branch>
```

## 改行コード確認
```
git ls-files --eol
```

## git cat-file
- [[Git]git cat-fileで任意のブランチの任意のファイルを閲覧できるので便利 · DQNEO起業日記](http://dqn.sakusakutto.jp/2013/06/git_cat-file.html)

## リポジトリの情報

```shell
# ファイル数
git ls-files | wc -l

# 容量
gh api repos/{owner}/{repo} --jq '.size'
```
