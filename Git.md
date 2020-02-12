# Git

## クライアント
- コマンドライン
- GitHub Desktop
- TortoiseGit
- SourceTree
- GitKraken
- Fork
- [Jasper](https://jasperapp.io/)
- [gmaster](https://gmaster.io/)
- [Sublime Merge](https://www.sublimemerge.com/)
- IDE 付属
  - Visual Studio
  - JetBrains

### コマンドライン
- 基本
- 何でもできる
- `git graph` エイリアスは設定しておく

### GitHub Desktop
- シンプル
- [github.com](https://github.com/) からクローンができる

### Fork
- 一通りの機能が揃っている
- rebase 時にバックアップブランチを作成してくれる
- ググラビリティが低い
- `git remote` ができない

### SourceTree
- 一通りの機能が揃っている
- 重い

## 設定
- `core.autocrlf`
  - CRLF じゃないと動かないファイルが存在するケースがあるので `false` 推奨
  - Windows 系のファイル（バッチファイル等）が含まれていなければ `input` でも可
  - `true` にするメリットは特にない
    - 仮想環境でシェルスクリプトを動かそうとしたときに CRLF になって動かない
  - [.gitattributesで改行コードの扱いを制御する](https://qiita.com/nacam403/items/23511637335fc221bba2)
- `core.ignorecase`
  - `false` にしておいた方が無難
  - ファイルは `git mv -f file.txt File.txt` で変更できる
  - ディレクトリは一度別名にするしかなさそう
- `core.pager`
  - Windows 環境で日本語が文字化けする場合は `git config --global core.pager "LESSCHARSET=utf-8 less"`
  - [git diff や git status での日本語の文字化けを防ぐ | まくまくGitノート](https://maku77.github.io/git/settings/garbling.html)

## SSH
- [git clone 時に秘密鍵を指定する - Qiita](https://qiita.com/sonots/items/826b90b085f294f93acf)

## SVN との比較

### メリット
- ブランチ開発をしやすい
  - ブランチの切り替えが高速
  - PR 文化

### デメリット
- 一部だけをクローンできない
  - 10GB を超えるリポジトリを扱いづらい
- 容量の大きなファイルを扱いづらい

## パッチ
- [Git で変更を patch ファイルにする / patch コマンドで適用する](https://qiita.com/sea_mountain/items/7d9c812e68a26bd1a292)

## メンテナンス
- [BFG Repo-Cleaner](https://rtyley.github.io/bfg-repo-cleaner/)
  - [BFGを使用するにあたって色々調べてみた](http://yuki10.hatenablog.com/entry/2017/01/14/211430)

## 推奨ルール
- 基本的に force push はしない
  - 履歴が改変されてしまう
    - コミットハッシュが変わる
    - レビューコメントに対する修正差分が分からなくなる

## 巨大リポジトリ
5GB を超えるリポジトリを扱うには。

### 課題
- `git clone` が重い
- `git status` が重い

### 対策
- [明日から出来る重い Gitレポジトリへの対抗策 - Qiita](https://qiita.com/aeroastro/items/9ed7a41f52362b31a01c)
- [How to handle big repositories with Git | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/big-repositories)

### 関連
https://github.com/SnowCait/git-notes/blob/master/GitHubActions.md#%E5%B7%A8%E5%A4%A7%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%82%92%E6%89%B1%E3%81%86%E6%96%B9%E6%B3%95

## Sparse checkout
- [git sparse checkout で clone せずに一部のサブディレクトリだけを pull/checkout する](https://mseeeen.msen.jp/git-sparse-checkout/)
