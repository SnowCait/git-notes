# Gist

## Gist から通常リポジトリへ移行
ファイルが増えてきたら通常のリポジトリで管理したくなります。

### 手順
1. Gist のページを開いて URL をコピー
2. ローカルにクローン
```shell
git clone https://gist.github.com/user-name/commit-hash directory-name
```
3. ディレクトリへ移動
```shell
cd directory-name
```
4. リポジトリ `repository-name` を新規作成
5. リモートを書き換え
```shell
git remote set-url origin git@github.com:user-name/repository-name.git
```
6. プッシュ
```shell
git push -u origin master
```
7. Gist の削除
