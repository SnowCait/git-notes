# Git

## クライアント
- コマンドライン
- GitHub Desktop
- TortoiseGit
- SourceTree
- Fork
- [Jasper](https://jasperapp.io/)

## 設定
- `core.autocrlf`
  - CRLF じゃないと動かないファイルが存在するケースがあるので `false` 推奨
  - Windows 系のファイル（バッチファイル等）が含まれていなければ `input` でも可
  - `true` にするメリットは特にない
    - 仮想環境でシェルスクリプトを動かそうとしたときに CRLF になって動かない
- `core.ignorecase`
  - `false` にしておいた方が無難
  - ファイルは `git mv -f file.txt File.txt` で変更できる
  - ディレクトリは一度別名にするしかなさそう

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
