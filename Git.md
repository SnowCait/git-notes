# Git

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

## パーミッション
- [Gitで空のディレクトリを管理する方法の復習｜リスティング広告運用代行専門｜カルテットコミュニケーションズ](https://quartet-communications.com/info/topics/13642)
- [git bashでディレクトリごと実行権限を付与する - Qiita](https://qiita.com/70_/items/6986a1b1b24004d32af4)

## .gitignore
- [[Git] 自分の環境だけgitignoreする方法（2つ） - YoheiM .NET](https://www.yoheim.net/blog.php?q=20160510)
  - `.git/info/exclude`
  - `~/.gitconfig` `core.excludesfile`

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

## 操作が重い
- `git fsck`
- `git gc`

## 巨大リポジトリ
5GB を超えるリポジトリを扱うには。

### 課題
- `git clone[push]` が重い、失敗する
- `git status` が重い

### 対策
- [明日から出来る重い Gitレポジトリへの対抗策 - Qiita](https://qiita.com/aeroastro/items/9ed7a41f52362b31a01c)
- [How to handle big repositories with Git | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/big-repositories)
- the remote end hung up unexpectedly
  - [git cloneで「the remote end hung up unexpectedly」エラーが出たときの3つの対処方法！「http.postBuffer」を変更しても解決しなかったときに読む | Course out](https://dream-target.jp/2019/03/17/git_remote_end_hung_up/)
  - [gitで大きいサイズのファイルを扱う時 - Qiita](https://qiita.com/akiko-pusu/items/2d65a54e9d2a6c7f9d13)
    - `git clone –depth 1` > `git fetch –unshallow`
    - `git config http.postBuffer 157286400`
- [【Git】push 時に fatal: the remote end hung up unexpectedly が出たときの対応 | | ぶろねこ -Blog on NEKOTEAM-](https://blog.nekoteam.com/?p=1993)
- [パーシャルクローンとシャロークローンを活用しよう - GitHubブログ](https://github.blog/jp/2021-01-13-get-up-to-speed-with-partial-clone-and-shallow-clone/)

### 関連
https://github.com/SnowCait/git-notes/blob/master/GitHubActions.md#%E5%B7%A8%E5%A4%A7%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%82%92%E6%89%B1%E3%81%86%E6%96%B9%E6%B3%95

## Sparse checkout
- [git sparse checkout で clone せずに一部のサブディレクトリだけを pull/checkout する](https://mseeeen.msen.jp/git-sparse-checkout/)
- [リポジトリの一部だけcheckoutするGitコマンド：sparse-checkout - はんなりと、ゆるやかに](https://iucstscui.hatenablog.com/entry/2020/05/21/090321)

## Tracking branch
- [Git のトラッキングブランチの確認と設定方法 - yu8mada](https://yu8mada.com/2018/08/11/how-to-confirm-and-set-up-tracking-branches-in-git/)

## Out of memory
- [[git] push におけるメモリ不足回避 | Tech控え帳](https://www.chihayafuru.jp/tech/index.php/archives/1238)

## Branch
- [Gitのブランチの作成者を調べる方法（結論：おそらく方法はない） | ちこの資格取得日記](https://chico-shikaku.com/2019/11/investigate-git-branch-creator/)

## マージ
- [git mergeでコンフリクトが発生するか前もって調べる方法 - Qiita](https://qiita.com/horimislime/items/84fa431460c8d39f37e6)

## 仕組み
- [Gitオブジェクトの中身 - Qiita](https://qiita.com/nkshigeru/items/eb2b6f758c2707757738)
- [Gitのコミットの裏側で起こっていること - LIVESENSE ENGINEER BLOG](https://made.livesense.co.jp/entry/2017/08/22/080000)

## Bisect
- [git bisect で問題箇所を特定する - Qiita](https://qiita.com/usamik26/items/cce867b3b139ea5568a6)
- [問題のあるコミットを特定する ( git bisect ) - Qiita](https://qiita.com/Shaula/items/1e13808946d8ca8bacbc)
